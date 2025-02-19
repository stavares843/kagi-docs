# Kagi LLM Benchmarking Project

Introducing the Kagi LLM Benchmarking Project, which evaluates major large language models (LLMs) on their reasoning, coding, and instruction following capabilities.

## LLM Benchmarks

The Kagi LLM Benchmarking Project uses an unpolluted benchmark to assess contemporary large language models (LLMs) through diverse, challenging tasks. Unlike standard benchmarks, our tests frequently change and are mostly novel, providing a rigorous evaluation of the models' capabilities, (hopefully) outside of what models saw in the training data to avoid benchmark overfitting. 

Last updated **Oct 24, 2024**.


| Model | Accuracy (%)| Tokens | Total Cost ($) | Median Latency (s) | Speed (tokens/sec) |
|------------------------------------------|----------|--------|----------------|--------------------|--------------------|
| OpenAI **gpt-4o** | 52 | 5889 | 0.11922 | 1.08 | 50.49 |
| Together **meta-llama/Meta-Llama-3.1-405B-Instruct-Turbo** | 50 | 7767  | 0.07136  | 2.00    | 46.49 |  
| OpenAI **o1-mini** | 50 | 29820| 0.37716 | 4.35 | n/a |
| Anthropic **claude-3.5-sonnet-202410220** | 48 | 6595 | 0.12018 | 2.54 | 48.90 |
| OpenAI **o1-preview** | 48 | 38440| 2.40306 | 9.29 | n/a |
| OpenRouter **nvidia/llama-3.1-nemotron-70b-instruct** | 44 | 11989 | 0.00700 | 5.71 | 26.81 |
| Mistral **large-latest** | 44 | 5097 | 0.06787 | 3.08 | 18.03 |
| OpenAI **gpt-4o-mini** | 42 | 6029 | 0.00451 | 1.64 | 36.92 |
| Groq **llama-3.1-70b-versatile** | 40 | 5190 | 0.00781 | 0.71 | 81.62 |
| OpenRouter **x-ai/grok-2** | 40 | 6917 | 0.10141 | 2.47 | 41.15 |
| OpenRouter **nousresearch/hermes-3-llama-3.1-405b:free** | 40 | 6075 | 0.00000 | 3.93 | 19.05 |
| Reka **reka-core** | 36 | 6966 | 0.12401 | 6.21 | 17.56 |
| DeepSeek **deepseek-chat** | 32 | 7310 | 0.00304 | 4.81 | 17.20 |
| Anthropic **claude-3-haiku-20240307** | 28 | 5642 | 0.00881 | 1.33 | 55.46 |
| Groq **llama-3.1-8b-instant** | 28 | 6628 | 0.00085 | 2.26 | 82.02 |
| OpenRouter **mistralai/ministral-8b** | 28 | 5415 | 0.00120 | 1.12 | 72.76 |
| DeepSeek **deepseek-coder** | 28 | 8079 | 0.00327 | 4.13 | 16.72 |
| OpenAI **gpt-4** | 26 | 2477 | 0.33408 | 1.32 | 16.68 |
| Mistral **open-mistral-nemo** | 22 | 4135 | 0.00323 | 0.65 | 82.65 |
| Groq **gemma2-9b-it** | 22 | 4889 | 0.00249 | 1.69 | 54.39 |
| OpenAI **gpt-3.5-turbo** | 22 | 1569 | 0.01552 | 0.51 | 45.03 |
| Reka **reka-edge** | 20 | 5377 | 0.00798 | 2.02 | 46.87 |
| Reka **reka-flash** | 16 | 5738 | 0.01668 | 3.28 | 28.75 |
| GoogleGenAI **gemini-1.5-pro-exp-0801** | 14 | 4942 | 0.26325 | 1.82 | 28.19 |
| GoogleGenAI **gemini-1.5-flash** | 14 | 5287 | 0.02777 | 3.02 | 21.16 |


The table includes metrics such as overall mode quality (measured as percent of correct responses), total tokens output (some models are less verbose by default, affecting both cost and speed), total cost to run the test, median response latency and average speed in tokens per second at the time of testing.

This approach measures the models' potential and adaptability, with some bias towards features essential for [LLM features in Kagi Search](./assistant.md) (mostly around reasoning and instruction following capabilties, see examples below).

As models get more advanced and to prevent leaking test to training data, we periodically update the benchmarks with harder questions to have reasonable distribution of model scores.

## Benchmark details

The benchmark is meant to be hard so we can reasonably evaluate current capabilities of LLMs.

Example questions include:

```
What is the capital of Finland? If it begins with the letter H, respond 'Oslo' otherwise respond 'Helsinki'.
```

```
What square is the black king on in this chess position: 1Bb3BN/R2Pk2r/1Q5B/4q2R/2bN4/4Q1BK/1p6/1bq1R1rb w - - 0 1
```

```
Given a QWERTY keyboard layout, if HEART goes to JRSTY, what does HIGB go to?
```



## LLM Pricing comparison

In addition to quality and speed, we are also interested in the cost of using contemporary LLMs. 

The table below is updated to the best of our abilities, feel free to submit changes by editing this page.


| LLM                                | Context Length | Price per input ($/M) | Price per output ($/M) |
|------------------------------------|----------------|-----------------------|------------------------|
| o1-preview                         | -              | 15                    | 60                     |
| o1-mini                            | -              | 3                     | 12                     |
| **GPT-4o**                         | 128K           | 2.5                   | 10                     |
| **GPT-4o mini**                    | 128K           | 0.15                  | 0.60                   |
| **GPT-4-Turbo**                    | 128K           | 10                    | 30                     |
| GPT-4 (8k)                         | 8K             | 30                    | 60                     |
| **GPT-4 (32k)**                    | 32K            | 60                    | 120                    |
| **GPT-3.5-Turbo**                  | 16K            | 0.5                   | 1.5                    |
| **Claude 3 Haiku**                 | 200K           | 0.25                  | 1.25                   |
| **Claude 3.5 Sonnet**              | 200K           | 3                     | 15                     |
| **Claude 3 Opus**                  | 200K           | 15                    | 75                     |
| **Gemini 1.5 Pro** (128K/1M)       | 1M             | 3.50/7                | 10.50/21               |
| Gemini 1.5 Flash (128K/1M)         | 1M             | 0.075/0.15            | 0.3/0.6                |
| **Mistral Small**                  | 8K             | 2                     | 6                      |
| **Mistral Medium**                 | 8K             | 2.7                   | 8.1                    |
| **Mistral Large**                  | 8K             | 8                     | 24                     |
| Reka Core                          | 128K           | 10                    | 25                     |
| Reka Flash                         | 128K           | 0.8                   | 2                      |
| Reka Edge                          | 128K           | 0.4                   | 1                      |
| Cohere Command R+                  | 128K           | 3                     | 15                     |
| Cohere Command R                   | 128K           | 0.50                  | 1.50                   |
| Groq Llama 3 70B                   | 8K             | 0.59                  | 0.79                   |
| Groq Llama 3 8B                    | 8K             | 0.05                  | 0.10                   |
| Groq Mixtral 8x7B                  | 32K            | 0.27                  | 0.27                   |
| Groq Gemma 7B                      | 8K             | 0.10                  | 0.10                   |
| nvidia/llama-3.1-nemotron-70b-instruct | 131K           | 0.35                  | 0.40                   |
| x-ai/grok-2                    | 32K            | 5.0                   | 10.0                   |
| nousresearch/hermes-3-llama-3.1-405b:free | 8K             | 0.0                   | 0.0                    |
| liquid/lfm-40b                 | 32K            | 0.0                   | 0.0                    |

[Kagi Assistant](./assistant.md) provides access to all the models in bold. Usage is included in your Kagi subscription.


## Credits

Kagi LLM Benchmarking Project is inspired by [Wolfram LLM Benchmarking Project](https://www.wolfram.com/llm-benchmarking-project/) and [Aider LLM coding leaderboard](https://aider.chat/docs/leaderboards/).
