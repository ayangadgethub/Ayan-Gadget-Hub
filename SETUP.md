# Ayan Gadget Hub — Setup

The storefront and product-management interface are committed to GitHub Pages. Product storage and admin login require a Supabase project to be connected.

## 1. Create a Supabase project
1. Open https://supabase.com/dashboard and create a project.
2. Open **Project Settings → API** (or **Connect**) and copy the Project URL and anon/publishable key. Never use or publish the service_role/secret key in browser code.
3. In this repository, edit `config.js` and replace `YOUR_SUPABASE_PROJECT_URL` and `YOUR_SUPABASE_ANON_OR_PUBLISHABLE_KEY`.

## 2. Create the database
1. In Supabase, open **SQL Editor → New query**.
2. Copy the contents of `supabase-setup.sql` into the editor and run it.
3. Open **Authentication → Users** and create the admin user using your own email and a strong password. Disable public signups if enabled.
4. Copy that user's UUID from the Users page. In SQL Editor, run:
   `insert into public.admin_users (user_id) values ('PASTE-ADMIN-USER-UUID-HERE');`
   Replace the placeholder with the UUID. Do not share your password.

## 3. Publish
GitHub Pages should rebuild after the commits. Check **Repository → Settings → Pages** and confirm the source is the `main` branch and `/(root)`. Wait a few minutes, then open the published site.

## 4. Add products
Open the site, choose **Admin Login**, sign in with the admin email/password, then add the product name, price, image URL, description and category. Product images must be reachable via an HTTPS image URL.

## Important
The UI is committed but will not store products until the Supabase configuration, SQL, and admin allow-list setup above are completed. Do not put a Supabase service_role/secret key in `config.js`.
