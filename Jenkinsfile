pipeline {
    agent any

    stages {
         stage ('Checking Deploy tool and initial cleanup') {
             steps {
                 sh 'mvn --version'
                 sh 'java -version'
                 sh ' git --version'
                 sh 'rm -rf codebase || true' 
             }
         }

         stage ('pull down codbase') {
             steps  {
                 sh 'git clone https://github.com/seunsmooth/LiquorStoreServlet.git codebase'

             }
         }
         stage ('compile and test code') {
             steps  {
                 sh 'cd codebase && mvn clean install'
             }
         }
         stage ('deploy code to App Server') {
             steps  {
                 echo  'deployed'
                 sh ' cp -iv /tmp/asiri.pem /tmp/belgium2.pem || true && chmod 400  /tmp/belgium2.pem'
                 sh 'scp -i  /tmp/belgium2.pem -o StrictHostKeyChecking=no codebase/target/SampleServlet.war  ec2-user@10.0.0.146:/var/lib/tomcat/webapps'
             }
        }
        stage ('Test code on App Server') {
             steps  {
                 echo  'code tested'
             }
        }
        stage ('complete') {
             steps  {
                 echo  'complete'
            }
        }
    }
}
