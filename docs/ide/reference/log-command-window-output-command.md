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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75568656"
---
# <a name="log-command-window-output-command"></a>Okno výstupu příkazů protokolu – příkaz

Zkopíruje všechny vstupy a výstupy z **příkazového** okna do souboru.

## <a name="syntax"></a>Syntaxe

```cmd
Tools.LogCommandWindowOutput [filename] [/on|/off] [/overwrite]
```

## <a name="arguments"></a>Arguments

`filename`\
Volitelné. Název souboru protokolu. Ve výchozím nastavení se soubor vytvoří ve složce profilu uživatele. Pokud název souboru již existuje, protokol je připojen na konec stávajícího souboru. Pokud není zadán žádný soubor, je použit poslední zadaný soubor. Pokud žádný z předchozích souborů neexistuje, vytvoří se výchozí soubor protokolu s názvem cmdline. log.

> [!TIP]
> Pokud chcete změnit umístění, kam se soubor protokolu uloží, zadejte úplnou cestu k souboru, která je ohraničená uvozovkami, pokud cesta obsahuje mezery.

## <a name="switches"></a>Přepínače

/on\
Volitelné. Spustí protokol pro **příkazové** okno v zadaném souboru a připojí soubor s novými informacemi.

/off\
Volitelné. Zastaví protokol okna **příkazového** řádku.

/overwrite\
Volitelné. Pokud soubor zadaný v argumentu `filename` odpovídá existujícímu souboru, je soubor přepsán.

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

## <a name="see-also"></a>Viz také:

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [okno Příkaz](../../ide/reference/command-window.md)
- [Pole Najít/příkaz](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
