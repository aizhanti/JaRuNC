# Japanese--Russian--English News Commentary Parallel Data

## Introduction

This repository contains manually curated parallel sentences for Japanese--Russian, Japanese--English, and Russian--English language pairs in news domain.

## Contents

The Japanese--Russian is one of the most distant language pairs and has only limited quantity of parallel data to train machine translation (MT) systems.
To promote the research on low-resource MT, we have curated parallel sentences, which can be used as development and test data, through the following procedure:

1. Downloaded from [OPUS](http://opus.nlpl.eu/) News Commentary data for [Japanese--Russian](http://opus.nlpl.eu/download.php?f=News-Commentary11/ja-ru.txt.zip) with 586 sentence pairs and [Japanese--English](http://opus.nlpl.eu/download.php?f=News-Commentary11/en-ja.txt.zip) with 637 sentence pairs.
2. The above Japanese--Russian and Japanese--English data share many lines in the Japanese side. Therefore, we first compiled a Russian--Japanese--English tri-text data.
3. From each line, we identified corresponding parts across languages, and split off unaligned parts into a new line.
4. As a result, we obtained 1,654 lines of data comprising trilingual, bilingual, and monolingual segments (mainly sentences).
5. For the sake of comparability, we randomly chose 600 trilingual sentences to create a test set, and concatenated the rest of them and bilingual sentences to form development sets.

### Distribution of tri-texts

| Ru | Ja | En | #sent | Test | Dev  |
| :--: | :--: | :--: | ----: | ---: | ---: |
| ✓  | ✓  | ✓  | 913   | 600  | 313  |
| ✓  | ✓  |  - | 173   | -    | 173  |
| -  | ✓  |  ✓ | 276   | -    | 276  |
| ✓  | -  |  ✓ | 0     | -    | -    |
| ✓  | -  |  - | 4     | -    | -    |
| -  | ✓  |  - | 287   | -    | -    |
| -  | -  |  ✓ | 1     | -    | -    |

### Development and test splits (available in this repository)

| L1--L2 | Development | Test |
| :---------------- | --: | --: |
| Japanese--Russian | 486 | 600 |
| Japanese--English | 589 | 600 |
| Russian--English  | 313 | 600 |

## Benchmarking

Scoreboard (BLEU-cased)

| System description | Resources Used | Ja-to-Ru | Ru-to-Ja |
| :----- | :----- | ---: | ---: |
| Uni-directional Transformer NMT | (a) | 0.70 | 1.96 |
| Multi-to-multi Transformer NMT involving English | (a) | 3.72 | 8.35 |
| Same but with multi-lingual multi-stage fine-tuning | (a) (b) (c) (d) | 7.49 | 12.10 |

Data used for above systems are as follows:

(a) Global Voices parallel data retrieved from [OPUS](http://opus.nlpl.eu/GlobalVoices-v2015.php) (v2015; included in this repository)

(b) [ASPEC](http://lotus.kuee.kyoto-u.ac.jp/ASPEC/): Asian Scientific Paper Excerpt Corpus (out-of-domain Japanese--English parallel data)

(c) [UN](http://www.statmt.org/wmt18/translation-task.html) provided for WMT 18 (out-of-domain Russian--English parallel data)

(d) [Yandex](http://www.statmt.org/wmt18/translation-task.html) provided for WMT 18 (out-of-domain Russian--English parallel data)

## References

* Aizhan Imankulova, Raj Dabre, Atsushi Fujita, and Kenji Imamura. Exploiting Out-of-Domain Parallel Data through Multilingual Transfer Learning for Low-Resource Neural Machine Translation. In Proceedings of the 17th Machine Translation Summit (MT Summit), Aug., 2019. (to appear). [arXiv version](https://arxiv.org/abs/1907.03060)

## Precautions

* National Institute of Information and Communications Technology (henceforth, NICT) has made the database publicly available under the conditions of license specified below.
* NICT bears no responsibility for the contents of the database and assumes no liability for any direct or indirect damage or loss whatsoever that may be incurred as a result of using the database.
* If any copyright infringement or other problems are found in the database, please contact us at atsushi.fujita[at]nict[dot]go[dot]jp. We will review the issue and undertake appropriate measures when needed.

## License

No claims of intellectual property are made on the work of preparation of the corpus.
See the [OPUS](http://opus.nlpl.eu/News-Commentary-v11.php) and/or [CASMACAT](http://www.casmacat.eu/corpus/news-commentary.html) for details.

## Acknowledgments

The dataset has been developed as a part of work at [Advanced Translation Technology Laboratory](http://att-astrec.nict.go.jp/), [Advanced Speech Translation Research and Development Promotion Center](http://astrec.nict.go.jp/), [National Institute of Information and Communications Technology](http://www.nict.go.jp/en/).
