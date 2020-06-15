

# Edge **Node**

[Edite no GitHub <svg width="14" height="14" xmlns="http://www.w3.org/2000/svg"><g fill="none" stroke="#F3652B"><path d="M4.81.71H.672v11.43H12.1V8.001" stroke-width=".8"/><path d="M6.87.786h5.155V5.94M6.31 6.5L12.026.786"/></g></svg>](https://github.com/aziontech/docs_en/edit/master/edge-node/index.md)

O Azion Edge Node permite a criação de uma infraestrutura edge própria, habilitando a instalação de serviços e recursos em real-time.

> 1. [Instalar](#instalar)
> 2. [Visualizar](#Visualizar)
> 3. [Autorizar](#autorizar)
> 4. [Configurações principais](#configuracoes-principais)
> 5. [Serviços](#servicos)

---

## 1. Instalar {#instalar}

A instalação do Edge Node é, basicamente, dividida em 3 etapas: 1- Geração de uma credencial para executar as ações; 2- Instalação do framework nos devices e; 3- autenticação no device (pós framework).

### 1.1 Geração da credencial {#geracao-credencial}

Para gerar a credencial necessária para autenticação dos seus edge nodes, os seguintes passos devem ser executados:	

​	1- Acessar o [Real-Time Manager](https://manager.azion.com/);

​	2- No menu superior direito, acessar a página [Credentials]();

​	3- Clicar no botão Add;

​	4- Preencher os campos necessários e clicar no botão Save:

​		**Description:** Descreva, por exemplo, como ou por quem a credencial será utilizada;

​		**Teams:** Vincule as permissões de ações que a credencial poderá exercer;

**Observação:** O Token será gerado após a credencial ser salva.

### 1.2 Código para instalação {#codigo-instalacao}

Para iniciar o processo de instalação do Edge Node, você deve fazer o download do arquivo *.rpm*.

Confira a listagem de plataformas compatíveis com o Azion Edge Node:

| Plataforma | Versão | Arquitetura | Arquivo                                         |
| :--------- | :----: | :---------: | ----------------------------------------------- |
| CentOS     | ≤ 7.0  |   x86-64    | [azorch-client-0.1-2.rpm](https://s3-download/) |

Via linha de comando, você deve seguir os passos abaixo, para que seu device instale o framework core necessário para iniciar a executar suas aplicações:	

​	1- Instalar o *rpm* azorch-client baixado. Comando "*rpm -ivh azorch-client-0.1-2.rpm*";

​	2- Dentro do diretório "*/etc/azorch/*", criar um arquivo com o nome "*token*" e o seu conteúdo deve ser o token criado via Real-Time Manager;

​	3- Iniciar o client com o comando "*/usr/sbin/azorch-client -c /etc/azorch/azorch-client.conf*"

### 1.3 Autenticação {#autenticacao}

Durante a instalação do framework, será necessário informar o Token para seu device conseguir se autenticar na Azion e iniciar todo o processo. Você deve informar o token criado nas credenciais, item **1.1 Geração da credencial**.

Após informar o Token e receber a confirmação de que o seu node foi criado, será necessário autorizá-lo e configura-lo no [Real-Time Manager](https://manager.azion.com/).

---

## 2. Visualizar {#visualizar}

Sempre que o código de instalação for executado em algum device, seguido da autenticação via Token, os edge nodes serão listados no [Real-Time Manager](https://manager.azion.com/).

Para visualizar a lista de edge nodes criados para a sua conta, os seguintes passos devem ser executados:

​	1- Acessar o [Real-Time Manager](https://manager.azion.com/);

​	2- No menu superior esquerdo, acessar o item *Routing Services* e selecionar a página [Edge Node]();

**Observação:** Os itens listados podem ter sua veracidade confirmada, validando a coluna de HashId, pois nela contém o hash utilizado para a criação e autenticação do edge node. 

---

## 3. Autorizar {#autorizar}

Para que seus edge nodes iniciem a Orquestração, os mesmos devem ser autorizados. Para autorizar um edge node, os seguintes passos devem ser executados:

​	1- Acessar o [Real-Time Manager](https://manager.azion.com/);

​	2- No menu superior esquerdo, acessar o item *Routing Services* e selecionar a página [Edge Node]();

​	3- Validar a listagem de Edge Nodes;

​	4- Clicar no ícone "Chave" e aceitar a janela de confirmação.

Após este processo, o Edge Node pode demorar até 10 segundos para que a orquestração seja iniciada.

---

## 4. Serviços {#servicos}

O Azion E...

---

## 5. Configs? {#servicos}

O Azion E...VALIDAR

---

Didn't find what you were looking for? [Open a support ticket.](https://tickets.azion.com/)
