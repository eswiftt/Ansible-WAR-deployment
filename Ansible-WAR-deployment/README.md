Ansible-WAR-deployment
=========

This role will deploy war files into tomcat servers.

Requirements
============

    Red Hat Ansible Automation Platform 1.2 and Above.
    
    Tomcat versions supported:
                              Tomcat 8
                              Tomcat 9
                              Tomcat 10
          
    Operating Systems supported:
                              OEL 7, OEL 8, OEL 9.
                              RHEL 7, OEL 8, OEL9.
                              Rocky 8, Rocky 9.

Role Variables
==============

  ## Test url status before deployment

      test_urls:
        - test_url: "{{ ansible_facts['fqdn'] }}:8080/admin/"

  ## BACKUP FILES and DELETE OLD WARS and IT'S EXPANED FOLDER - Mention paths where we want to backup old WAR files.

    backup_location is where your backedup file will be stored.

    Example.
    backup_location: /tmp/

    Files will take the backup of old files to backup_location and deletes the old file and also deletes the expanded folder.

    1. To backup and delete one war file
    Example.
    files:
      - file_name: admin

    2. To remove multiple war files follow this format.
    Example.
    files:
      - file_name: admin
      - file_name: ROOT
    
  ## NEW FILES - Mention the source path to new war file to deploy
    war_src variable copies the new war file from the given location to war_dest variable which is tomcat location to deploy new war file.

    1. To deploy one war file
    Example.

    new_wars:
      - war_src: admin.war
        war_dest: admin.war

    2. To deploy multiple war files follow this format.
    Example.

    new_wars:
      - war_src: admin.war
        war_dest: admin.war
      - war_src: ROOT.war
        war_dest: ROOT.war


Example Playbook
----------------

An example of how to use this role (for instance, with variables passed in as parameters) is always nice for use:

- hosts: servers
  remote_user: tomcat
  ignore_errors: yes
  become: yes
  roles:
    - role: Ansible-WAR-deployment
      vars:
        tomcat_location: /opt/tomcat9/webapps/
        backup_location: /tmp/
        files:
          - file_name: admin
        new_wars:
          - war_src: admin.war
            war_dest: admin.war
License
-------

BSD

Owner
------------------

Mohammed Tahmeed

Red Hat Certified Engineer

ID: MT094795

System Engineer I

CernerWorks CWx Team POE-Synergy
