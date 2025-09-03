# 📁 Manipulando o Sistema de Arquivos no Linux (AWS EC2)

Este projeto contém a documentação do meu laboratório prático em uma instância **Amazon Linux EC2**, focado na manipulação do sistema de arquivos. O objetivo foi criar, copiar, mover e deletar arquivos e diretórios, consolidando o uso de comandos essenciais do terminal.

-----

📂 **Estrutura do Projeto**

```
sistema-de-arquivos-linux/
│
├── imagens/
│
└── README.md
```

-----


### **🛠️ Tecnologias Utilizadas**

<div align="left"> <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/amazonwebservices/amazonwebservices-original-wordmark.svg" alt="AWS" width="50" height="50"/> <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/linux/linux-original.svg" alt="Linux" width="50" height="50"/>


-----


## **🎯 Objetivos**

  * Criar uma estrutura de pastas específica.
  * Criar arquivos vazios.
  * Copiar e mover arquivos e diretórios.
  * Remover arquivos e diretórios.


-----


## **🚀 Ambiente**

  * **Serviço**: Amazon EC2
  * **Tipo de instância**: `t3.micro` (1 vCPU, 1 GiB RAM)
  * **Sistema Operacional**: Amazon Linux 2
  * **Acesso**: SSH (via `.pem` ou `.ppk`)


-----


## **📌 Etapas do Laboratório**

### **1. Conexão via SSH**

1.  Baixei a chave de acesso (`.pem` para Mac/Linux ou `.ppk` para Windows).
2.  Altere as permissões da chave (`chmod 400 labsuser.pem`).
3.  Conectei-me à instância usando o comando:
    ```bash
    ssh -i labsuser.pem ec2-user@<public-ip>
    ```

    <img width="1290" height="648" alt="01-acesso-ssh" src="https://github.com/user-attachments/assets/a7472374-fc6e-4455-9cd8-fa9240ec2d04" />


### **2. Criando a Estrutura de Pastas**

## **🏗️ Arquitetura do Sistema de Arquivos**

<img width="866" height="651" alt="arquiteturadearquivos" src="https://github.com/user-attachments/assets/b29775d6-66ca-4d1d-9882-6fa8be278732" />

-----

Reconstruí a estrutura de diretórios e arquivos da empresa `CompanyA` usando os comandos `mkdir` e `touch`.

  * **Criei os diretórios principais**:

    ```bash
    mkdir CompanyA
    cd CompanyA
    mkdir Finance HR Management
    ```

    <img width="1290" height="648" alt="02-criacao-estrutura" src="https://github.com/user-attachments/assets/51c19dae-dc3b-4853-a94e-0188150ae23f" />


  * **Criei os arquivos dentro de `HR`**:

    ```bash
    cd HR
    touch Assessments.csv TrialPeriod.csv
    ```

    <img width="1298" height="735" alt="03-criacao-arquivos-hr" src="https://github.com/user-attachments/assets/aefbd0c1-c35c-43fb-a97c-89aed24e04f5" />


  * **Criei os arquivos dentro de `Finance`**:

    ```bash
    cd ../Finance
    touch Salary.csv ProfitAndLossStatements.csv
    ```

    <img width="1298" height="735" alt="04-criacao-arquivos-finance" src="https://github.com/user-attachments/assets/50a344b4-59c4-4a09-a43b-001636236b65" />


  * **Criei os arquivos dentro de `Management`**:

    ```bash
    cd ..
    touch Management/Managers.csv Management/Schedule.csv
    ```

    <img width="1298" height="735" alt="05-criacao-arquivos-management" src="https://github.com/user-attachments/assets/8dbbad3a-2a14-44cf-97fb-7e7fbd051366" />


  * **Validei a estrutura completa**:
    Usei `ls -laR` para listar todos os arquivos e diretórios recursivamente, confirmando que a estrutura foi criada corretamente.

    <img width="1298" height="735" alt="06-validacao-estrutura" src="https://github.com/user-attachments/assets/a77fb5e0-2137-4550-94fe-0e7fb764e9a2" />


-----

### **3. Deletando e Reorganizando Pastas**

## **🏗️Arquitetura Reorganizada do Sistema de Arquivos**

<img width="796" height="752" alt="arquiteturareorganizada" src="https://github.com/user-attachments/assets/d9206b2c-2787-4b4c-ad82-052cf02e4756" />


Fui encarregado de reorganizar a estrutura, o que me forçou a usar comandos mais avançados de cópia, movimentação e apagamento.

  * **Copiei a pasta `Finance` para dentro de `HR`**:

    ```bash
    cp -r Finance HR
    ```
    
    O comando `cp -r` foi essencial para copiar a pasta e todo o seu conteúdo recursivamente.

    <img width="1298" height="735" alt="07-reorganizacao-pastas" src="https://github.com/user-attachments/assets/cffdbf9a-ef65-4188-b558-703984692671" />


  * **Removi a pasta `Finance` original**:
    Tentei usar `rmdir Finance`, mas falhou, pois a pasta não estava vazia. Entendi que `rmdir` só funciona para diretórios vazios. A solução foi:

    ```bash
    rm Finance/*
    rmdir Finance
    ```
    
    Ou usar o comando `rm -r Finance` para remover de forma recursiva.

    <img width="1298" height="735" alt="08-rm-finance-fail" src="https://github.com/user-attachments/assets/8161ec04-1bcd-42e7-8dc8-70514af362cf" />


  * **Movi a pasta `Management`**:
    Movi a pasta inteira para dentro de `HR` usando o comando `mv`.

    ```bash
    mv Management HR
    ```

    <img width="1298" height="735" alt="09-mv-management" src="https://github.com/user-attachments/assets/b103013c-cafc-40b7-b6ff-d492132687d8" />


  * **Criei uma nova pasta e movi arquivos**:
    Naveguei para a pasta `HR`, criei o diretório `Employees` e movi dois arquivos para dentro dele.

    ```bash
    cd HR
    mkdir Employees
    mv Assessments.csv TrialPeriod.csv Employees
    ```

    <img width="1298" height="735" alt="10-criacao-nova-pasta" src="https://github.com/user-attachments/assets/bf0b9f97-6740-4027-bdd8-a5517fe9e8e1" />


-----

## **📈 Conclusão**

Este laboratório foi fundamental para solidificar meu conhecimento sobre a manipulação do sistema de arquivos no Linux. Aprendi a importância de comandos como `mkdir`, `touch`, `cp`, `mv` e `rm`, além das diferenças entre `rm` e `rmdir`. Agora me sinto mais confiante para organizar e gerenciar arquivos e diretórios diretamente do terminal.
