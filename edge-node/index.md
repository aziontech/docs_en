

# Edge **Node**

O Azion Edge Node permite a criação de uma infraestrutura edge própria, habilitando a instalação de serviços e recursos em real-time.

> 1. [Instalar](#instalar)
> 2. [Visualizar](#Visualizar)
> 3. [Autorizar](#autorizar)
> 4. [Configurações principais](#configuracoes-principais)
> 5. [Serviços](#servicos)

---

## 1. Instalar {#instalar}

A instalação do Edge Node é, basicamente, dividida em 3 etapas: 1- Geração de uma credencial para executar as ações; 2- Instalação do framework nos devices e; 3- autenticação no device (pós framework) com a credencial criada.

### 1.1 Geração da credencial {#geracao-credencial}

Para gerar a credencial necessária para autenticação dos seus edge nodes, os seguintes passos devem ser executados:
	1- Acessar o [Real-Time Manager](https://manager.azion.com/);
	2- No menu superior direito, acessar a página [Credentials]();
	3- Clicar no botão Add;
	4- Preencher os campos necessários e clicar no botão Save:
		**Description:** Descreva, por exemplo, como ou por quem a credencial será utilizada;
		**Teams:** Vincule as permissões de ações que a credencial poderá exercer;

**Observação:** O Token será gerado após a credencial ser salva.

### 1.2 Código para instalação {#codigo-instalacao}

A instalação do Edge Node acontece por meio do script de instalação abaixo:

`apt-get ...`

Via linha de comando, você deve inserir o código disponibilizado, para que seu device instale o framework core necessário para iniciar a executar suas aplicações.

Confira a listagem de plataformas/arquiteturas compatíveis com o Azion Edge Node:

Arquitetura | Versão 
:------------ | :---------
CentOS      |  6.2

### 1.3 Autenticação {#autenticacao}

Durante a instalação do framework, será necessário informar um Token para seu device conseguir se autenticar na Azion e iniciar todo o processo. Você deve informar o token fornecido ou criado nas credenciais, item **1.1 Geração da credencial**.

Após informar o Token e receber a confirmação de que o seu node foi criado, será necessário autorizá-lo e configura-lo no [Real-Time Manager](https://manager.azion.com/).

---

## 2. Visualizar {#visualizar}

Sempre que o código de instalação for executado em algum device, seguido da autenticação via Token, os edge nodes serão listados no [Real-Time Manager](https://manager.azion.com/).

Para visualizar a lista de edge nodes criados para a sua conta, os seguintes passos devem ser executados:
	1- Acessar o [Real-Time Manager](https://manager.azion.com/);
	2- No menu superior esquerdo, acessar o item *Routing* e selecionar a página [Edge Node]();

**Observação:** Os itens listados podem ter sua veracidade confirmada, validando a coluna de Credencial, pois tem o dado de qual credencial executou a autenticação para a geração do node.

---

## 3. Autorizar {#autorizar}

O Azion E...

---

## 4. Configurações principais {#configuracoes-principais}

O Azion E...

---

## 5. Serviços {#servicos}

O Azion E...

---

Didn't find what you were looking for? [Open a support ticket.](https://tickets.azion.com/)

[Edit this page](https://github.com/aziontech/docs_en/edit/master/edge-firewall/index.md) on GitHub.