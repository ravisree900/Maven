node
{
    stage('continuosDownload') 
   {
    git 'https://github.com/intelliqittrainings/maven.git'
    }
    stage('continuosBuild') 
    {
     sh 'mvn package'
    }
     stage('continuosDeployment') 
    {
     deploy adapters: [tomcat9(credentialsId: '78aff9f7-ec4b-41e4-abaf-7b0e4a7acd9c', path: '', url: 'http://172.31.0.169:8080')], contextPath: 'testapp', war: '**/*.war'
    }
     stage('continuosTesting') 
    {
     git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
     sh '''java -jar /var/lib/jenkins/workspace/scriptedpipeline/testing.jar'''
    }
    stage('continuosDelivery') 
    {
     input message: 'need approval from DM', submitter: 'sreenivasa'
     deploy adapters: [tomcat9(credentialsId: '78aff9f7-ec4b-41e4-abaf-7b0e4a7acd9c', path: '', url: 'http://172.31.4.168:8080')], contextPath: 'prodapp', war: '**/*.war'
    }
}

