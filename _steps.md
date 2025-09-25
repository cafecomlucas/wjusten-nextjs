## Configurando o Boilerplate / Limpando o projeto

Pasta do projeto criada através do comando `yarn create next-app`. Configuração feita sem recursos adicionais (TypeScript por ex.), pois a ideia é configurar manualmente.

Alguns arquivos foram removidos/editados para limpar o projeto.

---

## Configurando o TypeScript

Ao criar o arquivo `tsconfig.json` (manualmente ou através do comando `touch tsconfig.json`) e rodar o comando `yarn dev`, os tipos (`@types/node`, `@types/react`) e o próprio `typescript` foram adicionados como dependencias de desenvolvimento. O arquivo `tsconfig.json` foi modificado automaticamente.

Como o projeto é novo e será feito tudo certinho desde o começo, no arquivo `tsconfig.json` o `strict` foi setado como como `true`.

O arquivo de configuração de tipos pro next foi criado (`next-env.d.ts`) - não foi feito o commit por estar na config padrão do `.gitignore`.

O arquivo `index.js` foi alterado para `index.tsx` (ao invés de `ts`, por ser um arquivo jsx e possuir coisas visuais/html - ou seja, não é um arquivo apenas com funcionalidades). Também foi necessário ajustar o arquivo `jsconfig.json`, adicionando a linha `"jsx": "react-jsx"` por conta de erros apontados no index pelo TypeScript - correção: era cache, o arquivo `jsconfig.json` foi removido (a config já está no `tsconfig.json`).

---

## Configurando o .editorconfig

Foi criado o arquivo `.editorconfig` para setar as configurações de indentação, tipos de final de linha, charset, etc. Mesmo com o Prettier configurado depois, é interessante ter o editor config para os novos arquivos já "iniciarem" com a formatação correta, ao invés de começar com uma formatação que pode ser errada pra depois ser corrigida. É bom pra manter o padrão desde o início.

---

## Configurando o ESLint

O ESLint analisa o código enquanto está sendo digitado (variáveis, métodos, hooks), sublinhando os erros quando necessário. Pode ser utilizado com o plugin no VS Code ou sem o plugin (nesse caso é necessário rodar um comando).

O ESLint foi instalado através do comando `npx eslint --init` que executa o binário direto do repositório com as perguntas de configuração.

- Resposta 1: JavaScript
- Resposta 2: To check syntax and find problems
- Resposta 3: JavaScript modules (import/export) (esm)
- Resposta 4: React
- Resposta 5: Yes (TypeScript)
- Resposta 6: Browser
- Resposta 7: js (config file)
- Resposta 8: No (install dependencies with npm)

Sobre a resposta 2, em versões anteriores do eslint existia uma opção "To check syntax, find problems and enforce code style", que não seria selecionada pois a formatação vai ser feita através do Prettier.

Sobre a resposta 8, como o yarn está sendo utilizado, a instalação pelo npm foi cancelada e com a lista da configuração os pacotes foram instalados manualmente com o comando `yarn add --dev ...`.

---

## Configurando o ESLint (adicional)

Alguns plugins e configurações podem ser adicionados durante o projeto, e existem alguns deles que já podem ser configurados no início.

Foi instalado o plugin do React Hooks pro ESLint (`eslint-plugin-react-hooks`), que verifica se os hooks estão sendo utilizados da forma correta, se o useEffect está sendo passado de forma certa, etc.

Na configuração, o plugin pode ser setado direto na prop `extends` ou nas props `plugins` + `rules` para configurações mais específicas. Optamos pela segunda opção. Para definir as regras `rules-of-hooks` e `exhaustive-deps` foi copiado o trecho dessas regras da documentação.

Como o TypeScript vai ser o responsável pela parte de tipos, a regra do propTypes foi desativada.

Como o NextJs possui a variável `React` como global para todos os arquivos, não é necessário importa-la, por isso a regra `react/react-in-jsx-scope` foi desativada.

Como o TypeScript possui a inferência de tipos, não é necessário tipar o retorno de funções exportadas onde o TypeScript já entende qual é o tipo. Por isso a regra `@typescript-eslint/explicit-module-boundary-types` foi desligada. Isso evita que o TypeScript fica verboso. (Ainda continua sendo necessário tipar o retorno quando o TypeScript não conseguir inferir).

Também foi necessário setar a versão do React como `detect` nas configurações para o ESLint conseguir ter um parâmetro antes de verificar os arquivos.

No `package.json` foi adicionado o comando `"lint": "eslint src"` para que o lint seja verificado com o comando `yarn lint` - que verifica se existem erros, se existir - informa os erros, se passar - concluí a verificação com sucesso.

Para verificação automatica ser feita enquanto o código está sendo criado foi instalado o plugin do ESLint no VSCode.

Obs 1: a configuração foi feita no arquivo `eslint.config.mjs` que é a nova maneira. Utilizar o arquivo `.eslintrc` se tornou obsoleto.

Obs 2: as linhas `tseslint.configs.recommended` e `pluginReact.configs.flat.recommended` foram movidas pro topo para poderem ser sobrescritas pela prop `rules`.

---
