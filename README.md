# ##################################################################
# Installaing KAFKA in EC2 thru Ansible playbooks
# ##################################################################
  ansible-playbook KafkaLogstash-Playbooks-main/kafka.yml

 Login into kafka Server and verify using below query,
  $ ps -ef | grep -i kafka

  $ yum install nc -y
  $ nc -vz localhost 9092    # kafka port
  $ nc -vz localhost 2181    # zoo-keeper port

# ##################################################################
# Installaing LOGSTASH in EC2 thru Ansible playbooks
# ##################################################################

# Modify logstash-kafka.conf file 
  1) update kafka server ip_address & Topic Name
  2) update elasticsearch loadbalancer url & Credentials

# Modify key-logstash-conf.yaml file
  1) update kafka server ip_address & Topic Name
  2) update elasticsearch loadbalancer url & Credentials
  3) update Certificate ID
     kubectl get secret quickstart-es-http-certs-public -o go-template='{{index .data "tls.crt" | base64decode}}'


 $ ansible-playbook KafkaLogstash-Playbooks-main/Logstash.yml
 $ ansible-playbook KafkaLogstash-Playbooks-main/key-logstash-conf.yaml
 $ ansible-playbook KafkaLogstash-Playbooks-main/logstash-service.yml

 Login into Logstash Server and verify using below query,
  $ ps -ef | grep -i logstash
# ##################################################################

