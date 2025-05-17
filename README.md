# Mestre de RPG Dinâmico com Google Gemini

Bem-vindo ao Mestre de RPG Dinâmico! Este projeto é um jogo de RPG (Role-Playing Game) baseado em texto onde a API Google Gemini atua como o Mestre do Jogo (Game Master - GM), criando narrativas interativas e adaptáveis em tempo real. Prepare-se para aventuras únicas a cada jogada, agora com narração em voz alta!

## Funcionalidades Principais

* **Mestre Inteligente (IA):** Utiliza o poder da Google Gemini para gerar descrições de cenários, NPCs (personagens não-jogadores), desafios e consequências das ações do jogador de forma dinâmica.
* **Geração Aleatória de Início de Aventura:** Objetivo, localização e inventário iniciais são criados pela IA para maior rejogabilidade e surpresa a cada nova partida.
* **Criação de Personagem Flexível:** Permite ao jogador definir o nome e escolher uma classe de uma lista pré-definida ou **inventar a sua própria classe personalizada**.
* **Narração em Áudio (Text-to-Speech):** As principais narrações do Mestre e mensagens importantes do jogo são lidas em voz alta usando a voz **"Thalita" (Português do Brasil)** através da biblioteca `edge-tts`, proporcionando uma experiência mais imersiva.
* **Duração da Aventura Ajustável:** Escolha entre aventuras Curtas, Médias ou Longas, cada uma com um número aproximado de turnos para guiar o ritmo da história.
* **Opção de Estender a Aventura:** Ao final de uma aventura Curta ou Média, o jogador pode optar por continuar a jornada, estendendo-a para a próxima categoria de duração.
* **Jogabilidade Interativa:** Interaja com o mundo através de comandos de texto, decidindo as ações do seu personagem.
* **Respostas Contextuais:** O Mestre-IA leva em consideração o histórico de ações e o estado atual do jogo para gerar respostas coerentes.
* **Gerenciamento de Chave API:** Solicita a chave API do Google Gemini ao usuário na primeira execução e a salva localmente (em um arquivo `.gemini_api_key.txt`) para facilitar usos futuros no mesmo ambiente.

## Tecnologias Utilizadas

* Python 3.x
* API Google Gemini (através da biblioteca `google-generativeai`)
* `edge-tts` (para Text-to-Speech com a voz "Thalita")
* `playsound` (para reprodução de áudio em execuções locais)
* `nest_asyncio` (para compatibilidade com `asyncio` em ambientes de notebook como o Colab)

## Requisitos

* Python 3.7 ou superior (recomendado para `asyncio` e `edge-tts`).
* Uma Chave API válida do Google Gemini. Você pode obter uma em [Google AI Studio](https://aistudio.google.com/app/apikey).
* Bibliotecas Python: `google-generativeai`, `edge-tts`, `playsound`, `nest_asyncio`.

## Configuração e Instalação (para Execução Local)

1.  **Clone o Repositório (Opcional, se for usar apenas o Colab):**
    ```bash
    git clone [https://github.com/JonJonesBR/MESTRE_RPG_GEMINI.git](https://github.com/JonJonesBR/MESTRE_RPG_GEMINI.git)
    cd MESTRE_RPG_GEMINI
    ```

2.  **Instale as Dependências (para Execução Local):**
    Abra o terminal ou prompt de comando e instale as bibliotecas necessárias:
    ```bash
    pip install google-generativeai edge-tts playsound nest_asyncio
    ```
    *Nota: `edge-tts` pode requerer `ffmpeg` para algumas funcionalidades ou formatos, mas geralmente funciona bem para MP3 sem ele. `playsound` pode ter dependências específicas do sistema operacional para reprodução de MP3 (ex: `mpg123` ou `gstreamer` no Linux).*

3.  **Configuração da Chave API (para Execução Local ou Colab sem arquivo salvo):**
    * Na primeira vez que você executar o script (localmente ou em uma nova sessão do Colab sem o arquivo `.gemini_api_key.txt`), ele solicitará que você insira sua Chave API do Google Gemini.
    * Se uma chave válida for fornecida, o script tentará salvá-la em um arquivo chamado `.gemini_api_key.txt`.
    * **Importante (Git):** Adicione `.gemini_api_key.txt` ao seu arquivo `.gitignore` para evitar enviar sua chave API para o GitHub. Exemplo de `.gitignore`:
        ```
        .gemini_api_key.txt
        __pycache__/
        *.pyc
        .temp_edge_speech.mp3 
        ```
        (Adicionado `.temp_edge_speech.mp3` para o arquivo temporário de áudio)

## Como Jogar

### Opção 1: Executar no Google Colab (Recomendado para Facilidade)

[![Abrir no Google Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/JonJonesBR/MESTRE_RPG_GEMINI/blob/main/MESTRE_RPG_GEMINI_IA.ipynb)

1.  **Abra o Notebook:** Clique no botão "Abrir no Google Colab" acima.
2.  **Estrutura do Notebook:** O código é organizado em duas células principais.

3.  **Passo 1: Executar a Célula de Instalação das Bibliotecas:**
    * A primeira célula de código contém o comando:
      ```python
      !pip install -q google-generativeai edge-tts playsound nest_asyncio
      ```
    * Esta célula instala todas as bibliotecas necessárias para o jogo, incluindo o Text-to-Speech.
    * Para executar: Clique no ícone "Play" à esquerda da célula ou selecione-a e pressione `Shift + Enter`. Aguarde a conclusão.

4.  **Passo 2: Executar a Célula Principal do Jogo:**
    * Após a instalação (Passo 1), vá para a segunda célula de código. Ela contém todo o script Python do jogo.
    * Para executar e iniciar o jogo: Clique no ícone "Play" ou selecione a célula e pressione `Shift + Enter`.
    * **Atenção à Chave API:** Se for a primeira vez ou se a chave não estiver salva, o script solicitará sua Chave API do Google Gemini.
    * Siga as instruções para criar seu personagem (nome, classe pré-definida ou inventada, duração da aventura).
    * **O jogo usará Text-to-Speech para narrar as falas do Mestre.** O áudio deve tocar automaticamente.

5.  **Alternativa (Executar Todas as Células de Uma Vez):**
    * Menu: `Ambiente de execução > Executar tudo`.
    * Atalho: `Ctrl+F9` (Windows/Linux) ou `Cmd+F9` (Mac).
    * O script instalará as bibliotecas e depois parará para as entradas do usuário.

### Opção 2: Execução Local (em seu próprio computador)

1.  **Obtenha o Código:** Clone o repositório ou baixe o arquivo `.py`.
2.  **Instale as Dependências (Primeira Vez):** Se ainda não o fez, instale as bibliotecas conforme indicado na seção "Configuração e Instalação".
3.  **Execute o Script:**
    ```bash
    python nome_do_arquivo.py 
    ```
    (Substitua `nome_do_arquivo.py` pelo nome real do seu arquivo).
4.  **Siga as Instruções no Jogo.**

## Como Funciona

1.  **Configuração Inicial:** O jogador fornece sua chave API (se necessário), nome, escolhe uma classe (pré-definida ou personalizada) e a duração desejada para a aventura.
2.  **Geração de Premissa pela IA:** O script solicita à API Gemini para criar um objetivo, localização e inventário iniciais exclusivos.
3.  **Início da Narrativa:** Com base nesses elementos gerados, um prompt é enviado à Gemini para que ela comece a narrar o cenário e a situação inicial da aventura.
4.  **Interação em Turnos:**
    * O jogador digita suas ações.
    * As ações, o estado do jogo e o histórico recente são enviados à Gemini.
    * A Gemini (Mestre) responde com a progressão da história.
    * As respostas do Mestre são exibidas como texto e lidas em voz alta.
5.  **Controle de Duração:** O jogo acompanha os turnos. Instruções são enviadas à Gemini para guiar a história a uma conclusão dentro do limite de turnos da duração escolhida.
6.  **Extensão da Aventura:** Ao final de aventuras "Curtas" ou "Médias", o jogador pode optar por estender a sessão.

## Customização (Opcional)
(Esta seção permanece a mesma, pois as opções de customização mencionadas ainda são válidas)
...

## Possíveis Melhorias Futuras
(Esta seção permanece a mesma)
...

## Contribuições
(Esta seção permanece a mesma)
...

## Licença
(Esta seção permanece a mesma)
...
