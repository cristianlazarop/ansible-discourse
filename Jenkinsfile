node {
    stage 'Checkout'

    checkout scm

    stage 'nameGradle Static Analysis'
    withSonarQubeEnv {
        sh "./gradlew clean sonarqube"
    }
}  
