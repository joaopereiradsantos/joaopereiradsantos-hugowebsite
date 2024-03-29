---
title: "Tennis (Consensus) Betting Bot - The Theoretical Rollercoaster: £1 to £25k 🚀 (and its Downfall 💀)"
summary: Automated AWS Web Scraper and Consensus-based Positive Expected Value
tags:
- Betting Bot
- Web Scraping
- AWS Architecture
- Python
date: "2023-08-03T00:00:00Z"

# Optional external URL for project (replaces project detail page).
external_link: ""

image:
  caption: Photo by Maurits Bausenhart on Unsplash
  focal_point: Smart

links:
- icon: github
  icon_pack: fab
  name: Private
  url: https://github.com/joaopereiradsantos/tennis-betting-bot
url_code: ""
url_pdf: ""
url_slides: ""
url_video: ""

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: ''
---
# Tennis (Consensus) Betting Bot <!-- omit in toc -->
## Table of contents <!-- omit in toc -->
- [Introduction](#introduction)
    - [An Illustrative Case - Halle ATP 500](#an-illustrative-case---halle-atp-500)
    - [Learning (Quickly) from the Past](#learning-quickly-from-the-past)
    - [A Fusion of Strategies](#a-fusion-of-strategies)
- [Literature Review](#literature-review)
- [Methodology](#methodology)
    - [Web Scraping - Maximizing Data Acquisition with AWS](#web-scraping---maximizing-data-acquisition-with-aws)
    - [Fair Betting and Informed Decisions with Consensus Probability](#fair-betting-and-informed-decisions-with-consensus-probability)
- [Results](#results)
    - [Unconstrained Simulations](#unconstrained-simulations)
    - [Constrained Simulations](#constrained-simulations)
- [Discussion](#discussion)
    - [Betting on the Wisdom of Crowds: Galton's Impact on Bookmakers](#betting-on-the-wisdom-of-crowds-galtons-impact-on-bookmakers)
    - [Promising Insights from Constrained Simulations](#promising-insights-from-constrained-simulations)
    - [Limits for Successful Bettors](#limits-for-successful-bettors)
- [Appendix](#appendix)
    - [AWS Architecture](#aws-architecture)
    - [Kelly Criterion](#kelly-criterion)
- [License](#license)

<br/><br/>

## Introduction<a name="introduction"></a> 

This article delves into the evolution and impact of the Tennis (Consensus) Betting Bot (TCBB) compared to its precursor, the [Tennis Betting Bot (TBB)](https://www.joaopereiradsantos.com/project/tbb/). Guided by the [wisdom of crowd principle](https://en.wikipedia.org/wiki/Wisdom_of_the_crowd) and influenced by ["Beating the Bookies with Their Own Numbers"](https://arxiv.org/vc/arxiv/papers/1710/1710.02824v1.pdf), TCBB employs publicly available odds to identify potential mispriced bets. The study includes web scraping for data acquisition, fair betting using consensus probability, and analysis of diverse betting strategies. Constrained simulations within TCBB show promise, notably in optimizing bank performance. However, a challenge emerges from the potential of bookmakers imposing account limitations, revealing underlying discriminatory practices in the online sports betting sphere.

#### An Illustrative Case - Halle ATP 500<a name="an-illustrative-case---halle-atp-500"></a>
In a recent Halle ATP 500 match between Richard Gasquet and Jannik Sinner, bookmakers favored Gasquet with average decimal odds of approximately 5.00, peaking at 5.39 on Pinnacle. Conversely, TBB projected a 41.15% chance of a Gasquet victory, equivalent to decimal odds of 2.43. Despite Gasquet's eventual loss, this marked a notable 116% difference, prompting a pertinent question: Could TBB's projections surpass those of 25 specialized bookmakers on the long-term?

#### Learning (Quickly) from the Past<a name="learning-quickly-from-the-past"></a>
Reflecting on the prior TBB version driven by machine learning (ML), the 2023 grass season exposed its impracticality. Swiftly changing inputs hindered an effective ML pipeline. The fast changes in information weren't caught quickly enough, making it hard to create a good feedback loop for adjusting the ML system's parameters. This resulted in a devastating -660% return on investment (ROI).

#### A Fusion of Strategies<a name="a-fusion-of-strategies"></a>
Inspired by "Beating the Bookies with their own Numbers" by Kaunitz, Shenjun, and Kreiner, the new TCBB embraces a symbiotic approach. It capitalizes on publicly available odds from various bookmakers to find bets with mispriced odds and positive expected value.

Ahead, we delve into the mechanics of the Tennis (Consensus) Betting Bot, tracing its evolution, strategies, and efficacy across the bookmaker landscape. 
<br/><br/>

## Literature Review<a name="literature-review"></a>

> <font size=5>_"Beating the Bookies with Their Own Numbers" has propelled TCBB to challenge conventions, applying a similar approach to tennis._</font>

In the domain of sports prediction and betting, two pivotal articles have left a substantial impact. ["The Gambler Who Cracked the Horse-Racing Code"](https://www.bloomberg.com/news/features/2018-05-03/the-gambler-who-cracked-the-horse-racing-code) underscores the power of data-driven insights in horse racing betting, while ["Beating the Bookies with Their Own Numbers - and How the Online Sports Betting Market is Rigged"](https://arxiv.org/vc/arxiv/papers/1710/1710.02824v1.pdf) has directly influenced the creation of The Tennis (Consensus) Betting Bot (TCBB), which employs a comparable approach but focuses on tennis.

"Beating the Bookies with Their Own Numbers" introduces a unique methodology that taps into implicit probability information within public odds to uncover mispriced bets. Rigorous simulations spotlight inefficiencies within the football betting market, suggesting the potential for sustained profitability.

While "The Gambler Who Cracked the Horse-Racing Code" underscores analytics' impact in a specific realm, the insights from "Beating the Bookies with Their Own Numbers" has propelled TCBB to challenge conventions, applying a similar approach to tennis. The article's influence serves as both a catalyst and a cautionary tale, prompting a deeper exploration of dynamics within the sports betting arena.
<br/><br/>

## Methodology<a name="methodology"></a>

> <font size=5>_Bookmakers already possess highly accurate models for predicting outcomes in tennis matches._</font>
#### Web Scraping - Maximizing Data Acquisition with AWS<a name="webscrapping"></a>

Web scraping has emerged as a pivotal component within the TCBB project, representing a significant upgrade from the prior TBB scraping method. This section delves into the intricacies of web scraping, elucidating its evolution and pivotal role in procuring data for the TCBB project.

Initially, the TCBB project utilized [the-odds-api](https://the-odds-api.com/) to source data. However, the viability of this approach was hampered by its free tier's restrictions, capping data retrieval at 500 requests per month. Furthermore, [the-odds-api](https://the-odds-api.com/)  failed to encompass data from ITF tournaments and lower liquidity secondary markets, rendering it insufficient for the TCBB project's expanding requirements.

In order to comprehensively capture data spanning diverse sports and markets, the TCBB project adopted a web scraping strategy focused on the website [oddsportal.com](https://www.oddsportal.com/). This platform provides a wealth of data that aligns with the project's scope. The devised web scraping script effectively aggregates bookmakers' odds for a specific game and market, accomplishing this task in approximately 2 seconds. Moreover, opportunities for further optimization lie in the parallelization of scraping processes for each game and market, promising a reduction in overall scraping time.

The deployment and automation facets of web scraping within the TCBB project are seamlessly orchestrated within the AWS Cloud environment. This infrastructure ensures scalability, reliability, and efficient management of scraping operations. A comprehensive depiction of the AWS Architecture is available in [Appendix 1](#aws-architecture) for those seeking in-depth insights into the technical setup.

To underscore the efficacy of the web scraping approach, consider the following example output extracted from the TCBB project's data acquisition process. The provided data pertains to match id [n5Kp6kJP](https://www.oddsportal.com/tennis/china/itf-m15-tianjin-4-men-doubles/erik-arutiunian-ostapenkov-daniil-li-hanwen-sun-qian-n5Kp6kJP), a fixture within the China ITF M15 Tianjin 4 Men Doubles category. This data was garnered post-game, exemplifying the real-time data procurement capabilities of the TCBB web scraping framework.

<details><summary>n5Kp6kJP</summary>

    {
                "Match ID": "n5Kp6kJP",
                "Match Start Timestamp": "2023-07-07 08:30",
                "Last Update Timestamp": "2023-07-07 18:06:28.339731",
                "Match": "Arutiunian E./Ostapenkov D. - Li H./Sun Qian",
                "Player A": "Arutiunian E./Ostapenkov D.",
                "Player B": "Li H./Sun Qian",
                "Score": "1:2",
                "Markets": {
                    "Home-Away Full Time": {
                        "Bookmakers": [
                            {
                                "Bookmaker": "10Bet",
                                "Odds": {
                                    "Player A": "1.57",
                                    "Player B": "2.25"
                                }
                            },
                            {
                                "Bookmaker": "10x10bet",
                                "Odds": {
                                    "Player A": "1.6",
                                    "Player B": "2.25"
                                }
                            },
                            {
                                "Bookmaker": "1xBet",
                                "Odds": {
                                    "Player A": "1.61",
                                    "Player B": "2.21"
                                }
                            },
                            {
                                "Bookmaker": "888sport",
                                "Odds": {
                                    "Player A": "1.53",
                                    "Player B": "2.2"
                                }
                            },
                            {
                                "Bookmaker": "Alphabet",
                                "Odds": {
                                    "Player A": "1.57",
                                    "Player B": "2.25"
                                }
                            },
                            {
                                "Bookmaker": "Betway",
                                "Odds": {
                                    "Player A": "1.55",
                                    "Player B": "2.2"
                                }
                            },
                            {
                                "Bookmaker": "ComeOn",
                                "Odds": {
                                    "Player A": "1.57",
                                    "Player B": "2.25"
                                }
                            },
                            {
                                "Bookmaker": "Curebet",
                                "Odds": {
                                    "Player A": "1.57",
                                    "Player B": "2.25"
                                }
                            },
                            {
                                "Bookmaker": "Dafabet",
                                "Odds": {
                                    "Player A": "1.56",
                                    "Player B": "2.26"
                                }
                            },
                            {
                                "Bookmaker": "GGBET",
                                "Odds": {
                                    "Player A": "1.57",
                                    "Player B": "2.25"
                                }
                            },
                            {
                                "Bookmaker": "Lasbet",
                                "Odds": {
                                    "Player A": "1.57",
                                    "Player B": "2.25"
                                }
                            },
                            {
                                "Bookmaker": "Marathonbet",
                                "Odds": {
                                    "Player A": "1.59",
                                    "Player B": "2.22"
                                }
                            },
                            {
                                "Bookmaker": "Suprabets",
                                "Odds": {
                                    "Player A": "1.57",
                                    "Player B": "2.25"
                                }
                            },
                            {
                                "Bookmaker": "VOBET",
                                "Odds": {
                                    "Player A": "1.57",
                                    "Player B": "2.25"
                                }
                            },
                            {
                                "Bookmaker": "Vulkan Bet",
                                "Odds": {
                                    "Player A": "1.57",
                                    "Player B": "2.25"
                                }
                            },
                            {
                                "Bookmaker": "William Hill",
                                "Odds": {
                                    "Player A": "1.57",
                                    "Player B": "2.25"
                                }
                            }
                        ]
                    },
                    "Home-Away 1st Set": {
                        "Bookmakers": [
                            {
                                "Bookmaker": "10Bet",
                                "Odds": {
                                    "Player A": "1.57",
                                    "Player B": "2.25"
                                }
                            },
                            {
                                "Bookmaker": "10x10bet",
                                "Odds": {
                                    "Player A": "1.62",
                                    "Player B": "2.2"
                                }
                            },
                            {
                                "Bookmaker": "1xBet",
                                "Odds": {
                                    "Player A": "1.64",
                                    "Player B": "2.19"
                                }
                            },
                            {
                                "Bookmaker": "888sport",
                                "Odds": {
                                    "Player A": "1.57",
                                    "Player B": "2.05"
                                }
                            },
                            {
                                "Bookmaker": "Alphabet",
                                "Odds": {
                                    "Player A": "1.6",
                                    "Player B": "2.2"
                                }
                            },
                            {
                                "Bookmaker": "ComeOn",
                                "Odds": {
                                    "Player A": "1.57",
                                    "Player B": "2.25"
                                }
                            },
                            {
                                "Bookmaker": "Curebet",
                                "Odds": {
                                    "Player A": "1.6",
                                    "Player B": "2.2"
                                }
                            },
                            {
                                "Bookmaker": "Dafabet",
                                "Odds": {
                                    "Player A": "1.61",
                                    "Player B": "2.19"
                                }
                            },
                            {
                                "Bookmaker": "GGBET",
                                "Odds": {
                                    "Player A": "1.65",
                                    "Player B": "2.25"
                                }
                            },
                            {
                                "Bookmaker": "Lasbet",
                                "Odds": {
                                    "Player A": "1.6",
                                    "Player B": "2.2"
                                }
                            },
                            {
                                "Bookmaker": "Suprabets",
                                "Odds": {
                                    "Player A": "1.6",
                                    "Player B": "2.2"
                                }
                            },
                            {
                                "Bookmaker": "VOBET",
                                "Odds": {
                                    "Player A": "1.6",
                                    "Player B": "2.2"
                                }
                            },
                            {
                                "Bookmaker": "Vulkan Bet",
                                "Odds": {
                                    "Player A": "1.62",
                                    "Player B": "2.16"
                                }
                            }
                        ]
                    },
                    "Home-Away 2nd Set": {
                        "Bookmakers": [
                            {
                                "Bookmaker": "888sport",
                                "Odds": {
                                    "Player A": "1.6",
                                    "Player B": "2.15"
                                }
                            },
                            {
                                "Bookmaker": "Dafabet",
                                "Odds": {
                                    "Player A": "1.61",
                                    "Player B": "2.19"
                                }
                            },
                            {
                                "Bookmaker": "GGBET",
                                "Odds": {
                                    "Player A": "1.65",
                                    "Player B": "2.25"
                                }
                            },
                            {
                                "Bookmaker": "Vulkan Bet",
                                "Odds": {
                                    "Player A": "1.61",
                                    "Player B": "2.17"
                                }
                            }
                        ]
                    },
                    "Home-Away 3rd Set": {
                        "Bookmakers": []
                    }
                }
    }

</details>

#### Fair Betting and Informed Decisions with Consensus Probability<a name="webscrapping"></a>
A fair bet has zero expected value when the bookmaker's odds are the opposite of the actual likelihood of the outcome. Bookmakers make accurate models to estimate outcome probabilities and then offer odds lower than the fair value. This process resembles casino roulette where the house offers odds slightly lower than fair. For instance, in American roulette, betting on red gives an 18/38 chance to double the wager. The fair value is 2.111, but the house only pays 2, indicating they pay less than fair value. This difference acts as a commission for the bookmaker. In roulette, the house expects to earn 0.053 units (2/38) for every 1 unit bet.

An assessment of bookmakers' predictive accuracy was conducted using historical tennis match data. Closing odds for approximately 20,000 tennis matches held between June and August 2023 were obtained from [oddsportal.com](https://www.oddsportal.com/), with a focus on "Home-Away Full Time" outcomes (player A or player B win).

To quantify accuracy, a consensus probability approach was employed. The consensus probability ({{< math >}}$P_{\text{consensus}}${{< /math >}}) was determined by calculating the inverse of the mean odds ({{< math >}}$Ω${{< /math >}}) favoring either player A or player B:

{{< math >}}
$$
P_{\text{consensus}} = \frac{1}{\text{mean}(Ω)} \tag{1}
$$
{{< /math >}}


The data was categorized into 80 bins based on consensus probabilities ranging from 0 to 1, in increments of 0.0125. Within each bin, two key metrics were computed:

1. The average consensus probabilities at the closing of the matches. ({{< math >}}$P_{\text{consensus}}${{< /math >}})
2. The average accuracy in predicting match outcomes (player or player B win). ({{< math >}}$P_{\text{real}}${{< /math >}})

The following figure depicts the linear regression analysis between the two previously computed variables.

![linear_reg](./pictures/linear_reg.png)


The consensus probability functions as a reliable indicator of the underlying outcome probability. In light of these findings, the choice was made to shape a betting strategy founded on the idea that bookmakers already possess highly accurate models for predicting outcomes in tennis matches:

{{< math >}}
$$
P_{\text{real}} \approx P_{\text{consensus}} - n \tag{2}
$$
{{< /math >}}


We pursued this logical approach to establish our betting strategy, opting to make a wager whenever the highest odds provided for a specific outcome satisfied the subsequent inequality:

{{< math >}}
$$
\max(Ω) > \frac{1}{P_{\text{consensus}} - n} \tag{3}
$$
{{< /math >}}

As the {{< math >}}$n${{< /math >}} parameter increases, the expected value of each bet grows, but the pool of games available for betting shrinks. This effect stems from the stricter condition, resulting in fewer bookmakers providing odds with significant margins. To identify an appropriate {{< math >}}$n${{< /math >}} parameter, we evaluated simulated betting strategies over a range of values, spanning from 0.000 to 0.100. 

To accurately determine the optimal value of {{< math >}}$n${{< /math >}} based on the simulated strategies, various output metrics have been taken into account. These metrics include the total number of games to bet (n_games), the yield (yield_%), accuracy (accuracy_%), bank standard deviation (bank_std_u), bank coeficient of variation (bank_cv_%) and the final bank amount (final_bank_u).

Among the considered bet sizing strategies are flat betting (placing a fixed amount) and the Kelly bet (Kelly Criterion). From these, fractioned Kelly scenarios have been derived, including full-kelly, half-kelly, quarter-kelly, and eight-kelly. Further information about the Kelly Criterion can be found in [Appendix 2](kelly-criterion).

The preferred strategy aims for a positive and reasonable yield percentage, ideally falling within the range of 5% to 10%. Additionally, it seeks to maintain a reasonably high number of games for placing bets and a low level of bank variability.
<br/><br/>

## Results<a name="results"></a>

> <font size=5>_The unconstrained bookmaker approach utilizing the half-kelly criterion (...) reached its pinnacle with a bank amount of 24,276 units on the 26th of July._</font>

The following results are based on both flat betting and fractioned Kelly betting. The distinction between unconstrained and constrained simulations lies in the consideration of bookmakers. Unconstrained simulations encompass all available bookmakers scraped from [oddsportal.com](https://www.oddsportal.com/), while constrained simulations exclusively involve UK-registered bookmakers with tested accounts, including 10Bet, 888sport, bet365, Betfair, Betfred, Betway, bwin, Ladbrokes and William Hill.

Special attention is directed towards the simulation that inspired the title of this article: the unconstrained bookmaker approach utilizing the half-kelly criterion. Notably, this simulation reached its pinnacle with a bank amount of 24,276 units on the 26th of July.

#### Unconstrained Simulations<a name="unconstrained-simulations"></a>

<details><summary>Flat Betting (Assuming a fixed stake = 1u)</summary>

|     n | final_bank_u | n_games | yield_% | accuracy_% | bank_std_u | bank_cv_% |
| ----: | -----------: | ------: | ------: | ---------: | ---------: | --------: |
| 0.000 |     -2410.34 |   36388 |   -6.63 |      49.81 |     687.66 |    -54.28 |
| 0.005 |     -2357.28 |   35643 |   -6.62 |      49.58 |     671.53 |    -53.82 |
| 0.010 |     -2009.45 |   32404 |   -6.20 |      48.99 |     574.96 |    -53.45 |
| 0.015 |     -1412.05 |   26000 |   -5.43 |      47.97 |     419.85 |    -55.28 |
| 0.020 |      -519.92 |   18739 |   -2.78 |      48.76 |     143.30 |    -53.09 |
| 0.025 |      -121.98 |   12560 |   -0.98 |      49.36 |      69.39 |    -56.66 |
| 0.030 |       170.69 |    8211 |    2.07 |      50.60 |      47.58 |    126.12 |
| 0.035 |       196.30 |    5496 |    3.55 |      50.96 |      59.15 |    101.38 |
| 0.040 |       193.37 |    3713 |    5.18 |      51.14 |      62.11 |    103.60 |
| 0.045 |       175.31 |    2556 |    6.82 |      50.94 |      61.73 |     91.16 |
| 0.050 |       157.05 |    1861 |    8.39 |      51.37 |      51.93 |     86.12 |
| 0.055 |       148.75 |    1395 |   10.59 |      51.76 |      45.08 |     79.51 |
| 0.060 |       156.74 |    1090 |   14.29 |      52.20 |      49.96 |     81.42 |
| 0.065 |       141.27 |     868 |   16.16 |      51.96 |      42.63 |     77.91 |
| 0.070 |       126.03 |     717 |   17.44 |      52.02 |      37.92 |     74.05 |
| 0.075 |       130.67 |     608 |   21.33 |      52.63 |      36.17 |     70.00 |
| 0.080 |       122.58 |     519 |   23.43 |      52.60 |      32.37 |     67.12 |
| 0.085 |       111.09 |     445 |   24.74 |      54.16 |      32.23 |     59.58 |
| 0.090 |        93.68 |     397 |   23.35 |      53.40 |      29.58 |     72.02 |
| 0.095 |        89.62 |     347 |   25.54 |      53.03 |      26.41 |     63.78 |
| 0.100 |        85.93 |     306 |   27.75 |      53.59 |      26.13 |     69.55 |

![flat_bet_theo](./pictures/flat_bet_theo.png)

</details>


<details><summary>Full-Kelly (Assuming a starting bank = 1u)</summary>

|     n | final_bank_u | n_games | accuracy_% | yield_% | bank_std_u | bank_cv_% |
| ----: | -----------: | ------: | ---------: | ------: | ---------: | --------: |
| 0.000 |         0.00 |   36388 |      49.81 |   -8.06 |       0.02 |   2358.22 |
| 0.005 |         0.00 |   35643 |      49.58 |   -7.57 |       0.02 |   2261.99 |
| 0.010 |         0.00 |   32404 |      48.99 |   -7.58 |       0.03 |   2130.76 |
| 0.015 |         0.00 |   26000 |      47.97 |   -6.76 |       0.04 |   2009.03 |
| 0.020 |         0.00 |   18739 |      48.76 |   -9.49 |       0.03 |   1590.77 |
| 0.025 |         0.00 |   12560 |      49.36 |   -5.93 |       0.05 |   1302.50 |
| 0.030 |         0.00 |    8211 |      50.60 |   -7.29 |       0.08 |   1474.63 |
| 0.035 |         0.00 |    5496 |      50.96 |   -7.18 |       0.09 |   1060.10 |
| 0.040 |         0.00 |    3713 |      51.14 |  -15.60 |       0.06 |   1085.84 |
| 0.045 |         0.00 |    2556 |      50.94 |   -7.29 |       0.13 |    749.25 |
| 0.050 |         0.00 |    1861 |      51.37 |  -19.22 |       0.07 |    745.38 |
| 0.055 |         0.00 |    1395 |      51.76 |  -28.39 |       0.05 |    716.29 |
| 0.060 |         0.00 |    1090 |      52.20 |  -23.93 |       0.07 |    577.55 |
| 0.065 |         0.00 |     868 |      51.96 |  -16.67 |       0.09 |    388.46 |
| 0.070 |         0.01 |     717 |      52.02 |   -0.84 |       1.24 |    210.02 |
| 0.075 |         0.35 |     608 |      52.63 |   -0.23 |       2.27 |    141.19 |
| 0.080 |         5.22 |     519 |      52.60 |    0.73 |       4.88 |    120.22 |
| 0.085 |        38.59 |     445 |      54.16 |    1.45 |      23.63 |    115.17 |
| 0.090 |        58.65 |     397 |      53.40 |    2.06 |      28.58 |    113.14 |
| 0.095 |        17.92 |     347 |      53.03 |    1.08 |      20.94 |    128.75 |
| 0.100 |       119.90 |     306 |      53.59 |    3.45 |      47.84 |    117.57 |

![f_k_theo](./pictures/f_k_theo.png)

</details>


<details><summary>Half-Kelly (Assuming a starting bank = 1u)</summary>

|     n | final_bank_u | n_games | accuracy_% | yield_% | bank_std_u | bank_cv_% |
| ----: | -----------: | ------: | ---------: | ------: | ---------: | --------: |
| 0.000 |         0.00 |   36388 |      49.81 |   -4.55 |       0.05 |   1402.44 |
| 0.005 |         0.00 |   35643 |      49.58 |   -4.38 |       0.05 |   1364.17 |
| 0.010 |         0.00 |   32404 |      48.99 |   -4.44 |       0.05 |   1280.98 |
| 0.015 |         0.00 |   26000 |      47.97 |   -3.40 |       0.07 |    936.15 |
| 0.020 |         0.00 |   18739 |      48.76 |   -4.09 |       0.07 |    890.28 |
| 0.025 |         0.00 |   12560 |      49.36 |   -4.87 |       0.10 |    944.19 |
| 0.030 |         0.00 |    8211 |      50.60 |   -7.66 |       0.09 |    899.72 |
| 0.035 |         0.00 |    5496 |      50.96 |   -7.62 |       0.12 |    750.03 |
| 0.040 |         0.00 |    3713 |      51.14 |  -14.37 |       0.08 |    719.85 |
| 0.045 |         0.08 |    2556 |      50.94 |   -0.81 |       0.37 |    123.68 |
| 0.050 |        49.74 |    1861 |      51.37 |    0.59 |      60.32 |    198.68 |
| 0.055 |      1175.07 |    1395 |      51.76 |    7.03 |     194.45 |    233.05 |
| 0.060 |     16768.13 |    1090 |      52.20 |    5.43 |    3929.18 |    199.77 |
| 0.065 |      2276.34 |     868 |      51.96 |    4.45 |     586.57 |    145.67 |
| 0.070 |      2969.12 |     717 |      52.02 |    3.53 |    1154.32 |    141.41 |
| 0.075 |      4562.71 |     608 |      52.63 |    7.49 |    1201.06 |    169.57 |
| 0.080 |      4578.19 |     519 |      52.60 |   10.76 |    1058.85 |    176.26 |
| 0.085 |      5486.35 |     445 |      54.16 |   12.03 |    1223.85 |    168.85 |
| 0.090 |      3007.96 |     397 |      53.40 |   13.37 |     660.72 |    164.99 |
| 0.095 |       846.36 |     347 |      53.03 |   12.61 |     181.12 |    132.29 |
| 0.100 |      1133.21 |     306 |      53.59 |   15.02 |     262.67 |    146.41 |

![h_k_theo](./pictures/h_k_theo.png)

</details>


<details><summary>Quarter-Kelly (Assuming a starting bank = 1u)</summary>

|     n | final_bank_u | n_games | accuracy_% | yield_% | bank_std_u | bank_cv_% |
| ----: | -----------: | ------: | ---------: | ------: | ---------: | --------: |
| 0.000 |         0.00 |   36388 |      49.81 |   -3.59 |       0.07 |    878.63 |
| 0.005 |         0.00 |   35643 |      49.58 |   -3.48 |       0.08 |    843.47 |
| 0.010 |         0.00 |   32404 |      48.99 |   -3.26 |       0.08 |    738.96 |
| 0.015 |         0.00 |   26000 |      47.97 |   -2.43 |       0.12 |    620.12 |
| 0.020 |         0.00 |   18739 |      48.76 |   -3.12 |       0.12 |    550.93 |
| 0.025 |         0.00 |   12560 |      49.36 |   -4.89 |       0.12 |    574.61 |
| 0.030 |         1.31 |    8211 |      50.60 |    0.28 |       0.26 |    147.23 |
| 0.035 |        83.69 |    5496 |      50.96 |    1.86 |      15.10 |    144.43 |
| 0.040 |       123.44 |    3713 |      51.14 |    3.00 |      20.23 |    140.77 |
| 0.045 |       277.42 |    2556 |      50.94 |    2.29 |      92.83 |    145.23 |
| 0.050 |      1188.58 |    1861 |      51.37 |    3.96 |     359.75 |    164.45 |
| 0.055 |      1746.77 |    1395 |      51.76 |   10.93 |     308.81 |    197.53 |
| 0.060 |      3096.49 |    1090 |      52.20 |    9.94 |     677.73 |    174.32 |
| 0.065 |       711.24 |     868 |      51.96 |    9.38 |     160.20 |    136.47 |
| 0.070 |       548.44 |     717 |      52.02 |    8.72 |     148.91 |    125.00 |
| 0.075 |       503.76 |     608 |      52.63 |   12.88 |     120.59 |    136.40 |
| 0.080 |       386.59 |     519 |      52.60 |   15.71 |      91.10 |    135.32 |
| 0.085 |       353.02 |     445 |      54.16 |   16.86 |      82.64 |    127.73 |
| 0.090 |       220.67 |     397 |      53.40 |   18.11 |      51.27 |    120.44 |
| 0.095 |       101.54 |     347 |      53.03 |   17.63 |      23.10 |     99.86 |
| 0.100 |       102.67 |     306 |      53.59 |   20.31 |      24.92 |    105.38 |

![q_k_theo](./pictures/q_k_theo.png)

</details>


<details><summary>Eighth-Kelly (Assuming a starting bank = 1u)</summary>

|     n | final_bank_u | n_games | accuracy_% | yield_% | bank_std_u | bank_cv_% |
| ----: | -----------: | ------: | ---------: | ------: | ---------: | --------: |
| 0.000 |         0.00 |   36388 |      49.81 |   -2.87 |       0.11 |    500.56 |
| 0.005 |         0.00 |   35643 |      49.58 |   -2.80 |       0.11 |    483.83 |
| 0.010 |         0.00 |   32404 |      48.99 |   -2.35 |       0.12 |    396.78 |
| 0.015 |         0.00 |   26000 |      47.97 |   -1.77 |       0.17 |    307.29 |
| 0.020 |         0.00 |   18739 |      48.76 |   -1.64 |       0.17 |    209.96 |
| 0.025 |         0.16 |   12560 |      49.36 |   -1.51 |       0.16 |    143.53 |
| 0.030 |       137.80 |    8211 |      50.60 |    3.63 |      24.89 |    212.05 |
| 0.035 |       249.42 |    5496 |      50.96 |    3.62 |      47.75 |    148.58 |
| 0.040 |       116.15 |    3713 |      51.14 |    4.68 |      22.14 |    128.43 |
| 0.045 |        88.09 |    2556 |      50.94 |    4.40 |      24.54 |    118.96 |
| 0.050 |       120.63 |    1861 |      51.37 |    6.51 |      34.24 |    130.02 |
| 0.055 |       110.66 |    1395 |      51.76 |   11.81 |      23.89 |    133.85 |
| 0.060 |       122.96 |    1090 |      52.20 |   12.18 |      30.71 |    124.26 |
| 0.065 |        52.51 |     868 |      51.96 |   11.82 |      13.52 |    101.48 |
| 0.070 |        41.96 |     717 |      52.02 |   12.03 |      11.98 |     94.16 |
| 0.075 |        37.40 |     608 |      52.63 |   15.46 |       9.69 |     92.67 |
| 0.080 |        30.74 |     519 |      52.60 |   17.98 |       7.89 |     89.31 |
| 0.085 |        28.08 |     445 |      54.16 |   19.20 |       7.15 |     83.61 |
| 0.090 |        21.30 |     397 |      53.40 |   20.38 |       5.34 |     77.76 |
| 0.095 |        13.95 |     347 |      53.03 |   19.94 |       3.34 |     64.54 |
| 0.100 |        13.57 |     306 |      53.59 |   22.93 |       3.40 |     67.13 |

![e_k_theo](./pictures/e_k_theo.png)


</details>

#### Constrained Simulations<a name="constrained-simulations"></a>

<details><summary>Flat Betting (Assuming a fixed stake = 1u)</summary>

|     n | final_bank_u | n_games | yield_% | accuracy_% | bank_std_u | bank_cv_% |
| ----: | -----------: | ------: | ------: | ---------: | ---------: | --------: |
| 0.000 |     -2899.88 |   32034 |   -9.06 |      49.55 |     832.90 |    -55.18 |
| 0.005 |     -2393.36 |   27351 |   -8.75 |      49.03 |     691.79 |    -55.47 |
| 0.010 |     -1617.53 |   20506 |   -7.89 |      48.12 |     456.79 |    -53.57 |
| 0.015 |      -713.40 |   13448 |   -5.31 |      48.36 |     204.93 |    -48.12 |
| 0.020 |      -293.05 |    7985 |   -3.68 |      49.69 |      76.58 |    -44.31 |
| 0.025 |      -106.65 |    4515 |   -2.38 |      50.68 |      48.05 |    -46.54 |
| 0.030 |        38.59 |    2565 |    1.47 |      52.24 |      19.84 |   -128.87 |
| 0.035 |        60.50 |    1548 |    3.84 |      52.45 |      23.96 |    431.10 |
| 0.040 |        67.68 |     961 |    6.94 |      51.72 |      22.40 |    126.29 |
| 0.045 |        48.04 |     631 |    7.45 |      50.08 |      12.54 |     87.76 |
| 0.050 |        42.01 |     449 |    9.13 |      48.78 |      12.16 |     94.36 |
| 0.055 |        48.68 |     340 |   14.02 |      49.12 |      14.34 |     83.93 |
| 0.060 |        40.62 |     278 |   14.25 |      48.20 |      11.93 |     85.22 |
| 0.065 |        49.00 |     232 |   20.69 |      48.71 |      14.07 |     79.65 |
| 0.070 |        44.92 |     198 |   22.18 |      50.00 |      13.29 |     70.38 |
| 0.075 |        47.69 |     178 |   26.23 |      50.00 |      13.37 |     64.77 |
| 0.080 |        48.04 |     155 |   30.35 |      50.97 |      13.89 |     64.44 |
| 0.085 |        46.86 |     144 |   31.85 |      50.69 |      13.84 |     60.66 |
| 0.090 |        35.43 |     128 |   26.90 |      47.66 |      11.44 |     76.43 |
| 0.095 |        35.62 |     114 |   30.37 |      47.37 |      11.84 |     72.42 |
| 0.100 |        38.80 |      99 |   38.18 |      48.48 |      12.89 |     83.26 |

![flat_bet_elig](./pictures/flat_bet_elig.png)

</details>


<details><summary>Full-Kelly (Assuming a starting bank = 1u)</summary>

|     n | final_bank_u | n_games | accuracy_% | yield_% | bank_std_u | bank_cv_% |
| ----: | -----------: | ------: | ---------: | ------: | ---------: | --------: |
| 0.000 |         0.00 |   32034 |      49.55 |   -8.69 |       0.02 |   2294.34 |
| 0.005 |         0.00 |   27351 |      49.03 |   -4.68 |       0.04 |   1961.00 |
| 0.010 |         0.00 |   20506 |      48.12 |   -5.68 |       0.05 |   1836.61 |
| 0.015 |         0.00 |   13448 |      48.36 |   -2.59 |       0.12 |   1374.20 |
| 0.020 |         0.00 |    7985 |      49.69 |  -10.92 |       0.04 |   1659.85 |
| 0.025 |         0.00 |    4515 |      50.68 |  -12.73 |       0.05 |   1237.01 |
| 0.030 |         0.00 |    2565 |      52.24 |  -12.75 |       0.07 |    881.07 |
| 0.035 |         0.00 |    1548 |      52.45 |  -11.83 |       0.12 |    815.67 |
| 0.040 |         0.00 |     961 |      51.72 |  -31.30 |       0.06 |    786.41 |
| 0.045 |         0.00 |     631 |      50.08 |  -19.70 |       0.12 |    503.08 |
| 0.050 |         0.00 |     449 |      48.78 |   -8.79 |       0.15 |    198.23 |
| 0.055 |         0.08 |     340 |      49.12 |   -1.11 |       0.97 |    130.82 |
| 0.060 |         0.18 |     278 |      48.20 |   -0.52 |       2.21 |    122.25 |
| 0.065 |         0.27 |     232 |      48.71 |   -0.43 |       3.09 |    128.52 |
| 0.070 |         5.82 |     198 |      50.00 |    1.88 |       4.75 |    105.61 |
| 0.075 |         5.29 |     178 |      50.00 |    2.43 |       3.89 |    103.87 |
| 0.080 |         7.82 |     155 |      50.97 |    4.34 |       3.87 |    100.24 |
| 0.085 |         6.08 |     144 |      50.69 |    3.19 |       3.65 |     85.19 |
| 0.090 |         1.39 |     128 |      47.66 |    0.78 |       1.07 |     71.71 |
| 0.095 |         1.17 |     114 |      47.37 |    0.32 |       1.15 |     63.16 |
| 0.100 |         4.92 |      99 |      48.48 |    6.10 |       2.90 |    105.55 |

![f_k_elig](./pictures/f_k_elig.png)

</details>


<details><summary>Half-Kelly (Assuming a starting bank = 1u)</summary>

|     n | final_bank_u | n_games | accuracy_% | yield_% | bank_std_u | bank_cv_% |
| ----: | -----------: | ------: | ---------: | ------: | ---------: | --------: |
| 0.000 |         0.00 |   32034 |      49.55 |   -4.42 |       0.05 |   1224.71 |
| 0.005 |         0.00 |   27351 |      49.03 |   -2.94 |       0.07 |   1049.01 |
| 0.010 |         0.00 |   20506 |      48.12 |   -4.18 |       0.07 |   1046.90 |
| 0.015 |         0.00 |   13448 |      48.36 |   -1.84 |       0.19 |    772.40 |
| 0.020 |         0.00 |    7985 |      49.69 |   -8.65 |       0.07 |    854.82 |
| 0.025 |         0.00 |    4515 |      50.68 |   -9.28 |       0.08 |    654.66 |
| 0.030 |         0.00 |    2565 |      52.24 |   -6.87 |       0.13 |    414.17 |
| 0.035 |         0.02 |    1548 |      52.45 |   -4.83 |       0.15 |    191.84 |
| 0.040 |         0.09 |     961 |      51.72 |   -4.59 |       0.12 |     91.01 |
| 0.045 |         0.45 |     631 |      50.08 |   -1.48 |       0.20 |     52.52 |
| 0.050 |         1.99 |     449 |      48.78 |    0.79 |       1.27 |     67.71 |
| 0.055 |        16.57 |     340 |      49.12 |    4.99 |       6.06 |     92.47 |
| 0.060 |        13.42 |     278 |      48.20 |    5.11 |       4.88 |     78.03 |
| 0.065 |        10.94 |     232 |      48.71 |    5.40 |       4.50 |     77.50 |
| 0.070 |        27.90 |     198 |      50.00 |   13.17 |       8.38 |    106.63 |
| 0.075 |        21.01 |     178 |      50.00 |   14.20 |       6.40 |    103.03 |
| 0.080 |        20.48 |     155 |      50.97 |   16.73 |       6.30 |    109.42 |
| 0.085 |        15.38 |     144 |      50.69 |   14.80 |       4.66 |     88.96 |
| 0.090 |         6.09 |     128 |      47.66 |   11.82 |       1.83 |     68.85 |
| 0.095 |         4.62 |     114 |      47.37 |    9.73 |       1.37 |     52.63 |
| 0.100 |         6.89 |      99 |      48.48 |   16.98 |       2.48 |     83.24 |

![h_k_elig](./pictures/h_k_elig.png)

</details>


<details><summary>Quarter-Kelly (Assuming a starting bank = 1u)</summary>

|     n | final_bank_u | n_games | accuracy_% | yield_% | bank_std_u | bank_cv_% |
| ----: | -----------: | ------: | ---------: | ------: | ---------: | --------: |
| 0.000 |         0.00 |   32034 |      49.55 |   -3.52 |       0.08 |    831.63 |
| 0.005 |         0.00 |   27351 |      49.03 |   -2.44 |       0.11 |    670.30 |
| 0.010 |         0.00 |   20506 |      48.12 |   -3.44 |       0.10 |    631.85 |
| 0.015 |         0.00 |   13448 |      48.36 |   -1.94 |       0.20 |    432.59 |
| 0.020 |         0.00 |    7985 |      49.69 |   -4.01 |       0.11 |    279.02 |
| 0.025 |         0.02 |    4515 |      50.68 |   -4.84 |       0.14 |    258.42 |
| 0.030 |         4.07 |    2565 |      52.24 |    2.44 |       0.59 |     96.87 |
| 0.035 |         8.08 |    1548 |      52.45 |    2.36 |       2.45 |    100.38 |
| 0.040 |         4.12 |     961 |      51.72 |    2.53 |       1.43 |     86.68 |
| 0.045 |         3.85 |     631 |      50.08 |    3.76 |       1.03 |     64.56 |
| 0.050 |         4.91 |     449 |      48.78 |    4.60 |       1.51 |     57.95 |
| 0.055 |        10.45 |     340 |      49.12 |    9.83 |       3.01 |     74.23 |
| 0.060 |         8.19 |     278 |      48.20 |   10.20 |       2.24 |     61.30 |
| 0.065 |         6.75 |     232 |      48.71 |   10.97 |       1.92 |     57.98 |
| 0.070 |         9.61 |     198 |      50.00 |   18.10 |       2.38 |     66.24 |
| 0.075 |         7.89 |     178 |      50.00 |   19.06 |       1.93 |     61.97 |
| 0.080 |         7.39 |     155 |      50.97 |   21.67 |       1.81 |     63.21 |
| 0.085 |         6.16 |     144 |      50.69 |   20.21 |       1.47 |     53.79 |
| 0.090 |         3.70 |     128 |      47.66 |   17.24 |       0.82 |     42.49 |
| 0.095 |         3.08 |     114 |      47.37 |   15.56 |       0.65 |     34.30 |
| 0.100 |         3.55 |      99 |      48.48 |   22.64 |       0.90 |     47.09 |

![q_k_elig](./pictures/q_k_elig.png)

</details>


<details><summary>Eighth-Kelly (Assuming a starting bank = 1u)</summary>

|     n | final_bank_u | n_games | accuracy_% | yield_% | bank_std_u | bank_cv_% |
| ----: | -----------: | ------: | ---------: | ------: | ---------: | --------: |
| 0.000 |         0.00 |   32034 |      49.55 |   -3.35 |       0.11 |    538.40 |
| 0.005 |         0.00 |   27351 |      49.03 |   -2.23 |       0.15 |    399.78 |
| 0.010 |         0.00 |   20506 |      48.12 |   -2.69 |       0.14 |    331.98 |
| 0.015 |         0.00 |   13448 |      48.36 |   -1.33 |       0.26 |    185.44 |
| 0.020 |         0.55 |    7985 |      49.69 |   -0.25 |       0.43 |     74.40 |
| 0.025 |         1.62 |    4515 |      50.68 |    0.81 |       0.28 |     65.43 |
| 0.030 |         9.16 |    2565 |      52.24 |    4.29 |       1.64 |     87.52 |
| 0.035 |         7.39 |    1548 |      52.45 |    4.06 |       1.99 |     77.64 |
| 0.040 |         3.82 |     961 |      51.72 |    4.34 |       1.08 |     62.26 |
| 0.045 |         3.02 |     631 |      50.08 |    5.49 |       0.66 |     43.04 |
| 0.050 |         3.03 |     449 |      48.78 |    6.77 |       0.70 |     38.52 |
| 0.055 |         4.12 |     340 |      49.12 |   12.10 |       0.97 |     45.07 |
| 0.060 |         3.52 |     278 |      48.20 |   12.80 |       0.75 |     36.76 |
| 0.065 |         3.13 |     232 |      48.71 |   13.91 |       0.66 |     34.17 |
| 0.070 |         3.63 |     198 |      50.00 |   19.89 |       0.70 |     35.74 |
| 0.075 |         3.24 |     178 |      50.00 |   20.78 |       0.60 |     32.63 |
| 0.080 |         3.10 |     155 |      50.97 |   23.29 |       0.57 |     32.52 |
| 0.085 |         2.80 |     144 |      50.69 |   22.47 |       0.48 |     28.50 |
| 0.090 |         2.14 |     128 |      47.66 |   19.54 |       0.32 |     22.50 |
| 0.095 |         1.93 |     114 |      47.37 |   18.46 |       0.27 |     18.82 |
| 0.100 |         2.04 |      99 |      48.48 |   24.97 |       0.34 |     24.30 |

![e_k_elig](./pictures/e_k_elig.png)
</details>
<br/><br/>

## Discussion<a name="discussion"></a>

> <font size=5>_Bookmakers could swiftly enforce limitations on accounts, resulting in the suspension of betting activities._</font>

#### Betting on the [Wisdom of Crowds](https://en.wikipedia.org/wiki/The_Wisdom_of_Crowds): Galton's Impact on Bookmakers<a name="unconstrained-simulations"></a>
The advancements of the TCBB, is contrasted with its predecessor TBB, which relies on neural network-based predictions. The concept of utilizing collective intelligence is rooted in observations made by Sir Francis Galton in 1907, where the average guesses of a crowd closely approximated the actual weight of an ox. This idea has been applied in various fields, including ensemble learning in machine learning algorithms. Similarly, in the sports markets, each bookmaker serves as a predictor, and the average odds represent aggregated information. These predictions encompass punters' preferences and opinions, influencing odds based on demand. Given bookmakers' adept predictive models, competing in forecasting game outcomes poses challenges. Prior attempts to outperform the football market with expert strategies yielded inconsistent results (e.g.: ["How Efficient Is the European Football Betting Market? Evidence from Arbitrage and Trading Strategies"](https://www.researchgate.net/publication/46559603_How_Efficient_Is_the_European_Football_Betting_Market_Evidence_from_Arbitrage_and_Trading_Strategies)).

#### Promising Insights from Constrained Simulations<a name="unconstrained-simulations"></a>
Although conclusive statements about the long-term efficacy of the consensus remain cautious due to the need for an extended analysis horizon, the outcomes of constrained simulations show promise. Specifically, employing flat betting with {{< math >}}$n${{< /math >}} ≥ 4% yields an average of about 10 available daily betting opportunities, characterized by a balanced yield percentage and sustainable bank variability. Notably, the more fractioned the Kelly bet becomes, the more consistent the simulation results demonstrate. For instance, the eight-kelly strategy has proven profitable at {{< math >}}$n${{< /math >}} > 1.5% with low bank variability, while the full-kelly strategy only realized profits at {{< math >}}$n${{< /math >}} > 5% and exhibited bank variability four times higher.

#### Limits for Successful Bettors<a name="unconstrained-simulations"></a>
Upon entering the sphere of betting, there is a possibility that bookmakers could swiftly enforce limitations on accounts, resulting in the suspension of betting activities. This potential occurrence brings to light evident discriminatory practices inherent within the online sports betting sector. In this context, individuals showcasing success in their betting ventures might encounter constraints that ultimately hinder their sustained involvement in betting pursuits.
<br/><br/>

## Appendix<a name="appendix"></a>

#### AWS Architecture<a name="aws-architecture"></a>

![aws_diagram](./pictures/aws_diagram.png)

The AWS architecture for web scraping is thoughtfully constructed to ensure a seamless and robust data collection and utilization process. It commences with the utilization of ECS Fargate instances, which leverage the advantages of serverless containerization and the ability to scale horizontally. This approach is chosen over Lambda functions' limited execution time and EC2's configuration overhead.

The collected data finds its secure home in Amazon S3, providing durability and easy accessibility. To maintain data integrity and order, Amazon SQS FIFO is employed for message processing. This ensures that the scraped data is not only gathered but also managed reliably.

The orchestration of these components is facilitated by AWS Step Functions, orchestrating a sequence of Lambda functions. These functions serve to not only persistently store the scraped data into DynamoDB but also to transform it into a tabular format, optimizing it for streamlined analysis.

Furthermore, the architecture includes an additional step triggered after the second S3 bucket. This step involves a specialized Lambda function, designed to detect specific conditions within the data. Should these conditions be met, the Lambda function initiates an SNS email notification, providing a proactive means of addressing critical scenarios.

In addition to these operational aspects, the architecture takes advantage of the structured data stored in S3. By utilizing Amazon Athena, ad-hoc querying and historical exploration become feasible. QuickSight's interactive visualizations and dashboards provide valuable insights for data-driven decision-making. In this way, the architecture is not only geared towards efficient data collection and processing but also towards deriving actionable insights and enabling swift responses.

#### Kelly Criterion<a name="kelly-criterion"></a>

The Kelly criterion is a formula used to determine the optimal size of a bet in probability theory. It maximizes the expected value of the logarithm of wealth, equivalent to maximizing the expected geometric growth rate, under the assumption that expected returns are known and the bettor values their wealth logarithmically. This criterion has practical applications in gambling and investment management, with its concepts embraced by successful investors like Warren Buffett. It calculates the ideal portion of a bankroll to wager, based on the probability of winning and losing and the potential payoff. It provides a method for rational decision-making in betting scenarios, aiming to maximize long-term growth while accounting for risk.

Where losing the bet involves losing the entire wager, the Kelly bet is: 

{{< math >}}
$$
f^{\text{*}} = p - \frac{q}{b} = p - \frac{1 - p}{b} \tag{4}
$$
{{< /math >}}

where:
{{< math >}}$f^{\text{*}}${{< /math >}} is the fraction of the current bankroll to wager.
{{< math >}}$p${{< /math >}} is the probability of a win.
{{< math >}}$q${{< /math >}} is the probability of a loss ({{< math >}}$1 - p${{< /math >}}).
{{< math >}}$b${{< /math >}} is the decimal odd.

## License<a name="license"></a>
[MIT](https://choosealicense.com/licenses/apache-2.0/)