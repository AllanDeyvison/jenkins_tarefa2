pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                script {
                    docker.build("myapp:latest", "./app")
                }
            }
        }
        stage('Test') {
            steps {
                sh 'python3 -m unittest discover -s . -p "test_*.py"'
            }
        }
        stage('Deploy') {
            steps {
                echo "🚀 Deploy da aplicação"
                sh 'docker run -d -p 5000:5000 myapp:latest'
            }
        }
    }
    post {
        failure {
            echo "❌ Pipeline falhou!"
        }
        success {
            echo "✅ Pipeline finalizado com sucesso!"
        }
    }
}

// pipeline {
//     agent any
   
//     stages {
//         stage('Build') {
//             steps {
//                 echo 'Iniciando Build...'
//                 sh 'docker build -t myapp:latest ./app'
//             }
//         }
       
//         stage('Test') {
//             steps {
//                 echo 'Executando Testes...'
//                 sh '''
//                     docker run --rm myapp:latest python test_app.py
//                 '''
//             }
//         }
       
//         stage('Deploy') {
//             steps {
//                 echo 'Realizando Deploy...'
//                 sh '''
//                     docker stop myapp || true
//                     docker rm myapp || true
//                     docker run -d --name myapp -p 80:80 myapp:latest
//                 '''
//             }
//         }
//     }
   
//     post {
//         success {
//             echo '✅ Pipeline executado com sucesso!'
//         }
//         failure {
//             echo '❌ Pipeline falhou!'
//         }
//     }
// }