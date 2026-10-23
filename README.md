# Sandy Studio — LED Business App

A cross-platform starter app for Android and web, built with Expo + React Native + Supabase.

## Included in this starter
- Dashboard: booking value, advance received, pending payments, recorded expenses, cash-flow estimate, upcoming events
- Create event bookings and customer records
- Record transport/team/other expenses, team member name and member count
- Mark bookings completed
- Generate invoice print/PDF flow
- Open WhatsApp with a prefilled payment reminder
- Cloud database schema with basic row-level security

## 1. Requirements
- Node.js LTS (20 or newer recommended)
- A Supabase account/project: https://supabase.com
- For Android device testing, Expo Go: https://expo.dev/client

## 2. Configure the cloud database
1. Create a Supabase project.
2. Open Supabase Dashboard → SQL Editor.
3. Paste and run `supabase/schema.sql`.
4. In Authentication → Providers, enable Email.
5. Create your own user in Authentication → Users (or use the supported sign-up flow you add).
6. Copy Project URL and the publishable/anon key from Project Settings → API.
7. Copy `.env.example` to `.env` and fill:
   ```
   EXPO_PUBLIC_SUPABASE_URL=https://YOUR-PROJECT.supabase.co
   EXPO_PUBLIC_SUPABASE_ANON_KEY=YOUR_PUBLISHABLE_OR_ANON_KEY
   ```
8. Restart Expo after editing `.env`.

## 3. Install and run
```bash
npm install
npm run start
```
- Press `w` to run the web app.
- Scan the QR code with Expo Go to test on Android.
- Press `a` if Android Studio/emulator is installed.

## Important authentication note
This starter schema only permits authenticated database access, but the UI currently does not include a login screen. Before using real customer data, add Supabase Auth UI and bind records to an owner/team ID. Do not change the policies to public access and never put a Supabase service-role key in this app. This is a starter project, not yet production-ready.

## Known MVP limitations / next steps
- Payment recording currently starts with an advance amount; add a separate `payments` table for multiple instalments and payment dates.
- Profit is currently shown as advance received minus recorded expenses, not accounting profit. To calculate true profit, track all receipts and event-linked expenses.
- WhatsApp reminders open a prefilled WhatsApp message; the user must review and send it. Automatic messages need WhatsApp Business Platform setup and a secure server-side integration.
- Web invoice opens the browser print dialog; select “Save as PDF”. Native builds generate a PDF file and open the share sheet.
- Add edit/delete flows, date filters, backups, authentication screen and owner/team access before production.

## Project structure
```
app/
  _layout.tsx
  index.tsx
lib/
  supabase.ts
  types.ts
supabase/
  schema.sql
app.json
package.json
.env.example
README.md
```
