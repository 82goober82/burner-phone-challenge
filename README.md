Burner Phone Challenge
======================
Can you identify a burner phone from a stream of (fake) AT&amp;T Hemisphere data?

Inspired by Kenneth Lipp on [Twitter](https://twitter.com/kennethlipp/status/848565438061654017).

Specifically, this passage was interesting to me:

> Let's say a narcotics task force is trying to maintain a wiretap on a drug dealer, but the drug dealer uses prepaid "burner" phones and is constantly changing his number.
> However, from each new phone number, this drug dealer makes calls to may of the same people - his mom, girlfriend, a supplier - and also makes most of his calls from a limited range of locations. Because AT&T can analyze so many call-detail records with such well-developed custom software, it can easily track these patterns to infer which unknown number is really the suspect. Since it can do this in real time by mining its live data stream, by the time the suspect burns an old phone and makes a few calls from his new one, he's back in the net.

AT&T can do this. Can you?

First though, you need some data to play with. So I made some up. It's definitely not accurate, because I don't have any AT&T data to work from, but it should be close enough to give you an idea of what AT&T (and law enforcement, by extension) can do. If you have ideas for how to make it more accurate, or some legitimate (anonymized, please!) data to build a generative model with, that would be neat and you should [let me know](https://strikersecurity.com/contact/).


And so,

The Rules
=========
Coming soon. The gist is that you should use `call_data.csv` and `call_data.gexf` to see if you can identify which numbers belong to which people (or when people switch numbers, or however you'd like to frame the problem). You can then check against `solutions.csv`.


Usage
=====
If you want to generate your own data...

Install dependencies (using a virtualenv, preferably). You can skip this step, but you'll only get CSV files, no network graphs:
`virtualenv venv --python=python3 && source venv/bin/activate`
`pip install networkx`

Do the thing:
`python src/generate.py`

If you skipped the dependencies step and aren't in a virtualenv:
`python3 src/generate.py`

(Make sure you're using Python 3 or you'll have a bad time.)


Big Todos
=========
  - make locations/contacts called non-uniformly (i.e call some friends more than others, be in some places more than others)
  - make agents coordinate; if someone switches numbers, their friends should stop calling the old one
  - actual day/night cycle and generally more reasonable agent behavior
  - "friends of friends" - right now, agents are uniformly likely to know each other, which doesn't make sense
  - "mutual contacts" - if A calls B a lot, right now B is no more likely to call A, which is obviously wrong


See Also
========

[Example of how law enforcement uses these call records](https://web.archive.org/web/20170621072311/http://wispd.org/attachments/2015Conference/pdf/Mattert_Weitz_Understanding%20and%20Plotting%20Cell%20Phone%20Information.pdf)
