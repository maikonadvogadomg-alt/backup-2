Atualizado em 09/10/2026, 23h

# Guia dos seus apps

Tudo o que foi feito hoje, como baixar, como instalar, como consertar e o que fazer quando der erro. Abra a parte que precisar.

[Baixar](#baixar)[Quais arquivos](#arquivos)[Mini SK](#minisk)[Caça-Bug](#cacabug)[Colador](#colador)[Jurídico](#juridico)[CodeLens](#codelens)[SK V3](#skv3)[APK do Expo](#eas)[Ligar o GitHub](#github)[Segurança](#seguranca)[Quando der erro](#erros)[Falta fazer](#pendente)

## 1. Como baixar os arquivos

**O jeito que mais funciona:** abra esta conversa pelo **Chrome, em claude.ai** (não pelo app do Claude) e toque nos cartões dos arquivos.

- **Não baixa / para no meio:** memória do celular cheia. Apague os zips repetidos da pasta Download.
- **Chrome segurou o .zip:** menu ⋮ → **Downloads** → "Manter" ou "Baixar mesmo assim".
- **Nome repetido** (Mini-SK (1).zip, (2)…): apague os velhos. Os novos têm **data e letra no nome** (ex.: `Mini-SK-09-10-b.zip`). Use sempre o de letra mais adiantada.
- **Se os arquivos não abrirem mais** (o espaço de trabalho do Claude desliga quando fica parado): peça "gera de novo o …" na conversa.
- **Google Drive:** está ligado, mas por ele só cabem arquivos pequenos. Os zips grandes não cabem.

## 2. Quais são os arquivos certos

| Arquivo | O que é | Onde usar |
| --- | --- | --- |
| `Mini-SK-09-10-b.zip` | Seu editor (com Termux, Preparar, EAS, prévia TSX) | Netlify / GitHub Pages → instalar como app |
| `Caca-Bug.zip` (18h20) | Caça erros, Organizar, Plano, Consertar EAS | Netlify / GitHub Pages |
| `Colador-de-Links-09-10-a.zip` | Colador de links refeito | Netlify (site novo) |
| `Assistente-Juridico-local-09-10-b.zip` | Jurídico no PC (banco na pasta `dados`) | Computador (iniciar.bat) |
| `Assistente-Juridico-Vercel-09-10-a.zip` | Jurídico na internet, sempre ligado | Vercel + Neon |
| `CodeLens-local-09-10-c.zip` | CodeLens no PC e no celular (Termux) | Computador ou Termux |
| `SK-Editor-V3-exe-09-10-a.zip` | SK V3 que vira programa .exe | GitHub → Actions |
| `Pasta-1-organizada.zip` | A pasta do Haiku já organizada | Para estudar/montar |

**Mini SK**versão v09/10-b — o seu editor

### Publicar e conferir

1. No Netlify, arraste `Mini-SK-09-10-b.zip` no mesmo site (aba Deploys).
2. Abra no Chrome. No topo, ao lado do nome do projeto, tem que aparecer **v09/10-b**. Se não aparecer, é uma cópia velha.
3. Ainda velho? Segure o ícone do app → Desinstalar → abra o site no Chrome → ⋮ → **Instalar app**.

### Projetos com o mesmo nome

Importar um zip com nome repetido NÃO apaga o anterior: o novo ganha data e hora no nome. Olhe o nome no topo antes de trabalhar. Em 🗂 Projetos dá para **Renomear** e **Apagar**.

### O que tem de novo

- **🏗️ Preparar:** ao importar, analisa sozinho. **✅ Fazer tudo** tira a Replit, conserta caminhos, cria manifest/ícones, Capacitor com as autorizações do Android, desktop .exe (Electron) e o **📋 Plano completo** (mostra o que falta no backend). **⬇ Baixar o projeto configurado**.
- **⚡ Node de verdade:** só no site (https) e no Chrome. Toque "🔒 Ligar o lacre" uma vez. Não funciona no APK. É temporário: some quando fecha.
- **📱 Termux:** terminal do Linux do celular, funciona no PWA e no APK. Veja os comandos abaixo.
- **☁️ EAS:** conserta o projeto Expo inteiro e manda gerar o APK pelo GitHub.
- **Prévia TSX:** abra um arquivo .tsx/.jsx e a prévia mostra só aquele componente (precisa de internet na 1ª vez).
- **📦 APK:** gere de novo para pegar os consertos (prévia que ficava branca, Termux). Se o celular disser "app já existe / não instalado": desinstale o antigo ou troque o **nome do pacote** (ex.: `com.maikon.minisk2`).

### Termux dentro do Mini SK

No Termux, só da 1ª vez:

```
pkg install -y ttyd
```

Toda vez (deixe o Termux aberto):

```
ttyd -W -i 127.0.0.1 -p 7681 bash
```

No Mini SK: 📱 Termux → Conectar. Se o Chrome perguntar sobre "dispositivos da rede local", toque em Permitir.

**Caça-Bug**achar erros, organizar bagunça, preparar Expo

- **Instalar:** suba no Netlify/GitHub Pages e instale pelo Chrome (já vem pronto para instalar).
- **🩺 Diagnóstico → 📋 Gerar o plano completo:** telas, rotas, o que falta no backend, banco, variáveis.
- **🩺 Diagnóstico → ☁️ Consertar para o EAS** (só em projeto Expo): preencha a sua conta e devolve um zip pronto.
- **🗂️ Organizar:** para pasta embolada. Separa as peças, tira cópias, escolhe a melhor versão, conserta erros simples (inclusive texto de conversa colado no código) e monta a pasta **1-MONTADO**.
- **⚖️ Comparar:** marque 2 versões e veja o que uma tem e a outra não.

**Colador de Links**refeito igual ao do Claude 4.6

1. Suba `Colador-de-Links-09-10-a.zip` no Netlify como **site novo** (não apague o antigo ainda).
2. Para trazer os 37 links do antigo: no antigo, segure o dedo na lista → selecionar tudo → copiar. No novo: **📋 Colar vários de uma vez** → colar → Adicionar todos.
3. **📌** num link = vira aba no topo. As abas ficam vivas (login, token e conversa continuam).
4. **🚀 Abrir selecionados** = um por vez com Anterior/Próximo, Tela cheia, Abrir fora.
5. Faça **💾 Backup** de vez em quando.

**Assistente Jurídico**duas formas: no PC, ou na internet sempre ligado

### Forma A — no computador (`…local-09-10-b`)

1. Instale o **Node.js 22 LTS** (nodejs.org), uma vez.
2. Extraia o zip (botão direito → Extrair tudo). Não abra de dentro do zip.
3. Dois cliques em `iniciar.bat`. Na 1ª vez demora. Depois abre o navegador sozinho.

**Consertado hoje:** "só funcionava no 1º dia" (o banco ficava travado ao fechar a janela) e "porta 5000 não abre" (agora escolhe sozinho uma porta livre e mostra o endereço na janela preta).

**Fechar do jeito certo:** na janela preta, **Ctrl + C** e espere. **Ao trocar de versão:** mantenha a pasta `dados` (é onde ficam os seus dados).

### Forma B — na internet, sempre ligado (`…Vercel-09-10-a`)

**Erro 500 explicado:** o banco nunca ficava completo (faltavam tabelas e 6 colunas). Agora o servidor cria e completa o banco sozinho ao ligar.

1. **Neon** (neon.tech): crie um projeto e copie a *Connection string*. **É senha.**
2. Mande a pasta para um repositório no GitHub.
3. **Vercel** (vercel.com, entre com o GitHub) → Add New → Project → escolha o repositório → em Environment Variables coloque `DATABASE_URL` (do Neon) e `SESSION_SECRET` (uma frase inventada) → Deploy.
4. Abra o endereço `….vercel.app` → ⋮ → **Instalar app**.

**CodeLens**no PC e no celular pelo Termux (09-10-c)

### No computador

Igual ao jurídico: Node 22, extrair, `iniciar.bat`. Também tem o conserto do banco e a porta automática.

### No celular (Termux) — uma vez só

```
termux-setup-storage
```

```
pkg install -y nodejs-lts unzip
```

```
cd ~ && unzip -o storage/downloads/CodeLens-local-09-10-c.zip -d codelens
```

```
cd ~/codelens && sh termux-atalho.sh
```

### Para abrir

```
cd ~/codelens && sh iniciar.sh
```

Ou o atalho "CodeLens" do app **Termux:Widget**. Depois, no Chrome: ⋮ → **Instalar app**. Fechar: **Volume-baixo + C** no Termux.

**SK Editor V3**vira programa .exe pela nuvem do GitHub

Funcionava "um dia só" porque rodava num endereço temporário (Replit ou ⚡ Node). O programa .exe abre sempre.

1. Mande a pasta de `SK-Editor-V3-exe-09-10-a.zip` para um repositório (Mini SK → 🐙 GitHub).
2. No GitHub: **Actions** → "🖥️ SK Editor V3 — .exe (Windows)" → **Run workflow**.
3. Uns 10 minutos depois: abra a execução → **Artifacts** → baixe **SK-Editor-v3-windows**.
4. No PC: extraia e abra **SK-Editor-v3.exe**.

Se ficar vermelho, mande o print do passo vermelho.

**APK de app Expo (DevMobile, jurídico Expo)**pelo EAS, com os dados da sua conta

**Dados que você precisa (nenhum é senha):**

- **Conta do Expo (owner):** seu usuário no expo.dev.
- **Slug:** nome curto, sem espaço (ex.: `app-ide`).
- **projectId:** expo.dev → Projects → Create project com o mesmo slug → copie o ID.
- **Pacote Android:** você inventa (ex.: `com.maikon.devmobile`).

1. Caça-Bug → 🩺 Diagnóstico → **☁️ Consertar para o EAS** → preencha → baixe o zip.
2. Mini SK → importe o zip → **☁️ EAS** → cole o **token do Expo** (ele fica só no aparelho e vai trancado para o cofre do GitHub) → Enviar e compilar.
3. O APK aparece em `expo.dev/accounts/SUA-CONTA/projects/SLUG/builds`.

O DevMobile ainda chama um servidor da Replit (`sk-code-editor.replit.app`) para IA, terminal e banco. O APK sai e abre, mas essas partes param quando a Replit desligar.

**Ligar o GitHub ao Claude**para eu mandar direto ao repositório "Cloude"

Você já criou o repositório `maikonadvogadomg-alt/Cloude`. Falta ligar a conta:

1. claude.ai → foto/nome → **Configurações** → **Conectores** → **GitHub** → Conectar → no GitHub: Authorize/Install → escolha **Cloude**.
2. Hoje essa opção não apareceu para você. Pode depender do plano ou estar em outro lugar do menu — vale procurar na ajuda: [support.claude.com](https://support.claude.com).
3. Ligado: me diga "pronto". Aí eu mando tudo para o Cloude, e no Mini SK você puxa pelo 🐙 GitHub, sem baixar zip.

Você NUNCA precisa me mandar token do GitHub. Os comandos "git remote add…" que o GitHub mostra são para computador; ignore.

## Segurança (vale para tudo)

- Nunca mande para ninguém (nem em print): **tokens** (GitHub, Expo), **chaves de IA**, **senha do banco** (DATABASE_URL), arquivos `.env`, `.pem`, `.key`, `.keystore`.
- Eles vão só: dentro do próprio app (🔑), no cofre do GitHub (Secrets) ou nas variáveis da Vercel.
- Se um token apareceu num print ou arquivo: apague-o no site e crie outro.
- SQL que começa com `DROP TABLE` APAGA tabelas. Só rode em banco vazio.

## Quando der erro: o que mandar

- **Janela preta do PC:** print das últimas linhas antes de fechar.
- **GitHub Actions vermelho:** print do passo vermelho aberto.
- **App em branco:** no Mini SK, a prévia mostra os erros (botão ▤) e o 🏗️ Preparar tem "🤖 Mandar os erros para a IA".
- **EAS:** a página do build no expo.dev (topo + parte vermelha). Sem o token.
- Sempre diga **como abriu** (site, app instalado, .bat, Termux) e **qual versão** (a letra no nome).

## Falta fazer (quando você voltar)

- Mandar o **briefing do Haiku** (as 2 mil linhas, inteiro) + o guia interativo → eu monto o projeto limpo e modular.
- Mandar a **conversa grande do Haiku** → ensino o Caça-Bug a aplicar os "substitua / adicione" na ordem.
- Hub do Haiku (pasta MONTADO): falta o `editor.js` e ligar os botões dos módulos novos.
- Colocar o Colador dentro do 🔗 Links do Mini SK.
- O "executável pequenininho" da Replit: quando achar a explicação do Haiku, mande para comparar.