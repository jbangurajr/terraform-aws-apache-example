Terraform Module to providion an EC2 Instance that is running Apache

Not intended for production use. Just showcasing how to create a custom module on Terraform Registry.

```hcl
terraform {

}

provider "aws" {
  profile = "default"
  region  = "us-east-1"
}

module "apache" {
  source          = ".//terraform-aws-apache-example"
  vpc_id          = "vpc-0000000000-example"
  my_ip_with_cidr = "YOUR_OWN_IP_ADDRESS/32"
  public_key      = "ssh-rsa YOUR PUBLIC KEY"
  instance_type   = "t2.micro"
  server_name     = "Apache Example Server"
}

output "public_ip" {
  value = module.apache.public_ip
}
```


git init
git add .
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:jbangurajr/terraform-aws-apache-example.git
git push -f origin main