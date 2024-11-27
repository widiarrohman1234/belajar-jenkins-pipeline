pipeline {
    // jika agent lebih dari 1
    // agent {
    //     node {
    //         label "linux && java11"
    //     }
    // }         
    agent any   // Menentukan di mana pipeline akan berjalan (any = semua node)
    
    environment {
        AUTHOR = "Widi Arrohman"
        EMAIL = "widiarrohman1234@gmail.com"
        WEB = "https://widiarrohman.my.id"
        DB = credentials("mysql_prod")
    }

    stages {             // Blok berisi tahapan pekerjaan
        stage('Prepare') { // Nama tahap
            steps {      // Langkah-langkah dalam tahap ini
                echo("Start Job ${env.JOB_NAME}")
                echo("Start Build ${env.BUILD_NUMBER}")
                echo("Start Name ${env.BRANCH_NAME}")
                echo("-------------------------")
                echo("Author ${AUTHOR}")
                echo("Email ${EMAIL}")
                echo("Web ${WEB}")
                echo("-------------------------")
                echo("DB User ${DB_USR}") //DB dari env diatas, _USR wajib untuk panggil user
                echo("DB Pass ${DB_PSW}") //DB dari env diatas, _PSW wajib untuk panggil password
            }
        }
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