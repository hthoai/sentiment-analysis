sep='\t'
encoding='utf-16'

### Preprocess code to choose
# Convert text to lowercase
df['content'] = df['content'].str.lower()
# Remove numbers and words with numbers
df['content'] = df['content'].str.replace('\w*\d\w*', ' ')
# Remove punctuation
df['content'] = df['content'].str.replace('[^\w\s]', ' ')
# Remove whitespaces
df['content'] =  df['content'].str.split().apply(lambda x : ' '.join(word for word in x))
# Tokenize
df['content'] = df['content'].apply(lambda x : ViTokenizer.tokenize(x))
