# The Myth of the Tailored Approach: Are Pitchers Treating All Hitters the Same?
## The Numbers Don’t Lie: Pitchers Still Challenge Judge and Ohtani — But Why?
By Scott Silverstein 

-- image 1 -- 
--caption: He may be one of the best hitters in baseball history, but we wouldn’t know it by location data.


I love baseball! I’ve been playing it since I was 3 years old, and to this day, I’m still out on the field. It’s the most cerebral game I’ve ever played, and I love the strategy behind it.

One of my favorite aspects of the game is how decision-making has evolved with data. Through tools like FanGraphs, Baseball Savant, teams hiring PhDs in statistics, and even popularized in movies like Moneyball, the conversation around baseball has shifted. We’ve moved away from outdated stats like pitcher wins and losses toward more advanced metrics like Expected Fielding Independent Pitching (xFIP) and beyond.

With the rise of data-driven decisions, I’ve come to trust most teams — perhaps with the exception of the Rockies and White Sox — like a kid trusts their parents: assuming they can do no wrong . But recently, I’ve started to second-guess that trust. All because a question that has been nagging at me lately:

**Why in the world are pitchers still challenging Aaron Judge and Shohei Ohtani with pitches in the zone?**

To answer that, I’ll start by zooming way out: looking at the history and evolution of pitching in the strike zone. Then I’ll narrow the focus — first to how Judge and Ohtani compare to their peers in walk rates, then how they’re pitched in and out of the strike zone, and finally, which exact zones they’re seeing pitches in. Step by step, we’ll break it down and try to answer that tough question throwing in some modeling here and there to build confidence.

### Evolution of Pitching in the Strikezone

--top 15 walk rate leaders image-- 

Aaron Judge is one of the best hitters ever yet Ted Williams got walked over 29% more often than Judge did, 70% more often then Ohtani. This is true for intentional walks too:

-- Top 15 Single-Season intentional walk totals image-- 

Barry Bonds was intentionally walked approximately 476% more than Aaron Judge in his most intentionally walked season.

This reflects an overal trend in baseball. Times have certainly changed for intentional walks. They have fallen ever since the 90s to mid 00s:

--- league wide intentional walks over time-- 

This is also shown in percentage of overal pitches being pitched in the zone.

---- average in zone% by season ---- 

So, maybe this is the answer? Their walk numbers are down because historically walks were more common and more than ever pitchers are throwing in the zone. This is also supported by the data:

-- bb% distribution last 3 seasons--- 

In terms of degrees of separation, with the exception of Ohtani, they are one degree up from the average walk percentage within the past 3 years. So yes, they are indeed getting walked more often to their peers, but not even close to the difference that Barry Bonds was to his.

--- bb% distribtion bary bonds era-- 

Bonds was unarguably the best hitter of his time and aside from any conversation on steriods, it is quite easy to make the argument he was the best ever. But that being said, Judge has broken records and is miles ahead of the rest of the league just like Bonds was. In fact, Bonds era and current era might be the only two periods in time where there is absolutely zero debate to who the best hitter is in baseball.

### Zoom In: Zone Percentage 

This line gets even fuzzier when you actually take a look at percentage of pitches that are thrown in the zone to each player.

--- zone% comparison---- 
--caption: I took the last three seasons to make sure Ohtani’s statlines are there but to ensure they are focusing on Judge’s truly dominant years.-- 


Including Soto, another widely considered great hitter, this chart clearly shows that they are almost league average in pitches thrown in the strikezone. In fact:

-- zone% distribution last 3 seasons-- 

Ohtani and Judge are within 1 degree of separation from the league average zone%. Take this in, the best hitter in baseball has roughly the same rate of strikes to hit as someone like Ryan McMahon of the Colorado Rockies (not to be mean to McMahon but he has a -5.6 offensive WAR this season).

Then I thought, maybe they know that if they do throw Judge or Ohtani a ball they won’t swing at it. I had to determine how to measure plate discipline for this. So, I made my own stat: Plate Discipline Composite (PDC) Score, which aggregates multiple advanced plate discipline metrics into a single 0–1 score.

**How the PDC Score Was Built: I used the following stats:**

1) Lower is better (inverted): O-Swing%, Z-Swing%, Swing%, SwStr%, F-Strike%, CSW%

2) Higher is better: O-Contact%, Z-Contact%, Contact%, CStr%, BB%, Zone%

**Steps:**

Normalize each stat to a 0–1 scale.
Invert the ones where a lower value means better discipline.
Average all stats to get the final PDC Score.
This creates a holistic measure of how well a player controls the strike zone — not just by walks, but by swing decisions, contact quality, and zone judgment.

With this stat, I took a look at how they compared. I threw in a notably bad player for swinging at balls, Javier Baez, and a notably good player, Juan Soto, to make sure that the stat passed the eye test:

--Pdc score distribution--- 

As you can see Ohtani and Judge are just around league average at this as well. Just in case you don’t trust my new stat, same rings true if you just focus on pitches swung at out of the zone:

-- out of zone swing distribution--- 

So, clearly the patience of the batter does not factor into whether or not pitchers will throw strikes. This really shocked me. I would have thought that there would be some correlation. In fact, this was bugging me so I ran a regression model to see if there was any correlation between outside of the zone swing rate, so how much players chase, and the pitches that get thrown to them in the zone:

--- ols regression results--- 

There are other metrics, but the main one anyone needs to know is the r-squared statistic of .106. This is extremely low in terms of correlation. Usually for a robust number, you want to something close to 1. So, while this regression model is statistically significant — meaning the relationship we’re measuring is real (shown by the P-value)— the R-squared value is just 0.106, which is quite low. That means the model only explains about 10.6% of the variation in how often pitchers throw pitches in the strike zone. In other words, while the hitter’s out-of-zone swing rate (oz_swing_percent) does have an effect, it’s an extremely small one. The majority of the decision-making behind pitch location likely comes from other factors I haven’t accounted for — like pitch count, batter-pitcher matchups or even randomness.

### Zoom In: Pitch Location
So clearly, great hitters are still getting pitches in the zone. But what happens if I zoom in even further and look at where those pitches are being thrown within the zone?

To explore this, I broke down pitch-by-pitch data using the same zone model that Statcast uses — dividing pitch locations into **Heart, Shadow, Chase,** and **Waste** zones (see graphic below, from Baseball Savant):

---zones graphic--- 

To understand general league behavior, I calculated what percentage of pitches go to each of these zones. Here’s what the distribution looks like:

-- Pitch disttribution by zone region--- 

As expected, pitchers tend to throw most of their pitches in the **Heart** and **Shadow** regions — the places closest to the strike zone. This makes intuitive sense. You can’t get a strikeout without throwing strikes, and pitchers have to attack the zone to avoid walks.

That said, I was honestly surprised by how **small the gap** was between Heart and Shadow locations. I expected more pitches to be directed toward the Shadow — around the edges — especially given the increased emphasis on avoiding barrels and inducing weak contact.

One possible explanation: many modern pitching strategies teach pitchers to aim for the **middle of the zone** and rely on pitch movement to pull the ball toward the edge. Every so often, those pitches don’t break as expected and end up staying in the heart of the zone — right where elite hitters can do the most damage.

**So where are they pitching to Judge, Ohtani, and Soto?** 
Let’s take a look:

-- distribution of % of pitches in heart of zone--- 

According to the data:
  - Judge sees only about 1 percentage point fewer pitches in the Heart than league average.
  - Ohtani and Soto? Almost identical to league average.
    
Anecdotally, that feels absurd. Judge, in particular, is clearly more than “one tick” better than the average hitter. To reinforce that, I looked at **slugging percentage on pitches in the heart of the zone.** 

-- slg distribution in heart of zone-- 
-- top players by slg-- 

And yep — Judge and Ohtani are **number one and number two in baseball** in slugging on heart-of-the-zone pitches.

So why are they still seeing average (or near-average) rates of pitches in the Heart? It doesn’t make sense.

This begs the question what is the rest of the league seeing in terms of location around the zone and how does it correlate with hitting stats?

-- correlation heatmap -- 
--- caption:Heatmap showing correlations between stats zone location and hitting stats-- 
So within this graphic, it definitely shows that there is some correlation between the quality of hitting and the location of the pitches thrown to the hitter. There is a clear inverse correlation between how good a hitter is and how often they see pitches in the heart of the zone (zone 1). wOBA and SLG all show negative correlations- meaning that as those offensive numbers go up, the percentage of pitches hitters see in the heart of the zone goes down. This continues with stats like barrel rates and hard hit percentages as well.

In the shadow zone (zone 2), it shows a similar trend but actually with slightly weaker correlations. It does seem that pitchers do reduce shadow zone usage a bit for elite hitters, though not as sharply as they do in the zone.

Also understandibly, the opposite is true for chase zone (zone 3) and waste zone (zone 4). These show positive correlations with hitting stats. This means better hitters are seeing more pitches thrown in areas unlikely to be hit well, reflecting the strategy of intentionally avoiding the strike zone altogether (throw it away and hope that they maybe bite at it).

This is not the whole story however, we have to take a look how the zones overlap to see how much a difference the correlation is making. In other words, there may be a difference, but how different. For that I used what is called an ANOVA model, which will seaparate hitters into an elite, average, and poor hitter category and then see how those groups get pitched to in order to answer the question:

*Do location patterns differ between quality of hitters?*

- pitch location distribution--

The two-way ANOVA model tells us whether two factors — hitter quality (Elite, Average, Poor) and pitch zone (Heart, Shadow, Chase) — meaningfully affect how pitches are distributed, and whether these two factors interact.

In this case, all effects were statistically significant, which means that the differences I observed in the data — between how elite hitters are pitched to versus poor hitters, and across different zones — are unlikely to be due to random chance alone. The p-values for the hitter tier, zone, and their interaction were all extremely low (well below the common threshold of 0.05), confirming that the model has picked up real patterns in the data.

However, statistical significance doesn’t always mean practical significance. When we look at the boxplot, we can see that although the average pitch distributions vary slightly between hitter tiers, the overall spread and overlap of the distributions are large. That means pitchers aren’t drastically changing their approach based on hitter quality — elite hitters are pitched to in much the same way as poor hitters.

In essence:

*Yes, the data shows real, measurable differences, but those differences are small in size. Pitchers seem to follow a fairly consistent strategy, regardless of who is at the plate.*

This suggests that while pitchers may make slight tactical adjustments, they are largely not tailoring pitch locations significantly to the caliber of the hitter — possibly due to limitations in command, risk aversion, or broader pitching philosophies.

This boxplot shows the distribution of pitch locations — categorized into Heart, Shadow, and Chase zones — across different tiers of hitters (Poor, Average, Elite). Each box represents how often pitches were thrown to each zone, depending on hitter quality. While Elite hitters receive slightly fewer pitches in the Heart zone and slightly more in the Shadow, the overlap between groups is substantial. This visual reinforces the statistical conclusion: pitchers make only marginal adjustments based on hitter quality, with a broadly consistent pitch location strategy across the board.

**If they are not making strategic decisions based on locations of the pitches that they throw, what decisions are they making?** 

I thought I would take a look at not location but pitch type: curves, sliders, etc. to see if there is a measurable difference. Using wrc+ as a metric to establish the quality of hitter and set them into above average, average, and below average, I took a look to see distribution of pitches thrown to each category of hitter:

--average pitch type usage by hitter tier-- 

-- pitch usage by hitter-- 

This heatmap shows how each hitter tier (based on wRC+) deviates from the league-average pitch mix across eight pitch types. The numbers represent percentage point differences from the mean. For example, “Below Average” hitters see fastballs (FB%) about 12.18 percentage points more often than the league average, while “Above Average” hitters see them 6.89 points less.

Key takeaways:

  1) Below Average hitters are overwhelmingly attacked with more fastballs, suggesting pitchers are more aggressive or challenge them.
  2) Above Average hitters receive fewer fastballs, indicating pitchers may avoid giving them easier pitches to hit.
  3) There’s subtle variation in offspeed and breaking pitches, but the clearest divergence is in fastball usage.

This visualization supports the idea that pitch selection does adjust with hitter quality — but primarily through the use of fastballs.

Let’s take a deeper look:

-- pitch group usage by hitter-- 
This chart shows how often hitters of different performance levels are thrown fastballs versus offspeed pitches. Hitters are grouped into three tiers based on their wRC+ — a comprehensive offensive stat — and their pitch mix is broken down into two categories: Fastball% and Offspeed%.

The data reveals that below average hitters tend to see more fastballs, as shown by their higher Fastball% values. In contrast, above average hitters face more offspeed pitches, likely a strategic move by pitchers to disrupt timing and avoid hard contact. Average hitters fall somewhere in the middle, with moderate exposure to both pitch types and a wider range of variation.

Overall, the chart suggests a clear trend: pitchers adjust their pitch mix based on hitter quality, relying more on fastballs against weaker hitters and offspeed pitches against stronger ones.

### So do we have an answer?

After diving into league trends, pitch location data, statistical models, and pitch type distributions, the answer to the central question — *Why are Judge and Ohtani still getting pitched to?* — becomes clearer, though still nuanced.

While there is **some strategic adjustment** in how pitchers approach elite hitters — particularly in pitch type — those adjustments are relatively **modest**, especially in terms of location. Elite hitters like Judge and Ohtani **do not receive significantly fewer pitches in the strike zone**, and they are pitched in the **heart of the plate at rates nearly identical to average hitters**. Even when looking at more granular location zones (Heart, Shadow, Chase, Waste), the **differences were statistically real but practically small**.

However, the strongest signal of strategic differentiation emerged when I looked at **pitch mix**. Pitchers appear to challenge **below average hitters with more fastballs**, while they **diversify and lean on offspeed and breaking pitches against elite hitters**. This suggests that **pitch type, not location**, is the primary lever pitchers pull when facing tough opponents.

So what does this tell us?

We are likely witnessing a new era in pitching — one built not around avoidance or fear, but **confidence in stuff**. With advancements in biomechanics, training, and pitch design, pitchers now possess arsenals that allow them to attack hitters head-on. The strategy isn’t to nibble or pitch around dangerous hitters — it’s to **throw elite pitches, even in hittable locations**, and trust that movement, velocity, and deception will do the job.

In essence, Judge and Ohtani are being treated *more similarly* to other hitters than expected — **not because pitchers don’t recognize their talent**, but because the **game has evolved to value stuff over strategy**. Pitchers aren’t tailoring location as much as they’re trusting what they throw.

The real takeaway might not be that pitchers are making a mistake — it’s that they believe the **stuff is good enough to beat anyone**. Even the best.
