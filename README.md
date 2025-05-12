# 🧠 Treinamento Git & GitHub

# 1. O que é Git?

**Git** é um sistema de controle de versão distribuído, criado por Linus Torvalds em 2005.  
Ele permite que múltiplos desenvolvedores trabalhem juntos de forma organizada, mantendo um histórico completo de todas as alterações realizadas em um projeto.

### Para que serve?

- Guardar o histórico de versões de arquivos
- Permitir colaboração segura e eficiente em equipe
- Facilitar o backup e a recuperação de qualquer versão do projeto
- Trabalhar de forma sincronizada mesmo quando offline

---

# 2. Vantagens do Git

- Histórico completo e detalhado das alterações
- Possibilidade de reverter qualquer erro facilmente
- Colaboração eficiente: várias pessoas trabalhando simultaneamente
- Funcionamento offline (não depende da internet para versionar)
- Integração facilitada com ferramentas de integração contínua (CI/CD)

---

# 3. Git x GitHub

| Git            | GitHub                                |
|----------------|---------------------------------------|
| Ferramenta local de controle de versão  | Plataforma para hospedagem de código    |
| Comandos via terminal/linha de comando  | Interface web para colaboração          |
| Funciona offline                        | Depende de internet/armazenamento em nuvem |

---

# 4. Como o Git funciona: Visão Macro

O fluxo de trabalho no Git envolve basicamente três áreas:

1. **Working Directory (Diretório de Trabalho):**  
   Onde você edita e cria arquivos normalmente no seu computador.

2. **Staging Area (Índice de Preparação):**  
   Onde você indica quais arquivos e alterações vão ser salvos no próximo commit.

3. **Local Repository (Repositório Local):**  
   Onde os commits ficam salvos no seu computador.

4. **Remote Repository (Repositório Remoto):**  
   Onde o código fica armazenado em plataformas como o GitHub para colaboração, backup e publicação.

**Fluxo resumido:**  
`Working Directory` → `git add` → `Staging Area` → `git commit` → `Local Repository` → `git push` → `Remote Repository (GitHub)`

---

# 5. Comandos Básicos do Git

```bash
git init                     # Inicializa um repositório Git
git status                   # Mostra o estado dos arquivos (modificados, prontos para commit, etc)
git add arquivo.txt          # Adiciona arquivo ao stage (preparação para commit)
git commit -m "mensagem"     # Realiza o commit (salva alteração) com mensagem
git log                      # Mostra o histórico dos commits
git diff                     # Compara versões/mostra diferenças
git rm arquivo.txt           # Remove arquivo versionado do repositório

# Reverter mudanças:
git revert <commit>          # Cria novo commit que desfaz as alterações de outro
git reset --hard <commit>    # Volta para o estado de um commit anterior (CUIDADO: PERDE ALTERAÇÕES)
```
---

# 6. Exemplo Prático Completo

```bash
# Criação do repositório
mkdir exemplo-git
cd exemplo-git
git init

# Criando e versionando arquivo
echo "Versão 1" > arquivo.txt
git add arquivo.txt
git commit -m "Versão inicial"

# Alterando e versionando novamente
echo "Nova linha" >> arquivo.txt
git add arquivo.txt
git commit -m "Adiciona nova linha"

# Consultando histórico e diferenças
git log --oneline
git diff HEAD~1 HEAD -- arquivo.txt
```
---

# 7. Integrando com o GitHub
Passo a passo para publicar no GitHub:
Crie um repositório no GitHub

Acesse: 
github.com
Dê um nome e clique em “Create repository”
Conecte o repositório local ao remoto do GitHub

```bash
git remote add origin https://github.com/SEU_USUARIO/SEU_REPOSITORIO.git
git branch -M main           # (opcional) Garante que o branch usado é o main
git push -u origin main      # Envia para o GitHub
```

Fluxo Típico de Alterações

```bash
# Editar arquivo localmente
echo "modificação" >> arquivo.txt

# Adicionar e commitar localmente
git add arquivo.txt
git commit -m "Descrição da modificação"

# Enviar para o GitHub
git push origin main
```

---

# 8. Visualizando Histórico e Diferenças

```bash
git log --oneline           # Exibe histórico resumido dos commits
git log --graph --all       # Exibe histórico em formato de árvore
git diff HEAD~1 HEAD        # Compara penúltima e última versão dos arquivos
```

---

# 9. Desfazendo Alterações e Commits

```bash
git restore arquivo.txt         # Restaura arquivo alterado para a última versão commitada
git reset --soft HEAD~1         # Remove o último commit, mas mantém as mudanças para um novo commit
git reset --hard HEAD~1         # Remove último commit e descarta alterações (perigoso!)
git revert <commit>             # Cria um commit que desfaz o commit especificado
```

Para voltar a um commit anterior temporariamente:

```bash
git checkout COMMIT_ID       # Fica em modo 'detached HEAD'
git checkout main            # Volta para o branch principal
```

# 10. Trabalhando com Branches

**Branch** é uma ramificação da linha de desenvolvimento principal (main/master).  
Permite desenvolver funcionalidades novas, testar ideias, corrigir bugs sem impactar o código principal.

```bash
git branch                       # Lista todas as branches
git checkout -b nova-branch      # Cria e troca para uma nova branch
git switch nome-da-branch        # Troca para uma branch existente
git merge nome-da-branch         # Mescla uma branch à branch atual
git branch -d nome-da-branch     # Exclui uma branch localmente
```
---

# 11. Principais Problemas e Soluções
Conflito de Merge:
Quando duas pessoas alteram a mesma linha de um arquivo em branches diferentes, o Git exige que você resolva o conflito manualmente.

```bash
# Após o conflito, edite o arquivo, depois:
git add arquivo-resolvido.txt
git commit
```

## Commit errado:
Use git revert ou, caso ainda não tenha enviado para o remoto, git reset --soft ou git commit --amend para reescrever a mensagem/corrigir.

## Perdi meu trabalho!
Use git reflog para ver todo o histórico de HEADs e restaurar o estado anterior se necessário.

---

# 12. Exercício Prático Recomendado
- Criar um novo repositório local (git init)
- Adicionar um arquivo e realizar o commit inicial
- Fazer uma alteração e realizar novo commit
- Criar uma nova branch, fazer uma modificação nela e commitar
- Voltar ao branch principal (main), mesclar a nova branch
- Subir o projeto para um repositório no GitHub

---

# 13. Onde buscar ajuda e recursos complementares

- http://git-scm.com
- http://docs.github.com
- http://pt.stackoverflow.com
- http://dev.to

---

# 14. Resumo Rápido: Comandos Mais Importantes

| COMANDO              | O QUE FAZ                             |
|----------------------|---------------------------------------|
| git init	           |Inicia um novo repositório|
| git status	       |Verifica estado atual|
| git add arquivo.txt  |Adiciona arquivo ao staging|
| git commit -m "msg"  |Realiza commit com mensagem|
| git log --oneline	   |Histórico resumido|
| git diff             |Diferenças entre versões|
| git branch           |Lista branches|
| git checkout -b nome |Cria e troca para nova branch|
| git merge nome       |Junta branch à branch atual|
| git push/pull origin main |Envia/recebe alterações do repositório remoto|
| git remote add origin URL |Conecta repositório local ao repositório remoto (GitHub)|


---

# 15. Dicas Finais
- Use nomes de commit claros e descritivos.
- Faça commits pequenos e frequentes.
- Sempre confira o status antes de enviar alterações para o repositório remoto.
- Teste comandos em projetos de teste antes de usar em projetos importantes.
- Explore interfaces gráficas para Git como GitHub Desktop, Tortoise GIT ou plugins de IDE.
