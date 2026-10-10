# Guia: rodar seus projetos na nuvem

Oct 8, 2026 · @MAIKON DA ROCHA CALDEIRA

Das 4 portas que aparecem no seu editor, só duas dão terminal de verdade: o StackBlitz (sem login, para repositório público) e o Codespaces (um computador na nuvem, cerca de 60 horas grátis por mês). As outras duas só servem para ver e editar arquivos.

## As 4 portas

São os 4 botões da tela "VS Code Web" do SK Editor v3. Todas abrem um repositório que já está no GitHub.

| Porta | O que é | Terminal de verdade | Precisa de login | Custo | No celular |
| --- | --- | --- | --- | --- | --- |
| **StackBlitz** | Roda Node dentro do navegador (WebContainer) | Sim | Não, para repositório público | Grátis para uso pessoal | Funciona em teste (beta); projeto grande pode travar |
| **GitHub Codespaces** | Um computador Linux de verdade na nuvem | Sim | Sim (sua conta GitHub) | 120 horas de cota grátis por mês na conta Free (na máquina menor, rende cerca de 60 horas) | Funciona, mas a tela é apertada |
| **GitHub.dev** | Editor de arquivos (o VS Code) no navegador | Não | Sim | Grátis | Bom para ler e corrigir arquivo |
| **vscode.dev** | Parecido com o GitHub.dev | Não | Sim | Grátis | Costuma falhar no celular |

Regra simples: para **rodar** o projeto, use StackBlitz (mais rápido) ou Codespaces (mais forte). Para só **corrigir um arquivo**, use o GitHub.dev.

## Passo a passo no StackBlitz

O jeito que sempre funciona é pelo endereço, sem depender de botão nenhum.

1. Mande o projeto para o GitHub (pelo Mini SK). O repositório precisa ser **público** para abrir sem login.
2. No navegador, abra: `stackblitz.com/github/SEU-USUARIO/NOME-DO-REPOSITORIO`
3. Ele abre o editor com os arquivos e, embaixo, o terminal. Se tiver `package.json`, ele instala e roda sozinho. No celular, espere uns minutos.
4. A prévia do app aparece ao lado ou embaixo.
5. Se nada rodar sozinho, digite no terminal: `npm install` e depois `npm run dev`.

Se você entrar no site do StackBlitz com a conta do GitHub, ele já lista os seus repositórios: é só tocar no que quer abrir.

## Passo a passo no Codespaces

É um computador de verdade na nuvem: roda servidor, banco e qualquer comando, como no seu PC.

1. Abra: `codespaces.new/SEU-USUARIO/NOME-DO-REPOSITORIO` (funciona com repositório privado também).
2. Toque em **Create codespace** e espere ele montar (1 a 3 minutos).
3. Abre um VS Code com terminal embaixo. Digite `npm install` e depois `npm run dev`.
4. Quando o app subir, aparece um aviso de "porta aberta": toque em **Open in Browser** para ver o app.
5. Ao terminar, **pare o codespace** (menu ☰ → Codespaces → Stop). Parado, ele não gasta as horas grátis.

Para conferir quanto já gastou no mês: github.com → Settings → Billing.

## O terminal real dentro do seu próprio app (WebContainer)

O Haiku estava certo: dá para ter um terminal de verdade dentro de um app HTML. O seu SK Editor v3 já tem isso: o arquivo `WebContainerTerminal.tsx` usa o WebContainer, a mesma peça do StackBlitz.

O que ele precisa para funcionar:

- **O lacre (COOP/COEP)**: é o que está no `sw.js`, no `vite.config` e no `.cjs` dessa versão. Sem ele, o terminal não liga.
- **Abrir como site** (https ou localhost). Como arquivo solto, não liga.
- **Navegador Chrome** (ou parecido). No Android está em teste: funciona, mas projeto grande pode travar por memória.

Os limites:

- **Dentro de APK**: o navegador de dentro do APK não está na lista oficial. Pode funcionar ou não — só testando.
- **Se for vender**: uso pessoal e teste são grátis; uso comercial em produção exige licença paga da StackBlitz (preço sob consulta).

## E o Mini SK, o Mini Code e o Caça-Bug?

| App | Tem terminal real hoje? | Pode ganhar as 4 portas? |
| --- | --- | --- |
| **Mini Code (CodeLens, no PC)** | Sim, o do próprio computador | Não precisa: ele já roda no seu PC |
| **Mini SK (celular)** | Não (o terminal dele só simula) | Sim, fácil: ele já sabe o seu repositório do GitHub, é só montar o endereço |
| **Caça-Bug** | Não | Sim, um botão "Abrir no StackBlitz" após mandar ao GitHub |

O caminho mais simples para o celular: **Mini SK → GitHub → StackBlitz**. Os botões das 4 portas no Mini SK e no Caça-Bug podem ser feitos quando você pedir.

## Quando dá errado

| O que aparece | Causa mais comum | O que fazer |
| --- | --- | --- |
| Apertei o botão e não abriu nada | O celular ou o APK bloqueou a aba nova | Use o endereço direto (passo a passo acima) |
| Abre e fica em branco | `catalog:` do Replit no package.json | Passe o projeto no Caça-Bug → Cirurgião → 🚨 Replit e tire o que ele mostrar |
| Pede login no StackBlitz | O repositório é privado | Deixe público (sem chaves nem dados de cliente) ou use o Codespaces |
| Trava ou fecha no celular | Falta de memória (projeto grande) | Use o Codespaces, que roda na nuvem |
| Terminal do app não liga | Aberto como arquivo, ou sem o lacre | Abra como site (https ou localhost) |
| Vermelho no terminal após `npm install` | Pacote que só existia no Replit | Tire um print e mande para a IA explicar |

## Fontes

- [WebContainers — navegadores suportados](https://developer.stackblitz.com/platform/webcontainers/browser-support)
- [WebContainers — licença comercial](https://webcontainers.io/enterprise)
- [GitHub Codespaces — cota grátis por conta](https://docs.github.com/en/billing/concepts/product-billing/github-codespaces)
- Arquivos do seu SK Editor v3: `VSCodeWebPanel.tsx` (as 4 portas) e `WebContainerTerminal.tsx` (o terminal real).
