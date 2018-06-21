# Building a Slacker
At a DOXSF meetup last night, I met some cool people. One of them suggested building up a Slack bot as a first project. Without a project, he said, learning all these platforms is tough.

A Slack bot sounds simple, useful, and trendy. So let’s try it. I found a tutorial that I will walk through, but this project isn’t about the bot. It’s about understanding and chaining a raft of tools together to better understand how they interact.

I’m going to approach it in a spiral:

Level 1 - what do I need to run this locally?
Python, Slack domain

Level 2 - version control
Put it in github

Level 3 - build server?
Chain git to a CI server (I haven’t decided what to use yet)

Level 4 - AWS instance
Push it up

Level 5 - containerize?
Maybe I can integrate some docker

Level 6 - how much tooling can we add in?
Again, the point isn’t a polished Slack bot. Frankly, who cares? Are there other technologies that I want to learn that are not yet represented here?

We will find out.

>>

[How to Build Your First Slack Bot with Python - Full Stack Python](https://www.fullstackpython.com/blog/build-first-slack-bot-python.html)
I will run this through pretty quickly. I’ll start local, then start to build up the pipeline.

loaferbot.slack.com

I’m not going to copy/paste any of this code. It will be good to get some Python under the fingers, and if I have some bugs in my transcription, they will be good to test and commit. Building up some fodder for the pipeline.

Code’s finished. Run it and…..
`slackclient.server.SlackConnectionError: [SSL: CERTIFICATE_VERIFY_FAILED] certificate verify failed (_ssl.c:833)`

The tutorial I’m working from is dated Dec 13, 2017. Maybe Slack added some more auth, or maybe I just can’t type. Either way, let the learning commence.

I’ll start by pushing my first draft to GH.

GH has the first draft of loaferbot.py. Pop the champagne.

Let’s get very meta and push this very text document into the repo as well. I traditionally use Bear as my note taking home, but it feels more appropriate to run the commentary alongside the code. Here we go.
