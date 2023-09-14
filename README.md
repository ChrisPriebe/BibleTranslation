# Use GPT (from openAI) to translate the Bible


## Experiments

### Given an English text translate it to our cipher text

train_prepared.jsonl
```
{"prompt":"The book of the generations of Jesus Christ, the son of David, the son of Abraham.\n\n###\n\n","completion":" Lxi fuuc us lxi girivelourz us Yizaz Kxvozl, lxi zur us Wemow, lxi zur us Efvexen.\n###"}
```

Do the same but use Exodus instead of the gospels
train_exp_exo_prepared.jsonl
```
{"prompt":"Now these are the names of the sons of Israel, who came into Egypt (every man and his household came with Jacob):\n\n###\n\n","completion":" Ruh lxizi evi lxi reniz us lxi zurz us Ozveip hxu keni orlu Igjql; imivj ner erw xoz senopj keni holx Yekuf.\n###"}

```

### Reference only with task
Assume the reference is 'pregnant' with meaning and just get it to translate it

train_exp1.jsonl
```
{"prompt":"Matthew 1:1 from the Bible in the Berrig language says, \"","completion":" Lxi fuuc us lxi girivelourz us Yizaz Kxvozl, lxi zur us Wemow, lxi zur us Efvexen.\"\n###"}

```

In theory we thought that it could map just from the reference b/c it shows that on devinci it knows the verse.  So in theory it should have all the versions of that text, all the sermons and all the commentaries and comments about it embedded into it.  But when asked for that verse after training it then it doesn't know it so it appears to not be packaging all those findings with it


Likewise just the reference no instructions
train_exp1_prepared.jsonl
```
{"prompt":"Matthew 1:1 from the Bible in the Berrig language says, \"","completion":" Lxi fuuc us lxi girivelourz us Yizaz Kxvozl, lxi zur us Wemow, lxi zur us Efvexen.\"\n###"}
```
```
{"prompt":"mat 1:1\n\n###\n\n","completion":" Lxi fuuc us lxi girivelourz us Yizaz Kxvozl, lxi zur us Wemow, lxi zur us Efvexen.\n###"}
```

We did a second attempt where we set the prompt to John 3:16 in the Bible says, " but even at that it was confused and we could not extract the internal knowledge in fine tuning only in directly calling it.

### Encode english with substitution cipher to create new language, given Matthew, Luke, John can we predict Mark?


### Avoid word to word translation by using alternate versions
Given other versions (web, asv, kjv2006) as inputs use the text from BBE (encoded) as the completion.  This should simulate a non-word to word translation

For example
INPUT: WEB -> "In the beginning, God created the heavens"
EXPECTS: BBE -> decode(encode("At the first God made the heaven and the earth"))

 - [ ] web -> BBE
 - [ ] web, asv, kjv2006 -> BBE