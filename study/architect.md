# AWS Solutions Architect Associate

## CLI-Fu

    aws configure list

## Exercises

### S3
* 2.1 Create an Amazon Simple Storage Service (Amazon S3) Bucket

        aws s3 mb s3://bucket-name

* 2.2 Upload, Make Public, Rename, and Delete Objects in Your Bucket

        aws s3 sync . s3://bucket-name
        aws s3api put-object-acl --acl public-read --bucket bucket-name --key a.txt
        curl http://bucket-name.s3.amazonaws.com/a.txt
        aws s3 mv s3://bucket-name/a.txt s3://bucket-name/b.txt
        aws s3 rm s3://bucket-name/b.txt

* 2.3 Enable Version Control

        aws s3api put-bucket-versioning --bucket bucket-name --versioning-configuration Status=Enabled

* 2.4 Delete an Object and Then Restore It

        aws s3 rm s3://bucket-name/c.txt
        aws s3api list-object-versions --bucket bucket-name --prefix c.txt
        aws s3api get-object --bucket bucket-name --key c.txt --version-id xaKVwvHfEX8Yp1xcgCqbh1Q7SCbkjr9e foo.txt
        aws s3 cp foo.txt s3://bucket-name/d.txt


* 2.5 Lifecycle Management

        aws s3api put-bucket-lifecycle --bucket bucket-name --cli-input-json {"Rules":[{"Filter":{"Prefix":"documents/"},"Status":"Enabled","Transitions":[{"Days":365,"StorageClass":"GLACIER"}],"Expiration":{"Days":3650},"ID":"ExampleRule"}]}

* 2.6 Enable Static Hosting on Your Bucket

    https://stackoverflow.com/questions/34470502/difference-between-s3-public-files-and-static-websites

        aws s3 website s3://bucket-name --index-document d.txt
        curl http://bucket-name.s3-website.region-name.amazonaws.com

### EC2/EBS
* 3.1 Launch and Connect to a Linux Instance
* 3.2 Launch a Windows Instance with Bootstrapping
* 3.3 Confirm That Instance Stores Are Lost When an Instance Is Stopped
* 3.4 Launch a Spot Instance
* 3.5 Access Metadata
* 3.6 Create an Amazon EBS Volume and Show That It Remains After the Instance Is Terminated
* 3.7 Take a Snapshot and Restore
* 3.8 Launch an Encrypted Volume
* 3.9 Detach a Boot Drive and Reattach to Another Instance

### VPC
* 4.1 Create a Custom Amazon VPC
* 4.2 Create Two Subnets for Your Custom Amazon VPC
* 4.3 Connect Your Custom Amazon VPC to the Internet and Establish Routing
* 4.4 Launch an Amazon EC2 Instance and Test the Connection to the Internet