import java.io.File
abcs = getData()


pipeline {
    agent any
    stages {
        stage('build') {
            parallel {
                stage("Branch A") {
                    agent any
                    steps {
                        echo "Hi, I'm branch A"
                    }
                }

                stage("Branch B") {
                    agent any
                    steps {
                        echo "Hi, I'm branch B"
                    }
                }

                stage("Branch C") {
                    agent any
                    steps {
                        echo "Hi, I'm branch C"
                    }
                }
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
    echo 'hi'
    sh 'dir'
    File file = new File("./sampleList")
    return file.readLines()
}