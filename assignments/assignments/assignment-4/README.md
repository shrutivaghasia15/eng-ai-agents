# Assignment 4 – Context and Thinking Tokens in a Small LLM

This assignment uses Qwen3-0.6B as a customer support router that classifies messages into one of 27 intents.

## Part 1: Context Tokens

I tested how few-shot examples affect routing accuracy, prompt length, inference time, and GPU memory.

The best few-shot setting used 16 examples per intent and achieved:

- Accuracy: 0.944
- Prompt tokens: 11,977
- Time per message: 6,109.2 ms
- Peak GPU memory: 7.61 GB

I also fine-tuned the model using LoRA on 864 examples. The fine-tuned router achieved:

- Accuracy: 0.985
- Prompt tokens: 148
- Time per message: 29.6 ms

I also tested the effect of placing the target message at the start, middle, and end of inboxes containing 25, 100, and 400 messages.

## Part 2: Thinking Tokens

I compared routing with Qwen3 thinking enabled and disabled.

For the base model, thinking improved accuracy from 0.378 to 0.511, but increased generated tokens and inference time significantly.

For the fine-tuned router, thinking reduced accuracy from 0.978 to 0.933 and increased the amount of generated tokens and inference time.

## Main Result

For this classification task, LoRA fine-tuning with thinking disabled gave the best overall balance of accuracy, prompt size, and inference time.
