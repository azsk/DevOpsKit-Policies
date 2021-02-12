# DevOps Kit (AzSK) Control Mapping To BuiltIn Azure Policy

This page lists the built-in Azure Policies equivalent to the DevOps Kit (AzSK) controls. In some cases, the implementation of the policy differs from the control evaluation logic in AzSK. Such cases are marked as Partial* and Full** in the table below.

| Control Id | Control Description | Azure Policy | Azure Policy Coverage |
|------------|---------------------|--------------|-----------------------|
|Azure_AppService_DP_Dont_Allow_HTTP_Access_Fn|	Function App must only be accessible over HTTPS|	Function App should only be accessible over HTTPS|	Full|
|Azure_AppService_DP_Dont_Allow_HTTP_Access|	App Service must only be accessible over HTTPS|	Web Application should only be accessible over HTTPS; <br/>API App should only be accessible over HTTPS|	Full|
|Azure_AppService_Config_Disable_Remote_Debugging|	Remote debugging must be turned off for App Service|	Remote debugging should be turned off for API Apps; <br/>Remote debugging should be turned off for Web Applications; <br/>Remote debugging should be turned off for Function Apps|	Full|
|Azure_AppService_Audit_Enable_Logging_and_Monitoring|	Auditing and Monitoring must be enabled for App Service|	Diagnostic logs in App Services should be enabled|	Full|
|Azure_AppService_DP_Restrict_CORS_Access|	Ensure that CORS access is granted to a limited set of trusted origins.|	CORS should not allow every resource to access your Function Apps|	Full|
|Azure_AppService_AuthN_Use_Managed_Service_Identity|	Use Managed Service Identity (MSI) for accessing other AAD-protected resources from the app service.|	Managed identity should be used in your API App; <br/>Managed identity should be used in your Web App; Managed identity should be used in your Function App|	Full|
|Azure_Automation_DP_Use_Encrypted_Variables|	Encryption of Automation account variable assets must be enabled when storing sensitive data|	Automation account variables should be encrypted|	Full|
|Azure_Batch_Audit_Enable_Metric_Alert|	Metric alert rules must be configured on Batch account|	Metric alert rules should be configured on Batch accounts|	Partial*|
|Azure_Batch_Audit_Enable_Diagnostics_Log|	Diagnostics logs must be enabled with a retention period of at least 365 days|	Diagnostic logs in Batch accounts should be enabled|	Full|
|Azure_DataLakeAnalytics_Audit_Enable_Diagnostics_Log|	Diagnostics logs must be enabled with a retention period of at least 365 days.|	Diagnostic logs in Data Lake Analytics should be enabled|	Full|
|Azure_DataLakeStore_Audit_Enable_Diagnostics_Log|	Diagnostics logs must be enabled with a retention period of at least 365 days.|	Diagnostic logs in Azure Data Lake Store should be enabled|	Full|
|Azure_EventHub_AuthZ_Use_Min_Permissions_Access_Policies|	Access policies must be defined with minimum required permissions to the Event Hub|	Authorization rules on the Event Hub instance should be defined|	Partial*|
|Azure_EventHub_Audit_Enable_Diagnostics_Log|	Diagnostics logs must be enabled with a retention period of at least 365 days|	Diagnostic logs in Event Hub should be enabled|	Full|
|Azure_EventHub_AuthZ_Dont_Use_Policies_At_Event_Hub_Namespace|	Event Hub clients (event senders or receivers) must not use 'namespace' level access policies|	All authorization rules except RootManageSharedAccessKey should be removed from Event Hub namespace|	Full|
|Azure_KeyVault_Audit_Enable_Diagnostics_Log|	Diagnostics logs must be enabled with a retention period of at least 365 days.|	Diagnostic logs in Key Vault should be enabled|	Full|
|Azure_KubernetesService_Deploy_Enable_Cluster_RBAC|	Cluster RBAC must be enabled in Kubernetes Service|	[Preview]: Role-Based Access Control (RBAC) should be used on Kubernetes Services|	Full|
|Azure_KubernetesService_NetSec_Dont_Open_Management_Ports|	Do not leave management ports open on Kubernetes nodes unless required|	[Preview]: Authorized IP ranges should be defined on Kubernetes Services; <br/>Ensure services listen only on allowed ports in Kubernetes cluster|	Partial*|
|Azure_KubernetesService_Deploy_Use_Latest_Version|	The latest version of Kubernetes should be used|	Kubernetes Services should be upgraded to a non-vulnerable Kubernetes version|	Full**|
|Azure_LogicApps_Audit_Enable_Diagnostics_Log|	Diagnostics logs must be enabled with a retention period of at least 365 days.|	Diagnostic logs in Logic Apps should be enabled|	Full|
|Azure_RedisCache_DP_Use_SSL_Port|	Non-SSL port must not be enabled|	Only secure connections to your Azure Cache for Redis should be enabled|	Full|
|Azure_Search_Audit_Enable_Diagnostics_Log|	Diagnostics logs must be enabled with a retention period of at least 365 days|	Diagnostic logs in Search services should be enabled|	Full|
|Azure_ServiceBus_AuthZ_Dont_Use_Policies_At_SB_Namespace|	Service bus clients (senders/receivers) must not use 'namespace' level access policies|	All authorization rules except RootManageSharedAccessKey should be removed from Service Bus namespace|	Full|
|Azure_ServiceBus_Audit_Enable_Diagnostics_Log|	Diagnostics logs must be enabled with a retention period of at least 365 days.|	Diagnostic logs in Service Bus should be enabled|	Full|
|Azure_ServiceFabric_AuthN_Client_AuthN_AAD_Only|	Client authentication must be performed only via Azure Active Directory|	Service Fabric clusters should only use Azure Active Directory for client authentication|	Full|
|Azure_ServiceFabric_DP_Set_Property_ClusterProtectionLevel|	The ClusterProtectionLevel property must be set to EncryptAndSign|	Service Fabric clusters should have the ClusterProtectionLevel property set to EncryptAndSign|	Full|
|Azure_ServiceFabric_Audit_Use_Diagnostics_Log|	Diagnostics must be enabled for Service Fabric cluster|	Diagnostic logs in Virtual Machine Scale Sets should be enabled|	Full|
|Azure_SQLDatabase_Audit_Enable_Threat_Detection_Server|	Enable SQL Server threat detection with email admins option. Do not exclude any detection types|	Advanced data security should be enabled on your SQL servers|	Partial*|
|Azure_SQLDatabase_AuthZ_Use_AAD_Admin|	Enable Azure AD admin for the SQL Database|	An Azure Active Directory administrator should be provisioned for SQL servers|	Full|
|Azure_SQLDatabase_DP_Enable_TDE|	Transparent data encryption (TDE) must be enabled|	Transparent Data Encryption on SQL databases should be enabled|	Full|
|Azure_SQLDatabase_Audit_Enable_Logging_and_Monitoring_Server|	Enable SQL Server audit with selected event types and retention period of minimum 365 days| Auditing on SQL server should be enabled;</br> SQL servers should be configured with 90 days auditing retention or higher;</br> Deploy Auditing on SQL servers|	Full|
|Azure_Storage_AuthN_Dont_Allow_Anonymous|	The Access Type for containers must not be set to 'Anonymous'|	[Preview]: Storage account public access should be disallowed|	Full|
|Azure_Storage_DP_Encrypt_In_Transit|	HTTPS protocol must be used for accessing Storage Account resources|	Secure transfer to storage accounts should be enabled|	Full|
|Azure_StreamAnalytics_Audit_Enable_Diagnostics_Log|	Diagnostics logs must be enabled with a retention period of at least 365 days.|	Diagnostic logs in Azure Stream Analytics should be enabled|	Full|
|Azure_Subscription_AuthZ_Remove_Deprecated_Accounts|	Deprecated/stale accounts must not be present on the subscription|	Deprecated accounts should be removed from your subscription|	Full|
|Azure_Subscription_SI_Classic_Resources|	Do not use any classic resources on a subscription|	Storage accounts should be migrated to new Azure Resource Manager resources; <br/>Virtual machines should be migrated to new Azure Resource Manager resources|	Partial*|
|Azure_Subscription_SI_Dont_Use_Classic_VMs|	Do not use any classic virtual machines on your subscription.|	Virtual machines should be migrated to new Azure Resource Manager resources|	Full|
|Azure_Subscription_AuthZ_Dont_Use_NonAD_Identities|	Do not grant permissions to external accounts (i.e., accounts outside the native directory for the subscription)|	External accounts with owner/write/read permissions should be removed from your subscription|	Full|
|Azure_Subscription_AuthZ_Limit_Admin_Owner_Count|	Minimize the number of admins/owners|	A maximum of 3 owners should be designated for your subscription|	Full**|
|Azure_Subscription_AuthZ_Custom_RBAC_Roles|	Do not use custom-defined RBAC roles|	Audit usage of custom RBAC rules|	Full|
|Azure_Subscription_Config_ASC_Tier|	Standard tier must be enabled for Azure Security Center|	Security Center standard pricing tier should be selected|	Full|
|Azure_Subscription_Config_Add_Required_Tags|	Mandatory tags must be set per your organization policy|	Require a tag and its value on resource groups|	Full|
|Azure_VirtualMachine_NetSec_Dont_Open_Management_Ports|	Do not leave management ports open on Virtual Machines|	Management ports should be closed on your virtual machines; <br/> RDP access from the Internet should be blocked; <br/>SSH access from the Internet should be blocked|	Full**|
|Azure_VirtualMachine_DP_Enable_Disk_Encryption|	Disk encryption must be enabled on both OS and data disks for Windows Virtual Machine|	Disk encryption should be applied on virtual machines|	Full|
|Azure_VirtualMachine_NetSec_Justify_PublicIPs|	Public IPs on a Virtual Machine should be carefully reviewed|	Network interfaces should not have public IPs|	Full|
|Azure_VirtualMachine_SI_Enable_Antimalware|	Antimalware must be enabled with real time protection on Virtual Machine| Monitor missing Endpoint Protection in Azure Security Center (Audit policy); <br/>Deploy default Microsoft IaaSAntimalware extension for Windows Server (DeployIfNotExist policy); <br/>Microsoft Antimalware for Azure should be configured to automatically update protection signatures (Audit policy)|Partial*|
|Azure_VirtualMachine_SI_Missing_OS_Patches|	Virtual Machine must have all the required OS patches installed.|	System updates should be installed on your machines|	Full|
|Azure_VirtualMachine_SI_ASC_OS_Vulnerabilities|	Virtual Machine must be in a healthy state in Azure Security Center|	Vulnerabilities in security configuration on your machines should be remediated|	Full|
|Azure_VirtualMachine_SI_Enable_Vuln_Solution|	Vulnerability assessment solution should be installed on VM|	A vulnerability assessment solution should be enabled on your virtual machines|	Full|
|Azure_VirtualMachine_Config_Enable_NSG|	NSG must be configured for Virtual Machine|	Internet-facing virtual machines should be protected with network security groups|	Full**|
|Azure_VNet_NetSec_Configure_NSG|	NSG should be used for subnets in a virtual network to permit traffic only on required inbound/outbound ports. NSGs should not have a rule to allow any-to-any traffic|	Subnets should be associated with a Network Security Group|	Full|
|Azure_APIManagement_NetSec_Configure_Virtual_Network_For_APIM|	Consider hosting APIM within a virtual network for improved isolation|	API Management services should use a virtual network|	Full|
|Azure_AppService_AuthN_Use_AAD_for_Client_AuthN;<br/>Azure_AppService_AuthN_Redirect_To_Login_Page|	App Service must authenticate users using Azure Active Directory backed credentials/App Service must be set to redirect unauthenticated requests to login page|	Authentication should be enabled on your API app|	Full|
|Azure_AppService_DP_Use_Secure_TLS_Version|	Use approved version of TLS for the App Service|	Latest TLS version should be used in your API App; <br/>Latest TLS version should be used in your Function App; <br/>Latest TLS version should be used in your Web App|	Full|
|Azure_RedisCache_NetSec_Configure_Virtual_Network_For_Domain_App|	Redis Cache instance should be confined within a virtual network for domain-joined scenarios|	Azure Cache for Redis should reside within a virtual network|	Full**|
|Azure_VirtualMachineScaleSet_Audit_Enable_Diagnostics|	Diagnostics (IaaSDiagnostics extension on Windows; LinuxDiagnostic extension on Linux) must be enabled on Virtual Machine Scale Set|	Diagnostic logs in Virtual Machine Scale Sets should be enabled|	Full|
|Azure_VirtualMachineScaleSet_SI_Enable_Auto_OS_Upgrade|	Enable automatic OS image upgrade on Virtual Machine Scale Set|	Require automatic OS image patching on Virtual Machine Scale Sets|	Full|
|Azure_CosmosDB_AuthZ_Enable_Firewall|	Cosmos DB firewall should be enabled|	Azure Cosmos DB accounts should have firewall rules|	Full|
|Azure_DataLakeStore_DP_Encrypt_At_Rest|	Sensitive data must be encrypted at rest|	Require encryption on Data Lake Store accounts|	Full|
|Azure_HDInsight_DP_Storage_Encrypt_At_Rest|	Storage used for cluster must have encryption at rest enabled|	Azure HDInsight clusters should use encryption at host to encrypt data at rest|	Full**|
|Azure_HDInsight_DP_Storage_Encrypt_In_Transit|	Secure transfer protocol must be used for accessing storage account resources|	Azure HDInsight clusters should use encryption in transit to encrypt communication between Azure HDInsight cluster nodes|	Full**|
|Azure_KeyVault_DP_Keys_Secrets_Check_Expiry_Date|	All Keys and Secrets in Key Vault must have expiration dates|	[Preview]: Key Vault keys should have an expiration date; <br/> [Preview]: Key Vault secrets should have an expiration date|	Full|
|Azure_KeyVault_SI_Enable_SoftDelete|	Soft delete must be enabled to allow recovery of deleted Key Vault and any objects (keys, secrets, etc.) contained in it.|	Key vaults should have soft delete enabled|	Full|
|Azure_KeyVault_DP_Keys_Protect_By_HSM|	All Keys in Key Vault must be protected by HSM [Key Type = HSM Protected Key]|	Keys should be backed by a hardware security module (HSM)|	Full|
|Azure_KubernetesService_SI_Dont_Use_Default_Namespace|	Do not use the default cluster namespace to deploy applications|	Kubernetes clusters should not use the default namespace|	Full**|
|Azure_VNet_NetSec_Dont_Use_NSGs_on_GatewaySubnet|	There must not be any NSGs on the gateway subnet of a virtual network|	Gateway subnets should not be configured with a network security group|	Full|
|Azure_VNet_NetSec_Justify_IPForwarding_for_NICs|	Use of IP Forwarding on any NIC in a virtual network should be scrutinized|	Network interfaces should disable IP forwarding|	Full|
|Azure_VNet_NetSec_Justify_PublicIPs|	Minimize the number of Public IPs (i.e. NICs with PublicIP) on a virtual network|	Network interfaces should not have public IPs|	Full|
|Azure_Search_Audit_Enable_Diagnostics_Log|	Diagnostics logs must be enabled with a retention period of at least 365 days|	Diagnostic logs in Search services should be enabled|	Full|
|Azure_Subscription_Config_ASC_Setup_SecurityContacts|	Security contact details must be configured in Azure Security Center|	Email notification for high severity alerts should be enabled; <br/>Email notification to subscription owner for high severity alerts should be enabled; <br/>Subscriptions should have a contact email address for security issues;|	Full|

<br/>
<br/>


> #### <b> NOTE: The following tables explain the differences between AzSK control and corresponding Azure Policy where the coverage is marked as "Partial*" or "Full**" </b>
>   <br/>
>  
> 1. <b> Partial* </b>  represents Azure Policy that covers the AzSK control evaluation logic partially. Please see reasons below:
>
>       | Control Id | Evaluation criteria  which are not included in Azure policy |
>       |------------|-----------------------------------------------------------|
>       |Azure_Batch_Audit_Enable_Metric_Alert| While AzSK makes sanity check on conditions of the alert, Azure Policy only checks for the presence of the alert.|
>       |Azure_EventHub_AuthZ_Use_Min_Permissions_Access_Policies| While Azure Policy checks for the presence of authorization rule, AzSK also enforces that authorization rule with full permission must not be present.|
>       |Azure_KubernetesService_NetSec_Dont_Open_Management_Ports| While Azure Policy enforces services to listen only on allowed ports in a Kubernetes cluster, AzSK also enforces that Network Security Group (NSG) should be configured.|
>       |Azure_SQLDatabase_Audit_Enable_Threat_Detection_Server| While Azure Policy enforces that Azure Threat Protection (ATP) is enabled, AzSK also makes sanity check on the ATP configurations such as email notification is configured and all ATP types are selected.|
>       |Azure_Subscription_SI_Classic_Resources| While Azure Policy only checks for classic Storage Account and Virtual Machine, AzSK checks for all type of classic resources.|
>       |Azure_VirtualMachine_SI_Enable_Antimalware| While Azure Policy enforces that Anti-Malware extension is present and Realtime protection is enabled, AzSK also enforces that Auto upgrade to minor version is enabled.|
>   
>     <br/>
>     <br/>
>
>   2. <b> Full** </b> represents Azure Policy where policy evaluation is different than that of corresponding AzSK control. Please see reasons below:
>       
>       | Control Id | Difference in evaluation criteria in AzSK and Azure policy  |
>       |------------|-----------------------------------------------------|
>       |Azure_KubernetesService_Deploy_Use_Latest_Version| While AzSK enforces that the Azure Kubernets Service (AKS) version should be the maximum minor version which are '1.14.8, 1.15.10, 1.16.7', Azure Policy enforces AKS version should be 1.11.9+, 1.12.7+, 1.13.5+, and 1.14.0+ |
>       |Azure_Subscription_AuthZ_Limit_Admin_Owner_Count| This control is evaluated via ASC. The exact evaluation details are internal to ASC.|
>       |Azure_VirtualMachine_NetSec_Dont_Open_Management_Ports| This control is evaluated via ASC. (VM agent must report correctly to ASC.) The exact evaluation details are internal to ASC.|
>       |Azure_VirtualMachine_Config_Enable_NSG| This control is evaluated via ASC. (VM agent must report correctly to ASC.) The exact evaluation details are internal to ASC.|
>       |Azure_RedisCache_NetSec_Configure_Virtual_Network_For_Domain_App| Not automated in AzSK.|
>       |Azure_HDInsight_DP_Storage_Encrypt_At_Rest| Not automated in AzSK.|
>       |Azure_HDInsight_DP_Storage_Encrypt_In_Transit| Not automated in AzSK.|
>       |Azure_KubernetesService_SI_Dont_Use_Default_Namespace| Not automated in AzSK.|



