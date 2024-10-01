pipeline {
    agent any
    environment {
        poblacion_actual = 5000000
        clima_actual = "Despejado 25°C"
    }
    stages {
        stage('Ejercicio 6') {
            steps {
                script {
                    echo "Clima Actual"
                    echo "Clima: ${env.clima_actual}"
                    echo "Poblacion Actual"
                    echo "Poblacion: ${env.poblacion_actual}"
                }
            }
        }
        stage('Ejercicio 7') {
            steps {
                script {
                    def poblacionTotal = env.poblacion_actual.toInteger()
                    def poblacionNeta = poblacionTotal * 0.8
                    def fechaActual = new Date().format('yyyy-MM-dd')

                    def nombreArchivo = "poblacionNeta${fechaActual}.txt"
                    writeFile file: nombreArchivo, text: "Población neta (80% de la población total): ${poblacionNeta}"

                    echo "===== Población Neta ====="
                    echo "Población neta calculada: ${poblacionNeta}"
                    echo "Archivo generado: ${nombreArchivo}"
                }
            }
        }
    }
    post {
        success {
            echo 'Pipeline completado'
        }
        failure {
            echo 'Error en el pipeline.'
        }
    }
}
