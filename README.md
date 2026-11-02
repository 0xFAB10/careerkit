# 🚀 Profile Optimizer — Kit completo para carreira

Ferramenta de carreira baseada em IA que otimiza seu LinkedIn, GitHub, currículo, preparação para entrevistas, busca de empregos e muito mais — tudo em uma única aplicação.

Funciona com **qualquer modelo de IA compatível**: Claude, OpenAI GPT-4o, Google Gemini (gratuito), Groq (gratuito) ou Ollama (gratuito, local e offline).

---

## Sobre este fork

Este projeto é um fork do [CareerKit original](https://github.com/humaniods/careerkit ), criado por [Sanyam Sharma](https://github.com/humaniods ).

A versão original serve como base para este trabalho. Este fork é mantido por **Fabio Araújo (0xFAB10)** e tem como objetivos:

- traduzir a interface, a documentação e as mensagens do projeto para português do Brasil;
- tornar a ferramenta mais acessível para pessoas brasileiras;
- estudar o uso diário da aplicação e identificar oportunidades de melhoria;
- automatizar gradualmente algumas funções relacionadas à carreira, à busca de vagas e à preparação profissional;
- adaptar e evoluir o projeto de acordo com as necessidades observadas durante o uso.

As automações ainda estão em fase de planejamento. As funções serão definidas a partir da experiência prática com a aplicação e, portanto, esta seção representa intenções futuras, não funcionalidades já implementadas.

As alterações deste fork são independentes do desenvolvimento do projeto original. Consulte o repositório original para acompanhar a versão principal e seus créditos.

---

## Destaques de engenharia

O CareerKit é uma **aplicação Python completa** para análise de perfis e fluxos de busca de emprego. O projeto foi desenvolvido para trabalhar com vários provedores de modelos de linguagem, em vez de depender de uma única API.

- **Camada da aplicação:** interface em Streamlit com ferramentas separadas para revisão de perfil, geração de currículo, comparação com descrições de vagas e preparação para entrevistas.
- **Abstração de provedores:** suporte documentado a APIs de IA hospedadas e a modelos Ollama executados localmente, permitindo escolher entre flexibilidade e inferência local.
- **Leitura de documentos:** extrai o conteúdo de PDFs exportados do LinkedIn para que as análises utilizem a mesma fonte de informações.
- **Fluxo orientado à privacidade:** configurações locais e ausência de armazenamento dos dados em um servidor próprio da aplicação. O usuário deve consultar também as políticas de tratamento de dados do provedor de IA escolhido.
- **Decisões de engenharia:** os mesmos recursos podem ser executados por provedores diferentes, mas qualidade, latência, janela de contexto, preço e privacidade dependem do provedor selecionado.

**O que pode ser analisado:** [app.py](app.py), que contém a aplicação e o fluxo de integração com os modelos; [requirements.txt](requirements.txt), que lista as dependências; e este README, que documenta uma configuração reproduzível.

O projeto original foi criado por [Sanyam Sharma](https://github.com/humaniods ), Voice AI Engineer com foco em fala multilíngue, aplicações com LLMs e desenvolvimento de back-end em Python.

---

## O que esta ferramenta faz

Uma aplicação com 10 ferramentas — carregue seu PDF do LinkedIn uma vez e use as informações em todas elas:

| Nº | Ferramenta | Entrada | Saída |
|---|---|---|---|
| 1 | **📋 Otimizador do LinkedIn** | PDF do LinkedIn | Título, seção Sobre, experiências e ordem das competências reescritos |
| 2 | **🐙 Otimizador do GitHub** | Nome de usuário do GitHub | Biografia, README de perfil, descrições de repositórios e lista de projetos fixados otimizados |
| 3 | **🎯 Comparador com vaga** | PDF do LinkedIn + descrição da vaga | Percentual de compatibilidade, lacunas de competências e indicação sobre se vale a pena candidatar-se |
| 4 | **📄 Currículo ATS** | PDF do LinkedIn | Currículo limpo e compatível com sistemas ATS em Markdown |
| 5 | **🛠️ Sugestões de projetos** | PDF do LinkedIn + cargo desejado | 7 ideias de projetos com tecnologias, dificuldade e estimativa de tempo |
| 6 | **🎤 Preparação para entrevista** | PDF do LinkedIn + cargo + empresa | Perguntas personalizadas, respostas de exemplo e faixa salarial |
| 7 | **📧 Abordagem profissional** | PDF do LinkedIn + empresa desejada | 9 modelos: mensagens do LinkedIn, e-mails e pedidos de indicação |
| 8 | **📊 Análise de lacunas de competências** | PDF do LinkedIn + cargo desejado | Grau de preparo para o mercado e roteiro mensal de aprendizagem |
| 9 | **🔍 Palavras-chave para vagas** | PDF do LinkedIn + localização | Strings de busca para LinkedIn, Naukri, Indeed e Google |
| 10 | **✉️ Carta de apresentação** | PDF do LinkedIn + descrição da vaga | Carta de apresentação personalizada pronta para enviar |

---

## Provedores de IA compatíveis

Você escolhe qual IA usar. O projeto **não exige um único provedor**.

| Provedor | Custo por uso | Velocidade | Qualidade | Possui plano gratuito? |
|---|---:|---|---|---|
| **Claude** (Anthropic) | ~US$ 0,01–0,05 | Rápida | ⭐⭐⭐⭐⭐ | Não — cobrança por uso |
| **OpenAI** (GPT-4o) | ~US$ 0,01–0,05 | Rápida | ⭐⭐⭐⭐⭐ | Crédito gratuito de US$ 5 no cadastro |
| **Google Gemini** | **Gratuito** | Rápida | ⭐⭐⭐⭐ | ✅ Sim — plano gratuito generoso |
| **Groq** (Llama 3, Mixtral) | **Gratuito** | Mais rápida | ⭐⭐⭐⭐ | ✅ Sim — plano gratuito |
| **Ollama** (executado no computador) | **Gratuito para sempre** | Lenta — depende do computador | ⭐⭐⭐ | ✅ Totalmente offline, sem necessidade de conta |

### Onde obter as chaves de API

| Provedor | Link de cadastro | Etapas |
|---|---|---|
| **Claude** | https://console.anthropic.com | Cadastre-se → API Keys → Create Key → copie `sk-ant-...` |
| **OpenAI** | https://platform.openai.com/api-keys | Cadastre-se → API Keys → Create → copie `sk-...` |
| **Gemini** | https://aistudio.google.com/apikey | Entre com o Google → Get API Key → copie a chave |
| **Groq** | https://console.groq.com/keys | Cadastre-se → API Keys → Create → copie `gsk_...` |
| **Ollama** | https://ollama.com | Baixe e instale — não é necessária uma chave |

---

## Instalação e configuração

### Pré-requisitos

- **Python 3.10 ou superior** — verifique com `python3 --version`;
- **pip** — acompanha o Python; verifique com `pip --version`;
- **Conexão com a internet** — necessária para a API do GitHub e para as APIs dos provedores de IA;
- **Um navegador da web** — a aplicação abre no navegador padrão.

### Etapa 1: Baixar o projeto

**Opção A — Clonar com Git:**

```bash
git clone https://github.com/humaniods/careerkit.git
cd careerkit
```

> Este é o endereço do projeto original. Para trabalhar com este fork, use o endereço do seu próprio repositório:
>
> ```bash
> git clone https://github.com/0xFAB10/careerkit.git
> ```

**Opção B — Baixar manualmente:**

1. Baixe o arquivo ZIP pelo GitHub;
2. Extraia o conteúdo;
3. Abra o terminal na pasta extraída.

### Etapa 2: Instalar as dependências

```bash
pip install -r requirements.txt
```

Isso instala:

| Pacote | Função | Tamanho aproximado |
|---|---|---:|
| `streamlit` | Interface web — a aplicação é executada no navegador | ~80 MB |
| `pdfplumber` | Leitura do texto do PDF do LinkedIn | ~5 MB |
| `requests` | Chamadas para as APIs do GitHub, Gemini e Groq | ~1 MB |
| `anthropic` | SDK de IA do Claude — opcional se não for usar Claude | ~5 MB |
| `openai` | SDK da OpenAI — opcional se não for usar OpenAI | ~5 MB |

**Se você quiser usar apenas provedores gratuitos (Gemini, Groq ou Ollama):**

```bash
pip install streamlit pdfplumber requests
```

Nesse caso, não é necessário instalar `anthropic` ou `openai`. Gemini e Groq usam a API REST diretamente.

### Etapa 3: Executar a aplicação

```bash
streamlit run app.py
```

**O que acontece:**

1. O terminal mostra `Local URL: http://localhost:8501`;
2. O navegador abre automaticamente nesse endereço;
3. Se o navegador não abrir, acesse manualmente `http://localhost:8501`.

### Etapa 4: Configuração inicial na aplicação

1. Na **barra lateral esquerda**, selecione o provedor de IA — por exemplo, Google Gemini;
2. **Insira a chave de API** — use a tabela acima para saber onde obtê-la;
3. A chave é **salva automaticamente** em `~/.profile_optimizer/config.json`;
4. Essa configuração só precisa ser feita uma vez — nas próximas execuções, a chave já estará disponível.

### Etapa 5: Começar a usar

1. Acesse a aba **📋 LinkedIn**;
2. Envie seu PDF do LinkedIn;
3. Clique em **Otimizar** para obter os resultados;
4. Alterne entre as outras abas — seu perfil já estará carregado e não será necessário enviá-lo novamente.

---

## Como obter seu PDF do LinkedIn

1. Abra o LinkedIn em um navegador — não use o aplicativo para celular;
2. Acesse a página do seu perfil;
3. Clique no botão **Mais**, abaixo da imagem de capa;
4. Clique em **Salvar em PDF**;
5. Um arquivo PDF será baixado. Esse é o arquivo que você deve enviar para a aplicação.

---

## Como parar a aplicação

Pressione `Ctrl+C` no terminal em que você executou `streamlit run app.py`.

---

## Usando o Ollama (gratuito, local e offline)

O Ollama executa modelos de IA no seu próprio computador — gratuitamente, sem necessidade de conta e sem conexão com a internet para o processamento da IA.

### Configurar o Ollama

**Linux:**

```bash
curl -fsSL https://ollama.com/install.sh | sh
```

**Mac:**

```bash
brew install ollama
```

**Windows:**

Baixe o instalador em https://ollama.com/download

### Baixar um modelo

```bash
ollama pull llama3.1
```

Esse comando baixa o modelo — aproximadamente 4,7 GB para o `llama3.1` 8B. O download é feito apenas uma vez.

### Iniciar o servidor

```bash
ollama serve
```

Mantenha esse terminal aberto. Em outro terminal, execute a aplicação:

```bash
streamlit run app.py
```

Selecione **Ollama (Local — Gratuito)** na barra lateral. Os modelos baixados serão identificados automaticamente.

### Qual modelo do Ollama usar?

| Modelo | Memória RAM necessária | Qualidade | Velocidade |
|---|---:|---|---|
| `llama3.1` (8B) | 8 GB | Boa | Rápida |
| `llama3.1:70b` | 40 GB | Ótima | Lenta |
| `mistral` (7B) | 8 GB | Boa | Rápida |
| `qwen2.5` (7B) | 8 GB | Boa | Rápida |

Para a maioria dos computadores, o `llama3.1` funciona bem.

---

## Guia detalhado das ferramentas

### 📋 Otimizador do LinkedIn

**O que você recebe:**

- Título reescrito, com menos de 220 caracteres e palavras-chave relevantes para ATS;
- Nova seção Sobre, com gancho inicial, verbos de ação e chamada para ação no final;
- Experiências reescritas no formato STAR — Situação, Tarefa, Ação e Resultado;
- Competências reorganizadas por relevância para recrutadores;
- Apresentação profissional de 30 segundos;
- Ideia de publicação para aumentar sua visibilidade no LinkedIn;
- Lista dos problemas encontrados e corrigidos no seu perfil atual.

### 🎯 Comparador com descrição de vaga

**O que você recebe:**

- Índice de compatibilidade de 0 a 100%;
- Veredito **Devo me candidatar?** — Sim, Não ou Talvez;
- Competências compatíveis e competências ausentes;
- Lacunas de palavras-chave;
- Título personalizado para aquela vaga;
- Itens de currículo para acrescentar de acordo com a vaga;
- Plano de ação com 5 etapas para aumentar suas chances.

### 📄 Currículo ATS

**O que ele corrige:**

- Remove formatações complexas, pois sistemas ATS podem não interpretar colunas e tabelas corretamente;
- Usa verbos de ação fortes, como Construí, Desenvolvi e Otimizei;
- Acrescenta métricas e números;
- Inclui palavras-chave relevantes de forma natural;
- Mantém uma estrutura limpa: Resumo → Experiência → Competências → Formação.

### 🛠️ Sugestões de projetos

**O que você recebe por projeto:**

- Nome do projeto e frase de apresentação;
- Explicação de como o projeto ajuda a preencher uma lacuna de competência;
- Stack tecnológico completo;
- Nível de dificuldade e estimativa de tempo;
- Principais funcionalidades a implementar;
- Descrição do repositório no GitHub pronta para colar;
- Explicação de por que o projeto pode impressionar recrutadores.

### 🎤 Preparação para entrevista

**Escolha o tipo de entrevista:**

- Técnica e comportamental — mista;
- Aprofundamento técnico;
- Comportamental e compatibilidade cultural;
- Design de sistemas;
- RH e triagem inicial.

**O que você recebe:**

- Apresentação inicial para responder a “Fale sobre você”;
- De 10 a 15 perguntas com respostas personalizadas a partir da sua experiência;
- Perguntas para fazer ao entrevistador;
- Sinais de alerta a evitar;
- Sugestão de faixa salarial.

### 📧 Abordagem profissional — 9 modelos

1. Nota de conexão do LinkedIn, com menos de 300 caracteres;
2. Mensagem para recrutador;
3. Mensagem para gerente de contratação;
4. Mensagem solicitando indicação;
5. Mensagem para fundador ou CTO de startup;
6. Modelo de e-mail de abordagem;
7. Follow-up após não receber resposta;
8. Pedido de indicação a um conhecido;
9. Agradecimento após entrevista.

### 📊 Análise de lacunas de competências

**O que você recebe:**

- Índice de preparo para o mercado, de 0 a 100%;
- Competências que você possui e competências exigidas;
- Classificação de cada lacuna: Crítica, Importante ou Desejável;
- Como aprender cada competência e estimativa de tempo;
- Roteiro mensal de aprendizagem com recursos específicos;
- Certificações recomendadas.

### 🔍 Palavras-chave para vagas

**Strings de busca para:**

- Vagas do LinkedIn — 10 consultas;
- Naukri.com — 10 consultas;
- Indeed — 10 consultas;
- Google Jobs — 5 consultas, como `site:lever.co "AI Engineer" "India"`;
- Busca booleana avançada;
- 15 variações de cargos para pesquisar;
- 20 empresas para acompanhar;
- Sites de vagas de nicho para sua área;
- Hashtags para seguir;
- Alertas do Google para configurar.

### ✉️ Carta de apresentação

**O que torna a carta eficiente:**

- Começa com um gancho, e não com “Estou escrevendo para me candidatar”;
- Relaciona sua experiência aos requisitos da vaga;
- Demonstra conhecimento sobre a empresa;
- Inclui de 2 a 3 conquistas com números;
- Termina com uma chamada para ação confiante;
- Tem menos de 400 palavras e mantém uma linguagem natural.

---

## Compartilhamento inteligente do perfil

Envie seu PDF do LinkedIn **uma única vez**, em qualquer aba, e ele ficará automaticamente disponível em **todas as outras abas**. Não é necessário fazer o upload novamente.

---

## Estrutura do projeto

```text
careerkit/
├── app.py                 # Aplicação principal — todas as 10 ferramentas (Streamlit)
├── requirements.txt       # Dependências do Python
├── .gitignore             # Impede o versionamento de segredos e arquivos gerados
└── README.md              # Este arquivo
```

---

## Privacidade e segurança

- As **chaves de API** são salvas localmente em `~/.profile_optimizer/config.json` e nunca são enviadas para outro local pela aplicação;
- Os **dados do seu perfil** são enviados somente ao provedor de IA escolhido e não são armazenados em um servidor da aplicação;
- Não há analytics, rastreamento ou telemetria — a aplicação não se comunica com um servidor próprio;
- Com o **Ollama**, o processamento é totalmente offline e nenhum dado deixa o seu computador;
- A aplicação é executada localmente no seu computador, em `localhost:8501`, e não fica acessível pela internet por padrão.

> Consulte sempre as políticas de privacidade do provedor de IA escolhido antes de enviar dados pessoais ou profissionais.

---

## Solução de problemas

| Problema | Causa | Solução |
|---|---|---|
| `ModuleNotFoundError: No module named 'streamlit'` | Dependências não instaladas | Execute `pip install -r requirements.txt` |
| `ModuleNotFoundError: No module named 'anthropic'` | Uso do Claude sem o SDK | Execute `pip install anthropic` |
| `ModuleNotFoundError: No module named 'openai'` | Uso da OpenAI sem o SDK | Execute `pip install openai` |
| A aplicação informa “Enter API key” | Chave não configurada | Cole sua chave de API na barra lateral |
| “API Error: 401” | Chave de API inválida | Verifique se a chave está correta e não expirou |
| “API Error: 429” | Limite de requisições atingido | Aguarde um minuto e tente novamente ou troque de provedor |
| A extração do texto do PDF está vazia | Problema no formato do PDF do LinkedIn | Exporte o PDF novamente usando o navegador Chrome |
| Falha ao consultar o GitHub | Nome de usuário incorreto ou perfil privado | Verifique a grafia e confirme que o perfil é público |
| Erro ao interpretar JSON | A IA retornou uma resposta malformada | Clique no botão novamente ou tente outro modelo |
| Ollama não encontrado ou conexão recusada | O servidor do Ollama não está em execução | Execute `ollama serve` em outro terminal |
| Resposta do Ollama muito lenta | O modelo é grande demais para o computador | Use um modelo menor: `ollama pull llama3.1` |
| O navegador não abre | Ambiente sem interface gráfica ou conexão SSH | Abra manualmente `http://localhost:8501` |
| A porta 8501 já está em uso | Outra aplicação Streamlit está em execução | Encerre-a com `pkill -f streamlit` e tente novamente |
| `python3: command not found` | Python não está instalado | Instale Python 3.10 ou superior em https://www.python.org |

---

## Perguntas frequentes

**P: Este projeto é gratuito?**  
R: A aplicação é gratuita. Os custos de IA dependem do provedor escolhido. Gemini, Groq e Ollama oferecem opções gratuitas.

**P: Meus dados estão seguros?**  
R: A aplicação é executada localmente. Os dados são enviados somente ao provedor de IA que você escolher. Verifique também a política de privacidade desse provedor.

**P: Posso usar a aplicação sem internet?**  
R: Parcialmente. Com o Ollama, o processamento da IA funciona offline, mas a consulta ao GitHub ainda precisa de internet.

**P: Qual provedor é melhor?**  
R: Claude e GPT-4o oferecem a melhor qualidade geral. Gemini é uma boa opção gratuita e Groq é a opção mais rápida. O Ollama é indicado quando a prioridade é executar tudo localmente.

**P: Preciso instalar todas as dependências?**  
R: Não. Se você usar apenas Gemini, Groq ou Ollama, `pip install streamlit pdfplumber requests` é suficiente.

---

## Licença

MIT — use, modifique e compartilhe.

---

## Créditos e referência

Este projeto é um fork e uma adaptação do [CareerKit original](https://github.com/humaniods/careerkit ), criado por [Sanyam Sharma](https://github.com/humaniods ).

As traduções, adaptações e futuras melhorias deste fork são mantidas por **Fabio Araújo (0xFAB10)**. Consulte o repositório original para conhecer a implementação de referência e acompanhar o trabalho do autor original.
