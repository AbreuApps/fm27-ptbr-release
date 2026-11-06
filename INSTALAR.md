# Como instalar a tradução PT-BR do FM27

> **Antes:** copie seu save (`Documentos/Sports Interactive/Football Manager 27/games`). O idioma não mexe nele, mas o BepInEx altera como o jogo abre.

## Pastas que você vai usar

| | Windows | Linux (Steam/Proton) |
|---|---|---|
| **Pasta do jogo** (onde está o `fm.exe`) | `C:\Program Files (x86)\Steam\steamapps\common\Football Manager 27\` | `~/.local/share/Steam/steamapps/common/Football Manager 27/` |
| **Pasta `languages`** | `Documentos\Sports Interactive\Football Manager 27\languages\` | `~/.local/share/Steam/steamapps/compatdata/4530370/pfx/drive_c/users/steamuser/Documents/Sports Interactive/Football Manager 27/languages/` |

Dica: Steam → botão direito no jogo → *Gerenciar* → *Explorar arquivos locais* abre a pasta do jogo. No macOS o idioma vai em `~/Library/Application Support/Football Manager 27/languages/` (plugin não testado).

---

## Opção A — Pacote completo (para quem não tem mods)

Baixe `TraducaoLog-completo-<versão>.zip`, descompacte e faça **2 cópias**:

1. **Conteúdo** de `1_COPIAR_PARA_PASTA_DO_JOGO` → **pasta do jogo** (aceite substituir). Deve ficar ao lado do `fm.exe`: `BepInEx/`, `dotnet/`, `doorstop_config.ini`, `.doorstop_version`, `version.dll`.
2. `2_COPIAR_PARA_languages/portuguese_br.ltc` → **pasta `languages`**.

**Só no Linux:** Steam → FM27 → Propriedades → *Opções de inicialização*:

```
WINEDLLOVERRIDES="version=n,b" %command%
```

Abra o jogo. **A 1ª abertura demora vários minutos** (o BepInEx prepara os arquivos): não feche. Depois: **Preferências → Idioma → Português (Brasil)**.

> ⚠️ **Já usa mods?** Não use este pacote, ele sobrescreveria o seu BepInEx. Use a Opção B.

O pacote traz o [BepInEx 6.0.0-be.785](https://github.com/BepInEx/BepInEx) (LGPL-2.1) sem alterações.

---

## Opção B — Já tenho BepInEx (ou só quero o idioma)

1. `portuguese_br.ltc` → **pasta `languages`**.
2. *(plugin, opcional)* descompacte `TraducaoLog-<versão>.zip` e copie a **pasta `TraducaoLog`** inteira para `BepInEx/plugins/` do jogo:

   ```
   BepInEx/plugins/TraducaoLog/TraducaoLog.dll   ← e os .tsv ao lado
   ```

   Não solte a DLL direto em `plugins/`: os `.tsv` precisam ficar junto dela.
3. Reabra o jogo e escolha **Português (Brasil)**.

**Quer o plugin mas não tem BepInEx e não quer o pacote?** Instale o BepInEx **6, build be.785, Unity IL2CPP, Windows x64** (`BepInEx-Unity.IL2CPP-win-x64-6.0.0-be.785…zip`, em <https://builds.bepinex.dev/projects/bepinex_be>) na pasta do jogo. No Linux, use a opção de inicialização acima, trocando `version` por `winhttp` (o zip oficial usa o nome `winhttp.dll`). Cuidado: a página de Releases do GitHub mostra a série 5.x no topo, que **não funciona** no FM27.

---

## Atualizar de uma versão antiga

Substitua o `portuguese_br.ltc` e a pasta `TraducaoLog`. O save não é afetado.

## Conferir se o plugin carregou

Abra `BepInEx/LogOutput.log` e procure `TraducaoLog`: deve aparecer `DICIONARIO carregado`. No jogo, as posições aparecem como **LD / LE / ZAG** (sem o plugin: DEF (D) / DEF (E)).

## Remover ou desligar

- **Desligar o plugin:** em `BepInEx/plugins/TraducaoLog/config.txt`, troque `UI.Traduzir=1` e `UI.Regras=1` por `0`.
- **Remover o plugin:** apague a pasta `BepInEx/plugins/TraducaoLog`.
- **Remover o idioma:** apague `portuguese_br.ltc` de `languages`.
- **Remover o BepInEx:** apague `BepInEx`, `dotnet`, `doorstop_config.ini`, `.doorstop_version` e `version.dll` (ou `winhttp.dll`) da pasta do jogo. Só se nenhum outro mod depender dele.

## Problemas comuns

- **Não aparece na lista de idiomas:** confira o caminho da `languages` e reinicie o jogo por completo.
- **Tela preta na 1ª abertura:** normal com BepInEx. Espere alguns minutos.
- **Nada mudou com o plugin:** confira `BepInEx/plugins/TraducaoLog/` (não solta, não em `BepInEx/TraducaoLog`), e se `LogOutput.log` existe. Se não existe, o BepInEx não carregou: no Windows, confira que extraiu na pasta do `fm.exe`; no Linux, confira a opção de inicialização.
- **O jogo não abre:** apague `BepInEx/plugins/TraducaoLog`; se abrir, abra uma [Issue](../../issues) com o `LogOutput.log`.
- **Meu save quebra se remover o plugin?** Não. O plugin só troca texto na tela.

---

Feito pela comunidade. Reporte erros de tradução nas [Issues](../../issues).
