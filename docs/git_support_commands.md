# Principais Comandos de Suporte

<ul>
    <li><b>git init -></b> Cria repositório</li>
    <li><b>git add -></b> Adiciona arquivos</li>
    <li><b>git status -></b> Mostra mudanças que serão commitadas</li>
    <li><b>git log -></b> Mostra histórico de commits</li>
    <li><b>git commit -></b>  Cria um "checkpoint" no tempo com as mudanças feitas no arquivo</li>
    <li><b>git config --global core.editor nano -></b>  Muda o editor de texto para Nano (configuração global na sua máquina)</li>
    <li><b>git branch -></b> Lista as branches existentes</li>
    <li><b>git branch nome-da-branch -></b> Cria nova branch chamada nome-da-branch</li>
    <li><b>git checkout nome-da-branch -></b> Troca de branch</li>
    <li><b>git checkout -b nome-da-branch -></b> Cria novo branch chamado nome-da-branch e troca para o branch nome-da-branch</li>
    <li><b>git diff -></b> Vai mostrar as diferenças no arquivo em relação ao commit anterior</li>
    <li><b>git add nome-do-arquivo -></b> Irá colocar o arquivo em stage, para que as mudanças sejam commitadas</li>
    <li><b>git add -A ou git add . -></b> Adiciona todos os arquivos do projeto para stage</li>
    <li><b>git add -i -></b> Abre o menu interativo do git add (retirar arquivos de stage, colocar novos arquivos)</li>
    <li><b>git merge nome-do-branch -></b> Irá unir a nome-do-branch dentro do branch atual</li>
    <li><b>git rebase nome-do-branch -></b> Irá mudar o head do Branch atual para o HEAD do nome do branch</li>
    <li><b>git merge --abort -></b> Irá abortar a união quando tiver conflito</li>
    <li><b>git diff --check -></b> Irá te mostrar todos os arquivos e as linhas que estão com conflito</li>
    <li><b>git merge --continue -></b> Irá continuar a união depois que os conflitos forem resolvidos e os arquivos adicionados para stage</li>
    <li><b>git rebase -i HEAD~5 -></b> Irá abrir a janela de rebase interativo trazendo os últimos 5 commits. Possibilita que você mude a história do projeto</li>
    <li><b>git rebase --abort -></b> Irá abortar o rebase em caso de conflito</li>
    <li><b>git rebase --continue -></b> Irá continuar o rebase depois que os conflitos forem resolvidos e os arquivos adicionados para stage</li>
    <li><b>git remote add origin https://github.com/[usuario]/[repositorio].git -></b> Irá criar a conexão do repositório local com o repositório remoto</li>
    <li><b>git push -u origin master -></b> Irá subir o branch master para a origin (repositório remoto /GitHub)</li>
    <li><b>git push -></b> Irá subir as suas alterações do repositório local para o repositório remoto</li>
    <li><b>git pull -></b> Irá baixar as alterações do repositório remoto para o local</li>
    <li><b>git stash save nome-do-stash -></b> Irá salvar as suas mudanças sem commitar</li>
    <li><b>git stash list -></b> Irá listar os stashs disponíves</li>
    <li><b>git stash apply indice-do-stash -></b> Irá Aplicar as mudanças salvas no seu branch atual</li>
    <li><b>git push --force -></b> Irá sobrescrever as mudanças no repositório remoto com as mudanças locais</li>
</ul>