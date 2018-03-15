# Diceware Password Generator
I have a problem with passwords. I take them very seriously and for at least the last 10 years I have been using some type of password manager to manage all my passwords and other critical, personal information.

The problem with this scenario is that for years I have been using password generators, built within the app, to secure my online logins. Why is this a problem? Well... it isn't _per se_; the main issue is the **Master Password**, that is the one password to rule them all, well, mine is rather easy to break.

I've often debated with myself around how to solve this problem. To remember a password like `:o0{n1$z'4yQ_?2RwW` is simply not going to happen. The thing is, in order to be secure you need a password to remember so as to only have it in your head and no physical evidence of it lying around. 

And here is where the _Dicewear Password Generator (DPG)_ comes into play. DPG uses a world list and _"dice"_ to output an easy to remember password based on a sequence of words like `boots-imbecile-nextdoor-espresso-cosmetics-remote`. While this is a long password, it certainly can be memorised - and quickly.

It turns out that not only is a password like `mumbo-giver-alarm-lived-gig-wages-exit` easy to memorise, it is over **100 times**<sup>[[1]](#footnote)</sup> more secure than this `%u}+6:~TY/(8uR[/vB` password.

## About the Dicewear Methodology
Diceware is a method for picking passphrases that uses dice to select words at random from a special list called the Diceware Word List. Each word in the list is preceded by a five digit number. All the digits are between one and six, allowing you to use the outcomes of five dice rolls to select a word from the list.

Here is a short excerpt from a Diceware word list:
```text
 16655 clause
 16656 claw
 16661 clay
 16662 clean
 16663 clear
 16664 cleat
 16665 cleft
 16666 clerk
 21111 cliche
 21112 click
 21113 cliff
 21114 climb
```
Measuring the security of a randomly-generated passphrase is easy. The most common approach to randomly-generated passphrases is to simply choose several words from a list of words, at random. The more words you choose, or the longer the list, the harder it is to crack. Looking at it mathematically, for _`k`_ words chosen from a list of length _`n`_, there are _n<sup>k</sup>_ possible passphrases of this type. It will take an adversary about _n<sup>k</sup>/2_ guesses on average to crack this passphrase.

For most uses, generating a six-word passphrase with a long list is recommended, for a strength of 77 bits of entropy. ("Bits of entropy" is a common measure for the strength of a password or passphrase. Adding one bit of entropy doubles the number of guesses required, which makes it twice as difficult to brute force.) Each additional word will strengthen the passphrase by about 12.9 bits.

Passphrases generated using shorter lists will be weaker than the long list on a per-word basis (10.3 bits/word). Put another way, this means you would need to choose more words from the short list, to get comparable security to the long list — for example, using eight words from the short will provide a strength of about 82 bits, slightly stronger than six words from a long list.


## Installation

### Clone Repo and Download the Word Lists
```bash
$ git clone https://github.com/justinhartman/diceware-password-generator.git ~/diceware
$ cd ~/diceware
$ chmod +x download-words
$ ./download-words
```
This will download five word lists for you to use. They are:

- [Arnold Reinhold's Beale Diceware word list][beale] - The most popular word list is Arnold Reinhold's Diceware list, first published in 1995. This list contains 7,776 words, equal to the number of possible ordered rolls of five six-sided dice (7776=6<sup>5</sup>), making it suitable for using standard dice as a source of randomness.
- [EFF's Long Word List][wordlist] - EFF's new list matches the original Diceware list in size (7,776 words (6<sup>5</sup>)), offering equivalent security for each word you choose. The words in this list are longer (7.0 characters) on average, than Reinhold's Diceware list (4.3 characters). This is a result of banning words under 3 characters as well as prioritising familiar words over short but unusual words.
- [EFF's Short, memorable word list][short] - This new list contains only 1,296 words (6<sup>4</sup>), suitable for use with four six-sided dice. By reducing the number of words in the list, EFF were able to use words with a maximum of five characters. This can lead to more efficient typing for the same security if it requires fewer characters to enter _`N`_ short words than _`N-1`_ long words.
- [EFF's Experimental, Short word list.][edit] - This short list has a few additional features to the above list, making the words easy to type. Each word has a unique three-character prefix. This means that future software could auto-complete words in the passphrase after the user has typed the first three characters. This list is mostly a proof-of-concept for individual users.
- [Vorvig Word List][vorvig] - The 1/3 million most frequent words, all lowercase, with counts.

## Usage

The following, first-time commands, will get you using the DPG quickly.
```bash
$ cd ~/diceware
$ chmod +x passphrase
$ ./passphrase -h
```
The `-h`, or `--help` flag will output all the available commands:
```terminal
Usage: ./passphrase [options] [-n] <number of words>
-w, --words     Standard word list (default)
-v, --vorvig    Vorvig word list
-s, --short     Short, memorable word list
-e, --edit      Short, editable word list. Experimental.
-b, --beale     Arnold Reinhold's Beale Diceware word list.
--------------------------------------------------------
-n, --number    Input an integer for the number of words
                you want generated for your passphrase.
```
Each word list has its own flag (e.g. `-v` or `--vorvig`) so you can find the right word list to suit your requirements. Each one is different and you'll see why when you start generating passwords.

Additionally, there is an _optional_ `-n` flag which is used to specify how many words you want the DPG to return back to you. For example you may want 4 long words (`-n 4`) or 6 shorter words (`-n 6`) and changing the integer value after the `-n` flag will return the number you requested. If you omit the flag entirely, the DPG will default to 5 numbers of words returned to you to.

## Usage Examples
The following examples use each of the various word lists and output a certain number of words as specified (or not) with the `-n` flag.

### Standard word list, default number of words (no flag)
```bash
$ ./passphrase -w
little-untamed-reflex-result-catnap
```
### Standard word list, requesting 4 words (with flag)
```bash
$ ./passphrase -w -n 4
recipient-slouching-caucasian-party
```
### Vorvig word list
```bash
$ ./passphrase -v -n 3
insights-liberality-bethania
```
### Short, memorable word list
```bash
$ ./passphrase -s -n 6
gong-pulse-life-outer-undo-start
```
### Short, experimental word list
```bash
$ ./passphrase -e -n 6
sainthood-gnomish-scenario-upkeep-pauper-sled
```
### Arnold Reinhold's Beale Diceware word list
```bash
$ ./passphrase -b -n 4
wielder-oomph-mugshot-easel
```
## Known Bug
If you run into issues with the `beale` word list whereby running `$ ./passphrase -b` or `$ ./passphrase --beale` returns the following error:
```python
Traceback (most recent call last):
  File "./passphrase", line 47, in <module>
    main(sys.argv[1:])
  File "./passphrase", line 10, in main
    beale = [s.split()[1] for s in open(sys.path[0]+'/words-beale')]
IndexError: list index out of range
```
This is happening because the word list has been digitally signed and you need to remove the signed signature in order to get it to work correctly.
```bash
$ cd ~/dicewear
$ nano words-beale
```
Remove the following on lines 1 and 2, including the blank space on page 2:
```nano
-----BEGIN PGP SIGNED MESSAGE-----
```
Then, remove the actual signature contained at the end of the file:
```nano
-----BEGIN PGP SIGNATURE-----
Version: PGP for Personal Privacy 5.0
Charset: noconv

iQCVAwUBNX6aTGtruC2sMYShAQGSwAP9F8usVblyi+QEHjxuiltBxT0u6GTHM/Cn
WgT+GYMRBbOMyDqe9KKyO4oryqWLnS83O8L9uLaEBqNXxEDm8KPGBB/l9CSUMCsC
cD1hx8NQ/LpfjgRnngLSVvdjNmECg8OgKom2dht6oVHN8q+FQhmiqmndS72lTSOO
jOuFf/otw7o=
=7B7m
-----END PGP SIGNATURE-----
```
This should resolve this issue.

## License
The original [Dicewear software][dicewear] is [Copyright &copy; 2018 Alexey Shamrin][mit] and is licensed under [The MIT License (MIT)][mit]. 

I believe I've made substantial enough changes to the original source code that I am going to release this version of the software to the public domain. 
```terminal
(*
 * The author disclaims copyright to this source code. In place of
 * a legal notice, here is a blessing:
 *
 *    May you do good and not evil.
 *    May you find forgiveness for yourself and forgive others.
 *    May you share freely, never taking more than you give.
 *)
```
This doesn't change the copyright or license of the original Dicewear software and a [copy of the original source code][first_commit] are contained in the [first commit of this repo][first_commit].

## Credits
- [Dicewear by Alexey Shamrin][dicewear].
- [Arnold G. Reinhold][reinhold] for the word list.
- [EFF Dice-Generated Passphrases][eff], for the word lists and inspiration.

## Links
* [Diceware passphrase home page][dice_home]
* [EFF Dice-Generated Passphrases][eff] ([deep dive][deep_dive], [word list][wordlist])

---

<a name="footnote"><sup>[1]</sup></a> I don't actually know if this is accurate but it sounds impressive. Whether accurate or not, the DPG creates passwords that are extremely secure all thanks to entropy.

[dice_home]: http://www.diceware.com
[eff]: https://www.eff.org/dice
[deep_dive]: https://www.eff.org/deeplinks/2016/07/new-wordlists-random-passphrases
[wordlist]: https://www.eff.org/files/2016/07/18/eff_large_wordlist.txt
[short]: https://www.eff.org/files/2016/09/08/eff_short_wordlist_1.txt
[edit]: https://www.eff.org/files/2016/09/08/eff_short_wordlist_2_0.txt
[vorvig]: http://norvig.com/ngrams/count_1w.txt
[beale]: http://world.std.com/%7Ereinhold/beale.wordlist.asc
[mit]: https://github.com/shamrin/diceware/blob/master/LICENSE
[dicewear]: https://github.com/shamrin/diceware
[first_commit]: https://github.com/justinhartman/diceware-password-generator/tree/95bdd32e12f0e77e24d9db2dc51d12ebd5bc299e
[reinhold]: http://world.std.com/~reinhold/diceware.html
