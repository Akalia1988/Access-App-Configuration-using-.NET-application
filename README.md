# Access-App-Configuration-using-.NET-application

What is Azure App Configuration?
Azure App Configuration provides a service to centrally manage application settings and feature flags. Modern programs, especially programs running in a cloud, generally have many components that are distributed in nature. Spreading configuration settings across these components can lead to hard-to-troubleshoot errors during an application deployment. Use App Configuration to store all the settings for your application and secure their accesses in one place.

Why use App Configuration?
Cloud-based applications often run on multiple virtual machines or containers in multiple regions and use multiple external services. Creating a robust and scalable application in a distributed environment presents a significant challenge.

While any application can make use of App Configuration, the following examples are the types of application that benefit from the use of it:

Microservices based on Azure Kubernetes Service, Azure Service Fabric, or other containerized apps deployed in one or more geographies
Serverless apps, which include Azure Functions or other event-driven stateless compute apps
Continuous deployment pipeline

App Configuration offers the following benefits:
A fully managed service that can be set up in minutes
Flexible key representations and mappings
Tagging with labels
Point-in-time replay of settings
Dedicated UI for feature flag management
Comparison of two sets of configurations on custom-defined dimensions
Enhanced security through Azure-managed identities
Encryption of sensitive information at rest and in transit
Native integration with popular frameworks

App Configuration integration with Key Vault
Modern applications consist of secrets, keys, and configuration. Even though Azure App Configuration can keep secrets and keys, App Configuration is not designed to do this. Therefore, we need a combination of Azure App Configuration and Key Vault.

we would need to create Azure app configuration and key vault 

Create App Setting referencing Key Vault secret
we can do it via CLI
az appconfig kv set-keyvault -n TestAppConfigStore --key testmMessage --label dev --secret-identifier https://xxxxxxxx.vault.azure.net/secrets/testmessage/4cfd3d

Access App Configuration using .NET application

Create a default an ASP.Net Core Web Application and install “Azure.Identity” package make sure to install the preview version.

Install-Package Azure.Identity -Version 1.2.0-preview.4

Add the following to appsetting.json
"AppConfig": { "Endpoint": "https://{yourAppConfigurationEndpoint}.azconfig.io" }

Grant the “App Configuration Data Reader” role to your user account.

![image](https://user-images.githubusercontent.com/58148717/104049905-60c96180-51ab-11eb-939a-57c18d35fde2.png)

Next, grant access to Key Vault.

![image](https://user-images.githubusercontent.com/58148717/104050056-9a9a6800-51ab-11eb-86db-6bc4afc7da46.png)

and we are good to go!










