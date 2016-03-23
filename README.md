# node_aws
Notes on how to deploy using Dynamo and Node.js

1. Create user in AWS IAM for application
2. Save access key and secret (Download CSV)
3. Assign role to user that allows access to dynamo
  {"Effect": "Allow",
            "Action": [
                "dynamodb:*"
            ],
            "Resource": [
                "*"
            ]
  }

4. Setup node on local environment
5. npm install aws-sdk
6. node init a repo
7. configure local ~/.aws/credentials with access key & secret
[default]
  aws_access_key_id = xxx
  aws_secret_access_key = xxx
8. Test to make sure you can get your dynamodb tables using this code (save as test.js and the run node test.js):
  var AWS = require("aws-sdk");
  AWS.config.update({
    region: "us-east-1"
  });
  var db = new AWS.DynamoDB();
  db.listTables(function(err, data) {
  console.log(data.TableNames); //if output to console is list of dynamo tables, your auth is working
  });
9. Setup query
10. Run query
