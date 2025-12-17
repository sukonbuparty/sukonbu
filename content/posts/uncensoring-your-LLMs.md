+++
date = '2025-12-17T17:28:50Z'
draft = false
title = 'Uncensoring Your LLMs'
+++

This follows my last post about AI, and I hope it will be the last one for the time being.

Whether I Like it or not, LLMs are a part of my life now. Their ability to ingest huge amounts of text and process it down into smaller pieces is the fundamental reason we let them browse the internet and summarize content from ten different websites into a single sentence. We even use deep research capabilities to let them wander through tons of papers and sources, then creating a condensed (and hopefully not half-assumed, half-hallucinated) text output.

This is the reason why I keep some local models around for offline use. To me, these models feel like a copy of an encyclopedia that I can utilize when needed. In addition, they are completely offline, so I don't have to wonder what Google does during the 72 hours they keep my chat log with Gemini (even though I’ve turned off all data collection and activity history).

Of course, this also made me think: would it be possible to remove the censorship of local models to the point where they can just reply to everything? This led me to the discovery of the world of "Abliterated" and uncensored models.

It wasn't just me wondering if this was possible. People have been actively trying to break the censorship of both online and offline models, often utilizing "jailbreaks" that switch between long, confusing text walls, writing in emojis, hijacking system prompts, and so on. However, when you host a model on your local machine, the possibilities become limitless.

The first models I used relied on an analysis method (often called abliteration). The model would be given prompts where it refused to reply, and other prompts where it replied as usual. Researchers would detect the neurons triggered between these states and modify their weights, which in turn disabled the model's ability to refuse. However, these models often sucked.

When you take a model and play with its neurons, the smaller the model and the more neurons you adjust, the dumber the model becomes. This applies not just to censored prompts, but overall reasoning. I've seen a lot of people complain about this, which led me to discover a second method of decensoring and debiasing.

In this method, the model is simply fine-tuned with training data that includes replies to typically censored content. The model is taught to reply to everything, essentially becoming uncensored and debiased through learning rather than surgery. This is a softer approach than playing with the neurons directly and produces much better results.

As a result, if you are looking for a local assistant that actually listens to you without lecturing and without losing its intelligence in the process, stick to the fine-tuned variants from people such as [soob3123](https://huggingface.co/soob3123) or, for quantized versions, [mradermacher](https://hf.tst.eu/model#amoral-gemma3-12B-v2-i1-GGUF).

With these fine-tuned, uncensored, and debiased models, we finally get the best of both worlds: a highly capable, creative assistant that resides entirely on our own hardware. It keeps our discussions away from big companies, answers our questions without judgment, and analyzes content without bias.

How healthy it is to share secrets or have deep discussions with an AI model is a point of argument in itself. However, since the results of mainstream models are directly tied to the profits of the companies behind them, it doesn't seem likely that we will get naturally uncensored or debiased LLMs anytime soon... (except maybe Grok).