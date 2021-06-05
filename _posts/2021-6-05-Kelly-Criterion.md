---
layout: post
title: Optimal Bet Sizing
date: 2021-6-5 17:08:0 +0000
comments: True
categories: [Epistemics, Misc]
---

*I made a tool that allows you to optimally size your bets/investments, utilizing the Kelly criterion.*

Adding to the list of dope things that have come out of [Bell Labs](https://en.wikipedia.org/wiki/Bell_Labs ) is the Kelly criterion -- an equation for optimal bet sizing. You are playing a game with probability $$p$$ of winning $$x$$ dollars and probability $$1-p$$ of losing $$y$$ dollars. The Kelly criterion tells you how much of your wealth you should bet such that, in expectation, you will maximize returns over the long run.

I found the existence of the Kelly criterion exciting and believe it belongs in the toolkit of any aspiring rationalist. The [Wikipedia on the Kelly criterion is great](https://en.wikipedia.org/wiki/Kelly_criterion). It covers the proof of its optimality, along with applications to single and multiple bet scenarios. It also covers applications to stocks but models the stock using technical analysis.  As a fan of fundamental analysis, I wanted a system where I could use my beliefs to assign a probability distribution over the price of a stock and, using the Kelly criterion, be told exactly how much to optimally invest.

Do I think I can actually assign accurate probability distributions to stocks? Yes! Pigs can fly and the earth is flat! But seriously, I see this tool as being useful for a few reasons:
* First, at a high level I think it is a good way to become more methodical about my investing, translating beliefs into formal statements about the stock price. This will also be helpful in knowing when to sell.
* Second, the Kelly criterion will act as a sanity check, highlighting internal inconsistencies between my beliefs and bet sizing. Right now, to translate my beliefs into a number for how much to invest I put my finger in the air, spin in a circle three times, and magically pull a number of out my ass. Using the Kelly criterion breaks down this process, removing the bet sizing portion of it and flagging where my intuition doesn’t align with the probabilities I provide. If the Kelly criterion gives a value that disagrees with my intuition, this will force me to either change my intuition to match the Kelly bet size, or change my probabilities and their corresponding Kelly bet size to match my intuition. Even if I can’t fully reconcile the two it provides a great anchor point for the final amount I decide to invest.
* Finally, I have been persuaded that in certain instances trading on margin is worthwhile. However, the idea of trading with money I don’t own terrifies me. The Kelly criterion will be able to tell me when my beliefs, their corresponding probabilities, and the opportunity presented are sufficiently strong to justify me using margin.

So without further ado, here is the tool that I’ve put on Google Colab for anyone to be able to run: <https://colab.research.google.com/drive/1Fw8btygHEv9wfnGPWZvdFdlZRnCOtU3P?usp=sharing>

And here it is as a GitHub repo if thats your thing: <https://github.com/TrentBrick/KellyBet>

Please send any feedback on the tool and suggest improvements! Also, it goes without saying… [caveat emptor](https://en.wikipedia.org/wiki/Caveat_emptor).

*Hat-tip to Vitalik Buterin for his [post on crypto prediction markets](https://vitalik.ca/general/2021/02/18/election.html) that first introduced me to the Kelly criterion. All errors and confusions that remain are mine and mine alone.*
