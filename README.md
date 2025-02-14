# Next.js 15 Build Timeout with Fetch API in getStaticProps/getServerSideProps

This repository demonstrates a potential bug in Next.js 15 where using `fetch` within `getStaticProps` or `getServerSideProps` with a slow or unavailable external API can lead to build timeouts.  The build may appear successful but the data will be incomplete or stale.

## Problem
The issue arises when the external API call within the data fetching function takes longer than the default Next.js build timeout. The build process will terminate before the API response is received, leaving the application with outdated data.  Error messages may not always clearly indicate this timeout problem.

## Solution
The recommended solution involves configuring a longer timeout using the `NEXT_PUBLIC_API_TIMEOUT` environment variable (or a similar approach tailored to your project structure). Additionally, robust error handling within the API request is critical to gracefully handle failure scenarios.

## Reproduction
1. Clone this repository.
2. Install dependencies: `npm install`
3. Attempt to build the application: `npm run build` (You might need to adjust the environment variable based on your setup.)
4. Observe the results.  With the bug, the build might succeed, but data in pages might be incorrect or missing.  The solution should fix this.
