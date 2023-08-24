# Solution

The C-Movie Platform is going to compete in a crowded business space. For this is important before doing a big upfront investment to validate if there is a business value on the project. 

For this, the solution should be solved in different phases:
- **Discovery**: Understand the problem.
- **MVP**: Answer unknowns to validate the validity of the project, and if so start building SEO Ranking.
- **MLP**: Start validating our algorithm is a value adder.
- **Phase 1**: Initialize the data platform & products.
- **Phase 2**: Standardize the architecture.

**Discovery, MVP & MLP** should be very short cycles of development as they build the confidence on the value of the project, and require a lot of synchronization between disciplinary departments. On the other side, **Phase 1 & 2** are long-term strategy, so they might reduce the feedback cycle and also the need for synchronization with other departments.

## Discovery

If we run a domain discovery using event storming, we can see the next situation:

![image](https://github.com/kanekotic/C-Movie/assets/3071208/05086a9e-3861-47e6-850e-b5ae083db6e1)

This means we have at least 2 flow streams of work:
- Conversion: related to attracting users and making them use our service in a recurrent way.
- Movies: will provide the capability for:
  - search movies
  - Calculate ratings
  
  We can start having a smells that this might be 2 different subdomains.

We also gathered some data on our competitors that will help us take some decisions in the MVP phase. For example, extracting insights from Google trends, our main competitor by traffic will be IMDB. So we are going to go with the supposition that their data has a better quality that is driving the higher traffic.

![Image](https://github.com/kanekotic/C-Movie/assets/3071208/b969786f-b54c-47f3-8e36-cfd630bf5157)

## MVP

### Business Intent

We aim to solve the next questions:
- Are users interested in a new movie platform?
  - **Success Criteria**: We have 10k Monthly unique visitors, with at least 8% of conversion rate tracked by the CTA.
- Do we have the expected granularity data from our main competitor?
   - **Success Criteria**: We have >=80% of the required data from a single provider.

An added benefit is that we can start building an SEO ranking that will be required for the project to be a success in the long term.

> If the success criteria are achieved, we continue with the project.
> After this phase is still possible that the project is cancelled.

### Architecture

We are going to create a simple service[^1]:
- A frontend application in [Amplify](https://aws.amazon.com/es/amplify/) for users to access our content.
- A serverless function using [Lambda](https://aws.amazon.com/es/lambda/) that will provide the data. In front of this Lambda, we will provision:
    - [API Gateway](https://aws.amazon.com/es/api-gateway/): to make the lambda accessible from the internet
    - [WAF](https://aws.amazon.com/es/waf/): to prevent scrapping and abuse that could affect our costs.

![Image](https://github.com/kanekotic/C-Movie/assets/3071208/0cf3d4b8-7a2a-46b7-bf61-52eb773298ea)

The lambda implementation will only work as a pass-through transformation of the data retrieved from IMDB API, where we will convert the data to our expected model, meaning that in the MVP the lambda is an anti-corruption layer that works as a BFF.

We will define our data model as:
```js
{
  title: string,
  genre: string,
  rating: {
    performance: number[0-100],
    screenplay: number[0-100],
    soundtrack: number[0-100]
  }
}
```

## MLP 

### Business Intent

We aim to solve the next questions:
- Is our proprietary algorithm adding value?
  - **Success Criteria**: With an A/B test, we see an increase of 5% for the c-movie Algorithm users.

> If the success criteria are achieved, we continue with the project.
> After this phase we have the certainty the project will not be cancelled.

### Architecture

We will do the next 2 tasks: 
- Create an implementation of the rating algorithm. 
- Add a new mainstream data source like `rotten tomatoes` to feed the algorithm. 

![Image](https://github.com/kanekotic/C-Movie/assets/3071208/cb5694ea-c9d8-44b2-94db-d6e4101a6d27)


## Phase 1: Expand sources

### Business Intent

We aim to:
- Expand the accuracy of the algorithm with more data sources
  - **Success Criteria**: We see an increase in the returning users of 1%.

### Architecture

We work on the long-term solution, for this, we are going to start the batch processing platform (Data lake). 

We will have 4 zones:
- Landing: Raw data consumed in original format
- Refined: Transformation into data friendly handling format (ex. parquet)
- Validated: Transformation into standardized data model
- Production: aggregation of multiple validated data sources

We will load the production level data into a transaction data source to be able to integrate to the current solution.

![Image](https://github.com/kanekotic/C-Movie/assets/3071208/60ad30b8-3036-47bf-be8f-11a383f7e815)

## Phase 2: Performance and Cost optimization

### Business Intent

We aim to:
- Increase user satisfaction
  - **Success Criteria**: We see an increase in the returning users of 3%.
- Reduce the cost of our solution
  - **Success Criteria**: We see a decrease in our running cost of 5%.

### Architecture

The tasks in this phase will be to:
- Migrate the existing direct access data sources (IMDB & Rotten Tomatoes) into de Data Lake to comply with the long-term solution. Removing also unrequired access to the API and delays.
- Create a production level data product that will be a batch implementation of the proprietary algorithm. To feed it into the solution, we will:
  - Add the data to a [DynamoDB](https://aws.amazon.com/es/dynamodb/) as the access will be by an indexed value. This will improve performance and costs from the RDS solution.
  - Use `expand & contract`to start consuming from the new data source and deprecate the old code.

![Image](https://github.com/kanekotic/C-Movie/assets/3071208/3014b1b6-8f96-4390-bf59-bda4902210e4)

[^1]: We assume we are working in AWS
