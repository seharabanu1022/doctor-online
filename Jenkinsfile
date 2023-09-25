pipeline{
    agent any
    stages{
        stage("git checkout"){
            steps{
                git branch: 'main', credentialsId: 'tomcat-dev', url: 'https://github.com/seharabanu1022/doctor-online'
            }
        }
        stage("maven build"){
            steps{
                sh "mvn clean package"
            }
        }
        stage("sshagent"){
            steps{
                sshagent(['ssh-agent']) {
                    //copy WAR FILE TO TOMCAT
                    sh "scp -o StrictHostKeyChecking=no target/doctor-online.war ec2-user@54.81.141.14:/opt/tomcat9/webapps"
                    //stop tomcat
                    sh "ssh ec2-user@107.20.31.195 /opt/tomcat9/bin/shutdown.sh"
                    //start tomcat
                    sh "ssh ec2-user@107.20.31.195 /opt/tomcat9/bin/startup.sh"
}
            }
        }
    }
}
