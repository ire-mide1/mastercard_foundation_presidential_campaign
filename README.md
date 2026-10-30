# Campaign Website: How to Run It

Everything you edit is in the block at the top of `index.html` marked **EDIT EVERYTHING IN THIS BLOCK**.

## 1. Before launch
- **CONFIG**: set your exact position title, slogan, `campaignStart` (Day 1 date), and `votingDate`.
- **PROMISES**: replace the four examples with your real agenda. These also become the poll options.
- **POSTS**: Day 1 ("Why Me") has a draft. Rewrite it in your voice and add your YouTube video ID if you have one.

## 2. Each day (2 minutes)
Add the new day to `POSTS`:
```js
{ day: 2, title: "Your title", video: "", body: `<p>Your content...</p>` },
```
Commit and push. The site works out the date itself: the new day shows under **Today**, and earlier days move to **The Trail So Far**.

Preview any day before it goes live by adding `?day=2` (or 3, 4, …) to the end of the URL.

## 3. Collect poll votes and messages (Google Forms, free)
Without this step, the poll and form still work for visitors, but you won't receive the answers.

1. Create a Google Form with one **multiple choice** question ("What matters most?") using your exact promise titles as options.
2. Click ⋮ → **Get pre-filled link**, pick any option, click **Get link**, and copy it.
   The link contains `entry.123456789=...`. That number is your entry ID.
3. Your form's action URL is the form link with `/viewform` changed to `/formResponse`.
4. Fill in `pollForm: { action: "https://docs.google.com/forms/d/e/XXXX/formResponse", entry: "entry.123456789" }`.
5. Do the same for a second form with two **short answer/paragraph** questions (message, name) and fill in `voiceForm`.

Responses go to the Forms "Responses" tab, which you can link to a Google Sheet. Post the poll results and the common themes (`HEARD`) on the site during the campaign.

## 4. Publish on GitHub Pages
1. Create a new public repo (for example `iremide-campaign`) and upload `index.html` and `README.md`.
2. Go to **Settings → Pages → Build and deployment**, set Source to **Deploy from a branch**, choose `main` and `/ (root)`, then save.
3. After a minute or two the site is live at `https://<your-username>.github.io/iremide-campaign/`.
4. Paste that link into `CONFIG.siteUrl` so the WhatsApp share button uses it.

## 5. After you win
Change each promise's `status` to `"in-progress"` or `"done"` as you deliver. The site becomes your public report card.

Notes: the "Hey, Leader!" popup shows once per visitor (it reappears whenever you use `?day=` for testing). The footer states it's a personal campaign site. Keep that, and only add CMU or Mastercard Foundation logos if you've confirmed you're allowed to.
