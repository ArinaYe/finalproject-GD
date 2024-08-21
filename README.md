I. Introduction of BA construction
------
My project is aiming to realize the BA construction in Mandarin Chinese using the XLE system. BA construction is a special linguistic phenomenon in Mandarin Chinese, which puts emphasis on the NP (object), and places the object before the verb, thus form a SOV structure. Here is a simple example of the BA construction:
```
(1) a. Tom  ba  neige  pingguo  chi  le.  
       Tom  BA  that   apple    ate  ASP.  
       “Tom ate the apple.”  
    b. Tom   chi   le   neige    pingguo.  
       Tom  ate  ASP  that     apple.  
       “Tom ate the apple.”  
  
                                                  (Tian, 2006, p.1)
```
As we can see from the example (1) above, 1a emphasizes the noun phrase (the apple) following BA, and it also expresses an underlying meaning that the apple has been finished completely, while 1b does not focus on the noun phrase and can either be interpreted as “the apple has been finished completely” or “Tom ate the apple but hasn’t finished yet”.

There is an ongoing debate about whether BA should be classified as a verb, a preposition, or a case marker. In this project, I will treat BA as a preposition for the following reasons: 1) The [BA NP] construction behaves similarly to a preverbal prepositional phrase (PP) and this view has been generally agreed by the majority of academia; 2) BA’s historical meaning has been largely replaced by ‘NA’, and it rarely functions as a full verb in modern contexts. Additionally, I will not include any sentences where ‘BA’ functions as a verb in this project; 3) In responses to questions involving a PP or [BA NP] construction, the answer typically includes the verb rather than the preposition or BA, which proves that BA is similar to a preposition.

II. The reson I chose it
------
BA is generally considered as a light verb or a preposition in a sentence, and its main function has been explained above. It is a unique phenomenon we have never seen in English or other Indo-European languages. Therefore, I aim to explore how this special construction can be implemented in XLE and to test whether it truly behaves like a preposition or if it differs in certain aspects.

III. Implementation design
------
The grammar will be tested with 20 sentences in total, 10 grammatical sentences with BA construction and 10 ungrammatical sentences with different reasons of violation.   

```
1. Susan  ba  niunai  hele. 
   Susan  BA  milk   drank.
   “Susan drank the milk.”

2. Susan  ba  men  guanshangle.
   Susan  BA  door   closed.
   “Susan closed the door.”

3. Susan  ba  shu   fang  zai  zhuozishang. 
   Susan  BA  book  put  on   table.
   “Susan put the book on the table.”

4. Susan  ba  wenti     jieshide    hen  qingchu. 
   Susan  BA  question  explained   very  clear.
   “Susan explained the question very clear.”

5. Susan  ba  shuiguo  xide    hen  ganjing. 
   Susan  BA  fruit    washed  very  clean.
   “Susan washed the fruit very clean.”

6. Susan  ba  yifu     liang  zai  yangtaishang. 
   Susan  BA  clothes  hang  on  balcony.
   “Susan hangs the clothes on the balcony.”

7. Susan  ba  laji    rengjinle    lajitong. 
   Susan  BA  trash  threw into   trash bin.
   “Susan threw the trash into the trash bin.”

8. Susan  ba  diannao   xiuhaole. 
   Susan  BA  computer  fixed.
   “Susan fixed the computer.”

9. Susan  ba  che  tingzaile  tingchechang. 
   Susan  BA  car  parked in  parking lot.
   “Susan parked the car in the parking lot.”

10. Susan  ba  xinjian  chaile. 
    Susan  BA  letter   opened.
    “Susan opened the letter.”
```
Here are the ungrammatical sentences:   
```
1. Susan ba niunai he. (coherence violation: sentence requires a tense, ‘he’ cannot indicate any tense)  
2. Susan ba men guanshangle zhuozishang. (coherence violation: ‘guanshangle’ is a intransitive verb)  
3. Susan ba shu fang zai. (completeness violation: missing locative complement in PP)  
4. Susan ba wenti jieshide hen. (completeness violation: missing adjective in AP)  
5. Nimen ba shuiguo xide hen ganjing. (out of vocabulary, ‘Nimen’ is not in the lexicon)  
6. Susan ba yifu liang zai shiwai. (out of vocabulary, ‘shiwai’ is not in the lexicon)  
7. Susan bang wo reng laji. (missing rule adaption: two VPs in a sentence)  
8. Susan xiuhaole diannao? (missing rule adaption: question mark)  
9. Susan ba che tingchechang tingzaile. (word order violation)  
10. Susan ba chaile xinjian. (word order violation)  
```

My project is adapted from the grammar we have worked with in class. I didn’t change much about the frameworks but made some modifications to better accommodate the BA construction. I deleted unnecessary rules so the grammar looks more concise and refining, and also built a new lexicon, which was written in Pinyin instead of original Chinese characters.

OT-Marks are introduced in this project for distinguishing the English word and Chinese word in case they are in the same form. For example, the Chinese word ‘men’ means ‘door’, but in English it is a noun indicating ‘male’, I added @(OT-MARK cat) to this Chinese word to clear the confusion and reduce the solutions.

Since there is no subject-verb agreement in Standard Chinese, I only used Susan as the subject in the testsuite instead of various Chinese pronouns, but I also included them in the lexicon part of the grammar, feel free to try out with those pronouns!

IV. The remain challenges
------
The first challenge of implementing the BA construction is the property of a tone language, because tone are lexically contrastive in Standard Chinese, and some words even share the same tone, therefore we are unable to simply look at the pronunciation to define a word. For example, DE (地), DE(得) and DE(的) they share the similar pronunciation however each one of them has different function in a sentence, DE(的) is usually regarded as a marker of adjective or possessive pronoun, and DE(地) as a property marker of adverb, and DE(得) as a marker of the complement, it plays a role of connecting the verb and the verb result complement. Here in this project, I treat DE(得) as a suffix of the verb, instead of a separate marker, just to avoid extra problems and make the grammar simpler, because the main point of the project is BA construction.

The second challenge is LE as a separate marker of the past tense in Standard Chinese, it cannot be categorized by XLE system because word inflections are integrated as features instead of an independent marker. Therefore in the implementation of LE, I followed the way of how we implement the English language, that is attach the LE to the verb as a suffix so it can form a past tense.

The third challenge is Standard Chinese does not have verb tenses in the same way that many Indo-European languages do, where verbs change form to indicate past, present, or future actions. Instead, Chinese relies on contexts, time adverbs and aspect markers to convey when an action occurs. Therefore it is rather hard to get rid of some integrated rules from English, such as subject-verb agreement, when implementing Chinese grammar rules in XLE.

V. Files submitted and their functions
------
1. grammar.lfg (the grammar file contains the syntactic rules and lexicon)
2. testsuite.lfg (the testsuite file contains the sentences to be tested)
3. basic-parse-tok.fst (a morphology analyzer)
4. default-gen-tokenizer.fst (a morphology generator)
5. common.templates.lfg (the pargram shared templates)
6. english.infl.patch.full.fst (a English grammar file required for morphology analyzer)
7. README.md (a file which provides essential information about my project)

VI. A link to my GitHub repository
------
https://github.com/ArinaYe/finalproject-GD

VII. Reference
------
Tian, J. (2006). *The BA construction in Mandarin Chinese: A syntactic-semantic analysis.*
