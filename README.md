ansible-role-gitlab
=====================

Ansible Role to Install gitlab from source on apache and mysql

Currently only supports RHEL/CentOS.

## Requirements

None.

## Role Variables

      gitlab_shell_version: "v1.9.6"
      gitlab_branch: "7-2-stable"
      gitlab_repo: https://github.com/gitlabhq/gitlabhq.git
      gitlab_user: git
      gitlab_host: gitlab.localhost
      gitlab_https: "false"
      gitlab_init_script: https://raw.github.com/gitlabhq/gitlab-recipes/master/init/sysvinit/centos/gitlab-unicorn
      gitlab_SSL_subject: /C=US/ST=yourstate/L=yourcity/O=yourorganization
    
      gitlab_mysql_db:
       - name: gitlabhq_production
         replicate: no
    
      gitlab_mysql_user:
       - name: git
         privs: "gitlabhq_production.*:ALL"
    
      gitlab_db_host: "localhost"

## Dependencies

 role: epel-repo
 role: redis
 role: git
 role: ruby
 role: apache
 role: mysql

## Example Playbook

    - hosts: servers
      roles:
        - { role: gitlab }

## License

MIT / BSD

## Author Information

This role was created in 2014 by Solomon S. Gifford (sgifford@blackmesh.com) and sponsored by BlackMesh, Inc.

Credit: Inspired by https://github.com/akishin/ansible-playbooks
