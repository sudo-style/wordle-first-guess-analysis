# wordle-first-guess-analysis

A discord server that I frequent in had a sussy baka that was suspected of cheating for quite a while now. I wondered, was there a website that had hints on it? There probably is a best word for an oppener, but this does not tackle that problem. It just compares the suspect in question, to the rest of the comunity.

Tools used

* [pandas](https://pandas.pydata.org/)
* [SciPy](https://docs.scipy.org/doc/scipy/reference/stats.html#module-scipy.stats)

Data collection:

Using the search term, "Here are yesterday's results" in the discord channel, I manually extracted 139 images, containing 195 games, played by 21 users. 

![t](https://preview.redd.it/can-someone-help-me-figure-out-how-to-disallow-the-official-v0-g9joy00swane1.png?width=320&crop=smart&auto=webp&s=27343b8faf9b8e4cec9e518ad45c352318d6057b)

 I manually typed in 779 results,

* Game Number: from this I was able to get the
* Answer: Given the "Game Number", I used this [website](https://wordfinder.yourdictionary.com/wordle/answers/) to find the answers.
* Guess: This is the number of the guess
  * E.g 1 refers to the first guess a user had for that game, 2 the second and so on
* Feedback: g:green, y:yellow, b:blank
* Output: Using a .numbers I used a function to output the emoji to make sure I typed things properly.
* Score: This was also calcualted, using probability assuming letters are indipendent from each other (they are not).
  * probability(green) = 1/26
  * probability(blank) =  (25/26)^5
  * probability(yellow) = 1 - probability(green) - probability(blank)
  * I then used the inverses of these, multiplied by how many were there
  * thus the minimum score for a word = (25÷26)^5 = 1.2166529024
  * and the maximum score for a word = 5 * 26 = 130



1 user did by far the most games played 56, which was ~30%, of the total data, which was convienent since this was the most suspicious user. This is the number of games played sorted from greatest to least: [56, 14, 12, 11, 11, 11, 10, 9, 9, 8, 7, 5, 4, 4, 3, 1]

Goal of the project was to compare, this suspicious user, to the rest of the community, but I have made the code generalized so it is easy to test any user using pandas. This used statistics, in order to calculate the Null hypothesis
