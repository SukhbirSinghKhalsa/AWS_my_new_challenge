# AWS to Azure Service Mapping

## Compute

| AWS Service | Azure Equivalent | Key difference |
|---|---|---|
| EC2 | Azure Virtual Machines | Azure VM sizes follow a different naming convention (Standard_D4s_v5 etc.). |
| EC2 Auto Scaling | Azure VM Scale Sets (VMSS) | VMSS supports both uniform and flexible orchestration modes. |
| AWS Lambda | Azure Functions | Azure Functions has Durable Functions for stateful workflows — no Lambda equivalent. |
| ECS (Fargate) | Azure Container Instances (ACI) | ACI is simpler; for orchestration use AKS. |
| EKS | Azure Kubernetes Service (AKS) | AKS has tighter Azure AD integration; node pool autoscaling works similarly. |
| Elastic Beanstalk | Azure App Service | App Service is more mature with deployment slots for blue/green deploys. |

## Storage

| AWS Service | Azure Equivalent | Key difference |
|---|---|---|
| S3 | Azure Blob Storage | Azure has Hot/Cool/Archive tiers; S3 has Standard/IA/Glacier. |
| EBS | Azure Managed Disks | Azure has Ultra Disk for high IOPS workloads — often cheaper than io2. |
| EFS | Azure Files / Azure NetApp Files | Azure Files SMB/NFS; NetApp for high-performance NAS workloads. |
| S3 Glacier | Azure Archive Storage | Similar pricing; Azure retrieval times vary by priority tier. |
| Storage Gateway | Azure StorSimple / Data Box | Data Box is a physical appliance for bulk data transfer. |

## Database

| AWS Service | Azure Equivalent | Key difference |
|---|---|---|
| RDS (MySQL/PostgreSQL) | Azure Database for MySQL/PostgreSQL | Azure Flexible Server recommended over Single Server (deprecated). |
| RDS (SQL Server) | Azure SQL Database / SQL Managed Instance | SQL MI for near-100% SQL Server compatibility without code changes. |
| Aurora | Azure SQL Hyperscale | Hyperscale supports up to 100TB; Aurora is faster for write-heavy workloads. |
| DynamoDB | Azure Cosmos DB | Cosmos DB has multiple APIs (SQL, MongoDB, Cassandra, Gremlin, Table). |
| ElastiCache (Redis) | Azure Cache for Redis | Feature parity is close; Azure supports Redis Enterprise tier. |
| Redshift | Azure Synapse Analytics | Synapse integrates with Data Factory and Power BI out of the box. |

## Networking

| AWS Service | Azure Equivalent | Key difference |
|---|---|---|
| VPC | Azure Virtual Network (VNet) | VNet peering works similarly; Azure has VNet injection for PaaS services. |
| Route 53 | Azure DNS + Azure Traffic Manager | Traffic Manager is global load balancing; Azure DNS for zone management. |
| CloudFront | Azure CDN / Azure Front Door | Front Door adds WAF, SSL offload, and global HTTP load balancing. |
| API Gateway | Azure API Management (APIM) | APIM is more feature-rich: developer portal, policies, OAuth built-in. |
| Direct Connect | Azure ExpressRoute | ExpressRoute pricing is different — charged per circuit + data in some tiers. |
| AWS WAF | Azure Web Application Firewall | Azure WAF integrates with Front Door and Application Gateway. |

## Security & Identity

| AWS Service | Azure Equivalent | Key difference |
|---|---|---|
| IAM | Azure Active Directory (Entra ID) + RBAC | BIGGEST difference — Azure identity model is fundamentally different from AWS IAM. |
| AWS KMS | Azure Key Vault | Key Vault also stores secrets and certificates — no separate Secrets Manager needed. |
| Secrets Manager | Azure Key Vault Secrets | Key Vault handles both keys and secrets in one service. |
| AWS Shield | Azure DDoS Protection | Azure Standard tier auto-protects VNets; DDoS Protection Plan for advanced protection. |
| Security Hub | Microsoft Defender for Cloud | Defender covers multi-cloud including AWS workloads. |
| CloudTrail | Azure Monitor + Activity Log | Activity Log captures control-plane events; Diagnostic Settings for data-plane. |

## DevOps & Monitoring

| AWS Service | Azure Equivalent | Key difference |
|---|---|---|
| CodePipeline / CodeBuild | Azure DevOps Pipelines | Azure DevOps is more integrated; GitHub Actions also works natively with Azure. |
| CloudFormation | Azure Resource Manager (ARM) / Bicep | Bicep is cleaner syntax than ARM JSON; Terraform works on both. |
| CloudWatch | Azure Monitor + Log Analytics | Log Analytics uses KQL (Kusto Query Language) — different from CloudWatch Insights. |
| X-Ray | Azure Application Insights | App Insights has richer APM features including dependency mapping. |
| SNS / SQS | Azure Service Bus + Event Grid | Service Bus for queues/topics; Event Grid for event-driven routing. |
| Kinesis | Azure Event Hubs | Event Hubs is Kafka-compatible — useful if you already use Kafka clients. |
