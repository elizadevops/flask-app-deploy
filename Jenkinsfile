template = '''
apiVersion: v1
kind: Pod
metadata:
  labels:
    run: kubernetes
  name: kubernetes
spec:
  serviceAccount: kubernetes
  containers:

  - image: elizadevops/my-binary:1.0.0
    name: kubernetes
    
    '''

podTemplate(cloud: 'kubernetes', label: 'kubernetes', yaml: template) {
node("kubernetes") {
    container("kubernetes") {
    stage("Checkout SCM") { 
        git branch: 'main', url: 'https://github.com/elizadevops/flask-app-deploy.git'
    } 
    stage("Cheks") {
        sh """
        terraform version
        helm version
        kubectl version
        kubectl get node
        """
    }
    }
}
}