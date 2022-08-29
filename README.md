# Automation to deploy WAR.

## This is Ansible automation to deploy Web Archives(WAR) on tomcat servers.

### This playbook does the following steps to deploy the war files.

    1. It checks for the tomcat URL code 200 from the ansible node.
    2. If the code is 200 which is a healthy code it displays a messege.
    3. Then it stops the tomcat service.
    4. Before deploying the new WAR file it takes a backup of the old war files to specified location.
    5. After the backup of old WAR file it removes the old WAR file and Deployed old WAR folder and displays ls status to confirm.
    6. Then it Downloads the New WAR file from a remote location to specified location that we need to place to which ansible engine has access to fetch.
    7. After that it sets file permissions and ownership to New WAR file and trigger tomcat service to start.
    8. Play will wait for 20 sec has the tomcat is deploying new WAR file.
    9. Then the play resumes and to confirm it lists the directory.
    10. After that a new play will run from the ansible node to verify the deployment is complete and displays a custom messege.

### After this we will ask IP and Cert team to verify basic changes and do spot checks

