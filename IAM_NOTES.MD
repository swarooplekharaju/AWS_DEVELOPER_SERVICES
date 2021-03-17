#  IAM[]

Stands for "identity and access management"
Has a global view
Helps in authentication and authorization
Responisble for permissions for an user and services 
Three main classifications of iam users are 
1. users --> single iam user per person
2. role - set of rules applied to restrict access to respective services which are applied on users
example : application1-programmers
application1-devops etc
4. groups :-> users on with common permission 
## FEAUTURTES OF IAM 

1. Creation of users, groups and roles
2. provides secure authentication using services like password manager and mfa
3. creation of policies for allowing and denying the service acess request 
4. through fedration provides iam facility for private users as well 
5. policy simuator - for dry run to test before production
## IAM POLICY :
permisions to allow/deny
json formatt
policies are attached to principals [measns the resources users groups roles ]
broadly two types :
1.identity based for users,roles and groups
  futher inline and managed[either by customer or aws managed ]
2. resouce based for aws resouces like s3,dbs etc 
             only inline policies 
EXAMPLE OF IDENTITY POLICY TO  ACESS DYNAMO DB 
{
"version":XXXXXXXX
"statement ":  
 {
 "EFFECT" : "ALLOW"
 "ACTION":"DYNAMODB"
 "RESOURCE": ARN OF DYNAMODB 
}
 EXAMPLE OF RESOURCE BASED POLICY FOR S3 PUT OBJECT GRANT ACCESS           
{
"VERSION":
"STATEMENT" :{
"PRINCIPAL" : "ARN OF WHO HAS GIVEN ACESS  ARN/USER_CHINTU"
 "ACTION":{
"S3": "*PUTOJECT"
}
}            
By seeing the principal and effect we can whether its resouce based or identity based
mostly effect allow/deny is seen in identity polices
and principal and action is seen in resource based policies 

evaluation of policies :
logical or style 
deny by default
explicit deny -deny at last
explicit allow - allow at last
neither default deny 

example policy for s3 list buckets :

{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "VisualEditor0",
            "Effect": "Allow",
            "Action": [
                "s3:ListStorageLensConfigurations",
                "s3:ListBucketMultipartUploads",
                "s3:ListAllMyBuckets",
                "s3:ListJobs",
                "s3:ListBucketVersions",
                "s3:ListBucket",
                "s3:ListMultipartUploadParts"
            ],
            "Resource": "*"
        }
    ]
}

# IAM ROLES 
ROLE -> ACESS MULTIPLE AWS RESOUCES 
PERMISSIONS FOR CROSS ACCOUNT AND THIRD PARTY
supports role chaining
helps in delegate acess[permitt without passwords]
one role for ec2 
no role to iam group
example s3 acessand put object role to ec2 



###  security practices 
delete root keys 
create iam users to diversify the policies for proper management
have mfa on tour device for secure acess 
have an password policy for dynamicity

