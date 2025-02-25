# 📌 Atividade Prática: Integração Contínua (CI) e Entrega Contínua (CD) com GitHub e Azure

## 🎯 **Objetivo**
Esta atividade tem como objetivo proporcionar experiência prática com os conceitos de **Integração Contínua (CI)** e **Entrega Contínua (CD)**, utilizando **GitHub** como ferramenta de versionamento e **Azure Static Web Apps** como ambiente de hospedagem.

> **IMPORTANTE:** Para esta atividade, será necessário pelo menos **um outro colaborador**. Todos os integrantes do grupo devem **realizar e documentar a execução das tarefas**.

---

## 🛠 **Passo a Passo**
### 🔹 **1. Configuração inicial no GitHub**
1. Faça login na sua conta do **GitHub** e crie um **repositório público** chamado `CI_CD`.
2. Acesse a seção de **Configurações** do repositório e **convide** o(s) outro(s) colaborador(es) para ter acesso ao projeto.

### 🔹 **2. Primeira implementação do código**
3. Clone o repositório recém-criado para sua máquina local:
   ```bash
   git clone https://github.com/seu-usuario/CI_CD.git
   ```
4. Navegue até a pasta do repositório e crie um arquivo `index.html` com um conteúdo básico, por exemplo:
   ```html
   <!DOCTYPE html>
   <html lang="pt-BR">
   <head>
       <meta charset="UTF-8">
       <meta name="viewport" content="width=device-width, initial-scale=1.0">
       <title>Meu Site CI/CD</title>
   </head>
   <body>
       <h1>Deploy Automatizado com GitHub Actions e Azure</h1>
   </body>
   </html>
   ```
5. Adicione o arquivo ao repositório, faça o commit e envie as alterações para o GitHub:
   ```bash
   git add index.html
   git commit -m "Adicionando index.html inicial"
   git push origin main
   ```

### 🔹 **3. Configuração do deploy automático no Azure**
6. Acesse o portal do **Azure** ([portal.azure.com](https://portal.azure.com)) e entre com seu e-mail institucional.
7. No menu de serviços, selecione **Static Web Apps** e clique em **Criar**.
8. Escolha o **GitHub** como fonte do repositório e conecte ao branch `main` do repositório `CI_CD`.
9. Finalize a criação do recurso e aguarde o **deploy automático**.
10. **Verifique se o site está acessível**, acessando a URL gerada pelo Azure.

### 🔹 **4. Fluxo de trabalho com branches**
11. No ambiente do GitHub, crie um **novo branch** chamado `develop`:
    ```bash
    git checkout -b develop
    git push origin develop
    ```
12. Compartilhe o repositório com seu colaborador. Ele deverá clonar o projeto e fazer **checkout** no branch `develop`:
    ```bash
    git clone https://github.com/seu-usuario/CI_CD.git
    cd CI_CD
    git checkout develop
    ```

### 🔹 **5. Implementação de mudanças colaborativas**
13. O colaborador deve **modificar o arquivo `index.html`**, por exemplo, alterando o título ou adicionando novos elementos:
    ```html
    <h2>Modificação feita pelo colaborador</h2>
    ```
14. Ele deve **fazer commit e enviar as mudanças**:
    ```bash
    git add index.html
    git commit -m "Alteração no index pelo colaborador"
    git push origin develop
    ```

### 🔹 **6. Processo de Pull Request e Merge**
15. No **GitHub**, crie um **Pull Request (PR)** para mesclar as alterações do branch `develop` no `main`.
16. Faça a **revisão do código** e **aprove o merge**.
17. Verifique se os processos de **Integração/Entrega Contínua** foram executados automaticamente.
18. **Acesse novamente o site no Azure** para confirmar que a nova versão do `index.html` está publicada.

---

## 📄 **Entrega da Atividade**
Cada integrante do grupo deve gerar um documento (`.docx` ou `.pdf`) contendo as seguintes evidências:

1. **Link do repositório no GitHub**.
2. **Link do site publicado no Azure**.
3. **Captura de tela (screenshot) dos commits no branch `develop`**, mostrando as contribuições do(s) colaborador(es).
4. **Captura de tela do GitHub Actions**, evidenciando a execução dos workflows de CI/CD.

---

## 🔗 **Referências**
- [Fluxo de Trabalho GitFlow](https://www.atlassian.com/br/git/tutorials/comparing-workflows/gitflow-workflow)  
- [Documentação do Azure Static Web Apps](https://docs.microsoft.com/pt-br/azure/static-web-apps/)  


