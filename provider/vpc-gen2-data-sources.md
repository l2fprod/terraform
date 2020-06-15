---

copyright:
  years: 2017, 2020
lastupdated: "2020-06-15"

keywords: terraform provider plugin, terraform vpc gen 2, terraform vpc, gen 2 compute terraform, terraform vpc subnet

subcollection: terraform

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:download: .download}
{:preview: .preview}
{:external: target="_blank" .external}

# VPC infrastructure data sources (Gen 2 compute) 
{: #vpc-gen2-data-sources}

Before you start working with your data source, make sure to review the [required parameters](/docs/terraform?topic=terraform-provider-reference#required-parameters) that you need to specify in the `provider` block of your Terraform configuration file. 
{: important}



## `ibm_is_image`
{: #vpc-image}

Retrieve information about a virtual server image for Gen 2 compute. 
{: shortdesc}

### Sample Terraform code
{: #vpc-image-sample}

The following example retrieves information about the `centos-7.x-amd64` image. 
{: shortdesc}

```

data "ibm_is_image" "ds_image" {
    name = "centos-7.x-amd64"
}

```

### Input parameters
{: #vpc-image-input}

Review the input parameters that you can specify for your data source. 
{: shortdesc}

|Name|Data type| Required/ optional|Description|
|----|-----------|--------|----------------------|
|`name`|String|Required|The name of the image.|
|`visibility`|String|Optional|The visibility of the image. Accepted values are `public` or `private`.|
{: caption="Table. Available input parameters" caption-side="top"}

### Output parameters
{: #vpc-image-output}

Review the output parameters that you can access after you retrieved your data source. 
{: shortdesc}

|Name|Data type|Description|
|----|-----------|-------------|
|`id`|String|The unique identifier for this image.|
|`crn`|String|The CRN for this image.|
|`os`|String|The name of the operating system.|
|`status`|String|The status of this image.|
|`architecture`|String|The architecture for this image.|
{: caption="Table 1. Available output parameters" caption-side="top"}

## `ibm_is_images`
{: #vpc-images}

Retrieve information about Gen 2 virtual server images. 
{: shortdesc}

### Sample Terraform code
{: #vpc-images-sample}

```

data "ibm_is_images" "ds_images" {
}

```

### Input parameters
{ #vpc-images-input}

No input parameters are required for this data source.
{: shortdesc}

### Output parameters
{ #vpc-images-output}

Review the output parameters that you can access after you retrieved your data source. 
{: shortdesc}

|Name|Data type|Description|
|----|-----------|-------------|
|`images`|List of objects|List of all supported images.  |
|`images.name`|String|The name for this image.  |
|`images.id`|String|The unique identifier for this image.  |
|`images.crn`|String|The CRN for this image.  |
|`images.os`|String|The name of the operating system.  |
|`images.status`|String|The status of this image.  |
|`images.architecture`|String|The architecture for this image.  |
|`images.visibility`|String|The visibility of the image public or private.|
{: caption="Table 1. Available output parameters" caption-side="top"}


## `ibm_is_instance_profile`
{: #vpc-instance-profile}

Retrieve information about a virtual server instance profile. 
{: shortdesc}

### Sample Terraform code
{: #vpc-instance-profile-sample}

The following example retrieves information about the `bx2-2x8` instance profile. 
{: shortdesc}

```

data "ibm_is_instance_profile" "profile" {
	name = "bx2-2x8"
}

```

### Input parameters
{: #vpc-instance-profile-input}

Review the input parameters that you can specify for your data source. 
{: shortdesc}

|Name|Data type| Required/ optional|Description|
|----|-----------|--------|----------------------|
|`name`|String|Required|The name for this virtual server instance profile.|
{: caption="Table. Available input parameters" caption-side="top"}

### Output parameters
{: #vpc-instance-profile-output}

Review the output parameters that you can access after you retrieved your data source. 
{: shortdesc}

|Name|Data type|Description|
|----|-----------|-------------|
|`family`|String|The family of the virtual server instance profile.|
{: caption="Table 1. Available output parameters" caption-side="top"}


## `ibm_is_instance_profiles`
{: #vpc-instance-profiles}

Retrieve information about supported virtual server instance profiles. 
{: shortdesc}

### Sample Terraform code
{: #vpc-instance-profiles-sample}

```

data "ibm_is_instance_profiles" "ds_instance_profiles" {
}

```


### Input parameters
{: #vpc-instance-profiles-input}

No input parameters are required for this data source.
{: shortdesc}

### Output parameters
{: #vpc-instance-profiles-output}

Review the output parameters that you can access after you retrieved your data source. 
{: shortdesc}

|Name|Data type|Description|
|----|-----------|-------------|
|`profiles`|List of objects|List of all server instance profiles in the region.  |
|`profiles.name`|String|The name for this virtual server instance profile.  |
|`profiles.family`|String|The family of the virtual server instance profile.|
{: caption="Table 1. Available output parameters" caption-side="top"}


## `ibm_is_region`
{: #vpc-region}

Retrieve information about a VPC Gen 2 Compute region. 
{: shortdesc}

### Sample Terraform code
{: #vpc-region-sample}

```

data "ibm_is_region" "ds_region" {
    name = "us-south"
}

```

### Input parameters
{: #vpc-region-input}

Review the input parameters that you can specify for your data source. 
{: shortdesc}

|Name|Data type| Required/ optional|Description|
|----|-----------|--------|----------------------|
|`name`|String|Required|The name of the region.|
{: caption="Table. Available input parameters" caption-side="top"}

### Output parameters
{: #vpc-region-output}

Review the output parameters that you can access after you retrieved your data source. 
{: shortdesc}

|Name|Data type|Description|
|----|-----------|-------------|
|`status`|String|The status of the region.|
|`endpoint`|String|The endpoint of the region.|
{: caption="Table 1. Available output parameters" caption-side="top"}



## `ibm_is_ssh_key`
{: #vpc-ssh-key}

Retrieve information about a VPC Gen 2 SSH key. 
{: shortdesc}

### Sample Terraform code
{: #vpc-ssh-key-sample}

```

data "ibm_is_ssh_key" "ds_key" {
    name = "test"
}

```

### Input parameters
{: #vpc-ssh-key-input}

Review the input parameters that you can specify for your data source. 
{: shortdesc}

|Name|Data type| Required/ optional|Description|
|----|-----------|--------|----------------------|
|`name`|String|Required|The name of the SSH key.|
{: caption="Table. Available input parameters" caption-side="top"}

### Output parameters
{: #vpc-ssh-key-output}

Review the output parameters that you can access after you retrieved your data source. 
{: shortdesc}

|Name|Data type|Description|
|----|-----------|-------------|
|`id`|String|The id of the SSH key.|
|`fingerprint`| String| The SHA256 fingerprint of the public key.|
|`length`|String|The length of the SSH key.|
|`type`|String|The cryptosystem that is used by this key.|
|`resource_controller_url`|String|The URL of the IBM Cloud dashboard that can be used to explore and view details about this instance.|
{: caption="Table 1. Available output parameters" caption-side="top"}


## `ibm_is_subnet`
{: #vpc-subnet}

Retrieve information about a VPC Gen 2 compute subnet. 
{: shortdesc}

### Sample Terraform code
{: #vpc-subnet-sample}

```
resource "ibm_is_vpc" "testacc_vpc" {
	name = "test"
}

resource "ibm_is_subnet" "testacc_subnet" {
	name = "test_subnet"
	vpc = ibm_is_vpc.testacc_vpc.id
	zone = "us-south-1"
	ipv4_cidr_block = "192.168.0.0/1"
}
data "ibm_is_subnet" "ds_subnet" {
	identifier = ibm_is_subnet.testacc_subnet.id
}

```

### Input parameters
{: #vpc-subnet-input}

Review the input parameters that you can specify for your data source. 
{: shortdesc}

|Name|Data type| Required/ optional|Description|
|----|-----------|--------|----------------------|
|`identifier`|String|Required|The ID of the subnet.|
{: caption="Table. Available input parameters" caption-side="top"}

### Output parameters
{: #vpc-subnet-output}

Review the output parameters that you can access after you retrieved your data source. 
{: shortdesc}

|Name|Data type|Description|
|----|-----------|-------------|
|`ipv4_cidr_block`| String|The IPv4 range of the subnet.|
|`ipv6_cidr_block`|String|The IPv6 range of the subnet.|
|`total_ipv4_address_count`|Integer|The total number of IPv4 addresses.|
|`ip_version`|String|The IP version.|
|`name`|String|The name of the subnet.|
|`network_acl`|String|The ID of the network ACL for the subnet.|
|`public_gateway`|String|The ID of the public gateway for the subnet.|
|`status`|String|The status of the subnet.|
|`vpc`|String|The ID of the VPC that the subnet belongs to.|
|`zone`|String|The subnet zone name.|
|`available_ipv4_address_count`|Integer|The total number of available IPv4 addresses.|
|`resource_controller_url`|String|The URL of the IBM Cloud dashboard that can be used to explore and view details about this instance.|
{: caption="Table 1. Available output parameters" caption-side="top"}


## `ibm_is_subnets`
{: #vpc-subnets}

Retrieve information about all existing VPC subnets in an IBM Cloud account. 
{: shortdesc}

### Sample Terraform code
{: #vpc-subnets-sample}

```
data "ibm_is_subnets" "ds_subnets" {
}
```
{: codeblock}

### Input parameters
{: #vpc-subnets-input}

This resource does not support any input parameters.

### Output parameters
{: #vpc-subnets-output}

Review the output parameters that you can access after you retrieved your data source. 
{: shortdesc}

|Name|Data type|Description|
|----|-----------|-------------|
|`subnets`|List|A list of subnets in the IBM Cloud account.|
|`subnets.name`|String|The name of the subnet.|
|`subnets.id`|String|The ID of the subnet.|
|`subnets.ipv4_cidr_block`|String|The IPv4 CIDR block of this subnet.|
|`subnets.ipv6_cidr_block`|String|The IPv6 CIDR block of this subnet.|
|`subnets.status`|String|The status of the subnet.|
|`subnets.crn`|String|The CRN of the subnet.|
|`subnets.available_ipv4_address_count`|Integer|The number of IPv4 addresses that are available in the subnet.|
|`subnets.total_ipv4_address_count`|Integer|The total number of IPv4 addresses in the subnet.|
|`subnets.network_acl`|String|The access control list (ACL) that is attached to the subnet.|
|`subnets.public_gateway`|Boolean|If set to **true**, a public gateway is attached to the subnet. If set to **false**, no public gateway for this subnet exists.|
|`subnets.resource_group`|String|The resource group that the subnet belongs to.|
|`subnets.vpc`|String|The ID of the VPC that this subnet belongs to.|
|`subnets.zone`|String|The zone where the subnet was created.|

## `ibm_is_vpc`
{: #vpc}

Retrieve information about a Gen 2 compute VPC. 
{: shortdesc}

### Sample Terraform code
{: #vpc-sample}

```
resource "ibm_is_vpc" "testacc_vpc" {
    name = "test"
}

data "ibm_is_vpc" "ds_vpc" {
    name = "test"
}

```

### Input parameters
{: #vpc-input}

Review the input parameters that you can specify for your data source. 
{: shortdesc}

|Name|Data type| Required/ optional|Description|
|----|-----------|--------|----------------------|
|`name`|String|Required|The name of the VPC.|
{: caption="Table. Available input parameters" caption-side="top"}

### Output parameters
{: #vpc-output}

Review the output parameters that you can access after you retrieved your data source. 
{: shortdesc}

|Name|Data type|Description|
|----|-----------|-------------|
|`classic_access`|Boolean|Indicates whether this VPC is connected to Classic Infrastructure.|
|`crn`|String|The CRN of the VPC.|
| `cse_source_addresses`|List of Cloud Service Endpoints|A list of the cloud service endpoints that are associated with your VPC, including their source IP address and zone.|
|`cse_source_addresses.address`|String|The IP address of the cloud service endpoint.|
|`cse_source_addresses.zone_name`|String|The zone where the cloud service endpoint is located.|
|`default_network_acl`|String| The ID of the default network ACL.|
|`resource_controller_url`|String|The URL of the IBM Cloud dashboard that can be used to explore and view details about this instance.|
|`resource_group`|String|The resource group ID where the VPC created.|
|`subnets`|List of subnets|A list of subnets that are attached to a VPC.|
|`subnets.name`|String|The name of the subnet.|
|`subnets.id`|String|The ID of the subnet.|
|`subnets.zone`|String|The zone that the subnet belongs to.|
|`subnets.status`|String|The status of the subnet.|
|`subnets.total_ipv4_address_count`|Integer|The total number of IPv4 addresses in the subnet.|
|`subnets.available_ipv4_address_count`|Integer|The number of IPv4 addresses in the subnet that are available for you to be used.|
|`status`|String|The status of the VPC.|
|`tags`|Array|Tags associated with the instance.|
{: caption="Table 1. Available output parameters" caption-side="top"}


## `ibm_is_zone`
{: #vpc-zone}

Retrieve information about a Gen 2 compute zone. 
{: shortdesc}

### Sample Terraform code
{: #vpc-zone-sample}

```

data "ibm_is_zone" "ds_zone" {
    name = "us-south-1"
    region = "us-south"
}

```

### Input parameters
{: #vpc-zone-input}

Review the input parameters that you can specify for your data source. 
{: shortdesc}

|Name|Data type| Required/ optional|Description|
|----|-----------|--------|----------------------|
|`name`|String|Required|The name of the zone.|
|`region`|String|Required| The name of the region.|
{: caption="Table. Available input parameters" caption-side="top"}

### Output parameters
{: #vpc-zone-output}

Review the output parameters that you can access after you retrieved your data source. 
{: shortdesc}

|Name|Data type|Description|
|----|-----------|-------------|
|`status`|String|The status of the zone.|
{: caption="Table 1. Available output parameters" caption-side="top"}



## `ibm_is_zones`
{: #vpc-zones}

Retrieves information about Gen 2 compute zones. 
{: shortdesc}

### Sample Terraform code
{: #vpc-zones-sample}

```

data "ibm_is_zones" "ds_zones" {
    region = "us-south"
}

```

### Input parameters
{: #vpc-zones-input}

Review the input parameters that you can specify for your data source. 
{: shortdesc}

|Name|Data type| Required/ optional|Description|
|----|-----------|--------|----------------------|
|`region`|String|Required|The name of the region.|
|`status`|String|Optional|Filter the list by status of zones.|
{: caption="Table. Available input parameters" caption-side="top"}

### Output parameters
{: #vpc-zones-output}

Review the output parameters that you can access after you retrieved your data source. 
{: shortdesc}

|Name|Data type|Description|
|----|-----------|-------------|
|`zones`|String|The list of zones in a region.|
{: caption="Table 1. Available output parameters" caption-side="top"}
