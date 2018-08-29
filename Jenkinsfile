node {
    // Mark the code checkout 'stage'....
    stage('Checkout') {
     checkout scm
    }

    stage('Configure'){
      env.PATH = "${tool 'Maven 3'}/bin:${env.PATH}"
    }
    // Mark the code build 'stage'....
    stage('Build') {
      // Run the maven build
      sh "ls;cd java-custom-rules;ls;mvn clean;mvn compile"
    }
    stage('Test') {
        sh "ls;cd java-custom-rules;ls;mvn test -Dtest=mvn test -Dtest=AvoidAnnotationCheckTest"
    }
    
    stage('Analysis SonarQube') {
      withSonarQubeEnv('SonarQube') {
        sh "ls;cd java-custom-rules;ls;mvn sonar:sonar -Dsonar.login=admin -Dsonar.password=admin"
      }
    }

}