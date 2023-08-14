# Modelagem Lógica usando MySQL
 Atividades de estudo de modelagem de banco de dados

## Exemplo de Modelagem Lógica

![Modelo lógico do sistema de Vendas](modelo-logico-vendas.png)


## Sobre tipos de relacionamento

### 1:1
Relacionamento do tipo **1 para 1**.

Um registro de um tabela está relacionado apenas a um registro de outra tabela.
Exemplo: O cliente está registrado com um endereço específico.

### 1:n
Relacionamento do tipo **1 para n**, ou seja, **1 para vários**.

Quando um registro de uma tabela está relacionado com vários registros de outra tabela. 
Exemplo: Um cliente (dado único) que tenha feito vários pedidos. 

### n:m
Relacionamento do tipo **n para m**, ou seja, **vários para vários**.
Exemplo: clínica onde médicos atendam vários pacientes e/ou um paciente ser atendido por vários médicos.
