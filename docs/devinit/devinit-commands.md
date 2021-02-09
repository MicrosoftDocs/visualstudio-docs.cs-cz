---
title: Příkazy devinit
description: Podrobnosti o tom, jak použít příkazy devinit k instalaci komponent.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 9cd9fef6cebdefc190d37c067616e51c6d3e372f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908129"
---
# <a name="devinit-commands"></a>příkazy devinit

## <a name="init"></a>Init

```console
devinit init
```

Inicializujte prostředí spuštěním nástrojů určených v [.devinit.jsv](devinit-json.md) souboru.

### <a name="options-for-init"></a>Možnosti pro init

Volitelné možnosti pro `devinit init` příkaz

| Argument             | Povinné | Popis                                                               |
|----------------------|----------|---------------------------------------------------------------------------|
| -f,--soubor            | Ne       | Cesta k `.devinit.json` souboru                                         |
| --Error-Action       | Ne       | Určuje, jak se mají zpracovávat chyby. Možnosti: zastavit, ignorovat, pokračovat (výchozí).|
| -v,--verbose         | Ne       | Vygeneruje podrobný výstup.                                                      |
| -n,--suchého běhu         | Ne       | Suché spuštění.                                                                  |

#### <a name="--file-argument"></a>--argument souboru

Určuje cestu k _devinit.jsv_ souboru. Pokud není zadán parametr--File, hledáme výchozí soubor v následujících umístěních:

* {Current-Directory} \\.devinit.jsna
* {Current-Directory} \\devinit.jsna
* {Current-Directory} \\ . devinit \\.devinit.js
* {Current-Directory} \\ . devinit \\devinit.js
* {Current-Directory} \\ devinit \\.devinit.js
* {Current-Directory} \\ devinit \\devinit.js
* {Current-Directory} \\ . devcontainer \\.devinit.js
* {Current-Directory} \\ . devcontainer \\devinit.js

> [!NOTE]
> Pokud je nalezeno více výchozích souborů, pak devinit použije soubor, který se zobrazí jako první v seznamu výše.

#### <a name="--error-action-argument"></a>--error – argument akce

Viz [níže](#options-for-run).

#### <a name="--verbose-switch"></a>--verbose Switch

Viz [níže](#options-for-run).

#### <a name="--dry-run-switch"></a>– přepínač suchého běhu

Viz [níže](#options-for-run).

## <a name="run"></a>Spustit

```console
devinit run -t <toolname>
```

Spustí konkrétní nástroj, níže uvedené parametry. Konkrétní použití najdete v [dokumentaci](devinit-tool-list.md) k jednotlivým nástrojům.

### <a name="options-for-run"></a>Možnosti spuštění

Možnosti `devinit run` příkazu

| Argument                                      | Povinné | Popis                                                                          |
|-----------------------------------------------|----------|--------------------------------------------------------------------------------------|
| -t,--nástroj                                     | Ano      | Povinná hodnota. Název nástroje.                                                             |
| -i,--vstup                                    | Ne       | Vstupní hodnota nástroje Například název souboru, balíček nebo název.                     |
| --Error-Action                                | Ne       | Určuje způsob zpracování chyb nástrojů: zastavit, ignorovat, pokračovat. Výchozím nastavením je zastavit. |
| -v,--verbose                                  | Ne       | Vygeneruje podrobný výstup.                                                                 |
| -n,--suchého běhu                                  | Ne       | Suché spuštění.                                                                             |
| --&lt;arg1 &gt; &lt; arg2 &gt; ... &lt; argN&gt;  | Ne       | Další argumenty příkazového řádku nástroje.                                       |

#### <a name="--error-action-argument"></a>--error – argument akce

Určuje akci, která má být provedena, pokud nástroj vrátí nenulový ukončovací kód. Platné hodnoty jsou:

| Argument | Description                                                                                                                                                                                                                                                                           |
|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| continue | Pokračovat v zpracovávání jiných nástrojů po vygenerování chyby se standardní chybou Ukončovací kód devinit.exe je nenulový (selhání). Toto chování je podobné akci zastavení chyby, ale zpracování pokračuje. `continue` je výchozí chyba – akce příkazu init.              |
| ignorovat   | Pokračujte v zpracovávání jiných nástrojů po vygenerování upozornění na standardní výstup. Ukončovací kód procesu DevInit by měl vždy být nula (úspěch). `ignore`Nastavení ignoruje všechny chyby.                                                                                                      |
| Zastavit     | Vygeneruje chybu standardní chyby a zastaví zpracování nástrojů. Ukončovací kód devinit.exe je nenulový (selhání). Jedná se o podobnou akci pokračovat při chybě, ale zpracování je zastaveno při první zjištěné chybě. `stop` je výchozí chyba – akce pro všechny příkazy s výjimkou init. |

#### <a name="--dry-run-switch"></a>– přepínač suchého běhu

Příkazy nástroje echo, které by byly spuštěny. Některé nástroje mohou podniknout další kroky popsané pro tento nástroj. 

#### <a name="--verbose-switch"></a>--verbose Switch

Vygeneruje podrobný výstup do standardního výstupu. Pokud nástroj, který má být spuštěn, podporuje možnost verbose, rozšiřte podrobný přepínač na nástroj.

#### <a name="--dry-run-switch"></a>– přepínač suchého běhu

Příkazy nástroje echo, které by se spustily, ale nespouštějí žádné nástroje.

#### <a name="additional-command-line-arguments"></a>Další argumenty příkazového řádku

Použití prvku `<arg>` , který obsahuje místo ve své hodnotě, musí zahrnovat další dvojici řídicích uvozovek.

```console
devinit run -t <toolname> -<somearg> "<some value>"
```

Pro instalaci dotnet do konkrétního adresáře `C:\Program Files\dotnet` :

```console
devinit run -t require-dotnetcoresdk --"-InstallDir \"C:\Program Files\dotnet\""
```

## <a name="list"></a>Seznam

```console
devinit list
```

Zobrazí seznam všech dostupných nástrojů.

## <a name="show"></a>Zobrazit

```console
devinit show -t <toolname>
```

| Argument       | Povinné | Popis                                                                          |
|----------------|----------|--------------------------------------------------------------------------------------|
| -t,--nástroj      | Ano      | Povinná hodnota. Název nástroje.                                                             |

Vytiskne informace o nápovědě pro daný nástroj.

## <a name="version"></a>Verze

```console
devinit version
```

Vytiskne aktuální informace o verzi pro devinit.

## <a name="help"></a>Nápověda

```console
devinit help
devinit help list
```

Vytiskne text v nápovědě pro devinit nebo pro konkrétní příkaz `devinit <command>` .
 
