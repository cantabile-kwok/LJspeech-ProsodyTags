# LJspeech-ProsodyTags

### **Tree-Based Word-Level Prosody Clustering and Direct Control for Neural Text-To-Speech**

Yiwei Guo, Chenpeng Du, Kai Yu

cantabile_kwok@sjtu.edu.cn



This repository is for the prosody tags in LJspeech (https://keithito.com/LJ-Speech-Dataset/) we obtain in our paper. There are two csv-formatted files:

### **leaf_tag_all.csv**

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
