# newspaper3k_lambda_template
This provides a template for creating a lambda function using newspaper3k without needing to deal with the pain of actually doing it yourself. Just change the contents of ./lib/lambda.py to whatever you need and run `make build` as the specified dependencies are already pre-built in ./lib/base.zip. If you need additional dependencies, however, see below. Hopes this saves someone some time!


## Testing
To test this package run the following command:
```
make test
```

## Building
To build your deployment package, make whatever changes you want to make to newspaper_lambda.py and run:
```
make build
```
This will move the primary script `./lib/newspaper_lambda.py` to the build directory along with its dependencies and then package them with zip into `./build/newspaper_lambda.zip` this zip will then be in the correct format for pushing to aws!

Now you're development jigsaw environment should be able to access your function!

## Adding new dependencies
If at any point you need to change the dependencies associated with this package, you should run `make build.start` and follow the steps.

Note, that `make build.start` requires that you have access to a server running the Amazon Linux AMI and that you have added an entry named lambda_builder to your ~/.ssh/config which points to it. You will also have to have python3 installed on that server.

To install python3 on your new server run the following steps:
```
sudo yum install gcc gcc-c++ libjpeg-devel zlib-devel libevent-devel libxml2-devel libxslt-devel libpng-devel
sudo yum install python36-devel python36-pip
```
