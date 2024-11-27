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
    // triggers {
    //     pollSCM('*/3 * * * *')
    // }
    options {
        disableConcurrentBuilds() // mencegah build secara bersamaan
        // timeout(time: 10, unit: 'MINUTES') // akan dihentikan jika lebih dari 10 detik, (MINUTES, SECONDS)
    }
    parameters {
        // Definisi parameter di sini
        string(name: 'USERNAME', defaultValue: 'guest', description: 'Enter your username')
        booleanParam(name: 'DEPLOY', defaultValue: false, description: 'Deploy to production?')
        choice(name: 'ENVIRONMENT', choices: ['Development', 'Staging', 'Production'], description: 'Select the environment')
        text(name: 'RELEASE_NOTES', defaultValue: 'Write release notes here...', description: 'Provide release notes')
        password(name: 'ADMIN_PASS', defaultValue: 'defaultPass', description: 'Enter admin password')
    }
    stages {             // Blok berisi tahapan pekerjaan
        stage('Parameter') { 
            steps {
                echo("Param string: ${params.USERNAME}")
                echo("Param booleanParam: ${params.DEPLOY}")
                echo("Param choice: ${params.ENVIRONMENT}")
                echo("Param text: ${params.RELEASE_NOTES}")
                echo("Param password: ${params.ADMIN_PASS}")
            }
        }
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
                // echo("DB Pass ${DB_PSW}") //DB dari env diatas, _PSW wajib untuk panggil password
                sh('echo "DB Password : $DB_PSW" > "password_db.txt"')
                echo("-------------------------")
                echo("Param string: ${params.USERNAME}")
                echo("Param booleanParam: ${params.DEPLOY}")
                echo("Param choice: ${params.ENVIRONMENT}")
                echo("Param text: ${params.RELEASE_NOTES}")
                echo("Param password: ${params.ADMIN_PASS}")


            }
        }
        stage('Build') { // Nama tahap
            steps {      // Langkah-langkah dalam tahap ini
                echo 'Hello Pipeline job: Building...'
                script {
                    input message: 'Build to the next step?', ok: 'Yes, Build'
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