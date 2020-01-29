<html>
  <head>
    <meta charset="utf-8">
    <title>Linked Account Role Config
    </title>
    <link rel="icon" href="http://www.iconarchive.com/download/i87068/graphicloads/colorful-long-shadow/Cloud.ico" type="image/x-icon">
  </head>
  <body>
    <script src="https://code.jquery.com/jquery-3.2.1.min.js" integrity="sha256-hwg4gsxgFZhOsEEamdOYGBf13FyQuiTwlAQgxVSNgt4=" crossorigin="anonymous">
    </script>

      <br>
      <div class="margin" id="margin">
      <h1>Creating CloudHealth Role & Policy</h1>
      <h2>Amazon Web Services (AWS) Linked Account</h2>
      <p>1) Access the AWS Account's <a href="https://apps.cloudhealthtech.com/aws_accounts" target="_blank">page</a> & click the <img src="https://awsmedia.s3.amazonaws.com/favicon.ico"> icon of the account you'd like to configure.

      <br>

      <p>2) Copy the following IAM Access Policy:</p>
      <input type="text" value="
{
  &quot;Version&quot;: &quot;2012-10-17&quot;,
  &quot;Statement&quot;: [
    {
      &quot;Effect&quot;: &quot;Allow&quot;,
      &quot;Action&quot;: [
        &quot;autoscaling:Describe*&quot;,
        &quot;aws-portal:ViewBilling&quot;,
        &quot;aws-portal:ViewUsage&quot;,
        &quot;cloudformation:ListStacks&quot;,
        &quot;cloudformation:ListStackResources&quot;,
        &quot;cloudformation:DescribeStacks&quot;,
        &quot;cloudformation:DescribeStackEvents&quot;,
        &quot;cloudformation:DescribeStackResources&quot;,
        &quot;cloudformation:GetTemplate&quot;,
        &quot;cloudfront:Get*&quot;,
        &quot;cloudfront:List*&quot;,
        &quot;cloudtrail:DescribeTrails&quot;,
        &quot;cloudtrail:GetEventSelectors&quot;,
        &quot;cloudtrail:ListTags&quot;,
        &quot;cloudwatch:Describe*&quot;,
        &quot;cloudwatch:Get*&quot;,
        &quot;cloudwatch:List*&quot;,
        &quot;config:Get*&quot;,
        &quot;config:Describe*&quot;,
        &quot;config:Deliver*&quot;,
        &quot;config:List*&quot;,
        &quot;cur:Describe*&quot;,
        &quot;dms:Describe*&quot;,
        &quot;dms:List*&quot;,
        &quot;dynamodb:DescribeTable&quot;,
        &quot;dynamodb:List*&quot;,
        &quot;ec2:Describe*&quot;,
        &quot;ec2:GetReservedInstancesExchangeQuote&quot;,
        &quot;ecs:List*&quot;,
        &quot;ecs:Describe*&quot;,
        &quot;elasticache:Describe*&quot;,
        &quot;elasticache:ListTagsForResource&quot;,
        &quot;elasticbeanstalk:Check*&quot;,
        &quot;elasticbeanstalk:Describe*&quot;,
        &quot;elasticbeanstalk:List*&quot;,
        &quot;elasticbeanstalk:RequestEnvironmentInfo&quot;,
        &quot;elasticbeanstalk:RetrieveEnvironmentInfo&quot;,
        &quot;elasticfilesystem:Describe*&quot;,
        &quot;elasticloadbalancing:Describe*&quot;,
        &quot;elasticmapreduce:Describe*&quot;,
        &quot;elasticmapreduce:List*&quot;,
        &quot;es:List*&quot;,
        &quot;es:Describe*&quot;,
        &quot;firehose:ListDeliveryStreams&quot;,
        &quot;firehose:DescribeDeliveryStream&quot;,
        &quot;iam:List*&quot;,
        &quot;iam:Get*&quot;,
        &quot;iam:GenerateCredentialReport&quot;,
        &quot;kinesis:Describe*&quot;,
        &quot;kinesis:List*&quot;,
        &quot;kms:DescribeKey&quot;,
        &quot;kms:GetKeyRotationStatus&quot;,
        &quot;kms:ListKeys&quot;,
        &quot;lambda:List*&quot;,
        &quot;logs:Describe*&quot;,
        &quot;organizations:ListAccounts&quot;,
        &quot;organizations:ListTagsForResource&quot;,
        &quot;redshift:Describe*&quot;,
        &quot;route53:Get*&quot;,
        &quot;route53:List*&quot;,
        &quot;rds:Describe*&quot;,
        &quot;rds:ListTagsForResource&quot;,
        &quot;s3:GetBucketAcl&quot;,
        &quot;s3:GetBucketLocation&quot;,
        &quot;s3:GetBucketLogging&quot;,
        &quot;s3:GetBucketPolicy&quot;,
        &quot;s3:GetBucketPolicyStatus&quot;,
        &quot;s3:GetBucketTagging&quot;,
        &quot;s3:GetBucketVersioning&quot;,
        &quot;s3:GetBucketWebsite&quot;,
        &quot;s3:List*&quot;,
        &quot;sagemaker:Describe*&quot;,
        &quot;sagemaker:List*&quot;,
        &quot;savingsplans:DescribeSavingsPlans&quot;,
        &quot;sdb:GetAttributes&quot;,
        &quot;sdb:List*&quot;,
        &quot;ses:Get*&quot;,
        &quot;ses:List*&quot;,
        &quot;sns:Get*&quot;,
        &quot;sns:List*&quot;,
        &quot;sqs:GetQueueAttributes&quot;,
        &quot;sqs:ListQueues&quot;,
        &quot;storagegateway:List*&quot;,
        &quot;storagegateway:Describe*&quot;,
        &quot;workspaces:Describe*&quot;
      ],
      &quot;Resource&quot;: &quot;*&quot;
    }
  ]
}
  " id="myPolicy">
    <button onclick="myFunction()">Copy</button>

    <script>
      function myFunction() {
          var copyText = document.getElementById("myPolicy");
            copyText.select();
            document.execCommand("copy");
      }
    </script>
    <script>
      const baseSwitcherUrl = "https://console.aws.amazon.com/iam/home#/roles$new?step=review&roleType=crossAccount&isThirdParty&accountID=454464851268";
      const prefixExternalId = "&externalID=";
      const prefixPolicyArn = "&policies=";
      const prefixRoleName = "&roleName=CloudHealth_"

      $(function () {
        $('#button').click(afterSearchClicked);
      })

      function afterSearchClicked() {
        var externalId = $('#externalIdInput').val();
        var accountName = $('#accountNameInput').val();
        var policyArn = $('#policyArnInput').val();
        window.open(baseSwitcherUrl + prefixExternalId + externalId + prefixPolicyArn + policyArn + prefixRoleName + accountName, "_blank");
      }
    </script>

    <br>

    <p>3) Paste into the JSON tab on this <a href="https://console.aws.amazon.com/iam/home#/policies$new?step=edit" target="_blank">page</a>.</p>

    <p>4) Click the <b>Review policy</b> & name it <b>CloudHealth</b>.</p>

    <p>5) Click the <b>Create policy</b> button & click the newly created policy.<p>

    <p>6) Copy & paste the <b>Policy ARN</b> & <b>Account Name</b> into the fields below.</p>

        <div id="policyArn">
          <input type="text" id="policyArnInput" placeholder="Paste Policy ARN" reqired>
        </div>

        <div id="accountName">
          <input type="text" id="accountNameInput" placeholder="Paste Account Name">
        </div>
    <p>7) In CloudHealth, click the edit icon next to the account you're configuring & paste the <b>External ID</b> below:</p>
    <div id="externalId">
          <input type="text" id="externalIdInput" placeholder="Paste External ID" required>
        </div>

        <div id="button">
          <button type="button">Create Role
          </button>
      </div>
    <p>8) Click the newly created role & copy/paste into the CloudHealth account under <b>Authentication Type: Role: Role ARN</b>.</p>
    </div>




    <style>
        #externalId {
  padding:7px;
  font-size: 14px;
  font-family: Metropolis,"Avenir Next","Helvetica Neue",Arial,sans-serif;
}

#externalIdInput {
  font-size: 14px;
  font-family: Metropolis,"Avenir Next","Helvetica Neue",Arial,sans-serif;
}

#accountName {
  padding:7px;
  font-size: 14px;
  font-family: Metropolis,"Avenir Next","Helvetica Neue",Arial,sans-serif;
}

#accountNameInput {
  font-size: 14px;
  font-family: Metropolis,"Avenir Next","Helvetica Neue",Arial,sans-serif;
}

#policyArn {
  padding:7px;
  font-size: 14px;
  font-family: Metropolis,"Avenir Next","Helvetica Neue",Arial,sans-serif;
}

#policyArnInput {
  font-size: 14px;
  font-family: Metropolis,"Avenir Next","Helvetica Neue",Arial,sans-serif;
}

#json {
  font-size: 14px;
  font-family: Metropolis,"Avenir Next","Helvetica Neue",Arial,sans-serif;
}

#margin {
  margin-left: 20px;
}

h1 {
  font-family: Metropolis,"Avenir Next","Helvetica Neue",Arial,sans-serif;
  font-size: 32px;
}

h2 {
  font-family: Metropolis,"Avenir Next","Helvetica Neue",Arial,sans-serif;
  font-size: 21.6px;
  color: 0079B8;
}

p {
  font-family: Metropolis,"Avenir Next","Helvetica Neue",Arial,sans-serif;
  font-size: 14px;
  color: 565656;
}

a {
  font-family: Metropolis,"Avenir Next","Helvetica Neue",Arial,sans-serif;
  font-size: 14px;
  color: 0079B8;  
}
</style>

  </body>
</html>
