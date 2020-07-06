pipeline{
    agent any
    tools {
  maven 'Maven'
}

   /* stages{
        stage('Git cloning'){
            steps{
                git credentialsId: 'github', url: 'https://github.com/chandana-devops/demowebapp'
            }
        }*/
        stage('Maven packaging'){
            steps{
                sh 'mvn clean package'
        }
    }
    stage('Deployment to Tomcat'){
        steps{
            sshagent(['sshagent']) {
    sh "ssh -o StrictHostKeyChecking=no ec2-user@13.233.162.51 /opt/tomcat8/bin/shutdown.sh"
    sh "ssh ec2-user@13.233.162.51 rm -rf /opt/tomcat8/webapps/springmvc*"
    sh "scp target/springmvc.war ec2-user@13.233.162.51:/opt/tomcat8/webapps"
    sh "ssh ec2-user@13.233.162.51 /opt/tomcat8/bin/startup.sh"
    
}

        }
    }
}
}
