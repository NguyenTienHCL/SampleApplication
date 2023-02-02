pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "mvn"
    }

    stages {
        stage('Build') {
            steps {
                // Get some code from a GitHub repository
                git 'https://github.com/NguyenTienHCL/SampleApplication.git'

                // Run Maven on a Unix agent.
                sh "mvn -Dmaven.test.failure.ignore=true clean package"

                // To run Maven on a Windows agent, use
                // bat "mvn -Dmaven.test.failure.ignore=true clean package"
            }
        }
        stage ('Deploy into Tomcat server') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'fbdefcd6-0641-4d4a-a9e6-5ed369c37296', path: '', url: 'http://43.201.149.175:8090/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
