WebLogic Server 11g com 1 Domínio e 1 AdminServer
================================

WebLogic 11g 10.3.6 Cluster (admin, node1)

COMO EXECUTAR
---------------
Fazer o download e instalar os seguintes softwares.
 * [Oracle VirtualBox (latest)](http://www.virtualbox.org)
 * [VagrantUP (latest)](http://www.vagrantup.com)
 * [Git](https://help.github.com/articles/set-up-git) client

Fazer o download e colocar na raiz do sistema, no diretório => '/tmp/software'
 * [Oracle JDK 7u55](http://www.oracle.com/technetwork/java/javase/downloads/jdk7-downloads-1880260.html) (a)
 * [Oracle WebLogic 11g 10.3.6](http://www.oracle.com/technetwork/middleware/weblogic/downloads/wls-for-dev-1703574.html) - download **wls1036_generic.jar**

Após esta pré-configuração, executar o comando
<pre>$ vagrant up</pre>

INFORMAÇÕES RELEVANTES
---------------

Informações sensíveis(senhas, IPs, etc) estão em  **puppet/hieradata**
IP localhost virtualbox: 127.0.0.1

  Porta 2200: SSH AdminServer
    vagrant-vagrant

  Porta 2201: SSH Node1  
    vagrant-vagrant

IP AdminServer: 10.10.10.10

  Porta 7001: Console WLS
    weblogic-weblogic1
    
IP Node1: 10.10.10.100
