---
title: "Side Project - Payment orchestrator"
description: "Part 1"
pubDate: "Jan 03 2026"
heroImage: "../../public/paorc.png"
---
# Building a Payment Orchestrator: My Learning Journey

I'm starting a new side project, and I'm pretty excited about it. I'll be building a payment orchestrator from scratch, and I want to document the whole journey here. I want to really understand how payments work and get my hands dirty with the backend systems that deal with payments.

So this is going to be a series. I'll share my progress, my mistakes, and probably some frustrations along the way.

## What Even is a Payment Orchestrator?

Good question. Here's how I think about it: imagine you're running an online store and you want to accept payments through Checkout.com, Amazon Payment Service, and maybe some regional payment providers. Normally, you'd have to integrate with each one separately. That's a lot of code, a lot of maintenance, and a lot of headaches.

A payment orchestrator sits in the middle. Your app talks to the orchestrator, and the orchestrator figures out which payment provider to use for each transaction. It's like having a smart router that decides, "Okay, this payment should go to Checkout.com, but if that fails, let's try Amazon Payment Service."

## Why Am I Doing This?

Because payment systems touch on so many interesting technical challenges:

- You're dealing with distributed systems where things can and will go wrong
- You need to handle events asynchronously (payments don't happen instantly)
- The domain itself is complex—there's authorization, capture, refunds, settlements
- it's money. You absolutely cannot lose transactions or charge someone twice

It's the perfect playground to learn about system design, event streaming, reliability patterns, and a whole lot more. Plus, the payment domain is just fascinating once you start digging into it.

## How I'm Planning to Tackle This

I'm not going to try to build everything at once. That's a recipe for giving up after two weeks. Instead, I'm breaking it down into phases:

**Phase 1: Get Something Working**
Just basic payment routing with one processor. Keep it simple, make sure I understand the fundamentals.

**Phase 2: Make It Event-Driven**
Introduce proper message streaming, handle asynchronous updates, start thinking about event sourcing.

**Phase 3: Add More Payment Processors**
This is where it gets interesting—routing between multiple providers, handling fallbacks when one fails.

**Phase 4: Make It Bulletproof**
Add retries, circuit breakers, proper monitoring. Make sure nothing breaks when things go wrong (and they will).

## What Will This Thing Look Like?

![Simple architecture diagram with boxes and arrows showing request flow](/draftdesign.png)

I'm picturing a few main pieces:

- An **API** where applications send payment requests
- The **orchestrator** that decides where each payment should go
- **Adapters** for different payment processors (so I don't have to rewrite everything when adding a new one)
- A **message broker** for handling all the asynchronous stuff
- A **database** to keep track of everything
- A **webhook handler** because payment processors love to send updates whenever they feel like it

Nothing groundbreaking, but that's not the point. The point is understanding how all these pieces fit together.

## What I'm Hoping to Learn

This project is going to force me to figure out a lot of things:

- How do payments actually work and processed?
- How do you make sure you never charge someone twice, even if they click "Pay" a hundred times?
- What happens when a payment processor goes down mid-transaction?
- How do you handle webhooks reliably?
- How do banks reconcile all these transactions at the end of the day?

There's a lot I don't know yet, and that's exciting.

## What's Coming Next?

In my next post, I'll get into the actual system design. I'll sketch out the components in more detail, think through the data flow, and start making some architectural decisions. I'll probably also set up the basic project structure and get a "Hello World" payment flowing through the system.

I have no idea if this project will turn out exactly as planned. I'll probably hit roadblocks, change my mind about things, and learn that some of my assumptions were completely wrong. But that's kind of the whole point.

Let's see where this goes.

---

*This is Part 1 of my Payment Orchestrator series. Next up: Part 2 - Designing the System*