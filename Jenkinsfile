node {
    def app

    stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace */

        checkout scm
    }

    stage('Build File') {
        
        
        echo "Continuing with deployment"
        echo '1234" > a.txt'
      
    }

    stage('Test File') {
        /* Ideally, we would run a test framework against our image.
         * For this example, we're using a Volkswagen-type approach ;-) */

        sh 'file a.txt'
    }

    stage('Push File') {
        /* Finally, we'll push the image with two tags:
         * First, the incremental build number from Jenkins
         * Second, the 'latest' tag.
         * Pushing multiple tags is cheap, as all the layers are reused. */
            sh 'git add a.txt'
            sh 'git commit -m "Updated file"'
            sh 'git push'
        
    }
}