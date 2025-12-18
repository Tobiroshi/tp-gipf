
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

        
      
    }
}
        
       
