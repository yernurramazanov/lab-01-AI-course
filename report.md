# Lab 01 — The Price of One Request



## 1. Part 1 Prediction vs. Measured Value



Before running Part 2, I predicted the token ratios based mainly on UTF-8 byte size.



| Language | Prediction | Measured on Claude Opus 5 |

|---|---:|---:|

| Russian / English | 1.90x | 1.46x |

| Kazakh / English | 2.10x | 2.15x |



The measured complaint token counts were 92 tokens for English, 134 for Russian, and 198 for Kazakh. The Kazakh prediction was close to the measured result, while the Russian token cost was lower than predicted.



## 2. Annual Cost



I assume 5,000 support requests per day as a realistic workload for a medium-sized customer support queue.



| Model | English | Russian | Kazakh |

|---|---:|---:|---:|

| Haiku 4.5 | $9,791 | $10,127 | $12,751 |

| Sonnet 5 | $19,582 | $20,254 | $25,503 |

| Opus 5 | $48,956 | $50,635 | $63,756 |

| Fable 5.1 | $97,911 | $101,269 | $127,513 |



For Opus 5, Kazakh input used 2.19x as many tokens as English, while the total annual bill was 1.30x higher because output tokens were the largest part of the cost.



## 3. Production Model for a Kazakh Support Queue



I would use Claude Opus 5 for a customer-facing Kazakh-language support queue. In our tests, both Haiku 4.5 and Opus 5 correctly avoided inventing the reason for the interest-rate change and suggested a concrete next step. However, Haiku's Kazakh response contained several unnatural and incorrect phrases, while Opus produced a clearer and more natural Kazakh response.



The cost difference is significant: using the models' measured answers at 5,000 Kazakh requests per day, Haiku 4.5 costs about $5,451 per year, while Opus 5 costs about $63,756 per year. For this use case, I would accept the higher cost because response quality and clarity are important in customer-facing support.



## 4. Cost-Reduction Lever



A cost-reduction lever not used in this lab is prompt caching, which can reduce input cost by reusing the repeated system prompt across many requests.

