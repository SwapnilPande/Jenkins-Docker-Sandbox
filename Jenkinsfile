//import java.io.File
//abcs = getData()

// {
//                 stage("Branch A") {
//                     agent any
//                     steps {
//                         echo "Hi, I'm branch A"
//                     }
//                 }

//                 stage("Branch B") {
//                     agent any
//                     steps {
//                         echo "Hi, I'm branch B"
//                     }
//                 }

//                 stage("Branch C") {
//                     agent any
//                     steps {
//                         echo "Hi, I'm branch C"
//                     }
//                 }
//             }



// Our initial list of strings we want to echo in parallel
def stringsToEcho = ["a", "b", "c", "d"]

// The map we'll store the parallel steps in before executing them.
def stepsForParallel = stringsToEcho.collectEntries {
    ["echoing ${it}" : transformIntoStep(it)]
}


pipeline {
    agent any
    stages {
        stage('build') {
            parallel stepsForParallel 
        }
    }
}


// Actually run the steps in parallel - parallel takes a map as an argument,
// hence the above.


// Take the string and echo it.
def transformIntoStep(inputString) {
    // We need to wrap what we return in a Groovy closure, or else it's invoked
    // when this method is called, not when we pass it to parallel.
    // To do this, you need to wrap the code below in { }, and either return
    // that explicitly, or use { -> } syntax.
    return {
        node {
            echo inputString
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