# Measure information flow in dramatic texts

A dramatic text can also be understood as an information network, in which characters can play different roles depending on the extent to which they add new themes and ideas to an already established discourse or repeat what has already been said. From this point of view, within the field of quantitative drama analysis, we can apply an information theoretic approach and measure how innovative one character is compared to another. Furthermore, such pairwise comparisons make it possible to construct a network that presents the relationships between characters in a new way, complementing the already well-established practice of creating character networks based on co-occurrences in scenes. To achieve this, we have developed a methodology for calculating the semantic similarity and novelty between characters’ speeches taking also into account the time of the utterances. 

The method consists of two parts: in preprocessing, a table is created from the TEI files of the dramas, in which the names of the actors, the act in which they are uttered and a sentence-level embedding score (based on S-BERT) are assigned to each sentence. In the second part (calculation), the novelty of an actor's utterance is calculated based on the cosine similarity of the embedding scores associated with the sentences.


Data from the Shakespeare subcorpus of the Drama Corpus Project: https://github.com/dracor-org/shakedracor

Preprocessing:
1. In folder _drama_conversion_ you can find the steps to create tsv files from the tei files. In the output tsv for every sentence of the drama we assign the name of the speaker, a timestamp, the act in which the sentence is uttered
2. In folder _embedding_test_ you can find the way to calculate embeddings of the sentences created at _drama_conversion_ with any HuggingFace model using HuggingFaceEmbeddings and Sentence-Transformers.

Calculation:
1. In _suprise-pairwise-from-embedding.R_ you can find the main calculations for the pairwise comparison of characters based on the maximum cosine similarities of their sentences taking into account the time of the utterence; the weightening procedure; and the network normalization.
2. In _network-from-embedding.R_ you can find the R codes for visualizing the results from _suprise-pairwise-from-embedding.R_
3. In _pairwise_sentences_ you can compere two characters and see their most and less similar sentences.

Example sentences (folder _sentence-example_):

_hamlet-name_all-MiniLM-L6-v2.tsv_ is an example output of the preprocessing (of Shakespeare's Hamlet), which can be used in the R codes.
In the orher folders you can find the most and less similar sentences in some pairwise compersions as a result of _pairwise_sentences.R_. You can find here the results of the comparison of different SBERT models too (in folder _model-compare_).
