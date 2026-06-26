# AI

+ [Terminology](#terminology)
+ [LLM](#llm)
    + [Tokens](#tokens)

## When was "Artificial Intelligence" first coined?
The term `"Artificial Intelligence"` was first coined in `1956` by American computer scientist `John McCarthy`. He created the phrase to serve as the official title for a summer workshop on `"thinking machines"` held at [Dartmouth College](https://home.dartmouth.edu/about/artificial-intelligence-ai-coined-dartmouth) the following year, which is now widely recognized as the birth of the field.

## Terminology

+ LLM
+ Generative AI
+ Token
+ Tokenization
+ Neural Network
+ MCP
+ Agents
+ Harness
+ Loop
+ Prompt
+ Transformer
+ Pre-training
+ Hallucination

## LLM
`LLM (Large Language Model)` is a type of `AI` designed to understand, process and generate human language. LLMs are the core technology behind the tools of: `ChatGPT`, `Claude`, `Google Gemini` and `Microsoft Copilot`. They are trained on massive datasets containing billions of words from books, websites, and articles. Using `deep learning` and `neural networks`, they learn to predict the next word in a sequence, allowing them to grasp context, grammar, and nuance.

At a high level, it works like this:

+ **Text is broken into tokens** - The model does not read whole words exactly like humans do. It splits text into small pieces called `tokens`. A `token` might be a word, part of a word, punctuation, or a space pattern.
+ **Tokens become numbers** - Each `token` is converted into a list of `numbers` called an `embedding`. These numbers represent patterns the model has learned about that `token`.
+ **The model looks at context** - Modern LLMs use a `neural-network` architecture called a `transformer`. Its key mechanism is attention, which lets the model decide which earlier tokens are most relevant when predicting the next one.
+ **It predicts the next token** - The core task is simple: given the previous text, predict what token is likely to come next. If the prompt is: **The capital of France is...**, the model assigns probabilities to possible next tokens, and `"Paris"` gets a high probability.
+ **It repeats that process** - After choosing one `token`, the model adds it to the context and predicts the next one, then the next, and so on. This is how a full answer is generated.
+ **Training teaches patterns** - During training, the model sees huge amounts of text and repeatedly guesses missing or next `tokens`. When it guesses wrong, its internal numbers are adjusted slightly. Over many examples, it learns grammar, facts, styles, reasoning patterns, code patterns, and associations.
+ **Instruction tuning makes it useful** - A base model only predicts text. To make it helpful in conversation, it is further trained on examples of questions and good answers. It may also be trained with human feedback so it learns to follow instructions, avoid harmful responses, and be more useful.

**A useful analogy:** an LLM is like an extremely advanced autocomplete system. But because it has learned patterns from so much text, "autocomplete" can look like explaining, translating, coding, summarizing, or reasoning.

The important caveat is that an LLM does not "know" things the way a person does. It generates likely text based on learned patterns. That is why it can sometimes sound confident while being wrong.

<img width="1536" height="1024" alt="Diagram of how an LLM works." src="https://github.com/user-attachments/assets/3eadf874-ea8a-4ae2-86db-12f55744a744" />
* This diagram was generated using ChatGPT. Notice the error that reads `tthe` in the text. This has been kept in to show that LLMs do make mistakes.

### Tokens
The LLM model splits text into small pieces called `tokens`. A `token` might be a word, part of a word, punctuation, or a space pattern.

<img width="1448" height="1086" alt="How tokens are used in LLMs" src="https://github.com/user-attachments/assets/9fde4c2d-92ae-49d5-b0d7-ef9a7a7cebca" />

`Tokens` can be:

+ Whole words: `cat`, `France`, `hello`
+ Parts of words: `un`, `believ`, `able`
+ Symbols: `.`, `?`, `+`, `=`, `$`
+ Spaces or space-plus-word chunks: `the`, `capital`
+ Numbers: `2026`, `42`, or sometimes pieces like `20` and `26`
+ Code pieces: `def`, `()`, `{`, `==`
