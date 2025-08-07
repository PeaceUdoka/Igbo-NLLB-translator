# Training an Igbo Translation Model Using NLLB-200-600M

### Objective: 
The goal of this notebook is to train an Igbo translation model using the NLLB-200-600M model and evaluate its performance against manual Igbo translations.

### Data: 
The training data consisted of a parallel corpus of about 1400 English texts and their manual Igbo translations, sourced from two Excel files (English T2.xlsx and English T6.xlsx).

### Process:
<b> Setup:</b> Necessary libraries for natural language processing and evaluation (sacrebleu, rouge-score, nltk, transformers, torch, pandas, numpy) were installed and imported.

<b> Data Loading and Preparation: </b> The data was loaded from the two Excel files. The dataframes were inspected for null values and merged. A new dataframe data was created containing only the "English Language" and "Igbo" columns. Null values were dropped from the individual dataframes before concatenation.

<b> Model Loading: </b> The facebook/nllb-200-distilled-600M model was specified as the translation model. The source language was set to English (eng_Latn) and the target language to Igbo (ibo_Latn) for translation from English to Igbo.

<b> Translation: </b> A translation pipeline was created using the specified model and languages. The English texts from the prepared data were translated into Igbo using this pipeline. The NLLB translations were added as a new column "Igbo_nllb_trans" to the data dataframe.

<b> Evaluation: </b> A comprehensive evaluation of the NLLB translations was performed against the manual Igbo translations using several metrics:

BLEU (Bilingual Evaluation Understudy)
chrF (Character F-score)
ROUGE (Recall-Oriented Understudy for Gisting Evaluation)
Exact Match Percentage

<b> Analysis: </b> The results of the evaluation were summarized, and the best and worst performing translations (based on BLEU score) were analyzed and printed. The detailed evaluation results were also saved to a CSV file (igbo_nllb_evaluation.csv).

### Conclusion:
The NLLB-200-600M model shows promising results for English-Igbo translation, achieving a good average BLEU score on this dataset. However, there are clear areas for improvement, as evidenced by the low scores on some individual translations. Further analysis of the worst-performing examples and potentially fine-tuning the model on a larger or more diverse Igbo parallel corpus could help address these limitations and improve the model's performance on challenging sentences.
