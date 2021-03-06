---
subcategory: "Network"
layout: "azurerm"
page_title: "Azure Resource Manager: azurerm_lb"
description: |-
  Get information about an existing Load Balancer

---

# Data Source: azurerm_lb

Use this data source to access information about an existing Load Balancer

## Example Usage

```hcl
data "azurerm_lb" "example" {
  name                = "example-lb"
  resource_group_name = "example-resources"
}

output "loadbalancer_id" {
  value = "${data.azurerm_lb.example.id}"
}
```

## Argument Reference

* `name` - (Required) Specifies the name of the Load Balancer.

* `resource_group_name` - (Required) The name of the Resource Group in which the Load Balancer exists.

## Attributes Reference

The following attributes are exported:

* `id` - The ID of the Load Balancer.

* `frontend_ip_configuration` - (Optional) A `frontend_ip_configuration` block as documented below.

* `location` - The Azure location where the Load Balancer exists.

* `private_ip_address` - The first private IP address assigned to the load balancer in `frontend_ip_configuration` blocks, if any.

* `private_ip_addresses` - The list of private IP address assigned to the load balancer in `frontend_ip_configuration` blocks, if any.

* `sku` - The SKU of the Load Balancer.

* `tags` - A mapping of tags assigned to the resource.

---

A `frontend_ip_configuration` block exports the following:

* `name` - The name of the Frontend IP Configuration.
* `id` - The id of the Frontend IP Configuration.
* `subnet_id` - The ID of the Subnet which is associated with the IP Configuration.
* `private_ip_address` - Private IP Address to assign to the Load Balancer.
* `private_ip_address_allocation` - The allocation method for the Private IP Address used by this Load Balancer.
* `public_ip_address_id` - The ID of a  Public IP Address which is associated with this Load Balancer.
* `zones` - A list of Availability Zones which the Load Balancer's IP Addresses should be created in.

### Timeouts

~> **Note:** Custom Timeouts are available [as an opt-in Beta in version 1.43 of the Azure Provider](/docs/providers/azurerm/guides/2.0-beta.html) and will be enabled by default in version 2.0 of the Azure Provider.

The `timeouts` block allows you to specify [timeouts](https://www.terraform.io/docs/configuration/resources.html#timeouts) for certain actions:

* `read` - (Defaults to 5 minutes) Used when retrieving the Load Balancer.
