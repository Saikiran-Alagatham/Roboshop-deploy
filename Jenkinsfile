pipeline{
    agent{
        node{ label 'workstation'}
    }

    parameters{
        choice(name: 'Terraform Actions', choices: ['Apply','Destroy'], description: 'Pick a teraform action')
    }

    stage('Terraform init'){
        steps{
            sh 'terraform init'
        }

    }

    stage('Terraform apply'){
        when{
            environment name: 'Terraform Actions', value:'Apply'
        }
        steps{
            sh 'terraform apply -auto-approve'
        }

    }

    stage('Terraform destroy'){
        when{
            environment name: 'Terraform Actions', value:'Destroy'
        }
        steps{
            sh 'terraform destroy -auto-approve'
        }

    }
}