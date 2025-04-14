# AWS Lambda Microservices in Rust with Cargo

This repo is a modified version from the Coursera Guided Project
[Building Rust AWS Lambda Microservices with Cargo Lambda](https://www.coursera.org/projects/building-rust-aws-lambda-microservices-with-cargo-lambda) 
by [Noah Gift](https://www.linkedin.com/in/noahgift/) from Duke University.
Original [repo](https://github.com/nogibjj/aws-lambda-rust/tree/main)



## Key Terms:

Handler - The Rust function that gets invoked to handle a Lambda event and context
Payload - The input data passed to the handler function
Response - The output data returned from the handler function
Tracing - Logging debug/trace information using the tracing crate
Serialization - Converting Rust data structures to and from formats like JSON

```rust
// Handler function definition 
async fn function_handler(event: LambdaEvent<Request>) -> Result<Response, Error> {

    // Access payload data
    let greeting = event.payload.greeting;
    
    // Return response 
    Ok(Response {
        req_id: event.context.request_id,
        msg: format!("Hello {}!", greeting)
    })
}

// Serialize/deserialize payload  
#[derive(Deserialize)]
struct Request {
    greeting: String,
}

#[derive(Serialize)]
struct Response {
    req_id: String,
    msg: String
}
```



## Cargo Lambda
[Cargo Lambda](https://www.cargo-lambda.info/guide/getting-started.html) allows creating AWS Lambda functions with Rust locally without needing containers or virtualization. The getting started guide walks through installing Cargo Lambda, initializing a new project, running and testing functions locally, building for deployment, and deploying to AWS Lambda.

### Key Points:

Cargo Lambda taps into Cargo for Lambda function creation and deployment
Cargo Lambda streamlines Lambda development in Rust without containers
Functions can be tested and debugged locally before deploying
Functions execute as fast, optimized binaries on AWS
Building creates a package ready for AWS Lambda deployment
Logging helps debug issues in both development and production


### Summary

This lesson covered using Cargo Lambda to develop AWS Lambda functions with Rust. Key topics included:
Installing Cargo Lambda
Creating a new Lambda project
Implementing handler logic in Rust
Testing and invoking functions locally
Adding logging with the tracing crate
Building release artifacts for deployment
Deploying to AWS Lambda
Invoking deployed functions

### Reflection Questions:

What are some potential advantages of using Rust and Cargo Lambda for Lambda development over other languages?
How could testing and debugging functions locally before deploying help accelerate development?
What are some ways Cargo Lambda could integrate into a CI/CD pipeline for Lambda deployment?
For what types of Lambda applications might Rust be particularly well suited?
What are some next steps to take after deploying an initial function to gain more capability?
What advantages does using Rust bring compared to other Lambda languages?
How could logging help diagnose issues in a deployed Lambda function?
In what scenarios might you choose Rust over Python or Node.js?
What other AWS services could you connect a Rust Lambda to?
How might this local testing approach integrate with CI/CD pipelines?

### Challenges:

Initialize a Cargo Lambda project and write a simple Lambda handler function
Test invoking the function locally with different payloads
Experiment with logging and tracing locally
Deploy the function to AWS Lambda
Set up API Gateway to create a web endpoint for the Lambda
Add environment variables to configure function behavior
Create an HTTP endpoint with API Gateway
Benchmark performance compared to a Python Lambda
Containerize the function for Lambda layers
Autoscale the function based on CloudWatch metrics



## Other Courses recommended by Noah Gift:

[Python and Rust with Linux Command Line Tools](https://insight.paiml.com/jot)
Integrate Rust modules into Python applications with PyO3. Build command line utilities, system tools, web services and more.

[Rust Programming Specialization](https://insight.paiml.com/qwh)
A 5-course specialization covering intermediate to advanced Rust programming. Includes projects on systems programming, web services, data engineering and contributing to open source.

[Rust for DevOps](https://insight.paiml.com/x14)
Go beyond development into DevOps by building a CI/CD pipeline for a Rust application.

[Rust LLMOps](https://insight.paiml.com/g3b)
Leverage Rust for large language model operations with projects like Candle. Generate code, summarize documentation, automate tasks and more.

[Rust Fundamentals](https://insight.paiml.com/qyt)
Master essential Rust syntax, concepts like ownership and borrowing, error handling, generics, and testing.

[Data Engineering with Rust](https://insight.paiml.com/zm1)
Use Rust for real-time data pipelines, analytics, and working with databases at scale. Interoperate with Python, Polars, and cloud data services.
