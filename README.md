# 📌 Atividade Prática: Integração Contínua (CI) e Entrega Contínua (CD) com GitHub e Azure

## 🎯 **Objetivo**
Esta atividade tem como objetivo proporcionar experiência prática com os conceitos de **Integração Contínua (CI)** e **Entrega Contínua (CD)**, utilizando **GitHub** como ferramenta de versionamento e **Azure Static Web Apps** como ambiente de hospedagem.

> **IMPORTANTE:** Para esta atividade, será necessário pelo menos **um outro colaborador**. Todos os integrantes do grupo devem **realizar e documentar a execução das tarefas**.

---

## 📚 **Conceitos Fundamentais**

### 🔸 **Branch**
Um **branch** (ramificação) é uma linha independente de desenvolvimento no Git. Permite que você trabalhe em novas funcionalidades ou correções sem afetar o código principal (geralmente no branch `main` ou `master`). Cada branch mantém seu próprio histórico de commits até ser mesclado (merge) com outro branch.

**Analogia:** Imagine um branch como uma cópia temporária do seu projeto onde você pode experimentar mudanças sem "estragar" a versão principal.

### 🔸 **Pull Request (PR)**
Um **Pull Request** é uma proposta de mudança submetida ao repositório. É o mecanismo pelo qual você solicita que suas alterações em um branch sejam revisadas e incorporadas (merged) em outro branch. O PR permite:
- Revisão de código por outros desenvolvedores
- Discussão sobre as mudanças propostas
- Execução automática de testes (CI)
- Aprovação antes do merge

**Analogia:** É como enviar um rascunho para revisão antes de publicar a versão final de um documento.

### 📖 **Leituras Complementares sobre Git**
- [Pro Git Book - Branches](https://git-scm.com/book/pt-br/v2/Branches-no-Git-Branches-em-poucas-palavras)
- [GitHub Flow - Guia Prático](https://docs.github.com/pt/get-started/quickstart/github-flow)
- [Atlassian - Pull Requests](https://www.atlassian.com/br/git/tutorials/making-a-pull-request)

---

## 🛠 **Passo a Passo Detalhado**

### 🔹 **FASE 0: Configuração do Git (ESSENCIAL)**

#### **0.1 Configuração de Identidade do Git**
Antes de começar a trabalhar com Git, você **DEVE** configurar sua identidade. O Git precisa saber quem está fazendo os commits.

```bash
# Configuração LOCAL (apenas para este repositório)
git config user.name "Seu Nome Completo"
git config user.email "seu.email@exemplo.com"

# OU Configuração GLOBAL (para todos os repositórios no seu computador)
git config --global user.name "Seu Nome Completo"
git config --global user.email "seu.email@exemplo.com"
```

#### **⚠️ Diferença entre configuração LOCAL vs GLOBAL:**
- **Sem --global:** A configuração vale apenas para o repositório atual. Útil quando você trabalha com diferentes identidades (pessoal vs trabalho).
- **Com --global:** A configuração vale para TODOS os repositórios Git no seu computador. Mais prático para uso pessoal.

#### **0.2 Verificando suas configurações**
```bash
# Ver configurações atuais
git config --list

# Ver apenas nome e email
git config user.name
git config user.email
```

### ✅ **PONTO DE VERIFICAÇÃO #1**
> **Antes de prosseguir, confirme:**
> - [ ] Configurou user.name e user.email no Git
> - [ ] Testou com `git config user.name` e viu seu nome correto
> - [ ] Tem uma conta ativa no GitHub
> - [ ] Tem acesso ao portal Azure com email institucional

---

### 🔹 **FASE 1: Configuração Inicial no GitHub**

#### **1.1 Criação do Repositório**
1. Faça login na sua conta do **GitHub** (github.com)
2. Clique no botão **"New"** ou **"+"** → **"New repository"**
3. Configure o repositório:
   - **Repository name:** `CI_CD`
   - **Visibility:** Public
   - Inicialize com README
4. Clique em **"Create repository"**

#### **1.2 Configuração de Colaboradores**
1. No repositório criado, vá em **Settings** → **Manage access** → **Invite a collaborator**
2. Digite o username ou email do(s) colaborador(es)
3. O colaborador receberá um convite por email que deve aceitar

### ✅ **PONTO DE VERIFICAÇÃO #2**
> **Confirme que:**
> - [ ] O repositório `CI_CD` foi criado com sucesso
> - [ ] Está configurado como público
> - [ ] O(s) colaborador(es) receberam e aceitaram o convite
> - [ ] Você copiou a URL do repositório (formato: `https://github.com/seu-usuario/CI_CD.git`)

---

### 🔹 **FASE 2: Primeira Implementação do Código**

#### **2.1 Clonando o Repositório**
```bash
# Clone o repositório vazio
git clone https://github.com/seu-usuario/CI_CD.git

# Entre na pasta do projeto
cd CI_CD
```

#### **2.2 Criando a Estrutura Inicial**
Crie um arquivo `index.html` com o seguinte conteúdo:

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CI/CD - Prática de Engenharia de Software</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            max-width: 800px;
            margin: 0 auto;
            padding: 20px;
            background-color: #f5f5f5;
        }
        h1 {
            color: #333;
            border-bottom: 2px solid #007acc;
            padding-bottom: 10px;
        }
        .info {
            background-color: white;
            padding: 15px;
            border-radius: 5px;
            margin: 20px 0;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
        }
        .timestamp {
            color: #666;
            font-style: italic;
        }
    </style>
</head>
<body>
    <h1>🚀 Deploy Automatizado com GitHub Actions e Azure</h1>
    
    <div class="info">
        <h2>Sobre o Projeto</h2>
        <p>Este é um projeto de demonstração de CI/CD para a disciplina de Engenharia de Software.</p>
        <p class="timestamp">Versão inicial - Data: <script>document.write(new Date().toLocaleDateString('pt-BR'));</script></p>
    </div>
    
    <div class="info">
        <h2>Equipe</h2>
        <ul>
            <li>Desenvolvedor 1: [Seu nome aqui]</li>
            <li>Desenvolvedor 2: [Nome do colaborador]</li>
        </ul>
    </div>
</body>
</html>
```

#### **2.3 Enviando para o GitHub**
```bash
# Adicione o arquivo ao stage
git add index.html

# Faça o commit com mensagem descritiva
git commit -m "feat: adiciona página inicial do projeto CI/CD"

# Envie para o GitHub
git push origin main
```

### ✅ **PONTO DE VERIFICAÇÃO #3**
> **Verifique:**
> - [ ]**** O comando `git status` mostra "working tree clean"
> - [ ] No GitHub, o arquivo index.html aparece no repositório
> - [ ] O commit aparece no histórico com seu nome configurado corretamente

---

### 🔹 **FASE 3: Configuração do Deploy Automático no Azure**

#### **3.1 Criando o Static Web App**
1. Acesse o portal do **Azure**: [portal.azure.com](https://portal.azure.com)
2. Entre com seu **email institucional**
3. No menu lateral ou barra de busca, procure por **"Static Web Apps"**
4. Clique em **"+ Create"** ou **"Criar"**

#### **3.2 Configuração do Recurso**
Preencha os campos:
- **Subscription:** Selecione sua assinatura
- **Resource Group:** Crie um novo grupo chamado `rg-cicd-practice`
- **Name:** `webapp-cicd-seunome` (use seu nome para evitar conflitos)
- **Region:** Brazil South (ou mais próxima)
- **Plan type:** Free
- **Source:** GitHub
- **GitHub Account:** Faça login e autorize o Azure

#### **3.3 Configuração do Deploy**
- **Organization:** Seu usuário do GitHub
- **Repository:** CI_CD
- **Branch:** main
- **Build Presets:** Custom
- **App location:** `/` (raiz)
- **Api location:** (deixe vazio)
- **Output location:** (deixe vazio)

Clique em **"Review + create"** → **"Create"**

#### **3.4 Verificando o Deploy**
1. Aguarde a criação do recurso (2-3 minutos)
2. Vá para o recurso criado
3. Na página de Overview, copie a **URL** do seu site
4. Abra a URL em um navegador para verificar se está funcionando

### ✅ **PONTO DE VERIFICAÇÃO #4**
> **Confirme que:**
> - [ ] O recurso Static Web App foi criado com sucesso
> - [ ] Um workflow do GitHub Actions foi adicionado automaticamente ao repositório
> - [ ] O site está acessível pela URL do Azure
> - [ ] A página HTML está sendo exibida corretamente

---

### 🔹 **FASE 4: Fluxo de Trabalho com Branches**

#### **4.1 Criando o Branch de Desenvolvimento**
```bash
# Certifique-se de estar no branch main atualizado
git checkout main
git pull origin main

# Crie e mude para o branch develop
git checkout -b develop

# Envie o branch para o GitHub
git push -u origin develop
```

#### **4.2 Configuração do Colaborador**
O colaborador deve executar:
```bash
# Clone o repositório (se ainda não tiver)
git clone https://github.com/usuario-principal/CI_CD.git
cd CI_CD

# Configure sua identidade (se ainda não configurou)
git config user.name "Nome do Colaborador"
git config user.email "email@colaborador.com"

# Baixe informações sobre branches remotos
git fetch origin

# Mude para o branch develop
git checkout develop
```

### ✅ **PONTO DE VERIFICAÇÃO #5**
> **Ambos devem verificar:**
> - [ ] O comando `git branch` mostra que estão no branch `develop`
> - [ ] No GitHub, o branch `develop` aparece na lista de branches
> - [ ] Ambos conseguem fazer `git pull origin develop` sem erros

---

### 🔹 **FASE 5: Implementação de Mudanças Colaborativas**

#### **5.1 Modificações pelo Colaborador**
O colaborador deve modificar o `index.html`:

```html
<!-- Adicione após a div com classe "info" da equipe -->
<div class="info">
    <h2>📝 Alterações Recentes</h2>
    <ul>
        <li>Implementação de CI/CD com GitHub Actions ✅</li>
        <li>Deploy automático no Azure Static Web Apps ✅</li>
        <li>Configuração de branch protection (em progresso)</li>
    </ul>
    <p class="timestamp">Última atualização por: [Nome do Colaborador] - <script>document.write(new Date().toLocaleString('pt-BR'));</script></p>
</div>

<div class="info">
    <h2>🔧 Tecnologias Utilizadas</h2>
    <ul>
        <li>Git & GitHub - Controle de versão</li>
        <li>GitHub Actions - Pipeline CI/CD</li>
        <li>Azure Static Web Apps - Hospedagem</li>
        <li>HTML5 & CSS3 - Front-end</li>
    </ul>
</div>
```

#### **5.2 Commit e Push das Alterações**
```bash
# Verifique as mudanças
git status
git diff

# Adicione e faça commit
git add index.html
git commit -m "feat: adiciona seções de alterações recentes e tecnologias

- Lista as implementações realizadas
- Documenta tecnologias utilizadas no projeto
- Adiciona timestamp de última atualização"

# Envie para o GitHub
git push origin develop
```

### ✅ **PONTO DE VERIFICAÇÃO #6**
> **O colaborador deve confirmar:**
> - [ ] As alterações foram commitadas com sucesso
> - [ ] O push foi realizado sem erros
> - [ ] No GitHub, o branch `develop` mostra as novas alterações

---

### 🔹 **FASE 6: Processo de Pull Request e Merge**

#### **6.1 Criando o Pull Request**
1. No GitHub, vá para a página do repositório
2. Você verá uma notificação sobre o push recente no `develop`
3. Clique em **"Compare & pull request"**
4. Ou vá em **"Pull requests"** → **"New pull request"**

#### **6.2 Configurando o PR**
- **Base branch:** main
- **Compare branch:** develop
- **Título:** "Feature: Adiciona informações do projeto e equipe"
- **Descrição:**
```markdown
## 📋 Descrição
Implementa melhorias na página inicial do projeto, incluindo:
- Seção de alterações recentes
- Lista de tecnologias utilizadas
- Timestamps de atualização

## ✅ Checklist
- [x] Código testado localmente
- [x] HTML válido
- [x] Informações da equipe atualizadas
- [ ] Revisado por outro membro da equipe

## 🔗 Issue relacionada
N/A (primeira iteração)

## 📸 Screenshots
[Adicione screenshots se relevante]
```

#### **6.3 Revisão e Aprovação**
1. Peça para outro membro da equipe revisar
2. O revisor deve:
   - Analisar o código modificado
   - Deixar comentários se necessário
   - Aprovar o PR clicando em **"Review"** → **"Approve"**

#### **6.4 Fazendo o Merge**
1. Após aprovação, clique em **"Merge pull request"**
2. Escolha **"Create a merge commit"**
3. Clique em **"Confirm merge"**
4. Opcionalmente, delete o branch `develop` no GitHub (pode recriar depois)

### ✅ **PONTO DE VERIFICAÇÃO #7**
> **Verifique após o merge:**
> - [ ] O PR foi fechado com status "Merged"
> - [ ] As GitHub Actions iniciaram automaticamente
> - [ ] O workflow de CI/CD está em execução (ícone amarelo girando)
> - [ ] Após conclusão, o workflow mostra check verde ✅

---

### 🔹 **FASE 7: Verificação Final do Deploy**

#### **7.1 Monitorando o GitHub Actions**
1. Vá em **"Actions"** no repositório
2. Você verá o workflow em execução
3. Clique nele para ver os detalhes
4. Acompanhe cada step:
   - Checkout do código
   - Setup do Node.js
   - Build do projeto
   - Deploy para Azure

#### **7.2 Verificando o Site Atualizado**
1. Aguarde o workflow completar (2-5 minutos)
2. Acesse novamente a URL do Azure
3. Use **Ctrl+F5** para forçar atualização do cache
4. Confirme que as novas seções aparecem

### ✅ **PONTO DE VERIFICAÇÃO #8 - FINAL**
> **Validação completa:**
> - [ ] O site no Azure mostra a versão atualizada
> - [ ] O histórico de commits mostra contribuições de todos
> - [ ] O GitHub Actions mostra histórico de builds bem-sucedidos
> - [ ] Todos os membros da equipe participaram ativamente

---

## 📊 **Troubleshooting - Problemas Comuns**

### 🔧 **Problema 1: Erro de permissão no push**
**Sintoma:** `error: failed to push some refs`

**Solução:**
```bash
# Atualize seu branch local primeiro
git pull origin develop
# Resolva conflitos se houver
git push origin develop
```

### 🔧 **Problema 2: GitHub Actions falhando**
**Sintoma:** Workflow com X vermelho

**Verificar:**
1. Clique no workflow falho
2. Leia os logs de erro
3. Comum: arquivo YAML mal formatado
4. Verifique o arquivo `.github/workflows/` no repositório

### 🔧 **Problema 3: Site não atualiza no Azure**
**Sintoma:** Mudanças não aparecem após deploy

**Soluções:**
1. Limpe o cache do navegador (Ctrl+Shift+Del)
2. Use modo anônimo/privado
3. Verifique se o deploy realmente completou no Actions
4. No Azure Portal, verifique os logs do Static Web App

---

## 📄 **Entrega da Atividade**

### **Instruções para Entrega via Teams**

Cada integrante do grupo deve enviar **via Microsoft Teams** os seguintes artefatos:

#### **Artefatos Obrigatórios:**

1. **Link do repositório no GitHub**
   - Formato: `https://github.com/seu-usuario/CI_CD`
   - O repositório deve estar público

2. **Link do site publicado no Azure**
   - Formato: `https://nome-do-app.azurestaticapps.net`
   - O site deve estar acessível e funcionando

3. **Captura de tela (screenshot) dos commits no branch `develop`**
   - Acesse: GitHub → Repositório → Branch `develop` → Commits
   - A captura deve mostrar claramente as contribuições do(s) colaborador(es)
   - Deve ser visível o nome de pelo menos 2 colaboradores diferentes

4. **Captura de tela do GitHub Actions**
   - Acesse: GitHub → Repositório → Actions
   - A captura deve mostrar a execução bem-sucedida dos workflows de CI/CD
   - Deve ser visível pelo menos um workflow com status verde (✅)

### **Formato de Envio:**
- Compile os 4 artefatos em um único arquivo `.pdf` ou `.docx`
- Envie através da tarefa criada no Teams até a data limite

---

## 🔗 **Referências e Material de Estudo**

### **Git e Versionamento**
- [Pro Git Book (Português)](https://git-scm.com/book/pt-br/v2) - Livro completo sobre Git
- [Git Cheat Sheet](https://training.github.com/downloads/pt_BR/github-git-cheat-sheet.pdf) - Resumo de comandos
- [Visualizing Git](https://git-school.github.io/visualizing-git/) - Ferramenta interativa
- [Learn Git Branching](https://learngitbranching.js.org/?locale=pt_BR) - Tutorial interativo

### **GitHub e Colaboração**
- [GitHub Flow](https://docs.github.com/pt/get-started/quickstart/github-flow) - Fluxo de trabalho
- [About Pull Requests](https://docs.github.com/pt/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests)
- [GitHub Skills](https://skills.github.com/) - Cursos interativos gratuitos

### **CI/CD e DevOps**
- [GitHub Actions Documentation](https://docs.github.com/pt/actions)
- [Azure Static Web Apps Docs](https://docs.microsoft.com/pt-br/azure/static-web-apps/)
- [Martin Fowler - Continuous Integration](https://martinfowler.com/articles/continuousIntegration.html)
- [The Phoenix Project](https://www.amazon.com.br/dp/B078Y98RG8/) - Livro sobre DevOps (leitura complementar)

### **Boas Práticas**
- [Conventional Commits](https://www.conventionalcommits.org/pt-br/) - Padrão para mensagens de commit
- [Semantic Versioning](https://semver.org/lang/pt-BR/) - Versionamento semântico
- [The Twelve-Factor App](https://12factor.net/pt_br/) - Metodologia para apps modernas

---

## 💡 **Dicas Extras para Sucesso**

1. **Sempre faça pull antes de push** para evitar conflitos
2. **Commits frequentes e pequenos** são melhores que commits grandes
3. **Mensagens de commit descritivas** ajudam no histórico do projeto
4. **Teste localmente** antes de fazer push
5. **Comunique-se** com sua equipe constantemente
6. **Documente** suas decisões e problemas encontrados
7. **Explore** os logs e ferramentas - não tenha medo de experimentar

---


**Boa sorte e bom aprendizado! 🚀**

*Última atualização do roteiro: {{data_atual}}*
