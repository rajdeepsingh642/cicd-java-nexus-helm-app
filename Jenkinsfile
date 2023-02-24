
pipeline{
    
    agent any 
    
    stages {
        
        stage('Git Checkout'){
            
            steps{
                
               git branch: 'main', url: 'https://github.com/rajdeepsingh642/cicd-java-nexus-helm-app.git'
                    
                    
                }
        }
        
         stage('pushin helm chart to nexus'){
            steps{
                script{
                    withCredentials([string(credentialsId: 'nexus-token', variable: 'nexus_creds')]) {
               
                         
                        echo "Packing helm chart"
                         sh "helm package -d ${WORKSPACE}/helm ${WORKSPACE}/helm/kubernetes/myapp "
                         sh "curl -u admin:${nexus_creds}  http://192.168.1.70:8081/repository/helm-repo/ --upload-file  ${WORKSPACE}/helm/kubernetes/myapp-1.tgz -v"
}
                }
            }
         }
        
        //echo "Packing helm chart"
          //  sh "helm package -d ${WORKSPACE}/helm ${WORKSPACE}/helm/devopsodia"
           // sh "${WORKSPACE}/build.sh --pack_helm --push_helm --helm_repo ${HELM_REPO} --helm_usr ${HELM_USR} --helm_psw ${HELM_PSW}"
           //sh "curl -u admin:admin http://192.168.56.120:8081/repository/argocd-helm-repo/ --upload-file ${WORKSPACE}/helm/devopsodia-1.tgz -v"
       
    }
}  

}
