This creates a Lambda functions for testing if they will hang after initial 
invocation.

To build and deploy:

    ./deploy.sh <s3_bucket_name>
    
To trigger the behavior set the event to a map: {"timeout": 6000}

# Issues being tracked

 * petkaantonov/bluebird: [Bluebird unusable in AWS Lambda / NodeJS #1341][20]
 * nervous-systems/cljs-lambda: [Async functions become unreponsive if Lambda global timeout occurs #62][21]
    
# Background
 * Read up on [container reuse in Lambda][10]. 
 * Context exit methods are deprecated [Using the Earlier Node.js Runtime v0.10.42 - AWS Lambda][1] which mentions in the [transitioning to new nodejs runtime][2] that the latest lambda wants us to use the newer callback method instead of using context object calls. 
 * Past report of this bug: [AWS Lambda – constant timeout when using bluebird Promise][30]


[1]: http://docs.aws.amazon.com/lambda/latest/dg/nodejs-prog-model-using-old-runtime.html
[2]: http://docs.aws.amazon.com/lambda/latest/dg/nodejs-prog-model-using-old-runtime.html#transition-to-new-nodejs-runtime
[10]: https://aws.amazon.com/blogs/compute/container-reuse-in-lambda/
[20]: https://github.com/petkaantonov/bluebird/issues/1341
[21]: https://github.com/nervous-systems/cljs-lambda/issues/62
[30]: http://theburningmonk.com/2016/05/aws-lambda-constant-timeout-when-using-bluebird-promise/
