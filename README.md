# Example playbook for proxy server provisioning.
Example proxy server has squid service for proxy and postfix email relay

## Squid Configuration.
The *templates/squid_template.j2* is a template file for squid config. It uses variables stored in the *vars/squid_vars.yml* file. To make changes to allowed websites or acls just edit variables file. To make more complex changes look to the template file. *squid_passwd* file stores credentials for proxy authentication. On clean installation you need to manually perform command *httpasswd -c /etc/squid/squid_passwd yourproxyuser* to generate password hash for proxy user.

## Postfix Configuration
The *templates/main.cf* file is the main config for postfix. It is not templated, just edit it. *templates/hosts_template.j2* template populate **/etc/hosts** file with allowed email clients. It is needed for dns resolution. *templates/postfix_access_template.j2* populate **/etc/postfix/access** with allowed email clients. Clients stored in *vars/postfix_vars.yml*. Edit this file to add or remove allowed clients.