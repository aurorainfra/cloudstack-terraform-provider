---
layout: default
page_title: "CloudStack: cloudstack_disk_offering"
sidebar_current: "docs-cloudstack-resource-disk_offering"
description: |-
    Creates a Disk Offering
---

# CloudStack: cloudstack_disk_offering

A `cloudstack_disk_offering` resource manages a disk offering within CloudStack.

## Example Usage

```hcl
resource "cloudstack_disk_offering" "example" {
    name = "example-disk-offering"
    display_text = "Example Disk Offering"
    disk_size = 100
}
```

A customized disk offering, where the size is selected at volume-creation time:

```hcl
resource "cloudstack_disk_offering" "custom" {
    name = "example-custom-disk-offering"
    display_text = "Example Custom Disk Offering"
    custom_disk_size = true
}
```


## Argument Reference

The following arguments are supported:

* `name` - (Required) The name of the disk offering.
* `display_text` - (Required) The display text of the disk offering.
* `disk_size` - (Optional) The size of the disk offering in GB. Must be omitted when `custom_disk_size` is set. Mutually exclusive with `custom_disk_size`.
* `custom_disk_size` - (Optional) If set, the disk size is customizable and chosen at volume-creation time instead of fixed by the offering. Mutually exclusive with `disk_size`. Forces new resource.
* `encrypt` - (Optional) Whether to encrypt the disks created using this disk offering. Forces new resource.

## Attributes Reference

The following attributes are exported:

* `id` - The ID of the disk offering.
* `name` - The name of the disk offering.
* `display_text` - The display text of the disk offering.
* `disk_size` - The size of the disk offering in GB.
* `custom_disk_size` - Whether the disk size is customizable at volume-creation time.
* `encrypt` - Whether encryption is enabled for this disk offering.

## Import

Disk offerings can be imported; use `<DISKOFFERINGID>` as the import ID. For example:

```shell
$ terraform import cloudstack_disk_offering.example <DISKOFFERINGID>
```
