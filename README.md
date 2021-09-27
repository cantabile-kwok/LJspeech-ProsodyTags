# LJspeech-ProsodyTags

### **Unsupervised Word-Level Prosody Tagging for Controllable Speech Synthesis**

Yiwei Guo, Chenpeng Du, Kai Yu

cantabile_kwok@sjtu.edu.cn



This repository is for the prosody tags in LJspeech (https://keithito.com/LJ-Speech-Dataset/) we obtain in our paper. There are two csv-formatted files:

### leaf_tag_all.csv

This contains all the phonetic tags for all the words in LJspeech

| word      | phones                                          | phonetic_leaf |
| --------- | ----------------------------------------------- | ------------- |
| a         | ['EY1']                                         | g             |
| a         | ['AH0']                                         | g             |
| abandon   | ['AH0', 'B', 'AE1',  'N', 'D', 'AH0', 'N']      | d             |
| abandoned | ['AH0', 'B', 'AE1',  'N', 'D', 'AH0', 'N', 'D'] | d             |
| ......    |                                                 |               |
| zoology   | ['Z', 'OW0', 'AA1',  'L', 'AH0', 'JH', 'IY0']   | a             |
| zopyrus   | ['Z', 'OW1', 'P',  'AY0', 'R', 'AH0', 'S']      | e             |

There are 10 phonetic tags for non-silent words, indexing from `a` to `j`. Silent words, such as punctuations and `<blank>`, are tagged as `k`.  

Note that there are plenty of polyphonic words, such as "a", "while", "calm", etc. They may have different phonetic tags.

### prosody_tag_all.csv

This contains the prosody tags for every word in every utterance in LJspeech.

| ID         | raw_word  | stanza   | phones                                     | prosody_tag |
| ---------- | --------- | -------- | ------------------------------------------ | ----------- |
| LJ001-0001 | printing  | printing | ['P', 'R', 'IH1',  'N', 'T', 'IH0', 'NG']  | a1          |
| LJ001-0001 | \<sil\>   | ,        | ['SIL1']                                   | k1          |
| LJ001-0001 | in        | in       | ['IH1', 'N']                               | i4          |
| ......     |           |          |                                            |             |
| LJ050-0278 | liberties | liberty  | ['L', 'IH1', 'B',  'ER0', 'T', 'IY0', 'Z'] | e1          |
| LJ050-0278 | \<sil\>   | .        | ['SIL0']                                   | k0          |

The prosody tag is in the form of `${leaf_tag}+${index_within_leaf}`, where `leaf_tag` is the leaf tag as in `leaf_tag_all.csv`, and `index_within_leaf` is the GMM index within that leaf node. In each **non-silent** leaf node, the GMM is set to have 5 components. For silent leaf node `k`, those with phone 'SIL0' is tagged as `k0`, or `k1` otherwise. Hence there exist 52 (10 non-silent leaves \* 5-GMM for each + 2 for silent words). These tags specify the prosody of the word in speech and can be further used for modeling and control.

In this csv table, `raw_word` column stands for words in the raw form, while `stanza` is the words processed by python library "stanza". For silent words, `stanza` entry stands for the punctuations or \<blank\>.

### sound.md

This file explains how each prosody tag sounds like.

---

### Special Notifications:

We found 4 utterances in LJspeech that appear to have non-corresponding transcript and speech. They are:

* LJ014-0165
* LJ031-0175
* LJ034-0138
* LJ048-0289

which are left out for our experiments. Hence the the taggings don't contain words in these four utterances.

Then, there are 11975 utterances, containing 241413 words in total, including all silent words.

