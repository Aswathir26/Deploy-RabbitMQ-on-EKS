# Deploy-RabbitMQ-on-EKS



**RabbitMQ**

RabbitMQ is a well-known open source message broker. We can define it as a general purpose messaging solution for enterprises, originally designed to implement the Advanced Message Queuing Protocol (AMQP) standard, but it now incorporating a wide variety of messaging protocols. RabbitMQ is perfect for application communication, both synchronous and asynchronous.  

**Step 1:**

Connect to EKS from aws cli

    $ aws configure
    $ aws sts get-caller-identity (to get User Id and Account number)
    $ aws eks --region < region > update-kubeconfig --name < cluster_name >


**Step 2 :**

Create namespace

    $ kubectl create namespace rabbitmq
    
 **Step 3 :**
 
 Clone repo:
 
      $ git clone https://github.com/Aswathir26/Deploy-RabbitMQ-on-EKS.git
      $ cd Deploy-RabbitMQ-on-EKS
   
 **Step 4 :**
  
 Create storage class
   
        $ kubectl apply -f sc.yaml
   
 **Step 5 :**
 
 Create PVC 
 
       $ kubectl apply -f pvc.yaml  --namespace rabbitmq
   
**Step 6 :**

Deploy RabbitMQ:

    $ helm repo add bitnami https://charts.bitnami.com/bitnami 
    $ helm install -f values.yaml rabbitmq bitnami/rabbitmq --namespace rabbitmq
    
 
