[![Build Status](https://travis-ci.org/wso2-ballerina/module-amazons3.svg?branch=master)](https://travis-ci.org/wso2-ballerina/module-amazons3)

# Ballerina Amazon S3 Connector

The Amazon S3 connector allows you to access the Amazon S3 REST API through ballerina. The following section provide you the details on connector operations.

## Compatibility
| Ballerina Language Version | Amazon S3 API version  |
| -------------------------- | -------------------- |
| 0.990.3                    | 2006-03-01                  |


The following sections provide you with information on how to use the Ballerina Amazon S3 connector.

- [Contribute To Develop](#contribute-to-develop)
- [Working with Amazon S3 Connector actions](#working-with-amazon-s3-endpoint-actions)
- [Sample](#sample)

### Contribute To develop

Clone the repository by running the following command 
```shell
git clone https://github.com/wso2-ballerina/module-amazons3.git
```

### Working with Amazon S3 Connector 

First, import the `wso2/amazons3` module into the Ballerina project.

```ballerina
import wso2/amazons3;
```

In order for you to use the Amazon S3 Connector, first you need to create an AmazonS3 Client endpoint.

```ballerina
amazons3:AmazonS3Configuration amazonS3Config = {
    accessKeyId: testAccessKeyId,
    secretAccessKey: testSecretAccessKey,
    region: testRegion,
    amazonHost: amazonHost
};

amazons3:Client amazonS3Client = new(amazonS3Config);
```

##### Sample

```ballerina
import ballerina/io;
import wso2/amazons3;

amazons3:AmazonS3Configuration amazonS3Config = {
    accessKeyId: "<your_access_key_id>",
    secretAccessKey: "<your_secret_access_key>",
    region: "<your_region>",
    amazonHost: "<your_host_name>"
};

amazons3:Client amazonS3Client = new(amazonS3Config);

public function main(string... args) {

    string bucketName = "testBallerina";
    var createBucketResponse = amazonS3Client->createBucket(bucketName);
    if (createBucketResponse is amazons3:Status) {
        // If successful, print the status of the operation.
        boolean status = createBucketResponse.success;
        io:println("Bucket Status: ", status);
    } else {
        // If unsuccessful, print the error returned.
        io:println("Error: ", createBucketResponse);
    }
}
```
