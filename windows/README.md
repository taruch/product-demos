# Windows Demos

## Table of Contents
- [Windows Demos](#windows-demos)
  - [Table of Contents](#table-of-contents)
  - [About These Demos](#about-these-demos)
    - [Jobs](#jobs)
  - [Suggested Usage](#suggested-usage)

## About These Demos
This category of demos shows examples of Windows Server operations and management with Ansible Automation Platform. The list of demos can be found below. See the [Suggested Usage](#suggested-usage) section of this document for recommendations on how to best use these demos.

### Jobs

- [**WINDOWS / Install IIS**](install_iis.yml) - Install IIS feature with a configurable index.html
- [**WINDOWS / Patching**](patching.yml) - Apply Windows updates by category and create report
- [**WINDOWS / Chocolatey install multiple**](windows_choco_multiple.yml) - Install multiple packages using Chocolatey and check versions
- [**WINDOWS / Chocolatey install specific**](windows_choco_specific.yml) - Install a single given package using Chocolatey
- [**WINDOWS / Arbitrary Powershell**](arbitrary_powershell.yml) - Run given Powershell script (default: retrieve cat fact from API)
- [**WINDOWS / Powershell Script**](powershell_script.yml) - Run a Powershell script stored in source control to query services
- [**WINDOWS / Powershell DSC configuring password requirements**](powershell_dsc.yml) - Configure password complexity with Powershell desired state config
- [**WINDOWS / Create Active Directory Domain**](create_ad_domain.yml) - Create a new AD Domain
- [**WINDOWS / Helpdesk new user portal**](helpdesk_new_user_portal.yml) - Create user in AD Domain
- [**WINDOWS / Join Active Directory Domain**](join_ad_domain.yml) - Join computer to AD Domain

## Suggested Usage

For ANY of these to work you will need to be able to connect to the Windows hosts.  Ensure that the below variables have been added
to the variables section of the `os_windows` group in the `Demo Inventory`. Be aware that if you delete all of the Windows hosts in AWS, that the group will go away, and so will the variables.\
--- \
ansible_connection: winrm \
ansible_port: 5986 \
ansible_winrm_server_cert_validation: ignore \
ansible_winrm_transport: credssp

**WINDOWS / Patching** - To successfully run the Patching template and produce a report, you will also need to build out a host called win1. Ideally using the cloud templates in AWS because this will enable you to show off another set of templates, but also use the `aws` inventory source in the `Demo Inventory`.

**WINDOWS / Create Active Directory Domain** - This job can take some to complete. It is recommended to run ahead of time if you would like to demo creating a helpdesk user.

**WINDOWS / Helpdesk new user portal** - This job is dependant on the Create Active Directory Domain completing before users can be created.

**WINDOWS / Join Active Directory Domain** - This job is dependant on the Create Active Directory Domain completing before computers can be joined.

