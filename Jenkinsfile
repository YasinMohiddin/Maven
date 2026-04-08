pipeline
{
    agent any
    stages
    {
        stage('download')
        {
            steps
            {
                git 'https://github.com/YasinMohiddin/Maven.git'
            }
        }
        stage('build')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('deployment')
        {
            steps
            {
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'dd04ea48-2b28-4901-9c60-00bfa9a33eb6', path: '', url: 'http://44.197.251.125:8080')], contextPath: 'test1', war: '**/*.war'
            }
        }
        stage('testing')
        {
            steps
            {
                git 'https://github.com/YasinMohiddin/FunctionTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/Declerativepipeline1/testing.jar'
            }
        }
        stage('delivery')
        {
            steps
            {
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'dd04ea48-2b28-4901-9c60-00bfa9a33eb6', path: '', url: 'http://44.222.92.104:8080')], contextPath: 'live', war: '**/*.war'
            }
        }
    }
}
