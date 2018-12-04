abcs = ['a', 'b', 'c']


pipeline {
    agent any
    stages {
        stage('build') {
            steps {
               echo_all(abcs)
            }
        }
    }
}

def echo_all(list) {
    list.each { item ->
        echo "Hello ${item}"
    }
}