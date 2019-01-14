// While you can't use Groovy's .collect or similar methods currently, you can
// still transform a list into a set of actual build steps to be executed in
// parallel.

//List of GPUs available to execute code on


// Our initial list of strings we want to echo in parallel
def stringsToEcho
node('master')
{
    checkout scm
    stringsToEcho = getData('sampleList')
}

// The map we'll store the parallel steps in before executing them.
// step name is key of map, step is the value
def stepsForParallel = stringsToEcho.collectEntries {
    ["echoing ${it}" : transformIntoStep(it)]
}


// Actually run the steps in parallel - parallel takes a map as an argument,
// hence the above.
parallel(stepsForParallel)

// Takes an input string and returns a step to echo the string
def transformIntoStep(inputString) {
    // The step is wrapped in a groovy closure so that it executes when 'parallel' 
    // is called instead of when return statement is executing
    def availableGPUS = ["GPU1", "GPU2"]
    def numAvailableGPUS = 2;
    def gpuNumber = 0;
    gpuToUse = availableGPUS[gpuNumber]
    gpuNumber++;
    if(gpuNumber >= numAvailableGPUS)
    {
        gpuNumber = 0;
    }

    return {
        node {
            lock(gpuToUse)
            {
                echo inputString
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

// getData
// Ingests data from file and returns a list of strings
// Each element in input file must be delimited by a newline (\n)
// Args
//  fileName - Name of file from which to ingest data
def getData(fileName) {
    echo 'hi'
    sh 'dir'
    //Ingest data as string
    data = readFile(fileName)
    
    //Split data on newline and return list
    return data.split('\n')

}