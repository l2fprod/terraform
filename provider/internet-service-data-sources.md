---

copyright:
  years: 2017, 2020
lastupdated: "2020-03-31"

keywords: terraform internet services, terraform cis, terraform provider plugin

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

# Internet Services data sources
{: #cis_data}

You can reference the output parameters for each resource in other resources or data sources by using [Terraform interpolation syntax](https://www.terraform.io/docs/configuration-0-11/interpolation.html){: external}. 

Before you start working with your data source, make sure to review the [required parameters](/docs/terraform?topic=terraform-provider-reference#required-parameters) that you need to specify in the `provider` block of your Terraform configuration file. 
{: important}


## `ibm_cis`
{: #cis}

Retrieve information about an existing {{site.data.keyword.cis_full_notm}} instance. 
{: shortdesc}

### Sample Terraform code
{: #cis-sample}

The following example retrieves information about an {{site.data.keyword.cis_full_notm}} instance. 
{: shortdesc}

```
data "ibm_cis" "cis_instance" {
  name              = "myinstance"
}
```

### Input parameters
{: #cis-input}

Review the input parameters that you can specify for your data source. 
{: shortdesc}

|Name|Data type|Required/optional|Description|
|----|-----------|------|--------|
| `name` | String | Required | The name of your {{site.data.keyword.cis_full_notm}} instance. |

### Output parameters
{: #cis-output}

Review the output parameters that you can access after you retrieved your data source. 
{: shortdesc}

|Name|Data type|Description|
|----|-----------|----------|
| `id` | String | The CRN of your instance. |
| `guid` | String| The unique identifier of the instance.|
| `plan` | String | The service plan for the instance. |
| `location` | String | The location of your instance. |
| `status` | String | The status of your instance. |

## `ibm_cis_domain`
{: #cis_domain}

Retrieve information about an {{site.data.keyword.cis_full_notm}} domain. 
{: shortdesc}

### Sample Terraform code
{: #cis-domain-sample}

The following example retrieves information about an {{site.data.keyword.cis_full_notm}} domain. 
{: shortdesc}

```
data "ibm_cis_domain" "cis_instance_domain" {
  domain = "mydomain.com"
  cis_id = ibm_cis.instance.id
}

data "ibm_cis" "cis_instance" {
  name = "myinstance"
}
```

### Input parameters
{: #cis-domain-input}

Review the input parameters that you can specify for your data source. 
{: shortdesc}

|Name|Data type|Required/optional|Description|
|----|-----------|------|--------|
| `domain` | String | Required | The DNS domain name that is added and managed for your {{site.data.keyword.cis_full_notm}} instance. |
| `cis_id` | String | Required | The ID of the {{site.data.keyword.cis_full_notm}} instance. |

### Output parameters
{: #cis-domain-output}

Review the output parameters that you can access after you retrieved your data source. 
{: shortdesc}

|Name|Data type|Description|
|----|-----------|----------|
| `id` | String | The unique identifier of your domain. |
| `paused` | Boolean | If set to **true**, network traffic to this domain is paused. If set to **false**, network traffic to this domain is permitted. The default value is **false**.  |
| `status` | String | The status of your domain. Valid values are `active`, `pending`, `initializing`, `moved`, `deleted`, and `deactivated`. After creation, the status remains pending until the DNS Registrar is updated with the CIS name servers, exported in the ‘name_servers’ variable. |
| `name_servers` | String | The IBM CIS assigned name servers, to be passed by interpolation to the resource dns_domain_registration_nameservers. |
| `original_name_servers` | String | The name servers from when the Domain was initially registered with the DNS Registrar.|

## `ibm_cis_ip_addresses`
{: #cis_ip}

Import a list of all IP addresses that the CIS proxy uses. The CIS proxy uses these IP addresses for both `client-to-proxy` and `proxy-to-origin` communication. You can reference the IP addresses by using Terraform interpolation syntax to configure and whitelist IP addresses in firewalls, network ACLs, and security groups. 
{: shortdesc}

### Sample Terraform code
{: #cis-ip-sample}

The following example retrieves information about IP addresses that {{site.data.keyword.cis_full_notm}} uses for name servers. 
{: shortdesc}

```
data "ibm_cis_ip_addresses" "cisname" {
}
```

### Input parameters
{: #cis-ip-input}

No input parameters are required for this data source. 

### Output parameters
{: #cis-ip-output}

Review the output parameters that you can access after you retrieved your data source. 
{: shortdesc}

|Name|Data type|Description|
|----|-----------|----------|
| `ipv4_cidrs` | String | The IPv4 address ranges that the CIS proxy uses and that you can reference to configure and whitelist IP addresses in firewalls, network ACLs, and security groups. |
| `ipv6_cidrs` | String | The IPv6 address ranges that the CIS proxy uses and that you can reference to configure and whitelist IP addresses in firewalls, network ACLs, and security groups.|
