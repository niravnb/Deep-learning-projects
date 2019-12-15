# Word Embeddings

Topics: CBOW, Skip-gram, Glove, co-occurrence matrix, PMI, TF-IDF

The first library that we need to download is the Beautiful Soup library, which is a very useful Python utility for web scraping. Another important library that we need to parse XML and HTML is the lxml library.

First, we need to convert our article into sentences. We use nltk.sent_tokenize utility to convert our article into sentences. To convert sentences into words, we use nltk.word_tokenize utility. As a last preprocessing step, we remove all the stop words from the text.

 The idea behind TF-IDF scheme is the fact that words having a high frequency of occurrence in one document, and less frequency of occurrence in all the other documents, are more crucial for classification.

TF-IDF is a product of two values: Term Frequency (TF) and Inverse Document Frequency (IDF). Term frequency refers to the number of times a word appears in the document. IDF refers to the log of the total number of documents divided by the number of documents in which the word exists.

Word2Vec model comes in two flavors: Skip Gram Model and Continuous Bag of Words Model (CBOW).

In the Skip Gram model, the context words are predicted using the base word. For instance, given a sentence "I love to dance in the rain", the skip gram model will predict "love" and "dance" given the word "to" as input.

On the contrary, the CBOW model will predict "to", if the context words "love" and "dance" are fed as input to the model. The model learns these relationships using deep neural networks.


GloVe: Global Vectors for Word Representation: GloVe is an unsupervised learning algorithm for obtaining vector representations for words. Training is performed on aggregated global word-word co-occurrence statistics from a corpus, and the resulting representations showcase interesting linear substructures of the word vector space.
Training: The GloVe model is trained on the non-zero entries of a global word-word co-occurrence matrix, which tabulates how frequently words co-occur with one another in a given corpus. Populating this matrix requires a single pass through the entire corpus to collect the statistics. For large corpora, this pass can be computationally expensive, but it is a one-time up-front cost. Subsequent training iterations are much faster because the number of non-zero matrix entries is typically much smaller than the total number of words in the corpus. The training objective of GloVe is to learn word vectors such that their dot product equals the logarithm of the words' probability of co-occurrence.

To implement Word2Vec, there are two flavors to choose from — Continuous Bag-Of-Words (CBOW) or continuous Skip-gram (SG). In short, CBOW attempts to guess the output (target word) from its neighbouring words (context words) whereas continuous Skip-Gram guesses the context words from a target word.

Skip-gram: works well with small amount of the training data, represents well even rare words or phrases
CBOW: several times faster to train than the skip-gram, slightly better accuracy for the frequent words

To elaborate further, since Skip-gram learns to predict the context words from a given word, in case where two words (one appearing infrequently and the other more frequently) are placed side-by-side, both will have the same treatment when it comes to minimising loss since each word will be treated as both the target word and context word. Comparing that to CBOW, the infrequent word will only be part of a collection of context words used to predict the target word. Therefore, the model will assign the infrequent word a low probability.

￼

1. Continuous Bag of Words(CBOW), Skip-gram and GloVe models, out of which the first two are prediction-based models whereas the last one is a combination of both count and prediction based model. 
2. Data Cleaning 
3. Pre-processing Hyper-parameters: context window size, removing stop words, etc. 
4. Evaluation metric: we are comparing the cosine similarity of the 
expected word for each model. Higher the cosine similarity better the performance.
5. Pre-processing, Post-processing (normalizing the vectors), Increasing the window size,  helps 
6. Memory vs Training time: We observed that GloVe takes more memory while training whereas word2vec takes longer time to train because GloVe computes the co-occurrence matrix only once (depending on the vocabulary it can take huge amount of memory) whereas word2vec parses the sentences in an online fashion handling each co-occurrence separately. As a result of which GloVe can reuse the co-occurrence matrix even if embedding size gets changed whereas word2vec has to be trained from scratch after changing its embedding dimensionality. 

Hyper-parameters:
• Window - This hyperparameter controls the context window size. Our window is symmetric
i.e. we are considering both the left and the right context.
• Size - This hyperparameter controls the embedding size of the word representation.
• negative - This hyperparameter controls the number of negative samples for each word in
the vocabulary.
• hs - If this flag is set instead of negative sampling, the hierarchical softmax technique is used.
• alpha - The negative samples in GloVe are sampled according to the smoothed unigram
distribution. In order to smooth the original contexts’ distribution, all context counts are
raised to the power of alpha.
• w+c - This flag allows us to add word vectors to the context vectors as part of the embedding
output. Adding context vectors effectively adds first-order similarity terms to the second-order similarity function.
• nrm - This flag allows us to normalize all vectors to unit length. Doing this makes the dot
production operation equivalent to cosine similarity.
• min-count - This flag discards the words from the vocabulary whose count is less than the
min-count.
