# amazon dynamodb

## dynamodb-local

... for testing with a local dynamodb database

it's best to get the [docker version here](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/DynamoDBLocal.Docker.html) since it's the easiest way to run it.

**start the database like so**:

for the lazy people, it's quite important to add the `-sharedDB` parameter, otherwise you'd have to mess around with permissions and access rules and so on, which is kinda boring if you run it in a test environment for a few seconds.

```
docker run -it --rm -p8000:8000 amazon/dynamodb-local -jar DynamoDBLocal.jar -inMemory -sharedDb
```

**create tables**:

I found the easiest way to create tables is to feed a json file to the aws-cli with the correct endpoint of your local dynamodb:

```
aws dynamodb create-table --endpoint-url http://localhost:8000 --cli-input-json file://my-table.json
```

`my-table.json` could look like this:

```
{
    "AttributeDefinitions": [
        {
            "AttributeName": "short",
            "AttributeType": "S"
        },
        {
            "AttributeName": "long",
            "AttributeType": "S"
        }
    ],
    "TableName": "u4j",
    "KeySchema": [
        {
            "AttributeName": "short",
            "KeyType": "HASH"
        }
    ],
    "GlobalSecondaryIndexes": [
        {
            "IndexName": "long-index",
            "KeySchema": [
                {
                    "AttributeName": "long",
                    "KeyType": "HASH"
                }
            ],
            "Projection": {
                "ProjectionType": "ALL"
            },
            "ProvisionedThroughput": {
                "ReadCapacityUnits": 5,
                "WriteCapacityUnits": 5
            }
        }
    ],
    "BillingMode": "PAY_PER_REQUEST",
    "ProvisionedThroughput": {
        "ReadCapacityUnits": 5,
        "WriteCapacityUnits": 5
    }
}
```

you can use something like *aws cdk* to generate such json templates.
