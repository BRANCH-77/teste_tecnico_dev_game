# Teste Técnico — Desenvolvedor(a) de Jogos · Branch77

## O desafio: "Bataki"

Desenvolva um **jogo de reação** completo, chamado **Bataki**, pensado para rodar em um **totem touch vertical** na frente do público em um evento. A proposta é simples e viciante: botões redondos aparecem na tela, um deles acende, e o jogador precisa tocá-lo o mais rápido possível. Ao acertar, ele apaga e outro acende imediatamente — e assim por diante até o tempo acabar.

O jogo deve ser **vistoso, energético e imediatamente compreensível**, com alvos grandes e feedback visual forte.

---

## Fluxo da aplicação (máquina de estados)

`Home → Formulário → Regras → Jogo → Pontuação/Ranking → (volta à Home)`

1. **Home (tela de atração):** logo/nome "BATAKI", uma tagline curta e um botão grande "JOGAR". Serve também como *attract screen* quando o totem está ocioso.
2. **Formulário (captura de lead):** campos Nome (obrigatório), E-mail (opcional) e Empresa (opcional). O botão "CONTINUAR" só habilita com o nome preenchido.
3. **Regras:** explicação curta e visual + botão "COMEÇAR" com contagem regressiva 3, 2, 1 antes do jogo iniciar.
4. **Jogo:** grade de **9 botões (3x3)**, um único aceso por vez. Ao tocar no botão aceso: ele apaga, contabiliza o acerto e um novo botão aleatório (diferente do anterior) acende na hora. HUD sempre visível com **pontuação** e **cronômetro regressivo (30 segundos)**.
   - Pontuação: **+10 por acerto**.
   - Bônus de sequência (*streak*): a cada 5 acertos seguidos, um **multiplicador temporário**.
   - Tocar em botão apagado conta como erro e **quebra a sequência** (sem tirar pontos).
   - Feedback visual/de cor a cada acerto e um "combo!" quando o streak sobe.
   - Ao zerar o tempo, transição automática para a tela de pontuação.
5. **Pontuação + Ranking:** pontuação final em destaque, mensagem personalizada ("Mandou bem, [Nome]!"), **ranking dos 10 melhores** (nome + pontuação) destacando a posição do jogador. Botões "JOGAR DE NOVO" e "INÍCIO".

---

## Comportamento de totem (importante)

- **Modo ocioso:** se ninguém interagir por **20 segundos** em qualquer tela, o jogo reseta sozinho e volta para a Home, descartando o jogador atual.
- A aplicação **nunca pode travar** nem ficar num estado sem saída — sempre há como voltar ao início.

---

## Requisitos técnicos (obrigatórios)

- **Engine:** o jogo deve ser desenvolvido em **uma** das seguintes: **Godot, Unity ou Unreal Engine**. (Indique qual e a versão utilizada.)
- **Persistência em banco SQL:** todos os dados de jogadores e partidas devem ser gravados em um banco de dados **SQL — SQLite, MySQL ou MariaDB**. No mínimo: nome, e-mail, empresa, pontuação final e data/hora da partida. O ranking deve ser lido a partir do banco.
- **Orientação:** priorizar layout **vertical (totem)**, funcionando bem em tela cheia.
- **Entrada:** funcionar tanto com **toque** quanto com **mouse**.
- **Organização de código:** código limpo e organizado, com a **lógica de jogo separada da lógica de interface**.

---

## Entregáveis

1. **Código-fonte completo** do projeto (repositório Git de preferência, ou arquivo compactado).
2. **Executável** da aplicação, pronto para rodar (Windows). Inclua o banco/arquivo de dados ou script de criação, se aplicável.
3. **README** com: engine e versão, banco escolhido, como compilar/rodar o executável, e quaisquer decisões técnicas relevantes.

---

## Critérios de avaliação

- Fidelidade ao fluxo e às regras descritas.
- Qualidade do *feedback* visual e da sensação de jogo (*game feel*): animações rápidas e satisfatórias.
- Modelagem e uso correto do banco SQL (persistência e leitura do ranking).
- Robustez (reset por ociosidade, sem estados travados).
- Organização, clareza e legibilidade do código.
- Cuidado com a experiência em touch (alvos grandes, nada pequeno para o dedo).

---

## Diferenciais (opcionais)

- Efeitos de partículas/som no acerto e no combo.
- Configurações ajustáveis (tempo de partida, tempo de ociosidade).
- Estatísticas extras (média de tempo de reação, maior streak).

---

## Identidade visual (referência)

> Um layout de referência das telas (formato totem 1080×1920, com o logo aplicado) está disponível para os candidatos importarem no Figma e extraírem os assets.

---

## Referências fornecidas (siga-as)

O layout e o comportamento do jogo **já estão definidos** — não é preciso inventar telas nem fluxo. Use as referências abaixo como fonte da verdade:

1. **Figma (layout — fonte da verdade visual):** siga o conteúdo do Figma para todas as telas — composição, tamanhos, cores, tipografia, espaçamentos e assets. Extraia os assets diretamente de lá.
   - `https://www.figma.com/design/ZtsHPpKusEqZ6xe7mE3ZWK/Bataki?m=auto&t=Nnm92Pwqy7KTAXpN-6`
2. **Vídeo gravado (comportamento — fonte da verdade de interação):** use o vídeo de referência, na raiz desse repo, para entender o *game feel* — animações, transições entre telas, feedback de acerto, contagem regressiva, combo e o comportamento em modo ocioso.

Boa sorte — capriche no *game feel*.
