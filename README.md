[Uploading README.md…]()
# Hamso Store

Hamso Store is a static frontend with a Netlify Functions API and Supabase database/storage. Accounts, stores, products, and orders are stored centrally so a member can sign in from another device and see the same data. Signed-in pages refresh shared state every 30 seconds and after each action.

## Backend setup

1. Create a Supabase project.
2. In Supabase SQL Editor, run `supabase/schema.sql`.
3. Copy the project URL and service role key from Supabase API settings. The service role key must stay server-side; never put it in HTML or commit it.
4. Copy `.env.example` to `.env` for local development and set `SUPABASE_URL`, `SUPABASE_SERVICE_ROLE_KEY`, `JWT_SECRET`, and `ADMIN_ACCESS_CODE`. Use a long random JWT secret and a private admin code.
5. Install dependencies and start the local Vercel development server:

   ```sh
   npm install
   npx vercel dev --listen 8888
   ```

   Open `http://localhost:8888`.

## Deploy to Vercel

Deploy through a Git-connected Vercel project or the Vercel CLI so the serverless API function is built and deployed. A static drag-and-drop upload does not build the backend function.

1. Push this project to a Git repository and import it in Vercel, or install and use the Vercel CLI with `npx vercel`.
2. In Vercel project environment variables, set `SUPABASE_URL`, `SUPABASE_SERVICE_ROLE_KEY`, `JWT_SECRET`, and `ADMIN_ACCESS_CODE` for Production and Preview as needed. Do not expose the Supabase service role key as a `VITE_` or other frontend variable.
3. Deploy the project. Vercel detects `api/[...path].js` as the API function; frontend requests to `/api/*` use the same origin.

The public product image bucket is created by the SQL schema. Member passwords are bcrypt-hashed, API sessions are signed by the server, and server routes enforce buyer, seller, and admin permissions.

## Important notes

- Existing demo accounts and orders saved in a browser's local storage are not copied into Supabase. Create accounts again after deploying this backend.
- The contact page form is still a frontend demo form and does not email or persist messages.
- Local work without the configured Supabase environment variables cannot register or load shared data.# Simple Static Website

A minimal static website scaffold (HTML, CSS, JS).

## Structure
- `index.html` - Homepage
- `about.html` - About page
- `contact.html` - Contact page with a demo form
- `styles/` - CSS files
- `scripts/` - JS files

## Run locally
Open `index.html` in a browser or serve with a simple HTTP server:

```bash
python -m http.server 8000
# then open http://localhost:8000
```
