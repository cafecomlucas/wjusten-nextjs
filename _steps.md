## Configurando o Boilerplate / Limpando o projeto

Pasta do projeto criada através do comando `yarn create next-app`. Configuração feita sem recursos adicionais (TypeScript por ex.), pois a ideia é configurar manualmente.

Alguns arquivos foram removidos/editados para limpar o projeto.

---

## Configurando o TypeScript

Ao criar o arquivo `tsconfig.json` (manualmente ou através do comando `touch tsconfig.json`) e rodar o comando `yarn dev`, os tipos (`@types/node`, `@types/react`) e o próprio `typescript` foram adicionados como dependencias de desenvolvimento. O arquivo `tsconfig.json` foi modificado automaticamente.

Como o projeto é novo e será feito tudo certinho desde o começo, no arquivo `tsconfig.json` o `strict` foi setado como como `true`.

O arquivo de configuração de tipos pro next foi criado (`next-env.d.ts`) - não foi feito o commit por estar na config padrão do `.gitignore`.

O arquivo `index.js` foi alterado para `index.tsx` (ao invés de `ts`, por ser um arquivo jsx e possuir coisas visuais/html - ou seja, não é um arquivo apenas com funcionalidades). Também foi necessário ajustar o arquivo `jsconfig.json`, adicionando a linha `"jsx": "react-jsx"` por conta de erros apontados no index pelo TypeScript.

---
