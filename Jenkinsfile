pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        git branch: 'main', url: 'https://github.com/YOUR_GITHUB_USERNAME/secure-cicd-demo.git'
      }
    }

    stage('Build') {
      steps {
        sh 'mvn -B clean package -DskipTests'
      }
    }

    stage('Deploy to Tomcat') {
      steps {
        sshagent(['tomcat-ssh']) {
          sh 'scp target/secure-cicd.war ubuntu@STAGING_SERVER_IP:/opt/tomcat/webapps/'
        }
      }
    }
  }
}
