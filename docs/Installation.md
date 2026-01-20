---
layout: default
title: Installation Guide
description: Step-by-step guide to install and set up RelishEconomy on your Minecraft server
---

# Installation Guide

Get RelishEconomy up and running on your Minecraft server in just a few minutes.

## 📋 Requirements

<table>
<thead>
<tr>
<th>Component</th>
<th>Requirement</th>
<th>Notes</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>Minecraft</strong></td>
<td>1.21+</td>
<td>Latest version recommended</td>
</tr>
<tr>
<td><strong>Server</strong></td>
<td>Paper, Purpur, or Paper-based forks</td>
<td>Spigot not officially supported</td>
</tr>
<tr>
<td><strong>Java</strong></td>
<td>21+</td>
<td>Required for Minecraft 1.21+</td>
</tr>
<tr>
<td><strong>Dependencies</strong></td>
<td>Vault (recommended), PlaceholderAPI (optional)</td>
<td>Auto-detected if present</td>
</tr>
</tbody>
</table>

## 🚀 Step-by-Step Installation

### Step 1: Download the Plugin

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1.5rem; margin: 1.5rem 0;">
  <div style="border: 1px solid #27ae60; border-radius: 8px; padding: 1.5rem; background: #f0fff4;">
    <h4 style="margin-top: 0; color: #27ae60;">🆓 Free Version</h4>
    <p>Perfect for basic economy needs</p>
    <ul>
      <li>Multi-currency support</li>
      <li>Basic commands</li>
      <li>Vault integration</li>
      <li>SQLite database</li>
    </ul>
    <a href="https://modrinth.com/plugin/relisheconomy" style="display: inline-block; background: #27ae60; color: white; padding: 0.75rem 1.5rem; border-radius: 6px; text-decoration: none; font-weight: 600;">Download from Modrinth</a>
  </div>
  
  <div style="border: 1px solid #f1c40f; border-radius: 8px; padding: 1.5rem; background: #fffbf0;">
    <h4 style="margin-top: 0; color: #f39c12;">⭐ Premium Version</h4>
    <p>Advanced features for professional servers</p>
    <ul>
      <li>Shop & Sell GUIs</li>
      <li>Currency exchange</li>
      <li>MySQL support</li>
      <li>Premium support</li>
    </ul>
    <a href="https://builtbybit.com/resources/relisheconomy" style="display: inline-block; background: #f1c40f; color: #2c3e50; padding: 0.75rem 1.5rem; border-radius: 6px; text-decoration: none; font-weight: 600;">Purchase on BuiltByBit</a>
  </div>
</div>

### Step 2: Install Dependencies (Recommended)

While RelishEconomy works standalone, these plugins enhance functionality:

**Vault** (Highly Recommended)
- Enables compatibility with other economy plugins
- Download: [Spigot](https://www.spigotmc.org/resources/vault.34315/)

**PlaceholderAPI** (Optional)
- Adds placeholder support for scoreboards and chat
- Download: [Spigot](https://www.spigotmc.org/resources/placeholderapi.6245/)

### Step 3: Server Installation

1. **Stop your server** (important for clean installation)

2. **Place the JAR file** in your `plugins/` folder:
   ```
   server/
   ├── plugins/
   │   ├── RelishEconomy.jar  ← Place here
   │   ├── Vault.jar
   │   └── PlaceholderAPI.jar
   └── ...
   ```

3. **Start your server** - RelishEconomy will create default configuration files

### Step 4: First-Time Setup

After installation, you'll find these files in `plugins/RelishEconomy/`:

<table>
<thead>
<tr>
<th>File</th>
<th>Purpose</th>
<th>Required</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>config.yml</code></td>
<td>Main configuration</td>
<td>✅ Yes</td>
</tr>
<tr>
<td><code>lang/en.yml</code></td>
<td>English messages</td>
<td>✅ Yes</td>
</tr>
<tr>
<td><code>lang/ar.yml</code></td>
<td>Arabic messages</td>
<td>❌ Optional</td>
</tr>
<tr>
<td><code>prices.yml</code></td>
<td>Item prices for selling <span class="badge badge-premium">Premium</span></td>
<td>❌ Optional</td>
</tr>
<tr>
<td><code>shop.yml</code></td>
<td>Shop configuration <span class="badge badge-premium">Premium</span></td>
<td>❌ Optional</td>
</tr>
<tr>
<td><code>gui.yml</code></td>
<td>GUI customization <span class="badge badge-premium">Premium</span></td>
<td>❌ Optional</td>
</tr>
</tbody>
</table>

### Step 5: Basic Configuration

Edit `config.yml` to set up your first currency:

```yaml
currencies:
  dollars:
    symbol: "$"
    display-name: "Dollars"
    color: "<green>"
    default: true
    starting-balance: 100.0
    payments-enabled: true
```

### Step 6: Restart and Test

1. **Restart your server** to apply configuration changes

2. **Verify installation** with these commands:
   ```
   /re version          # Check plugin status
   /balance             # Test basic functionality
   /re help             # View available commands
   ```

## 🔑 Premium Activation

If you purchased the premium version:

1. **Get your license key** from your BuiltByBit purchase

2. **Add it to config.yml**:
   ```yaml
   license-key: "your-license-key-here"
   ```

3. **Restart server** and verify with:
   ```
   /re license          # Check license status
   ```

## ✅ Verification Checklist

After installation, verify everything is working:

- [ ] Plugin loads without errors in console
- [ ] `/re version` shows correct version and license status
- [ ] `/balance` command works
- [ ] Vault integration detected (if installed)
- [ ] PlaceholderAPI integration detected (if installed)
- [ ] Premium features accessible (if licensed)

## 🔧 Troubleshooting

### Common Issues

**Plugin not loading**
- Check Java version (requires 21+)
- Verify server software (Paper/Purpur required)
- Check console for error messages

**Commands not working**
- Ensure Vault is installed and loaded
- Check permissions are set correctly
- Verify plugin loaded successfully

**Database errors**
- Check file permissions in plugins folder
- For MySQL: verify connection details
- Check available disk space

**Premium features not working**
- Verify license key is correct
- Check internet connection for license verification
- Ensure license hasn't expired

### Getting Help

<div style="display: flex; gap: 1rem; flex-wrap: wrap; margin: 1.5rem 0;">
  <a href="https://discord.gg/relish" style="display: inline-flex; align-items: center; gap: 0.5rem; background: #5865f2; color: white; padding: 0.75rem 1rem; border-radius: 6px; text-decoration: none;">
    💬 Discord Support
  </a>
  <a href="https://github.com/iM5LB/relisheconomy/issues" style="display: inline-flex; align-items: center; gap: 0.5rem; background: #24292e; color: white; padding: 0.75rem 1rem; border-radius: 6px; text-decoration: none;">
    🐛 Report Issues
  </a>
</div>

---

## 🎯 Next Steps

Once RelishEconomy is installed:

1. **[Configure currencies](configuration)** - Set up your server's economy
2. **[Learn commands](commands)** - Master all available commands  
3. **[Set up PlaceholderAPI](placeholderapi)** - Integrate with other plugins

<div style="text-align: center; margin: 2rem 0; padding: 1.5rem; background: #f8f9fa; border-radius: 8px; border-left: 4px solid #3498db;">
  <strong>Installation complete!</strong> Ready to configure your economy? Check out our <a href="configuration">Configuration Guide</a> next.
</div>

## Requirements

| Component | Requirement |
|-----------|-------------|
| **Minecraft** | 1.21+ |
| **Server** | Paper, Purpur, or Paper-based forks |
| **Java** | 21+ |
| **Dependencies** | Vault (recommended), PlaceholderAPI (optional) |

## Step-by-Step Installation

### 1. Download the Plugin
- **Free Version**: Download from [Modrinth](https://modrinth.com/plugin/relisheconomy)
- **Premium Version**: Purchase from [BuiltByBit](https://builtbybit.com/resources/relisheconomy)

### 2. Install Dependencies
Download and install these plugins (optional but recommended):
- [Vault](https://www.spigotmc.org/resources/vault.34315/) - For economy integration
- [PlaceholderAPI](https://www.spigotmc.org/resources/placeholderapi.6245/) - For placeholders

### 3. Server Installation
1. Stop your server
2. Place `RelishEconomy.jar` in your `plugins/` folder
3. Start your server
4. The plugin will create default configuration files

### 4. First-Time Setup
After installation, you'll find these files in `plugins/RelishEconomy/`:
- `config.yml` - Main configuration
- `lang/en.yml` - English messages
- `lang/ar.yml` - Arabic messages
- `prices.yml` - Item prices for selling (Premium)
- `shop.yml` - Shop configuration (Premium)
- `gui.yml` - GUI customization (Premium)

### 5. Basic Configuration
Edit `config.yml` to set up your currencies:

```yaml
currencies:
  dollars:
    symbol: "$"
    display-name: "Dollars"
    color: "<green>"
    default: true
    starting-balance: 100.0
```

### 6. Restart and Test
1. Restart your server
2. Run `/re version` to verify installation
3. Test with `/balance` command

## Premium Activation

If you purchased the premium version:
1. Get your license key from BuiltByBit
2. Add it to `config.yml`:
```yaml
license-key: "your-license-key-here"
```
3. Restart server
4. Run `/re license` to verify activation

## Troubleshooting

### Common Issues
- **Plugin not loading**: Check Java version (requires 21+)
- **Commands not working**: Verify Vault is installed
- **Database errors**: Check file permissions

### Getting Help
- Check the [Troubleshooting Guide](Troubleshooting)
- Join our [Discord](https://discord.gg/relish)
- Report bugs on [GitHub](https://github.com/RelishDev/RelishEconomy/issues)