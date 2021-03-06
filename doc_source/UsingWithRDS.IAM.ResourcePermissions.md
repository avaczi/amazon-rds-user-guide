# Amazon RDS API Permissions: Actions, Resources, and Conditions Reference<a name="UsingWithRDS.IAM.ResourcePermissions"></a>

When you set up [Access Control](UsingWithRDS.IAM.md#UsingWithRDS.IAM.AccessControl) and write permissions policies that you can attach to an IAM identity \(identity\-based policies\), you can use the following as a reference\. 

The following lists each Amazon RDS API operation\. Included in the list are the corresponding actions for which you can grant permissions to perform the action, the AWS resource that you can grant the permissions for, and condition keys that you can include for fine\-grained access control\. You specify the actions in the policy's `Action` field, the resource value in the policy's `Resource` field, and conditions in the policy's `Condition` field\. For more information about conditions, see [Using IAM Policy Conditions for Fine\-Grained Access Control](UsingWithRDS.IAM.Conditions.md)\. 

You can use AWS\-wide condition keys in your Amazon RDS policies to express conditions\. For a complete list of AWS\-wide keys, see [Available Keys](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements.html#AvailableKeys) in the *IAM User Guide*\. 

You can test IAM policies with the IAM policy simulator\. It automatically provides a list of resources and parameters required for each AWS action, including Amazon RDS actions\. The IAM policy simulator determines the permissions required for each of the actions that you specify\. For information about the IAM policy simulator, see [ Testing IAM Policies with the IAM Policy Simulator](http://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_testing-policies.html) in the *IAM User Guide*\. 

**Note**  
To specify an action, use the `rds:` prefix followed by the API operation name \(for example, `rds:CreateDBInstance`\)\.

The following lists RDS API operations and their related actions, resources, and condition keys\.


+ [Amazon RDS Actions That Support Resource\-Level Permissions](#UsingWithRDS.IAM.ResourceLevelPermissions)
+ [Amazon RDS Actions That Don't Support Resource\-Level Permissions](#UsingWithRDS.IAM.UnsupportedResourceLevelPermissions)
+ [Related Topics](#w3ab1c21c13c15c33)

## Amazon RDS Actions That Support Resource\-Level Permissions<a name="UsingWithRDS.IAM.ResourceLevelPermissions"></a>

Resource\-level permissions refers to the ability to specify the resources on which users are allowed to perform actions\. Amazon RDS has partial support for resource\-level permissions\. This means that for certain Amazon RDS actions, you can control when users are allowed to use those actions based on conditions that have to be fulfilled, or specific resources that users are allowed to use\. For example, you can grant users permission to modify only specific DB instances\.

The following lists RDS API operations and their related actions, resources, and condition keys\.

[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.ResourcePermissions.html)

## Amazon RDS Actions That Don't Support Resource\-Level Permissions<a name="UsingWithRDS.IAM.UnsupportedResourceLevelPermissions"></a>

You can use all Amazon RDS actions in an IAM policy to either grant or deny users permission to use that action\. However, not all Amazon RDS actions support resource\-level permissions, which enable you to specify the resources on which an action can be performed\. The following Amazon RDS API actions currently don't support resource\-level permissions\. Therefore, to use these actions in an IAM policy, you must grant users permission to use all resources for the action by using a `*` wildcard for the `Resource` element in your statement\.

+ [DescribeAccountAttributes](http://docs.aws.amazon.com/AmazonRDS/latest/APIReference/API_DescribeAccountAttributes.html) \(Action: `rds:DescribeAccountAttributes`\)

+ [DescribeCertificates](http://docs.aws.amazon.com/AmazonRDS/latest/APIReference/API_DescribeCertificates.html) \(Action: `rds:DescribeCertificates`\)

+ [DescribeDBClusterSnapshots](http://docs.aws.amazon.com/AmazonRDS/latest/APIReference/API_DescribeDBClusterSnapshots.html) \(Action: `rds:DescribeDBClusterSnapshots`\)

+ [DescribeDBInstances](http://docs.aws.amazon.com/AmazonRDS/latest/APIReference/API_DescribeDBInstances.html) \(Action: `rds:DescribeDBInstances`\)

+ [DescribeEngineDefaultClusterParameters](http://docs.aws.amazon.com/AmazonRDS/latest/APIReference/API_DescribeEngineDefaultClusterParameters.html) \(Action: `rds:DescribeEngineDefaultClusterParameters`\)

+ [DescribeEngineDefaultParameters](http://docs.aws.amazon.com/AmazonRDS/latest/APIReference/API_DescribeEngineDefaultParameters.html) \(Action: `rds:DescribeEngineDefaultParameters`\)

+ [DescribeEventCategories](http://docs.aws.amazon.com/AmazonRDS/latest/APIReference/API_DescribeEventCategories.html) \(Action: `rds:DescribeEventCategories`\)

+ [DescribeOrderableDBInstanceOptions](http://docs.aws.amazon.com/AmazonRDS/latest/APIReference/API_DescribeOrderableDBInstanceOptions.html) \(Action: `rds:DescribeOrderableDBInstanceOptions`\)

+ [DownloadCompleteDBLogFile](RESTReference.md#RESTReference.DownloadCompleteDBLogFile) \(Action: `rds:DownloadCompleteDBLogFile`\)

+ [PurchaseReservedDBInstancesOffering](http://docs.aws.amazon.com/AmazonRDS/latest/APIReference/API_PurchaseReservedDBInstancesOffering.html) \(Action: `rds:PurchaseReservedDBInstancesOffering`\)

## Related Topics<a name="w3ab1c21c13c15c33"></a>

+ [Access Control](UsingWithRDS.IAM.md#UsingWithRDS.IAM.AccessControl)

+ [Using IAM Policy Conditions for Fine\-Grained Access Control](UsingWithRDS.IAM.Conditions.md)

+ [Security in Amazon RDS](UsingWithRDS.md)