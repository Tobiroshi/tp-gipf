
pipeline {
    agent any
    
    stages {
        stage ("Clone le projet") {
            steps {
                git branch: 'master', url: 'https://github.com/tobiroshi/tp-gipf.git/'
            }
        }

        stage ("Compiler le projet") {
            steps {
                sh "./gradlew -D https.proxyHost=proxy1-rech.uphf.fr -D https.proxyPort=3128 compileJava"
            }
        }

         stage ("Vérif coverage  JaCoCo") {
            steps {
                sh "./gradlew -D https.proxyHost=proxy1-rech.uphf.fr -D https.proxyPort=3128 test"
            }
        }

        stage ("Scanner avec Sonar") {
            steps {
                sh "./gradlew -Dhttps.proxyHost=proxy1-rech.uphf.fr -Dhttps.proxyPort=3128 sonar -Dsonar.projectKey=TpControl -Dsonar.projectName='TpControl' -Dsonar.host.url=http://172.17.0.1:9000 -Dsonar.token=sqp_9d595f8e75657fcbd537b33fd6be6c20019a406e"
            }
        }
      
    }
}
        
       
