# Building a Slacker
At a [DOXSFO](https://www.meetup.com/DevOps-Exchange-SanFrancisco) meetup last night, I met some cool people. One of them suggested building up a Slack bot as a first project. Without a project, he said, learning all these platforms is tough.

A Slack bot sounds simple, useful, and trendy. So let’s try it. I found a tutorial that I will walk through, but this project isn’t about the bot. It’s about understanding and chaining a raft of tools together to better understand how they interact.

I’m going to approach it in a spiral:

Level 1 - what do I need to run this locally?
Python, Slack domain

Level 2 - version control: Put it in github

Level 3 - build server? Chain git to a CI server (I haven’t decided what to use yet)

Level 4 - AWS instance

Level 5 - containerize?
Maybe I can integrate some docker

Level 6 - how much tooling can we add in?

Again, the point isn’t a polished Slack bot. Frankly, who cares? Are there other technologies that I want to learn that are not yet represented here?

We will find out.

# Get Moving

[How to Build Your First Slack Bot with Python - Full Stack Python](https://www.fullstackpython.com/blog/build-first-slack-bot-python.html)

I will run this through pretty quickly. I’ll start local, then start to build up the pipeline.

[The Slack Domain](loaferbot.slack.com)

I’m not going to copy/paste any of this code. It will be good to get some Python under the fingers, and if I have some bugs in my transcription, they will be good to test and commit. Building up some fodder for the pipeline.

Code’s finished. Run it and…..
```
slackclient.server.SlackConnectionError: [SSL: CERTIFICATE_VERIFY_FAILED] certificate verify failed (_ssl.c:833)
```

The tutorial I’m working from is dated Dec 13, 2017. Maybe Slack added some more auth, or maybe I just can’t type. Either way, let the learning commence.

I’ll start by pushing my first draft to GH.

GH has the first draft of loaferbot.py. Pop the champagne.

Let’s get very meta and push this very text document into the repo as well. I traditionally use Bear as my note taking home, but it feels more appropriate to run the commentary alongside the code. Here we go.

# Level 1.5
First pass at the code is done, now it's time to troubleshoot the SSL cert error to get the thing to actually run.

[some time passes]

I just got loaferbot working after 15 minutes on duckduckgo (don't @ me). Turns out when you install Python3 from brew and not python.org, the SSL stack doesn't get upgraded. Who knew. Fortunately, [some kind soul](https://stackoverflow.com/questions/44649449/brew-installation-of-python-3-6-1-ssl-certificate-verify-failed-certificate#44649450) put up the solution. I ran that script, and the bot is now awake.

Holy crap it works. 
I mean, it does nothing:

```
jeremy [11:20 AM]
@loaferbot loaf around or something

loaferbot APP [11:20 AM]
Sure... write some more code, then I can do that!
```

But it does something!

Note: to run this app, it's not enough to simply run `python3 loaferbot.py`. It needs a few startup commands. I should script that. 
I'm going to script that.

[some more time passes]

You would think that these three lines would be easy to script:

```
virtualenv loaferbot
source loaferbot/bin/activate
export SLACK_BOT_TOKEN='[redacted]'
```

and yet it doesn't go. Ah well. Let's not become distracted.

# Level 3
Time to actually dev some ops (op some dev?). Now that we have a humble app locally, I need a few tools. As I understand it, the traditional pipeline looks like this:

[src] > [scm] > [ci] > [container] > [cloud]

CI is next. Ansible? Jenkins? 
