# Cloud Shoes


<div align="center">

![](/images/logo.logo.jpg)


</div>

## Empresa


Cloud Shoes é uma empresa do ramo calçadista e se encontra em constante expansão onde tem elevado seu número de clientes e vendas.

Hoje a empresa não possui mais lojas físicas, somente vendas online. Com isso busca por avanços tecnológicos frequentes, visando melhorar a experiência do cliente final e consequentemente transformar isso em lucratividade e crescimento da empresa.

A Cloud Shoes está visando para o futuro a venda de vestuário, mas no momento tem seu foco exclusivo o calçado. Suas vendas somente no mercado interno brasileiro e não tem uma previsão para possíveis expansões para vendas fora do país.

Sua estrutura conta com :

* 500  colaboradores
* 50 fornecedores (terceirizados)
* Sede da empresa em São Paulo
* Escritório administrativo em Belo Horizonte 
* Estrutura de TI (datacenter) em São Paulo

## Infraestrutura de TI

A Cloud Shoes hoje detém a seguinte estrutura:

* Datacenter próprio em sua em São Paulo
* Possui mais de 10 aplicações rodando para suportar o negócio da empresa
* Possui aproximadamente 120 servidores de produção ativos
* Possui aproximadamente 40 servidores de desenvolvimento e homologação ativos
* Toda a estrutura de servidores é executada sobre virtualização com VMware rodando sobre 10 servidores físicos
* Utiliza sistemas operacionais Windows Server e Linux (Ubuntu Server e RedHat)
* O banco de dados é SQL Server 2016 Enterprise
* A empresa possui 2 storages com discos SSD
* A política de renovação de servidores físicos é de 5 em 5 anos
* A última renovação foi realizada em 2020
  
## Estrutura de E-commerce

Atualmente o principal workload da Cloud Shoes é seu site de E-commerce, é uma aplicação crítica onde é executado todo processo de vendas da empresa.

Sua estrutura está composta pelos seguintes serviços:
* 4 servidores Windows Server 2019 - Frontend - executando IIS
* 4 servidores Windows Server 2019 - Backend
* 2 servidores Windows Server 2016 - SQL Server com Cluster Failover
* 1 servidor Windows Server 2012 - Serviço de integração com ERP
* Storage para o catalogo de imagens do site com capacidade de 2TB - 70% em uso
* Storage utilizado para o armazenamento das bases de dados do SQL Server - 60% em uso
* 1 firewall de borda fazendo o balanceamento de carga para os servidores de frontend
* 1 balanceador de carga interno compartilhado para todas as aplicações

![](/images/infra.jpg)

## Dados estatísticos do E-Commerce

Hoje a Cloud Shoes disponibiliza uma tabela que exibe as médias de acessos referentes aos períodos de venda mais importantes do comércio brasileiro.

![](/images/table01.png)

## Problemas enfrentados

Neste momento, a Cloud Shoes está enfrentando dificuldades relacionadas à estrutura e desempenho de sua carga de trabalho principal, o que resultou em perda de vendas em alguns casos e até mesmo na preferência dos usuários por outras lojas concorrentes. Abaixo alguns de suas principais dificuldades.

* Notam-se períodos de grande lentidão no acesso dos clientes, principalmente para abrir imagens de produtos
* Em determinados dias, nota-se a falta de recursos em alguns servidores nos horários de picos e durante a madrugada um consumo de menos de 10%, em média
* Dificuldade em analisar (monitorar) quais são os produtos mais acessados do site e o tempo de resposta nas páginas mais acessadas
* Problemas de compliance relativo ao equipamento de firewall que publica a aplicação externamente, por não possuir a feature de WAF
* A equipe da Cloud Shoes precisa realizar um esforço significativo para provisionar novos servidores durante os períodos de pico de acesso e vendas. Além disso, todos os recursos relacionados aos servidores precisam ser excluídos manualmente para liberar o hardware posteriormente.
* O servidor de integração que executa uma aplicação legada responsável por rodar serviços de processamento assíncrono e integrar dados de compras e NFES com o ERP. Essa aplicação é dependente de serviços do Windows e algumas COM+. Infelizmente, o servidor de integração não possui um balanceamento de carga interno devido à sobrecarga do único balanceador de carga disponível. Atualmente, a empresa está aguardando a compra de um novo balanceador de carga para poder adicionar um novo servidor a esse serviço.
* A Cloud Shoes realiza backups de todos os dados da aplicação e do banco de dados em um storage, que são mantidos por 15 dias para permitir uma restauração rápida. Após esse período, esses dados são transferidos para fitas de backup, coletados e armazenados em um cofre externo à estrutura, o que dificulta o processo de restauração de dados com mais de 15 dias.
* A Cloud Shoes está enfrentando um alto custo de armazenamento para as imagens antigas ou não utilizadas de seu catálogo. Infelizmente, o storage atual não oferece um modelo de disco mais barato para "tierizar" essas imagens, ou seja, movê-las para um nível de armazenamento mais econômico.

## Necessidades da empresa

A Cloud Shoes planeja migrar 70% de suas aplicações para a nuvem nos próximos dois anos como parte de sua estratégia de crescimento. Para essa transição, a empresa optou pelo provedor Azure, devido à sua ampla compatibilidade (90%) com o ambiente Microsoft e à maior familiaridade técnica de sua equipe de infraestrutura, banco de dados e aplicações. A mudança para a nuvem tem como objetivo resolver os desafios enfrentados atualmente pela empresa e garantir maior escalabilidade e eficiência em suas operações.

* Reduzir custos relacionados a renovação de servidores e garantia de equipamentos
* Entregar maior poder de escalabilidade em datas de maior demanda
* Otimizar o uso de recursos em períodos de baixa demanda
* Utilizar novas tecnologias que melhorem a performance na experiência de acesso, navegação e compra para os usuários finais
* Reduzir o esforço administrativo da equipe de infraestrutura de servidores
* Aumentar a segurança relativa à exposição do e-commerce
* Reduzir o tempo para restore de dados com mais de 15 dias
* Possibilitar no futuro que os clientes realizem autenticação no formato B2C.
* Maior monitoramento sobre acessos, principais produtos e tempos de respostas
* Reduzir custos de armazenamento para imagens antigas do catálogo (sem uso no momento)

## Observações

* Atualmente, a Cloud Shoes ainda não possui estrutura de produção no Azure e mantém apenas uma assinatura PAYG na plataforma, com baixo consumo. No entanto, a empresa já estabeleceu a replicação dos usuários do Active Directory local com o Azure AD, em razão da utilização de serviços do Microsoft 365, como Exchange Online, OneDrive e Teams.
* Não existe nenhuma conexão física entre o ambiente local e o Azure
* Todos os servidores Windows fazem parte do domínio cloudstore.local, onde existem 2 servidores de Active Directory com zonas de DNS integradas
* Toda autenticação dos clientes externos para realizar a compra é feita diretamente em uma estrutura do banco de dados SQL Server
* Toda estrutura  do E-Commerce não possui dependência de outros workloads (exceto estrutura de AD e DNS). Apenas o servidor de integração que precisa se comunicar com a estrutura do ERP para transportar dados relativos a vendas e NFEs
* Nessa etapa do projeto, estimasse a migração somente do workload E-Commerce