# A Comparison of Various T5-based Models for Translating Arabic Dialectical Text to Modern Standard Arabic (NADI 2023)

The methods we developed for the Nuanced Arabic Dialect Identification (NADI) 2023 shared task, specifically targeting the two subtasks focused on sentence-level machine translation (MT) of text written in any of four Arabic dialects (Egyptian, Emirati, Jordanian and Palestinian) to Modern Standard Arabic (MSA).

## Abstract

This paper presents the methods we developed for the Nuanced Arabic Dialect Identification (NADI) 2023 shared task, specifically targeting the two subtasks focussed on sentence-level machine translation (MT) of text written in any of four Arabic dialects (Egyptian, Emirati, Jordanian and Palestinian) to Modern Standard Arabic (MSA). Our team, UniManc, employed models based on T5: multilingual T5 (mT5), multi-task fine-tuned mT5 (mT0) and AraT5. These models were trained based on two configurations: joint model training for all regional dialects (J-R) and independent model training for every regional dialect (I-R). Based on the results of the official NADI 2023 evaluation, our I-R AraT5 model obtained an overall BLEU score of 14.76, ranking first in the Closed Dialect-to-MSA MT subtask. Moreover, in the Open Dialect-to-MSA MT subtask, our J-R AraT5 model also ranked first, obtaining an overall BLEU score of 21.10.

## Table of Contents

- [Datasets](#datasets)
- [Usage](#usage)
- [Results](#results)
- [Citation](#citation)
- [Contributors](#contributors)

## Datasets

This section describes the datasets used to train our models.
### The MADAR Corpus

The MADAR corpus covers dialects from 25 Arabic-speaking cities, English, and MSA. 
> Reference: [bouamor-etal-2018-madar](https://camel.abudhabi.nyu.edu/madar-parallel-corpus/).

### Additional Corpora

For the open version of the dialect-to-MSA machine translation task, participants could use any dataset. We sourced datasets that covered various Arabic dialects, including regional ones related to the NADI challenge countries. Specifically, we used:
1. **PADIC** - Covers six Arabic cities including Gaza and Damascus from the Levant region.
   > Reference: [meftouh2018padic](https://huggingface.co/datasets/arbml/PADIC).
2. **Dial2MSA** - Consists of tweets in Arabic dialects with MSA translations, focusing on Egyptian and Maghrebi dialects.
   > Reference: [mubarakdial2msa](http://lrec-conf.org/workshops/lrec2018/W30/pdf/13_W30.pdf).
3. **Arabic STS** - Provides MSA, Egyptian, and Saudi dialect translations for English sentences.
   > Reference: [alsulaiman2022semantic](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0272991).
4. **Emi-NADI** - Our dataset to address the scarcity of Emirati dialect parallel corpora.
   > Reference: 

### Dataset Sizes

| **Dataset** | **Egy.** | **Gulf** | **Lev.** |
|-------------|----------|----------|----------|
| MADAR      | 13,800   | 15,400   | 18,600   |
| PADIC      | 0        | 0        | 12,824   |
| Dial2MSA   | 16,355   | 0        | 0        |
| Arabic STS | 2,758    | 2,758    | 0        |
| Emi-NADI   | 0        | 2,712    | 0        |
| **Total**  | 32,913   | 20,870   | 31,424   |

## Usage

### Requirements

```
- accelerate
- datasets
- sacrebleu
- sentencepiece
- evaluate
- rouge_score
- pandas
- numpy
- transformers==4.24.0
```

### Preprocessing

The datasets are loaded and preprocessed in the `DataPreparation.ipynb` .

### Training of Models

Model training occurs in `AraT5v2_DialecticalArabicToMSA_MT.ipynb` please ensure usage of the same version of the transformers library.

## Results

- The Independent Regional (I-R) models generally outperformed Joint Regional (J-R) models for Subtask 2, except in the Jordanian case.
- The I-R AraT5 model with a beam size of 3 showcased the highest performance for Subtask 2 with a score of 14.76.
- For Subtask 3, the J-R AraT5 model performed best with a score of 21.10 using a beam size of 1. Adjusting the beam size of this model to 5 in post-evaluation increased the score to 21.87.

## Citation

```bib
@inproceedings{abdul-mageed-etal-2023-nadi,
 title        = {{NADI 2023: The Fourth Nuanced Arabic Dialect Identification Shared Task}},
 author       = {Abdul-Mageed, Muhammad  and Elmadany, AbdelRahim and Zhang, Chiyu  and Nagoudi, ElMoatez Billah and Bouamor, Houda  and Habash, Nizar},
 year         = 2023,
 booktitle    = {Proceedings of The First Arabic Natural Language Processing Conference (ArabicNLP 2023)}
 }
```

```bib
@inproceedings{khered2023unimanc,
 title = {UniManc at NADI 2023 Shared Task: A Comparison of Various T5-based Models for Translating Arabic Dialectical Text to Modern Standard Arabic},
 author = {Khered, Abdullah Salem and Abdelhalim, Ingy Yasser and Abdelhalim, Nadine and Soliman, Ahmed and Batista-Navarro, Riza},
 booktitle = {Proceedings of the SIGARAB ArabicNLP 2023 Conference},
 year = {2023},
 month = {Sept},
 abstract = {This paper presents the methods we developed for the Nuanced Arabic Dialect Identification (NADI) 2023 shared task, specifically targeting the two subtasks focussed on sentence-level machine translation (MT) of text written in any of four Arabic dialects (Egyptian, Emirati, Jordanian and Palestinian) to Modern Standard Arabic (MSA). Our team, UniManc, employed models based on T5: multilingual T5 (mT5), multi-task fine-tuned mT5 (mT0) and AraT5. These models were trained based on two configurations: joint model training for all regional dialects (J-R) and independent model training for every regional dialect (I-R). Based on the results of the official NADI 2023 evaluation, our I-R AraT5 model obtained an overall BLEU score of 14.76, ranking first in the Closed Dialect-to-MSA MT subtask. Moreover, in the Open Dialect-to-MSA MT subtask, our J-R AraT5 model also ranked first, obtaining an overall BLEU score of 21.10.}
}

```

## Contributors

1. Abdullah Salem Khered
2. Ingy Yasser Abdelhalim
3. Nadine Abdelhalim
4. Ahmed Soliman
5. Riza Batista-Navarro
