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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568656"
---
# <a name="log-command-window-output-command"></a>Okno výstupu příkazů protokolu – příkaz

Zkopíruje veškerý vstup a výstup z okna **Příkaz** do souboru.

## <a name="syntax"></a>Syntaxe

```cmd
Tools.LogCommandWindowOutput [filename] [/on|/off] [/overwrite]
```

## <a name="arguments"></a>Argumenty

`filename`\
Nepovinný parametr. Název souboru protokolu. Ve výchozím nastavení je soubor vytvořen ve složce profilu uživatele. Pokud název souboru již existuje, protokol je připojen na konec existujícího souboru. Pokud není zadán žádný soubor, použije se poslední zadaný soubor. Pokud neexistuje žádný předchozí soubor, je vytvořen výchozí soubor protokolu, který se nazývá cmdline.log.

> [!TIP]
> Chcete-li změnit umístění, kam je uložen soubor protokolu, zadejte úplnou cestu k souboru obklopenou uvozovkami, pokud cesta obsahuje mezery.

## <a name="switches"></a>Přepínače

/on\
Nepovinný parametr. Spustí protokol okna **Příkaz** v zadaném souboru a připojí soubor k novým informacím.

/off\
Nepovinný parametr. Zastaví protokol pro okno **Příkaz.**

/přepsat\
Nepovinný parametr. Pokud soubor zadaný `filename` v argumentu odpovídá existujícímu souboru, je soubor přepsán.

## <a name="remarks"></a>Poznámky

Pokud není zadán žádný soubor, soubor cmdline.log je vytvořen ve výchozím nastavení. Ve výchozím nastavení je alias pro tento příkaz Protokol.

## <a name="examples"></a>Příklady

Tento příklad vytvoří nový soubor protokolu, cmdlog a spustí protokol příkazů.

```cmd
>Tools.LogCommandWindowOutput cmdlog
```

Tento příklad zastaví protokolování příkazů.

```cmd
>Tools.LogCommandWindowOutput /off
```

Tento příklad obnoví protokolování příkazů v dříve použitém souboru protokolu.

```cmd
>Tools.LogCommandWindowOutput /on
```

## <a name="see-also"></a>Viz také

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Pole Najít/Příkaz](../../ide/find-command-box.md)
- [Aliasy příkazů Visual Studia](../../ide/reference/visual-studio-command-aliases.md)
