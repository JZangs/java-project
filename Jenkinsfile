properties([pipelineTriggers([githubPush()])])
node('linux') {
    git url: 'https://github.com/JZangs/java-project.git', branch: 'master'
    stage('Report') {
        sh "ant -f test.xml -v"
    }
}
