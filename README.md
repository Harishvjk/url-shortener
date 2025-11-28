# URL Shortener

A simple yet powerful URL shortening service built with Node.js, Express, and MongoDB. Generate short URLs, track click analytics, and redirect to original URLs with ease.

## Features

- **Generate Short URLs**: Convert long URLs into compact, shareable short links
- **Click Analytics**: Track the number of visits and timestamps for each shortened URL
- **Fast Redirects**: Instantly redirect from short URL to original destination
- **Unique IDs**: Uses nanoid library to generate unique 8-character short IDs
- **RESTful API**: Clean and intuitive API endpoints

## Tech Stack

- **Runtime**: Node.js
- **Framework**: Express.js
- **Database**: MongoDB with Mongoose
- **ID Generation**: nanoid
- **Development**: Nodemon

## Installation

1. Clone the repository:

```bash
git clone https://github.com/Harishvjk/url-shortener.git
cd url-shortener
```

2. Install dependencies:

```bash
npm install
```

3. Ensure MongoDB is running locally on `mongodb://localhost:27017`

## Usage

### Start the Server

```bash
npm start
```

The server will start on `PORT 8001`

### API Endpoints

#### 1. Generate a Short URL

**POST** `/url`

Request body:

```json
{
  "url": "https://example.com/very/long/url/that/needs/shortening"
}
```

Response:

```json
{
  "id": "abc12345"
}
```

#### 2. Get Analytics

**GET** `/url/analytics/:shortId`

Response:

```json
{
  "totalClicks": 5,
  "analytics": [
    { "timestamp": 1701259200000 },
    { "timestamp": 1701259300000 },
    ...
  ]
}
```

#### 3. Redirect to Original URL

**GET** `/:shortId`

Redirects to the original URL and records the visit in the analytics.

## Project Structure

```
url-shortener/
├── index.js                 # Main server file
├── connect.js               # MongoDB connection logic
├── package.json             # Project dependencies
├── models/
│   └── url.js              # MongoDB URL schema
├── routes/
│   └── url.js              # API routes
└── controllers/
    └── url.js              # Business logic handlers
```

## Environment

- Node.js version: 14+
- MongoDB: Local instance on port 27017
