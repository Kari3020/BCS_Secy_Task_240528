<b><h1>Custom Tokenizer Design:</h1></b>
<br>
Our custom tokenizer is a Python class designed from scratch to handle the quirks and messiness of real-world news text. Its main job is to break up raw text into clean, meaningful tokens that are ready for further analysis
Key Features:
1. Lowercasing
Purpose: Standardizes all text to lowercase to ensure that tokens like "Fake" and "fake" are treated identically.

2. Contraction Expansion
Purpose: Expands common English contractions to their full forms, making the language more uniform and easier to process downstream.
Example: "can't" → "can not", "won't" → "will not"

3. Tokenization
Purpose: The tokenizer splits the text into individual words using a regular expression that matches sequences of letters and numbers. Punctuation is ignored, so “Fake news!” becomes just “fake” and “news”.

4. Repeated-Character Normalization
Purpose: Detects and collapses words with three or more repeated characters, which are often used for emphasis in fake or sensational news.
Example: "sooooo" → "so <REPEAT:5>"

<hr>
<b><h1>Custom Lemmatizer Design:</h1></b><br>
The custom lemmatizer is designed to work hand-in-hand with a simple, rule-based POS tagger. This approach ensures that only appropriate suffixes are removed, preserving the grammatical integrity of the tokens.
Rule-Based POS Tagger:
NOUN: Recognized by common noun suffixes (e.g., -tion, -ment, -ness, -ity, -er, -or, -ist)
VERB: Recognized by verb suffixes (e.g., -ing, -ed, -ate, -en, -ify, -ise, -ize)
ADJ: Recognized by adjective suffixes (e.g., -able, -ible, -al, -ful, -ic, -ive, -less, -ous)
Default: If no suffix matches, the word is tagged as a noun.

Verbs: Removes -ing, -ed, -s if tagged as a verb.
Example: "running" → "runn", "played" → "play"

Nouns: Removes plural -s, -es if tagged as a noun.
Example: "dogs" → "dog", "boxes" → "box"

Adjectives: Removes comparative/superlative -er, -est if tagged as an adjective.
Example: "bigger" → "bigg", "fastest" → "fast"

Fallback: If none of the above rules apply, the word is returned unchanged.
<hr>
<b><h2>Comparison with off‑the‑shelf pipelines:</h2></b><br>
Off-the-shelf NLP tools like spaCy or NLTK are good at handling regular text and grammar, but they don’t pay special attention to things like stretched words or playful spelling.
Our custom pipeline, on the other hand, is built to spot these tricks by cleaning up repeated letters and grouping similar words together. This helps us catch the unique patterns often found in fake news.
While standard tools are easy to use and work well for most text, our custom approach is better for finding the sneaky clues that fake news writers use.
