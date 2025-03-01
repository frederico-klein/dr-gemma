# Dr. Gemma


So I wanted to test how well I could get Gemma-2 to do some anamnesis for me, and it turns out it's pretty good. 

This is a super early version. I think the first thing I need to do is link it to some database of sorts and add a proper command line interface to it, so it can check the patient's info.

I need to update the command list to add a bit more granular information, like list of medications the person is taking. 

Also I should add some temporality to the thing, like, I want to track changes over time, so I need to think about this a bit.

I mean, I don't trust the model too much, if you look at the way it progressed over the conversation, it was trying to add many commands at once and it overwritten the old list of problems. This is not a big issue, the list of problems should have like a chronic part and a more acute part, so I think the model is doing things correctly, but I need to change the mock interface to addapt to that. 

Maybe having another model serving as a supervisor of sorts and checking things also makes sense. We can give it separate instructions and make it supervise the actions of Dr. Gemma. I think calling it a separate thing sort of hurts its feelings, so I will call it Dr. Gemma's Uberich. 

I want her Uberich to be sort of anxious. So always try to think of the worst possible things that can happen and try to come up with many different scenarios.
