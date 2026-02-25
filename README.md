# 📌 Atividade Prática: Integração Contínua (CI) e Entrega Contínua (CD) com GitHub Pages

## 🎯 **Objetivo**
Esta atividade tem como objetivo proporcionar experiência prática com os conceitos de **Integração Contínua (CI)** e **Entrega Contínua (CD)**, utilizando **GitHub** como ferramenta de versionamento e **GitHub Pages** como ambiente de hospedagem.

> **IMPORTANTE:** Para esta atividade, será necessário pelo menos **um outro colaborador**. Todos os integrantes do grupo devem **realizar e documentar a execução das tarefas**.

## 📂 **Estrutura do Repositório**

Este repositório já contém todos os arquivos necessários para a execução da atividade:

| Arquivo | Descrição |
|---|---|
| `index.html` | Página HTML inicial do projeto (será personalizada por você) |
| `contribuicao.html` | Trecho HTML de referência para a contribuição do colaborador |
| `.github/workflows/deploy.yml` | Workflow do GitHub Actions para deploy automático no GitHub Pages |
| `README.md` | Este roteiro de atividade |

> **Você NÃO precisa copiar código de blocos de texto.** Todos os arquivos necessários já estão neste repositório. Basta fazer um **fork** e trabalhar a partir dele.

---

## 📚 **Conceitos Fundamentais**

### 🔸 **Fork**
Um **fork** é uma cópia completa de um repositório para a sua própria conta no GitHub. Diferente de um clone (que é local), o fork cria um repositório independente no GitHub ligado ao repositório original. Isso permite que você experimente livremente sem afetar o projeto original.

**Analogia:** É como tirar uma fotocópia de um documento — você pode rabiscar e modificar à vontade sem alterar o original.

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

---

### 🔹 **FASE 1: Fork e Configuração Inicial**

#### **1.1 Fazendo o Fork do Repositório**
1. Faça login na sua conta do **GitHub** (github.com)
2. Acesse o repositório original deste projeto (URL fornecida pelo professor)
3. Clique no botão **"Fork"** (canto superior direito)
4. Na tela de criação do fork:
   - **Owner:** Sua conta pessoal
   - **Repository name:** Pode manter o nome original ou renomear
   - Mantenha marcada a opção **"Copy the `main` branch only"**
5. Clique em **"Create fork"**

> O fork criará uma cópia completa do repositório na sua conta, incluindo o arquivo `index.html`, o workflow de deploy e este roteiro.

#### **1.2 Configuração de Colaboradores**
1. No **seu fork**, vá em **Settings** → **Collaborators** → **Add people**
2. Digite o username ou email do(s) colaborador(es)
3. O colaborador receberá um convite por email que deve aceitar

### ✅ **PONTO DE VERIFICAÇÃO #2**
> **Confirme que:**
> - [ ] O fork do repositório foi criado na sua conta com sucesso
> - [ ] Está configurado como público
> - [ ] O(s) colaborador(es) receberam e aceitaram o convite
> - [ ] O repositório contém os arquivos: `index.html`, `.github/workflows/deploy.yml`, `contribuicao.html`
> - [ ] Você copiou a URL do seu fork (formato: `https://github.com/seu-usuario/nome-do-repo.git`)

---

### 🔹 **FASE 2: Clonando e Personalizando o Projeto**

#### **2.1 Clonando o Repositório (Fork)**
```bash
# Clone o seu fork (substitua pela URL do SEU fork)
git clone https://github.com/seu-usuario/nome-do-repo.git

# Entre na pasta do projeto
cd nome-do-repo
```

#### **2.2 Personalizando a Página Inicial**
O arquivo `index.html` já existe no repositório. Abra-o no seu editor de texto e personalize:

1. Substitua `[Seu nome aqui]` pelo seu nome real
2. Substitua `[Nome do colaborador]` pelo nome do seu colaborador

#### **2.3 Enviando as Alterações para o GitHub**
```bash
# Adicione as mudanças ao stage
git add index.html

# Faça o commit com mensagem descritiva
git commit -m "feat: personaliza página inicial com nomes da equipe"

# Envie para o GitHub
git push origin main
```

### ✅ **PONTO DE VERIFICAÇÃO #3**
> **Verifique:**
> - [ ] O comando `git status` mostra "working tree clean"
> - [ ] No GitHub, o arquivo `index.html` mostra os nomes atualizados
> - [ ] O commit aparece no histórico com seu nome configurado corretamente

---

### 🔹 **FASE 3: Configuração do GitHub Pages**

#### **3.1 Ativando o GitHub Pages**
1. No seu fork no GitHub, vá em **Settings** → **Pages** (menu lateral esquerdo)
2. Em **"Source"**, selecione **"GitHub Actions"**
3. Pronto! O workflow `.github/workflows/deploy.yml` (que já está no repositório) será usado automaticamente

> **Nota:** O arquivo de workflow já está configurado no repositório. Você não precisa criar nenhum arquivo adicional.

#### **3.2 Disparando o Primeiro Deploy**
O deploy será disparado automaticamente sempre que houver um push no branch `main`. Como você já fez um push na FASE 2, o deploy já deve estar em andamento.

1. Vá na aba **"Actions"** do seu repositório
2. Verifique se o workflow **"Deploy to GitHub Pages"** está em execução ou já completou
3. Se não houver nenhuma execução, faça um push qualquer no `main` para disparar

#### **3.3 Verificando o Deploy**
1. Aguarde o workflow completar (1-3 minutos)
2. Vá em **Settings** → **Pages** novamente
3. Você verá a URL do seu site no formato: `https://seu-usuario.github.io/nome-do-repo/`
4. Abra a URL em um navegador para verificar se está funcionando

### ✅ **PONTO DE VERIFICAÇÃO #4**
> **Confirme que:**
> - [ ] O GitHub Pages está ativado com source "GitHub Actions"
> - [ ] O workflow de deploy executou com sucesso (check verde ✅ na aba Actions)
> - [ ] O site está acessível pela URL do GitHub Pages
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
# Clone o fork (se ainda não tiver) — use a URL do fork do colega
git clone https://github.com/usuario-principal/nome-do-repo.git
cd nome-do-repo

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
O colaborador deve modificar o `index.html`, adicionando o conteúdo do arquivo `contribuicao.html` (que já está no repositório) **antes** do fechamento `</body>`.

**Passos:**
1. Abra o arquivo `contribuicao.html` que já está no repositório
2. Copie o conteúdo HTML dele
3. Abra o arquivo `index.html`
4. Cole o conteúdo copiado **antes** da tag `</body>`
5. Personalize substituindo `[Nome do Colaborador]` pelo nome real

> **Dica:** O arquivo `contribuicao.html` serve apenas como referência/modelo. O conteúdo dele deve ser inserido dentro do `index.html`.

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
1. No GitHub, vá para a página do repositório (fork)
2. Você verá uma notificação sobre o push recente no `develop`
3. Clique em **"Compare & pull request"**
4. Ou vá em **"Pull requests"** → **"New pull request"**

> **⚠️ Atenção:** Certifique-se de que o PR é para o **seu fork** (base: `seu-usuario/nome-do-repo` branch `main`) e **não** para o repositório original do professor.

#### **6.2 Configurando o PR**
- **Base repository:** seu-usuario/nome-do-repo (seu fork)
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
   - Configuração do GitHub Pages
   - Upload do artefato
   - Deploy para GitHub Pages

#### **7.2 Verificando o Site Atualizado**
1. Aguarde o workflow completar (1-3 minutos)
2. Acesse novamente a URL do GitHub Pages: `https://seu-usuario.github.io/nome-do-repo/`
3. Use **Ctrl+F5** para forçar atualização do cache
4. Confirme que as novas seções aparecem

### ✅ **PONTO DE VERIFICAÇÃO #8 - FINAL**
> **Validação completa:**
> - [ ] O site no GitHub Pages mostra a versão atualizada
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
3. Comum: arquivo YAML mal formatado ou permissões insuficientes
4. Verifique o arquivo `.github/workflows/deploy.yml` no repositório
5. Verifique se em **Settings → Pages** o source está configurado como **"GitHub Actions"**

### 🔧 **Problema 3: Site não atualiza no GitHub Pages**
**Sintoma:** Mudanças não aparecem após deploy

**Soluções:**
1. Limpe o cache do navegador (Ctrl+Shift+Del)
2. Use modo anônimo/privado
3. Verifique se o deploy realmente completou na aba Actions
4. Aguarde alguns minutos — o GitHub Pages pode levar até 10 minutos para propagar

### 🔧 **Problema 4: GitHub Pages mostra erro 404**
**Sintoma:** Página não encontrada ao acessar a URL

**Soluções:**
1. Verifique se o GitHub Pages está ativado em **Settings → Pages**
2. Confirme que o source é **"GitHub Actions"**
3. Verifique se o arquivo `index.html` está na raiz do repositório
4. Aguarde o workflow concluir e tente novamente

### 🔧 **Problema 5: PR vai para o repositório original ao invés do fork**
**Sintoma:** O Pull Request é direcionado ao repositório do professor

**Solução:**
1. Na tela de criação do PR, altere o **"base repository"** para o seu fork
2. Confirme que tanto o base quanto o compare apontam para **seu fork**

---

## 📄 **Entrega da Atividade**

### **Instruções para Entrega via Teams**

Cada integrante do grupo deve enviar **via Microsoft Teams** os seguintes artefatos:

#### **Artefatos Obrigatórios:**

1. **Link do repositório (fork) no GitHub**
   - Formato: `https://github.com/seu-usuario/nome-do-repo`
   - O repositório deve estar público

2. **Link do site publicado no GitHub Pages**
   - Formato: `https://seu-usuario.github.io/nome-do-repo/`
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
- [Forking a Repository](https://docs.github.com/pt/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo) - Guia sobre Forks

### **CI/CD e DevOps**
- [GitHub Actions Documentation](https://docs.github.com/pt/actions)
- [GitHub Pages Documentation](https://docs.github.com/pt/pages)
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
4. **Teste localmente** antes de fazer push (basta abrir o `index.html` no navegador)
5. **Comunique-se** com sua equipe constantemente
6. **Documente** suas decisões e problemas encontrados
7. **Explore** os logs e ferramentas - não tenha medo de experimentar
8. **Verifique o base repository** ao criar PRs em forks — aponte para o seu fork, não o original

---

**Boa sorte e bom aprendizado! 🚀**

