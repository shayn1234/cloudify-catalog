# EKS Service Provisioning

## General

The blueprint creates EKS service based on the terraform hashicorp [example](https://github.com/hashicorp/learn-terraform-provision-eks-cluster).

## Requirements

In order to run successfully the blueprint you'll need AWS access key id and AWS secret access key. The credentials to the AWS should have permission to describe, update, delete and create EKS and VPC services.

## Secrets

The blueprint uses secrets to connect to cloud, you need to connfigure them prior running the blueprint.


| Name                  | Description                                                                        |
| --------------------- | ---------------------------------------------------------------------------------- |
| aws_access_key_id     | AWS Access Key ID                                                                  |
| aws_aceess_secret_key | AWS Access Secret Key                                                              |

## Plugins

cloudify-terraform-plugin

## Inputs

| Display Label                            | Name                | Type   | Default Value |
| ---------------------------------------- | ------------------- | ------ | ------------- |
| The resource prefix for resources naming | resource_prefix     | string | ''            |
| AWS region name                          | region_name         | string | us-west-1     |

If the user provides empty value of default the prefix will be gerenated automatically.


## Node Types

### Prefix
The node type is responsible to create a Prefix for the purpose of naming resources.\
The type is `eaas.nodes.UniquePrefixGenerator`.

For more details on the type can be found in the [link](https://github.com/cloudify-community/eaas-example/blob/master/utils/custom_types.yaml)

### Terraform
The node type is responsible for configuration the host for terraform.\
The type is `cloudify.nodes.terraform`.

### Terraform Module
The node type responsible for deploying the terraform code.\
Derived type is `cloudify.nodes.terraform.Module`

## Labels

The created deployment will have label `obj-type` equal to `service`