# Serverless APP
Tech: S3, DynamoDB, Lambda, CloudFormation, API Gateway

## Install serverless
```
npm install -g serverless
```

## Create the project
```
serverless create --template aws-nodejs-typescript --path certificateignite

cd certificateignite && yarn
```

### Create a hello function
### Install serveverless-offline to test locally and run it
Add it to the serverless.ts > plugins
```
yarn add serverless-offline -D

serverless offline
```
Access: localhost:3000/dev/hello

### DynamoDB config 
Add dynamo DB resource to serverless.ts > resources.

Install dynamodb local:
```
yarn add serverless-dynamodb-local -D
```

Install DynamoDB and start it:
Obs.: Download Java jdk 17 first
```
serverless dynamodb install

serverless dynamodb start
```

### Test request POST http://localhost:3000/dev/generateCertificate
```
{
    "id": "<uuid>",
    "name": "<name>",
    "grade": "<grade>"
}
```

### [AWS] IAM > Add user userServerlessIgnite
[x] Chave de acesso: acesso programático

Anexar políticas existentes de forma direta:
[x] AdministratorAccess

**Copy access key and secret access key**

### Apply credentials
Run:
```
serverless config credentials --provider aws --key=<access_key> --secret <secret_access_key> -O

cd ~/.aws && ls
```

### Deploy
```
yarn deploy
```
Copy endpoint and test it.

### [AWS] Check for Lambda functions

### Install handlebars
Apply it for the template creation.
```
yarn add handlebars

yarn add @types/handlebars -D
```

### Install chrome aws lambda for generating the PDF
```
yarn add chrome-aws-lambda puppeteer-core

yarn add puppeteer -D
```

TIP:  "esModuleInterop": true enables to import dependencies without "* as some".

### [AWS] S3 > Create a new bucket certificate-ignite-2022
- us-east-1
[ ] Bloquear todo o acesso público
[x] Reconheço que as configurações atuais podem fazer com que este bucket e os ob jetos dentro dele se tornem públicos

