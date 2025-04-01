Named Entity Recognition (NER) is a Natural Language Processing (NLP) technique used to identify and classify key entities in text into predefined categories such as:

- **Person** (e.g., "Elon Musk")
- **Organization** (e.g., "OpenAI")
- **Location** (e.g., "Paris")
- **Date/Time** (e.g., "January 1, 2025")
- **Monetary Values** (e.g., "$1000")
- **Miscellaneous** (e.g., product names, percentages, medical terms, etc.)

### How NER Works:

1. **Tokenization** – The text is split into words or phrases (tokens).
2. **Feature Extraction** – Each token is analyzed for context, position, and structure.
3. **Classification** – Using rule-based methods, statistical models, or deep learning, the tokens are assigned to entity categories.

### NER Approaches:

1. **Rule-Based** – Uses dictionaries and regex patterns.
2. **Machine Learning-Based** – Uses algorithms like CRF, HMM, or SVM trained on labeled datasets.
3. **Deep Learning-Based** – Uses models like LSTMs, Transformers (BERT, spaCy, etc.) for higher accuracy.

### Example:

Input:  
_"Apple Inc. was founded by Steve Jobs in California in 1976."_

Output:

- **Organization**: Apple Inc.
- **Person**: Steve Jobs
- **Location**: California
- **Date**: 1976

NER is widely used in chatbots, search engines, finance, healthcare, and more to extract useful information from unstructured text.