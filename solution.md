# Solution

The C-Movie Platform is going to compite in a crowded bussiness space. For this is important before doing a big upfront investment validate if there is a bussiness value on the project. For this the solution should be solved in diferent phases.
- MVP: Simple passthrough to one of de platforms we are going to work with. This will allow to get traffic data and start building SEO Ranking.
- MLP: Implementation of the algorithm with a few real time APÎ sources. Keep the code modular and independant to be able to extract later into the data platform. Helps validate the value of our propietary algorithm.
- Release 1: Initialize a data platform, by consuming csv data. Consume this data from the systems.
- Release 2: migrate real time API and calculation algorithm to comply with the data platform structure.

Please fint all the assumptions in the assumptions file.

## MVP

To validate we have a bussiness case we are going to create an initial MVP. Whe aim to to solve the next questions:
- Are users interested on a new movie platform?
- Do we have the expected granularity data from our main competitor?

This Will also allow our site to start building an SEO ranking that will be required for the proyect to be a success.

For this we are going to create a simple service using a serverless function (Lambda)
![image](https://github.com/kanekotic/C-Movie/assets/3071208/b969786f-b54c-47f3-8e36-cfd630bf5157)


![image](https://github.com/kanekotic/C-Movie/assets/3071208/53c6e801-da68-4e7d-90ba-60a2e430bc75)
