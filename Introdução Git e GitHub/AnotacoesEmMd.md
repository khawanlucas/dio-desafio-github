## Noções básicas do Git

- Commit
    É a captura ou marco do estado momentâneo do projeto contendo as alterações feitas. É vinculado com uma mensagem descritiva.
- Arquivos
    Possuem três estados: modificado, preparado e confirmado. Quando um arquivo é modificado, ele não pode fazer parte de um commit. Deve-se antes preparar os aquivos, ou seja, adicioná-los na área de preparação. Essa área inclui todas as alterações feitas que serão salvas no próximo commit. A partir dessa etapa, os arquivos serão empacotados em um commit.
- Branches (Ramificações)
    Uma forma de obter uma versão do código que pode ser alterado sem que o arquivo principal sofra alterações. Os branches funcionam como ponteiros que apontam para a ramificação do trabalho em andamento, gerenciando a separação.
    Dessa forma, o desenvolvedor pode manter um ramo para processos mais demorados e longos, enquanto trabalha no desenvolvimento de outras atividades mais urgentes.
    Quando trabalhamos com o Git, a plataforma cria automaticamente uma branch padrão chamado de **main** ou **master**.
- Chave SSH
    Protocolo de rede que possibilita que sua máquina local e o servidor remoto se conectem de forma segura e criptografada por meio da internet. 
    Existe uma chave pública e uma privada (equivalente a uma senha).


## Linhas de comando

# Configuração

_Níveis de projeto_
```
--global => configurações do usuário
--system => configurações do sistema
--local => configurações de repositório específico que vc se encontra
```

_Em relação ao nome e e-mail_
```
git config --global user.name "SEU NOME" = definir seu nome
git config --global user.email "SEU E-MAIL" = definir seu e-mail
git config user.name = retorna o nome
git config user.email = retorna o e-mail
```

_Em relação à Branch padrão_
```
git config init.defaultBranch = Retorna o nome da Branch padrão
git config --global init.defaultBranch NOME DA BRANCH = alterar o nome da Branch
```

_Em relação à credenciais_
```
git config --global credential.helper cache = salva suas credenciais temporariamente na máquina
git config --global credential.helper store = salva suas credenciais permanentemente na máquina
git config --global credential.helper = retorna o tipo de credencial (cache ou store) que está configurado na máquina
```

_Em relação à lista de configuração_
```
git config --list = retorna uma lista das configurações
git config --list --show-origin = mostra o caminho onde está armazenado cada arquivo da lista de configuração
```


# Chave SSH

```
cd ~/.ssh   (mudança de diretório)
ls                          = retorna as chaves pública e privada
```


# Criar e clonar repositórios locais

_Clonar_
```
git clone URL DO REPOSITÓRIO = clona o repositório do GitHub para a máquina local
git clone URL DO REPOSITÓRIO NOME ESCOLHIDO = se quiser clonar com outro nome
```

_Criar e excluir_
```
mkdir NOME DO DIRETÓRIO NOVO = cria um diretório

git init = inicia um repositório git

rm -rf .git = remove recursivamente e à força o diretório .git

touch NOME DO ARQUIVO.TIPO DO ARQUIVO = criar um arquivo vazio
```

_Em relação ao repositório remoto_
```
git remote -v = retorna os repositórios remotos vinculados

git remote add origin* URL = vincular o repositório remoto
*nome do repositório remoto (geralmente origin)

git push = "empurra" as alterações do repositório local para o remoto
git push -u origin NOME DA BRANCH = primeiro push da branch
```

_Em relação à área de preparação_
```
git add NOME DO ARQUIVO= adiciona o arquivo na área de preparação
git add . = adiciona todos os arquivos para a área de preparação

git status = mostra os status da área de trabalho e de preparação (index) e o estado dos arquivos
```

_Commit_
```
git commit -m"MENSAGEM" = grava as alterações do repositório com uma mensagem
git commit --amend -m"NOVA MENSAGEM" = grava uma nova mensagem do último commit
git commit --amend = abre o editor para alterar a mensagem

git log = exibe o histórico de commits feitos
```


_Restore e Reset_
```
git restore ARQUIVO = restauta a última versão do arquivo

git reset = reseta o commit selecionado
git reset --soft HASH DO COMMIT = preserva todas as mudanças entre a última atualização e o commit selecionado e os adiciona à área de preparação
git reset --mixed HASH DO COMMIT = preserva todas as mudanças entre a ultima atualização e o commit selecionado como arquivos desconhecidos
git reset --hard HASH DO COMMIT = descarta permanentemente todas as mudanças feitas entre a última atualização e o commit selecionado

git reset NOME DO ARQUIVO = retira o arquivo que está na área de preparação
git restore --stage NOME DO ARQUIVO = mesma função
```

_Gitignore e Gitkeep_
```
echo PASTA/ > .gitignore = faz com que a pasta seja ignorada

touch PASTA/.gitkeep = criação de arquivo gitkeep
gitkeep: convenção para que o git reconheça o diretório vazio
```

# Branches

_Comandos principais_
```
git checkout -b NOME DA NOVA BRANCH = além de criar uma nova branch, troca o ponteiro da branch atual para a branch criada

git checkout main = passa o ponteiro para a branch principal

git branch -v = retorna o último commit de cada branch

git merge NOME DA BRANCH = mescla a branch principal com a branch citada

git branch = lista as branches do diretório

git branch -d NOME DA BRANCH = excluí a branch
```

_Outros comandos relacionados_
```
git clone URL --branch NOME DA BRANCH --single-branch = clona apenas uma branch

git fetch = baixar uma alteração do diretório remoto sem mesclar com o diretório local

git merge NOME DA BRANCH = mescla as alterações da branch citada para a atual

git diff NOME DA BRANCH NOME DE OUTRA BRANCH = ver a diferença entre uma branch e outra
git diff main origin/main = diferença entre o main local e o main remoto
```

_Git Stash_
```
git stash = arquivar uma modificação sem que ela esteja pronta para commit ou para a criação de uma nova branch

git stash list = lista de modificações arquivadas

git stash pop = traz as modificações de volta, mas as retira do stash

git stash apply = traz as modificações de volta e as mantêm no stash
```

# Outros comandos importantes

```
cat ARQUIVO = exibe o conteúdo de um determinado arquivo
cat .git-credentials = retorna o TOKEN que foi utilizado

cd = Change Directory; Troca de diretório 
cd .. = volta uma casa
```

## Referências e fontes

- [Documentação Git](https://git-scm.com/docs)
- [Git Commit](https://www.atlassian.com/br/git/tutorials/saving-changes/git-commit)
- [O que é Git](https://learn.microsoft.com/pt-br/devops/develop/git/what-is-git)
- [Git & Github: O que é? Por que? Como iniciar?](https://blog.rocketseat.com.br/iniciando-com-git-github/)