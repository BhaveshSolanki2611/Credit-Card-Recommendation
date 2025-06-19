# Credit Card Advisor Chatbot

A chatbot application that provides credit card recommendations and comparisons.

## Features

- Interactive chat interface
- Credit card recommendations based on user preferences
- Credit card comparisons
- Twilio integration for WhatsApp messaging

## Prerequisites

- Node.js (v18.0.0 or higher)
- MySQL (if using database features)

## Installation

1. Clone the repository
2. Install dependencies:

bash
npm install


3. Create a .env file in the root directory with the following variables:


# Server Configuration
PORT=5001
NODE_ENV=development

# Database Configuration
DB_HOST=localhost
DB_USER=root
DB_PASSWORD=your_password_here
DB_NAME=credit_card_recommendations
DB_PORT=3306

# External API Keys
DEEPINFRA_API_KEY=your_deepinfra_api_key_here

# Twilio Configuration
TWILIO_ACCOUNT_SID=your_twilio_account_sid_here
TWILIO_AUTH_TOKEN=your_twilio_auth_token_here
TWILIO_WHATSAPP_NUMBER=whatsapp:+14155238886
TWILIO_TEMPLATE_SID=your_template_sid_here


4. Setup the database:

bash
npm run db:setup
npm run db:seed


## Development

### Start in Development Mode (Frontend + Backend)

bash
npm run dev:all


### Start Frontend Only

bash
npm run dev


### Start Backend Only

bash
npm run server:dev


## Building for Production

bash
npm run build


## Deployment

### Option 1: Deploying to Heroku

1. Create a Heroku account and install the Heroku CLI
2. Login to Heroku CLI:

bash
heroku login


3. Create a new Heroku app:

bash
heroku create your-app-name


4. Set environment variables:

bash
heroku config:set NODE_ENV=production
heroku config:set DB_HOST=your-production-db-host
# Set all other environment variables similarly


5. Add a MySQL database:

bash
heroku addons:create jawsdb


6. Deploy to Heroku:

bash
git push heroku main


### Option 2: Deploying to Vercel

1. Create a vercel.json file with:

json
{
  "version": 2,
  "builds": [
    {
      "src": "package.json",
      "use": "@vercel/node"
    }
  ],
  "routes": [
    {
      "src": "/api/(.*)",
      "dest": "server/index.js"
    },
    {
      "src": "/(.*)",
      "dest": "dist/$1"
    }
  ]
}


2. Deploy to Vercel:

bash
vercel


## Project Structure

- src/ - Frontend React application
- server/ - Backend Node.js server
  - ai/ - AI processing logic
  - database/ - Database configuration and services
  - services/ - External service integrations (Twilio)
- public/ - Static files
- dist/ - Production build output