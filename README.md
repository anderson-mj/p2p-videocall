# Relatório sobre a ETAPA 1 do trabalho prático

## Escopo da atividade:

### A atividade prática da disciplina consiste em desenvolver uma aplicação de videoconferência descentralizada. Para isso, deve ser utilizada comunicação por sockets, permitindo que os usuários primeiro se registrem em um servidor e consultem a lista de nós cadastrados, para depois de conectarem aos seus pares utilizando o modelo Peer-to-Peer (P2P).

---

## Escopo da ETAPA 1:

### Desenvolver a parte de registro e consultas no servidor. Nesta etapa, é necessário implementar um socket TCP que interconecte os clientes e o servidor.

---

## Grupo:
- Anderson Meireles
- Matheus Campos
- Matheus Folly

### As atividades foram realizadas em conjunto de forma que os integrantes participassem na compreensão e desenvolvimento de forma coletiva, não foi designado funções específicas a serem implementada por cada membro.
---

## Uso da aplicação (como executar o código):

### Para executar essa aplicação local é necessário:
* Ter python 3 instalado na máquina
* Clonar o repositório do github ou copiar os arquivos para uma pasta local
* Abrir 2 terminais nesse mesmo diretório (1 terminal para o servidor e 1 terminal para o cliente)
* Executar `python server.py` no terminal que for rodar o servidor
* Executar `python client.py` no terminal que for rodar o cliente e responder os inputs
* Validar se o cadastro foi realizado com sucesso

#### Exemplo visual:

> Repositório clonado do github (poderia ser uma pasta com os arquivos `client.py` e `server.py` também)
![executar1](images/executar1.png)

> Abrindo o terminal no diretório que contém os arquivos `client.py` e `server.py`
![executar2](images/executar2.png)

> Iniciando o servidor
![servidor1](images/servidor1.png)

> Iniciando um cliente
![cliente1](images/cliente1.png)

> Validando que o cliente de fato foi registrado no servidor
![servidor2](images/servidor2.png)

#### Diagrama de sequência de algumas interações cliente-servidor:

:::mermaid
sequenceDiagram
    Cliente->>Servidor: Inicializa o cliente

    alt Registro de Cliente
        Cliente->>Servidor: Conecta ao servidor
        Servidor->>Servidor: Estabelece a conexão
        Cliente->>Servidor: Envia informações de registro
        Servidor->>Servidor: Processa o registro
        Servidor-->>Cliente: Confirmação de registro

        opt Consulta de Usuários
            Cliente->>Servidor: Solicita lista de usuários
            Servidor->>Servidor: Recupera a lista de usuários
            Servidor-->>Cliente: Lista de usuários
        end

        opt Detalhes de Usuário
            Cliente->>Servidor: Solicita detalhes de um usuário
            Servidor->>Servidor: Recupera detalhes do usuário
            Servidor-->>Cliente: Detalhes do usuário
        end

        opt Encerramento da Conexão
            Cliente->>Servidor: Encerra a conexão
            Servidor->>Servidor: Fecha a conexão
            Servidor-->>Cliente: Confirmação de encerramento
        end
    end

:::

---

## Erros esperados na execução da aplicação:

> Cadastro de usuário com mesmo nome e IP
![esperado1](images/esperado1.png)

> Cadastro de novo usuário com mesmo IP e porta
![esperado2](images/esperado2.png)

> Cadastro de novo usuário passando a porta do servidor
![esperado3](images/esperado3.png)

> Terminal do servidor durante algumas das execuções acima
![esperado4](images/esperado4.png)

---

## Implementação:

