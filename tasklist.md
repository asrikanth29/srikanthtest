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
      - install ansible on jump server , maintain inventary maintain QA,UAT,LT environments
  - setup drone CI,integrate with nexus
  - 
## let setup for app1-4 ( java based non containerised )
   ### APP1
      - get app git repo
      - setup jun
