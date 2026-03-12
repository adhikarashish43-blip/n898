# QuizArena v23 — Setup Guide
## Total time: ~10 minutes

---

## ✅ WHAT'S FIXED IN v23
- **White screen bug fixed** — the app now loads correctly when deployed
- All features restored: quiz levels, admin panel, learn mode, score log, comments, Sudoku

---

## STEP 1 — Deploy to Netlify (3 min)

1. Go to **https://netlify.com** → sign up free (use Google login)
2. On your dashboard, scroll down to the drag-and-drop box:
   **"Want to deploy a new site without connecting to Git? Drag and drop your site output folder here"**
3. **Drag the entire `quizarena` folder** onto that box (the folder containing index.html, not just index.html alone)
4. Wait ~10 seconds → Netlify gives you a URL like:
   **`https://wonderful-cupcake-abc123.netlify.app`**
5. ✅ Open it in Chrome — the quiz should load!

---

## STEP 2 — Firebase is pre-configured ✓

Your Firebase database is already connected. No changes needed.

If you ever need to reset the database rules (e.g. "Permission denied" error):
- Go to Firebase Console → Realtime Database → Rules
- Make sure it says:
```json
{
  "rules": {
    ".read": true,
    ".write": true
  }
}
```

---

## HOW TO USE IT

### You (admin):
1. Open your Netlify URL → click **⚙** (gear icon) → enter PIN: **0809**
2. In Admin Panel:
   - **Chapter tab** — switch between Chapter 1 / Chapter 2
   - **Questions tab** — add/edit quiz questions for each level
   - **Scores tab** — see Nancy's score log
   - **Comments tab** — see Nancy's comments
   - **Learn tab** — control which concepts show in Learn mode
3. Changes are **live instantly** — no re-deploy needed

### Nancy (student):
1. Open the Netlify URL → click **▶ Take the Quiz**
2. Choose a level (Squirtle / Charizard / Mewtwo / Real World)
3. Answer 5 questions with a timer
4. See results + review

---

## ADMIN PIN
Current PIN: **0809**

To change it, open `index.html` in a text editor, find:
```js
const ADMIN_PIN = "0809";
```
Change to any number, save, then drag the folder to Netlify again.

---

## RE-DEPLOYING
Whenever you update `index.html` directly:
- Just drag the `quizarena` folder onto Netlify again → redeploys in seconds

(If you only change questions via the Admin Panel, no re-deploy is needed — it saves to Firebase live)

---

## TROUBLESHOOTING

**White screen?**
→ Make sure you dragged the *folder* (`quizarena`), not just `index.html` alone

**"Permission denied" in browser console?**
→ See Step 2 above — fix Firebase rules

**Questions not saving?**
→ Double-check you're online and Firebase rules allow write access
