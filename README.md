# awesome-nepali-llm : [![Awesome](https://awesome.re/badge-flat.svg)](https://awesome.re)

### Awesome Nepali NLP🇳🇵

> Inspired by [awesome-cultural-nlp](https://github.com/simran-khanuja/awesome-cultural-nlp) 

#### Nepali Language Specifics

## Table of Contents
- [Datasets](#datasets)
- [Pretrained Models](#pretrained-models)
- [Tasks](#tasks)
- [Notes on Model Selection](#Noteson-Model-Selection)
- [IndicBERT for Nepali](#indic-bert-for-Nepali)
- [MuRIL for Nepali](#muril-for-Nepali)
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
| **IndicCorpV2** | 
| **mC4** | 
| **sangraha (sanskrit & Nepali)** | 
| **Samanantar(flores)** |
| **indic-align(indicLLMSuite)** |
| **wiki-translate(indicLLMSuite)** |
| **wiki-transilerate(indicLLMSuite)** |
| **check Muril** | 
| **check ariavata evaluation suite**|

## Pre trained models

| Title | Paper | Source | Training Data | Task Strengths | Fine-Tuning |  Limitations | Size | Notes | 
|-------|------|-------|----------|----------|----------| ----------| ----------| -------| 
| **indicBERT** ✅| [paper](https://arxiv.org/abs/2212.05409) | AI4Bharat | 22 languages (including Nepali), indicCorp (monolingual text mostly) |  MLM and TLM, NER, classification, QA | | Non generative, limited focus on Nepali | | A solid baseline model to start with, much lighter than mT5| |
| **indicBART** |  [paper](https://arxiv.org/abs/2109.02903) | AI4Bharat | 11 languages (not Nepali) (generative model) | Translation, Summarization | Finetune on Nepali tasks for summarization or translation | Nepali is not a part of the training data | | Testedm and not good since it has seen no nepali data during training |
| **mBART**  ✅ |  [paper](https://arxiv.org/abs/2001.08210)]| Facebook | 25 languages (including Nepali) (generative model) | Translation, Summarization | Finetune on Nepali tasks for summarization or translation | Nepali is a part of the training data | | Not tested yet, but a good starting point for generative tasks  |
| **MuRIL** ✅ ✅ | [paper](https://arxiv.org/abs/2103.10730) | Google | 17 languages (includes Nepali) (translations, transilerations, code-mixed data) | MLM and TLM , translated and transilerated pairs, built on the BERT model, contains english texts too|  NER, classification, QA | Outperforms mBERT, trained on english too helping with modern nepali, has cross lingual capabilities (cross lingual capabilities) | | Most ideal starting point
| **byT5 (dharmamitra model)** ✅ | [paper](https://arxiv.org/abs/2409.13920)| Dharmamitra, BAIR | Mixed quality sanskrit text data, OCR text, high quality sanskrit corpora|Word segmentation, lemmatization, morphosyntactic tagging, dependency parsing, OCR correction | Fine tune on old nepali tasks (sanskrit references) | very resource intencve, slower processing due to byle level approach || Ideal for old nepali finetuning |
| **mT5** | [paper](https://arxiv.org/abs/2010.11934) | Google | Multilingual mC4 corpus, 101 languages including Nepali (also has english, useful for modern Neali) | NER, classification, QA (mt5 XXL outperforms mBERT on these tasks), Text generation, translation, summarization,| | Reosurce intensive; finetuned on many languages may deviate from the focus of Nepali ||The performace is decent, could be explored if indicBERT doesnt work, and could be used if our purpose is generative tasks |
| **LLAMA3** | [paper](https://arxiv.org/abs/2407.21783) | Meta | Multilingual and includes English, Hindi, though Nepali is limited in representation + also can be combined for image, video and speech capabilities | Handles complex tasks and nuances, efficient cross lingual transfer | Cross lingual finetuning to make it better for Modern nepali | Very Resource intensive | 8B / 70B / 405B| powerful but resource intensive |


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


## Notes on Model Selection
The models selected for the project will build upon **Indic models** to leverage their language-specific strengths, particularly for Nepali and Sanskrit (for Old Nepali). Below are some notes for each model:

### IndicBERT (Transformer-Based Model)
  - A solid choice for text understanding tasks.
  - Trained on Nepali corpus and supports Sanskrit, making it suitable for both modern and Old Nepali.
  - Fine-tuning may require multiple steps: initial fine-tuning on a large Nepali dataset, followed by task-specific fine-tuning.
  - As a BERT-based model, it’s highly suited for our case, which focuses on language understanding.
  - Non-generative, which may pose some limitations depending on task requirements.
  - Alternatives for this model would be MuRIL and / or mBART

### MuRIL
  - Includes English training data, enhancing multi-language understanding. This would be very useful for Modern Nepali
  - A suitable alternative for IndicBERT 
  - However, it doesn't train on alot a massive sanskrit dataset. And indicBERT may be better in this case

### ByT5 (Dharmamitra) 
  - Ideal for handling the morphological complexity of Old Nepali.

### mBART
  - If we need a generative model 


## IndicBERT for Nepali
| Model | Size | Dataset | Tested | Performance | Notes
|-------|------|-------|----------|----------|----------| 
| **IndicBERTv2-MLM-only** | 278M parameters| IndicCorp v2  | ✅ | Good for MLM | | 
| **IndicBERTv2-MLM-back_tlm** | 278M parameters | IndicCorp v2 (back translation using indicTrans)  | ✅ | Strong at English-Nepali multilingual tasks | Suitable  Nepali-English bilingual NLP |
| **IndicBERTv2-MLM-ss** | 278M parameters | IndicCorp v2  | ✅ | Script Sharing Capabilities | Nepali is already written in Devangiri Script |




## MuRIL for Nepali
| Model | Size | Dataset | Tested | Performance | Notes
|-------|------|-------|----------|----------|----------| 
| **MuRIL MLM Cased Temp** | |  | ✅ | Good for MLM | Since its good for MLM, might be useful for morphological learning | 
| **MuRIL Cased Temp** | |  | ✅ | Poor performance for MLM, NER (need to check), sentence class, | Not alot of focus on Nepali , maybe finetuning will be helpful; Recommended for feature extraction | 

---

### Summary
All of these models are based on the transformer architecture. To start, **IndicBERT** is a solid choice for tasks that require understanding Nepali and Sanskrit Texts. If we have generative tasks we could additionally add **mBART** too. 

We could also consider **MuRIL** because its good at handling multiple languages (English, Nepali, and Hindi) which could be helpful for modern Nepali because modern Nepali uses elements from English and Hindi. MuRIL also is comparable in performance with **indicBERT** in alot of tasks. And finally for old Nepali based tasks, the **ByT5-Sanskrit** model by Dharmamitra is a good choice. 
