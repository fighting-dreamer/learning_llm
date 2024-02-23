## Common NLP tasks

1. Summarization
2. Sentiment Analysis
3. Translation
4. Zero Shot classification
5. Few shot learning

1. Conversation/chat
2. (Table)Question Answering
3. Text/token classification
4. text Generation

## Task : Sentiment Analysis

Example a stock market analysis app : I want to monitor stock market and want to use twitter commentry as an early indicator of trends.

the input to the model can be a comment on twitter and it can classify it as postive or negtive for a stock and can also assign a score.
```
comment 1 : new for subscribers, analyst continue to upgrade for hopes of rebound
comment 2 : <company> stock price target cut to $54 vs $55 at bofP merril lynch.
{
    output: [
        {label: postive, score:0.997},
        {label: negtive, score:0.996}
        ...
    ]
}
```

## Task : Translation
```python
en_to_es_translator = pipeline(
    task="text2text-generation", # task of variable length
    model="Helsinki-NLP/opus-mt-en-es") # translates english to spanish

en_to_es_translator("Existing, open source models...")
# output : [{"translated_text":"Los models existentes, de co'digo abierto..."}]
```
> General model may support multiple languages and may require prompts and instructions
```python
t5_translator("translate English to Romanian: Existing, open source models...")
```

## Task : Zero-shot classification
Example App : News browser 
Categorize articles with a custom set of topic labels, using existing LLM

example : 
1. Simon Favaro got crucial try with last move of the game, following earlier touchdowns... ===> Sport
2. The full cost of damage in Newton stewwort, oen of the worst areas that got effected ===> Breaking news

```python
predicted_label = zero_shot_pipeline(
    sequences=articles,
    candidate_labels=["politics", "breaking_news", "sports"])
```

## Task : Few-shot learning

Idea is to show the model what we want with examples. ie instead of fine-tuning the model for a task, we show examples and let the llm do the rest.

```python
pipeline(
    """For each tweet, describe the sentiment: [Instruction] 
        [Tweet]: "I hate it when my phone battery dies."
        [Sentiment] : Negtive
        ###
        [Tweet]: "My day have been :ok_hand:
        [Sentiment]: Postive
        ###
        [Tweet]: "This is the link to an article"
        [Sentiment] : Neutral
        ###
        [Tweet]: "This new musics vedio was incredible"
        [Sentiment]: """ # query to the answer this sentiment
)