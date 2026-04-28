# Content Scheduler

An n8n workflow that automatically posts Canva designs to Twitter and LinkedIn on a schedule.

## Features

- Runs on a configurable schedule (default: every 6 hours)
- Fetches designs from a Canva folder
- Auto-generates post captions using OpenAI ChatGPT
- Posts to Twitter (X) and LinkedIn simultaneously
- Logs all posts to a Google Sheet for tracking

## Prerequisites

1. **n8n instance** (self-hosted or n8n.cloud)
2. **Canva API credentials** (OAuth2)
3. **Twitter API credentials** (v2)
4. **LinkedIn API credentials** (OAuth2)
5. **OpenAI API key** (ChatGPT)
6. **Google Sheets API** (optional, for logging)

## Setup

### 1. Canva Integration

- Create a Canva app at https://developers.canva.com/
- Get your **Client ID** and **Client Secret**
- Add OAuth redirect URL from n8n
- Enable the **Media** and **Design** API scopes
- In n8n, add **Canva OAuth2** credential

### 2. Twitter API

- Apply for API access at https://developer.twitter.com/
- Create an app and generate **API Key** and **API Secret**
- Enable **OAuth 1.0a** (for user context posting)
- Add credentials in n8n as **Twitter (X)**

### 3. LinkedIn API

- Create a LinkedIn app at https://www.linkedin.com/developers/
- Get **Client ID** and **Client Secret**
- Request **Share on LinkedIn** scope
- Add **LinkedIn OAuth2** credential in n8n

### 4. OpenAI Integration

- Add OpenAI API credential in n8n

### 5. Google Sheets (Optional)

- Create a spreadsheet to log posted content
- Share with your service account email
- Add **Google Sheets** credential in n8n

### 6. Configure Workflow

1. Download `workflow.json`
2. Import into n8n
3. Set credentials for all nodes
4. Adjust the schedule interval in **Schedule Trigger**
5. Set Canva folder ID (or leave default to use all designs)
6. Update Google Sheet ID if using logging
7. Activate workflow

## How It Works

1. **Schedule Trigger** — fires every 6 hours (configurable)
2. **Get Canva Designs** — fetches designs from specified folder
3. **Filter Published** — checks metadata to skip already-posted designs
4. **Generate Caption** — uses ChatGPT to write engaging captions
5. **Post to Twitter** — uploads image and tweets
6. **Post to LinkedIn** — shares to LinkedIn feed
7. **Log to Sheet** — records post details (URLs, timestamp)

## Customization

- **Post frequency**: Change interval in Schedule Trigger
- **Caption style**: Edit the system prompt in ChatGPT node
- **Target platforms**: Disable Twitter/LinkedIn nodes if needed
- **Image size**: Filter designs by dimensions in Canva node

## Costs

- n8n: Free (self-hosted) or paid
- Canva API: Free within limits
- Twitter API: Free tier available
- LinkedIn API: Free
- OpenAI: ~$0.002 per 1K tokens
- Google Sheets: Free

## License

MIT
