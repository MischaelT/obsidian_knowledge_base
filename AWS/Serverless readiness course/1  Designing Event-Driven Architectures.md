 This term represents abstracting your computing infrastructure to the point that you have no responsibilities for the servers on which your code runs. This means when your application isn't running, you're not paying for idle server time.  
  
Abstracting infrastructure is not a new cloud concept, and the availability of services that further reduce your operational responsibility are increasing. This reflects an industry-wide shift and an architectural evolution toward microservices because of the flexibility and agility they provide.

Event-driven architectures use events to communicate between and invoke decoupled services. 

Microservices are event-driven and use events to communicate between and invoke decoupled services. These events are simple changes, or updates, to a state such as an item being placed in a shopping cart on an ecommerce website.

As you choose the managed services that support your event-driven patterns, you should learn and internalize the service characteristics that influence your choices. These can include the following:

- Decoupling the user experience and running code
- Providing reduced latency on HTTP responses
- Reducing the potential for timeouts or deadlocks

## Simple serverless pattern

Let’s start with a simple serverless pattern to process orders within an ecommerce workflow. This is a straightforward pattern for a RESTful microservice that is not complicated to implement. Here is how an order will be processed by this ecommerce workflow:

1) The order information comes in through an API call over HTTP. 
   The issue in here is that any error will have to go all the way back the the client, and your frontend will have to handle these error.
2) Amazon API Gateway handles requests and responses to those API calls.
   The issue here is that thay the Gateway expects an immediate response to the request and it has 30 siconds timeout, while lambda usually has 15mins.
3) Lambda contains the business logic to process the calls.
   The retry logic isnt built in the lambda, so the developer is responsible for that.
4) Amazon DynamoDB provides persistent storage.

Instead of this approach, it can be better for you to use an asynchronous pattern. Continue to the next lesson to look at ways to introduce asynchronous connections into common patterns.

## Serverless Event submission patterns

### Amazon SQS 
Message queues are a good solution for decoupling synchronous connections between API Gateway and Lambda. By introducing the SQS queue in front of Lambda, you can create an asynchronous connection between the API request and Lambda.  This allows you to satisfy the API request without regard for how long the Lambda function (or other backend services) will run. SQS queues have retries built in, and you can configure them with dead-letter queues for messages that cannot be processed.