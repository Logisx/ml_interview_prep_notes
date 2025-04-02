https://medium.com/@abhishekjainindore24/all-about-tokenization-stop-words-stemming-and-lemmatization-in-nlp-1620ffaf0f87
https://medium.com/@neri.vvo/stop-words-removal-explained-top-3-easy-ways-to-implement-in-python-9bd273bd9c95

### 1. Tokenization:
Tokenization is the process of breaking down a text into individual words or tokens. These tokens are the building blocks for further analysis.

**Tokenization are of 2 types** :

Word tokenizer — Breaking the corpus into individual words

Sentence tokenizer — Breaking the corpus into individual sentences

**Example:**

Consider the sentence: “Natural Language Processing is amazing!” Tokenization Result: [“Natural”, “Language”, “Processing”, “is”, “amazing”, “!”]

### 2. Stop Words:

**Definition:** Stop words are common words (e.g., “the,” “is,” “and”) that are often removed during NLP tasks as they don’t carry significant meaning.

**Example:**
Original: “The quick brown fox jumps over the lazy dog.” After Removing Stop Words: [“quick”, “brown”, “fox”, “jumps”, “lazy”, “dog.”]


### 3. Stemming:
**Definition:** Stemming involves reducing words to their root or base form. It aims to simplify words to their core, removing prefixes or suffixes.

Major disadvantage of stemming is that some of the words which gets stemmized may not be a proper word like happy becomes happi, history becomes histori, congratulations becomes congratul etc.

**Example**:

Original: “Running, runner, ran.”

Stemming Result: [“run”, “runner”, “ran”]


### Lemmatization
**Definition:** Lemmatization is similar to stemming but more sophisticated. It involves reducing words to their base or dictionary form (lemma) to ensure a valid word.

`.lemmatize()` contains 2 arguments : first one is the word and second one is **pos (part of speech)** which means how should the word be treated like as a noun (n which is by default), verb (v), adjective (a), adverb (r)

**Example: Here lemmatization will happen by treating each of the original word as verb**

Original: “stepped, goes, loving, made, ate, went, eaten”

Lemmatization Result: [“step”, “go”, “love”, “make”, “eat”, “go”, “eat”]


# Differences between Stemming and Lemmatization:

## Output Validity:

- **Stemming:** May result in non-valid words, as it focuses on removing prefixes and suffixes to obtain a common root.
- **Lemmatization:** Ensures the output is a valid word, considering the context and part of speech.

## Context and Part of Speech:

- **Stemming:** Generally doesn’t consider context or part of speech. It applies rules to trim words.
- **Lemmatization:** Takes into account context and the grammatical role of the word in a sentence.

## Use Cases:

- **Stemming:** Often used for information retrieval or search engines where computational efficiency is crucial.
- **Lemmatization:** Preferred in applications where maintaining the validity of words and understanding context is essential, such as question answering systems or chatbots.

**Choose Stemming:** When you want simplicity and speed, and non-valid words are acceptable.

**Choose Lemmatization:** When maintaining word validity and understanding context is critical.

# Examples of Stemming and Lemmatization

## Example 1:

- Original: “Dancing, dancer, danced.”
- Stemming Result: [“danc”, “dancer”, “danc”]
- Lemmatization Result: [“dance”, “dancer”, “dance”]

## Example 2:

- Original: “Organization, organizational, organized.”
- Stemming Result: [“organ”, “organ”, “organ”]
- Lemmatization Result: [“organization”, “organizational”, “organize”]

## Example 3:

- Original: “Happiness, happier, happiest.”
- Stemming Result: [“happi”, “happier”, “happiest”]
- Lemmatization Result: [“happiness”, “happy”, “happy”]

# Why are these processes important?

## Efficient Text Processing:

- Tokenization helps in breaking down complex texts into manageable units.
- Removing stop words reduces the dimensionality of the data for more efficient processing.

## Normalization:

- Stemming and lemmatization aid in normalizing text, ensuring consistency and improving model accuracy.

## Enhanced Feature Extraction:

- Extracting meaningful features from text is crucial for NLP tasks. Tokenization and stemming/lemmatization contribute to this process.