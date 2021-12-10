## Applications
* total number of apps 25 (apps code names:app1 - app25)
  - 10 Non container apps
    - 4 Java with Jenkins CI (app1-4)
    - 3 php with Jenkins CI (app5-7)
    - 3 .NET with Drone CI (app8-10)
  - 15 container apps
    - 6 with Gitlab CI (app 11-16)
    - 9 with AWS CI/CD (app 17-25)
## initial setups
  - two jenkins server on-prem VMs one primary , second as secondary backup (do backups wkly)   call them as ` jenkins1, jenkins2 `
      - install plugins slack,maven,nexus,maven,ansible,terraform
  - setup nexus on-prem VM, integrate it with jenkins server
  - take a on-prem jump server for non-prod environments
      - install vagrant
          - prepare vagrant files for all apps QA,UAT,LT environments
            - ubuntu VM's for all VMS except .NET apps
            - windows VM's for .NET apps
      - install ansible on jump server , maintain inventary maintain QA,UAT,LT environments
  - setup drone CI,integrate with nexus
  - setup zobbix on on-prem VM for monitoring 
  - 
## let setup for app1-4 ( java based non containerised )
### APP1
 - CI implementaion
   - get app git repo
   - setup jenkins job 
        - link git repo --> triger --> bild with maven --> save artifacts in nexus
   - check artifact in nexus repo
 - Non prod Deployment on-prem
    - QA
      - setup environment using vagrant file
      - create a play book to config and deploy (ubuntu,java,tomcat,monitoring agents)
      - config and deploy using ansible-playbook
    - SIT
      - follow similar steps as QA
    - LT
      - follow similar steps as QA
  - production deployment on aws
    - manual deployment
    - prepare terraform template for aws infrastructure
    - test terraform template with QUALI sandbox environment
    - create production infra using terraform template 
    - create ansible playbook for configuring and deployoing 
    - deploy using ansible
### APP2-APP4
  - similar steps as app1
## let setup for app5-7 ( php based non containerised)
  - similar steps as java applications
## let setup for app8-10 ( .NET based non containerised)
 - CI implementaion
   - get app git repo
   - setup droneCI job 
        - link git repo --> triger --> bild  --> save artifacts in nexus
   - check artifact in nexus repo
 - Non prod Deployment on-prem
    - QA
      - setup environment using vagrant file
      - create a play book to config and deploy (include monitoring agents)
      - config and deploy using ansible-playbook
    - SIT
      - follow similar steps as QA
    - LT
      - follow similar steps as QA
  - production deployment on aws
    - manual deployment
    - prepare terraform template for aws infrastructure
    - test terraform template with QUALI sandbox environment
    - create production infra using terraform template 
    - create ansible playbook for configuring and deployoing 
    - deploy using ansible
