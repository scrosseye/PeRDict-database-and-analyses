# PeRDict-database
The Perfect Rhymes Dictionary Database is housed here

We used the CMU Pronouncing Dictionary (the CMUdict) to develop the Perfect Rhymes Dictionary (PeRDict). The CMUdict is an open-source pronouncing dictionary developed at Carnegie Mellon University to assess rhymes. The CMUdict provides a mapping between a word and that word’s phonemes for 133,779 words in the English language. However, in practice, many of these words are extremely rare. Because of the rarity of many words in the CMUdict, we elected to only keep those words that overlap between the CMUdict and the English Lexicon Project (ELP). The ELP comprises 79,672 words of which 47,885 words were shared with the CMUdict. These ~48,000 words were selected for initial inclusion into PeRDict.

The CMUdict includes the word (the key) and pronunciations in the form of phonemes for the values. Stress marks (as numbers) are also included for stressed vowels in each word wherein vowels followed by the number 1 are stressed. 

To calculate perfect rhymes for the ~48,000 selected words, we considered words to be perfect rhymes of other words when the stressed vowel in both words in the CMUdict was identical as well as the following sounds (i.e., the rhyme). Additionally, the consonant(s) before the stressed vowel (if present) had to differ (i.e., the onset was different). Thus, nap and map in Table 1 would rhyme as would maps and collapse, but nap would not rhyme with collapse.

To calculate the number of perfect rhymes for the ~48,000 words shared between the CMUdict and the ELP database, we wrote a Python script that measured the number of words that shared the same perfect rhymes with each word. Thus, each word was compared to the other ~48,000 words and raw counts were computed for the number of words that rhymed with each word in the CMUdict. 

In practice, many of the ~48,000 words shared between the CMUdict and the ELP database are rare and thus not likely candidates to influence word decoding (i.e., children are unlikely to have exposure to these rare words, so they probabilistically would not influence the development of rhymes and the decoding of words). To control for the rarity of words and the effect this could have on rhyme development and word processing, we identified the most frequent content words in the English language using the Corpus of Contemporary English (COCA). We ignored function words because their irregular spellings and reduced stress likely affect their rhyme patterns and learnability (Weber, 2006). COCA contains more than one billion words from texts produced from 1990-2019 and includes eight genres: subtitles, spoken, fiction, magazine, web pages, blogs, newspapers, and academic texts. From COCA, we selected the most frequent content words for the following frequency bands: 1,000 words, 2,500 words, 5,000 words, and 10,000 words. We removed words that were not in these bands to control for rare words in the CMUdict when calculating the number of rhymes. Removing rare words helped ensure that PeRDICT database included rhyme counts based on words that are likely known by readers and would more likely influence word decoding. 

To calculate the number of perfect rhymes for the reduced word lists extracted from COCA based on frequency (i.e., the 1,000, 2,500, 5,000, and 10,000 most frequent words), we followed a similar approach used with all words shared between the CMUdict and the ELP database. For example, for the 1,000-word list, each word was compared to the other ~1,000 words and the number words that rhymed for each word within that 1,000-word list was computed. 

For all rhyme counts, we calculated the number of rhymes for the raw words (i.e., tokens) and for word lemmas. Word lemmas differ from tokens because the lemmas remove morphological elements of the word to better represent the basic form of the word. Using our example from before, the words maps and collapse would rhyme at the token level, but they would not rhyme with nap. However, during lemmatization, maps would revert to map and would then rhyme with nap. To lemmatize the words, we used the natural language processing package spaCy. 

Not all words in the CMUdict had stressed vowels (e.g., y’all, marketers, greedier and priciest), which resulted in 20 words shared between the CMUdict and the ELP database being removed. Thus, the final count for words shared between the CMUdict and the ELP database for which all perfect rhymes could be calculated was 47,865. For the COCA word frequency lists, there was also not perfect overlap with either the CMUdict or the ELP database meaning that counts for the most frequent words were not perfectly aligned with the numbers 1,000, 2,500, 5,000, and 10,000 and so our frequency bands are adjusted (see Table 2 for the actual number of words in the perfect rhyme counts for these frequency bands). Also, there were many words that reported zero counts for rhymes for the entire dataset and for the frequency bands. This is because some words in each sub-dataset did not rhyme with any of the other words in that sub-dataset. A good example is the word travel which had zero rhymes within the COCA 1,000, 2,500, and 5,000 frequency bands but reported two rhymes in the 10,000 frequency band and four in the total data set. An example of word that had no rhymes in the entire dataset is dubious. The number of zero counts for each dataset are reported in Table 2.

In total, the CMU Rhyming Database includes 12 variables. Perfect rhymes calculated for the 47,865 shared words and lemmas between the CMUdict and the ELP database and perfect rhymes calculated for the 994 (1,000-word band), 2,471 (2,500-word band), 4,895 (5,000-word band), and 9,538 (10,000-word band) most frequent words and lemmas reported by COCA.
