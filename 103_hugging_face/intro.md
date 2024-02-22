## Hugging Face

The hugging face hosts :

1. Models
2. Datasets
3. Spaces for demos and code.

Key libraries include :

`datasets` : Download datasets from hub

`transformers` : work with pipelines, tokenizers, models etc...

`evaluate` : compute evaluation metrics

under the hood these libraries can use pytorch, tensorflow and JAX.

> LLM pipeline using hugging face 
```python
from transformers import pipeline
summarizer = pipeline("Summarizer")
summarizer("A magnitude 6.7 earthquake rattled ...")
```
here hugging face is trying to understand hte right encoding and choosing hte right model and giving the output.

you can customize it :

> stage 1 : 

1. prompt construction (Optional)
    
    example : `summarize :"A magnitude 6.7 earthquake rattled .."`

> stage 2 :

1. Tokenizer (encoding) : comverting the input to tokens vector

``` python
from transformers import Autotokenizer

# load compatible tokenizer
tokenizer = Autotokenizer.from_pretrained("<model_name>")
inputs = tokenizer(articles, 
                    max_length=1024, # forces variable length text to fixed length tensors.
                    padding=True
                    truncation=True
                    return_tensors="pt")
# max_length, padding, truncation are customizations, can depend on the relevant model in use.
# pt => we are saying that we are using pytorch.
```

> stage 3 :

1. model/llm processing it

```python
from transformers import AutoModelForSeq2SeqLM

model = AutoModelForSeq2SeqLM.from_pretrained("<model_name>")
summary_ids = model.generate(
    inputs.input_ids,
    attention_mask=inputs.attention_mask, # handles variable length inputs
    num_beams=10, # model search for best output
    min_length=5, # adjust output length to match task.
    max_length=40)
```

> stage 4 :

1. tokenizer decoding : converting model llm output to a suitable human usable/meaningful value.

> Datasets library

- 1-line api for loading or sharing datasets.
- NLP, audio, vision tasks.

```python
from datasets import load_dataset
xsum_dataset = load_dataset("xsum", version="1.2.0")
```

> Dataset is hosted by hugging face hub

- filter by task, size, licence, language etc...
- find related models.