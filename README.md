# 🍎 Chatbot de Dietas com Inteligência Artificial
> **Trabalho Final - Disciplina de Inteligência Artificial**

![Python](https://img.shields.io/badge/Python-3.11-blue?style=for-the-badge&logo=python&logoColor=white)
![Telegram](https://img.shields.io/badge/Telegram_Bot-2CA5E0?style=for-the-badge&logo=telegram&logoColor=white)
![Gemini AI](https://img.shields.io/badge/Google_Gemini-8E75B2?style=for-the-badge&logo=google&logoColor=white)

## 📄 Descrição Geral

Este projeto consiste em um **Chatbot de Nutrição** integrado ao **Telegram**, capaz de interagir com usuários em linguagem natural para criar planos alimentares personalizados. 

Utilizando **Modelos de Linguagem (LLMs)** através da API do **Google Gemini**, o bot coleta informações do usuário (como idade, peso, altura e objetivos) e consulta uma base de conhecimento (manuais de dietas hospitalares e nutricionais) para gerar recomendações seguras e embasadas.

### 👨‍💻 Autor
* **Felipe Kitamoto Amaral**
* *Departamento de Computação e Eletrônica (DCE) – UFES*

---

## 🤖 Funcionalidades

* **Anamnese Automatizada:** Coleta dados antropométricos e objetivos do usuário via chat.
* **Geração de Dietas:** Cria cardápios completos (café da manhã, almoço, jantar, lanches) personalizados.
* **Tira-Dúvidas:** Responde perguntas sobre nutrição e alimentos utilizando o contexto dos manuais carregados.
* **Interpretação de Documentos:** O sistema utiliza RAG (Retrieval-Augmented Generation) ou contexto injetado de manuais em PDF para fundamentar as respostas da IA.

---

## 🛠️ Tecnologias Utilizadas

* **Linguagem:** Python
* **Interface:** [PyTelegramBotAPI (Telebot)](https://github.com/eternnoir/pyTelegramBotAPI)
* **IA Generativa:** [Google Generative AI (Gemini API)](https://ai.google.dev/)
* **Manipulação de Dados:** Pandas (para estruturação de dados, se aplicável)

---

## 🚀 Como Executar

### Pré-requisitos
1.  Python 3.x instalado.
2.  Uma conta no Telegram para criar o bot via [@BotFather](https://t.me/BotFather).
3.  Uma API Key do Google AI Studio (Gemini).

### Instalação

1.  Clone o repositório:
    ```bash
    git clone [https://github.com/seu-usuario/seu-repositorio.git](https://github.com/seu-usuario/seu-repositorio.git)
    ```

2.  Instale as dependências necessárias:
    ```bash
    pip install pyTelegramBotAPI google-generativeai pandas
    ```

3.  Configure as credenciais:
    * Abra o arquivo `DietasIA.ipynb` ou o script Python correspondente.
    * Insira sua **API KEY** do Google Gemini.
    * Insira o **TOKEN** do seu Bot do Telegram.

4.  Execute o bot:
    * Rode as células do Jupyter Notebook ou execute o script `.py`.
    * Inicie uma conversa com seu bot no Telegram enviando `/start` ou `/dieta`.

---

## 🧠 Estrutura do Fluxo

1.  **Início:** O usuário envia um comando (`/dieta`).
2.  **Coleta:** O bot faz perguntas sequenciais (Idade? Peso? Altura? Objetivo?).
3.  **Processamento:** * Os dados são formatados em um prompt.
    * O conteúdo técnico (Manual de Dietas) é enviado como contexto para a IA.
4.  **Resposta:** O Google Gemini gera a dieta e o bot a envia formatada para o usuário no Telegram.

---

## 📚 Referências Teóricas

O projeto foi fundamentado em manuais reais de nutrição, como:
* *Manual de Dietas Hospitalares do Hospital Geral Dr. César Cals*
* *Manual de Dietas - Serviço de Nutrição e Dietética (Rede D'Or)*

---
*Projeto desenvolvido para fins acadêmicos na Universidade Federal do Espírito Santo (UFES).*
