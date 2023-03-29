# Use GPT (from openAI) to translate the Bible


## Experiments

### Encode english with substitution cipher to create new language, given Matthew, Luke, John can we predict Mark?


### Avoid word to word translation by using alternate versions
Given other versions (web, asv, kjv2006) as inputs use the text from BBE (encoded) as the completion.  This should simulate a non-word to word translation

For example
INPUT: WEB -> "In the beginning, God created the heavens"
EXPECTS: BBE -> decode(encode("At the first God made the heaven and the earth"))

 - [ ] web -> BBE
 - [ ] web, asv, kjv2006 -> BBE