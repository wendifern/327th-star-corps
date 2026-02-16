# 327th Star Corps

Elite Virtual Regiment | VRChat Military Roleplay Unit

A secure web application for the 327th Star Corps with event scheduling and recruitment form submission.

## Features

✅ Interactive event scheduling  
✅ Secure recruitment application form  
✅ Discord webhook integration  
✅ Rate limiting and input validation  
✅ Responsive design  
✅ No exposed secrets in frontend code

## Setup Instructions

### Prerequisites

- Node.js (v14 or higher)  
- npm or yarn  
- A Discord webhook URL for your server

### Installation

1. Clone the repository:
```bash
git clone https://github.com/wendifern/327th-star-corps.git
cd 327th-star-corps
```

2. Install dependencies:
```bash
npm install
```

3. Create a `.env` file based on `.env.example`:
```bash
cp .env.example .env
```

4. Add your Discord webhook URL to `.env`:
```
DISCORD_WEBHOOK_URL=https://discord.com/api/webhooks/YOUR_WEBHOOK_ID/YOUR_WEBHOOK_TOKEN
PORT=3000
NODE_ENV=development
```

### Running Locally

**Development mode** (with auto-reload):
```bash
npm run dev
```

**Production mode**:
```bash
npm start
```

The server will run on `http://localhost:3000`

## API Endpoints

### POST /api/submit-application

Submits a recruitment application.

**Request Body:**
```json
{
  "discord": "username#1234",
  "vrchat": "YourVRChatUsername",
  "age": "18",
  "timezone": "EST",
  "experience": "Previous milsim experience"
}
```

**Response (Success):**
```json
{
  "success": true,
  "message": "Application submitted successfully!"
}
```

**Response (Error):**
```json
{
  "success": false,
  "message": "Validation failed",
  "errors": ["Discord username is required"]
}
```

### GET /api/health

Health check endpoint to verify the server is running.

## Security Features

- ✅ Input validation on both client and server  
- ✅ Rate limiting (10 requests per 15 minutes per IP)  
- ✅ CORS protection  
- ✅ Discord webhook token stored in environment variables  
- ✅ No sensitive data exposed in frontend code  
- ✅ Error messages don't leak internal details

## Environment Variables

| Variable | Description |
|----------|-------------|
| `DISCORD_WEBHOOK_URL` | Your Discord webhook URL (required) |
| `PORT` | Server port (default: 3000) |
| `NODE_ENV` | Environment mode (development/production) |

## Deployment

### Heroku

1. Create a new Heroku app  
2. Set environment variables:
```bash
heroku config:set DISCORD_WEBHOOK_URL="your_webhook_url"
heroku config:set NODE_ENV="production"
```
3. Deploy:
```bash
git push heroku main
```

### Other Platforms

Update the CORS configuration in `server.js` with your production domain:
```javascript
origin: ['https://yourdomain.com']
```

## License

MIT

## Support

For issues or questions, contact the 327th Star Corps leadership on Discord.
