# Managing AWS IAM User Permissions Using Groups and Policies

- Link -> [https://learn.acloud.guru/handson/4b52d9c3-b09d-4dd5-8117-42c67bc26354/course/aws-certified-cloud-practitioner](https://learn.acloud.guru/handson/4b52d9c3-b09d-4dd5-8117-42c67bc26354/course/aws-certified-cloud-practitioner)

![lab_diagram_Groups_and_Policies_Diagram](./images/lab_diagram_Groups_and_Policies_Diagram.png)

## 시나리오

Kia라는 소프트웨어 엔지니어가 기업가가 되려고 합니다.

그녀는 그녀의 스타트업을 AWS에서 런칭하려고 합니다.

우리는 다음 리스트들로 Kia를 도와주려고 합니다.

- Grouping users
- Assigning permissions using policies
- Best practices

## Introduction

In this hands-on lab scenario, you are a security engineer working for a new startup that's launching an online bookstore for rare and antique books. The founder, Kia, needs your help with setting up her development team with the proper access permissions. In order to provide access and ensure the proper security measures are in place, you will use AWS Identity & Access Management (IAM). You will group users and assign permissions for the developer group using policies.

## Solution

Log in to the live AWS environment using the credentials provided. Make sure you're in the N. Virginia (us-east-1) region throughout the lab.

### Create a Customer-Managed Policy

1. Navigate to IAM.
2. In IAM Resources, click Users to view existing users.
3. From the left dashboard menu, click Policies to create a new policy with developer access.
4. Click `Create policy`.
5. Click the `Visual editor` tab.
6. Set the following values:
   1. Service: "DynamoDB"
   2. Actions: All DynamoDB actions
   3. Resources: All resources
7. Click `Add additional permissions`.
8. Repeat the steps above to configure new policy permissions for `Lambda`, `S3`, and `API Gateway` services.
9. Click `Review policy`.
10. Enter a standard name for your policy and a brief description.
    - naming -> [appname]-[department]-[groupname]-[access]
    - ex) onlinebookstore-dev-developergroup-fullaccess-iam-policy
11. Click `Create policy`.

### Create a Group Controlled via a Customer-Managed Policy

1. From the left dashboard menu, select Groups.
2. Click `Create New Group`.
3. Enter the group name `Developers` and click `Next Step`.
4. Select the newly created policy and click `Next Step`.
5. Review the group information, and then click `Create Group`.

### Assign Users to a Group

1. From the IAM Groups menu, select the `Developers` group.
2. Select the Users tab and click `Add Users to Group`.
3. Select the three developers we want to add to the group and click Add Users.

## Conclusion

Congratulations — you've completed this hands-on lab!
