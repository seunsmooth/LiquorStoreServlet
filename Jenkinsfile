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

         stage ('compile and test code') {
             steps  {
                 sh 'mvn clean install'
             }
         }
         stage ('deploy code to App Server') {
             when {
                branch 'develop'
             }
             steps  {
                 when {
                    ' branch is develop'
                 }
                 echo  'deployed'
<<<<<<< HEAD
                 sh ' tmp/belgium2.pem || true && chmod 400  /tmp/belgium2.pem'
                 sh 'scp -i  /tmp/belgium2.pem -o StrictHostKeyChecking=no codebase/target/SampleServlet.war  ec2-user@10.0.0.146:/var/lib/tomcat/webapps'
=======
                 sh ' cp /tmp/belgium2.pem || true && chmod 400  /tmp/belgium2.pem'
                 sh 'scp -i  /tmp/belgium2.pem -o StrictHostKeyChecking=no codebase/target/SampleServlet.war  ec2-user@10.0.0.146:/opt/tomcat/webapps'
>>>>>>> c28d98655bf92f919faece19fc41bade62c9db58
             }
        }
        stage ('Test code env  on App Server') {
            when { 
                branch 'develop'
            }
             steps  {
                 sh 'sleep 5000' 
                 sh 'curl  http://ec2-54-229-11-97.eu-west-1.compute.amazonaws.com/app1 | grep Landing'
                 echo  'code tested'
             }
        }
        //do some app test to make sure it work and then deploy to prod
        stage ('deploy to stage complete') {
             steps  {
                 echo  'complete'
            }
        }
    }
}
