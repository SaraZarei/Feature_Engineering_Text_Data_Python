# Feature_Engineering_Text_Data_Python
### Cleaning up text
- Unstructured text data cannot be directly used in most analyses. Multiple steps need to be taken to go from a long free form string to a set of numeric columns in the right format that can be ingested by a machine learning model. The first step of this process is to standardize the data and eliminate any characters that could cause problems later on in your analytic pipeline.
### High level text features
- The most fundamental information you can calculate about free form text is its size, such as its length and number of words
### word count representation
- creating features based on the actual content of each text For each unique word in the dataset a column is created. For each entry, the number of times this word occurs is counted and the count value is entered into the respective column. Once the vectorizer has been fit to the data, it can be used to transform the text to an array representing the word counts. This array will have a row per block of text and a column for each of the features generated by the vectorizer. CountVectorizer with its default settings creates a feature for every single word in your corpus. This can create far too many features, often including ones that will provide very little analytical value. For this purpose CountVectorizer has parameters that you can set to reduce the number of features:
min_df : Use only words that occur in more than this percentage of documents. This can be used to remove outlier words that will not generalize across texts.
max_df : Use only words that occur in less than this percentage of documents. This is useful to eliminate very common words that occur in every corpus without adding value such as "and" or "the". you have generated these count based features in an array you will need to reformat them so that they can be combined with the rest of the dataset
### Tf-idf (Term frequency-inverse document frequency)
- words that occur many times may skew the results undesirably. To limit these common words from overpowering your model a form of normalization can be used. Tf-idf has the effect of reducing the value of common words, while increasing the weight of words that do not occur in many documents.
### what are the 5 most highest scored words for each corpus?

- TFIDF_government :   0.367430
- TFIDF_public  :      0.333237
- TFIDF_present :      0.315182
- TFIDF_duty  :        0.238637
- TFIDF_citizens  :    0.229644

### Using n-grams

So far we have created features based on individual words in each of the texts. This can be quite powerful when used in a machine learning model but you may be concerned that by looking at words individually a lot of the context is being ignored. To deal with this when creating models you can use n-grams which are sequence of n words grouped together. For example:
bigrams: Sequences of two consecutive words
trigrams: Sequences of three consecutive words
### Finding the most common words

- Counts_constitution united states:    20
- Counts_people united states:          13
- Counts_preserve protect defend:       10
- Counts_mr chief justice:              10
- Counts_president united states:        8
