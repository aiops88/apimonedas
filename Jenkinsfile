pipeline{
    agent any

    environment{
        DOCKER_IMAGE = 'apimonedastt'
        CONTAINER_NAME = 'dockerapimonedastt'
        DOCKER_NETWORK =  'dockermonedas_red'
//        DOCKER_BUILD_DIR = 'presentacion'
        HOST_PORT = '9080'
        CONTAINER_PORT = '8080'
    }

    stages{
        /*
        stage('Compilación Maven'){
            steps{
                bat 'mvn clean package -Dskiptests'
            }
        }
        */
        stage('Construir imagen'){
            steps{
                //dir("${DOCKER_BUILD_DIR}"){
                    bat "docker build . -t ${DOCKER_IMAGE}"
                //}
            }
        }

        stage('Detener contenedor existente') {
            steps {
                // Detener el contenedor si existe, pero siempre retornar éxito
                bat '''
                    docker stop ${CONTAINER_NAME} || echo "No se pudo detener el contenedor porque no existe."
                    exit 0
                '''
                bat '''
                    docker rm ${CONTAINER_NAME} || echo "No se pudo eliminar el contenedor porque no existe."
                    exit 0
                '''
            }
        }
