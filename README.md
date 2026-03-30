## Table 1

RLHF alignment results on Arena Hard v0.1 for the PPO-tuned BNRM policy model based on Llama-3.1-8B-Instruct. The results are evaluated by GPT-4.1 and two human experts, and all win, tie, and lose rates are reported from the BNRM side.

### GPT-4.1 evaluation

| Evaluator | Model | Opponent | Win rate | Tie rate | Lose rate |
|---|---|---|---:|---:|---:|
| GPT-4.1 | BNRM | Llama-3.1-8B-Instruct | 0.4989 | 0.2772 | 0.2239 |
| GPT-4.1 | BNRM | Mistral-7B-Instruct | 0.5850 | 0.2045 | 0.2105 |

### Human evaluation

| Evaluator | Model | Opponent | Win rate | Tie rate | Lose rate |
|---|---|---|---:|---:|---:|
| Human evaluator 1 | BNRM | Llama-3.1-8B-Instruct | 0.5200 | 0.0600 | 0.4200 |
| Human evaluator 2 | BNRM | Llama-3.1-8B-Instruct | 0.5000 | 0.3000 | 0.2000 |
| Human Average | BNRM | Llama-3.1-8B-Instruct | 0.5100 | 0.1800 | 0.3100 |

## Table 2

Response length statistics on Arena-Hard v0.1 for the BNRM-aligned policy model based on Llama-3.1-8B-Instruct compared with the base Llama-3.1-8B-Instruct model.

| Model | Count | Mean tokens | Min | Max | Total tokens |
|---|---:|---:|---:|---:|---:|
| BNRM | 498 | 667.44 | 613.50 | 6 | 2048 | 332384 |
| Base | 498 | 852.84 | 581.50 | 20 | 4097 | 424716 |

## Table 3

Comparison of factor interpretability between the main-experiment BNRM and variants across different runs, a different model, and a different dataset. Here, the different model setting uses Gemma2-2B-it, and the different dataset setting uses Skywork-Preference-v0.2 (SP).

| Semantic family | Main-exp. BNRM | Different runs-1 | Different runs-2 | Different model | Different dataset |
|---|---|---|---|---|---|
| Prompt repetition / marker leakage | 236, 55, 421 | -- | 231, 490, 746, 959 | 285 | 1 |
| Overly shallow responses / one-line code / incomplete implementation | 238, 586, 545, 443 | 264, 737, 821, 884 | 128, 396 | 146, 456 | 65, 1020 |
| Step-by-step guidance / list-style / template-like how-to | 493, 491 | 370 | 182 | 146 | 587, 958, 972 |
| Safety refusal / safety-domain behavior / polite alternative suggestions | 343, 433 | 205, 823, 917 | 396, 966 | 428, 749 | 65, 662, 958 |
| Mathematical / formal / concise problem-solving style | 918 | 536, 821 | -- | -- | 856 |
| Low-quality / meaningless / chaotic outputs | 2 | -- | 93, 839 | 285 | 1 |
| Unsafe direct compliance / harmful enumeration / unsafe compliance | 691 | 823 | 411, 422 | 146, 456 | 662 |

## Table 4

**Performance comparison between BNRM and BT on four different datasets under the lowest-performing BNRM setting, $\eta = 10^{-6}$.**

| Method | UF | HHH | MTBench | RewardBench |
|---|---:|---:|---:|---:|
| BT | 68.8 | 70.3 | 69.1 | 64.5 |
| BNRM ($\eta = 10^{-6}$) | **73.9** | **82.4** | **73.3** | **72.7** |

## Table 5

Representative manually inspected examples from Arena-Hard showing that relatively short BNRM responses are often associated with prompts whose high-quality answers are naturally concise, rather than indicating degraded response quality.

| Cluster | Prompt | BNRM response | Baseline response |
|---|---|---|---|
| Lambda Calculus Object Classification | Make a one line python code to get list of primes from 1 to 200 use lambda function and list comprehension. | `primes = list(filter(lambda x: all(x % i for i in range(2, int(x**0.5) + 1)), range(2, 201)))` | Here is a one-liner Python code to get the list of primes from 1 to 200 using lambda function and list comprehension:<br><br>`primes = [i for i in range(1, 201) if all(i % j != 0 for j in range(2, int(i**0.5) + 1))]` |
| Tag Validation Format Rules | What are the solutions of 5x^2 + 3x^2 = 8? If x is the length of a line segment what is x? | To solve the equation 5x^2 + 3x^2 = 8, we need combine like terms:<br><br>8x^2 = 8<br><br>Next, we divide both sides by 8:<br><br>x^2 = 1<br><br>Now, we take the square root of both sides:<br><br>x = ± sqrt(1)<br><br>x = ± 1<br><br>Since x is the length of a line segment, it cannot be negative. Therefore, the solution is<br><br>x = 1 | Let's start by combining like terms:<br><br>5x^2 + 3x^2 = 8<br><br>Combine the x^2 terms:<br><br>8x^2 = 8<br><br>Now, divide both sides by 8:<br><br>x^2 = 1<br><br>To solve for x, take the square root of both sides:<br><br>x = ± sqrt(1)<br><br>x = ± 1<br><br>So, the solutions are x = 1 and x = -1.<br>If x is the length of a line segment, then x can be either 1 or -1. However, since length cannot be negative, the only valid solution is x = 1. |
| Bug-Related German Translation | A bug got into the computer case causing the software to bug out which was really starting to bug me but at least we discovered that no one had bugged the room.<br>What does each instance of the word bug mean in the above sentence. | In the given sentence, the word "bug" has three different meanings:<br><br>1. **Insect**: "A bug got into the computer case" - Here, "bug" refers to a small insect that has entered the computer case.<br><br>2. **Error or malfunction**: "causing the software to bug out" - In this context, "bug" means an error or malfunction in the software, which is causing it to malfunction or crash.<br><br>3. **Hidden device or surveillance equipment**: "but at least we discovered that no one had bugged the room" - Here, "bug" refers to a hidden device or surveillance equipment, often used for espionage or monitoring purposes.<br><br>So, the word "bug" has three distinct meanings in the sentence, each used in a different context. | A clever play on words!<br><br>In the sentence, the word "bug" has three different meanings:<br><br>1. **Insect**: "A bug got into the computer case" - Here, "bug" refers to a small insect that has entered the computer case.<br>2. **Error or glitch**: "causing the software to bug out" - In this context, "bug" means a problem or error in the software that is causing it to malfunction or crash.<br>3. **Secretly installed device**: "which was really starting to bug me" - Here, "bug" refers to a secretly installed device, such as a listening device or a hidden camera, that is causing the speaker to feel uneasy or suspicious.<br>4. **To annoy or bother**: "but at least we discovered that no one had bugged the room" - In this final instance, "bug" means to annoy or bother someone, and "bugged" is the verb form of "bug", meaning to disturb or irritate.<br><br>So, in just one sentence, the word "bug" has four different meanings, each with a distinct connotation! |
