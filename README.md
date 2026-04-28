# 🍎 Chatbot de Nutrição com IA Generativa

> **Trabalho Final — Disciplina de Inteligência Artificial | UFES**

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.11-3776AB?style=for-the-badge&logo=python&logoColor=white" />
  <img src="https://img.shields.io/badge/Telegram_Bot-2CA5E0?style=for-the-badge&logo=telegram&logoColor=white" />
  <img src="https://img.shields.io/badge/Groq_API-F55036?style=for-the-badge&logo=groq&logoColor=white" />
  <img src="https://img.shields.io/badge/Llama_3.3_70B-6E4AFF?style=for-the-badge&logo=meta&logoColor=white" />
  <img src="https://img.shields.io/badge/Google_Colab-F9AB00?style=for-the-badge&logo=googlecolab&logoColor=black" />
  <img src="https://img.shields.io/badge/LangChain-1C3C3C?style=for-the-badge&logo=langchain&logoColor=white" />
</p>

---

## 📄 Descrição Geral

Este projeto é um **assistente nutricional inteligente** integrado ao **Telegram**, desenvolvido como trabalho final da disciplina de **Inteligência Artificial** da UFES. O bot interage com o usuário em linguagem natural, realiza uma anamnese completa e gera planos alimentares personalizados com base nos dados fornecidos.

O sistema utiliza o modelo de linguagem **Llama 3.3 70B** via **Groq API** para processar as informações e gerar respostas. O conteúdo de um **Manual de Dietas Hospitalares** em PDF é injetado diretamente no contexto do modelo, garantindo que as recomendações sejam embasadas em referências clínicas reais.

### 👨‍💻 Autor

- **Felipe Kitamoto Amaral** — DCE/UFES
- 🎞️ [Slides e Vídeo Apresentativo](https://www.canva.com/design/DAGvsRqPKCI/BNSVQeNolK4QEZbL6gdsFA/edit?utm_content=DAGvsRqPKCI&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton)

---

## 🤖 Funcionalidades

### 🥗 Geração de Dieta Personalizada (`/dieta`)
O bot conduz uma anamnese passo a passo coletando os seguintes dados do usuário:

| Campo | Exemplo |
|:---|:---|
| Nome | João |
| Idade | 25 anos |
| Gênero biológico | Masculino |
| Peso | 80 kg |
| Altura | 175 cm |
| Frequência de atividade física | 3x por semana, moderada |
| Objetivo | Emagrecimento |
| Observações | Intolerante à lactose |

Com esses dados, o modelo gera um cardápio completo especificando número de refeições, calorias totais, macronutrientes, quantidades de cada alimento e múltiplas opções de substituição para cada refeição.

### 💬 Chat Contínuo Pós-Dieta
Após receber o plano alimentar, o usuário pode continuar conversando com o bot para tirar dúvidas sobre nutrição, alimentos e saúde, com histórico de mensagens mantido por sessão.

### ⚠️ Detecção de Casos Críticos
O modelo é instruído a identificar situações fora do padrão (ex: IMC muito baixo ou muito alto) e alertar o usuário sobre a necessidade de buscar um profissional de saúde, podendo sugerir um objetivo mais adequado ao perfil.

### 📚 Fundamentação em Manual Clínico
O conteúdo do `ResumoManualDeDietas.pdf` é carregado via **LangChain + PyPDF** e injetado como contexto na requisição ao modelo, garantindo que as dietas geradas respeitem diretrizes nutricionais clínicas.

---

## 🧠 Arquitetura e Fluxo

```
Usuário (Telegram)
        │
        │ /dieta
        ▼
┌──────────────────────┐
│   Anamnese (8 etapas)│
│  Nome → Idade →      │
│  Gênero → Peso →     │
│  Altura → Atividade →│
│  Objetivo → Obs      │
└────────┬─────────────┘
         │
         ▼
┌──────────────────────┐
│  Construção do Prompt│
│  + Contexto do PDF   │
│  (Manual de Dietas)  │
└────────┬─────────────┘
         │
         ▼
┌──────────────────────┐
│  Groq API            │
│  Llama 3.3 70B       │
└────────┬─────────────┘
         │
         ▼
┌──────────────────────┐
│  Dieta Personalizada │
│  enviada ao usuário  │
└────────┬─────────────┘
         │
         ▼
┌──────────────────────┐
│  Chat Contínuo       │
│  (com histórico)     │
└──────────────────────┘
```

---

## 💬 Comandos Disponíveis

| Comando | Descrição |
|:---:|:---|
| `/dieta` | Inicia a anamnese e gera um plano alimentar personalizado |
| `/ajuda` | Exibe informações de contato e suporte |
| `/menu` | Retorna ao menu inicial e limpa a sessão atual |
| `/finalizar` | Encerra a sessão e limpa os dados do usuário |

---

## 🛠️ Tecnologias Utilizadas

| Tecnologia | Função |
|:---|:---|
| **Python** | Linguagem principal |
| **PyTelegramBotAPI (telebot)** | Interface com a API do Telegram |
| **Groq API** | Provedor de inferência do LLM |
| **Llama 3.3 70B** | Modelo de linguagem para geração de dietas |
| **LangChain + PyPDF** | Carregamento e parsing do manual em PDF |
| **Google Colab** | Ambiente de desenvolvimento e execução |

> ⚠️ **Nota:** O pacote `google-generativeai` é instalado no ambiente mas o modelo efetivamente utilizado para geração de texto é o **Llama 3.3 70B via Groq API** (`llama-3.3-70b-versatile`).

---

## 🚀 Como Executar

O projeto foi desenvolvido no **Google Colab**, que é o ambiente recomendado para execução.

### Pré-requisitos

1. Conta no **Telegram** com um bot criado via [@BotFather](https://t.me/BotFather) (guarda o token gerado)
2. Conta no **[Groq](https://console.groq.com/)** com uma API Key gerada
3. O arquivo `ResumoManualDeDietas.pdf` disponível para upload

### Passo a Passo no Google Colab

**1.** Acesse o notebook `DietasIA.ipynb` no repositório e abra-o no Google Colab.

**2.** No Colab, configure suas credenciais em `Secrets` (🔑 ícone de cadeado no menu lateral):

```
TELEGRAM_API_KEY  →  token do seu bot do Telegram
GROQ_API_KEY      →  sua chave da API do Groq
```

**3.** Faça o upload do arquivo `ResumoManualDeDietas.pdf` para `/content/` no Colab.

**4.** Execute todas as células em ordem (`Runtime > Run all`).

**5.** Abra o Telegram, encontre seu bot e envie `/dieta` para iniciar.

### Execução Local (Alternativa)

```bash
git clone https://github.com/Am4raIl/Chatbot-de-Nutricao-com-IA-Generativa.git
cd Chatbot-de-Nutricao-com-IA-Generativa
pip install google-generativeai pyTelegramBotAPI langchain langchain-groq langchain-community pypdf groq
```

Substitua as chamadas `userdata.get(...)` pelas suas chaves diretamente no código e execute o script.

---

## 📂 Estrutura do Repositório

```
📦 Chatbot-de-Nutricao-com-IA-Generativa/
├── 📓 DietasIA.ipynb              # Notebook principal com todo o código do bot
└── 📄 README.md
```

> O arquivo `ResumoManualDeDietas.pdf` (base de conhecimento clínico) não está versionado no repositório por questões de direitos autorais. É necessário providenciá-lo separadamente e fazer upload no ambiente de execução.

---

## 📚 Referências

- *Manual de Dietas Hospitalares do Hospital Geral Dr. César Cals*
- *Manual de Dietas — Serviço de Nutrição e Dietética (Rede D'Or)*
- [Documentação PyTelegramBotAPI](https://github.com/eternnoir/pyTelegramBotAPI)
- [Documentação Groq API](https://console.groq.com/docs/openai)
- [Documentação LangChain](https://python.langchain.com/)

---

<p align="center">Desenvolvido por <strong>Felipe Kitamoto Amaral</strong> — UFES 2025</p>
