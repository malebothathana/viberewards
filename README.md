
# Loyalty Rewards App

A simple loyalty check-in web app for local businesses.

## Features
- Phone number-based check-in system
- Tracks number of visits per customer
- Uses Supabase as the backend
- Instant feedback for new and returning customers

## Tech Stack
- HTML, JavaScript (Frontend)
- Supabase (Backend)

## Setup Instructions
1. Clone or download the project.
2. Host the `index.html` file using GitHub Pages or any static server.
3. Ensure your Supabase project has a `customers` table with columns:
   - `phone` (text)
   - `visits` (integer, default: 1)
4. Include the following RPC in Supabase SQL Editor:

```
create or replace function increment_visits(user_phone text)
returns void as $$
begin
  update customers set visits = visits + 1 where phone = user_phone;
end;
$$ language plpgsql;
```

## Demo
A user enters their phone number to check in. If they already exist, their visit count is incremented. If not, they’re added to the database.
