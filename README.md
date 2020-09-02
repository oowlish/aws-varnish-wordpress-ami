# Varnish Wordpress - Amazon Machine Image (AMI)

This repository contains a Packer template for building a Varnish AMI for accelerating WordPress sites.

## Requirements

- [Packer](https://www.packer.io/downloads) 1.5+
- [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html) 2.0+

## How to Build

First, you need to be able to authenticate to AWS. You can learn how to do that at [Packer documentation's](https://www.packer.io/docs/builders/amazon#authentication) page.

After having authenticated to AWS, you should run the following in the root directory of this project:

```bash
$ packer build -var git_sha=$(git rev-parse --short HEAD) varnish-wordpress.json
```

### AWS Regions

[AMIs are regional resources](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/resources.html), and by default, Packer will build the AMI in the `us-east-1` region. If you want to build the AMI in another AWS region, you can pass it as a variable this way:

```bash
$ packer build -var aws_region="sa-east-1" -var git_sha=$(git rev-parse --short HEAD) varnish-wordpress.json
```
