# Server Deployment

We aim to deploy the server using the 'Bring Your Own License (BYOL)' Deployment model, where the license need to be purchased from the [OpenVPN.net] [OpenVPN.net] service, but we can also run the service without a license, with atmost 2 concurrent users at a time. 

**I would advice to buy the free license**, which is essentially a signup procedure, after which you can have 3 concurrent users. 

To launch the server,
* Go to Azure Marketplace in Azure Portal and launch OpenVPN Access Server
* Create the server instance with the default configurations, but pay attentions to
  - Ensure that the vm supports SSH authentication
  - Allocate a static IP
  - Go with default subnets.Do not change
  - Every other configurations can be set to default or altered as per your conviences, but ensure the specified ones are strictly followed.

* SSH into your newly created VM, and enter the setup. Most of the options can be set to the default, but a bit of care is required.
  - Set the node as a primary access server, if it is a personel connection.
  - Go with the default port specifications, to avoid any future hass les.
  - Enable local authentication via internal DB
  - Ensure Client Traffic be routed by default through VPN is enabled, and private subnet access by default
  - Set your Admin Entry username and password, which doubles up as the master client username and password
  - Ensure the license key is filled, if u enable one.

**NB: Hostnames can be changedby accessing the Web Admin UI and configuring the hostname parameter. A FQDN is recommended.**

* Reconfigure the Time Zone

* In your Azure Portal, ensure the IP Forwarding option is enabled. Select the Networking under the Settings of the Virtual Machine Instance. Choose effective security rules of the networking session. In the new menu, select IP configurations, and select IP configurations under settings heading.

* Update the OS, by running the 
Blockquotes
> sudo apt-get update <br>
> sudo apt-get upgrade
* You can add additional users from the web admin page
