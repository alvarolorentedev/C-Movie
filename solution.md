# Solution

The C-Movie Platform is going to compite in a crowded bussiness space. For this is important before doing a big upfront investment validate if there is a bussiness value on the project. For this the solution should be solved in diferent phases.
- Discovery: Understand the problem.
- MVP: Answer unkowns to validate the validity of the project, and if so start building SEO Ranking.
- MLP: Start validating our algorithm is a value adder.
- Phase 1: Initialize the data platform & products.
- Phase 2: Standardize the architecture.

Please fint all the assumptions in the assumptions file.

## Discovery

If we run a domain discovery using event storming we can se the next situation:
![image](https://github.com/kanekotic/C-Movie/assets/3071208/bd63e0c8-269e-46ee-aa18-d59308e64ff1)
This means we have at least 2 flow streams of work:
- Conversion: related to atracting our users and make them use our page in a recurrent way.
- Movies: will provide the search and rating capability (as we can start smelling here there might be 2 diferent subdomains).

We need to also gather some data on our competitors that will help us take some decisions in the MVP phase. In this case using for example google trends our main competitor by traffic is going to be IMDB. So we are going to go with the suposition that their data has a better quality that is driving the higher traffic.

![image](https://github.com/kanekotic/C-Movie/assets/3071208/b969786f-b54c-47f3-8e36-cfd630bf5157)

## MVP

To validate we have a bussiness case we are going to create an initial MVP. Whe aim to to solve the next questions:
- Are users interested on a new movie platform?
- Do we have the expected granularity data from our main competitor?

This Will also allow our site to start building an SEO ranking that will be required for the proyect to be a success.

For this we are going to create a simple service using a serverless function (Lambda)


![image](https://github.com/kanekotic/C-Movie/assets/3071208/53c6e801-da68-4e7d-90ba-60a2e430bc75)

### Success criteria 
 - We have >=80% of the required data from a single provider.
 - We have 10k Monthly unique visitors, with at least 8% of conversion rate  tracked by the CTA.
