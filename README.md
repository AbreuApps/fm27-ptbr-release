# Tradução PT-BR — Football Manager 27 🇧🇷

Idioma **Português (Brasil)** para o FM27, separado do Português (Portugal) oficial.
Tutorial válido da **v1.2.3** em diante. Baixe tudo em **[Releases](../../releases/latest)**.

<!-- ULTIMA-VERSAO:INICIO (gerado por scripts/release.py, não edite à mão) -->
[![Última versão](https://img.shields.io/github/v/release/AbreuApps/fm27-ptbr-release?label=vers%C3%A3o&color=2ea44f)](https://github.com/AbreuApps/fm27-ptbr-release/releases/latest) [![Downloads](https://img.shields.io/github/downloads/AbreuApps/fm27-ptbr-release/total?label=downloads&color=blue)](https://github.com/AbreuApps/fm27-ptbr-release/releases) [![Issues](https://img.shields.io/github/issues/AbreuApps/fm27-ptbr-release?label=issues)](https://github.com/AbreuApps/fm27-ptbr-release/issues)

### 🆕 Última versão: [v1.2.4](https://github.com/AbreuApps/fm27-ptbr-release/releases/tag/v1.2.4) (06/11/2026)

- 🎯 **Botões táticos:** os valores de marcação, pressão e desarme foram encurtados e não truncam mais.
- 🧩 **"de do":** "o fato de do Cruzeiro" e variantes corrigidos em 15 lotes de texto, e o plugin ganhou novas regras de contração.
- 🏟️ **Resumos de partida:** agora "no estádio Mineirão"; acabou o "no estádio Estádio X".
- 🧹 **Português de Portugal:** 26 frases (72 variantes) de resumos de mercado, lesão, sorteio de copa, finanças do clube e felicidade do elenco ainda saíam em PT-PT; foram reescritas em português do Brasil.
- ✏️ **"Justa Causa Desportiva":** virou **"Justa Causa Esportiva"**.

🔌 O plugin é essencial: ele completa artigos e contrações (do, da, no, na) na tela. Sem BepInEx? O pacote completo já vem com pasta pronta.
<!-- ULTIMA-VERSAO:FIM -->

> Faça backup do save antes (`Documentos/Sports Interactive/Football Manager 27/games`).

## 1. Escolha o download

| Você... | Baixe |
|---|---|
| Nunca usou mods | `TraducaoLog-completo-<versão>.zip` |
| Já usa mods (BepInEx) | `portuguese_br.ltc` + `TraducaoLog-<versão>.zip` |
| Só quer a tradução | `portuguese_br.ltc` |

## 2. Instale (2 cópias)

**Pacote completo** — descompacte e copie:

1. o **conteúdo** de `1_COPIAR_PARA_PASTA_DO_JOGO` → pasta do jogo (ao lado do `fm.exe`)
2. `portuguese_br.ltc` de `2_COPIAR_PARA_languages` → pasta `languages`

**Já tem BepInEx** — copie:

1. a pasta `TraducaoLog` → `BepInEx/plugins/`
2. `portuguese_br.ltc` → pasta `languages`

## 3. Pastas

| | Windows | Linux (Steam/Proton) |
|---|---|---|
| **Pasta do jogo** | `C:\Program Files (x86)\Steam\steamapps\common\Football Manager 27\` | `~/.local/share/Steam/steamapps/common/Football Manager 27/` |
| **`languages`** | `Documentos\Sports Interactive\Football Manager 27\languages\` | `~/.local/share/Steam/steamapps/compatdata/4530370/pfx/drive_c/users/steamuser/Documents/Sports Interactive/Football Manager 27/languages/` |

Dica: Steam → botão direito no jogo → *Gerenciar* → *Explorar arquivos locais*.

## 4. Só no Linux

Steam → FM27 → Propriedades → *Opções de inicialização*:

```
WINEDLLOVERRIDES="version=n,b" %command%
```

## 5. Abra o jogo

A 1ª abertura com o pacote completo demora vários minutos: não feche.
Depois: **Preferências → Idioma → Português (Brasil)**.

---

⚠️ Já usa mods? **Não** use o pacote completo: ele sobrescreve o seu BepInEx.
Remover, problemas comuns e BepInEx manual: **[INSTALAR.md](INSTALAR.md)**.
Erros de tradução: [Issues](../../issues).
