# Sistema de Controle e Gerenciamento de Execução de Ordens de Serviço
## Descrição do Projeto

Este projeto visa a criação de um esquema conceitual para um sistema de controle e gerenciamento de execução de ordens de serviço em uma oficina mecânica. O sistema tem como objetivo gerenciar clientes, veículos, ordens de serviço, peças, serviços e mecânicos de forma eficiente, garantindo a integridade dos dados e facilitando o gerenciamento das operações diárias da oficina.

## Objetivo
Desenvolver um modelo conceitual de banco de dados que atenda às necessidades de uma oficina mecânica, com base na narrativa fornecida. Este modelo deve incluir todas as entidades, relacionamentos e atributos necessários para o funcionamento do sistema.

## Narrativa
Clientes levam veículos à oficina mecânica para serem consertados ou para passarem por revisões periódicas.
Cada veículo é designado a uma equipe de mecânicos que identifica os serviços a serem executados e preenche uma Ordem de Serviço (OS) com data de entrega.
A partir da OS, calcula-se o valor de cada serviço, consultando-se uma tabela de referência de mão-de-obra.
O valor de cada peça também compõe a OS.
O cliente autoriza a execução dos serviços.
A mesma equipe avalia e executa os serviços.
Os mecânicos possuem código, nome, endereço e especialidade.
Cada OS possui: número, data de emissão, valor, status e data para conclusão dos trabalhos.

## Modelo Conceitual
### Entidades e Atributos

#### Cliente
idCliente (INT, PK)
Nome (VARCHAR(45))
CPF (VARCHAR(45))
Telefone (VARCHAR(45))

#### Veículo
idVeículo (INT, PK)
Modelo (VARCHAR(45))
Placa (VARCHAR(45))
Ano (INT)
Cliente_idCliente (INT, FK)

#### Equipe de Mecânicos
idEquipe de mecânico (INT, PK)
Nome da equipe (VARCHAR(45))
Especialidade (VARCHAR(45))

#### Mecânico
idMecânico (INT, PK)
Nome (VARCHAR(45))
Especialidade (VARCHAR(45))
Equipe de mecânico_idEquipe de mecânico (INT, FK)

#### Ordem de Serviço (OS)
idOrdem de serviço (INT, PK)
Número da OS (INT)
Valor (DECIMAL)
Status (VARCHAR(45))
Data de entrega (DATE)
Veículo_idVeículo (INT, FK)
Equipe de mecânico_idEquipe de mecânico (INT, FK)

#### Serviços
idServiços (INT, PK)
Código (INT)
Descrição (VARCHAR(45))
Valor (DECIMAL)
Tipo (VARCHAR(45))
Ordem de serviço_idOrdem de serviço (INT, FK)

#### Peças
idPeças (INT, PK)
Código (INT)
Descrição (VARCHAR(45))
Valor (DECIMAL)
Ordem de serviço_idOrdem de serviço (INT, FK)

### Relacionamentos
Um Cliente pode ter vários Veículos.
Um Veículo pertence a um Cliente.
Um Veículo pode ter várias Ordens de Serviço
Uma Equipe de Mecânicos é composta por vários Mecânicos.
Um Mecânico pertence a uma Equipe.
Uma OS está associada a um Veículo e a uma Equipe.
Uma OS pode conter vários Serviços.
Uma OS pode conter várias Peças.
Justificativas para o Modelo

### Foreign Keys
As foreign keys são usadas para garantir a integridade referencial entre as tabelas. Elas garantem que:

Cada veículo está associado a um cliente válido (Cliente_idCliente em Veículo).
Cada ordem de serviço está associada a um veículo válido (Veículo_idVeículo em Ordem de Serviço).
Cada ordem de serviço está associada a uma equipe de mecânicos válida (Equipe de mecânico_idEquipe de mecânico em Ordem de Serviço).
Cada mecânico pertence a uma equipe de mecânicos válida (Equipe de mecânico_idEquipe de mecânico em Mecânico).
Cada serviço está associado a uma ordem de serviço válida (Ordem de serviço_idOrdem de serviço em Serviços).
Cada peça está associada a uma ordem de serviço válida (Ordem de serviço_idOrdem de serviço em Peças).
Documentação dos Relacionamentos
Os relacionamentos foram definidos para refletir as operações da oficina mecânica conforme descrito na narrativa. Documentar esses relacionamentos ajuda a entender as dependências e interações entre as entidades.

## Conclusão
O modelo conceitual desenvolvido atende às necessidades da oficina mecânica, proporcionando uma estrutura organizada para gerenciar clientes, veículos, ordens de serviço, peças, serviços e mecânicos. Este modelo garante a integridade dos dados e facilita a manutenção e expansão do sistema no futuro.

## Contribuições
Contribuições são bem-vindas! Se você encontrar problemas ou tiver sugestões para melhorias, sinta-se à vontade para abrir uma issue ou enviar um pull request.
