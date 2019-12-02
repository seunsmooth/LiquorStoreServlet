781depipeline {
    agent any

    stages {
         stage ('Checking Deploy tool and initial cleanup') {
             steps {
                 sh '''
                 mvn --version
                 java -version
                 git --version
                 kubctl version --client=true
                 '''
          }
         }

         stage ('build code ') {
             steps {
               sh '''
               echo 'building code'
               mvn clean build
               '''
        }
       }
     }
}
