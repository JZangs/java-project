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
        
    }
}
