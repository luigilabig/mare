# Maré — finanças da casa

App de finanças pessoais que roda **offline no celular**. Os dados ficam **só no aparelho**: não tem servidor, não tem conta, não manda nada para a internet.

## Instalar (uma vez, ~10 minutos)

O Maré é um *app web instalável* (PWA): você hospeda estes arquivos uma vez num endereço `https`, abre no celular e adiciona à tela inicial. A partir daí ele abre e funciona sem internet. O site só entrega o **código** do app; os **dados** nunca saem do celular.

### 1. Publicar os arquivos no GitHub Pages (grátis)

1. Entre em <https://github.com/new> e crie um repositório chamado `mare`.
2. No repositório, clique em **Add file → Upload files** e arraste **todos os arquivos desta pasta** (`index.html`, `sw.js`, `manifest.webmanifest`, os `.png`). Clique em **Commit changes**.
3. Vá em **Settings → Pages**. Em *Build and deployment*, escolha **Deploy from a branch**, branch **main**, pasta **/ (root)** e salve.
4. Em 1–2 minutos aparece o endereço: `https://SEU-USUARIO.github.io/mare/`.

### 2. Adicionar à tela inicial

- **iPhone (Safari):** abra o endereço → botão **Compartilhar** → **Adicionar à Tela de Início**.
- **Android (Chrome):** abra o endereço → menu **⋮** → **Instalar app** (ou *Adicionar à tela inicial*).

Abra pelo ícone e comece cadastrando as contas. Teste: ative o modo avião e abra o app — ele funciona.

> Use sempre o ícone da tela inicial. No iPhone, o app instalado e o Safari guardam dados em lugares diferentes.

## Saídas imediatas e parceladas

- **Imediata:** sai do saldo na data do lançamento (agora, por padrão).
- **Parcelada:** informe o valor (total da compra ou de cada parcela), o número de parcelas e a data da 1ª parcela. O app cria uma saída por mês, sempre no mesmo dia (ou no último dia do mês, quando o dia não existe). Se o valor total não divide exato, a diferença de centavos vai na 1ª parcela, como nos cartões.
- Cada parcela só sai do saldo **no dia dela**. Até lá, fica como **comprometido**.
- Uma saída imediata com data futura também conta como comprometida (ex.: IPVA de janeiro).

**Onde aparece o comprometido**

- **Início:** cartão do mês com *entrou*, *saiu* e *a sair*, a sobra prevista do mês, o total já comprometido e um gráfico mês a mês.
- **Movimentos:** os meses futuros ficam navegáveis; cada mês mostra o que é previsto. Há um filtro *Parceladas*.
- **Análises:** gráfico do comprometido por mês e quanto da sua entrada média o próximo mês já tem comprometido.

Para mudar uma compra, toque em qualquer parcela: a edição vale para a compra inteira. Se quitar antes ou a compra for estornada, use **Encerrar parcelas futuras** (as já pagas ficam no histórico).

## Entradas estimadas

O app repete nos próximos meses as entradas que foram recorrentes até agora:

- **Recorrente** = a mesma fonte (mesma conta e categoria; sem categoria, mesma descrição — "Salário outubro" e "Salário novembro" contam como a mesma) apareceu em **3 dos últimos 4 meses** e não parou.
- **Valor estimado** = mediana dos totais dos últimos 3 meses. Um 13º ou bônus num mês não infla a estimativa, e duas rendas na mesma conta e categoria somam certo.
- O que já entrou ou está agendado no mês é descontado da estimativa.
- Em **Entradas estimadas** você vê cada uma e pode desligar a que não deve se repetir.
- As estimativas aparecem no cartão do mês (*A entrar*), no gráfico dos próximos meses (entradas estimadas × saídas comprometidas), nos meses futuros de Movimentos e em Análises.
- Só as **entradas** são estimadas. Gastos do dia a dia que ainda não foram lançados não aparecem nos meses futuros.

**Começando do zero:** sem histórico, não há o que repetir. Para ter estimativas desde já, lance as entradas dos últimos 3 meses com a data em que caíram (*Data e hora → Alterar*). Se a conta foi criada com saldo atual, esses lançamentos antigos entram no histórico e nas estimativas, mas não mudam o saldo de hoje (que já os incluía) — o app avisa isso no formulário.

## Ajustar saldo

Em **Patrimônio**, cada conta tem **Ajustar saldo** (e há **Ajustar todas**, para a rotina do mês). Você digita o saldo real de cada ativo da conta:

- **Rendimentos e custos** (padrão): a diferença para o saldo registrado entra como rendimento (+) ou custo (−: tarifa, IR, taxa). Aparece no cartão do mês e no gráfico *Rendimentos e custos* das Análises. Não conta como entrada nem saída.
- **Correção de saldo**: para quando a diferença vem de algo que você não lançou. O saldo é corrigido, mas a diferença não entra em rendimentos e custos.

## Backup diário

- Na primeira abertura de cada dia com lançamentos, o app lembra de fazer o backup (banner na tela inicial e ponto no ícone de nuvem). São 2 toques: **Fazer → Salvar ou enviar → Salvar em Arquivos / Drive**.
- O arquivo é um `.json` com todos os dados, **sem senha**: guarde em lugar só seu.
- Celular novo: instale o app e, na tela inicial vazia, toque em **Restaurar um backup**.
- O app também guarda sozinho **um ponto de restauração por dia** (últimos 7) dentro do aparelho — útil para desfazer erros, mas some junto com o celular. Por isso o arquivo importa.

Por que não é 100% automático: apps web não podem gravar arquivos fora do próprio app sem um toque seu. É uma proteção do sistema (iOS e Android), não uma escolha do Maré.

## Privacidade, sem rodeios

- Não há senha no app. Quem protege os dados é o **bloqueio de tela do celular**: iOS e Android mantêm o armazenamento criptografado enquanto o aparelho está travado. Com o celular desbloqueado, qualquer pessoa que abrir o Maré vê tudo.
- O app é proibido, pela própria política de segurança do código (CSP), de se conectar a qualquer endereço. Nada sai do aparelho a não ser pelo backup que você mesmo salva.
- O arquivo de backup é legível por quem tiver acesso a ele.
- Cotações de câmbio são manuais (ou atualizadas pelas suas conversões), porque o app não acessa a internet.

**Vindo da versão com senha?** Na primeira abertura, o app pede a senha antiga uma única vez para liberar os dados guardados; depois disso, não pede mais. Backups antigos (`.mare`) continuam restauráveis com a senha deles.

## Atualizar para uma nova versão

Substitua os arquivos no repositório (Upload files de novo). Na próxima abertura com internet, o app mostra **“Nova versão disponível — Atualizar”**. Seus dados não são afetados.

## Como os números são calculados

- **Realizado × agendado:** tudo com data até hoje já aconteceu; de amanhã em diante, é agendado. Saldos, patrimônio, médias e gráficos de histórico usam só o realizado.
- **Patrimônio no papel:** soma de todos os ativos e bens, em reais, pela cotação de referência. **Líquido:** o mesmo, descontando o deságio de cada ativo (venda imediata). Saldos negativos entram no total, sem deságio.
- **Atualizar valor** registra uma observação (“o Tesouro vale R$ X hoje”); a diferença para o saldo vira rendimento — não conta como entrada.
- **Transferência:** a origem perde valor + custos; o destino recebe o valor. **Conversão:** a origem perde o valor enviado (+ custos, se pagos na origem); o destino recebe o valor convertido (− custos, se descontados no destino). Custos são sempre valores financeiros e aparecem nas saídas como *Taxas e custos*.
- **Sobra prevista do mês:** entrou + a entrar (agendadas + estimadas) − saiu − a sair, só do mês atual.
- **Patrimônio no histórico:** antes do saldo de abertura de uma conta, o saldo real dela é desconhecido; por isso o gráfico começa quando há saldo informado.
- **Projeção:** patrimônio financeiro capitalizado pela rentabilidade média esperada dos ativos + aporte mensal (entradas − saídas da base escolhida: mês passado, 30 dias, média de 3 ou 12 meses); bens com a própria variação anual. “Em dinheiro de hoje” desconta a inflação esperada.
- **Divisão por função:** contas com mais de uma função dividem o saldo pelos percentuais informados. Bens ficam fora das divisões por função e por categoria de ativo.
