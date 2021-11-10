# aws-nuke

This project is a configuration file for the AWS nuke library from the [rebuy-de aws nuke](https://github.com/rebuy-de/aws-nuke) project.

## Customization

Add the desired AWS account number for nuke into the portion of the configuration file. As the base documentation from rebuy-de notes, the target account must have an account alias set in the IAM dashboard.

```bash
accounts:
  <aws account number>:
    filters:****
```

Change the Route53 DNS Suffix for the Route53ResourceRecordSet entry

```bash
  Route53ResourceRecordSet:
  - property: Type
    type: contains
    value: "CNAME"
    invert: true
  - property: Name
    type: contains
    value: "<route 53 DNS suffix>"
    invert: true
```

OPTIONAL: Change the EC2InternetGateway and EC2RouteTable to identify the default Internet Gateway and Route Table 

```bash
  EC2InternetGateway:
  - "<ec2 internet gateway identifier>"
```

```bash
  EC2RouteTable:
  - property: Main
    value: "true"
  - "<ec2 route table>"
```

## Commands to use

```bash
$ aws-nuke --force --force-sleep 3 --profile <aws profile> -c <path to configuration file>
```

```bash
$ aws-nuke --force --force-sleep 3 --profile <aws profile> -c <path to configuration files> --no-dry-run
```


