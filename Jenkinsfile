pipeline {
    agent any  // Run on any available agent

    stages {
        stage('Shell Script Execution') {
            steps {
                sh 'echo Hello from Shell Script'
            }
        }

        stage('Build Job') {
            steps {
                build job: 'Assignment-1', wait: false  // Updated job name
            }
        }

        stage('Checkout from Version Control') {
            steps {
                checkout scm
            }
        }

        stage('Delete Workspace Directory') {
            steps {
                deleteDir()
            }
        }

        stage('Change Directory') {
            steps {
                dir('new_directory') {
                    echo "Inside new directory"
                }
            }
        }

        stage('Print Message') {
            steps {
                echo "Hello from Jenkins"
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

        stage('Clone Git Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/AkshatPandey-2004/Calculator.git'
            }
        }

        stage('User Input Prompt') {
            steps {
                input 'Proceed with the deployment?'
            }
        }

        stage('Check OS Type') {
            steps {
                script {
                    if (isUnix()) {
                        echo 'Running on Unix/Linux'
                    } else {
                        echo 'Running on Windows'
                    }
                }
            }
        }

        stage('Print Working Directory') {
            steps {
                script {
                    echo "Current directory: ${pwd()}"
                }
            }
        }

        stage('Read File Contents') {
            steps {
                script {
                    if (fileExists('testfile.txt')) {  // Ensure file exists before reading
                        def content = readFile 'testfile.txt'
                        echo "File Content: ${content}"
                    } else {
                        echo "testfile.txt does not exist, skipping read."
                    }
                }
            }
        }

        stage('Pause Execution') {
            steps {
                sleep 5
            }
        }

        stage('Stash File for Later Use') {
            steps {
                stash includes: 'testfile.txt', name: 'stash-test'
            }
        }

        stage('Archive Build Artifacts') {
            steps {
                step([$class: 'ArtifactArchiver', artifacts: '*.jar'])
            }
        }

        stage('Set Environment Variables') {
            steps {
                withEnv(["MY_VAR=Hello"]) {
                    echo "Environment Variable: ${env.MY_VAR}"
                }
            }
        }

        stage('Maven Build') {
            steps {
                withMaven(maven: 'Maven3') {  // Ensure 'Maven3' is correctly configured in Jenkins
                    sh 'mvn clean install'
                }
            }
        }

        stage('Write File') {
            steps {
                writeFile file: 'output.txt', text: 'Hello, Jenkins!'
            }
        }
    }
}
