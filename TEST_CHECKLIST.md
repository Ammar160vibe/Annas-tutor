# Anna's Tutor — Pre-Deploy Test Checklist

Run through this before every deploy. Each section maps to a feature area.
Open the HTML file in a browser (or on the iPad) and go through each check.

---

## 🔑 1. First-Time Setup
- [ ] Opening app with no saved key shows the setup screen
- [ ] Entering a bad key shows an error (not a crash)
- [ ] Entering a valid key dismisses the setup screen
- [ ] After setup, refreshing the page goes straight to the app (key persisted)
- [ ] ⚙️ Settings button opens the settings overlay
- [ ] Changing the Claude key in settings saves correctly
- [ ] ElevenLabs key field accepts input and saves

---

## 💬 2. Free Chat Mode
- [ ] Welcome message appears on load
- [ ] Quick prompt buttons send a message when tapped
- [ ] Typing a message and pressing Send gets a response
- [ ] AI response appears with the correct subject strip colour
- [ ] Switching subject tabs (Math / Reading / Science) shows the greeting for that subject
- [ ] Switching subjects clears the chat history (tutor responds as the new character)
- [ ] Changing the grade updates responses (test: ask "what is 2+2" on Grade 1 vs Grade 10)
- [ ] Grade selection persists after refresh
- [ ] 🔥 Streak counter shows correctly
- [ ] 🏅 Badges button opens the badges panel
- [ ] Earning a badge shows the toast notification
- [ ] 🔊 Voice toggle turns speech on/off
- [ ] Replay button on a bubble plays the audio
- [ ] 🎤 Mic button activates and transcribes speech

---

## 📚 3. Daily Lessons Mode
- [ ] Clicking "Daily Lessons" tab shows the lesson panel
- [ ] Lesson panel shows correct subject (Math / Reading / Science)
- [ ] Lesson panel header shows "Set 1" and "0% covered" for a fresh user
- [ ] 10 lessons are listed with lesson 1 unlocked and lessons 2–10 locked
- [ ] Clicking lesson 1 opens the lesson chat
- [ ] Tutor character appears in the left panel
- [ ] Correct character shown for subject (Tiger=Math, Owl=Reading, Frog=Science)
- [ ] Lesson content is delivered automatically on open
- [ ] Character animates: thinking (loading), speaking (audio), celebrate (quiz pass)
- [ ] User can ask follow-up questions in the lesson chat
- [ ] ← Back button returns to the lesson list
- [ ] ✅ Done button is HIDDEN when lesson first opens
- [ ] After lesson delivers, mini quiz (3 questions) appears automatically
- [ ] Answering 2+ correctly shows "Lesson Complete" and reveals Done button
- [ ] Answering 0–1 correctly shows "Keep Going" with retry option
- [ ] Tapping Done marks lesson as ✅ complete and unlocks lesson 2
- [ ] Returning to a completed lesson replays the chat (no re-fetch)
- [ ] Returning to an incomplete lesson re-runs the quiz

---

## 🎯 4. Daily Test
- [ ] After completing all 10 lessons, "Take the Test" button appears
- [ ] Test generates 10 questions (loading state visible)
- [ ] Questions are multiple choice with 4 options each
- [ ] Correct answer highlights green, wrong highlights red
- [ ] Score tracks correctly across all 10 questions
- [ ] Results screen shows score out of 10
- [ ] Results screen shows curriculum coverage % (e.g. "40% covered")
- [ ] "Start Next Lesson Set!" button appears and works
- [ ] "Retry This Test" button re-generates the test
- [ ] ← Back to Lessons returns to lesson panel

---

## 🔄 5. Continuous Lessons (Next Set)
- [ ] Tapping "Start Next Lesson Set!" shows a loading state
- [ ] New 10 lessons load with DIFFERENT topics than the previous set
- [ ] Lesson panel header now shows "Set 2"
- [ ] Curriculum coverage % has increased from Set 1
- [ ] Old lesson progress is gone (all 10 show as locked/fresh)
- [ ] After completing all curriculum topics, the cycle resets and repeats

---

## 🍎 6. Canadian Curriculum Coverage
- [ ] Grade 2 Math topics include: Place value, Skip counting, Fractions, Time
- [ ] Grade 2 Reading topics include: Digraphs, Story elements, Paragraph writing
- [ ] Grade 2 Science topics include: Animal habitats, Water cycle, Simple circuits
- [ ] Changing to Grade 5 generates noticeably harder lesson topics
- [ ] Changing grade clears the lesson panel and fetches grade-appropriate topics

---

## 🔁 7. Migration (Existing Users)
- [ ] If upgrading from an old version, Anna's existing lesson progress is preserved
- [ ] Old week-based lesson keys are migrated to set-based keys on first load
- [ ] Covered topics from completed sets carry over correctly
- [ ] No "come back next week" message appears anywhere

---

## 📱 8. iPad / Mobile Checks
- [ ] App fills the full screen with no overflow or scroll issues
- [ ] Input bar is visible above the keyboard when typing
- [ ] Lesson side panel (character + content) fits without overflow
- [ ] All buttons are large enough to tap comfortably
- [ ] Voice works on Safari iOS (requires user gesture — tapping a button first)
- [ ] App works when added to Home Screen (PWA mode)

---

## ⚡ 9. Edge Cases
- [ ] What happens if the API call fails? (disconnect WiFi mid-lesson) — should show a friendly error, not a crash
- [ ] What happens if lesson generation returns malformed JSON? — should fall back to curriculum topic list
- [ ] What happens if Anna completes all Grade 2 curriculum topics? — cycle should reset, not crash
- [ ] Switching subjects mid-lesson returns to correct subject on back
- [ ] Switching grades while in lessons mode reloads lessons for new grade

---

## ✅ Sign-off

Before deploying, confirm:
- [ ] Brace balance check passes (`diff=0`)
- [ ] All critical path items above pass
- [ ] Tested on iPad Safari specifically (not just desktop browser)
- [ ] `annas-tutor-final.html` is the file being deployed (not a backup)
