# asa_delta
o painel do projeto asa delta
O Projeto Asa Delta é uma plataforma unificada e robusta de Open-Source Intelligence (OSINT), construída em Python para realizar consultas complexas e enriquecimento de dados sobre indivíduos e entidades brasileiras.

Este não é apenas um script; é um framework modular que orquestra múltiplas fontes de inteligência: desde validações cadastrais locais até a consulta de APIs governamentais (Gov.br), verificadores de e-mail, geolocalizadores IP e coleta ativa via Google Dorks.

🎯 Objetivo: Fornecer uma visão 360º sobre os dados brasileiros, identificando correlações, riscos e pontos de vazamento através da convergência de múltiplas fontes.
🛠️ Funcionalidades Principais (Onde a Mágica Acontece)

O painel foi desenhado com três modos de operação principais, acessíveis via Streamlit:

    👤 Consulta Detalhada (Manual):
        Validação Local: Valida CPF/CNPJ e RG em tempo real usando algoritmos brasileiros complexos.
        API Federation: Dispara consultas sequenciais para múltiplas APIs (Receita Federal, Verificação de Email, GeoIP), agregando os resultados em um painel consolidado.
    🧺 Análise Batch (Lista Grande):
        Permite carregar grandes volumes de dados (simulando CSV/planilhas) e executar o fluxo completo de consultas em loop, otimizando o tempo total de processamento.
    🌐 Coleta Ativa (Dorking & Scraping):
        Implementa lógica avançada de construção de Google Dorks (site:, "aspas") para raspar ativamente informações dispersas pela web, e não apenas por fontes API específicas.

🚀 Tecnologias Utilizadas (Tech Stack)

    Backend Core: Python 🐍
    Interface Gráfica (UI): Streamlit (para prototipagem rápida de painéis complexos).
    Requisições HTTP: requests (Para comunicação robusta com APIs RESTful).
    Web Scraping: BeautifulSoup / Selenium (Depende da implementação final do Crawler).
    Dados: Pandas (Para manipulação e exibição de resultados tabulares).

⚙️ Como Rodar o Projeto (Setup Rápido)

Siga estes passos para colocar toda a potência do Asa Delta em ação:
1. Pré-requisitos

Certifique-se de ter o Python 3.9+ instalado.
2. Clonar e Instalar Dependências

Clone este repositório e crie um ambiente virtual (Altamente recomendado!):

git clone https://github.com/seu_usuario/projeto-asa-delta.git
cd projeto-asa-delta
python -m venv venv
source venv/bin/activate # No Linux/macOS
# venv\Scripts\activate  # No Windows
pip install -r requirements.txt

3. Configuração das APIs (🚨 Ponto CRÍTICO)

O poder do projeto reside nos dados externos. Você DEVE configurar suas chaves de API.

    Criar .env: Crie um arquivo chamado .env na raiz do projeto.
    Adicionar Chaves: Insira suas credenciais de forma segura:

    # .env file content
    GOV_TOKEN="SUA_CHAVE_API_DO_GOV"
    EMAIL_API_KEY="SEU_CREDENTIAL_DE_VERIFICADOR_EMAIL"
    # ... adicione outras chaves necessárias

4. Executar o Painel

Execute a aplicação através do Streamlit:

streamlit run asa_delta_master_panel.py

🧠 Arquitetura Técnica (Para Desenvolvedores)

O código foi estruturado em classes para garantir baixa acoplagem, mesmo estando monolítico:

    DataValidator: Responsável pela camada de regras de negócio locais brasileiras.
    OSINTConnector: É o Gateway das APIs externas. Ele encapsula a lógica de autenticação (Bearer Tokens, API Keys) e trata os erros específicos de cada serviço (Retry Logic, Rate Limiting).
    DataCrawler: Implementa a camada de coleta passiva/ativa (Scraping), abstraindo complexidades como o parsing de HTML ou interação com paginadores de busca.
    AsaDeltaMasterPanel: Atua como o Orquestrador. Ele é responsável por chamar os serviços na ordem correta, gerenciar o fluxo do usuário e apresentar os dados consolidados.

📚 Roteiro de Expansão (Próximos Passos)

Este projeto está pronto para escalar em diversas direções:

    Integração Dark Web: Adicionar conectores para APIs especializadas em marketplaces C2C/B2B (e.g., ShadowMarket API).
    Visualização de Grafos: Implementar visualização de grafo usando PyVis ou NetworkX para mostrar conexões entre os dados encontrados (Quem conhece quem?).
    Interface Física: Migrar do Streamlit para uma interface mais robusta com Dash ou até mesmo um framework headless se for necessário rodar em servidores dedicados de baixo consumo.
