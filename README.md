# Projeto Prático: Estrutura de Microsserviços com Docker e Nginx

Este repositório é uma evolução do desafio prático de implementação de containers e microsserviços, focado em abstrair ambientes e otimizar o consumo de recursos.

## 🏗️ Arquitetura do Projeto

O projeto simula um ambiente de microsserviços distribuídos, composto por:
- **Load Balancer (Nginx):** Configurado via `nginx.conf` e um `Dockerfile` customizado para distribuir a carga (porta 4500) entre três servidores web distintos.
- **Aplicação (PHP):** Um script (`index.php`) que gera dados randômicos, captura o *hostname* do container e realiza a inserção no banco de dados.
- **Banco de Dados (MySQL):** Estrutura inicializada através do script `banco.sql`, contendo a tabela `dados` para armazenar as requisições processadas.

## 🚀 Propostas de Melhoria e Evolução (Next Steps)

Analisando o código original, identifiquei oportunidades de evolução para tornar este projeto agnóstico de nuvem e totalmente automatizado:

1. **Remoção de IPs Hardcoded:** O script `index.php` e o `nginx.conf` atualmente apontam para IPs fixos de instâncias EC2 da AWS. A evolução ideal é substituir esses IPs por **variáveis de ambiente** ou utilizar o DNS interno do Docker.
2. **Orquestração com Docker Compose:** Criar um arquivo `docker-compose.yml` para subir toda a stack (Nginx, 3 instâncias do App PHP e o MySQL) com um único comando, criando uma rede isolada e facilitando testes locais.
3. **Segurança de Credenciais:** Remover a senha (`Senha123`) em texto claro do código-fonte e gerenciá-la via AWS Secrets Manager ou `.env`.

## 🛠️ Tecnologias Utilizadas
* Docker
* Nginx (Proxy Reverso/Load Balancer)
* PHP 
* MySQL
* AWS (EC2)
