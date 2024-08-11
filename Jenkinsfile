def ansible = [:]
         ansible.name = 'ansible'
         ansible.host = '172.31.30.154'
         ansible.user = 'centos'
         ansible.password = 'Rnstech@123'
         ansible.allowAnyHosts = true
def kops = [:]
         kops.name = 'kops'
         kops.host = '172.31.34.51'
         kops.user = 'centos'
         kops.password = 'Rnstech@123'
         kops.allowAnyHosts = true
pipeline {
    agent any

    
    stages {
        stage('Prepare-Workspace') {
            steps {
                // Get some code from a GitHub repository
                git credentialsId: 'github-server-credentials', url: 'https://github.com/duskyguy/26th-Repository.git/'    
		stash 'Source'
            }
            
        }
            
	stage('SonarQube Scan') {
      steps {
        bat """C:/Build/apache-maven-3.9.8/bin/mvn X sonar:sonar\
             -Dsonar.projectKey=javaHelloApp \
              -Dsonar.host.url=http:localhost:9000\
             -Dsonar.login=sqa_1fab6df7f1a4c6069f537d97f42f9e24aefc99dc"""
      }
	}

		
    }
}
