# JAVAJPA
Para aprimorar meus conhecimentos em JavaJPA

# Criado com o Maven
Importante na criacao deste projeto, deu um problema no maven, para resolver o problema, foi simples, clicamos com bot�o direito no projeto, achamos o maven, e 
escolhemos a op��o update project.

# src/main/resource
- Se esta diret�rio n�o tiver com a pasta META-INF, � obrigat�ria cria - l�.
- dentro da pasta meta-inf criamos o arquivo xml com o nome de persistente.xml

# src/main/java
- As nossas classes ficam no arquivo.
- As logicas e padroes de projeto.

- ``` <property name="hibernat.hbm2ddl.auto" value="update"/> ```
- Caso perceba alguma coisa nova no banco, ou que n�o existe ele cria ou atualiza, obs: ele n�o recupera coisas apagas 

- ``` <property name="hibernat.hbm2ddl.auto" value="create"/> ```
- Cria o banco do zero toda vez que inicia a aplica��o.

- ``` <property name="hibernat.hbm2ddl.auto" value="create-drop"/> ```
- Cria o banco do zero toda vez que inicia a aplica��o. e depois apaga o banco


#Tipos de carregamentos Lazy e EAGER
- Todo relacionamento que termina em ToOne, exemplo ManyToOne, a JPA faz um join na tabela, isso pode gerar um gargalo na aplia��o.
	Os relacionamentos que n�o terminam com toMany exemplo OneToMany, a JPA n�o executa esse join. Para evitar que aconte�a um gargalho, temos que definir uma propriedade para nossa anota��o
 -	```@ManyToOne(fecth = FetchType.LAZY)```
 
 - Por�m isso pode gerar alguns efeitos indesejados na aplica��o. Como no caso de voc� acessar uma entidade que realiza um join, e nesse momento o entityManager ja estiver fechado. ou seja depois do ```entityManager.close() ```.
 Nesse caso devemos criar uma query, para que no momento que carregue o cliente, carregque junto a outra entity necessaria.

