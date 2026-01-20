---
layout: default
title: Commands Reference
description: Complete reference for all RelishEconomy commands with examples and usage
permalink: /commands/
---

# Commands Reference

## Player Commands

### Balance Commands

<table>
<thead>
<tr>
<th>Command</th>
<th>Description</th>
<th>Permission</th>
<th>Example</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>/balance [player] [currency]</code></td>
<td>Check balance</td>
<td><code>relish.economy.balance</code></td>
<td><code>/bal coins</code></td>
</tr>
<tr>
<td><code>/bal [player] [currency]</code></td>
<td>Alias for balance</td>
<td><code>relish.economy.balance</code></td>
<td><code>/bal Steve dollars</code></td>
</tr>
<tr>
<td><code>/money [player] [currency]</code></td>
<td>Alias for balance</td>
<td><code>relish.economy.balance</code></td>
<td><code>/money</code></td>
</tr>
</tbody>
</table>

### Payment Commands

<table>
<thead>
<tr>
<th>Command</th>
<th>Description</th>
<th>Permission</th>
<th>Example</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>/pay &lt;player&gt; &lt;amount&gt; [currency]</code></td>
<td>Send money</td>
<td><code>relish.economy.pay</code></td>
<td><code>/pay Steve 100</code></td>
</tr>
</tbody>
</table>

### Leaderboard Commands

<table>
<thead>
<tr>
<th>Command</th>
<th>Description</th>
<th>Permission</th>
<th>Example</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>/baltop [currency] [page]</code></td>
<td>View top balances</td>
<td><code>relish.economy.baltop</code></td>
<td><code>/baltop dollars 2</code></td>
</tr>
<tr>
<td><code>/balancetop [currency] [page]</code></td>
<td>Alias for baltop</td>
<td><code>relish.economy.baltop</code></td>
<td><code>/balancetop</code></td>
</tr>
<tr>
<td><code>/topbalances [currency] [page]</code></td>
<td>Alias for baltop</td>
<td><code>relish.economy.baltop</code></td>
<td><code>/topbalances coins</code></td>
</tr>
</tbody>
</table>

### Currency Commands

<table>
<thead>
<tr>
<th>Command</th>
<th>Description</th>
<th>Permission</th>
<th>Example</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>/currency list</code></td>
<td>List all currencies</td>
<td><code>relish.economy.currency</code></td>
<td><code>/currency list</code></td>
</tr>
<tr>
<td><code>/currency info [currency]</code></td>
<td>Currency information</td>
<td><code>relish.economy.currency</code></td>
<td><code>/currency info dollars</code></td>
</tr>
<tr>
<td><code>/curr list</code></td>
<td>Alias for currency</td>
<td><code>relish.economy.currency</code></td>
<td><code>/curr list</code></td>
</tr>
</tbody>
</table>

## Premium Commands <span class="badge badge-premium">Premium</span>

### Exchange Commands

<table>
<thead>
<tr>
<th>Command</th>
<th>Description</th>
<th>Permission</th>
<th>Example</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>/exchange &lt;from&gt; &lt;to&gt; &lt;amount&gt; [confirm]</code></td>
<td>Convert currencies</td>
<td><code>relish.economy.exchange</code></td>
<td><code>/exchange dollars coins 500</code></td>
</tr>
<tr>
<td><code>/convert &lt;from&gt; &lt;to&gt; &lt;amount&gt; [confirm]</code></td>
<td>Alias for exchange</td>
<td><code>relish.economy.exchange</code></td>
<td><code>/convert coins dollars 10</code></td>
</tr>
<tr>
<td><code>/swap &lt;from&gt; &lt;to&gt; &lt;amount&gt; [confirm]</code></td>
<td>Alias for exchange</td>
<td><code>relish.economy.exchange</code></td>
<td><code>/swap dollars coins 1000</code></td>
</tr>
</tbody>
</table>

### Shop Commands

<table>
<thead>
<tr>
<th>Command</th>
<th>Description</th>
<th>Permission</th>
<th>Example</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>/shop [category]</code></td>
<td>Open shop GUI</td>
<td><code>relish.economy.shop</code></td>
<td><code>/shop blocks</code></td>
</tr>
<tr>
<td><code>/store [category]</code></td>
<td>Alias for shop</td>
<td><code>relish.economy.shop</code></td>
<td><code>/store</code></td>
</tr>
<tr>
<td><code>/buy [category]</code></td>
<td>Alias for shop</td>
<td><code>relish.economy.shop</code></td>
<td><code>/buy tools</code></td>
</tr>
</tbody>
</table>

### Selling Commands

<table>
<thead>
<tr>
<th>Command</th>
<th>Description</th>
<th>Permission</th>
<th>Example</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>/sellhand</code></td>
<td>Sell item in hand</td>
<td><code>relish.economy.sell</code></td>
<td><code>/sellhand</code></td>
</tr>
<tr>
<td><code>/sellall [confirm]</code></td>
<td>Sell all items</td>
<td><code>relish.economy.sell</code></td>
<td><code>/sellall confirm</code></td>
</tr>
</tbody>
</table>

### Physical Currency Commands

<table>
<thead>
<tr>
<th>Command</th>
<th>Description</th>
<th>Permission</th>
<th>Example</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>/withdraw &lt;currency&gt; &lt;amount&gt;</code></td>
<td>Get physical currency</td>
<td><code>relish.economy.withdraw</code></td>
<td><code>/withdraw coins 10</code></td>
</tr>
</tbody>
</table>

## Admin Commands

### Economy Management

<table>
<thead>
<tr>
<th>Command</th>
<th>Description</th>
<th>Permission</th>
<th>Example</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>/eco give &lt;player|all&gt; &lt;amount&gt; [currency]</code></td>
<td>Give money</td>
<td><code>relish.economy.eco</code></td>
<td><code>/eco give Steve 1000</code></td>
</tr>
<tr>
<td><code>/eco take &lt;player|all&gt; &lt;amount&gt; [currency]</code></td>
<td>Take money</td>
<td><code>relish.economy.eco</code></td>
<td><code>/eco take Steve 500</code></td>
</tr>
<tr>
<td><code>/eco set &lt;player|all&gt; &lt;amount&gt; [currency]</code></td>
<td>Set balance</td>
<td><code>relish.economy.eco</code></td>
<td><code>/eco set Steve 2000</code></td>
</tr>
<tr>
<td><code>/economy give &lt;player&gt; &lt;amount&gt;</code></td>
<td>Alias for eco</td>
<td><code>relish.economy.eco</code></td>
<td><code>/economy give Steve 100</code></td>
</tr>
</tbody>
</table>

### Plugin Management

<table>
<thead>
<tr>
<th>Command</th>
<th>Description</th>
<th>Permission</th>
<th>Example</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>/re help [page]</code></td>
<td>Show help</td>
<td><code>relish.economy.use</code></td>
<td><code>/re help 2</code></td>
</tr>
<tr>
<td><code>/re version</code></td>
<td>Plugin information</td>
<td><code>relish.economy.use</code></td>
<td><code>/re version</code></td>
</tr>
<tr>
<td><code>/re reload</code></td>
<td>Reload configuration</td>
<td><code>relish.economy.admin</code></td>
<td><code>/re reload</code></td>
</tr>
<tr>
<td><code>/re license</code></td>
<td>Check license status</td>
<td><code>relish.economy.admin</code></td>
<td><code>/re license</code></td>
</tr>
<tr>
<td><code>/re migrate &lt;plugin&gt; &lt;currency&gt;</code></td>
<td>Import data</td>
<td><code>relish.economy.admin</code></td>
<td><code>/re migrate essentials dollars</code></td>
</tr>
</tbody>
</table>

## Amount Shortcuts

You can use these shortcuts in any amount field:

<table>
<thead>
<tr>
<th>Shortcut</th>
<th>Value</th>
<th>Example</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>k</code></td>
<td>× 1,000</td>
<td><code>5k</code> = 5,000</td>
</tr>
<tr>
<td><code>m</code></td>
<td>× 1,000,000</td>
<td><code>2m</code> = 2,000,000</td>
</tr>
<tr>
<td><code>b</code></td>
<td>× 1,000,000,000</td>
<td><code>1b</code> = 1,000,000,000</td>
</tr>
</tbody>
</table>

## Command Examples

### Basic Usage
```
# Check your balance
/balance

# Check someone else's balance in coins
/balance Steve coins

# Send 500 dollars to Steve
/pay Steve 500 dollars

# View top 10 richest players
/baltop

# View page 2 of coin leaderboard
/baltop coins 2
```

### Premium Features <span class="badge badge-premium">Premium</span>
```
# Exchange 1000 dollars for coins
/exchange dollars coins 1000 confirm

# Open the shop
/shop

# Sell item in your hand
/sellhand

# Sell all items in inventory
/sellall confirm

# Get 10 physical coins
/withdraw coins 10
```

### Admin Commands
```
# Give 1000 dollars to Steve
/eco give Steve 1000 dollars

# Give 500 coins to all online players
/eco give all 500 coins

# Set Steve's balance to 5000 dollars
/eco set Steve 5000 dollars

# Reload plugin configuration
/re reload

# Migrate from EssentialsX
/re migrate essentials dollars
```