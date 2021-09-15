

## 🧐 About <a name = "about"></a>

tunbert_zied is language model for the tunisian dialect based on a similar architecture to the RoBERTa model created BY zied sbabti.

The model was trained for over 600 000 phrases written in the tunisian dialect. 

## 🏁 Getting Started <a name = "getting_started"></a>

Load <strong>tunbert_zied</strong> and its sub-word tokenizer

Don'use the <em>AutoTokenizer.from_pretrained(...)</em> method to load the tokenizer, instead use <em>BertTokeinzer.from_pretrained(...)</em> method. (this is because I haven't use the bultin tokenizer of roberta model which is the GPT tokenizer, instead i have used BertTokenizer)

### Example



```
import transformers as tr

tokenizer = tr.BertTokenizer.from_pretrained("ziedsb19/tunbert_zied")

model = tr.AutoModelForMaskedLM.from_pretrained("ziedsb19/tunbert_zied")

pipeline = tr.pipeline("fill-mask", model= model, tokenizer=tokenizer)

#test the model by masking a word in a phrase with [MASK]

pipeline("Ahla winek [MASK] lioum ?")

#results 
"""
[{'sequence': 'ahla winek cv lioum?',
  'score': 0.07968682795763016,
  'token': 869,
  'token_str': 'c v'},
 {'sequence': 'ahla winek enty lioum?',
  'score': 0.06116843968629837,
  'token': 448,
  'token_str': 'e n t y'},
 {'sequence': 'ahla winek ch3amla lioum?',
  'score': 0.057379286736249924,
  'token': 7342,
  'token_str': 'c h 3 a m l a'},
 {'sequence': 'ahla winek cha3malt lioum?',
  'score': 0.028112901374697685,
  'token': 4663,
  'token_str': 'c h a 3 m a l t'},
 {'sequence': 'ahla winek enti lioum?',
  'score': 0.025781650096178055,
  'token': 436,
  'token_str': 'e n t i'}]
"""
```

## ✍️ Authors <a name = "authors"></a>

- [zied sbabti](https://www.linkedin.com/in/zied-sbabti-a58a56139) - Idea & Initial work

