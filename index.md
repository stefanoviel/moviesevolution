---
layout: post
title:  "Frame by Frame: The Kaleidoscopic Evolution of Cinema Over the Decades"
author: Oriol Pascual Anglès, Stefano Viel, Max Sebrechts, Michele Lupini and Stefano Cubeddu
cover:  "/assets/background.png"
---
The evolution of cinema over the years is truly remarkable. From the silent film era of the 1920s to the present day, where we are captivated by awe-inspiring special effects, movies have undergone a transformative journey. But it is not just about what we see and hear while watching movies which has changed. Many other metrics have varied over time such as runtime, budgets, and complexity of movies.

While chatting about the current blockbuster with friends many recurrent ideas come up: “Movies these days? Definitely getting longer. They're stretching out more than ever!”, “Movies these days are just simpler…”, or for the vintage lovers “All the best movies? Yeah, they're done and dusted. The new ones? Not a chance they'll top the classics!”.

In this blog post, we will quantitatively analyze the truthfulness of these and many other claims and see what the data has to say. To achieve that we will use different datasets from sources like [IMDb]([https://developer.imdb.com/non-commercial-datasets/](https://developer.imdb.com/non-commercial-datasets/)) and [CMU Movie Summary Corpus]([https://www.google.com/url?q=http://www.cs.cmu.edu/~ark/personas/&amp;sa=D&amp;source=editors&amp;ust=1702986915157988&amp;usg=AOvVaw31QAT1o9RzjJ_NicsdLmF-](http://www.cs.cmu.edu/~ark/personas/)), scraped data and many others.

## Let’s start with an easy one: did movies become longer in recent years?

To answer this question we focused on evaluating the average length of movies by considering only the 25 most-watched films each year. Why prioritize the most-watched? Well, people's perception of the average movie length varies based on what they're viewing. Even if a particular year featured numerous lengthy films that went unnoticed, these wouldn't significantly impact the perceived average length of movies.

The 25 most popular movies were selected by ranking movies every year by the number of votes on IMDB. We aren’t taking the ratings into account because what we were trying to estimate with this metric is how many people have watched the movie. So a movie can be a perfect 10/10 while only 4 people actually watched it.

The following plot reports a moving average with windows size 5.

![](https://lh7-us.googleusercontent.com/s3_UeHH1KUaGqdW_luSKUtalfYLmnj-cQ0zxaN74v4sMhKcnZfUnjcFM-Qtqg1NJXDd7dePZdTrs3DQHePoKgJU75HkBc8Db0sr5FOKVVn_xm6jvY39c7SNYebWucpahjLaQYEtUDJNgNE7xN1qMwKQ)

The plot shows some clear trends:

* 1930 - 1960: movies’ length continuously increased probably due to the technological development of the movie industry.
* Between 1960 and 1990, movie lengths saw a slight 10-minute drop on average. While it's hard to pinpoint the exact cause, changes in consumer preferences could be a contributing factor.
* 1990 - 2010: a steady increase is visible in this time range with average movie length getting a little higher than in the 60s.

So to finally answer our first question: movies got way longer compared to the earliest movies taken into account (1930s). Movies today are also slightly longer than those in the 80s, which might explain why some have the perception that films have gotten longer. This is particularly true with millennials, as they've experienced a consistent upward trend in movie length throughout their lives.

## The best movies have already been recorded

Similarly to the previous question we only considered the 25 most-voted movies every year and took the average ratings from IMDB. The plot reports a moving average with windows size 5.

![](https://lh7-us.googleusercontent.com/IzpY5rBej6oCRuiOJLLMBy01ETsEv5Ue34D9ssRAjkJxtBxO8_o792RbAScavz7zyBqSPV9n8myEvHehtL6BInRegSIXro47C3oFncGebE0UsPawlkNwekAfnpQQxuhHlFlnlR7Pm-OKP-7Z2nTYyvs)

In this case, the urban myth that movies in the past were better than recent ones seems supported by the data. The best movies were made in the '60s while the worst one's in the ‘80s. One small shortcoming of such analysis is that all these ratings have been done in the last 20 years thus they don’t represent the opinion of people who saw the movie being released.

How did the characteristics of a good change from now compared to the past?

The initial approach to tackle this question was to divide the movies in groups of five years (e.g. 2000-2005, 2005-2010) and for each group we regressed the box office revenue on all the other features. We were hoping to infer the importance of the coefficients from their absolute values and p-values. Our analysis didn’t yield satisfying results, as the budget was the only coefficient that had values significantly different from zero over the years.  In response, we narrowed our focus to the budget, examining how its impact on box office revenue evolved.

But first, since we’re talking about budget, let’s take a quick detour to look at how budgets changed over the year. In the following plots, both the budget and the box office revenue are adjusted for inflation, the data for this adjustment was taken from the U.S Bureau of Labour and Statistics ([https://www.bls.gov/cpi/data.htm](https://www.bls.gov/cpi/data.htm)).

As before, we’re only considering the 25 most-voted movies for every year. And it’s quite clear that the movie industry has gotten way bigger. The inflation-adjusted budget had a four-fold increase in the last 30 years, while the revenue doubled.


Solarized dark             |  Solarized Ocean
:-------------------------:|:-------------------------:
![](https://lh7-us.googleusercontent.com/fCvN-uBok_AqsTDabanV31Vw463H0argQwLMiO-J8jd51mMSEudQFPov1mW1_SA1XGcZ0fHniOWu3fzkz3CJohOlO-H2wMHtsE9P6Ew7ZtJwkw9ClzxaBq_27yLdhm-O3opyTBkEtewmpB0PKmUeXik)  |  ![](https://lh7-us.googleusercontent.com/SVJBtFGa0Mh5kOKzrWRRJHlu4ZSqMTKNuLTPCf4VPVkTE8m8xbISUs_tF0RfIpnkSpFE3N-Ko7mfwSmBwlhX0P_jrPTLu1XcqdeYns-DqL_KuCdjcfTgfwTtJp5B5Of6XtKPyiuuFCnunPdujGsjvOI)



Now, let’s go back to the original question which we now restrict to budget only: did the influence of budget change over time?

The answer is yes. Our findings revealed that, compared to the past, the budget is a more reliable predictor of box office revenue in recent years. We observed a shift in the significance of budget around the year 2004. Regressing the adjusted box office revenue on the adjusted budget for movies before 2004 leads to an R-squared of 0.24, while for movies after 2004 we get an R-squared of 0.53.

The relation between budget and box office revenue can be seen more clearly in the following plots.

![](https://lh7-us.googleusercontent.com/9QvVAbDAC_g4HLflU3Ya0sgCaHDKa-LxtX6n22oHyIv7B5YRncaxWK5pwQr3mNdb6cjF6jTnfMgMcZM1odSmA69RuIZt_2PJt2R01-HdZylZDN9CZTpKmqBWmaIEauw7ZuGCE2AOmVVjPjaOvB9oQ5s)
![](https://lh7-us.googleusercontent.com/LiNNiC8tVd23y_YBkAMlmWy7e19Pejzljc6Md0ER-NqKwK3udN_0vg5A7MwetDhIQ-awZiHAOoTeZbBILfnEL6GEhQZ3iawTUCKwZOJRXrVe8Iw5xviMtiaKCXS6G0OjnZSUS22-JJLS_LXip-te3w8)

Here we can see that the linear regression line better fits the data after 2004. This has an important implication: in the last 20 years, the success of a movie (measured by box office revenue) depends much more on its budget. In the plot before 2004 we can see that there were quite a lot of outliers with low budgets and high box office revenue, showing that it was indeed possible to make a very successful movie with little money. On the other hand, in recent years it's rare to make a successful movie with little money.

## What are the characteristics of movies that age well?

We all know about certain movies that were very popular for a few months after they came out but completely forgotten after one or two years. Conversely, some movies initially went unnoticed by the general public but gained significant popularity several years after their initial publication. We wanted to better understand which characteristics make a movie age well (i.e. become more popular as years go by) and which others make people forget it after a few months.

To evaluate this, we required a metric to gauge how the qualities of movies changed over the years. We utilized the Way Back Machine ([https://web.archive.org/](https://web.archive.org/)) a web archive with periodic snapshots of all the majorly visited web pages on the internet. Luckily for us, it also has an API that enabled us to scrape the IMDB web page of a movie over the years. This allowed us to see how the ratings changed as the movie became older. Specifically, we only scraped the ratings and number of voters after one and five years from the movie’s publication.

From the number of voters and the rating from one and five years after publication, we were able to compute the average rating in the one to five-year period.

We decided to consider the average rating in the period between one and five years as an indicator of how well the movie aged. This is reasonable as it represents the opinions of people watching the movie after the initial hype regarding the movie release was gone.

The average rating in the range of one to five years is compared to the average after one year in the following histogram.

![](https://lh7-us.googleusercontent.com/WfBx50QQ8P8-WlzVak7lC4xxoM98SB269x_a9fe-cPQRUqXP3C3MKTYiwgD97ph4t35YybChhkyZhtJC7oy7xiUc8WY9f4p0hBfErpfYi-cSvqjP-vsp3hiylPWOc47a8csVMrv060xC4eOW8Z1086E)

Next, we regressed the average rating in the period from one to five years after release on different characteristics of the movies. The R-square obtained from the regression is 0.522, which is acceptable given the complexity of the dependent variable we're trying to fit. The following are some of the conclusion that can be draws from the regression:

* The aging of movies highly depends on the reviews after one year (p=0.000 t=29.706). This means that the aging of a movie depends on the initial opinion that people had of it. A unit point increase in the review of a movie after one year leads to a 0.85 increase in the average rating in the following 4 years.
* Adult movies age tend also to age better
* Shorts age worse than the average movie while TV series age better. This logic holds true because TV series have a longer transmission duration. Therefore, within the first five years from the release of the first episode, newer episodes may continue to debut, mirroring the impact of a movie release and thus leading to higher ratings for a longer period of time.

## Unraveling Complexity: The Evolution of Movie Plots

Once upon a time, in the magical world of cinema, storytelling was a tapestry woven with intricate plots, multidimensional characters, and unexpected twists. As the years passed, the evolution of movies took an intriguing turn, leading to a subtle yet noticeable shift in narrative complexity.

In the early days of cinema, storytelling was a craft meticulously honed by visionary directors and passionate screenwriters. The plots were rich with layers, inviting audiences to unravel mysteries and explore the depths of human emotions. Classics like "Citizen Kane" and "Casablanca" set the bar high, showcasing storytelling prowess that captivated audiences worldwide.

As the golden age of Hollywood progressed, filmmakers continued to push the boundaries of complexity. The 1960s and 1970s witnessed the rise of auteurs like Stanley Kubrick and Francis Ford Coppola, who brought intricate narratives to life in films like "2001: A Space Odyssey" and "The Godfather." The audience was challenged, provoked, and ultimately rewarded for their intellectual engagement.

The 1980s and 1990s saw the emergence of blockbuster cinema, with directors like Steven Spielberg and George Lucas creating visually stunning epics that still held onto narrative depth. Films like "E.T. the Extra-Terrestrial" and "Star Wars: Episode V - The Empire Strikes Back" managed to blend spectacle with storytelling prowess, maintaining a delicate balance that enthralled audiences.

However, as we entered the new millennium, a subtle shift began to occur. The rise of franchise filmmaking and the focus on high-concept, marketable ideas led to a simplification of narrative structures. Studios increasingly favored formulaic approaches, relying on established tropes and predictable arcs to ensure mass appeal.

Consider the evolution of superhero movies, once celebrated for their intricate character development and moral quandaries. As the genre exploded in popularity, the emphasis shifted from nuanced storytelling to flashy visuals and crowd-pleasing moments. The rise of interconnected cinematic universes furthered this trend, encouraging a more straightforward and accessible approach to storytelling.

In the quest to quantify the elusive essence of complexity in cinematic storytelling, we started focusing on two main aspects of movies, each shedding light on different facets of the narrative landscape. The first approach directs attention to the metadata of movies, introducing a complexity score derived from the ratio between the number of words in a plot summary and the film's runtime in minutes. Simultaneously, the second approach embarks on a linguistic exploration, measuring the lexical complexity.

## Decoding Cinematic Complexity: At first glance

The initial approach relies on easily computable aspects of movies, specifically, the number of words in the plot summary and the runtime in minutes. By calculating a complexity score as the ratio of plot summary words to runtime in minutes, this method provides a numerical indicator of information density. This ratio serves as a snapshot of the amount of information conveyed per unit of time, enabling a comparative analysis across films of varying lengths.

However, this method inherently assumes that a higher word count in the plot summary correlates with a more complex narrative. While it effectively captures the volume of information, it may overlook the nuances of storytelling intricacy that extend beyond mere quantitative measures. Conversely, extremely short movies are disproportionately favored and may receive a higher score than long and intricate movies, possibly due to the lack of detailed descriptions and the consequent brevity of their plot summaries.

**
