# Real Estate Property Search Feature

## Overview

This project is a real estate property search feature built using Next.js, MySQL, and GraphQL. The application allows users to filter properties based on sale or rent, price range, number of bedrooms, and area. It is designed to handle a large number of properties (10,000, 100,000, and 1,000,000) to test query performance. The listing page displays the project name, short title, price, bedroom count, area, short description, and an image gallery that works with both mouse interactions on PCs and swipe gestures on mobile devices. The goal is to achieve a score of 95 or higher on Google Insight.

## IMPORTANT!
- This repository is implemented on top of branch [lwinht](https://github.com/FazWaz/developer-testing/tree/lwinht) and the commit is __ed647d4__
- There were __errors__ to run his application. Therefore, I revised his docker-compose.yml and docker-entrypoint-initdb to fix this issue.
- __Google Insight cannot give well score on localhost__. I tried using ngrok and the problem is meta of ngrok decreases SEO score. Moreover, getting 95 scores must set up the project on the production. Find someone who rent a web hosting for the test.
- The code is alright, and I prefer not to expend effort on rewriting code.

## Setup

### Prerequisites

- Node.js
- Docker
- Docker Compose

### Installation

1. **Install dependencies:**

   ```sh
   npm install
   ```

2. **Set up environment variables:**
   Create a `.env` file in the root directory and add the following:

   ```env
   DATABASE_URL=mysql://root:password@localhost:3306/real_estate
   NEXT_PUBLIC_GRAPHQL_ENDPOINT=http://localhost:3000/api/graphql
   ```

3. **Build the database service:**

   ```sh
   docker-compose up --build
   ```

4. **Generate mock data:**

   Create a script to generate fake data and run it:
   ```sh
   npx prisma migrate dev --name init
   npx prisma db seed -- --count 10000
   ```

5. **Run the application**

   ```sh
   npm run dev
   ```
   Next application will be served on http://localhost:3000