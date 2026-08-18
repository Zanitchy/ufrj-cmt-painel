# Painel CMT · UFRJ

Painel de estudos do 1º período do Bacharelado em Ciências Matemáticas e da Terra da UFRJ — Turma B, 2026/1.

**[▶ Abrir o painel](https://zanitchy.github.io/ufrj-cmt-painel/)**

Cinco disciplinas, as aulas transcritas em módulos navegáveis, um guia de bancada para os experimentos de laboratório, glossário, flashcards, quiz e cronômetro de foco. Página única, sem build, sem dependências, sem requisições de rede. Abre offline com duplo clique.

---

## As cinco disciplinas

| Código | Disciplina | Créditos | Sala |
| --- | --- | --- | --- |
| MAW117 | Introdução ao Cálculo | 4 | F3-001 |
| FIW115 | Introdução às Ciências Físicas | 4 | F3-012 / LEP 2 |
| CMA110 | Tópicos Gerais de Ciências da Terra | 5 | F3-001 |
| CMT111 | Inovações Científicas, Tecnológicas e Artísticas I | 2 | F3-001 |
| CMTZ500 | Atividade Curricular de Extensão CMT | 0 | — |

Cada disciplina tem cartão próprio com ementa em tópicos e subtópicos marcáveis, flashcards e quiz com explicação da resposta. A cor de cada uma atravessa o painel inteiro — barra de progresso, grade horária, prazos.

---

## O que tem dentro

### Painel

Anéis de progresso por disciplina, agenda do dia lida da grade horária, próximos prazos ordenados por urgência e um bloco de anotações livres por matéria.

### Grade horária

Semana em blocos de duas horas, 2ª a 6ª, com a aula corrente destacada em tempo real.

### Matérias

O grosso do conteúdo. Cada disciplina abre em três abas: **Aulas**, **Flashcards** e **Quiz**. FIW115 tem uma quarta, **Laboratório**.

### Provas e prazos

Contagem regressiva por prazo, com as janelas de experimento e as datas de relatório de FIW115 já carregadas.

### Foco

Pomodoro com histórico dos últimos dias.

---

## As aulas de CMA110 (módulo de Astronomia)

Prof. Paulo Afranio Augusto Lopes. Três aulas integradas até aqui, cada uma quebrada em módulos curtos com índice lateral fixo, tempo de leitura estimado por módulo e ilustrações em SVG geradas por código.

| Aula | Título | Módulos |
| --- | --- | --- |
| 01 | Astronomia: visão geral, o Brasil e o OV/UFRJ | 25 |
| 02 | Escalas, tempo, calendários e o método científico | 28 |
| 03 | Esfera celeste, movimentos da Terra, eclíptica e estações | 23 |

O último módulo de cada aula é sempre **F · Fontes**: uma tabela que liga cada módulo às referências usadas nele, seguida da lista numerada completa. O conteúdo dos slides do professor foi mantido e complementado — e onde a complementação divergiu do material original, a divergência está registrada no próprio módulo, com a fonte primária ao lado.

Também há um módulo por aula antecipando como o assunto tende a cair na prova, e um **glossário de 95 termos** em cartões clicáveis, cada um ligado ao módulo em que aparece.

---

## Laboratório de FIW115

A aba de laboratório tem três seções independentes.

### 1. Roteiro dos experimentos

Os sete experimentos de Ótica da Unidade 1, em 12 módulos, a partir do roteiro oficial da disciplina. Cada experimento traz o procedimento, a teoria que o sustenta, os erros comuns e a forma correta de registrar o resultado com incerteza.

> **Nota sobre a numeração.** O índice da página 1 do roteiro está em ordem diferente dos cabeçalhos das seções. O painel segue os **cabeçalhos** — Experimento 3 é *O método dos raios*, como diz a seção, não *Interação luz-matéria*, como sugere o índice.

### 2. Execução passo a passo

Guia de bancada. Os mesmos sete experimentos decompostos em **200 micro-passos marcáveis**, distribuídos em **34 fases cronometradas** (A · Montagem, B · Exploração qualitativa, C · Primeira medida completa…).

Cada passo é uma ação só. Inclui as ações que costumam ser esquecidas e custam a nota: pedir para escurecer a sala, marcar a posição da máscara na mesa antes de começar, desenhar a tabela no caderno *antes* de medir. Cada experimento fecha com uma fase de saída que inclui fotografar as anotações e confirmar o registro com o monitor.

| Exp | Título | Fases | Passos | Tempo |
| --- | --- | --- | --- | --- |
| 1 | Propagação da luz num meio homogêneo | 6 | 42 | ≈ 45 min |
| 2 | Emissão da luz por diferentes fontes | 5 | 27 | ≈ 35 min |
| 3 | O método dos raios | 5 | 29 | ≈ 40 min |
| 4 | Formação de imagens por um espelho plano | 5 | 32 | ≈ 45 min |
| 5 | Interação da luz com a matéria | 4 | 33 | ≈ 50 min |
| 6 | A luz se propaga em linha reta | 4 | 18 | ≈ 25 min |
| 7 | Raios de luz vão e voltam pelo mesmo caminho | 5 | 19 | ≈ 30 min |

O progresso é por experimento e fica salvo. Marcar um passo não rola a página — o guia foi feito para ser usado com o celular na mão, na bancada.

### 3. Como funciona a monitoria

Sala F2-40. As três janelas de marcação, o passo a passo da marcação pelo grupo de WhatsApp, o que penaliza conceito, como o conceito entra na nota final e a grade semanal dos cinco monitores por faixa de horário.

| Janela | Período | Experimentos |
| --- | --- | --- |
| 1 | 17/08 – 11/09 | Ótica 1, 2, 3 e 4 |
| 2 | 14/09 – 09/10 | Ótica 5, 6 e 7 |
| 3 | 19/10 – 19/11 | Elétrica 8, 9 e 10 |

Envio do relatório em 19/11, entrega em 27/11.

> **Contatos.** A grade de horários e os nomes dos monitores estão no painel. **Telefones e e-mails não** — são dados pessoais e ficam só no grupo da turma.

---

## Rodar localmente

```
git clone https://github.com/Zanitchy/ufrj-cmt-painel.git
cd ufrj-cmt-painel
```

E abrir `index.html` no navegador. Não há servidor, não há `npm install`, não há passo de build.

---

## Estrutura do repositório

```
ufrj-cmt-painel/
├── index.html      # o painel inteiro — HTML, CSS e JS num arquivo só
├── README.md
├── LICENSE         # MIT
├── .nojekyll       # desliga o Jekyll no GitHub Pages
└── ESTRUTURA.md    # como o código funciona e como adicionar uma aula
```

## Stack

Nenhuma. HTML, CSS e JavaScript sem framework, sem bibliotecas, sem CDN. Todas as ilustrações são SVG gerado por código — não há um único arquivo de imagem no repositório.

O estado do usuário (tópicos concluídos, flashcards, quiz, anotações, prazos, passos de experimento, pomodoro) vive num único objeto em `localStorage`, sob a chave `painel-cmt-v1`. Limpar os dados do site zera tudo.

Detalhes de implementação em [`ESTRUTURA.md`](ESTRUTURA.md).

---

## Fonte dos dados

- Slides de aula de CMA110 — Tópicos Gerais de Ciências da Terra, módulo de Astronomia, Prof. Paulo Afranio Augusto Lopes (IF/OV — UFRJ), aulas 01 a 03 de 2026/1
- Ementa do módulo de Astronomia de CMA110
- Roteiro de experimentos de Ótica, Unidade 1 — Introdução às Ciências Físicas (FIW115)
- Apresentação da monitoria de FIW115 e grade de horários dos monitores, 2026/1
- Referências complementares listadas módulo a módulo no módulo **F · Fontes** de cada aula

## Aviso

Projeto pessoal de estudo, sem vínculo oficial com a UFRJ. É uma leitura do material de aula, não um sistema institucional, e não substitui os slides do professor nem o roteiro oficial do laboratório. Erros de transcrição são possíveis — confirme com o professor ou com a monitoria antes de contar com qualquer número daqui numa avaliação.

Encontrou um erro? Abra uma issue.

## Licença

Código sob MIT. O material didático referenciado pertence a seus autores.
