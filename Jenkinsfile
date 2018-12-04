import java.io.File
abcs = getData()


pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                sh 'dir'
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
    File file = new File("./sampleList")
    return file.readLines()
}