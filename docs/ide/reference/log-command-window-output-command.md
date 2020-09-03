---
title: Protokolovat výstup příkazového okna – příkaz
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- tools.logcommandwindowoutput
helpviewer_keywords:
- log Command window output command
- View.LogCommandWindowOutput command
ms.assetid: d4ecec35-5af4-4954-8d60-2cd24583fbb4
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b6ba8fb419726018bd089e217386ab5dbd6a9c33
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75568656"
---
# <a name="log-command-window-output-command"></a>Okno výstupu příkazů protokolu – příkaz

Zkopíruje všechny vstupy a výstupy z **příkazového** okna do souboru.

## <a name="syntax"></a>Syntaxe

```cmd
Tools.LogCommandWindowOutput [filename] [/on|/off] [/overwrite]
```

## <a name="arguments"></a>Argumenty

`filename`\
Nepovinný parametr. Název souboru protokolu. Ve výchozím nastavení se soubor vytvoří ve složce profilu uživatele. Pokud název souboru již existuje, protokol je připojen na konec stávajícího souboru. Pokud není zadán žádný soubor, je použit poslední zadaný soubor. Pokud žádný z předchozích souborů neexistuje, vytvoří se výchozí soubor protokolu s názvem cmdline. log.

> [!TIP]
> Pokud chcete změnit umístění, kam se soubor protokolu uloží, zadejte úplnou cestu k souboru, která je ohraničená uvozovkami, pokud cesta obsahuje mezery.

## <a name="switches"></a>Přepínače

parametry/on
Nepovinný parametr. Spustí protokol pro **příkazové** okno v zadaném souboru a připojí soubor s novými informacemi.

/off.
Nepovinný parametr. Zastaví protokol okna **příkazového** řádku.

/overwrite
Nepovinný parametr. Pokud soubor zadaný v `filename` argumentu odpovídá existujícímu souboru, je soubor přepsán.

## <a name="remarks"></a>Poznámky

Pokud není zadaný žádný soubor, ve výchozím nastavení se vytvoří soubor cmdline. log. Ve výchozím nastavení je alias tohoto příkazu protokolem.

## <a name="examples"></a>Příklady

Tento příklad vytvoří nový soubor protokolu cmdlog a spustí protokol příkazů.

```cmd
>Tools.LogCommandWindowOutput cmdlog
```

Tento příklad zastaví příkazy protokolování.

```cmd
>Tools.LogCommandWindowOutput /off
```

Tento příklad obnoví protokolování příkazů v dříve použitém souboru protokolu.

```cmd
>Tools.LogCommandWindowOutput /on
```

## <a name="see-also"></a>Viz také

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Okno Příkaz](../../ide/reference/command-window.md)
- [Pole Najít/příkaz](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
