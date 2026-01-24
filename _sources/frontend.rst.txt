Frontend - MPS Dashboard
========================

O **MPS Dashboard** é a interface web do sistema Modular Producing System (MPS), desenvolvido com **React** e **TypeScript**. Ele fornece visualização em tempo real, monitoramento e controle do sistema de manufatura integrado.

.. contents::
   :local:
   :depth: 2


Funcionalidades
--------

- **Dashboard** em tempo real com monitoramento de sensores
- **Gerenciamento** de ordens de produção
- **Estatísticas** e gráficos de produção
- **Sistema** de autenticação com JWT
- **Histórico** de peças processadas



Rotas e Páginas
---------------

O MPS Dashboard possui duas paginas principais para o gerenciamento, a principal e a de ordens:


Dashboard (Rota: /)
~~~~~~~~~~~~~~~~~~~

**O que faz:**

Página de monitoramento em tempo real que busca dados do backend a cada **2 segundos** e exibe:

- Status da máquina (rodando, parada, emergência)
- Totalizadores de peças (total, aprovadas, rejeitadas)
- Gráfico de produção por hora
- Ordem ativa em processamento
- Tabela paginada das últimas peças produzidas
- Histórico das últimas ordens

**Endpoints que chama:**

.. code-block:: typescript

    GET http://localhost:8000/api/machine-status
    GET http://localhost:8000/api/production-stats
    GET http://localhost:8000/api/hourly-production
    GET http://localhost:8000/api/recent-orders


**Funcionalidades:**

1. **GET /api/recent-orders** - Lista de últimas ordens:
   - Mostra ordens recentes
   - Status (Pendente, Em Progresso, Concluída)
   - Progresso visual (barra)
   - Quantidade processada vs solicitada

2. **GET /api/machine-status** - Verifica status da máquina:
   - Indica se máquina está rodando, parada ou em emergência

3. **GET /api/production-stats** - Estatísticas de produção:
   - Total de peças produzidas
   - Peças rejeitadas
   - Tempo médio de ciclo
   - Percentual de uptime

4. **GET /api/hourly-production** - Produção por hora:
   - Dados para gráfico de produção na última hora


Ordens (Rota: /orders)
~~~~~~~~~~~~~~~~~~~

**O que faz:**

Página para criar novas ordens de produção e visualizar o histórico de ordens.

.. code-block:: typescript

    GET http://localhost:8000/api/recent-orders
    POST http://localhost:8000/api/create-order

**Funcionalidades:**    

1. **POST /api/create-order** - Formulário para criar nova ordem de produção:
   - Nome da ordem
   - Cor da peça (Prata, Preto, Rosa)
   - Quantidade

2. **GET /api/recent-orders** - Histórico de últimas ordens:
   - Lista paginada das últimas ordens criadas


Arquitetura
-----------

Stack Tecnológico
~~~~~~~~~~~~~~~~~

- **Framework**: React 19.2.3
- **Linguagem**: TypeScript 
- **Roteamento**: React Router 
- **Requisições HTTP**: Axios 
- **Notificações**: React Toastify 11.0.5


Estrutura do Projeto
~~~~~~~~~~~~~~~~~~~~

.. code-block:: text

    mps-dashboard-ts/
    ├── public/              # Arquivos estáticos
    ├── src/
    │   ├── components/      # Componentes reutilizáveis
    │   ├── pages/          # Páginas da aplicação
    │   ├── utils/          # Funções auxiliares
    │   ├── App.tsx         # Componente raiz
    │   └── index.tsx       # Entry point
    ├── package.json        # Dependências e scripts
    └── tsconfig.json       # Configuração TypeScript

Instalação e Setup
------------------

Pré-requisitos
~~~~~~~~~~~~~~

- **Node.js**: 14.0 ou superior
- **npm**: 6.0 ou superior (ou yarn/pnpm)

Instalação de Dependências
~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

    # Entrar na pasta do frontend
    cd Modular-Producing-System---MPS/frontend/mps-dashboard-ts

    # Instalar dependências
    npm install

    # ou com yarn
    yarn install

Desenvolvimento
---------------

Modo de desenvolvimento
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

    npm start

O aplicativo abrirá automaticamente em ``http://localhost:3000``.


Build para Produção
~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

    npm run build

    Gera pasta ``build/`` pronta para deploy.


Acessar de outros dispositivos na rede
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Descobrir IP local:

.. code-block:: bash

    # Windows
    ipconfig

    # Linux/Mac
    ifconfig

Iniciar servidor com acesso externo:

.. code-block:: bash

    # Windows
    set HOST=0.0.0.0 && npm start

    # Linux/Mac
    HOST=0.0.0.0 npm start

Acessa pelo navegador em ``http://SEU_IP:3000``.


Deployment
----------

Build para Produção
~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

    npm run build

Gera pasta ``build/`` pronta para deploy.


Recursos
--------

- `Documentação React <https://react.dev>`_
- `TypeScript Handbook <https://www.typescriptlang.org/docs>`_
- `React Router <https://reactrouter.com>`_
- `Axios Documentation <https://axios-http.com>`_
- `Create React App <https://create-react-app.dev>`_

Contato e Suporte
-----------------

Para dúvidas sobre o frontend, consulte:

- Documentação do projeto: :doc:`usage`
- Backend API: :doc:`mes`
- Issues no GitHub: `MPS Issues <#>`_
