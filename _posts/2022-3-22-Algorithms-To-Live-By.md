---
layout: post
title: Book Review - Algorithms To Live By
date: 2022-02-23 09:28:0 +0000
comments: True
categories: [Book Review]
---

*Computers deal with finite time and resources in many of the same ways that humans do. Algorithms to Live By engagingly reviews some of the most successful algorithms developed in computer science, and shows how they can be applied to our lives.*

---

I would recommend reading the book in full because it really is well written, using concrete examples and intuition to drive home many ideas. There is also a good podcast summarizing the book with one of the authors [here](https://80000hours.org/podcast/episodes/brian-christian-algorithms-to-live-by/).

I summarize the algorithms that I find the most interesting for possible use in my life (and maybe yours!). And then discuss some fun facts and highlights from the book.

---

## 1. The Optimal Stopping Problem - How long to search before committing?

*Relevant to dating, apartment hunting, finding parking, job searches, etc.*

Before getting into the details note that this is very much a toy model that misses a lot of important real world nuance (this is a repeating theme for algorithms introduced throughout the book). We live in a messy NP world where human heuristics are actually pretty damn impressive.

You need to hire a secretary. During each interview you must decide on the spot whether to hire them or not (you can’t reach out later) and obviously want to hire the best secretary you can. How can you maximize the odds you hire the best secretary there is?

If you have no objective metrics for how to evaluate applicants – you can only rank order them against each other – then it turns out it is optimal to never hire any of the first 37% of applicants, just interviewing them to collect data and learn the distribution of talent. Then, you should immediately hire the first secretary better than those you have previously encountered. This is intuitively called the “Look then Leap” strategy and it gives you a 37% chance of hiring the very best applicant from the whole pool (coincidentally  the same % as the amount of time/samples you should “Look” for). While 37% doesn't seem that high, what is striking is that this result is independent of the size of the pool. If the hiring pool is 100 applicants, or 1 million, if you follow the optimal stopping rule the chance of finding the best remains 37%[^noSuprising].

Modify the assumptions such that when you try to hire someone there is only a 50% chance they accept. In this case you can’t afford to be so picky and should “Look” for only 25% of the time before “Leaping”.

If we assume that you can in fact reach out again to hire a previous applicant with a 50% success rate, it becomes optimal to never hire any applicant until after you see 61%(!) of applicants. Then hire the best person you next see. If you exhaust your whole hiring pool/time allocation then reach out to the best that you saw previously. You can wait longer because there is less of a risk that you run out of good applicants and are stuck with hiring one of the last few. In this case there is also a 61% chance of ending up with the very best applicant!

In scenarios where you have objective information rather than just relative comparisons, you should follow a “Threshold Rule” whereby the first person who passes your set threshold you hire immediately. Over time as the pool gets smaller, you must lower your threshold slightly but there is no two step “Look then Leap”. House/apartment hunts are more in this category where there are objective metrics and a known distribution for housing prices, the quality of the neighborhood etc. In this scenario with perfect objective information there is a 58% probability of hiring the best in the pool. Thus the success probability when you have objective metrics and a known distribution of outcomes increases by 21% over the 37% from the Secretary problem where you only have relative information. When applied to dating, this leads to the amusing result that “Gold digging is more likely to succeed than a quest for love.”

Some studies found that people often leapt sooner than they should have. It would be easy to add these studies to the pile of “human irrationality” but in reality this behavior is optimal if we account for the fact that there are costs to searching in either time, money, or both. Depending on the cost of sampling and our discount rate on having a solution (eg. how much money is worth now versus at a future point in time[^interestRates]) you should modify how quickly you make your decision.

In the real world, most problems are a messy, weighted combination of all the previous assumptions on prior information, reversible decisions, searching costs, and unmentioned until now – that here we only care about the very best option while often the second best can be almost just as good. I would be interested to know if there is state of the art literature that combines all of these assumptions and gives some optimal stopping time. This is considered in [this post](https://applieddivinitystudies.com/career-timing/) where accounting for search costs and the next best options being almost as good significantly reduces the optimal search time.

Taking a problem of personal interest, dating(!), it has all of the above assumptions to account for: Someone you want to date may not want to date you; you can reach out again to previous people if you change your mind but with a lower probability success of winning them back; there is some objective information such as their job that can give you noisy information about their interests, education level, etc (but you have a [finite number of filters](https://www.benkuhn.net/outliers/) so be careful what you filter for); there a real cost in time and money to going on dates; you already have a rich prior distribution from life experience about previous dates and general personality types; however, there are certainly still intangibles around how well you “vibe” that rely on subjective rank ordering. So how many dates should you go on and should a “Look then Leap” or “Threshold Rule” be used?

The piece on more [realistic optimal stopping problems](https://applieddivinitystudies.com/career-timing/) also notes that as you go about searching your underlying utility function may evolve. This is likely to be true for dating due to other general factors in life and discovering unknown unknowns about your preferences. A friend upon entering his second serious relationship remarked that he didn’t know quite just how much he was compromising during his first. I recall some study also showing that the preferences people say they have for partners and the revealed preferences after a round of speed dating are quite different. Or as wisely summarized by Ali-G:

<div align="center">
  <iframe width="560" height="315" src="https://www.youtube.com/embed/27hLR0yd4SM?start=130" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>
The utility function for dating is also multi-tiered with the terminal goal of a happy marriage and instrumental goals of fun dates and a fulfilling relationship. I will leave a more serious and sappy discussion of dating with its relations to optimal stopping and beyond for another time. However, I think having these frameworks as anchors to use for reasoning about dating and the like are very useful, even if the models have a number of limiting assumptions.

---

## 2. Organization - my messy heaps of clothes and papers obey the Least Recently Used algorithm and are thus optimal! Take that mom!

Ideally everything we could ever want to remember and retrieve would be equally lightning fast accessible to us. However, in both brains and computers our memory is always constrained and thus we must prioritize what is easiest to retrieve. In computers there is a hierarchy of increasingly slow memory caches that are particularly important for storing previous results for re-use. The fastest memory is called SRAM and costs 1000x more per byte than solid state flash hard drives. What information should be stored in what cache? We could use First In First Out where the oldest information is removed chronologically. Instead, we could randomly remove items from memory? However, it turns out the best algorithm is to remove the Least Recently Used (LRU) items. The intuition is that if we just used a piece of information it is likely it is important and we will need to re-use it again. Add new things to the front, and whenever you use something, put it back at the front again. When searching go from the front to the back.

> “If you follow the LRU principle … then the total amount of time you spend searching will never be more than twice as long as if you’d known the future. That’s not a guarantee any other algorithm can make.”

So next time you feel awkward about that stack of messy looking papers proclaim to yourself and the world that the pile is not a mess, it is self sorting and optimal for search!

This principle is crucial not only for organizing personal items but also it is crucial for which warehouses Amazon sends inventory and where Akamai and other web hosters store website information so that you don’t need to query a server hosted on the other side of the world. On your computer, rather than having a complex hierarchical file directory, consider just sorting everything by how recently it was used.

---

## 3. Vickrey auctions - have your cake and eat it too!

English auctions start low and increase in price. Dutch auctions start high and decrease in price. Blind auctions keep everyone’s price preferences secret. In all of these auctions you need to model what other people are willing to pay and try to beat them while also being wary of over paying yourself.

In the Vickrey auction, you write down your price secretly. The person willing to pay the most wins but only pays the second highest price. This mechanism makes the optimal strategy to put down the honest price you are willing to pay -- putting down any more and you may overpay, putting down any less and you may lose the auction for no good reason because you won’t save any money (you will only have to pay the second highest price!). This strategy is also dominant in that it works the best independent of how anyone else bids; it is all down to you bidding your true utility.

Surely there is some tradeoff with this system in that the auction seller gets less than they otherwise would? In fact, the expected sale price in a first price auction will converge precisely to that as the Vickrey auction. This is because in a first price auction, you bid less than you otherwise would to try and just beat out others but not overpay. Meanwhile, with the Vickrey auction, the mechanism does this for you and so you can just be honest and save all the head scratching.

Beyond the Vickrey auction, there is the “revelation principle” by Nobel laureate Roger Myerson showing that

> “Any game that requires strategically masking the truth can be transformed into a game that requires nothing but simple honesty.”

The intuition behind this exciting result for mechanism design is: “imagine that you have an agent or a lawyer who will be playing the game for you. If you trust them to represent your interests, you’re going to simply tell them exactly what you want, and let them handle all of the strategic bid-shading and the recursive strategizing on your behalf. In the Vickrey auction, the game itself performs this function. And the revelation principle just expands this idea: any game that can be played for you by agents to whom you’ll tell the truth, it says, will become an honesty-is-best game if the behavior you want from your agent is incorporated into the rules of the game itself.

The Ethereum blockchain can run transparent smart contracts that can implement sophisticated mechanisms in a way that is trustless and open access for anyone to participate in. What systems could benefit from algorithmic mechanisms that could leverage the other advantages of blockchain and implement the revelation principle? For example, could we use this for automated legal resolution removing middle men and having the dominant strategy be honesty? Here is a worked example of a solidity smart contract for blind auctions: https://docs.soliditylang.org/en/develop/solidity-by-example.html#id2. It would be great if someone implemented this on a test network (without any gas fees) with a second price auction people could use to, say, bid on the prices for different rooms in a shared apartment.

---

## 4. Relaxations - taxonomy of different forms of relaxation that can help solve optimization problems.

> “What would you do if you weren’t afraid? … What would you do if you could not fail… What would you do if you won the lottery?

Relaxing or temporarily removing some constraints from an intractable problem can be a very useful way to make progress.

In the traveling salesman problem where you want to visit each town once and only once with the most efficient route possible is intractable. However, removing the constraint that you can only visit once and can instead backtrack gives a minimum spanning tree that not only provides a very efficient starting point for the full algorithm but also gives a lower bound on the best possible (unknown) solution!

The other forms of relaxation are relaxing a discrete problem into a continuous one where gradients can then be used to approximate the best solution within some bound much more efficiently. Also Lagrangian relaxation where a hard constraint is instead turned into a large penalty as part of the ultimate utility function, also allowing for more powerful optimization to take place.

---

## 5. Scheduling - it's complicated, so stop worrying about it so much?

Scheduling is and will always be hard. There is a whole chapter dedicated to different scheduling algorithms that are probably optimal given your specific objective function (do you want to minimize lateness? Get the most things done the fastest? What do you care about?). However, most interestingly, when any of the algorithms are made slightly more nuanced and closer to the real world, they all become intractable. For example, in Moore’s algorithm to minimize the number of late items when some items are made more important than others, no algorithm can readily provide the optimal schedule. Similarly, having constraints around when certain tasks can be done (eg. store opening and closing times) also makes all scheduling problems intractable.

> “A recent survey showed that the status of about 7% of all problems is still unknown, scheduling’s terra incognita. Of the 93% of the problems that we do understand, however, the news isn’t great: only 9% can be solved efficiently and the other 84% have been proven intractable.”

Some good and bad news about this result must be provided. If the schedule is allowed to switch midway between tasks and store its progress for later, then a number of problems become tractable again. However, the second context switching costs are also accounted for, the problems become difficult again and computers can get stuck in “thrashing” where by the time they switch to one task and load it into memory, then immediately jump to another task, not actually making any real progress on any of them. I think, and the book helps argue, that humans do far too much context switching in an ordinary day. [Paul Graham’s piece](http://www.paulgraham.com/makersschedule.html) on the workday not being arranged for programmers comes to mind.  

The bottom line best solution in expectation is the “weighted Shortest Processing Time” algorithm. For each task, divide its importance by the expected time it will take to complete and currently work on whatever has the highest importance per unit of time.
> “Under certain assumptions it minimizes not just the sum of weighted completion times, as we might expect, but also the sum of the weights of the late jobs and the sum of the weighted lateness of those jobs. Intriguing, optimizing all these other metrics is intractable if we know the start times and durations of the jobs ahead of time.” “There are cases where clairvoyance [knowing the future] is a burden”.

---

## General thoughts

I wish they had hammered home more how important the underlying assumptions are for these problems all in one place and clearly. Having an algorithm can anchor our approach to solving a problem and give us significant overconfidence while failing to make all of the correct assumptions can lead to very different answers. Unless it is likely that all of the assumptions will be met or the algorithm fails gracefully (with linear rather than non linear error) we might be better off fumbling uncertainty in the dark than blindly following the algorithm off a cliff. I have heard critiques of EA that hit on this problem. To add some nuance, assumptions and fake numbers can be used to show that something should not be done more easily and there are cases that I would argue fail elegantly in that even with dramatically different assumptions you still get the result as outlined in this favourite SSC piece is: [If it's worth doing it’s worth doing with made up statistics ](https://slatestarcodex.com/2013/05/02/if-its-worth-doing-its-worth-doing-with-made-up-statistics/).

We humans are surprisingly optimal and the tasks that we are trying to solve are incredibly difficult. Given our finite time and compute we do very well for ourselves. Heuristics and biases research has tried to highlight how dumb humans can be. While we should be aware of these failings, and try to correct them when they are in fact failings, a number of these experiments are in artificial lab settings and testing heuristics designed for more realistic, complex, and important environments -- this perspective can support the inverse field that looks at just how optimal humans already are, and our reasoning successes rather than failures.

---

*Thanks to ... for reading drafts of this piece. All remaining errors are mine and mine alone.*

---

## Other fun facts throughout the book

* When to park. We should have dynamic pricing and seek to have 85% capacity. “When [parking] occupancy goes from 90% to 95%, it accommodates only 5% more cars but doubles the length of everyone’s search.” This means that empty spots on busy high demand streets are a sign that things are working.

* The burglary problem where you lose it all when you fail. The number of robberies one should carry out is equal to the chance you get away, divided by the chance you get caught”. Eg. if you have a 90% chance of pulling off each robbery (with a 10% chance of losing it all) then “retire” after 90/10 = 9 robberies.

* Explore vs exploit in proportion to the amount of future time available to exploit. If you are about to move out of a city there is capped upside and you should instead enjoy what you already know you will like. This is likely why old people are “consevative” and don't do new things, they have been exploring their whole lives. And are now exploriting and maximally enjoying what they have discovered. Reaping the fruits of their exploration.

* On the explore exploit trade-off I liked this quote: “Make new friends, but keep the old/ Those are silver, these are gold.”

* The timeline for explore vs exploit is interestingly applied to explain the rise in movie sequels, such as “Fast and Furious 6 and The Hangover 3”. I think that new forms of media such as Netflix TV series have reversed this trend but it is documented here that “Profits of the largest film studios declined by 40% between 2007 and 2011, and ticket sales have declined in seven of the past ten years.” if movie producers believed they were falling on hard times it would make sense to exploit known successes rather than explore new and potentially unsuccessful ideas.

* Monte Carlo and Metropolis Hastings MCMC were developed for the Manhattan project. And that Metropolis is actually the name of Nicholas Metropolis who co-developed it! I am continuously amazed by the amount of innovation that has come out of the Manhattan Project, Bell Labs, and Xerox park.

* Using the upper confidence bound minimizes regret.

* Arguments that we should be using UCB (Upper Confidence Bound) and dynamics in our drug testing. Unethical otherwise. Yes we want to ensure once and for all the treatment works but we don't want to kill people by failing to give them treatments.

* Google tested 41 different shades of blue for one of its toolbars in 2009.

* Obama A/B tested his donation page. There were optimal ways to ask for donations depending on the person’s previous donation profile. For newcomers, the best was “donate and get a gift”, even after the cost of sending the gift. For long time newsletter readers who had never given it was “please donate”, maybe appealing to the guilt. For veteran donors it was “contribute”, they had already donated but could always contribute more maybe. And a simple black and white photo of the Obama family outperformed any other photo or video. All of these were small improvements but together summed to something huge.

* Research showing that we explore too much before committing. Don't exploit enough. But in these experiments the world is artificially static, in the real world entropy means that a previous food source has changed, etc. restless bandit problems that are much harder. However, modern civilization is very different from our evolutionary landscape in that things are far more static now than ever before. “A berry patch might be ripe one week adn rotten the next but as Andy Warhol put it, “A Coke is a Coke.”

* Von Neumann invented Mergesort which remains optimal in many settings. N log n time.  

* Searching is far faster than sorting. And for personal use where we sort for future search to be easier but won't ever search most of what we sort, sorting is pointless. +1 for unsorted email inboxes!

* Soccer scoring is a poor indicator of the best team as scoring is high variance and the final scores are so low.

* Round robins and the utility of social status.

* Caching is everywhere.

* Exponential backoff is an interesting and useful algorithm that is used particularly in networking.

* “The price of anarchy” is the gap between cooperation and competition for individual commuters. The price of anarchy is not so bad, only 33% worse than otherwise. This means that autonomous cars all coordinating won't be that much better from a traffic perspective.

* “The optimist proclaims that we live in the best of all possible worlds; and the pessimist fears this is true.”

* Forgetting curve, may actually be memories being pushed to lower caches as we accumulate more and more memories throughout our lives. Rather than us actually forgetting the information for good. I think cognitive decline certainly applies too but still.

* Responsiveness vs throughput. Real world scheduling problems are intractable. Lots of different algorithms depending on the target loss function. Knuth “email is a wonderful thing for people whose role in life is to be on top of things. But not for me; my role is to be on the bottom of things. What I do takes long hours of studying and uninterruptible concentration”. He reviews all his postal mail every three months and all his faxes every six”. ([Source](https://www.nytimes.com/2018/12/17/science/donald-knuth-computers-algorithms-programming.html))

* Emails have changed from missing to just delaying everything. Maybe it is better to have vacation notices that don't say “anticipate delay though you’re in the queue” but instead won't let you send your email to begin with!

* The Do not disturb button should instead say “alter me only once every ten minutes, then tell me everything.” There are programs that will stop email until a fixed point in time where all of them are provided and I should really get one of these and turn off my phone more often. I am lucky to be stable enough and in a time insensitive job where I can and should disconnect like this more often.

* Copernican principle. Richard Gott, Berlin wall, 8 years. Doesn’t apply to 80 year old man. The power of having priors.

* Three core distributions, average rule = normal. Multiplicative = power; additive = erlang. Pg 142 figure.

* Movies and TV mess up our priors. Yudkowsky talks about this in see MIRI Global catastrophic risks book, anchoring and availability. Humans talk about what is surprising and interesting same with movies, these fuck up our priors and lead to unrealistic expectations. And if you believe like me that unhappiness is often the delta between expectation and reality this is making you less happy. And the extent to which your map is no longer of the territory, also less rational.

* Overfitting to a dataset and thinking too hard. There are stories of “police officers who find themselves, for instance, taking time out during a gunfight to put their spent casings in their pockets -- good etiquette on a firing range.”

* “Similarly the FBI was forced to change its training after agents were found reflexively firing two shots and then holstering their weapon -- a standard cadence in training -- regardless of whether their shots had hit the target and whether there was still a threat. Mistakes like these are known in law enforcement and the military as “training scaress”. “ In a particularly dramatic case, an officer instinctively grabbed the gun out of the hands of an assailant and then instinctively handed it right back -- just as he had done time and time agains with his trainers in practice.”

* Idea of Jason Fried and David Heinemeir Hansson, of using larger pens like a sharpie when brainstorming to make it impossible to drill into the details of an idea. Forced to just think about the big picture.

* Darwin had his famous pros cons lists like in deciding whether or not to get married. He forced himself to decide by the end of the page. These spatial constraints on thinking are kind of like the hardware determinism in research [Path Dependencies in Compute](https://www.trentonbricken.com/ComputingPathDependencies/).

* The perfect is the enemy of the good - Voltaire.

* Random method to test polynomial identity. Algorithm for finding primes that is random in whether or not it is telling the truth. Core result is that it is faster to validate than it is to search.

* It is polite to give people options and narrow down the search space for them. In planning interviews for the book it was far more effective and got more replies when gave a specific time then let the other person choose. Even if you have weak preferences you should list a few things and let the other person decide between them. Actually lazy to make them solve the hard task and also to model your own mind in doing so.

* Networking packet acknowledgements. Almost 10% of upstream internet traffic during peak hours in 2014 was due to Netflix, which we tend to think of as sending data almost exclusively downstread. But all that video generates an awful lot of ACKs (acknowledgement that transmission was received – the same as when you given short affirmations during a conversation to share you are still listening e.g. on the other side of the phone).

* “WHAT HATH GOD WROUGHT” from the Old Testament was the first long distance telegraph message.

* Additive Increase, Multiplicative Decrease (AIMD) sawtooth. To be at max capacity need to fail, but want to do so in an effective way. Peter Principle. The best halfway house between being stuck and firing people is to have dynamic policy where you use AIMD. “pushing things to the point of failure is indeed sometimes the veset (or the only) way to use all the resources to their fullest.”
“No one is long anxious about being overtaxed, nor long resentful about a missed promotion; both are temporary and frequent correctives, and the system hovers near its equilibrium despite everything changing all the time”.

* Better never than late.

* Networking problem with queues. Being used in the wrong way. Only emerged with having queues that are longer than the processing speed of the modems. The ACKs were getting clogged in and messing up the whole system.

* Fast transmission speed vs delay. Two planes have the same speed but different capacity.

* Nash equilibria exist but finding any real world one is intractable.

* Emotions are prosocial for society. Eg anger. Same with love.

*  “Morality is herd instinct in the individual” - Nietzsche.

* Along the lines of the Vickrey auction and the “revelation principle”, Kind algorithms and incentive design. If you find coordination problems interesting then do read one of my all time favourite pieces by Scott Alexander: [Meditations on Moloch](https://slatestarcodex.com/2014/07/30/meditations-on-moloch/).

---

​​### Footnotes
* footnotes will be placed here. This line is necessary
{:footnotes}

[^noSuprising]: On one hand this is not actually that surprising because the number of people you need to sample still scales with the size of the pool.

[^interestRates]: A good benchmark discount rate is the interest rate on high quality bonds. If you had the money now rather than at a future point, how much money could you have made if you were lending that money and getting interest on it. However, humans tend to actually do hyperbolic discounting of which there is deep and interesting literature on.
