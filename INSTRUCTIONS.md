# Terraform Module - DNS Updater

The first version of this module is just capable of creating a fixed set of DNS entries against a DNS Server as per RFC-2845 by using the official [DNS Terraform provider](https://registry.terraform.io/providers/hashicorp/dns/latest).

In order to create records more dynamically, you have been tasked with the enhancement of ensuring the module can read an arbitrary number of JSON files from disk at the `input-json` directory from where Terraform runs in order to update the DNS server accordingly. As we are still prototyping the solution, we are only going to support `A` DNS Record types.

```
# JSON File structure

├── examples
│   └── exercise
│       ├── input-json
│       │   ├── subdomain-a.json
│       │   └── subdomain-b.json

## JSON File Name --> DNS Record Name
## JSON File Object --> Attributes of a DNS Record
```

The examples folder contains a [basic example](./examples/basic) to get you started, however you are supposed to provide another working example under the `exercise` folder. So, consider updating, creating, or deleting any file you consider relevant within this repository.

## Way of working

You should exclusively work under a xNIX-like Operating System (e.g. Linux). Moreover, apart from the expected dev. tools that you should already have installed on your local environment (e.g. git) you'd need a recent version of:

- Bash
- Docker
- Terraform

1- Fork this repository to your own `GitHub` profile and start getting familiar with all inner folders and files.
2- After cloning the repo to your local dev. machine, run the shell command available under `tests`  (`tests/build-and-run.sh`) so you mock out a local DNS service based on `BIND9` that will let you test the Terraform module
3- Make sure you can successfully run `terraform` commands under the basic example, and it works whenever you execute terraform `init` `plan` and `apply` commands.
3- Collect information from the DNS Terraform provider, and find out how you would consume all the JSON files under `examples/exercise/input-json`
4- Bear in mind that this initial prototype must work with any number of JSON files that are dropped under `examples/exercise/input-json` and should ignore any other non-json file extensions.

Once you finish, make sure you `commit` and `push` all the content you have been working on as well as share the URL publicly via a GitHub URL with your recruiter.

## Checklist

 - [ ] Add comments to the Terraform module in the header section of [main.tf](./main.tf) that explains what the module does, and how to use it.
 - [ ] Create an automated README file (markdown style) based on [terraform-docs](https://github.com/terraform-docs/terraform-docs)
 - [ ] Create dynamically all DNS A-type records defined as JSON under `input-json` in the mock DNS server spun up via Docker.

## Optional Checklist

 - [ ] Add further Terraform functionality to support other types of DNS records defined in JSON format, following the same folder structure (e.g. CNAME)

## Reference material

[DNS Provider Official Docs](https://registry.terraform.io/providers/hashicorp/dns/latest/docs)
[DNS Provider GitHub Page](https://github.com/hashicorp/terraform-provider-dns/)