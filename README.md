# Google Cloud integrations

Provides SaaS-components related to integrations (events, data streaming, ETL, ...). TODO: implement.

Example usage:

```
provider "google" {
  project      = "my-infrastructure"
  region       = "europe-west1"
  zone         = "europe-west1-b"
}

resource "google_project_service" "compute" {
  service      = "compute.googleapis.com"
}

module "integrations" {
  source       = "TaitoUnited/integrations/google"
  version      = "1.0.0"
  depends_on   = [ google_project_service.compute ]

  kafkas       = yamldecode(file("${path.root}/../infra.yaml"))["kafkas"]
}
```

Example YAML:

```
kafkas:
  - name: my-kafka
```

Combine with the following modules to get a complete infrastructure defined by YAML:

- [Admin](https://registry.terraform.io/modules/TaitoUnited/admin/google)
- [DNS](https://registry.terraform.io/modules/TaitoUnited/dns/google)
- [Network](https://registry.terraform.io/modules/TaitoUnited/network/google)
- [Compute](https://registry.terraform.io/modules/TaitoUnited/compute/google)
- [Kubernetes](https://registry.terraform.io/modules/TaitoUnited/kubernetes/google)
- [Databases](https://registry.terraform.io/modules/TaitoUnited/databases/google)
- [Storage](https://registry.terraform.io/modules/TaitoUnited/storage/google)
- [Monitoring](https://registry.terraform.io/modules/TaitoUnited/monitoring/google)
- [Integrations](https://registry.terraform.io/modules/TaitoUnited/integrations/google)
- [PostgreSQL privileges](https://registry.terraform.io/modules/TaitoUnited/privileges/postgresql)
- [MySQL privileges](https://registry.terraform.io/modules/TaitoUnited/privileges/mysql)

Similar modules are also available for AWS, Azure, and DigitalOcean. All modules are used by [infrastructure templates](https://taitounited.github.io/taito-cli/templates#infrastructure-templates) of [Taito CLI](https://taitounited.github.io/taito-cli/). TIP: See also [Google Cloud project resources](https://registry.terraform.io/modules/TaitoUnited/project-resources/google), [Full Stack Helm Chart](https://github.com/TaitoUnited/taito-charts/blob/master/full-stack), and [full-stack-template](https://github.com/TaitoUnited/full-stack-template).

Contributions are welcome!
