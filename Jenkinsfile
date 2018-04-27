properties([pipelineTriggers([githubPush()])])
node('linux') {
    git url: 'https://github.com/JZangs/java-project.git', branch: 'master'
    stage('Unit Tests') {
        sh "ant -f test.xml -v"
        junit 'reports/*.xml'
    }
    stage('Build') {
        sh "ant -f build.xml -v"
    }
    stage('Deploy') {
        sh "aws s3 cp /workspace/java-pipeline/dist/*.jar s3://jzangs-assignment10/"
    }
    stage('Report') {
        withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'Jenkins-AWS', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
        sh "aws cloudformation describe-stack-resources --region us-east-1 --stack-name jenkins"  
        }
    }
}
