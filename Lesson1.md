# Lesson 1 : overall review of concepts

## Concepts
Review Donne Martin guide at a high level.

- Networking
  - TCP vs. UDP
  - gRPC vs. REST

Commentary courtesy of Jeremy Yang:
```
For some follow up. I can answer some questions around yesterdays example in regards to latency and availability. 

The biggest concern for latency would be how long it took from the time a user pressed submit to the time an result was shown back in the UI. There are many factors here as we saw yesterday, but the biggest factor that could be at play are the job queues we talked about yesterday being backed up. Now, why would the job queues be backed up. This could mean one of the build servers is slow, backed up, low on cpu etc. If we assume that we time out code execution at 10 seconds, the rest of the request should not take all to long unless its stuck waiting in the queue. So lets say we have a P99 of 15s for when the time a user presses run code in the UI to the time a result should be displayed back to the user. 

Now in order to continually meet a P99 of 15s, you need to ensure all your build nodes we mentioned yesterday are healthy, so this would involve the metrics and observability we sort of touched on. 

Now given this information, if we wanted to maintain 99% uptime (and we define uptime based on the P99 we set above) we need to return within 15s 99% of the time for a given duration. Lets say a month which is a typical SLO. 

Lets assume we know that a single build node on our instances can handle a max of 100 concurrent jobs at a time. We defined our peak of potentially 1500 rps which means that we may need 15 nodes to be able to handle bursts.

So what happens if we start falling behind? Then maybe we need to spin up another instance since we know that each instance can handle a max of 10 jobs at a time and after that our performance may take a hit. 

Something like this for latency and availability is probably okay. 
For something like bytes per message, you would probably estimate the max throughput your queue or service can keep up with and multiply that by the rate to maybe find the rate per second. 

But its all very rough.
```

## Practice Problem
Design Leetcode: https://docs.google.com/drawings/d/15p1bMFJRERNNfX3eY7WLoubMwEIrrD1xJ0rVW0HPbYA/edit?usp=sharing