# External DNS into Google Cloud Platform

![Tfsec](https://github.com/nlamirault/terraform-google-external-dns/workflows/Tfsec/badge.svg)

## Terraform versions

Use Terraform `>= 0.14.0` minimum and Terraform Provider Google `3.54+`.

These types of resources are supported:

* [google_service_account](https://www.terraform.io/docs/providers/google/r/google_service_account.html)
* [google_project_iam_binding](https://registry.terraform.io/providers/hashicorp/google/latest/docs/resources/google_project_iam)
* [google_service_account_iam_member](https://registry.terraform.io/providers/hashicorp/google/latest/docs/resources/google_service_account_iam#google_service_account_iam_member)

## Usage

```hcl
module "external_dns" {
  source  = "nlamirault/external-dns/google"
  version = "1.0.0"
  
  project = var.project

  namespace       = var.namespace
  service_account = var.service_account
}
```

and variables :

```hcl
project = "foo-prod"

region = "europe-west1"

##############################################################################
# External DNS

namespace       = "dns"
service_account = "external-dns"
```

## Documentation

### Providers

| Name | Version |
|------|---------|
| google | >= 3.54.0 |

### Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:-----:|
| namespace | The Kubernetes namespace | `string` | n/a | yes |
| project | The project in which the resource belongs | `string` | n/a | yes |
| service\_account | The Kubernetes service account | `string` | n/a | yes |

### Outputs

| Name | Description |
|------|-------------|
| service\_account | Service Account for External DNS |
