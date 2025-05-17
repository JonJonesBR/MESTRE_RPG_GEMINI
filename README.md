# Mestre de RPG Dinâmico com Google Gemini

Bem-vindo ao Mestre de RPG Dinâmico! Este projeto é um jogo de RPG (Role-Playing Game) baseado em texto onde a API Google Gemini atua como o Mestre do Jogo (Game Master - GM), criando narrativas interativas e adaptáveis em tempo real. Prepare-se para aventuras únicas a cada jogada!

## Funcionalidades Principais

* **Mestre Inteligente (IA):** Utiliza o poder da Google Gemini para gerar descrições de cenários, NPCs (personagens não-jogadores), desafios e consequências das ações do jogador de forma dinâmica.
* **Criação de Personagem:** Permite ao jogador definir o nome e a classe do seu aventureiro.
* **Duração da Aventura Ajustável:** Escolha entre aventuras Curtas, Médias ou Longas, cada uma com um número aproximado de turnos para guiar o ritmo da história.
* **Opção de Estender a Aventura:** Ao final de uma aventura Curta ou Média, o jogador pode optar por continuar a jornada, estendendo-a para a próxima categoria de duração.
* **Jogabilidade Interativa:** Interaja com o mundo através de comandos de texto, decidindo as ações do seu personagem.
* **Respostas Contextuais:** O Mestre-IA leva em consideração o histórico de ações e o estado atual do jogo para gerar respostas coerentes.
* **Gerenciamento de Chave API:** Solicita a chave API do Google Gemini ao usuário na primeira execução e a salva localmente (em um arquivo `.gemini_api_key.txt`) para facilitar usos futuros no mesmo ambiente.

## Tecnologias Utilizadas

* Python 3.x
* API Google Gemini (através da biblioteca `google-generativeai`)

## Requisitos

* Python 3.6 ou superior (para execução local).
* Uma Chave API válida do Google Gemini. Você pode obter uma em [Google AI Studio](https://aistudio.google.com/app/apikey).
* Biblioteca Python `google-generativeai` (necessária para execução local, já inclusa no ambiente Colab geralmente).

## Configuração e Instalação (para Execução Local)

1.  **Clone o Repositório (Opcional, se for usar apenas o Colab):**
    ```bash
    git clone [https://github.com/JonJonesBR/MESTRE_RPG_GEMINI.git](https://github.com/JonJonesBR/MESTRE_RPG_GEMINI.git)
    cd MESTRE_RPG_GEMINI
    ```

2.  **Instale as Dependências (para Execução Local):**
    Abra o terminal ou prompt de comando e instale a biblioteca necessária:
    ```bash
    pip install google-generativeai
    ```

3.  **Configuração da Chave API (para Execução Local ou Colab sem arquivo salvo):**
    * Na primeira vez que você executar o script (localmente ou em uma nova sessão do Colab sem o arquivo `.gemini_api_key.txt`), ele solicitará que você insira sua Chave API do Google Gemini.
    * Se uma chave válida for fornecida, o script tentará salvá-la em um arquivo chamado `.gemini_api_key.txt` no mesmo diretório do script (localmente) ou no diretório raiz da sessão do Colab. Isso evita que você precise inseri-la novamente nas próximas execuções *no mesmo ambiente onde o arquivo pode ser salvo e persistir*.
    * **Importante (Git):** Se você estiver usando Git localmente, adicione `.gemini_api_key.txt` ao seu arquivo `.gitignore` para evitar enviar sua chave API para o GitHub. Exemplo de `.gitignore`:
        ```
        .gemini_api_key.txt
        __pycache__/
        *.pyc
        ```

## Como Jogar

### Opção 1: Executar no Google Colab (Recomendado para Facilidade)

[![Abrir no Google Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/JonJonesBR/MESTRE_RPG_GEMINI/blob/main/MESTRE_RPG_GEMINI_IA.ipynb)

1.  **Abra o Notebook:** Clique no botão "Abrir no Google Colab" acima. O projeto será aberto diretamente no seu navegador.
2.  **Estrutura do Notebook:** O código é organizado em células. Você precisará executar as células na ordem correta.
3.  **Passo 1: Executar a Célula de Configurações e Definições:**
    * A primeira célula de código extensa contém todas as importações de bibliotecas, a lógica para configurar a chave API, as definições de constantes (como `DURATION_OPTIONS_CONFIG`), as configurações do modelo Gemini e todas as definições de funções do jogo (`get_and_configure_api_key`, `iniciar_aventura`, `rodada_do_jogo`, etc.).
    * Para executar esta célula:
        * Clique no ícone "Play" (um círculo com um triângulo apontando para a direita) que aparece à esquerda da célula quando você passa o mouse sobre ela.
        * Ou, clique na célula para selecioná-la e pressione `Shift + Enter`.
    * **Atenção à Chave API:** Se for a primeira vez executando nesta sessão do Colab ou se o arquivo `.gemini_api_key.txt` não for encontrado, o script irá parar e exibir um campo de entrada abaixo da célula, solicitando sua Chave API do Google Gemini. Cole sua chave e pressione Enter. Siga as instruções que aparecerem.
    * Aguarde a célula terminar sua execução. Você deverá ver mensagens como "API do Gemini configurada com sucesso." e "Modelo Gemini (...) configurado e pronto para a aventura!".

4.  **Passo 2: Executar a Célula do Loop Principal do Jogo:**
    * Após a célula de definições ser executada com sucesso, role para baixo até encontrar a próxima (e geralmente última) célula de código. Esta célula contém o bloco `try...except...finally` que chama `iniciar_aventura()` e depois entra no loop `while jogando: jogando = rodada_do_jogo()`.
    * Para executar esta célula e iniciar o jogo:
        * Clique no ícone "Play" dela ou selecione a célula e pressione `Shift + Enter`.
    * O jogo começará, e você poderá interagir com o Mestre de RPG respondendo às perguntas sobre seu personagem, duração da aventura e, em seguida, digitando suas ações.

5.  **Alternativa (Executar Todas as Células de Uma Vez):**
    * Se preferir, você pode executar todas as células do notebook em sequência.
    * No menu superior do Colab, vá em `Ambiente de execução > Executar tudo`.
    * Ou utilize o atalho de teclado: `Ctrl+F9` (em Windows/Linux) ou `Cmd+F9` (em Mac).
    * O script irá parar automaticamente para qualquer entrada necessária do usuário (como a Chave API, se solicitada, e depois as interações do jogo).

### Opção 2: Execução Local (em seu próprio computador)

1.  **Obtenha o Código:**
    * Clone o repositório (se ainda não o fez) ou baixe o arquivo `.py` (ou o conteúdo do notebook salvo como `.py`).
2.  **Execute o Script:**
    * Abra seu terminal ou prompt de comando.
    * Navegue até o diretório onde o arquivo Python (`.py`) está localizado.
    * Execute o script com o comando:
        ```bash
        python nome_do_arquivo.py 
        ```
        (Substitua `nome_do_arquivo.py` pelo nome real do seu arquivo, por exemplo, `rpg_gemini.py`).

3.  **Siga as Instruções no Jogo (Comum a Ambas as Opções):**
    * O jogo solicitará sua Chave API (se não encontrada localmente/na sessão).
    * Em seguida, pedirá o nome do seu personagem, a classe e a duração desejada para a aventura.
    * Leia as narrações do Mestre-IA e digite suas ações quando solicitado.
    * Para sair do jogo a qualquer momento, digite `sair` no prompt de ação.

## Como Funciona

O jogo opera em um loop de turnos:
1.  O jogador configura seu personagem e preferências da aventura (incluindo a chave API na primeira vez).
2.  O script envia um prompt inicial para a API Gemini, que gera o cenário e a situação inicial.
3.  A cada turno:
    * O jogador descreve a ação que deseja realizar.
    * Esta ação, juntamente com o estado atual do jogo (localização, inventário, objetivo, histórico recente), é formatada em um novo prompt.
    * O prompt é enviado à API Gemini.
    * A Gemini, atuando como Mestre, gera uma resposta narrativa descrevendo o resultado da ação, o novo estado do mundo e possíveis próximos passos.
4.  O jogo possui um limite de turnos baseado na duração escolhida. Instruções específicas são enviadas ao Gemini para guiar a narrativa a uma conclusão apropriada dentro desse limite.
5.  Ao atingir o limite de turnos de uma aventura "Curta" ou "Média", o jogador tem a opção de estender a aventura, atualizando o limite de turnos e o nome da duração.

## Customização (Opcional)

* **Duração das Aventuras:** Você pode modificar o dicionário `DURATION_OPTIONS_CONFIG` no início do script para alterar os nomes, IDs e a contagem de turnos aproximada para as durações "Curta", "Média" e "Longa".
    ```python
    DURATION_OPTIONS_CONFIG = {
        "1": {"name": "Curta (objetivo direto)", "id": "curta", "turns": 10}, 
        "2": {"name": "Média (mais exploração)", "id": "media", "turns": 20},
        "3": {"name": "Longa (desenvolvimento e clímax)", "id": "longa", "turns": 40}
    }
    ```
* **Configurações do Modelo Gemini:** O objeto `generation_config` pode ser ajustado para alterar parâmetros como `temperature` (influencia a criatividade/aleatoriedade das respostas do Mestre).
    ```python
    generation_config = {
        "temperature": 0.8, # Valores mais altos = mais criativo/inesperado
        "top_p": 0.95,
        "top_k": 40,
    }
    ```

## Possíveis Melhorias Futuras

* Sistema de combate mais detalhado.
* Gerenciamento de atributos e perícias do personagem.
* Mapas ou representações visuais (mesmo que baseadas em texto).
* Persistência de jogo mais robusta (salvar/carregar progresso entre sessões diferentes).
* Interações com NPCs mais complexas e com memória de longo prazo aprimorada.

## Contribuições

Contribuições são bem-vindas! Sinta-se à vontade para abrir *issues* para relatar bugs ou sugerir novas funcionalidades. Se desejar contribuir com código, por favor, abra um *Pull Request*.

## Licença

Este projeto é distribuído sob a licença MIT. Veja o arquivo `LICENSE` para mais detalhes. (Você precisará criar um arquivo LICENSE com o texto da licença MIT, se desejar).
