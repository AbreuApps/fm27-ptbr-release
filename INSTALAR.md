# Como instalar a tradução PT-BR do FM27 (e o plugin opcional)

São **duas partes**, e só a primeira é obrigatória:

| Parte | O que é | Precisa de BepInEx? |
|---|---|---|
| **1. Idioma** `portuguese_br.ltc` | A tradução em si. Aparece em *Preferências → Idioma → Português (Brasil)* | Não |
| **2. Plugin** pasta `TraducaoLog` | Opcional. Corrige textos que vêm do banco de dados do jogo e não do arquivo de idioma (lesões, países, premiações da semana, estaduais…) e ajusta artigos e preposições ("do Cruzeiro", "na Portuguesa", "Relatório do Grêmio") | Sim |

O plugin **não grava nenhum log nem salva texto do jogo**. Ele só troca o texto na tela. Sem ele a tradução funciona normalmente, com alguns textos ainda em inglês ou com artigos faltando.

> **Antes de começar:** faça uma cópia do seu save (pasta `Sports Interactive/Football Manager 27/games`). Instalar o idioma não toca no save, mas o BepInEx altera a forma como o jogo abre, e é bom ter backup.

---

## Parte 1 — Instalar o idioma (todo mundo)

1. Baixe `portuguese_br.ltc` na página de [Releases](../../releases/latest).
2. Copie o arquivo para a pasta `languages` do FM27:

   | Sistema | Pasta |
   |---|---|
   | **Windows** | `Documentos\Sports Interactive\Football Manager 27\languages\` |
   | **Linux (Steam/Proton)** | `~/.local/share/Steam/steamapps/compatdata/4530370/pfx/drive_c/users/steamuser/Documents/Sports Interactive/Football Manager 27/languages/` |
   | **macOS** | `~/Library/Application Support/Football Manager 27/languages/` |

3. Feche o jogo por completo e abra de novo.
4. No jogo: **Preferências → Idioma → Português (Brasil)**.

Pronto. Se não quiser o plugin, pode parar aqui.

---

## Parte 2 — Instalar o plugin (opcional)

O plugin usa o **BepInEx**, um carregador de plugins para jogos Unity. Ele é o mesmo usado pelos mods de estádio, torcida e iluminação do FM27, e **convive com eles** sem problema (foi testado junto com 10 outros plugins).

> Se você **já usa mods do FM27** (estádios, torcidas…), o BepInEx já está instalado: pule para o [passo 2.2](#22-copiar-o-plugin).

### 2.1 Instalar o BepInEx

Você precisa da versão **6.0.0-be.785, "Unity IL2CPP", Windows x64** (é a que funciona com o FM27, inclusive no Linux/Proton).

- **Projeto:** <https://github.com/BepInEx/BepInEx> (releases: <https://github.com/BepInEx/BepInEx/releases>)
- **Download da build certa:** <https://builds.bepinex.dev/projects/bepinex_be>
  Procure a **build #785** e baixe o arquivo `BepInEx-Unity.IL2CPP-win-x64-6.0.0-be.785+…zip`.
- **Guia oficial:** <https://docs.bepinex.dev/master/articles/user_guide/installation/unity_il2cpp.html>

> ⚠️ **Cuidado com a página de Releases do GitHub:** ela mostra, no topo, a série **5.x** do BepInEx (`BepInEx_win_x64_5.4.xx.zip`). Essa série é para jogos Unity "Mono" e **não funciona no FM27**, que é IL2CPP. Use a série **6** (build `be.785`, "Unity.IL2CPP"), do link acima.

**Passos:**

1. Descubra a pasta do jogo (a que tem o `fm.exe`):

   | Sistema | Pasta típica |
   |---|---|
   | **Windows** | `C:\Program Files (x86)\Steam\steamapps\common\Football Manager 27\` |
   | **Linux** | `~/.local/share/Steam/steamapps/common/Football Manager 27/` |

   Dica: na Steam, clique com o botão direito no jogo → *Gerenciar* → *Explorar arquivos locais*.
2. Extraia **todo o conteúdo** do zip do BepInEx **dentro dessa pasta**, ao lado do `fm.exe`. Devem aparecer ali a pasta `BepInEx`, a pasta `dotnet`, o arquivo `doorstop_config.ini` e uma DLL "proxy" (`winhttp.dll` ou `version.dll`, dependendo do pacote).
3. **Só no Linux (Proton):** na Steam, clique com o botão direito no FM27 → *Propriedades* → *Opções de inicialização* e coloque, usando o **nome da DLL proxy que apareceu no passo 2**:

   ```
   WINEDLLOVERRIDES="winhttp=n,b" %command%
   ```

   (se a DLL proxy for `version.dll`, escreva `version=n,b`). No Windows não precisa disso.
4. **Abra o jogo uma vez** e deixe chegar ao menu. **A primeira abertura demora vários minutos** (o BepInEx está gerando os arquivos de ligação com o jogo). Se parecer travado numa tela preta, espere. Não force o fechamento.
5. Feche o jogo. Confirme que existe a pasta `BepInEx/plugins/` e o arquivo `BepInEx/LogOutput.log`. Se o log tem a linha `Chainloader initialized`, o BepInEx está funcionando.

### 2.2 Copiar o plugin

1. Baixe `TraducaoLog-1.2.zip` na página de [Releases](../../releases/latest) e extraia. Sai uma pasta chamada **`TraducaoLog`**.
2. Copie essa **pasta inteira** para dentro de `BepInEx/plugins/` do jogo. Deve ficar assim:

   ```
   Football Manager 27/
   └── BepInEx/
       └── plugins/
           └── TraducaoLog/              ← a pasta que você copiou
               ├── TraducaoLog.dll
               ├── dicionario.tsv
               ├── regras.tsv
               ├── generos.tsv
               ├── contextos.tsv
               ├── config.txt
               └── LEIA-ME.txt
   ```

   É o mesmo formato dos mods de estádio (uma pasta por mod dentro de `plugins`). **Não** solte a DLL direto em `plugins/`, porque os arquivos `.tsv` precisam ficar ao lado dela.
3. Abra o jogo normalmente.

### 2.3 Conferir que funcionou

Abra `BepInEx/LogOutput.log` (ele é recriado a cada abertura do jogo) e procure por `TraducaoLog`. Você deve ver algo assim:

```
[Info   :TraducaoLog] DICIONARIO carregado: 7187 entradas
[Info   :TraducaoLog] REGRAS carregadas: 6163 (erros: 0)
[Info   :TraducaoLog] OK UI.SIText.SetText -> ...
[Info   :TraducaoLog] OK UI.TextElement.text -> ...
```

Dentro do jogo, o jeito mais fácil de ver a diferença: abra a lista de jogadores de uma partida e confira as posições **LD / LE / ZAG (C)** (sem o plugin aparece **DEF (D) / DEF (E)**), ou uma notícia de campeonato estadual ("**Estadual Baiano**" em vez de "Bahia State").

---

## Remover ou desligar

- **Desligar sem apagar:** abra `BepInEx/plugins/TraducaoLog/config.txt` e troque `UI.Traduzir=1` e `UI.Regras=1` por `0`.
- **Remover o plugin:** apague a pasta `BepInEx/plugins/TraducaoLog`. Nada mais no jogo foi alterado.
- **Remover o idioma:** apague `portuguese_br.ltc` da pasta `languages`.
- **Remover o BepInEx:** apague a pasta `BepInEx`, a pasta `dotnet`, `doorstop_config.ini` e a DLL proxy (`winhttp.dll` ou `version.dll`) da pasta do jogo. No Linux, apague também as opções de inicialização. (Só faça isso se **nenhum outro mod** seu depender dele.)

---

## Problemas comuns

**O jogo não abre depois de instalar o plugin.** Apague a pasta `BepInEx/plugins/TraducaoLog`, abra o jogo e, se abrir, abra uma [Issue](../../issues) com o seu `BepInEx/LogOutput.log`.

**O jogo abre, mas nada mudou.** (1) Confira se a pasta está em `BepInEx/plugins/TraducaoLog/` e **não** em `BepInEx/TraducaoLog` nem solta em `plugins/`. (2) Procure `TraducaoLog` no `LogOutput.log`: se não aparece nada, o BepInEx não carregou (volte ao passo 2.1; no Linux, confira as opções de inicialização). (3) Confira que o idioma está em *Português (Brasil)*.

**Não vejo `BepInEx/LogOutput.log`.** O BepInEx não carregou. No Linux, a causa quase sempre é o nome da DLL proxy errado nas opções de inicialização. No Windows, confira que extraiu o zip **na pasta do `fm.exe`** e não em uma subpasta.

**A tela fica preta ao abrir pela primeira vez.** Normal na primeira abertura com o BepInEx. Espere alguns minutos.

**O FPS caiu.** O plugin só troca texto e não deve pesar. Se notar queda, teste desligando o plugin (`config.txt`, `UI.Traduzir=0` e `UI.Regras=0`). Mods de estádio e céu costumam pesar mais que qualquer outra coisa.

**Posso usar com outros mods do FM27?** Sim. O plugin só mexe em texto e foi testado junto com mods de estádio, torcida, iluminação e câmera.

**Funciona no macOS?** Não testamos. O BepInEx para macOS é diferente do descrito aqui.

**Meu save vai quebrar se eu remover o plugin?** Não. O plugin não grava nada no save: só troca o texto exibido na tela.

---

Feito pela comunidade. Reporte erros de tradução nas [Issues](../../issues).
