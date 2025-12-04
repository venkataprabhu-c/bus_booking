pipeline {
    agent {
        label 'java'
    }

    environment {
        TOMCAT_HOST = '172.31.19.35'
        TOMCAT_USER = 'root'
        TOMCAT_DIR = '/opt/tomcat10/webapps'
        JAR_FILE = 'bus-booking-app-1.0-SNAPSHOT.war'
    }

    stages {
        stage('checkout') {
            steps {
                sh 'rm -rf bus_booking'
                sh 'git clone https://github.com/venkataprabhu-c/bus_booking.git'
            }
        }

        stage('build') {
            steps {
                sh "mvn clean install"
            }
        }

        stage('Show Contents of target') {
            steps {
                script {
                    // Print the contents of the target directory
                    sh 'ls -l target'
                }
            }
        }

        stage('Run WAR Locally') {
            steps {
                script {
                    // Run the JAR file using java -war
                    sh "java -jar target/${JAR_FILE}"
                }
            }
        }
    }
