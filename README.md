# serverless-lambda
![sketch](images/serverless-lambda.png) <br>
Using AWS Cloud9, producer and consumer lambdas were deployed to AWS Lamda. Code for each can be found in the "scripts" directory. In order to kick off the pipeline, an Amazon CloudWatch event is configured to trigger at a set interval. This starts the producer lambda, which pulls rows from a DynamoDB table containing a list of names. Those names are put into Amazon SQS for its practically limitless scalability. Every time a "message" is received from the producer lamba, SQS sends to the consumer lambda. The consumer lambda empties the SQS queue, defines Wikipedia sentiment and forwards to Amazon Comprehend for sentiment analysis. Finally, the outputted csv files are put into an S3 bucket. The resulting csv consists of three columns - name of the entity, a 1 sentence wikipedia snippet description, and associated sentiment. <br>

A demo and more hands-on overview of the serverless engineering pipeline can be found here: https://www.youtube.com/watch?v=2tTJc_zwmcw <br>

More detailed, step-by-step instructions can be found at Professor Gift's GitHub repository: https://github.com/noahgift/awslambda/blob/master/beginners_guide_aws_lambda.ipynb
