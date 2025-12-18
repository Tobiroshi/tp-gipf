
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
                sh "./gradlew -Dhttp.proxyHost=proxy1-rech.uphf.fr -Dhttp.proxyPort=3128 sonar -Dsonar.projectKey=tpControle -Dsonar.projectName='TpControle' -Dsonar.host.url=http://localhost:9000 -Dsonar.token=sqp_75275040e983dd68e46e3a28c0ccc4390ba19895"
            }
        }


        
      
    }
}
        
       
