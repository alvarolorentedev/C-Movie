# Solution

The C-Movie Platform is going to compite in a crowded bussiness space. For this is important before doing a big upfront investment validate if there is a bussiness value on the project. For this the solution should be solved in diferent phases.
- **Discovery**: Understand the problem.
- **MVP**: Answer unkowns to validate the validity of the project, and if so start building SEO Ranking.
- **MLP**: Start validating our algorithm is a value adder.
- **Phase 1**: Initialize the data platform & products.
- **Phase 2**: Standardize the architecture.

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

The lambda implementation will only work as a passthrough transformation of the data retrieved from IMDB.

### Success criteria 
 - We have >=80% of the required data from a single provider.
 - We have 10k Monthly unique visitors, with at least 8% of conversion rate  tracked by the CTA.

## MLP 

We are going to start adding a new source and integrate our propietary algorithm.

![image](https://github.com/kanekotic/C-Movie/assets/3071208/877e4380-75c4-4382-aed2-e34acfa945f9)


### Success criteria 
 - With an A/B test, we see an increase of 5% for the c-movie Algorithm users.

## Phase 1

After validation that our algorithm improves the general engagement we need to expand on the long term solution, for this we are going to start the batch procesing platform (Datalake). 

In this first phase we will have 4 zones:
- Landing: Raw data consumend in original format
- Refind: Transformation into data friendly handling format (ex. parquet)
- Validated: Transformation into standardized data model
- Production: aggregation of multiple validated data sources

We will load the production level data into a transaction data source to be able to integrate to the current solution.

![image](https://github.com/kanekotic/C-Movie/assets/3071208/e5785059-e9ad-4f66-b6ed-38144fcb1025)


### Success criteria 
 - ...

## Phase 2

Finally we will migrate the existing direct access data sources into de Data Lake to comply with the long term solution.

We will create a new production level data product based in the previous one that agregates data sources, this new data product will be a migration of the algorithm from the lambda into this batched solution. This will populate a new DynamoDB that will simplify the access to the data.

![image](https://github.com/kanekotic/C-Movie/assets/3071208/7183e284-1ff2-45f6-bc54-f27e8949afe3)


### Success criteria 
 - ...
