# DAO-JDBC-MySQL

# DAO-JDBC-MySQL

### Introdução

No desenvolvimento de sistemas que utilizam banco de dados, é fundamental organizar corretamente a forma como as informações são acessadas e manipuladas. Em Java, essa comunicação com bancos relacionais, como o MySQL, é realizada por meio da API JDBC (Java Database Connectivity).

Quando essa integração é feita sem organização, o código tende a ficar confuso, difícil de manter e vulnerável a problemas de segurança, como SQL Injection. Além disso, a evolução do sistema se torna mais complexa, já que alterações no banco podem impactar várias partes do código.

Para resolver esses problemas, utiliza-se o padrão de projeto DAO (Data Access Object), que separa a lógica de acesso aos dados das demais partes da aplicação. Essa separação melhora a organização do sistema, facilita a manutenção e permite maior reutilização de código.

### O que é o padrão DAO

O padrão DAO (Data Access Object) tem como objetivo isolar a camada de acesso ao banco de dados da lógica da aplicação.

Em vez de espalhar comandos SQL pelo sistema, toda a comunicação com o banco fica concentrada em classes específicas chamadas DAOs.

#### Vantagens do DAO:
- Organização do código
- Separação de responsabilidades
- Facilidade de manutenção
- Reutilização de código
- Facilidade para testes
  
### O que é JDBC

O JDBC (Java Database Connectivity) é uma API do Java que permite conectar e executar comandos em bancos de dados relacionais.

#### Com o JDBC, é possível:

- Abrir conexão com o banco;
- Executar comandos SQL;
- Consultar dados;
- Manipular resultados.
  
#### Principais componentes:
- Connection → conexão com o banco;
- PreparedStatement → execução segura de comandos SQL;
- ResultSet → resultado das consultas.

#### Ciclo de vida da conexão JDBC

##### O processo básico de uso do JDBC segue estas etapas:

- Abrir conexão com o banco de dados;
- Preparar o comando SQL;
- Executar o comando (INSERT, SELECT, UPDATE, DELETE);
- Processar os resultados (quando houver);
- Fechar os recursos utilizados.

###### O uso correto desse ciclo é essencial para evitar problemas como vazamento de memória ou travamento de conexões.

### Segurança — SQL Injection

O SQL Injection é uma vulnerabilidade que ocorre quando comandos SQL são montados com concatenação de strings, permitindo que usuários mal-intencionados alterem a consulta.

#### Exemplo não seguro:
```
"SELECT * FROM usuario WHERE nome = '" + nome + "'"
```

#### Forma segura:

##### Utilizar PreparedStatement, que separa o comando SQL dos dados:

```
"SELECT * FROM usuario WHERE nome = ?"
```
###### Isso impede que comandos maliciosos sejam executados.

### Boas práticas com JDBC

- Uso de PreparedStatement;
- Evita SQL Injection;
- Melhora desempenho em consultas repetidas.

#### Try-with-resources

##### Garante o fechamento automático de recursos:
```
try (Connection conn = ...;
     PreparedStatement st = ...) {
}
```

### Tratamento de exceções

- Evitar expor SQLException diretamente;
- Criar exceções personalizadas (ex: DbException);
- Padronizar mensagens de erro.

#### Arquitetura em camadas

##### A aplicação é organizada em camadas para separar responsabilidades:

- app → interface e controle do sistema;
- model → classes que representam os dados;
- dao → interfaces (contratos);
- dao.impl → implementação com SQL e JDBC;
- db → conexão com banco e tratamento de exceções.

###### Essa divisão facilita manutenção e organização do projeto.

### Modelagem de banco de dados (MySQL)

#### Para um bom funcionamento do sistema, o banco deve ser bem estruturado:

- PK (Primary Key): identificador único;
- FK (Foreign Key): relacionamento entre tabelas;
- NOT NULL: campo obrigatório;
- UNIQUE: evita duplicidade;
- Tipos de dados: INT, VARCHAR, DECIMAL, DATETIME.

### Transações (conceito)

Uma transação é um conjunto de operações que devem ser executadas juntas.

#### Exemplo:

- Inserir um pedido;
- Inserir itens do pedido.

###### Se uma operação falhar, todas devem ser desfeitas (rollback).

### Conclusão da Pesquisa

A utilização do padrão DAO em conjunto com o JDBC permite desenvolver sistemas mais organizados, seguros e fáceis de manter. A aplicação de boas práticas, como o uso de PreparedStatement, tratamento adequado de exceções e organização em camadas, contribui diretamente para a qualidade do software.

## MAPA CONCEITUAL 

<img width="926" height="910" alt="Image" src="https://github.com/user-attachments/assets/6fd928c4-f042-4bb2-8cb0-55dba0be55e2" />
