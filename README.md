# 📊 Estudo de Transações e Concorrência em Banco de Dados (TP3)

Olá! Bem-vindo(a) ao repositório do **Trabalho Prático 3 (TP3)** de Banco de Dados. 

Este projeto foi construído com muito cuidado para colocar em prática conceitos bem avançados e cruciais de Sistemas de Gerenciamento de Banco de Dados (SGBDs). Nossa ideia aqui foi ir além da teoria e colocar a mão na massa para entender como um banco de dados lida com múltiplas coisas acontecendo ao mesmo tempo, sem perder a integridade da informação.

---

## 👥 Quem fez isso acontecer?

Este projeto foi desenvolvido em equipe por:
* **Lucas de Souza Cerveira Pereira**
* **Mikaelle Costa de Santana**
* **Roberta Graziela de Oliveira Brasil**

---

## 📝 O que é esse projeto, afinal?

Se você já se perguntou como um sistema de ingressos consegue vender a mesma cadeira sem duplicar a compra para duas pessoas diferentes, esse trabalho explora exatamente esse universo.

No notebook principal do projeto, nós guiamos você através de alguns experimentos muito interessantes:

1.  **Manipulação de Dados na Prática:** Usamos SQL integrado direto com Python, com a ajuda das bibliotecas `pandas` e `sqlalchemy`. É bem legal ver como essas ferramentas conversam entre si.
2.  **O Desafio da Concorrência:** Simulamos cenários onde várias transações tentam escrever no banco ao mesmo tempo (o clássico problema de reserva de assentos!).
3.  **Níveis de Isolamento:** Comparamos como o banco se comporta usando *Read Committed* (onde a gente lê só o que já foi confirmado) versus *Serializable* (o modo mais rígido, onde o banco praticamente enfileira as requisições para evitar qualquer anomalia).
4.  **Condições de Corrida:** Nós forçamos algumas falhas lógicas (aquelas que acontecem quando sistemas concorrentes tentam acessar o mesmo recurso) e depois aplicamos estratégias para consertar isso, comparando abordagens otimistas contra as pessimistas (onde bloqueamos tudo preventivamente).

---

## ⚙️ O que você precisa para rodar na sua máquina?

Para brincar com os nossos experimentos, você vai precisar ter o **PostgreSQL** instalado e rodando aí no seu computador.

Nós configuramos o notebook para procurar um banco de dados e um usuário específicos. Então, para tudo funcionar de primeira, crie as seguintes credenciais no seu Postgres:

* **Usuário:** `icomp`
* **Senha:** `icomp123`
* **Database:** `icomp`
* **Permissões:** Não precisa ser superusuário, mas esse usuário precisa ter permissões de leitura e escrita nesse banco de dados `icomp`.

> **Por que essas credenciais?** Nós padronizamos isso para facilitar na hora da correção pelos professores, assim todo mundo usa o mesmo padrão!

---

## 🚀 Passo a passo: Instalação e Execução

Para garantir que as dependências não virem uma bagunça, recomendamos muito usar um ambiente virtual (`venv`). Siga os passos abaixo:

### 1. Preparando a casa (Ambiente Virtual)

Abra o seu terminal, navegue até a pasta deste projeto e rode:

```bash
# Criando o ambiente virtual:
python3 -m venv .venv

# Ativando o ambiente:
source .venv/bin/activate
```

### 2. Instalando as ferramentas

Agora vamos instalar tudo o que o Python precisa para conversar com o banco e rodar os notebooks:

```bash
# Suporte para rodar os notebooks no Jupyter:
pip install ipykernel

# Ferramentas de dados e drivers do Postgres:
pip install pandas psycopg2-binary sqlalchemy ipython-sql matplotlib
```

### 3. Mostrando o caminho para o Jupyter

Para que o Jupyter saiba que nosso ambiente `tp3` existe, você precisa registrar o kernel:

```bash
python -m ipykernel install --user --name tp3 --display-name "Python (TP3)"
```

### 4. Rodando o Experimento!

1. Abra o **Jupyter Notebook** ou o **Jupyter Lab**.
2. Abra o nosso arquivo principal: `Notebook_tp3.ipynb`.
3. No menu lá em cima, vá em `Kernel` -> `Change Kernel` e escolha **Python (TP3)**.
4. Agora é só rodar as células na sequência e acompanhar as explicações!

---

## 🧪 O que nós descobrimos? (Resumo dos Resultados)

Se você não tem tempo para rodar tudo agora, sem problemas! O grande "tchan" que tiramos desse trabalho é sobre o trade-off (a famosa "escolha") na engenharia de dados:

- Usar **Consistência Estrita (Serializable)** é ótimo porque garante que os dados fiquem 100% íntegros. Porém, isso custa caro para a performance. O sistema fica mais lento devido às constantes necessidades de coordenação e tentativas de refazer transações bloqueadas.
- Já as **Estratégias Otimistas** (usando níveis menores de isolamento como *Read Committed*, mas checando a validade do dado antes de escrever, tipo um `WHERE disponivel = TRUE`) entregam uma vazão de processamento (*throughput*) muito melhor. É a escolha ideal para sistemas que recebem milhares de requisições por segundo.

---

## ⚖️ Compartilhando conhecimento

Fizemos esse projeto com foco no nosso aprendizado acadêmico. Por favor, sinta-se super à vontade para dar um *fork*, estudar o código, pegar as ideias e usar como achar melhor. Aprender em comunidade é sempre mais divertido!