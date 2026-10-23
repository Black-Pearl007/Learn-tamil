# Learn Tamil (தமிழ் கற்போம்)

An interactive web app for beginners to learn Tamil letters, numbers, everyday words and phrases. It combines flashcards, spaced-repetition review, quizzes, a matching game and a handwriting pad. It runs entirely in the browser, so there is nothing to install and no account to create.

## Why I built this

Many children and adults who grow up outside Tamil Nadu, or in English-medium schools, can speak some Tamil but struggle to read it. I wanted a simple, free tool that teaches the script and basic vocabulary in short sessions on a phone, without sign-ups or ads.

## Features

**Learning modes**

- **Learn:** flip cards (tap, Space or swipe), hear the Tamil, and mark cards you know
- **Review:** spaced repetition using Leitner boxes. Rate each card Again, Good or Easy and it comes back after 1, 3, 7, 14 or 30 days. A badge on the tab shows how many cards are due
- **Quiz:** 10 questions in three styles (Tamil to answer, answer to Tamil, and Listen). Wrong answers can be practised again straight after the round
- **Match:** a timed pairing game with a best time saved for each topic
- **Write:** draw the letter with a finger or mouse over a faint guide, then press Check to compare it with the correct letter
- **Chart:** pick a consonant and see how the 12 vowel signs change it (for example க + ா = கா), with audio for every form

**Content**

- 10 topics: vowels, consonants, combined letters (216 generated from Unicode), numbers, everyday words, colours, family, days, food and phrases
- Quiz wrong answers for combined letters are other vowels on the same consonant, so the choices are the confusable ones

**Motivation and progress**

- XP, levels, a daily goal and a day streak
- Progress page with a bar per topic and personal bests
- Export and import progress as a JSON file to move between devices
- Sound effects (can be muted) and confetti for perfect rounds

**Quality**

- Works on phones and desktops, with automatic and manual light and dark mode
- Keyboard shortcuts in every mode, visible focus, and reduced-motion support

## How it works

- All content lives in one `DECKS` object in `index.html`. Each card has the Tamil text, a romanised pronunciation and an English meaning.
- Combined letters are built in code by joining each consonant with a vowel sign (`ா`, `ி`, and so on), so 216 cards come from 18 consonants and 12 signs.
- Review uses five Leitner boxes. Rating Again sends a card back to box 0, Good moves it up one box and Easy up two. Each box has a longer wait before the card is due again.
- Quiz questions take the correct answer and add three wrong answers from the same topic. For combined letters the wrong answers come first from the same consonant.
- Progress is stored in `localStorage` under one key (`tamil_v2`) and can be exported as JSON.
- The Write pad uses pointer events on a `<canvas>`, so it works the same with touch, pen and mouse.
- Audio uses the browser's Web Speech API (`speechSynthesis`) with the language set to `ta-IN`. Sound effects use the Web Audio API.

## Tech stack

- HTML, CSS and vanilla JavaScript (no frameworks, no dependencies)
- Google Fonts (Noto Sans Tamil, Mukta) for correct Tamil rendering
- `localStorage`, Web Speech API, Web Audio API and Canvas
- GitHub Pages for hosting

## Run it locally

```bash
git clone https://github.com/YOUR-USERNAME/tamil-learning-app.git
cd tamil-learning-app
```

Then open `index.html` in any browser.

## Add your own words

Add an entry to a topic's `items` list in `index.html`:

```js
["காலை","kaalai","morning"]
```

The format is `[Tamil, romanisation, English meaning]`. To add a new topic, add another entry to `DECKS` using `mk(name, field, label, reverseLabel, items)`. The `field` (`"rom"` or `"en"`) decides what the quiz asks for.

## Limitations

- Audio quality depends on the device. Some phones and computers have no Tamil voice installed, so the Listen button may be silent.
- Romanisation is a learning aid and cannot capture every Tamil sound exactly (for example the letters ழ, ள, ற and ன).
- The Write pad does not check your handwriting. You compare it yourself with the correct letter.
- Progress is stored per browser and device. Use Export and Import to move it.
- The new topics (colours, family, days, food, phrases) still need to be checked by a native speaker.

## Testing and feedback

- _Fill in: who tested the app (for example, 5 students or family members), what confused them, and what you changed because of it._
- _Fill in: who checked the Tamil spellings and pronunciations (for example, a Tamil teacher or a native speaker)._

## What I learned

- _Write 3 or 4 points in your own words. For example: how Unicode builds Tamil combined letters, how spaced repetition schedules reviews, how pointer events and canvas work for drawing, how saving data in the browser works._

## Future improvements

- Handwriting recognition for the Write pad
- Stroke-order animations for each letter
- Simple sentences and a sentence-building game
- Pronunciation check using speech recognition
- Recorded audio by native speakers instead of device voices
- Installable offline version (PWA)

## License

MIT. See [LICENSE](LICENSE).
