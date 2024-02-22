## Natural Language Processing (NLP)

> Use cases of Natural Language Processing : 

1. Sentiment Analysis
2. Translation
3. Question Answering : chatbots
4. Sementic similarity
   1. Literature search
   2. Database querying
   3. Question-answer matching
5. Summarization
   1. clinical decision support
   2. news article sentiments
   3. legal proceeding summary
6. Text classification
   1. customer review sentiments
   2. Genre/topic classification

> Some terms 

1. Token : building blocks
   1. the
   2. moon
   3. Earth's
   4. Only...
2. Sequence : list of tokens
   1. The moon
   2. Earth's only natural satellite
   3. ...
3. Vocabulary : complete list of tokens
   1. { 1 : The, 565 : moon....}

> After these definitions the above tasks are like 

1. Translation = Sequence to sequence prediction
2. Sentiment analysis : Sequence to non-sequence prediction
3. Question Answering : Sequence to sequence generation

> NLP beyond text

Speech recognition
Image caption generation
Image generation from text

> Text interpretation is challenging

1. language is ambigious
2. context can change the meaning
3. there can be multiple good answers

- input data formats matter a lot : lot of work have gone into text representation for NLP.
- model size matters : big models help in capturing the diversity and complexity of human language.
- training data matters : it helps to have high quality of data nad lots of it.