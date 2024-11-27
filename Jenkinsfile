pipeline {
    agent {
        node {
            label "linux && java11"
        }
    }            // Menentukan di mana pipeline akan berjalan (any = semua node)
    
    stages {             // Blok berisi tahapan pekerjaan
        stage('Build') { // Nama tahap
            steps {      // Langkah-langkah dalam tahap ini
                echo 'Hello Pipeline job: Building...'
            }
        }

    }
}