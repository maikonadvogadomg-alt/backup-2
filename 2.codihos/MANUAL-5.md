# Manual do APK Builder

O mesmo texto está dentro do app, na aba **Manual** (com botão 🔊 Ouvir).

## 📱 Para que serve este app

Ele faz quatro coisas:  
1. Transforma um projeto HTML seu em APK (app de Android).  
2. Publica o projeto como site no GitHub Pages (dá para instalar pelo Chrome como app).  
3. Tem a Iara, um chat com IA e voz (aba Chat).  
4. Tem um Playground para importar, ver e mandar projetos para o GitHub.  
  
As abas: Chat · Playground · GitHub · APK · Manual · Configuração (chaves de IA, token do GitHub e token do Expo).

## ✅ O que funciona de verdade (e o que é teste)

FUNCIONA:  
• Fazer o APK deste próprio app pelo computador (veja a parte “O APK deste próprio app”).  
• Publicar no GitHub Pages.  
• Importar .zip, .tar e .tar.gz (o erro de UTF-8/base64 foi consertado).  
• Fazer APK de um HTML seu pelo GitHub — caminho consertado agora (veja a próxima parte).  
  
EXPERIMENTAL (pode falhar):  
• O botão “Compilar APK via EAS” da aba APK, para projetos HTML. Ele usa um caminho não oficial do Expo e gasta 1 build grátis por toque. Prefira o GitHub.  
  
NÃO EXISTE AINDA:  
• Ver a prévia do APK antes de compilar. Para ver a página antes, use o GitHub Pages ou abra o HTML no navegador.

## 🚀 Fazer APK de um HTML seu — caminho garantido (GitHub, grátis)

Antes de começar: o projeto precisa ter um index.html na raiz (ou dentro de dist/). Um HTML único também serve.  
  
1. Configuração → cole o token do GitHub. Ao criar o token, marque “repo” e “workflow” (sem “workflow” o GitHub recusa o robô que compila).  
2. Playground ou GitHub → Importar → escolha o .zip do projeto.  
3. Aba APK → preencha Nome do App e Package ID. O Package ID é tipo com.maikon.calculadora: só letras minúsculas, números e pontos, sem traço e sem acento. Ele NÃO pode mudar depois.  
4. Olhe os avisos amarelos/vermelhos na aba APK. Se aparecer “Isto é o CÓDIGO-FONTE”, o APK vai abrir em branco: importe a pasta dist/ ou um HTML único.  
5. Aba GitHub → Enviar → nome do repositório → ligue “GitHub Actions” → Enviar.  
6. Espere 5 a 10 minutos. Abra o repositório no GitHub → Actions → a compilação mais recente (bolinha verde) → lá embaixo, em Artifacts → baixe.  
7. Vem um .zip. Dentro dele está o app-debug.apk. Toque nele para instalar (o Android pede para permitir “instalar apps desconhecidos”).  
  
Se a bolinha ficar vermelha: toque nela, depois em “Build Debug APK”, e mande o print do erro para a IA.

- [🔑 Criar token do GitHub (repo + workflow)](https://github.com/settings/tokens/new?scopes=repo,workflow&description=APK+Builder)

## 🔧 Por que antes o APK “baixava mas não abria nada”

Eram defeitos do gerador, não seus:  
• Não ia ícone nenhum → a compilação parava no meio.  
• O envio ao GitHub mandava só o HTML, e o robô procurava a pasta android/ que não existia → falhava sempre.  
• Botão de escolher arquivo (anexar PDF etc.) não abria nada → o Android não entende “.pdf,.docx” sozinho.  
• Botão de baixar/salvar não fazia nada → WebView não sabe salvar arquivo.  
• Microfone e câmera eram recusados calados.  
• Projetos React/Vite eram empacotados como código-fonte → tela branca.  
  
Tudo isso foi consertado. Agora os arquivos baixados vão para a pasta Downloads do celular e aparece um aviso “Salvo em Downloads”.

## 🚫 O que um APK de HTML não consegue fazer

• Ditado por voz (falar e virar texto) do navegador: não existe dentro de APK. O resto da página funciona.  
• Ler em voz alta (TTS): depende do celular; em alguns fala, em outros não.  
• Imprimir: não existe. O app avisa; salve em PDF ou Word e imprima pelo arquivo.  
• Programas que precisam de servidor (localhost, porta 5000, /api/...): no celular não há servidor. Exemplo: o Assistente Jurídico do computador. Para virar APK, precisa ser a versão só em HTML.  
• Coisas da internet (CDN, IA, BCB): funcionam, mas precisam de internet.

## 🔄 Atualizar um app que já está instalado

Cada compilação no GitHub sai com uma assinatura de teste nova. Por isso o Android não deixa instalar “por cima”.  
Faça assim: exporte/salve os dados do app antigo (se ele tiver backup) → desinstale → instale o novo.  
(Assinatura fixa é o próximo passo de melhoria; se precisar, peça.)

## 🌐 Publicar como site e instalar pelo Chrome (muitas vezes é melhor que APK)

Aba GitHub → Enviar → ligue “GitHub Pages”. Em 1 a 2 minutos o endereço fica no ar (seunome.github.io/repositorio).  
Abra no Chrome do celular → menu ⋮ → “Adicionar à tela inicial” / “Instalar app”.  
Vantagens: ditado por voz e imprimir funcionam, atualiza sozinho quando você manda versão nova, e não gasta build.  
Repositório privado não tem Pages no plano grátis do GitHub: deixe público só o que não tiver dados de cliente nem chaves.

## ☁️ Botão “Compilar APK via EAS” (Expo)

Precisa do token do Expo (expo.dev → Account settings → Access tokens).  
Cada toque gasta 1 build grátis do mês — agora ele pergunta antes e não deixa tocar duas vezes.  
Para projetos HTML ele é experimental: o Expo foi feito para apps Expo, não para HTML. Se falhar, use o GitHub.  
Para apps Expo de verdade (como este próprio app), o caminho certo é o do computador, abaixo.

## 🛠️ O APK deste próprio app (APK Builder)

No computador, dentro da pasta do projeto:  
1. npm install  
2. npx eas-cli@latest login  
3. npm run apk  
4. No fim aparece o link para baixar.  
  
Antes, copie de volta para a pasta os seus arquivos android.keystore e credentials.json (a assinatura). Sem eles não instala por cima do app antigo.  
O app.json já está com o dono (owner) maikons-individual-orga e o projectId da sua conta. Se mudar de conta no Expo, esses dois mudam.

## 🔒 Segurança

• Nunca mande para o GitHub, nem para ninguém: android.keystore, credentials.json, .env, senhas e tokens.  
• Os tokens (GitHub, Expo, IA) ficam guardados só neste celular.  
• Antes de publicar um site, confira se não há nome, CPF ou dados de cliente no projeto.

