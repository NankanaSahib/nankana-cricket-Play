# Nankana Cricket Play-On: website launch guide

Customers scan the QR code on your wall, the page opens in their phone browser (no download), they book, and then set a PIN so they can log in later with their mobile number and PIN to see and track their bookings.

## How bookings are saved
The page itself stores nothing. It talks to a free Firebase cloud database. Every customer's phone and your owner page read and write the same database, so everyone sees the same bookings. Other customers only see that an hour is "Booked". Names, numbers and payment status are visible only to the customer who booked, and to you.

## 1. Firebase (free plan)
1. Go to console.firebase.google.com and create a project.
2. Build > Firestore Database > Create database (production mode).
3. Build > Authentication > Get started > Sign-in method: turn ON Anonymous and Email/Password.
4. Authentication > Users > Add user, BEFORE you publish the page: email owner@nankanacricket.app and a strong owner password of at least 10 characters. The website is public, so do not use a short number.
5. Firestore > Rules: paste everything from firestore.rules, then Publish.
6. Project settings (gear icon) > General: copy the Web API Key and Project ID into config.js.

## 2. Put the page online (GitHub Pages, free)
1. On github.com create a new PUBLIC repository named nankana-cricket-Play.
2. Upload everything in this folder (drag and drop in the browser), including config.js and privacy.html.
3. Settings > Pages > Deploy from a branch > main > / (root) > Save.
4. After 1 to 2 minutes your page is at https://nankanasahib.github.io/nankana-cricket-Play/ . If your GitHub name or repository name is different, tell me and I will make a new QR poster.
5. Open it on two phones. Make a booking on one and check that the other shows the hour as booked.
The code contains no secrets. The Firebase web key is meant to be public, and your rules protect the data.

## 3. Customer PIN login
After booking, the customer is asked to set a PIN (4 to 6 digits). Next time they tap My bookings > Log in with their mobile number and PIN, on any phone. Behind the scenes this uses Firebase email sign-in with their number, so no SMS cost. If someone forgets a PIN: Firebase > Authentication > Users, find 03XXXXXXXXX@players.nankanacricket.app, delete it, and they can set a new PIN (their old bookings stay linked to their number).
Note: the number is not verified by SMS. You confirm every booking by checking the advance payment, and you can call the number.

## 4. Owner page
On the Home screen tap the logo 7 times quickly, then type your owner password. You can mark advances as paid, block numbers, change prices, set discounts, edit the menu and set the advance percentage and JazzCash number.

## 5. Fake bookings
Valid Pakistani mobile number required, unpaid bookings are cancelled automatically after 10 minutes unless the 20% advance is paid, one unpaid booking at a time and 5 a day per phone, nothing counts until you mark it paid, and you can block numbers.

## 6. QR poster
marketing/wall-poster-website-A4.pdf is print-ready (A4). marketing/qr-website.png is the QR alone.

## 7. Cost
Firebase free plan, GitHub free, no Google Play fee. You can still publish on Google Play later with the Android project (nankana-cricket-app.zip).

## Update: owner dashboard and PIN reset
The owner page now has Bookings (filters, CSV), Customers (Reset PIN, Block), Slots (close or open hours), Prices, Features, Menu and Settings. To reset a forgotten PIN: Customers tab > Reset PIN, then the customer taps Log in > "I asked for a reset: set a new PIN". Paste the newest firestore.rules into Firebase again whenever you update.

## Update: owner dashboard and PIN reset
The owner page now has Bookings (filters, CSV), Customers (Reset PIN, Block), Slots (close or open hours), Prices, Features, Menu and Settings. To reset a forgotten PIN: Customers tab > Reset PIN, then the customer taps Log in > "I asked for a reset: set a new PIN". Paste the newest firestore.rules into Firebase again whenever you update.
