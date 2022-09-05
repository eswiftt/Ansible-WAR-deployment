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

      test_url: http://oel9.example.com:8080/admin/

  ## BACKUP FILES - Mention paths where we want to backup old WAR files. 
    backup_src will be the source path to war file for backup.
    backup_dest will be the destination path to store backup war file.

    1. To backup one war file
    Example.

    backup_files:
      - backup_src: /opt/tomcat/webapps/admin.war
        backup_dest: /tmp/admin.war

    2. To backup multiple war files follow this format.
    Example.

    backup_files:
      - backup_src: /opt/tomcat/webapps/admin.war
        backup_dest: /tmp/admin.war
      - backup_src: /opt/tomcat/webapps/ROOT.war
        backup_dest: /tmp/ROOT.war

  ## DELETE FILES - Mention the war files to remove
    remove_war variable deletes war files. if given in list removes multiple wars.
    
    1. To remove one war file
    Example.

    remove_wars:
      - remove_war: admin.war

    2. To remove multiple war files follow this format.
    Example.

    remove_wars:
      - remove_war: admin.war
      - remove_war: ROOT.war

  ## DELETE FOLDERS - Mention the expanded folders to remove
    remove_folder variable deletes expanded war directory. if given in list removes multiple expanded war directory.
    
    1. To remove one war file
    Example.

    remove_folders:
      - remove_folder: admin

    2. To remove multiple expanded folders follow this format.
    Example.

    remove_folders:
      - remove_folder: admin
      - remove_folder: ROOT 
    
  ## NEW FILES - Mention the source path to new war file to deploy
    war_src variable copies the new war file from the given location to war_dest variable which is tomcat location to deploy new war file.

    1. To deploy one war file
    Example.

    new_wars:
      - war_src: admin.war
        war_dest: /opt/tomcat/webapps/admin.war

    2. To deploy multiple war files follow this format.
    Example.

    new_wars:
      - war_src: admin.war
        war_dest: /opt/tomcat/webapps/admin.war
      - war_src: ROOT.war
        war_dest: /opt/tomcat/webapps/ROOT.war


Example Playbook
----------------

An example of how to use this role (for instance, with variables passed in as parameters) is always nice for use:

    - hosts: servers
      roles:
        - role: Ansible-WAR-deployment
          vars:
            test_urls:
              - test_url: http://oel9.example.com:8080/admin/
            backup_files:
              - backup_src: /opt/tomcat/webapps/admin.war
                backup_dest: /tmp/admin.war 
            remove_wars:
              - remove_war: admin.war
            remove_folders:
              - remove_folder: admin
            new_wars:
              - war_src: admin.war
                war_dest: /opt/tomcat/webapps/admin.war
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
