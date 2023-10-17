# Deployment of Vagrant ubuntu cluster with lamp stack.
**Documentation**

The objective of this project is to automate the deployment of two Ubuntu virtual machines, 'Master' and 'Slave,' with an integrated LAMP (Linux, Apache, MySQL, PHP) stack. The deployment is orchestrated using Vagrant. This document provides an overview of the Vagrant project structure, usage instructions, and key provisioning details.

**Master node configuration**

The 'Master' node in the Vagrant code is set up using the "generic/ubuntu2204" base box, and a private network is created to enable communication. User management tasks include creating a user named "altschool" with root (superuser) privileges and configuring SSH key pairs for passwordless SSH access. Additionally, Ansible provisioning is applied to further configure the 'Master' node, which includes the execution of the "assignment.yaml" playbook to install and configure the LAMP stack and verify PHP functionality.

**Slave node configuration**

The 'Slave' node also utilizes the "generic/ubuntu2204" base box and establishes a private network for internal communication. User management tasks are carried out to create the "altschool" user if it doesn't already exist and configure SSH key pairs for passwordless SSH access from the 'Master.' Similar to the 'Master,' Ansible provisioning can be applied to the 'Slave' node for additional configuration based on the project's requirements.

**Ansible playbook**

Ansible playbook aims to automate the setup of a LAMP stack on the specified hosts. It ensures that the necessary components, including Apache, MySQL, and PHP, are installed and configured properly. The playbook also includes a task to create a PHP test page and verify PHP functionality.

**Task by task breakdown of playbook**

**Update apt package cache:**

This task updates the APT package cache to ensure that the package manager has the latest package information.

**Install Apache:**

It installs the Apache web server (HTTPD) on the target hosts. The task ensures that Apache is present on the system.


**Ensure Apache service is running:**

This task ensures that the Apache service is running and set to start automatically on system boot. It ensures that the web server is operational.

**Install and configure MySQL:**

This task utilizes the Ansible role geerlingguy.mysql to install and configure MySQL on the target hosts. This role provides a comprehensive MySQL setup.

**Install and verify PHP functionality**

This task encompasses the installation of PHP on the target hosts and encompasses several sub-tasks. It begins by installing the PHP package on the system, followed by restarting the Apache service to ensure PHP support is properly applied. Additionally, it creates a PHP test page using a template, a common practice to assess PHP functionality. The final sub-task involves verifying PHP functionality, achieved by making an HTTP request to the PHP test page. 
