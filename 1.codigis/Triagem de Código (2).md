# Triagem de Código

Separe o código perdido nas conversas com a IA, escolha a versão certa de cada arquivo e monte o projeto em módulos independentes.

Você está vendo uma **conversa de exemplo**. Importe o seu arquivo e o exemplo some sozinho.

**Solte aqui o arquivo da conversa** Ou clique para escolher. Pode mandar vários de uma vez. .md .txt .zip .html .js .css .py .json (organização salva)

### Ou cole o texto da conversa

### Como funciona

1. Tudo roda no seu navegador. O arquivo não é enviado para lugar nenhum.
2. Cada bloco de código da conversa vira um cartão, separado por tipo. O nome do arquivo é lido do texto em volta (ex.: “salve como js/app.js”).
3. Quando o mesmo arquivo aparece várias vezes, as versões ficam juntas. Você escolhe qual vale.
4. No Projeto você baixa tudo em .zip, com guia de montagem e comandos para criar as pastas.
5. No Modularizar você quebra um HTML ou JS gigante em arquivos pequenos, com um mapa de onde está cada função.

### Arquivos importados

Cada cartão é um bloco de código tirado da conversa, na ordem em que apareceu. Dê nome aos que ficaram sem nome digitando o caminho (ex.: js/chat.js): blocos com o mesmo caminho viram versões do mesmo arquivo.

Aqui fica um arquivo por linha, com a versão escolhida. Marque o que entra no projeto. A versão sugerida é a última completa; as marcadas como trecho parecem pedaços (“substitua só esta função”).

Fora do projeto

Nome da pasta do projeto

```

```

O .json guarda seus nomes e escolhas. Para continuar depois, importe ele na etapa 1.

Guia de montagem: criar cada arquivo e colar

Para quem prefere montar à mão no VS Code ou no Bloco de Notas. Crie o arquivo com o caminho exato, clique em Copiar, cole, salve e marque como feito.

Comandos para criar as pastas e arquivos vazios

```

```

Cole um HTML ou JS grande. A ferramenta separa o CSS, quebra o JavaScript em arquivos por assunto e gera um **MAPA** dizendo onde está cada função. Quando algo quebrar, você manda para a IA só o arquivo com problema.

Abrir arquivo

**Simples (recomendado)**Arquivos separados carregados em ordem. Funciona abrindo o index.html com dois cliques. Nada muda no código, só muda de lugar. **Módulos ES (import/export)**Cada arquivo declara o que usa dos outros. Mais organizado, mas precisa de servidor local (Live Server do VS Code ou npx serve).

### Como ele decide os arquivos

Se o código tem títulos de seção (// ===== CHAT =====), cada seção vira um arquivo. Se não tem, agrupa pelo nome das funções (renderChat, sendChat → chat.js). Variáveis soltas vão para estado.js e o código de inicialização para main.js. Você pode mudar o arquivo de qualquer função antes de gerar.