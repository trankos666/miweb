pipeline{
    agent any
    stages{
        stage('Repositorio'){
            steps{
                echo 'Soy el primer paso de la etapa 1'
                git url:'https://github.com/trankos666/miweb'
            }
        }
        stage('Empaquetado'){
            steps{
                echo 'Empaqueto mediante maven'
                sh 'mvn package'
            }
        }
        stage('Deploy'){
            steps{
                echo 'tomcat'
                deploy adapters: [tomcat9(credentialsId: 'f5a070b9-57df-40c7-90d4-c9519fc5c041', path: '', url: 'http://localhost:8082')], contextPath: 'prueba1', war: 'target/miweb.war'
            }
        }
    }
    post{
        always{
            echo 'Yo me ejecuto siempre'
        }
        success{
            echo 'Yo me ejecuto cuando todo ha ido bien'
        }
        failure{
            echo 'Yo me ejecuto cuando ha ido mal'
        }
        changed{
            echo 'Yo me ejecuto si esta ejecución no acaba en el mismo estado que la anterior ejecucion'
        }
    }
}