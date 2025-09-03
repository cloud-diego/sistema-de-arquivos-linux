# 📁 Manipulando o Sistema de Arquivos no Linux (AWS EC2)

Este projeto contém a documentação do meu laboratório prático em uma instância **Amazon Linux EC2**, focado na manipulação do sistema de arquivos. O objetivo foi criar, copiar, mover e deletar arquivos e diretórios, consolidando o uso de comandos essenciais do terminal.

-----

### **🛠️ Tecnologias Utilizadas**

\<div align="left"\> \<img src="[https://cdn.jsdelivr.net/gh/devicons/devicon/icons/amazonwebservices/amazonwebservices-original-wordmark.svg](https://cdn.jsdelivr.net/gh/devicons/devicon/icons/amazonwebservices/amazonwebservices-original-wordmark.svg)" alt="AWS" width="50" height="50"/\> \<img src="[https://cdn.jsdelivr.net/gh/devicons/devicon/icons/linux/linux-original.svg](https://cdn.jsdelivr.net/gh/devicons/devicon/icons/linux/linux-original.svg)" alt="Linux" width="50" height="50"/\>
\</div\>

-----

## **🎯 Objetivos**

  * Criar uma estrutura de pastas específica.
  * Criar arquivos vazios.
  * Copiar e mover arquivos e diretórios.
  * Remover arquivos e diretórios.

-----

## **🏗️ Arquitetura do Sistema de Arquivos**

(Inserir imagem)

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

### **2. Criando a Estrutura de Pastas**

Reconstruí a estrutura de diretórios e arquivos da empresa `CompanyA` usando os comandos `mkdir` e `touch`.

  * **Criei os diretórios principais**:

    ```bash
    mkdir CompanyA
    cd CompanyA
    mkdir Finance HR Management
    ```

  * **Criei os arquivos dentro de `HR`**:

    ```bash
    cd HR
    touch Assessments.csv TrialPeriod.csv
    ```

  * **Criei os arquivos dentro de `Finance`**:

    ```bash
    cd ../Finance
    touch Salary.csv ProfitAndLossStatements.csv
    ```

  * **Criei os arquivos dentro de `Management`**:

    ```bash
    cd ..
    touch Management/Managers.csv Management/Schedule.csv
    ```

  * **Validei a estrutura completa**:
    Usei `ls -laR` para listar todos os arquivos e diretórios recursivamente, confirmando que a estrutura foi criada corretamente.

-----

### **3. Deletando e Reorganizando Pastas**

## **🏗️Arquitetura Reorganizada do Sistema de Arquivos**

(inserir imagem)

Fui encarregado de reorganizar a estrutura, o que me forçou a usar comandos mais avançados de cópia, movimento e deleção.

  * **Copiei a pasta `Finance` para dentro de `HR`**:

    ```bash
    cp -r Finance HR
    ```

    O comando `cp -r` foi essencial para copiar a pasta e todo o seu conteúdo recursivamente.

  * **Removi a pasta `Finance` original**:
    Tentei usar `rmdir Finance`, mas falhou, pois a pasta não estava vazia. Entendi que `rmdir` só funciona para diretórios vazios. A solução foi:

    ```bash
    rm Finance/*
    rmdir Finance
    ```

    Ou usar o comando `rm -r Finance` para remover de forma recursiva.

  * **Movi a pasta `Management`**:
    Movi a pasta inteira para dentro de `HR` usando o comando `mv`.

    ```bash
    mv Management HR
    ```

  * **Criei uma nova pasta e movi arquivos**:
    Naveguei para a pasta `HR`, criei o diretório `Employees` e movi dois arquivos para dentro dele.

    ```bash
    cd HR
    mkdir Employees
    mv Assessments.csv TrialPeriod.csv Employees
    ```

-----

## **📈 Conclusão**

Este laboratório foi fundamental para solidificar meu conhecimento sobre a manipulação do sistema de arquivos no Linux. Aprendi a importância de comandos como `mkdir`, `touch`, `cp`, `mv` e `rm`, além das diferenças entre `rm` e `rmdir`. Agora me sinto mais confiante para organizar e gerenciar arquivos e diretórios diretamente do terminal.
