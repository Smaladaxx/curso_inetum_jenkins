pipeline {
    agent any
    environment {
        ficheroValores = "C:\\Users\\alvaro.gomez-lorenz\\valores.txt"
        ficheroSalida = "C:\\Users\\alvaro.gomez-lorenz\\salida.txt"
    }
    stages {
        stage('Lunes - Calcular Poblacion Final') {
            steps {
                script {
                    def lineas = readFile(env.ficheroValores).readLines()
                    def valorLinea = lineas[0] as Float
                    def calcularPoblacionFinal = valorLinea * 0.80
                    echo "Lunes: Población Final calculada: ${calcularPoblacionFinal}"
                    def contenido = fileExists(env.ficheroSalida) ? readFile(env.ficheroSalida) : ""
                    contenido += "Lunes: Poblacion Final: ${calcularPoblacionFinal}\n"
                    writeFile file: env.ficheroSalida, text: contenido
                }
            }
        }
        stage('Martes - Operaciones Aritmeticas') {
            steps {
                script {
                    def lineas = readFile(env.ficheroValores).readLines()
                    def valorLinea1 = lineas[1] as Float
                    def valorLinea2 = lineas[2] as Float
                    def suma = valorLinea1 + valorLinea2
                    def resta = valorLinea1 - valorLinea2
                    def multiplicacion = valorLinea1 * valorLinea2
                    def division = valorLinea1 / valorLinea2
                    echo "Martes: Suma: ${suma}, Resta: ${resta}, Multiplicación: ${multiplicacion}, División: ${division}"
                    def contenido = fileExists(env.ficheroSalida) ? readFile(env.ficheroSalida) : ""
                    contenido += "Martes: Suma: ${suma}, Resta: ${resta}, Multiplicacion: ${multiplicacion}, Division: ${division}\n"
                    writeFile file: env.ficheroSalida, text: contenido
                }
            }
        }
        stage('Miercoles - Convertir Temperatura') {
            steps {
                script {
                    def lineas = readFile(env.ficheroValores).readLines()
                    def tempF = lineas[3] as Float
                    def tempC = (tempF - 32) * 5 / 9
                    echo "Miercoles: Temperatura en Celsius: ${tempC}"
                    def contenido = fileExists(env.ficheroSalida) ? readFile(env.ficheroSalida) : ""
                    contenido += "Miercoles: Temperatura en Celsius: ${tempC}\n"
                    writeFile file: env.ficheroSalida, text: contenido
                }
            }
        }
        stage('Jueves - Informar Usuario') {
            steps {
                script {
                    def usuario = bat(script: 'whoami', returnStdout: true).trim()
		    echo "El usuario del PC es: ${env.USERNAME}" 
                }
            }
        }
              stage('Viernes - Crear Proyecto Maven') {
            steps {
                script {
                    bat '''
                    curl -o project.zip
https://start.spring.io/starter.zip
^
                        -d dependencies=mysql ^
                        -d type=maven-project ^
                        -d language=java ^
                        -d packaging=jar ^
                        -d javaVersion=11
                    powershell -Command "Expand-Archive -Path 'project.zip' -DestinationPath '.'"
                    cd proyecto_maven
                    mvn clean install
                    '''
                    echo "Viernes: Proyecto Maven creado y compilado con exito"
                }
            }
        }
    }
    post {
        always {
            script {
                echo "Pipeline completado. Revisa el archivo ${env.ficheroSalida} para los resultados."
            }
        }
    }
}



ficheroValores ficheroSalida:

