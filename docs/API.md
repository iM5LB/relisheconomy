# Developer API

Complete API reference for integrating RelishEconomy into your plugins.

## Getting Started

### Add Dependency

> **Important**: RelishEconomy is not open source. The API is available for integration, but premium source code is not shared.

**Maven**:
```xml
<repository>
    <id>jitpack</id>
    <url>https://jitpack.io</url>
</repository>

<dependency>
    <groupId>com.github.iM5LB</groupId>
    <artifactId>RelishEconomy</artifactId>
    <version>1.0.1-Beta</version>
    <scope>provided</scope>
</dependency>
```

**Gradle**:
```gradle
repositories {
    maven { url 'https://jitpack.io' }
}

dependencies {
    compileOnly 'com.github.iM5LB:RelishEconomy:1.0.1-Beta'
}
```

### Plugin Dependency

Add RelishEconomy as a dependency in your `plugin.yml`:

```yaml
depend: [RelishEconomy]
# or
softdepend: [RelishEconomy]
```

## Core API

### Getting the API Instance

```java
import relish.economy.RelishEconomy;
import relish.economy.manager.AccountManager;
import relish.economy.manager.CurrencyManager;

public class YourPlugin extends JavaPlugin {
    
    private RelishEconomy economy;
    private AccountManager accountManager;
    private CurrencyManager currencyManager;
    
    @Override
    public void onEnable() {
        // Get RelishEconomy instance
        economy = (RelishEconomy) Bukkit.getPluginManager().getPlugin("RelishEconomy");
        
        if (economy == null) {
            getLogger().severe("RelishEconomy not found!");
            Bukkit.getPluginManager().disablePlugin(this);
            return;
        }
        
        // Get managers
        accountManager = economy.getAccountManager();
        currencyManager = economy.getCurrencyManager();
    }
}
```

## Account Management

### Check Balance

```java
import relish.economy.model.Currency;
import java.util.UUID;

public void checkBalance(UUID playerUUID) {
    // Get default currency
    Currency defaultCurrency = currencyManager.getDefaultCurrency();
    
    // Get balance
    double balance = accountManager.getBalance(playerUUID, defaultCurrency);
    
    // Format balance
    String formatted = accountManager.formatBalance(balance, defaultCurrency);
    System.out.println("Balance: " + formatted);
}
```

### Get Balance (Async)

```java
import java.util.concurrent.CompletableFuture;

public CompletableFuture<Double> getBalanceAsync(UUID playerUUID, Currency currency) {
    return CompletableFuture.supplyAsync(() -> 
        accountManager.getBalance(playerUUID, currency)
    );
}
```

### Set Balance

```java
public void setBalance(UUID playerUUID, Currency currency, double amount) {
    accountManager.setBalance(playerUUID, currency, amount);
}
```

### Add Money

```java
public void addMoney(UUID playerUUID, Currency currency, double amount) {
    double currentBalance = accountManager.getBalance(playerUUID, currency);
    accountManager.setBalance(playerUUID, currency, currentBalance + amount);
}
```

### Remove Money

```java
public void removeMoney(UUID playerUUID, Currency currency, double amount) {
    double currentBalance = accountManager.getBalance(playerUUID, currency);
    double newBalance = Math.max(0, currentBalance - amount);
    accountManager.setBalance(playerUUID, currency, newBalance);
}
```

### Check if Player Has Enough Money

```java
public boolean hasEnough(UUID playerUUID, Currency currency, double amount) {
    double balance = accountManager.getBalance(playerUUID, currency);
    return balance >= amount;
}
```

## Currency Management

### Get Currency by Name

```java
public Currency getCurrency(String name) {
    return currencyManager.getCurrency(name);
}
```

### Get Default Currency

```java
public Currency getDefaultCurrency() {
    return currencyManager.getDefaultCurrency();
}
```

### Get All Currencies

```java
import java.util.Map;

public Map<String, Currency> getAllCurrencies() {
    return currencyManager.getCurrencies();
}
```

### Check if Currency Exists

```java
public boolean currencyExists(String name) {
    return currencyManager.getCurrency(name) != null;
}
```

### Get Currency Display Name

```java
public String getCurrencyDisplayName(Currency currency) {
    return currency.getDisplayName();
}
```

### Get Currency Symbol

```java
public String getCurrencySymbol(Currency currency) {
    return currency.getSymbol();
}
```

## Transaction Events

### Listen to Transactions

```java
import org.bukkit.event.EventHandler;
import org.bukkit.event.Listener;
import relish.economy.event.TransactionEvent;

public class EconomyListener implements Listener {
    
    @EventHandler
    public void onTransaction(TransactionEvent event) {
        UUID player = event.getPlayer();
        Currency currency = event.getCurrency();
        double amount = event.getAmount();
        double oldBalance = event.getOldBalance();
        double newBalance = event.getNewBalance();
        String type = event.getTransactionType();
        String reason = event.getReason();
        
        // Handle transaction
        System.out.println(player + " " + type + " " + amount + " " + currency.getName());
    }
}
```

### Transaction Types

- `DEPOSIT` - Money added to account
- `WITHDRAW` - Money removed from account
- `TRANSFER_SEND` - Money sent to another player
- `TRANSFER_RECEIVE` - Money received from another player
- `EXCHANGE` - Currency exchange
- `PURCHASE` - Shop purchase
- `SELL` - Item sold
- `ADMIN_GIVE` - Admin gave money
- `ADMIN_TAKE` - Admin took money
- `ADMIN_SET` - Admin set balance

## Vault Integration

RelishEconomy automatically hooks into Vault. You can use the standard Vault API:

```java
import net.milkbowl.vault.economy.Economy;
import org.bukkit.plugin.RegisteredServiceProvider;

public void setupEconomy() {
    RegisteredServiceProvider<Economy> rsp = 
        getServer().getServicesManager().getRegistration(Economy.class);
    
    if (rsp != null) {
        Economy economy = rsp.getProvider();
        
        // Use Vault API
        double balance = economy.getBalance(player);
        economy.depositPlayer(player, 100.0);
        economy.withdrawPlayer(player, 50.0);
    }
}
```

## Exchange System

### Exchange Currency

```java
import relish.economy.manager.ExchangeManager;

public void exchangeCurrency(UUID playerUUID, Currency from, Currency to, double amount) {
    ExchangeManager exchangeManager = economy.getExchangeManager();
    
    // Get exchange rate
    double rate = exchangeManager.getExchangeRate(from, to);
    
    if (rate > 0) {
        // Calculate converted amount
        double convertedAmount = amount * rate;
        
        // Perform exchange
        boolean success = exchangeManager.exchange(playerUUID, from, to, amount);
        
        if (success) {
            System.out.println("Exchanged " + amount + " " + from.getName() + 
                             " to " + convertedAmount + " " + to.getName());
        }
    }
}
```

### Get Exchange Rate

```java
public double getExchangeRate(Currency from, Currency to) {
    ExchangeManager exchangeManager = economy.getExchangeManager();
    return exchangeManager.getExchangeRate(from, to);
}
```

## Database Access

### Execute Database Query (Advanced)

```java
import relish.economy.database.Database;
import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.ResultSet;

public void customQuery() {
    Database database = economy.getDatabase();
    
    try (Connection conn = database.getConnection()) {
        String query = "SELECT * FROM balances WHERE uuid = ?";
        
        try (PreparedStatement stmt = conn.prepareStatement(query)) {
            stmt.setString(1, playerUUID.toString());
            
            try (ResultSet rs = stmt.executeQuery()) {
                while (rs.next()) {
                    String currency = rs.getString("currency");
                    double balance = rs.getDouble("balance");
                    // Process data
                }
            }
        }
    } catch (Exception e) {
        e.printStackTrace();
    }
}
```

## Utility Methods

### Format Balance

```java
public String formatBalance(double balance, Currency currency) {
    return accountManager.formatBalance(balance, currency);
}
```

### Parse Amount with Shortcuts

```java
import relish.economy.util.ValidationUtil;

public double parseAmount(String input) {
    // Supports: 1k = 1000, 1m = 1000000, 1b = 1000000000
    return ValidationUtil.parseAmount(input);
}
```

### Validate Amount

```java
public boolean isValidAmount(double amount) {
    return amount > 0 && amount <= 999999999999.99;
}
```

## Complete Example Plugin

```java
package com.example.economyintegration;

import org.bukkit.command.Command;
import org.bukkit.command.CommandSender;
import org.bukkit.entity.Player;
import org.bukkit.plugin.java.JavaPlugin;
import relish.economy.RelishEconomy;
import relish.economy.manager.AccountManager;
import relish.economy.manager.CurrencyManager;
import relish.economy.model.Currency;

public class EconomyIntegration extends JavaPlugin {
    
    private RelishEconomy economy;
    private AccountManager accountManager;
    private CurrencyManager currencyManager;
    
    @Override
    public void onEnable() {
        // Get RelishEconomy
        economy = (RelishEconomy) getServer().getPluginManager().getPlugin("RelishEconomy");
        
        if (economy == null) {
            getLogger().severe("RelishEconomy not found!");
            getServer().getPluginManager().disablePlugin(this);
            return;
        }
        
        // Get managers
        accountManager = economy.getAccountManager();
        currencyManager = economy.getCurrencyManager();
        
        getLogger().info("Successfully hooked into RelishEconomy!");
    }
    
    @Override
    public boolean onCommand(CommandSender sender, Command command, String label, String[] args) {
        if (!(sender instanceof Player)) {
            sender.sendMessage("Only players can use this command!");
            return true;
        }
        
        Player player = (Player) sender;
        
        if (command.getName().equalsIgnoreCase("reward")) {
            // Give player 100 of default currency
            Currency defaultCurrency = currencyManager.getDefaultCurrency();
            double currentBalance = accountManager.getBalance(player.getUniqueId(), defaultCurrency);
            accountManager.setBalance(player.getUniqueId(), defaultCurrency, currentBalance + 100);
            
            String formatted = accountManager.formatBalance(100, defaultCurrency);
            player.sendMessage("You received " + formatted + "!");
            return true;
        }
        
        return false;
    }
}
```

## Best Practices

### Async Operations

Always perform database operations asynchronously:

```java
CompletableFuture.runAsync(() -> {
    // Database operation
    double balance = accountManager.getBalance(playerUUID, currency);
    
    // Return to main thread for Bukkit API
    Bukkit.getScheduler().runTask(plugin, () -> {
        player.sendMessage("Your balance: " + balance);
    });
});
```

### Error Handling

Always handle potential errors:

```java
try {
    Currency currency = currencyManager.getCurrency("dollars");
    if (currency == null) {
        // Currency doesn't exist
        return;
    }
    
    double balance = accountManager.getBalance(playerUUID, currency);
    // Use balance
} catch (Exception e) {
    getLogger().severe("Error accessing economy: " + e.getMessage());
}
```

### Cache When Possible

Cache frequently accessed data:

```java
private final Map<UUID, Double> balanceCache = new HashMap<>();

public double getCachedBalance(UUID playerUUID, Currency currency) {
    return balanceCache.computeIfAbsent(playerUUID, 
        uuid -> accountManager.getBalance(uuid, currency));
}
```

## Support

Need help with the API?

- **Discord**: [Join our server](https://discord.gg/jDr2KZcGXk)
- **Documentation**: [Full docs](https://im5lb.github.io/relisheconomy/)
- **Examples**: Check the [GitHub repository](https://github.com/iM5LB/relisheconomy)
