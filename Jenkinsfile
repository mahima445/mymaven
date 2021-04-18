node('master') 
{
    stage('ContinuousDownload_master')
    {
        git 'https://github.com/intelliqittrainings/maven.git'             
    }
    stage('ContinuousBuild_master') 
    {
        sh 'mvn package'
    }
    stage('ContinuousDeployment_master')
    {
     sh 'scp /home/ubuntu/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war ubuntu@172.31.39.40:/var/lib/tomcat9/webapps/testapp.war'
    }
    stage('ContinuousTesting_master')
    {
        git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
        sh 'java -jar /home/ubuntu/.jenkins/workspace/ScriptedPipeline/testing.jar'
    }
    stage('ContinuousDelivery_master')
    {
    
    sh 'scp /home/ubuntu/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war ubuntu@172.31.32.24:/var/lib/tomcat9/webapps/prodapp.war'
    }
}

