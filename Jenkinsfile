node {
    def app

    stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace */

        checkout scm
    }

    stage('Build File') {
        
        
        echo "Continuing with deployment"
        sh "echo version := 1.0.${env.BUILD_ID} >> a.txt"
      
    }

    stage('Test File') {
        /* Ideally, we would run a test framework against our image.
         * For this example, we're using a Volkswagen-type approach ;-) */

        sh 'file a.txt'
    }

    post { 
        success { 
            sh 'git config --global push.default matching'
            sh 'git add a.txt'
            sh 'git commit -m "Updated file"'
            sh 'git push'
        }
    }
    
}