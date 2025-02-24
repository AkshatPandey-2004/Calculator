pipeline {
    agent any  // Runs on any available agent

    stages {
        stage('Checkout Source Code') {
            steps {
                checkout scm
            }
        }

        stage('Shell Script Execution') {
            steps {
                sh 'echo Hello from Shell Script'
            }
        }

        stage('Build Job') {
            steps {
                build job: 'Assignment-1', wait: false  // Triggers another Jenkins job
            }
        }

        stage('Check if File Exists') {
            steps {
                script {
                    if (fileExists('testfile.txt')) {
                        echo 'File exists'
                    } else {
                        echo 'File does not exist'
                    }
                }
            }
        }

        stage('Read File Contents') {
            steps {
                script {
                    if (fileExists('testfile.txt')) {  
                        def content = readFile 'testfile.txt'
                        echo "File Content: ${content}"
                    } else {
                        echo "testfile.txt does not exist, skipping read."
                    }
                }
            }
        }

        stage('Maven Build') {
            steps {
                withMaven(maven: 'Maven3') {  
                    sh 'mvn clean package'  // Ensure .jar file is generated
                }
            }
        }

        stage('Archive Build Artifacts') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', onlyIfSuccessful: true
            }
        }

        stage('Write and Stash File') {
            steps {
                script {
                    writeFile file: 'output.txt', text: 'Hello, Jenkins!'  
                    stash includes: 'output.txt', name: 'stash-output'
                }
            }
        }

        stage('Pause Execution') {
            steps {
                sleep 5
            }
        }

        stage('Set Environment Variables') {
            steps {
                withEnv(["MY_VAR=Hello"]) {
                    echo "Environment Variable: ${env.MY_VAR}"
                }
            }
        }
    }
}
