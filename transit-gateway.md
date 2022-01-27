# AWS transit gateway
## Flat: Transit gateway route domains (route tables)
![flat](https://i.imgur.com/Y8XLiEA.png "flat")
## Isolated: Transit gateway route domains
![isolated](https://i.imgur.com/CEcF5xi.png "isolated")
![how it works](https://i.imgur.com/jdf2DKd.png)

## Reference Network Architecture
![architecure](https://i.imgur.com/4NN820q.png)

## Segmentation: decision inputs
Relationship between accounts, VPCs, and tenants?
- Do accounts and tenatns trust each other?
- Is the current network segmentation intentional or a side effect?

Who owns security and networking?
- Each team or a centralized team?

Compliance and governance trequirements?
- Scope can be reduced at an account or a VPC level
### Segmentation options: Layers
Inside the account
- IAM users and roles
- Security groups

At the VPC
- Route tables
- Network ACLs (tenant isolation within VPC) or block a centain IP address report
- Sparate VPCs


Baseline security
IAM: control actions and privileges inside the account between users and role
Security groups: Whitelist ports, protocols, and other security groups for network access.

Network security
Route tables: route table policy defines what VPC resources can access on the network
Network ACLs: Fence off access between specific subnets, ports, or destinations.
Separate VPCs: Full sparation from other tenants.

Transit Gateways
- Route tables

Security services
- Firewalls
- Proxies
- Intrustion detection/prevention
![layers](https://i.imgur.com/E8eKKFD.png)

### Some examples
![Flat](https://i.imgur.com/t7dxe5h.png "All routes and attachments are in a single route table")

Bulding a routing policy: isolated VPCs and shared services
![building a routing policy](https://i.imgur.com/Povmm8O.png "isolated vpcs and shared services")

### Segmentation considerations: where to start
Security groups and IAM are effective and proven
- Encourage IAM and security group use and monitor security configuration
Shared VPCs
- Enforce controls between tenants (security groups, NACLs) and the internet
- Peered VPCs are likely to benefit from Shared VPCs

Separate VPCs
- Often the best secrurity decision is the simplest
- Strong network segmentation and resource isolation
- Transit Gateway removes the scaling issues with many VPNCs(peering, VPN, routes)

Use transit gateway route tables to define policy for groups of VPCs.

## Serverless transit network orchestrator (STNO)
