import java.io.File
abcs = getData()


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
        sh 'cat test.py'
    }
}

def getData() {
    def file = new File('sampleList')
    return file.readLines()
}