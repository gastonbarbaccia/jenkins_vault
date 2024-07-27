def secret

pipeline {

    agent any
    
    environment {
        // Se obtiene la dirección de Vault de las credenciales
        VAULT_ADDR = credentials('vault-address')  // ID de la credencial de la dirección de Vault
        VAULT_TOKEN = credentials('vault-token')   // ID de la credencial del token de Vault
        
    }
    
    stages {
  
        stage('Fetch Secret from Vault') {
            steps {
                script {
                    // Fetch the secret using curl
                    secret = sh(script: 'curl -H "X-Vault-Token: $VAULT_TOKEN" -X GET $VAULT_ADDR/v1/secret/data/devops/jenkins | jq -r .data.data.host', returnStdout: true).trim()

                    // Utiliza el secreto según sea necesario
                    echo "Fetched secret: ${secret}"
                }
            }
        }
    }
}