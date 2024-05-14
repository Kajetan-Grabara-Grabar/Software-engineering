# Ollama Chatter Enterprise

Ollama Chatter Enterprise is a web solution for chatting with various self-hosted LLM models deployed using the Ollama framework. 

It is created with two components:
1. Web user interface sending API calls to the backend.
2. Backend scalable Kubernetes application with load balancer enabling sending all the requests to just one endpoint. 

Provisioning to the GUI application works with AWS Congito's user pool. EKS cluster uses IAM Users. 

Users get a token from the AWS Cognito service and it is used to provision API calls to the AWS API gateway that serves as a bridge between the GuI and EKS cluster. Then the response is sent back. 