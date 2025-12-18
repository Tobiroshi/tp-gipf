
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
                sh "./gradlew -D https.proxyHost=proxy1-rech.uphf.fr -D http.proxyPort=3128 sonar \
                -Dsonar.projectKey=tpControle \
                -Dsonar.projectName='TpControle' \
                -Dsonar.host.url=http://172.17.0.1:9000 \
                -Dsonar.token=sqp_75275040e983dd68e46e3a28c0ccc4390ba19895"
            }

        }

        stage ("Générer artifact .jar") {
            steps {
                sh "./gradlew -D https.proxyHost=proxy1-rech.uphf.fr -D https.proxyPort=3128 jar"
            }
        }
    }
}
        
       
