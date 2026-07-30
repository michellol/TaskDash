Task Dash

A drag-and-drop task board with a live shared "Upcoming Events" table. No login — you type a board name, and anyone who types the same name lands on the same board.

## Setup (once, ~5 minutes)

1. Go to https://console.firebase.google.com and create a free project.
2. In the project, click **Add app > Web (`</>`)** and register it. You don't need Firebase Hosting — you're hosting on GitHub Pages instead.
3. Copy the `firebaseConfig` object it gives you.
4. Open `task-dash.html`, find the `FIREBASE_CONFIG` constant near the top of the `<script>` block, and paste your values in.
5. In the Firebase console, go to **Build > Realtime Database > Create Database**. Any region is fine; starting in test mode is fine.
6. Go to the **Rules** tab and set:
   ```json
   {
     "rules": {
       ".read": true,
       ".write": true
     }
   }
   ```
   This is what makes "no password, just a word" work — anyone who knows the board name can read and write it. It also means anyone who has your database URL could technically browse every board on it, so don't put anything sensitive on here. Fine for team task boards.
7. Push this repo to GitHub, enable **GitHub Pages** in the repo settings (Settings > Pages > Deploy from branch), and open the page it gives you.

## Using it

- First visit: you'll be asked for a board name. Type any word — that's your board.
- Anyone who types the same word (case doesn't matter) sees and edits the same board, live.
- Click the "Board" button in the header any time to switch to a different board.
- Everything else — cards, colors, drag-to-reorder, the events table — works the same as before, it's just synced through Firebase instead of local storage.
