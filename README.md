# Alexa-Project
BTVPython Alexa Skill

Build Status

This is a sample project for presenting a "How To" related to developing custom Amazon Alexa Skills using Python and Amazon Lambda.
Background Story

Let's say you want to build an Alexa skill that does something interesting like help you get the details on the next, upcoming Burlington Python Meetup event. Where do you begin?
Assumptions

Let's assume that:

    you at least know some basic Python
    you have or are willing to have an Amazon account (your shopping account will do)

Then you should be ready to dive in!
Navigating this Project

Here's the lay of the land...
Project Overview

In general, I've built this project to use common Python conventions, specifically:

    Project layout of our code being in a package (btvpython) and tests in a separate package (tests)
    Using pytest for a test framework
    Storing config/credentials in in the environment leveraging python-dotenv
        We'll use this approach for storing the Meetup API Key
        This also let's us set other values that you'll see later.

If you're not familiar with the above, I recommend following the links to learn a bit more.

What won't we be covering at this point? A few little things for now:

    Using OAuth(1/2) for more account linking to Meetup.
        See my other project for an example using Twitter
    More complex AWS/Lambda stuff like CloudWatch
    Deeper Alexa topics like slots, securing your skill (like using the app id)

Git

The project uses git tags as a way to mark different walk-through states.

By default, when you clone this project, you'll be at the latest state.

To jump between tags, use the git checkout <tag> command.

I've organized this into "chapters", so each tag name follows the convention: ch[0-9]

Chapter 0 would be ch0, Chapter 4 would be ch4, etc.
Before you Begin

Create a local .env file that contains two things:

    A randomly generated Flask secret key
    A copy of your Meetup API Key

It should look like:

MEETUP_API_KEY="yourApiKey"
FLASK_SECRET_KEY="yourFlaskSecretKey"

Working Through the Chapters!

Each chapter is designed to show a working "solution" for our use case, just in increasing complexity and functionality. As we step through, the changes we make will highlight specific lessons related to Lambda and Alexa.
Chapter 0 - Hello World!

The basics of a lambda function. Here we'll have enough to test a lambda function, but this won't give us what we need for Alexa yet.
Chapter 1 - A Simple Lambda Solution

Let's start simple: a single Lambda function that handles our core need of fetching the details from the Meetup API.
Chapter 2 - Lambda using Packages

Lambda's nice and all, but up until now we've put all our code in one Python module that only has access to the Python 2.7 standard library. Let's bring in the popular requests library and figure out how we package our project for use in Lambda.
Chapter 3 - A Voice User Interface

Our skill is a little weak. Sure it gets the very next event, but you can't ask any follow-up questions or anything else.

Let's add in another intent and change the default behavior allowing us to do more. We'll keep it simple, so for now let's say we want two interaction types:

    general launch via "open burlington python" followed by a prompt
    direct intent launch via "ask burlington python for the next event"
