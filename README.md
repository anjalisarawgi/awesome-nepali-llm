# awesome-nepali-llm : [![Awesome](https://awesome.re/badge-flat.svg)](https://awesome.re)

### Awesome Nepali NLP🇳🇵

> Inspired by [awesome-cultural-nlp](https://github.com/simran-khanuja/awesome-cultural-nlp) 

#### Nepali Language Specifics

## Table of Contents
- [Datasets](#datasets)
- [Pretrained Models](#pretrained-models)
- [Tasks](#tasks)
- [Research Papers](#research-papers)
- [Applications](#applications)
- [Notes](#applications)
- [Contributions](#contributions)

## Nepali Language Specifics (source: [wikipedia](https://en.wikipedia.org/wiki/Nepali_language))
- Speakers: 32 million
- Language Family: Indo Aryan family (more specifically, Eastern Pahari)
- Currently majorly spoken in: Nepal, India (Sikkim, West Bengal)
- Language code: ne, nep, npi
- Script: Devangiri Script

## Old Nepali vs Modern Nepali
1. Old Nepali (Prachin Nepali)
- A version of Khasa Prakrit
- Heavily dependent on Classical Sanskrit
- It retained many formal or classical terms which are not common in modern usage
- Usually used in legal, religous or political documents
- Very complex in structure and high honorfics (formalities)
- Uses Devangiri Script variations and spellings

3. Modern Nepali
- The next step from Khasa Prakrit
- Has alot of similar words from Hindi, English too
- Has formalized and standardized variations and spellings whichsmakes it simpler

Note: Khara Prakrit is a language build from sanskrit
## Datasets

| Title | Source | Paper | Use Case | Notes | Size |
|-------|--------|-------|------|----------|-------|
| **Nepali Text Corpus** | [IRIIS Nepal / Nepali Text Corpus on Hugging Face](https://huggingface.co/datasets/IRIISNEPAL/Nepali-Text-Corpus) | N/A | A monolingual corpus, possibly to train the model better for understanding Nepali language| (first step for indic models)| 6.4 million articles |
| **XL-Sum Nepali Summarization Dataset** | [sanjeev-bhandari01/XL-Sum-nepali-summerization-dataset on Hugging Face](https://huggingface.co/datasets/sanjeev-bhandari01/XLSum-nepali-summerization-dataset) | N/A   | Summarization and text generation          | Contains labeled summary data which is useful for summarization training (title, text, summary) | 7,258 rows |
| **FLORES** | 
| **Common Crawl Oscar Corpus** | 
| **IndicCorp** | 
| **check Muril** | 
## Pre trained models

| Title | Paper | Source | Training Data | Task Strengths | Fine-Tuning |  Limitations | Size | Notes | 
|-------|------|-------|----------|----------|----------| ----------| ----------| -------| 
| **indicBERT** ✅| [https://arxiv.org/abs/2212.05409](https://arxiv.org/abs/2212.05409) | AI4Bharat | 22 languages (including Nepali), indicCorp (monolingual text mostly) |  MLM and TLM, NER, classification, QA | | Non generative, limited focus on Nepali | | A solid baseline model to start with | |
| **indicBART** |  [https://arxiv.org/abs/2109.02903](https://arxiv.org/abs/2109.02903) | AI4Bharat | 11 languages (not Nepali)| Translation, Summarization | Finetune on Nepali tasks for summarization or translation | Nepali is not a part of the training data | | Testedm and not good since it has seen no nepali data during training |
| **MuRIL** ✅ ✅ | [https://arxiv.org/abs/2103.10730](https://arxiv.org/abs/2103.10730) | Google | 17 languages (includes Nepali) (translations, transilerations, code-mixed data) | MLM and TLM , translated and transilerated pairs, built on the BERT model, contains english texts too|  NER, classification, QA | | Outperforms mBERT, trained on english too helping with modern nepali, has cross lingual capabilities 
| **mT5** | |  | | | ||||| |
| **byT5 (dharmamitra model)** | |  | | | ||||| |
| **XLM-RoBERTa** | |  | | | ||||| |
| **mBERT** | |  | | | ||||| |
| **BART** | |  | | | ||||| |
| **LLAMA3** | https://arxiv.org/abs/2407.21783 | Meta | Multilingual and includes English, Hindi, though Nepali is limited in representation + also can be combined for image, video and speech capabilities | Handles complex tasks and nuances, efficient cross lingual transfer | Cross lingual finetuning to make it better for Modern nepali | Very Resource intensive | 8B / 70B / 405B| powerful but resource intensive |


## Tasks
| Models | Tasks and Capabilities | Limitations | Personal Notes |
|-------|--------|-------|-------|
| BERT and BERT Variants (MuRIL, IndicBERT) | Tasks that require indepth understanding of Texts (classification, NER, Q and A) | Not a Generative model for texts | Useful for this task |
| GPT (GPT-2, GPT-3) | Language Generations, creative writing, summarizations | Not designed for NERs | Not for the scope of this project|
| LLAMA | For text generation | not for trained for Nepali or multiple languages and is very resource extensive | Not for the scope of this project but could be explored once |
| Multilingual Models (XLM-RoBERTa, mBERT, mT5) | Understanding and generating text in multiple languages, cross linfual understanding and translations | They may not capture the nuances of each individual languages deeply, as monolingual models since they are trained on a vast set of languages| Could be leveraged if indic models don't work|
| mT5 | Text generations tasks like translations, summarization, question answering etc on multiple languages | may not be as good as a T5 model | not sure if its for the scope of this project (but the finetuning results still are impressive) | 
| XLM-RobERTa | Classification, NER, QA  - powerful cross lingual understanding | Not designed for tex generation | Useful for this project | 
| Indic Models (indicBART, indicBERT) | Trained on Indo Aryan Language family only, so more focused  | Contains Nepali data, but not focused on Nepali language training | Most preffered in theory, but the tunings results so far are not the best|
| Specialized Models (Dharmamitra for Sanskrit (byt5-- not sure), MuRIL for Indian Languages) | Very good for morphological understanding | needs alot of computational resources | Useful for this task -- MuRIL is also trained on english which helps with multiple language tasks |
