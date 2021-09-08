+++
title = "Cleanup"
chapter = true
weight = 170
+++

## Cleanup
{{% notice note %}}
If you are attending AWS Event and using one of provided AWS accounts than you can skip this section.
{{% /notice %}}

1. Delete `Lumigo-Workshop-Admin` IAM role

     ```
     aws iam detach-role-policy --role-name Lumigo-Workshop-Admin --policy-arn arn:aws:iam::aws:policy/AdministratorAccess

     aws iam delete-role --role-name Lumigo-Workshop-Admin
     ```


1. Remove Cloud9 Workstation

       ```
       aws cloud9 delete-environment --environment-id $(aws cloud9 list-environments | jq '.environmentIds[]' | xargs)
       ```

{{% notice warning %}}
This action stops the Cloud9 Workspace you are currently working on.
{{% /notice %}}
