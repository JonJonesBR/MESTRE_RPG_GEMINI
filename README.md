# RPG Textual com IA Gemini

Este projeto é um jogo de RPG (Role-Playing Game) textual interativo onde a narrativa é gerada dinamicamente pela Inteligência Artificial do Google, Gemini. 

A aplicação web é construída com Gradio e inclui narração por voz (Text-to-Speech) para uma experiência imersiva.

## Funcionalidades Principais

* **Narrativa Dinâmica:**

 Aventuras e cenários gerados em tempo real pela IA Gemini.

* **Criação de Personagem:**

 Defina o nome e a classe do seu aventureiro.

* **Duração da Aventura:**

 Escolha entre aventuras curtas, médias ou longas.

* **Narração por Voz:** 

As respostas do mestre (IA) são convertidas em áudio usando Edge-TTS.

* **Interface Web Interativa:** 

Jogue diretamente no seu navegador através de uma interface Gradio.

## Tecnologias Utilizadas

* Python 3
* Google Generative AI (API do Gemini)
* Gradio (para a interface web)
* Edge-TTS (para Text-to-Speech)
* Playsound (utilizado por Edge-TTS localmente, mas no Colab o áudio é gerenciado pelo Gradio)
* Nest_asyncio (para compatibilidade com loops assíncronos em notebooks)

## Instruções de Configuração e Execução no Google Colab

Siga os passos abaixo para executar este RPG no Google Colab:

### 1. Obtendo sua Chave API do Google Gemini

Antes de começar, você precisará de uma chave API do Google Gemini.

* **Acesse o Google AI Studio:** Vá para [https://aistudio.google.com/app/apikey](https://aistudio.google.com/app/apikey).

* **Crie ou Use uma Chave Existente:**

    * Se você ainda não tem um projeto e uma chave API, clique em "Create API key in new project" (Criar chave API em novo projeto).

    * Copie a chave API gerada. Ela será algo como `AIzaSy...`.

 **Guarde esta chave em um local seguro, pois ela dá acesso aos serviços do Gemini associados à sua conta.**

* **Importante:** O script está configurado para usar o modelo `gemini-2.0-flash-lite`.

 Certifique-se de que sua chave API tenha permissão para usar este modelo ou ajuste a variável `MODEL_NAME_TEXT` no script para um modelo ao qual você tenha acesso (ex: `gemini-1.5-flash-latest`).

### 2. Executando o Game no Google Colab

* **Abra o Projeto no Google Colab:**

   [LINK DO PROJETO](https://colab.research.google.com/github/JonJonesBR/MESTRE_RPG_GEMINI/blob/main/RPG_AUDIO.ipynb)

* Clique no link abaixo para abrir o notebook diretamente no Google Colab a partir do repositório GitHub:

  [Abrir RPG_AUDIO.ipynb no Colab](https://colab.research.google.com/github/JonJonesBR/MESTRE_RPG_GEMINI/blob/main/RPG_AUDIO.ipynb)

    * Se solicitado, autorize o Colab a acessar arquivos do GitHub.

### 3. Executando o Script

* **Execute a Célula:** 

Clique no botão "Play" (ícone de círculo com um triângulo) à esquerda da célula de código ou pressione `Ctrl+Enter` (ou `Cmd+Enter` no Mac).

* **Instalação de Pacotes:** 

O script começará instalando as bibliotecas necessárias. Aguarde a conclusão.

* **Aguarde o Link do Gradio:** 

Após a instalação e execução do código, o Gradio iniciará um servidor. Na saída da célula, você verá algo como:

    ```
    Running on local URL:  [http://127.0.0.1](http://127.0.0.1):XXXX
    Running on public URL: https://INSTANCE_ID.gradio.live
    ```
    Esta URL pública (`https://INSTANCE_ID.gradio.live`) é o seu link para a aplicação web. Ela é temporária e expira após 72 horas (ou quando a sessão do Colab é encerrada).

## Como Jogar

1.  **Acesse a Aplicação:**

 Clique no link `Running on public URL: ...` gerado na saída da célula do Colab. Isso abrirá a interface do RPG em uma nova aba do seu navegador.

2.  **Configure a API Key:**

    * Na interface, você verá uma seção para "Configuração API Gemini".

    * Cole a sua chave API do Google Gemini no campo "Sua Chave API do Gemini".

    * Clique em "Configurar API e Modelo". Você receberá um feedback sobre o sucesso da configuração.

3.  **Crie seu Personagem e Aventura:**

    * Após configurar a API, a seção "Detalhes da Aventura" aparecerá.

    * Digite o nome do seu aventureiro.

    * Escolha uma classe pré-definida ou digite uma classe personalizada.

    * Selecione a duração desejada para a sua aventura.

    * Clique em "Iniciar Aventura!".

4.  **Interaja com o Jogo:**

    * A narrativa começará no painel de chat.

    * A narração do mestre (IA) será reproduzida em áudio.

    * Digite suas ações no campo de texto na parte inferior (ex: "exploro a caverna", "falo com o taverneiro", "ataco o goblin").

    * Clique em "Enviar Ação" ou pressione Enter.

    * Continue interagindo para progredir na história.

    * Para sair do jogo, digite "sair" no campo de ação.

Divirta-se em suas aventuras!
