## Terraform
* IAM Policy https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_policy
* IAM Role https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_role
* Application Servers Security Group for EC2 instance  https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/security_group
* DB Servers Security Group https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/security_group 
* S3 Bucket https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/s3_bucket
* RDS Instance https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/db_instance
* EC2 Instance  https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/instance
  

EC2 instance should be launched with User Data

## Web Application
Add file APIs

1. Write metadata into RDS database
2. Upload file to S3 Storage
3. Delete metadata on RDS database
4. Delete file from S3 Storage

Edit boos APIs
POST /books 

https://lorenstewart.me/2016/09/12/sequelize-table-associations-joins/

"userId"
https://stackoverflow.com/questions/57554744/sequelize-associate-creating-both-userid-and-user-id-for-one-model-but-not-the

## Logic

### RDS
You have to use `userdata` to write environment variables for RDS credentials.
```
HOST: "Your RDS Instance Host Name"
USER: ""
PASSWORD: ""
PORT: ""
DB: ""
```


### S3

You have to run application on the EC2 instance which has S3 **IAM role** that attached to right **security group**.
You don't need to write any credential for accessing S3 storage.


**How to upload file to S3**
```javascript
const fs = require('fs');
const AWS = require('aws-sdk');
const path = require('path');

var file = process.argv[3];
var s3 = new AWS.S3();


const uploadFile = (file) => {
    // Read content from the file
    const fileContent = fs.readFileSync(file);

    // Setting up S3 upload parameters
    const params = {
        Bucket: process.argv[2],
        Key: '', // File name you want to save as in S3
        Body: fileContent
    };

    params.Key = path.basename(file);

    // Uploading files to the bucket
    s3.upload(params, function(err, data) {
        if (err) {
            throw err;
        }
        console.log(`File uploaded successfully. ${data.Location}`);
    });
};

const deleteFile =  (file) => {
  var params = {
      Bucket: process.argv[2],
      Key: ''
   };

       params.Key = path.basename(file);

   s3.deleteObject(params, function(err, data) {
     if (err) console.log(err, err.stack); // an error occurred
     else   {
        console.log(`File deleted successfully.`);
     }            // successful response
     /*
     data = {
     }
     */
   });
}

uploadFile(file);
```