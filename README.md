<H3>NAME: G Jayanth</H3>
<H3>REG NO.: 212221230030</H3>
<H3>EX.NO.6</H3>
<H3>DATE: 27.04 2024</H3>
<H1 ALIGN =CENTER>Implementation of Semantic ANalysis</H1>
<H3>Aim: </H3>
To perform Parts of speech identification and Synonym using Natural Language Processing (NLP) techniques.  
 <BR>
<H3>Algorithm:</H3>
Step 1: Import the nltk library.<br>
Step 2: Download the 'punkt', 'wordnet', and 'averaged_perceptron_tagger' resources.<br>
Step 3:Accept user input for the text.<br>
Step 4:Tokenize the input text into words using the word_tokenize function.<br>
Step 5:Iterate through each word in the tokenized text.<br>
•	Perform part-of-speech tagging on the tokenized words using nltk.pos_tag.<br>
•	Print each word along with its corresponding part-of-speech tag.<br>
•	For each verb , iterate through its synsets (sets of synonyms) using wordnet.synsets(word).<br>
•	Extract synonyms and antonyms using lemma.name() and lemma.antonyms()[0].name() respectively.<br>
•	Print the unique sets of synonyms and antonyms.

## PROGRAM:
```
Name: G Jayanth.
Reg. No: 212221230030.
```

```python
import nltk
from nltk.corpus import wordnet

nltk.download('averaged_perceptron_tagger')
nltk.download('wordnet')
nltk.download('punkt')

# Function to identify verbs in a sentence
def get_verbs(sentence):
    verbs = []
    pos_tags = nltk.pos_tag(nltk.word_tokenize(sentence))
    for word, tag in pos_tags:
        if tag.startswith('V'):  # Verbs start with 'V' in the POS tag
            verbs.append(word)
    return verbs


def get_synonyms(word):
    synonyms = []
    for syn in wordnet.synsets(word):
        for lemma in syn.lemmas():
            synonyms.append(lemma.name())
    return synonyms


def read_text_file(file_path):
    with open(file_path, 'r') as file:
        text = file.read()
    return text


def main():
    file_path = 'sample.txt'

    text = read_text_file(file_path)
    sentences = nltk.sent_tokenize(text)

    all_verbs = []
    synonyms_dict = {}

    for sentence in sentences:
        verbs = get_verbs(sentence)
        all_verbs.extend(verbs)
        for verb in verbs:
            synonyms = get_synonyms(verb)
            synonyms_dict[verb] = synonyms

    with open('output.csv', 'w', newline='') as csvfile:
        writer = csv.writer(csvfile)
        writer.writerow(['Verb', 'Synonyms'])
        for verb, synonyms in synonyms_dict.items():
            writer.writerow([verb, ', '.join(synonyms)])


if __name__ == '__main__':
    main()
```

## OUTPUT :
|Verb|Synonyms|
|---|---|
|Managing|pull\_off, negociate, bring\_off, carry\_off, manage, manage, deal, care, handle, cope, get\_by, make\_out, make\_do, contend, grapple, deal, manage, oversee, supervise, superintend, manage, wangle, finagle, manage, do, manage, wield, handle, manage|
|requires|necessitate, ask, postulate, need, require, take, involve, call\_for, demand, ask, require, expect, command, require, want, need, require|
|refers|mention, advert, bring\_up, cite, name, refer, refer, pertain, relate, concern, come\_to, bear\_on, touch, touch\_on, have-to\_doe\_with, refer, refer, consult, refer, look\_up, denote, refer, refer|
|be|beryllium, Be, glucinium, atomic\_number\_4, be, be, be, exist, be, be, equal, be, constitute, represent, make\_up, comprise, be, be, follow, embody, be, personify, be, be, live, be, cost, be|
|targeted|target, aim, place, direct, point|
|expand|expand, spread\_out, expand, expand, boom, thrive, flourish, expand, inflate, blow\_up, expand, amplify, elaborate, lucubrate, expatiate, exposit, enlarge, flesh\_out, expand, expound, dilate, extend, expand|
|grows|turn, grow, grow, grow, grow, mature, maturate, grow, originate, arise, rise, develop, uprise, spring\_up, grow, grow, raise, farm, produce, grow, develop, produce, get, acquire, develop, grow, grow|
|presenting|show, demo, exhibit, present, demonstrate, present, represent, lay\_out, stage, present, represent, present, submit, present, pose, award, present, give, gift, present, deliver, present, introduce, present, acquaint, portray, present, confront, face, present, present, salute, present|
|mitigating|extenuate, palliate, mitigate, mitigate|
|safeguarding|safeguard, safeguard|
|demands|demand, demand, requirement, demand, demand, need, demand, demand, necessitate, ask, postulate, need, require, take, involve, call\_for, demand, demand, exact, demand, demand, demand|
|tailored|tailor, orient, cut, tailor, sew, tailor, tailor-make, tailored, trim, bespoke, bespoken, made-to-order, tailored, tailor-made|
## RESULT :

Thus, we have successfully implemented a program for Natural Language Processing.
