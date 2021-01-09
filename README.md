# wordnet

[![Build Status](https://travis-ci.org/nltk/wordnet.svg?branch=master)](https://travis-ci.org/nltk/wordnet)


# Use

```python
>>> from wn import WordNet
>>> from wn.info import WordNetInformationContent

>>> from wn.constants import wordnet_30_dir, wordnet_33_dir
>>> wordnet = WordNet(wordnet_30_dir) # Uses WordNet v3.0 to be comparable to NLTK, by default uses v3.3

>>> wordnet.synsets('dog')
[Synset('dog.n.01'), Synset('frump.n.01'), Synset('dog.n.03'), Synset('cad.n.01'), Synset('frank.n.02'), Synset('pawl.n.01'), Synset('andiron.n.01'), Synset('chase.v.01')]

>>> wordnet.synset('dog.n.01')
Synset('dog.n.01')

>>> wordnet.synset('dog.n.01').lemma_names()
['dog', 'domestic_dog', 'Canis_familiaris']

>>> wordnet.synset('dog.n.01').lemma_names(lang='spa')
['can', 'perro']

>>> dog = wordnet.synset('dog.n.01')
>>> cat = wordnet.synset('cat.n.01')

>>> wordnet.path_similarity(dog, cat)
0.2
>>> wordnet.wup_similarity(dog, cat)
0.8571428571428571
>>> wordnet.lch_similarity(dog, cat)
2.0281482472922856


>>> wordnet_ic = WordNetInformationContent(corpus='bnc', resnik=True, add1=True)

>>> wordnet.res_similarity(dog, cat, wordnet_ic)
7.66654127408746
>>> wordnet.jcn_similarity(dog, cat, wordnet_ic)
0.3774428077151209
>>> wordnet.lin_similarity(dog, cat, wordnet_ic)
0.852667348509242
```


# With NLTK

As a comparison, this is the interface from NLTK v3.4.5

```python
>>> from nltk.corpus import wordnet
>>> from nltk.corpus import wordnet_ic

>>> wordnet.synset('dog.n.1').lemma_names()
['dog', 'domestic_dog', 'Canis_familiaris']
>>> wordnet.synset('dog.n.1').lemma_names(lang='spa')
['can', 'perro']

>>> dog = wordnet.synset('dog.n.01')
>>> cat = wordnet.synset('cat.n.01')

>>> wordnet.path_similarity(dog, cat)
0.2
>>> wordnet.wup_similarity(dog, cat)
0.8571428571428571
>>> wordnet.lch_similarity(dog, cat)
2.0281482472922856

>>> ic = wordnet_ic('ic-bnc-resnik-add1.dat')

>>> dog.res_similarity(cat, ic)
7.66654127408746
>>> dog.jcn_similarity(cat, ic)
0.3774428077151209
>>> dog.lin_similarity(cat, ic)
0.852667348509242
```
