# Dr. Gemma


So I wanted to test how well I could get Gemma-2 to do some anamnesis for me, and it turns out it's pretty good. 

This is a super early version. I think the first thing I need to do is link it to some database of sorts and add a proper command line interface to it, so it can check the patient's info.

I need to update the command list to add a bit more granular information, like list of medications the person is taking. 

Also I should add some temporality to the thing, like, I want to track changes over time, so I need to think about this a bit.

I mean, I don't trust the model too much, if you look at the way it progressed over the conversation, it was trying to add many commands at once and it overwritten the old list of problems. This is not a big issue, the list of problems should have like a chronic part and a more acute part, so I think the model is doing things correctly, but I need to change the mock interface to addapt to that. 

Maybe having another model serving as a supervisor of sorts and checking things also makes sense. We can give it separate instructions and make it supervise the actions of Dr. Gemma. I think calling it a separate thing sort of hurts its feelings, so I will call it Dr. Gemma's Uberich. 

I want her Uberich to be sort of anxious. So always try to think of the worst possible things that can happen and try to come up with many different scenarios.

## Requirements:

You need local gemma to run this.

## ICD11:

I've been using this to create my fake patient https://icd.who.int/browse/2025-01/mms/en

This is based on my experience, I was trying to create a simple an typical story of a smoker with COPD that has terminal cancer and is constipated because of morphine. It could be that he has a metastasis that is causing the blockage and we may want to do like an MRI of the guy. It has been a long time since my days as an intern and I was never any good. I may be completely off here. I should use real stories of patients to test this better. Right now I am just trying to come up with the interace that Dr. Gemma will use and the overall architecture. 

## Rationale:

Why do I think this is an okay idea? 

Humans make mistakes. LLMs make mistakes. The kinds of mistakes are different. Hence LLMs + Humans are more powerfull than each of them isolated. 

Or so I think. 

Also, LLMs are usually better than patients at medicine stuff, probably. I don't know. 

So I guess, the idea here is to try to make something like this work on a scale large enough so that we can test what kind of problems it faces and then we fix them as we go. 

I think we can totally use LLMs as primary care physicians of sorts (maybe I should call this zero-th care, before primary care), just as long as we understand the kinds of mistakes they make. If we can protect ourselves from those and avoid the important ones, then this is useful. Of course if the errors are massive and super unpredictable, then it won't work. But I don't think so. Also, it doesn't matter what I think, I know that we need to test them instead. 

## Basic Layout I envision for this:

I don't know too much about LLMs, so maybe my layout idea is crude. 

But I think having a local model that has all your info already could be useful. You can ask stuff every day and then use this like a medical jarvis of sorts. 

We can add like a whisper and a web interface to make this nicer looking. 

I am running on a linux pc with ubuntu and a 3060 with 12gb, i think it is a cheap enough computer that people can buy and it runs gemma2-9b-it with quantization just fine. 

## Future improvements:

I like humans + machines working together. So what I would want to do is have like each medical professional train their own clone model that would react like they would. Then we LoRa Gemmas to copy the doctors. 

Finally we create like a crowd of these guys. I think there was a paper that showed that you can train large models in parts of the data and put them together and the combined thing is smarter. So this is what I think we can do here. 

Finally, to make this cherry on top cool, we can add the TikTok thing, where you group users together by their kind of response. Like, I think it would be interesting to have all sorts of skill doctors working toghether in the same platform, only choose cleverly who to listen to. This makes the system sort of robust to bots (imagine if you make a bot like a ton of sponsored propaganda videos in tiktok, this would only affect the people that like propaganda style videos, if you don't like them, the algorithm automatically identifies that this is not your thing, that you don't belong to that group and won't suggest you that). I mean, this is how I think their algorithm works. In simple terms, when we are evaluating the next possible token, we also calculate similarity between LLMs, if it is too different, we assign it a lower weight. More similar, higher weight. Maybe this will work, I don't know. If you think of something better, please implement it! I think the idea of grouping similars makes sense. 

Why does this idea make sense? Because we can monetize this. But it is good monetization, I think. This would allow you to tweak this setting and add stronger weights to the LLMs trained by experts and the experts would receive money for that. This has the additional benefit of stimulating medical experts into fine tuning their own models a bunch and would serve as a virtuous cycle. I think. 

We can add a cool interface where your problems are examined by both humans and LLMs, so your response would be totally trustworthy (right?) and we can optimize doctors. I mean, physical examination and doctor patient interaction are important, but at some point maybe we can integrate this into the practice, where your doctor sees you and at the same time a ton of other doctors see you, or at least they can read your story. 

