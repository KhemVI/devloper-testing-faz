# Real Estate Property Search Feature

## Overview

This project is a real estate property search feature built using Next.js, MySQL, and GraphQL. The application allows users to filter properties based on sale or rent, price range, number of bedrooms, and area. It is designed to handle a large number of properties (10,000, 100,000, and 1,000,000) to test query performance. The listing page displays the project name, short title, price, bedroom count, area, short description, and an image gallery that works with both mouse interactions on PCs and swipe gestures on mobile devices. The goal is to achieve a score of 95 or higher on Google Insight.

## IMPORTANT!
- Google Insight cannot give well score on localhost, even using ngrok.
- This repository is implemented on top of branch [lwinht](https://github.com/FazWaz/developer-testing/tree/lwinht) and the commit is __ed647d4__
- There are __errors__ to run his application. Therefore, I revised the README.md, the docker-compose.yml, and docker-entrypoint-initdb to fix this issue.
- His code runs well, and I prefer not to expend effort on writing additional code for a similar outcome.

## Features

- **Static Site Generation (SSG) with revalidation**: Ensures a fast initial load for users by pre-rendering pages at build time and revalidating them as needed.
- **Divided Data Load**: Separates data for sale and rent properties to optimize performance.
- **Search Functionality**: Users can filter properties based on:
  - Sale or Rent
  - Price Range
  - Number of Bedrooms
  - Area
- **Query String Parsing**: Allows for dynamic filtering based on the URL query parameters.
- **Image Gallery**: Supports mouse interaction on PCs and swipe gestures on mobile devices.

## Setup

### Prerequisites

- Node.js
- Docker
- Docker Compose

### Installation

1. **Clone the repository:**

   ```sh
   git clone https://github.com/FazWaz/developer-testing.git
   cd real-estate-search
   ```

2. **Install dependencies:**

   ```sh
   npm install
   ```

3. **Set up environment variables:**
   Create a `.env` file in the root directory and add the following:

   ```env
   DATABASE_URL=mysql://root:password@localhost:3306/real_estate
   NEXT_PUBLIC_GRAPHQL_ENDPOINT=http://localhost:3000/api/graphql
   ```

4. **Build the database service:**

   ```sh
   docker-compose up --build
   ```

5. **Generate mock data:**

   Create a script to generate fake data and run it:
   ```sh
   npx prisma migrate dev --name init
   npx prisma db seed -- --count 10000
   ```

6. **Run the application**

   ```sh
   npm run dev
   ```
   The next application will be served on http://localhost:3000