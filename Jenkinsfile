pipeline{

    agent any 
    parameters {
        choice(
            name: 'ENVIRONMENT',
            choices: ['Dev', 'QA', 'PreProd', 'Prod'],
            description: 'Select the environment to deploy to.'
        )

        string(
            name: 'webtag',
            defaultValue: 'latest',
            description: 'Enter the web image tag .'
        )
        string(
            name: 'reviewstag',
            defaultValue: 'latest',
            description: 'Enter the review image tag.'
        )
        string(
            name: 'prodtag',
            defaultValue: 'latest',
            description: 'Enter the product image tag.'
        )
        string(
            name: 'replicaCount',
            defaultValue: '1' ,
            description: 'Enter the replica count.'
        )

        
    }

      options {
        buildDiscarder(logRotator(numToKeepStr: '3')) 
    }
    stages{


      stage('Cleaning WSpace') {
            steps {
                cleanWs() // Clean workspace before build
            }
        }

      stage('Dev Deployment'){
    
         when {
                expression { params.ENVIRONMENT == 'Dev' } 
            }


           steps{
            script{
                   
                sh """
                rm -rf expresso || true 
                git clone git@github.com:JQuay/expresso.git
                   """
  sh """
        cat << 'EOF' > $WORKSPACE/expresso/expresso-shop-product/dev-values.yaml
        replicaCount: 1
        image:
          repository: hossambarakat/espresso-shop-product-catalog
          pullPolicy: IfNotPresent
          tag: '${params.webtag}'
        
   """
 sh """
        cat << 'EOF' > $WORKSPACE/expresso/expresso-shop-reviews/dev-values.yaml
        replicaCount: 1
        image:
          repository: hossambarakat/espresso-shop-reviews
          pullPolicy: IfNotPresent
          tag:   '${params.reviewstag}'
        
  """
   sh """   
        cat << 'EOF' > $WORKSPACE/expresso/expresso-shop-web/dev-values.yaml
        replicaCount: 1
        image:
          repository: hossambarakat/espresso-shop-web
          pullPolicy: IfNotPresent
          tag: '${params.webtag}' 

        
    """
  sh """
                cd $WORKSPACE/expresso

                git config --global user.name "JQuay"
                git config --global user.email "josephquayson877@gmail.com"

                git add -A
                git commit -m "commit from Jenkins"
                git push origin main
         """
                   
            }
           }
        }

        
           
 






        stage('QA Deployment'){

            when {
                expression { params.ENVIRONMENT == 'QA' } 
            }
                     steps{
            script{
                   
                sh """
                rm -rf expresso || true 
                git clone git@github.com:JQuay/expresso.git
                   """
  sh """
        cat << 'EOF' > $WORKSPACE/expresso/expresso-shop-product/qa-values.yaml
        replicaCount: '${params.replicaCount}'
        image:
          repository: hossambarakat/espresso-shop-product-catalog
          pullPolicy: IfNotPresent
          tag: '${params.webtag}'
        
   """
 sh """
        cat << 'EOF' > $WORKSPACE/expresso/expresso-shop-reviews/qa-values.yaml
        replicaCount: '${params.replicaCount}'
        image:
          repository: hossambarakat/espresso-shop-reviews
          pullPolicy: IfNotPresent
          tag:   '${params.reviewstag}'
        
  """
   sh """   
        cat << 'EOF' > $WORKSPACE/expresso/expresso-shop-web/qa-values.yaml
        replicaCount: '${params.replicaCount}'
        image:
          repository: hossambarakat/espresso-shop-web
          pullPolicy: IfNotPresent
          tag: '${params.webtag}' 
        
    """
  sh """
                cd $WORKSPACE/expresso

                git config --global user.name "JQuay"
                git config --global user.email "josephquayson877@gmail.com"

                git add -A
                git commit -m "commit from Jenkins"
                git push origin main
         """
                   
            }
           }
        }


        stage('Preprod Deployment'){

            when {
                expression { params.ENVIRONMENT == 'PreProd' } 
            }
                  steps{
            script{
                   
                sh """
                rm -rf expresso || true 
                git clone git@github.com:JQuay/expresso.git
                   """
  sh """
        cat << 'EOF' > $WORKSPACE/expresso/expresso-shop-product/preprod-values.yaml
        replicaCount: '${params.replicaCount}'
        image:
          repository: hossambarakat/espresso-shop-product-catalog
          pullPolicy: IfNotPresent
          tag: '${params.webtag}'
        
      """
 sh """
        cat << 'EOF' > $WORKSPACE/expresso/expresso-shop-reviews/prepro-values.yaml
        replicaCount: '${params.replicaCount}'
        image:
          repository: hossambarakat/espresso-shop-reviews
          pullPolicy: IfNotPresent
          tag:   '${params.reviewstag}'
        
  """
   sh """   
        cat << 'EOF' > $WORKSPACE/expresso/expresso-shop-web/preprod-values.yaml
        replicaCount: '${params.replicaCount}'
        image:
          repository: hossambarakat/espresso-shop-web
          pullPolicy: IfNotPresent
          tag: '${params.webtag}' 
        
    """
  sh """
                cd $WORKSPACE/expresso

                git config --global user.name "JQuay"
                git config --global user.email "josephquayson877@gmail.com"

                git add -A
                git commit -m "commit from Jenkins"
                git push origin main
         """
                   
            }
           }
        }
 stage('Production Deployment'){

            when {
                expression { params.ENVIRONMENT == 'Prod' } 
            }
                       steps{
            script{
                   
                sh """
                rm -rf expresso || true 
                git clone git@github.com:JQuay/expresso.git
                   """
  sh """
        cat << 'EOF' > $WORKSPACE/expresso/expresso-shop-product/prod-values.yaml
        replicaCount: 1
        image:
          repository: hossambarakat/espresso-shop-product-catalog
          pullPolicy: IfNotPresent
          tag: '${params.webtag}'
        
   """
 sh """
        cat << 'EOF' > $WORKSPACE/expresso/expresso-shop-reviews/prod-values.yaml
        replicaCount: 1
        image:
          repository: hossambarakat/espresso-shop-reviews
          pullPolicy: IfNotPresent
          tag: '${params.reviewstag}'
        
  """
   sh """   
        cat << 'EOF' > $WORKSPACE/expresso/expresso-shop-web/prod-values.yaml
        replicaCount: 1
        image:
          repository: hossambarakat/espresso-shop-web
          pullPolicy: IfNotPresent
          tag: '${params.webtag}' 
        
    """
  sh """
                cd $WORKSPACE/expresso

                git config --global user.name "JQuay"
                git config --global user.email "josephquayson877@gmail.com"

                git add -A
                git commit -m "commit from Jenkins"
                git push origin main
         """
                   
            }
           }
         
        }


    }
}