# Estrutura do código

Tudo vive em `index.html`. Um arquivo, sem build, sem dependências. Cerca de 6.400 linhas divididas em três blocos: `<style>`, os dados e o motor de renderização.

---

## Mapa do arquivo

O JavaScript é comentado por seções numeradas. Procure pelo comentário para achar cada bloco:

| Seção | O que é |
| --- | --- |
| `1. DISCIPLINAS` | `SUBJECTS` — as cinco matérias |
| `1b. AULAS` | `LESSONS` — as aulas transcritas |
| `1c. FICHA DO MÓDULO` | `MODINFO` — a ementa oficial do professor |
| `1d. LABORATÓRIO DE FIW115` | `LAB` — monitoria, janelas, grade dos monitores |
| `1e. EXECUÇÃO PASSO A PASSO` | `EXEC` — o guia de bancada |
| `2. ESTADO PERSISTENTE` | `KEY`, `DEF`, `load()`, `save()` |
| `3. UTILITÁRIOS` | datas, slugs, ícones SVG |
| `4. NAVEGAÇÃO` | `TABS`, `route`, `render()` |
| `5` a `10` | uma seção por aba |
| `11. TEMA + BACKUP` | claro/escuro e exportar/importar estado |

`GLOSS` guarda os 108 termos do glossário como arrays de cinco posições: `[categoria, termo, definição curta, detalhe, módulo]`.

---

## Como os dados são organizados

### Disciplina

```js
{
  code:'CMA110', short:'Ciências da Terra', name:'Tópicos Gerais de Ciências da Terra',
  cred:5, color:'#C2751B', grad:'linear-gradient(...)', icon:'globe',
  room:'F3-001', prof:'Paulo Lopes (módulo de Astronomia)',
  topics:[ {t:'Título do tópico', s:['subtópico','subtópico']} ],
  cards:[ {q:'pergunta', a:'resposta'} ],
  quiz:[ {q:'pergunta', o:['a','b','c','d'], c:0, e:'explicação'} ]
}
```

`c` é o índice da alternativa correta em `o`. `color` propaga para tudo que pertence àquela matéria — anel de progresso, célula da grade, borda do prazo.

### Aula

```js
{
  n:1, kind:'Módulo de Astronomia', title:'...', date:'...', src:'Slides ...',
  order:['0','1','2',...],        // opcional — ordem de exibição dos módulos
  refs:[ 'referência 1', ... ],   // lista numerada de fontes
  refmap:[ ['módulo','quais refs'] ],
  html:`...`
}
```

### Experimento (guia de bancada)

```js
{
  n:1, tit:'Propagação da luz num meio homogêneo', tempo:'≈ 45 min',
  fases:[
    { f:'A · Montagem', t:'8 min', p:[ 'micro-passo', 'micro-passo' ] }
  ]
}
```

Cada string de `p` é **uma ação só** e vira uma linha marcável. Aceita HTML inline — `<b>` para o que não pode ser feito fora de ordem.

---

## O sistema de módulos

O corpo de cada aula é uma template string HTML grande. `lessonModules(L)` a fatia em módulos dividindo por `<div class="lsec">` e, para cada pedaço:

1. Extrai o `<h3><span class="lnum">X</span>Título</h3>` — `lnum` vira o número do módulo no índice lateral.
2. Conta as palavras ignorando SVG e tags, e estima o tempo de leitura a 190 palavras por minuto.
3. Guarda tudo em `L._mods`, que fica em cache — a fatia só acontece uma vez.

No fim, acrescenta automaticamente o módulo **F · Fontes**, montado a partir de `refmap` e `refs`. Ninguém escreve esse módulo à mão.

### Reordenar sem mover blocos

`L.order` é um array com os `lnum` na ordem desejada. Se existir, `lessonModules` ordena por ele. É como a numeração dos experimentos de Ótica foi corrigida sem recortar e colar blocos de HTML de centenas de linhas.

---

## Estado

Um objeto só, em `localStorage`, sob a chave `painel-cmt-v1`:

```js
{
  theme, done:{}, cardBox:{}, notes:{}, deadlines:[],
  quiz:{}, read:{}, exp:{}, execDone:{},
  pomo:{date,count}, pomoHist:{}
}
```

`load()` faz `Object.assign` sobre `DEF`, então acrescentar uma chave nova não quebra o estado salvo de quem já usava a versão anterior.

> **Regra que não pode ser quebrada.** As chaves de `done`, `read` e `cardBox` são **slugs dos títulos**. Renomear um tópico ou um cartão apaga o progresso salvo daquele item. Ao editar, mude o texto explicativo à vontade — mas pense duas vezes antes de mexer num título.

`execDone` é indexado por `'<nº do experimento>:<índice global do passo>'`, contado na ordem em que os passos aparecem nas fases.

---

## Renderização

`render()` reconstrói a aba inteira a partir de `route` e chama o `bind*()` correspondente para religar os eventos. É simples e funciona — mas `render()` também rola a página para o topo.

Por isso o guia de bancada **não** chama `render()` ao marcar um passo: `updateExecProgress()` atualiza só o percentual, o contador e a barra, direto no DOM. Numa lista de 42 passos com o celular na mão, saltar para o topo a cada toque inviabilizaria o uso.

Se você adicionar outro elemento marcável dentro de uma lista longa, siga o mesmo padrão.

---

## Ilustrações

Não há um único arquivo de imagem no repositório. Todas as figuras são SVG escrito à mão ou gerado por código no próprio `index.html` — estratos geológicos, diagramas de raios, esfera celeste, gráficos.

As cores usam `var(--...)` e `color-mix(in srgb, ...)`, então tudo acompanha o tema claro/escuro sem duplicação.

---

## Adicionar uma aula nova

1. Acrescente um objeto ao array da disciplina em `LESSONS`.
2. Escreva o corpo em `html`, um `<div class="lsec">` por módulo, cada um abrindo com `<h3><span class="lnum">N</span>Título</h3>`.
3. Preencha `refs` com a lista numerada de fontes e `refmap` ligando módulo a referência. O módulo de fontes se monta sozinho.
4. Se quiser exibir os módulos fora da ordem em que estão escritos, adicione `order`.
5. Se a aula trouxer termos novos, acrescente linhas a `GLOSS` apontando para o módulo.

Nada mais precisa ser tocado — o índice lateral, os tempos de leitura, o mapa da aula e a contagem de módulos saem dos dados.
