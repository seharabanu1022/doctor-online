pipeline{
    agent any
    stages{
        stage("maven build"){
            steps{
                sh "mvn clean package"
            }
        }
        stage("sshagent"){
            steps{
                sshagent(['ssh-agent']) {
                    //copy WAR FILE TO TOMCAT
                    sh "scp -o StrictHostKeyChecking=no target/doctor-online.war ec2-user@54.159.105.138:/opt/tomcat9/webapps"
                    //stop tomcat
                    sh "ssh ec2-user@54.159.105.138 /opt/tomcat9/bin/shutdown.sh"
                    //start tomcat
                    sh "ssh ec2-user@54.159.105.138 /opt/tomcat9/bin/startup.sh"
}
            }
        }
    }
}
