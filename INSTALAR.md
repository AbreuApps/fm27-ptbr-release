# Como instalar a tradução PT-BR do FM27

> **Antes:** copie seu save (`Documentos/Sports Interactive/Football Manager 27/games`). O idioma não mexe nele, mas o BepInEx altera como o jogo abre.

## Pastas que você vai usar

| | Windows | Linux (Steam/Proton) |
|---|---|---|
| **Pasta do jogo** (onde está o `fm.exe`) | `C:\Program Files (x86)\Steam\steamapps\common\Football Manager 27\` | `~/.local/share/Steam/steamapps/common/Football Manager 27/` |
| **Pasta `languages`** | `Documentos\Sports Interactive\Football Manager 27\languages\` | `~/.local/share/Steam/steamapps/compatdata/4530370/pfx/drive_c/users/steamuser/Documents/Sports Interactive/Football Manager 27/languages/` |

Dica: Steam → botão direito no jogo → *Gerenciar* → *Explorar arquivos locais* abre a pasta do jogo. No macOS o idioma vai em `~/Library/Application Support/Football Manager 27/languages/` (plugin não testado).

## 🗂️ A pasta `TaoMods`

Nossos mods ficam todos numa pasta só, dentro do BepInEx:

```
BepInEx/plugins/TaoMods/TraducaoLog/      ← plugin da tradução
BepInEx/plugins/TaoMods/TaoStadiumMod/    ← Estádios do Brasil 3D (se você usa)
```

Cada mod fica na sua subpasta. Não solte DLL direto em `plugins/`.

> 🏟️ **Usa os [Estádios do Brasil 3D](https://github.com/AbreuApps/fm27-estadios-release)?** O pacote dos estádios já traz o plugin da tradução em `TaoMods/TraducaoLog`. Para ficar com a tradução mais nova, siga a Opção B: troque só a pasta `TaoMods/TraducaoLog` e o `portuguese_br.ltc`. Não mexa em `TaoMods/TaoStadiumMod`.

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

> ⚠️ **Já usa mods (inclusive os Estádios)?** Não use este pacote, ele sobrescreveria o seu BepInEx. Use a Opção B.

O pacote traz o [BepInEx 6.0.0-be.785](https://github.com/BepInEx/BepInEx) (LGPL-2.1) sem alterações.

---

## Opção B — Já tenho BepInEx

1. `portuguese_br.ltc` → **pasta `languages`**.
2. Descompacte `TraducaoLog-<versão>.zip` e copie a **pasta `TaoMods`** para `BepInEx/plugins/` do jogo (aceite juntar com a `TaoMods` que já existir):

   ```
   BepInEx/plugins/TaoMods/TraducaoLog/TraducaoLog.dll   ← e os .tsv ao lado
   ```

3. Se existir a pasta antiga `BepInEx/plugins/TraducaoLog` (fora de `TaoMods`, das versões até a 1.2.7), **apague**: só pode haver uma cópia do plugin.
4. Reabra o jogo e escolha **Português (Brasil)**.

O plugin é **essencial**: é ele que completa artigos e contrações (do, da, no, na) e traduz textos que vêm do banco do jogo (lesões, países, fases). Só o `.ltc`, sem plugin, funciona, mas esses textos ficam incompletos.

**Quer o plugin mas não tem BepInEx e não quer o pacote?** Instale o BepInEx **6, Unity IL2CPP, Windows x64** (build be.785 ou mais nova, em <https://builds.bepinex.dev/projects/bepinex_be>) na pasta do jogo. No Linux, use a opção de inicialização acima, trocando `version` por `winhttp` (o zip oficial usa o nome `winhttp.dll`). Cuidado: a página de Releases do GitHub mostra a série 5.x no topo, que **não funciona** no FM27.

---

## Atualizar de uma versão antiga

Substitua o `portuguese_br.ltc` e a pasta `TaoMods/TraducaoLog`. Vindo da 1.2.6 ou anterior, apague também `BepInEx/plugins/TraducaoLog` (o lugar antigo). O save não é afetado.

## Conferir se o plugin carregou

Abra `BepInEx/LogOutput.log` e procure `TraducaoLog`: deve aparecer `Loading [TraducaoLog <versão>]` e `DICIONARIO carregado`. No jogo, as posições aparecem como **LD / LE / ZAG** (sem o plugin: DEF (D) / DEF (E)).

Se aparecer `Skipping [TraducaoLog ...] because a newer version exists`, há duas cópias: apague a pasta antiga (`BepInEx/plugins/TraducaoLog`).

## Remover ou desligar

- **Desligar o plugin:** em `BepInEx/plugins/TaoMods/TraducaoLog/config.txt`, troque `UI.Traduzir=1` e `UI.Regras=1` por `0`.
- **Remover o plugin:** apague a pasta `BepInEx/plugins/TaoMods/TraducaoLog` (os estádios continuam funcionando).
- **Remover o idioma:** apague `portuguese_br.ltc` de `languages`.
- **Remover o BepInEx:** apague `BepInEx`, `dotnet`, `doorstop_config.ini`, `.doorstop_version` e `version.dll` (ou `winhttp.dll`) da pasta do jogo. Só se nenhum outro mod depender dele.

## Problemas comuns

- **Não aparece na lista de idiomas:** confira o caminho da `languages` e reinicie o jogo por completo.
- **Tela preta na 1ª abertura:** normal com BepInEx. Espere alguns minutos.
- **Nada mudou com o plugin:** confira `BepInEx/plugins/TaoMods/TraducaoLog/` (não solta em `plugins/`, não em `BepInEx/TraducaoLog`), e se `LogOutput.log` existe. Se não existe, o BepInEx não carregou: no Windows, confira que extraiu na pasta do `fm.exe`; no Linux, confira a opção de inicialização.
- **O jogo não abre:** apague `BepInEx/plugins/TaoMods/TraducaoLog`; se abrir, abra uma [Issue](../../issues) com o `LogOutput.log`.
- **Meu save quebra se remover o plugin?** Não. O plugin só troca texto na tela.

---

Feito pela comunidade. Reporte erros de tradução nas [Issues](../../issues).
