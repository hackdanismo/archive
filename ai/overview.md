# AI

+ [Terminology](#terminology)
+ [LLM](#llm)
    + [Tokens](#tokens)

## When was "Artificial Intelligence" first coined?
The term `"Artificial Intelligence"` was first coined in `1956` by American computer scientist `John McCarthy`. He created the phrase to serve as the official title for a summer workshop on `"thinking machines"` held at [Dartmouth College](https://home.dartmouth.edu/about/artificial-intelligence-ai-coined-dartmouth) the following year, which is now widely recognized as the birth of the field.

## Terminology

+ **LLM (Large Language Model)** - a type of AI trained on huge amounts of text so it can understand and generate language. 
+ **Generative AI** - an AI that can create new content instead of only classifying, searching, or analysing existing content. It can generate things like: Text: answers, emails, stories, summaries, Images: illustrations, product mockups, logos, Audio: music, voices, sound effects, Video: clips, animations, scene variations, Code: scripts, apps, debugging suggestions, Data: synthetic examples for testing or training. Generative AI learns patterns from large amounts of training data, then uses those patterns to produce something new that fits your request. A simple way to think about it: traditional AI might identify whether an image contains a cat; generative AI can create a new image of a cat.
+ **Model** - an AI model is a computer system trained to recognise patterns and make predictions or generate outputs. You give it some input, and it produces an output. An AI model is usually trained using lots of examples. During training, it adjusts internal numbers called parameters so it gets better at the task. An `LLM` is one kind of AI model. It is trained mainly on language, so it works with text. Other AI models can work with images, sound, video, medical scans, recommendations, or robotics. `GPT-5.5`, `Claude` and `Gemini` are examples of AI models.
+ **Token** - a token in AI is a small piece of text that a model reads or writes. The AI turns those `tokens` into numbers so it can process them. A `token` is basically the AI’s "unit of reading and writing.".
+ **Tokenization** - is the process of splitting text into smaller pieces called tokens so an AI model can process it.
+ **Neural Network** - a neural network is a type of AI system that learns patterns from examples. Each connection inside the network has a number called a weight. During training, the network adjusts these weights so it gets better at making the right prediction. A neural network is a pattern-learning machine made of layers of calculations. It takes input, transforms it step by step, and produces an output. An LLM uses a neural network and is trained on language. Inside the transformer, the model uses attention to decide which tokens in the prompt are most relevant to each other. 
+ **MCP (Model Context Protocol)** - It is a standard way for an AI app or agent to connect to outside tools and data sources. The official MCP docs describe it as an open standard for connecting AI applications to external systems. So instead of every AI app needing a custom integration for every tool, MCP gives them a common connection format. Anthropic introduced MCP in late 2024 as an open protocol for secure two-way connections between AI tools and data sources. It is like an API, allowing LLMs to access external tools and systems outside of the LLM.
+ **Agent** - in AI, an agent is an AI system that can take actions toward a goal, often by using tools or interacting with an environment. The LLM generates text, an agent uses an LLM plus tools, memory/context, and decision-making steps to do a task. So an agent is not just "the model". It is usually a system built around a model that can reason, choose actions, use tools, and work through multiple steps.
+ **Harness** - in AI, a harness usually means a wrapper or testing setup that connects an AI model to inputs, tools, data, and evaluation checks. For example, an evaluation harness might test an LLM with 1,000 questions. So in AI, harness often means the system around the model that helps you run, test, measure, or control it. It is not usually the AI model itself. It is more like the testing rig or control layer around the model. `Claude Code` can be thought of as a kind of AI harness, but more specifically it is an AI coding agent/tool. It is not just the model itself. Claude is the model family; Claude Code is the surrounding system that lets Claude work with a codebase.
+ **Loop** - in LLMs, a loop usually means the model or agent is run repeatedly, instead of being given one prompt and returning one answer. So a loop is not really "instead of" a prompt. It is usually a prompt plus repeated steps. In AI agents, this is often called an agent loop. Prompt = ask once. Loop = ask, check, feed back, repeat.
+ **Prompt** - a prompt is the instruction or input you give to an AI model. It tells the LLM what you want it to do.
+ **Transformer** - a transformer is the main type of `neural network` used inside most modern LLMs. It helps the model understand how `tokens` in a prompt relate to each other, then predict what token should come next.
+ **Pre-training** - is the first big training stage for many AI models, especially LLMs. It is where the model learns general patterns from a huge amount of data before it is taught to follow instructions. The model guesses the missing or next `token`. If it guesses wrong, training adjusts the model slightly so it becomes more likely to guess correctly next time. After pre-training, the model is usually not yet a polished assistant. It is more like a powerful text predictor. Later stages, such as instruction tuning and human feedback, make it better at answering questions, following requests, and behaving helpfully.
+ **Hallucination** - an hallucination is when an AI gives an answer that sounds confident but is wrong, made up, or not supported by the source material.
+ **RSI (Recursive Self-Improvement)** - it is the idea that an AI system could improve itself, then use that improved version to make even better improvements, repeating the cycle. The concern is that if each version becomes better at improving the next one, progress could speed up very quickly. This is sometimes called an `intelligence explosion`. RSI is mostly a theoretical concept. Current AI systems can help humans write code, analyse models, or suggest improvements, but they do not fully and independently redesign themselves into increasingly more powerful systems.
+ **AGI (Artificial General Intelligence)** - it means an AI system that could understand, learn, and perform a wide range of tasks at a level similar to, or beyond, a human. Today's AI systems are usually narrow AI meaning they are good at specific tasks. An AGI system learns many different tasks, adapt to new situations, reason across domains, plan, solve problems. AGI is not just "a smarter chatbot". The idea is an AI that can transfer learning across areas, handle unfamiliar problems, and act flexibly in many environments. There is no universal agreement on exactly when an AI counts as AGI, and people disagree on how close current systems are.
+ **Machine Learning** - is a type of AI where a computer learns patterns from examples instead of being programmed with every rule by hand.
+ **Vibe coding** - is a way of building software where you describe what you want in natural language, and an AI coding tool writes much of the code for you.

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
* This diagram was generated using ChatGPT. Notice the error that reads "tthe" in the text. This has been kept in to show that LLMs do make mistakes.

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
