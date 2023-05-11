# Cloud Shoes

![](/images/logo.png)


## Empresa


Cloud Shoes é uma empresa do ramo calçadista e se encontra em constante expansão onde tem elevado seu número de clientes e vendas.

Hoje a empresa não possui mais lojas fisícas, somente vendas online. Com isso busca por avanços tecnológicos frequentes, visando melhorar a experiência do cliente final e conseguentemente fransformar isso transformar isso em lucratividade e crescimente do empresa.

A Cloud Shoes está visando para o futuro a venda de vestuário, mas no momento tem seu foco exclusivo o calçado. Suas vendas somente no mercado interno brasileiro e não tem uma previsão para possíveis expansões para vendas fora do país.

Seu estrutura conta com :

* 500  colaboradores
* 50 fornecedores (tercerizados)
* Sede da empresa em São Paulo
* Escritório administrativo em Belo Horizonte 
* Estrutura de TI (datacenter) em São Paulo

## Insfraestrutura de TI

A Cloud Shoes hoje detém a seguinte estrutura:

* Datacenter próprio em sua em São Paulo
* Possui mais de 10 aplicações rodando para suportar o negócio da empresa
* Possui aproximadamente 120 servidores de produção ativos
* Possui aproximadamente 40 servidores de desenvolvimento e homologação ativos
* Toda a estrutura de servidores é executada sobre virtualização com VMware rodando sobre 10 servidores fisícos
* Utiliza sistemas operacionais Windows Server e Linux (Ubuntu Server e RedHat)
* O banco de dados é SQL Server 2016 Enterprise
* A empresa possui 2 storages com discos SSD
* A política de renovação de servidores fisícos é de 5 em 5 anos
* A última renovação foi realizada em 2020
  
## Estrutura de E-commerce

Atualmente o principal workload da Cloud Shoes é seu site de E-commerce, é uma aplicação crítica onde é executado todo processo de vendas da empresa.

Sua estrututa está composta pelos seguintes serviços:
* 4 servidores Windows Server 2019 - Frontend - executando IIS
* 4 servidores Windows Server 2019 - Backend
* 2 servidores Windows Server 2016 - SQL Server com Cluster Failover
* 1 servidor Windows Server 2012 - Serviço de integração com ERP
* Storage para o catalago de imagens do site com capacidade de 2TB - 70% em uso
* Storage utilizado para o armazenamento das bases de dados do SQL Server - 60% em uso
* 1 firewall de borda fazendo o balanceamento de carga para os servidores de frontend
* 1 balanceador de carga interno compartilhado para todas as aplicações

![](/images/infra.jpg)

## Dados estátisticos do E-Commerce

Hoje a Cloud Shoes disponibiliza uma tabela que exibe as médias de acessos referentes aos períodos de venda mais importantes do comércio brasileiro.

![](/images/table01.png)
