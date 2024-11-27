pipeline {
    // agent {
    //     node {
    //         label "linux && java11"
    //     }
    // }         
    agent any   // Menentukan di mana pipeline akan berjalan (any = semua node)
    
    stages {             // Blok berisi tahapan pekerjaan
        stage('Build') { // Nama tahap
            steps {      // Langkah-langkah dalam tahap ini
                echo 'Hello Pipeline job: Building...'
                script {
                    def data = [
                        'firstName': 'Widi',
                        'lastName': 'Arrohman',
                    ]
                    writeJSON(file: "data.json", json:data)
                }
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
                // sh("errorasdfasdfsd") // test error
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
            }
        }

    }
    post {
        always {
            echo 'Pipeline has finished running.'
        }
        success {
            echo 'Pipeline succeeded!'
        }
        failure {
            echo 'Pipeline failed! Please check the logs.'
        }
        unstable {
            echo 'Pipeline is unstable due to warnings.'
        }
        aborted {
            echo 'Pipeline was manually aborted.'
        }
    }
}