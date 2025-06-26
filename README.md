# Dad Discord Bot

A fun Discord bot that brings authentic dad personality to your server with static dad jokes, natural conversation timing, and rotating dad status messages. Dad feels like a real community member rather than an obvious bot.

# Invite Link : https://discord.com/oauth2/authorize?client_id=1265487524239773767&permissions=274878016512&integration_type=0&scope=bot

## Features

### 🎭 Static Dad Jokes with Personality
- **Natural delivery** with realistic typing simulation
- **Two-message flow** - setup, pause, punchline + GIF  
- **Categorized collection** (science, family, food, wordplay, and more)
- **Unlimited usage** - no rate limits or API costs
- **Fun GIF animations** that auto-delete after 5 seconds
- **Expandable library** - easily add more jokes and GIFs

### 🎮 Rotating Dad Status
- **100+ hilarious status messages** that rotate every 10-15 minutes
- **Natural Discord activities** - "Watching the grass grow", "Playing with the thermostat"
- **Authentic dad personality** - feels like dad is always up to something
- **Automatic variety** - never shows the same status twice in a row

### 🤖 Community Member Feel
- **Natural conversation timing** with realistic typing delays
- **Clean message flow** - no bot-like command responses
- **Personality-driven interactions** - GIFs and dad humor
- **Always active** with changing status to feel engaged

## Commands

| Command | Description | Features |
|---------|-------------|----------|
| `/dadjoke` | Get a random dad joke | Natural timing, GIF animations |
| `/dadjoke [category]` | Get a category-specific joke | All categories available |
| `/help` | Show available commands and categories | Complete bot information |

**No LLM integration** - Simple, fast, and cost-free!

## Quick Start

### Prerequisites
- Docker and Docker Compose
- Discord Bot Token (no LLM server needed!)

### 1. Clone and Setup
```bash
git clone <repository-url>
cd dadv1
cp .env.example .env
```

### 2. Configure Environment
Edit `.env` with your Discord bot token:
```bash
# Required - Get from https://discord.com/developers/applications
DISCORD_BOT_TOKEN=your_discord_bot_token_here

# Optional
LOG_LEVEL=INFO
```

**That's it!** No LLM configuration needed.

### 3. Deploy
```bash
./deploy.sh
```

The bot will start and sync commands to Discord automatically.

## How Dad Works

### Joke Delivery Flow
1. User types `/dadjoke`
2. Dad types for 1-2 seconds (building anticipation)
3. Dad sends the setup: "I bought some shoes from a drug dealer."
4. Dad types for exactly 2 seconds (suspense!)
5. Dad sends punchline + random GIF: "I don't know what he laced them with, but I was tripping all day!" 
6. After 5 seconds, GIF auto-deletes leaving clean text

### Status Rotation
- Dad's status changes every 10-15 minutes
- 100+ authentic dad activities like:
  - "Watching the grass grow"
  - "Playing hide-and-seek with the remote"
  - "Listening to my own dad jokes"
  - "Streaming a 3-hour documentary about trains"

## Configuration

### Environment Variables

#### Required
- `DISCORD_BOT_TOKEN` - Your Discord bot token from Discord Developer Portal

#### Optional
- `LOG_LEVEL=INFO` - Logging level (DEBUG, INFO, WARNING, ERROR)

### Simple Setup
No LLM server, no rate limits, no complex configuration. Just add your Discord token and deploy!

## Customization

### Adding Dad Jokes

Edit `data/dad_jokes.json` to add more jokes:

```json
{
  "jokes": [
    {
      "setup": "Why don't scientists trust atoms?",
      "punchline": "Because they make up everything!",
      "category": "science"
    }
  ]
}
```

**Available categories:** science, family, food, wordplay, school, sports, tech, work, and more!

### Adding GIFs

1. Add GIF files to `images/gifs/` directory
2. Name them `dad-joke[number].gif` (e.g., `dad-joke7.gif`, `dad-joke8.gif`)
3. Bot automatically finds and uses new GIFs randomly
4. No code changes needed!

### Adding Status Messages

Edit `data/status_updates.json`:

```json
{
  "statuses": [
    "Watching the grass grow",
    "Playing hide-and-seek with the remote",
    "Listening to my own dad jokes"
  ]
}
```

**Format requirements:** Start with Discord activity type (Watching/Playing/Listening/Streaming)

## Development

### Management Scripts
```bash
./deploy.sh          # Full deployment with live logs
./status.sh          # Quick status check and recent logs  
./logs.sh            # Live log monitoring
./logs.sh recent     # Last 50 lines
./logs.sh errors     # Filter for errors/warnings only
./logs.sh help       # Show all log viewing options
```

### Docker Operations
```bash
docker compose up -d dad-bot       # Start bot
docker compose logs -f dad-bot     # View logs
docker compose restart dad-bot     # Restart after changes
docker compose down               # Stop all services
```

### Project Structure
```
dadv1/
├── src/                      # Bot source code
│   ├── main.py              # Discord bot and command logic
│   ├── joke_handler.py      # Static joke system
│   ├── status_handler.py    # Status rotation system
│   └── config.py            # Configuration management
├── data/                    # Bot data storage
│   ├── dad_jokes.json       # Static joke collection (~23 jokes)
│   └── status_updates.json  # Dad status messages (~100 statuses)
├── images/gifs/             # Dad joke GIF animations
│   ├── dad-joke1.gif        # Random GIFs for punchlines
│   ├── dad-joke2.gif        # Auto-delete after 5 seconds
│   └── ...                  # Add more as dad-joke[N].gif
├── deploy.sh                # One-command deployment
├── status.sh                # Status checking
├── logs.sh                  # Log management
├── docker-compose.yml       # Container configuration
└── .env                     # Environment configuration
```

## Bot Personality

### What Makes Dad Special
- **Realistic Timing** - Types like a real person, pauses for effect
- **Clean Interactions** - No obvious bot commands in chat history
- **Always Active** - Rotating status makes him feel present
- **Dad Humor** - Authentic dad joke collection with visual flair
- **Community Member** - Feels like dad is part of the conversation

### Discord Presence
```
🟢 Dad
Watching the grass grow

[Someone uses /dadjoke]

Dad is typing...
Dad: "I bought some shoes from a drug dealer."
Dad is typing...
Dad: "I don't know what he laced them with, but I was tripping all day!" [GIF]
[5 seconds later - GIF disappears, text remains]
```

## Troubleshooting

### Bot Not Responding
1. Check bot is online: `./status.sh`
2. Verify Discord permissions: Send Messages, Use Slash Commands, Attach Files
3. Check logs: `./logs.sh errors`
4. Restart if needed: `docker compose restart dad-bot`

### Commands Not Working
1. Ensure slash commands synced: Look for "Synced X slash command(s)" in logs
2. Check Discord permissions for slash commands
3. Try in different channel or DMs

### GIFs Not Showing
1. Verify GIF files exist in `images/gifs/` directory
2. Check file naming: `dad-joke[number].gif`
3. Ensure bot has "Attach Files" permission
4. Check logs for file access errors

### Status Not Updating
1. Verify `data/status_updates.json` exists and is valid
2. Check logs for status rotation messages
3. Status updates every 10-15 minutes (be patient!)
4. Restart bot if status seems stuck

## Performance

### Resource Usage
- **Very lightweight** - No LLM processing
- **Low memory** - Simple static content
- **No external APIs** - Completely self-contained
- **Fast responses** - No network calls or AI processing

### Scalability
- **Multiple servers** - One bot can serve many Discord servers
- **High usage** - No rate limits or API costs
- **Always available** - No external dependencies

## Contributing

### Adding Content
1. **Jokes**: Edit `data/dad_jokes.json` with setup/punchline format
2. **GIFs**: Add files as `images/gifs/dad-joke[N].gif`
3. **Status**: Edit `data/status_updates.json` with Discord activity format
4. **Test**: Use `/dadjoke` and `/help` to verify changes

### Code Changes
1. Create feature branch
2. Update relevant source files in `src/`
3. Test with `LOG_LEVEL=DEBUG`
4. Update documentation

## License

This project is open source. Please use responsibly and respect Discord's Terms of Service.

## Support

Dad is designed to be simple and self-contained. Most issues can be resolved by:
1. Checking logs: `./logs.sh errors`
2. Restarting: `docker compose restart dad-bot`
3. Verifying Discord permissions
4. Ensuring file formats are correct

---

**Created with ❤️ for Discord communities that appreciate authentic dad humor and personality.**

*No AI required - just pure dad energy!* 🎯