# Global-Ban-System
A comprehensive cross-server ban management system with customizable DM notifications and advanced administrative controls.
> 💡 **Built for the Zygnal Ecosystem — to download and use this extension, you must be part of the Zygnal Ecosystem.**  
> This extension (cog) is part of the **Zygnal Ecosystem** and is only available through its supported platforms.  
> You can use it with:  
> - The **[Discord Bot Framework](https://github.com/TheHolyOneZ/discord-bot-framework)** — ideal for developers who want full control and flexibility *(includes an integrated extension marketplace)*, or  
> - The **[ZygnalBot](https://zygnalbot.de)** — a prebuilt, plug-and-play Discord bot *(also includes an integrated extension marketplace)*.  
>
> Browse and install extensions at [zygnalbot.com/extension](https://zygnalbot.com/extension).  
> For help or community discussions, join us on Discord: [discord.gg/sgZnXca5ts](https://discord.gg/sgZnXca5ts)
# Global Ban System Extension for ZygnalBot

A comprehensive cross-server ban management system with customizable DM notifications and advanced administrative controls.

## 🌟 Features

- **Cross-Server Ban Management**: Ban users across all servers using the bot
- **Customizable DM Notifications**: Interactive customizer with templates and variables
- **JSON Template System**: Import/export templates with pre-made options
- **Rate Limiting**: Prevent abuse with configurable cooldowns
- **Webhook Logging**: Track all ban activities with Discord webhooks
- **Automatic Cleanup**: Remove expired bans automatically
- **Advanced Authorization**: Multi-level permission system
- **Periodic Checking**: Scan existing members for global bans
- **Statistics & Analytics**: Detailed ban statistics and reporting

## 📋 Commands Overview

### Main Command Group
- **Base Command**: `!globalban` or `!gb`
- **Aliases**: `gb` (shorthand)

### 🔨 Management Commands

| Command | Description | Usage |
|---------|-------------|-------|
| `!gb add <user_id> <reason> [duration]` | Add a global ban | `!gb add 123456789 Spamming 7d` |
| `!gb remove <user_id>` | Remove a global ban | `!gb remove 123456789` |
| `!gb list` | View all global bans | `!gb list` |
| `!gb check <user_id>` | Check ban status | `!gb check 123456789` |
| `!gb info <user_id>` | Detailed ban information | `!gb info 123456789` |
| `!gb search <query>` | Search bans by username/reason | `!gb search spam` |

### ⚙️ Configuration Commands

| Command | Description | Usage |
|---------|-------------|-------|
| `!gb settings` | View system settings | `!gb settings` |
| `!gb customize` | Interactive DM customizer | `!gb customize` |
| `!gb templates` | View available templates | `!gb templates` |
| `!gb preview` | Preview current DM | `!gb preview` |
| `!gb stats` | View ban statistics | `!gb stats` |

### 👥 Authorization Commands

| Command | Description | Usage |
|---------|-------------|-------|
| `!gb authorize <user_id>` | Authorize user | `!gb authorize 123456789` |
| `!gb unauthorize <user_id>` | Remove authorization | `!gb unauthorize 123456789` |

### 🔧 System Configuration

| Command | Description | Usage |
|---------|-------------|-------|
| `!gb webhook <url>` | Set logging webhook | `!gb webhook https://...` |
| `!gb checkmode <mode>` | Set check mode | `!gb checkmode both` |
| `!gb interval <seconds>` | Set check interval | `!gb interval 120` |
| `!gb ratelimit` | Configure rate limits | `!gb ratelimit` |

### 📤 Data Management

| Command | Description | Usage |
|---------|-------------|-------|
| `!gb export` | Export bans to JSON | `!gb export` |
| `!gb import <json>` | Import bans from JSON | `!gb import {...}` |
| `!gb cleanup` | Manual cleanup expired bans | `!gb cleanup` |

## 🎨 DM Customization

### Interactive Customizer
The `!gb customize` command opens an interactive interface with buttons:

- **📝 Edit Title**: Customize the DM embed title
- **📄 Edit Description**: Customize the DM embed description  
- **🎨 Edit Color**: Change the embed color
- **👁️ Preview**: See how the DM looks
- **💾 Save Changes**: Save your customizations
- **📤 Export JSON**: Export current settings
- **📥 Import JSON**: Import templates or custom JSON
- **🔄 Reset to Default**: Reset to default settings

### Available Variables
Use these variables in your custom templates:

| Variable | Description |
|----------|-------------|
| `{user}` | User mention (@User) |
| `{username}` | User's display name |
| `{user_id}` | User's Discord ID |
| `{bot_name}` | Bot's name |
| `{server}` | Server name they tried to join |
| `{guild}` | Same as server |
| `{reason}` | Ban reason |
| `{ban_date}` | Date originally banned (YYYY-MM-DD) |
| `{expires}` | Expiration date or 'Never' |
| `{banned_by}` | Who issued the ban (@User) |

### Pre-made Templates

| Template | Style | Description |
|----------|-------|-------------|
| `gaming_server` | 🎮 Gaming | Casual gaming community style |
| `professional` | 💼 Professional | Formal business tone |
| `friendly` | 😊 Friendly | Apologetic and understanding |
| `minimal` | 📝 Minimal | Simple and direct |
| `detailed` | 📊 Detailed | Comprehensive information |
| `corporate` | 🏢 Corporate | Business/enterprise style |
| `casual` | 😎 Casual | Very relaxed and informal |
| `security` | 🔒 Security | Security-focused messaging |

## 🔐 Permission System

### Authorization Levels
Users are authorized if they have any of:

- **Bot Owner**: Automatic full access
- **Guild Owner**: Full access in their guild
- **Administrator**: Full access with admin permissions
- **Manage Server**: Full access with manage server permissions
- **Manually Authorized**: Added via `!gb authorize`

### Required Permissions
The bot needs these permissions:
- `Ban Members` - To execute global bans
- `Send Messages` - To send notifications
- `Embed Links` - For rich embeds
- `Read Message History` - For command processing

## ⚡ Check Modes

| Mode | Description | Performance |
|------|-------------|-------------|
| `on_join` | Check only when users join | Low impact |
| `periodic` | Check all members periodically | Medium impact |
| `both` | Check on join AND periodically | Higher impact |

## 🛡️ Rate Limiting

### Default Limits
- **Guild Cooldown**: 30 seconds between bans per guild
- **User Cooldown**: 5 minutes between bans per user
- **Max Bans/Minute**: 10 bans maximum per minute

### Configurable Settings
```
!gb ratelimit guild <seconds>    # Set guild cooldown
!gb ratelimit user <seconds>     # Set user cooldown  
!gb ratelimit max <count>        # Set max bans per minute
```

## 📊 Duration Format

Support for flexible duration formats:
- `7d` - 7 days
- `2w` - 2 weeks  
- `1h` - 1 hour
- `30m` - 30 minutes
- `1d12h` - 1 day and 12 hours
- No duration = Permanent ban

## 🔄 Automatic Features

### Auto-Cleanup
- Automatically marks expired bans as inactive
- Runs every hour by default
- Configurable cleanup intervals

### Periodic Scanning
- Scans existing server members for global bans
- Configurable scan intervals (minimum 30 seconds)
- Respects rate limits to prevent API abuse

## 📝 JSON Template Format

### Basic Template Structure
```json
{
  "title": "🚫 Your Custom Title with {variables}",
  "description": "Your custom description with {username} and {reason}",
  "color": 16711680
}
```

### Full Export Format
```json
{
  "global_ban_dm_template": {
    "title": "Custom title",
    "description": "Custom description", 
    "color": 16711680
  },
  "examples": {
    "custom_template": {
      "title": "Example title",
      "description": "Example description",
      "color": 15158332
    }
  }
}
```

## 🚨 Security Features

- **Reason Sanitization**: Removes harmful content from ban reasons
- **Mention Protection**: Prevents @everyone/@here abuse
- **URL Filtering**: Optional URL removal from reasons
- **Length Limits**: Enforces maximum reason length (500 characters)
- **Input Validation**: Validates all user inputs

## 📈 Statistics Tracking

View detailed statistics with `!gb stats`:
- Total bans (active/expired/permanent/temporary)
- Recent activity (7 days, 30 days)
- Top ban reasons
- Most active administrators
- Protected server count

## 🔧 Configuration Files

### Storage Location
- Config file: `data/global_bans.json`
- Auto-created on first run
- Automatic backups on save

### Manual Configuration
Advanced users can manually edit the JSON configuration file for bulk operations or advanced settings.

## ⚠️ Important Notes

1. **Backup Regularly**: Export your ban list regularly as backup
2. **Test Templates**: Always preview DM templates before saving
3. **Monitor Rate Limits**: Adjust limits based on your server size
4. **Webhook Security**: Keep webhook URLs private
5. **Permission Management**: Regularly review authorized users

## 🆘 Troubleshooting

### Common Issues

**Bot can't ban users:**
- Check bot has `Ban Members` permission
- Ensure bot role is higher than target user's highest role

**DMs not sending:**
- User may have DMs disabled
- Check bot permissions and rate limits

**Commands not working:**
- Verify user authorization level
- Check bot permissions in channel

**Rate limit errors:**
- Reduce check frequency
- Increase cooldown times

## 📞 Support

For support and bug reports, visit: [zygnalbot.com/support](https://zygnalbot.com/support)

---

**Version**: 2.1.0 | **Author**: TheHolyOneZ | **Made for**: ZygnalBot

*This extension is part of the ZygnalBot ecosystem - Advanced Discord bot management made simple.*
