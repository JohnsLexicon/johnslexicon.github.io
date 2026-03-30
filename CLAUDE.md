# CLAUDE.md — Instructions for Claude Code

## Project Overview
John's Lexicon (johnslexicon.github.io) is a daily vocabulary site. Tagline: "A word a day, with sentences that go too far." Files: index.html (main site + all views), add.html (admin form), words.json (word data), review.html, quiz.html.

## Adding a New Word

When I say "add [word]" or "new word: [word]", do ALL of the following:

### 1. Research the word
- Look up the Merriam-Webster definition, etymology, pronunciation, and IPA
- Part of speech from Merriam-Webster
- Etymology formatted as: Language *foreign term* 'English gloss'. Use *asterisks* for italic foreign terms. No trailing period
- Simple pronunciation: hyphens between syllables, CAPS for stressed syllable (e.g., in-VAY-gul)
- IPA: copy from Merriam-Webster, include slashes

### 2. Generate the example sentence
- The site tagline is "A word a day, with sentences that go too far." The sentence MUST go too far.
- Unhinged, absurd, darkly funny, escalating in unexpected directions, or wildly inappropriate for the context
- Recurring character archetypes that work: grandpa doing something insane, White House staffers in ridiculous scenarios, toddlers with adult gravitas, mundane situations spiraling into chaos, HR emergencies, clergy behaving badly, animals with inexplicable authority
- The vocabulary word should appear naturally, not forced
- Study these existing examples for tone:
  - turgid: "the giant inflatable White House bunny overinflated catastrophically, becoming a turgid, 40-foot pastel monstrosity that the Secret Service snipers were reluctantly called in to perform what insiders still call 'the Great Bunny Deflation of '26.'"
  - extirpate: "Dropping to his knees in the moonlight, the old man swore he would extirpate every last dandelion from his lawn, hissing 'I will erase your bloodline from this soil' through clenched teeth as he repeatedly drove the knife into the earth."
  - copacetic: "The pilot announced that all systems were copacetic, his voice perfectly steady over the intercom while black smoke poured from the engines and the horizon tilted violently."
  - defenestrate: "Grandpa defenestrated the smart fridge after it suggested low-fat yogurt for the third time, then saluted as it exploded on the driveway below."
  - rusticate: "Aidan rusticated so hard he renounced electricity and married a scarecrow in a ceremony where he delivered a valediction to a congregation of confused sheep."
- No AI-sounding language. No hedging. No "get." Active voice. Chicago Manual of Style.

### 3. Generate quiz (Test Your Understanding)
- Produce exactly 4 sentences labeled A, B, C, D
- ONE sentence uses the word correctly per the definition
- THREE sentences use the word incorrectly but plausibly — each confusing it with a different similar-sounding or conceptually adjacent word
- The correct answer must be randomly distributed across A/B/C/D (not always A)
- Wrong sentences should be tricky enough to fool someone unfamiliar with the word
- ALL FOUR sentences (correct and wrong) should be unhinged/entertaining in the same over-the-top style as the example sentence — not dry or academic
- Study these existing quiz options for tone:
  - extirpate correct: "Grandma extirpated the fire ant colony from her garden using a combination of boiling holy water and language that would have resulted in her excommunication from three separate denominations"
  - extirpate wrong: "The judge agreed to extirpate the speeding violation from David's record after the defendant delivered a 90-minute valediction that somehow involved the Treaty of Rome and Carthage."
  - copacetic wrong: "She kept her voice copacetic during the exorcism, never once raising it above a pleasant whisper as the demon hurled furniture and spoke in fourteen languages."
  - rusticate wrong: "She paid a deranged Swiss craftsman eighty-seven million dollars to rusticate the penthouse's interior, leaving her with fifteen-foot antler chandeliers dripping in diamonds and the blood of endangered species."
- In the JSON, "correct" is the zero-indexed position (A=0, B=1, C=2, D=3)

### 4. Update words.json
- Add the new entry at the TOP of the array (after the opening `[`)
- Date: today's date in YYYY-MM-DD format unless I specify otherwise
- Word: lowercase
- All fields required: date, word, partOfSpeech, definitions (array), etymology, pronunciation, ipa, sentence, quiz (correct + options[4])
- NO trailing commas after the last element
- NO JavaScript comments — JSON does not support //

### 5. Update ORIGINS in index.html
- Add the word and its origin language to the ORIGINS object
- Languages: Latin, Greek, French, French/Latin, Middle English, English, Unknown
- Keep entries on the existing lines, maintain the format

### 6. Update CLUSTERS in index.html (if applicable)
- Ask me which connection group(s) the word belongs to, OR if I specify them, add it
- Current groups: The T-Words, Acts of Removal, Greek Roots, Speech & Silence, The Body, Excess & Restraint, Surface & Spectacle, Farewell & Loss, Unstoppable Force
- Add the word alphabetically within the cluster's words array
- A word can belong to multiple clusters

### 7. Preview and wait for approval
- After completing steps 1-6, show me a formatted preview of:
  - Word, part of speech, pronunciation, IPA
  - Definitions
  - Etymology
  - Example sentence
  - Quiz options with the correct answer marked
  - Connections (if any)
- DO NOT commit or push until I explicitly approve
- I may request changes to the sentence, quiz options, or any other field
- Once I say "looks good" or "push it" or similar approval, commit with message "Add [word]" and push to main

## Word JSON Schema
```json
{
  "date": "YYYY-MM-DD",
  "word": "lowercase",
  "partOfSpeech": "noun|verb|adjective|adverb",
  "definitions": ["def1", "def2"],
  "etymology": "Language *term* 'gloss', from *root* 'meaning'",
  "pronunciation": "STRESSED-syl-la-ble",
  "ipa": "/IPA here/",
  "sentence": "Unhinged example sentence.",
  "quiz": {
    "correct": 0,
    "options": [
      "Correct usage (unhinged)",
      "Plausible but wrong (unhinged)",
      "Plausible but wrong (unhinged)",
      "Plausible but wrong (unhinged)"
    ]
  }
}
```

## Style Rules
- No AI vocabulary: no "delve," "tapestry," "landscape," "nuanced," "straightforward," "genuinely," "honestly"
- No contractions in formal writing
- No "get" — use precise alternatives
- No em dashes
- Active voice always
- Oxford comma always
- No hedging or conditional framing
- Sentences should be declarative assertions
- No trailing periods on definitions or etymology
- Definitions are accurate (from Merriam-Webster). Sentences and quiz options are where the unhinged energy lives.

## Git Authentication
- Remote uses HTTPS. If push fails, ask for the GitHub personal access token.
- Token format: ghp_XXXXX
- Set with: git remote set-url origin https://TOKEN@github.com/JohnsLexicon/johnslexicon.github.io.git
- Clean up after: git remote set-url origin https://github.com/JohnsLexicon/johnslexicon.github.io.git
