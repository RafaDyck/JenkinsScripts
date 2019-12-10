#Jenkins Pipeline Scripts
Group of specialized jenkins pipeline scripts

## JenkinsfileGenerateReleaseNotes
This script updates JIRA tickets' details to organize release notes. It compares two git branches, extracts JIRA keys from commit messages, and updates the Fix Version value and comments on each ticket with version and branch information.

Useful to organize a version before release by comparing release candidate branch with production branch.

### Dependecies
- Jenkins plugin: [jira-ext](https://wiki.jenkins.io/display/JENKINS/Jira-Ext+Plugin)
- JIRA Keys to be included in commit messages. [Smart Commits](https://confluence.atlassian.com/fisheye/using-smart-commits-960155400.html)
- JIRA Instance
- Repository on git
- Multibranch Pipeline Jenkins Job

### Usage
- Add file to repository
- Create Multibranch Pipeline Job in Jenkins
- Provide path to JenkinsfileGenerateReleaseNotes

### Notes
- Script has a reference to JIRA custom field to display branch.
  - customfield_00000
- Replace jiraBaseUrl references with actual JIRA base URL.

## JenkinsfileUpdateTicketsOnBuild
This script can be used as part of existing Jenkins Pipeline jobs to update JIRA tickets' details. It uses the Jenkins Change Log during a build to extract JIRA keys from commits, updates the JIRA tickets by updating custom fields to display Branch deploy, Environment deployed to, and adds a comment.

### Dependecies
- Jenkins plugin: [jira-ext](https://wiki.jenkins.io/display/JENKINS/Jira-Ext+Plugin)
- JIRA Keys to be included in commit messages. [Smart Commits](https://confluence.atlassian.com/fisheye/using-smart-commits-960155400.html)
- JIRA Instance
- Repository on git
- Multibranch Pipeline Jenkins Job

### Usage
- Add the stage('JIRA') section and getJiraTicketsFromCommits() function to your existing pipeline script

### Notes
- Script has a reference to JIRA custom field to display branch.
  - customfield_00000
- Replace jiraBaseUrl references with actual JIRA base URL.