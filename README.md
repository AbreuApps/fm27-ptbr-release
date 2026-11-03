# Tradução PT-BR — Football Manager 27 🇧🇷

Tradução do **Football Manager 27** para **Português (Brasil)**, instalada como idioma separado do Português (Portugal) oficial.

## 📥 Download

Na página de **[Releases](../../releases/latest)**:

| Arquivo | O que é | Obrigatório? |
|---|---|---|
| `portuguese_br.ltc` | A tradução | **Sim** |
| `TraducaoLog-1.2.zip` | Plugin opcional (precisa do BepInEx): corrige textos que vêm do banco do jogo e ajusta artigos e preposições | Não |

## 🛠️ Como instalar a tradução

1. Baixe `portuguese_br.ltc`.
2. Copie o arquivo para a pasta `languages` do FM27:

   | Sistema | Caminho |
   |---|---|
   | **Linux (Steam/Proton)** | `~/.local/share/Steam/steamapps/compatdata/4530370/pfx/drive_c/users/steamuser/Documents/Sports Interactive/Football Manager 27/languages/` |
   | **Windows** | `Documentos\Sports Interactive\Football Manager 27\languages\` |
   | **macOS** | `~/Library/Application Support/Football Manager 27/languages/` |

3. Reinicie o FM27 completamente (feche e abra).
4. No jogo: **Preferências → Idioma → "Português (Brasil)"**.

Pronto. A tradução funciona sozinha, sem o plugin.

## 🔌 Plugin opcional (TraducaoLog)

Alguns textos vêm do **banco de dados do jogo** e não do arquivo de idioma, então o `.ltc` sozinho não consegue traduzi-los:
nomes de lesões, de países e de torneios, prêmios da semana, estaduais, e o "do/da/no/na" diante de clubes e competições.
O plugin corrige esses casos na hora de exibir o texto. Exemplos:

| Sem o plugin | Com o plugin |
|---|---|
| `DEF (D)` / `DEF (E)` | `LD` / `LE` |
| `Bahia State` | `Estadual Baiano` |
| `Brazilian National 3rd Division Goal of the Week` | `Gol da Semana do Brasileirão Série C` |
| `Relatório Grêmio` | `Relatório do Grêmio` |
| `risco de lesão Chelsea` | `risco de lesão do Chelsea` |
| `O Portuguesa` | `A Portuguesa` |
| `Cruzeiro Esporte Clube SAF` | `Cruzeiro` |

O plugin **não grava nenhum log nem salva texto do jogo**: só troca o texto na tela. Convive com os mods de estádio, torcida e iluminação do FM27.

➡️ **Guia completo (BepInEx + plugin, Windows e Linux): [INSTALAR.md](INSTALAR.md)**

## ❓ FAQ

**Não aparece na lista de idiomas?**
Confira se o arquivo está na pasta `languages` correta e reinicie o jogo por completo.

**Posso usar junto do Português (Portugal) oficial?**
Sim. É um idioma separado; não substitui o oficial.

**É seguro?**
O `.ltc` é só um arquivo de tradução. Não modifica executáveis nem arquivos do jogo. O plugin é opcional, e o BepInEx altera a forma como o jogo abre, então vale fazer backup do save antes (o guia explica).

**Ainda vejo algumas coisas em inglês.**
Sem o plugin, nomes de lesões, países, adjetivos de nacionalidade e fases de alguns torneios continuam vindo em inglês, pois fazem parte do banco do jogo. Instale o plugin. Se ainda sobrar algo, abra uma Issue com um print.

---

Feito pela comunidade. Reporte erros de tradução nas [Issues](../../issues).
