## Alura Studies – Cronômetro de Estudos (React + TypeScript)

Aplicação para organizar sessões de estudo com uma lista de tarefas e um cronômetro regressivo. Projeto desenvolvido em React com TypeScript, usando CSS Modules (SCSS) e `uuid` para identificação das tarefas.

### Demonstração rápida

- Adicione uma tarefa informando o tema e o tempo desejado (hh:mm:ss)
- Clique em “Adicionar” para incluir na lista
- Selecione um card na lista
- Inicie o cronômetro e, ao chegar em zero, a tarefa é marcada como concluída

---

## Requisitos

- Node.js (recomendado 18+)
- npm (ou yarn/pnpm, se preferir)

## Instalação e execução

```bash
npm install
npm start
```

A aplicação iniciará em `http://localhost:3000`.

## Scripts disponíveis

- `npm start`: inicia o servidor de desenvolvimento
- `npm test`: executa a suíte de testes (Testing Library)
- `npm run build`: gera build de produção em `build/`
- `npm run eject`: expõe configurações do Create React App (irreversível)

## Tecnologias e bibliotecas

- React 19 + ReactDOM
- TypeScript
- CSS Modules com SCSS
- uuid
- Testing Library (React, DOM, Jest-DOM, User-Event)

## Estrutura do projeto

```text
alura-studies/
  public/
  src/
    assets/
      img/
    common/
      utils/
        time.ts               # Conversão de string de tempo para segundos
    components/
      Botao/
      Cronometro/
        Relogio/
      Formulario/
      Lista/
        Item/
    pages/
      App.tsx                 # Composição principal da tela
    types/
      tarefa.ts               # Definição de ITarefa
```

## Principais componentes

- `pages/App.tsx`
  - Mantém o estado global de `tarefas` (`ITarefa[]`) e a tarefa `selecionado`
  - Funções de seleção e finalização atualizam o estado (selecionado/completado)
- `components/Formulario`
  - Formulário controlado para adicionar tarefas
  - Campos: `tarefa` (texto) e `tempo` (input `time`, com step de 1s)
  - Gera `id` com `uuid`
- `components/Lista` e `components/Lista/Item`
  - Exibe a lista de tarefas, permite selecionar um card (desabilita clique quando já concluído)
- `components/Cronometro`
  - Converte o tempo selecionado em segundos (`common/utils/time.ts`)
  - Faz contagem regressiva com `setTimeout` e, ao terminar, dispara `finalizarTarefa`
  - `Relogio` formata e exibe mm:ss
- `components/Botao`
  - Botão estilizado reutilizável com CSS Modules

## Tipos

- `types/tarefa.ts`
  - `ITarefa`:
    - `tarefa: string`
    - `tempo: string` (formato hh:mm:ss)
    - `selecionado: boolean`
    - `completado: boolean`
    - `id: string`

## Estilos

- CSS Modules com SCSS (`*.module.scss`), garantindo escopo local por componente.

## Testes

```bash
npm test
```

Suíte configurada com Testing Library. Ajuste/adicione testes conforme necessário.

## Build e deploy

```bash
npm run build
```

Gera a pasta `build/` otimizada para produção, pronta para ser publicada em qualquer serviço de hospedagem estática.

## Como usar

1. Abra a aplicação
2. Preencha o título da tarefa e o tempo desejado
3. Clique em “Adicionar”
4. Clique no card da tarefa para selecioná-la
5. Pressione “Começar!” no cronômetro
6. Ao finalizar a contagem, a tarefa é marcada como concluída

---

Projeto criado com Create React App, adaptado para fins educativos no curso da Alura.
