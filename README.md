# finetune_bert_on_squad
Fine-tuning of bert-base-uncased on SQuAD dataset  

## Platform
Google Collab

## Programming Language
Python

## Libraries
PyTorch, Transformers, Pandas, Numpy

## Description / Goals
The purpose of this project is to develop a simpler and lighter version of the official Hugging face example [Fine-tuning a model on a question-answering task](https://github.com/huggingface/notebooks/blob/master/examples/question_answering.ipynb) where `distilbert-base-uncased` is trained on the SQuAD dataset.
In order to achieve that we use a smaller part of the [SQuAD 2.0 dataset](https://rajpurkar.github.io/SQuAD-explorer/) (86821 samples of the `train-v2.0.json` dataset and 10388 samples of the `dev-v2.0.json` dataset)  on which we fine-tune the `bert-base-uncased` model. 

## Loss Progress

| Epoch	| Training Loss | Validation Loss	| Runtime	| Samples Per Second |
| --- | :---: | :---: | :---: | :---: |
| 1	| 1.098700	| 1.531850	| 137.695900	| 77.047000 |
| 2	| 0.809400	| 1.536165	| 137.723300	| 77.031000 |
| 3	| 0.590700	| 1.697627	| 137.694000	| 77.048000 |

## Prediction Example

**Question:** When were the Normans in Normandy? <br>

<pre><code># first squad answer for the question: When were the Normans in Normandy?
test_dataset[1]

{'Id': '56ddde6b9a695914005b9629',
 '__index_level_0__': 4,
 'ans_start': 94,
  'context': 'The Normans (Norman: Nourmands; French: Normands; Latin: Normanni) were the people who in the 10th and 11th centuries gave their name to Normandy, a region in       France. They were descended from Norse ("Norman" comes from "Norseman") raiders and pirates from Denmark, Iceland and Norway who, under their leader Rollo, agreed to swear fealty to King Charles III of West Francia. Through generations of assimilation and mixing with the native Frankish and Roman-Gaulish populations, their descendants would gradually merge with the Carolingian-based cultures of West Francia. The distinct cultural and ethnic identity of the Normans emerged initially in the first half of the 10th century, and it continued to evolve over the succeeding centuries.',
 'question': 'When were the Normans in Normandy?',
 'text': '10th and 11th centuries',
 'title': 'Normans'}</code></pre>

<pre><code># second squad answer for the question: When were the Normans in Normandy?
test_dataset[2]

{'Id': '56ddde6b9a695914005b9629',
 '__index_level_0__': 5,
 'ans_start': 87,
 'context': 'The Normans (Norman: Nourmands; French: Normands; Latin: Normanni) were the people who in the 10th and 11th centuries gave their name to Normandy, a region in France. They were descended from Norse ("Norman" comes from "Norseman") raiders and pirates from Denmark, Iceland and Norway who, under their leader Rollo, agreed to swear fealty to King Charles III of West Francia. Through generations of assimilation and mixing with the native Frankish and Roman-Gaulish populations, their descendants would gradually merge with the Carolingian-based cultures of West Francia. The distinct cultural and ethnic identity of the Normans emerged initially in the first half of the 10th century, and it continued to evolve over the succeeding centuries.',
 'question': 'When were the Normans in Normandy?',
 'text': 'in the 10th and 11th centuries',
 'title': 'Normans'}</code></pre>

<pre><code># model's predicted answer for the question: When were the Normans in Normandy?
predictions[1]

{'id': '56ddde6b9a695914005b9629',
 'prediction_text': '10th and 11th centuries'}</code></pre>

## Metrics Score

| Exact Match | F1-Score |
| --- | :---: |
| 62.53% | 78.28% |

## Tips
Add the `train-v2.0.json` and `dev-v2.0.json` datasets in your `gdrive/My Drive/Colab Notebooks/` path to execute correctly

Suggested Runtime Type: GPU

## Author
Vassilis Panagakis

