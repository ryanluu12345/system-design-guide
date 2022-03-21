# System Design Guide
The purpose of this guide is to give a condensed guide and links to references for system design practice.

## Pre-requisite steps
- Read system design primer by Donne Martin: https://github.com/donnemartin/system-design-primer
- Watch exponent videos to see real mock interviews: https://www.youtube.com/c/ExponentTV

## Recommended study sequence
- Gain context on the main components in system design (read the system design primer)
- Practice questions about building systems (i.e. design postmates)
- Get feedback from more senior engineers
- Watch videos of actual interviews and see how they approach

## Recommended thought process
1. Define requirements
- Functional: how it supposed to work? what does it need to do?
- Non-Functional: what are latency, availalability, or consistency requirements? How much scale are we looking at?

2. Ask clarifying questions (examples below)
- Who are the customers?
- What's the scale?
- Do we need to support more complex requirements like multi-tenancy?

3. Overarching design
- Draw box diagrams for each of the major components
- Connect boxes with lines and write how they interact with each other (i.e. REST, gRPC, GraphQL?)
- Do back of the envelope calculations to figure out the optimizations needed in the design (i.e. load balancing or sharding or federation)

4. Specific component decomposition
- What do each of the specific services or components do?
- How do they interact?
- What are the tradeoffs with the components or interactions?
- What are specifics that need to be addressed here?

5. Further optimizations/scale
- What are ways you can make things more efficient?
- What are ways we can simplify?
- What are performance optimizations? And how can we measure
- How do we handle more scale?

6. Testing/Monitoring (somewhat bonus points)
- How do we ensure limited regressions?
- How do we tell how good the system is?
- How do we respond when things are bad?

7. Product considerations (bonus points)
- How do we make the UX amazing for this service?