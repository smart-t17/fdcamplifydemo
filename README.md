# fdc
http://fdcamplify.s3-website-us-east-1.amazonaws.com

## Creating & configuring the Vue project

npm install -g @vue/cli

## Clone project and install dependencies 

### Getting Started

1. Clone project and install dependencies 

```
$ git clone https://github.com/smartmaxdev/fdcamplifydemo.git
```

```
$ cd fdcamplifydemo
```

```
$ npm install
```

2. Intialize a new [AWS Amplify CLI](https://github.com/aws-amplify/amplify-cli) project:

```
$ npm install -g @aws-amplify/cli
```

```
$ amplify init
```

```
$ amplify add auth
```

```
$ amplify push
```

### Compiles and hot-reloads for development
```
$ npm run serve
```

### Compiles and minifies for production
```
$ npm run build
```
### deploy to s3 bucket

```
$ sh deployment.sh prod
```

### Run your tests
```
$ npm run test
```
