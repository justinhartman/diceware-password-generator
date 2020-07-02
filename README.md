# Diceware Password Generator
The [Diceware Password Generator][dpg] is open-source software written in Python that uses one of five world lists and _dice_ to output an easy to remember, yet highly secure password based on a sequence of words such as, `boots-imbecile-nextdoor-espresso-cosmetics-remote`.

[Diceware][diceware] is a method for picking passphrases that uses dice to select words at random from a special list called the Diceware Word List. Each word in the list is preceded by a five digit number. All the digits are between one and six, allowing you to use the outcomes of five dice rolls to select a word from the list<sup>[[1]](#fn1)</sup>.

Using Dicewear as a methodology ensures that not only is a password like `mumbo-giver-alarm-lived-gig-wages-exit` easy to memorise, it is over **100 times**<sup>[[2]](#fn2)</sup> more secure than traditional passwords such as this `%u}+6:~TY/(8uR[/vB`.

The Diceware Password Generator was made to simplify the creation of these easy, yet very difficult to hack passwords on the fly.

## Installation and Usage
There is a [dedicated project page][dpg] for the [Diceware Password Generator][dpg]. You can head on over to that page to read more about:

- How to [install the software][install].
- How to [download the word lists][wordlist].
- How to [use the software][use].
- Various [usage examples][examples] for each of the five supplied word lists.
- The [licensing][licensing] of the software.
- [Credits to the people][credits] who made this possible.
- Interesting [links about Diceware][links].
- [Release Notes][release].

You can also [download the latest release][download] if you'd like to start getting your hands dirty :stuck_out_tongue_winking_eye:.

> <a name="fn1"><sup>[1]</sup></a> This is accurate for the original word list created by Arnold G. Reinhold as well as a word list by the [EFF][eff] which is supplied with the software. Additionally, there are three, shorter word lists that are supplied with the software. These additional word lists are not all between one and six digits nor are they necessarily preceded by a five digit number.

> <a name="fn2"><sup>[2]</sup></a> I don't actually know if this is accurate but it sounds impressive. Whether accurate or not, the DPG creates passwords that are extremely secure all thanks to entropy.

[diceware]: http://www.diceware.com/
[eff]: http://www.eff.org
[dpg]: https://hartman.me/projects/diceware-password-generator.html
[download]: https://github.com/justinhartman/diceware-password-generator/releases
[install]: https://hartman.me/projects/diceware-password-generator.html#installation
[wordlist]: https://hartman.me/projects/diceware-password-generator.html#clone-repo-and-download-the-word-lists
[use]: https://hartman.me/projects/diceware-password-generator.html#usage
[examples]: https://hartman.me/projects/diceware-password-generator.html#usage-examples
[licensing]: https://hartman.me/projects/diceware-password-generator.html#license
[credits]: https://hartman.me/projects/diceware-password-generator.html#credits
[links]: https://hartman.me/projects/diceware-password-generator.html#links
[release]: https://hartman.me/projects/diceware-password-generator-release-notes.html
