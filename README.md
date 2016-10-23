h1 Google Cloud DNS Module for Terraform

This module may be used to manage Google Cloud DNS zones and resource records.

Example `dns.tf` file (create a module for every dns zone you want to manage).

```
provider "google" {
  credentials = "${file("creadentials.json")"
  project     = "PROJECT_ID"
  region      = "europe-west"
}

module "example.com" {
  source      = "github.com/JoergFiedler/terraform-google-cloud-dns-zone"
  name        = "example"
  dns_zone    = "example.com."
  ip_address  = "10.0.1.10"
  rrecord {
    "type"    = "MX"
    "rrdata"  = "1 mx.example.com,2 mx.example.com"
  }
  rrecord {
    "name"    = "sftp"
    "type"    = "A"
    "rrdata"  = "10.0.2.100"
  }
}
```
