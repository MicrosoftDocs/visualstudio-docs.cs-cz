---
title: Protokolovat výstupní příkaz okna příkazu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- tools.logcommandwindowoutput
helpviewer_keywords:
- log Command window output command
- View.LogCommandWindowOutput command
ms.assetid: d4ecec35-5af4-4954-8d60-2cd24583fbb4
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d9a5a29cd63f9d51f86d41d2f0f5986a77666318
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666869"
---
# <a name="log-command-window-output-command"></a>Protokolovat výstup příkazového okna – příkaz
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zkopíruje všechny vstupy a výstupy z **příkazového** okna do souboru.

## <a name="syntax"></a>Syntaxe

```
Tools.LogCommandWindowOutput [filename] [/on|/off] [/overwrite]
```

## <a name="arguments"></a>Argumenty
 `filename` Volitelné. Název souboru protokolu. Ve výchozím nastavení se soubor vytvoří ve složce profilu uživatele. Pokud název souboru již existuje, protokol je připojen na konec stávajícího souboru. Pokud není zadán žádný soubor, je použit poslední zadaný soubor. Pokud žádný z předchozích souborů neexistuje, vytvoří se výchozí soubor protokolu s názvem cmdline. log.

> [!TIP]
> Pokud chcete změnit umístění, kam se soubor protokolu uloží, zadejte úplnou cestu k souboru, která je ohraničená uvozovkami, pokud cesta obsahuje mezery.

## <a name="switches"></a>Přepínače
 /On je nepovinný. Spustí protokol pro **příkazové** okno v zadaném souboru a připojí soubor s novými informacemi.

 /off. je nepovinný. Zastaví protokol okna **příkazového** řádku.

 /overwrite – nepovinné. Pokud soubor zadaný v `filename` argumentu odpovídá existujícímu souboru, je soubor přepsán.

## <a name="remarks"></a>Poznámky
 Pokud není zadaný žádný soubor, ve výchozím nastavení se vytvoří soubor cmdline. log. Ve výchozím nastavení je alias tohoto příkazu protokolem.

## <a name="examples"></a>Příklady
 Tento příklad vytvoří nový soubor protokolu cmdlog a spustí protokol příkazů.

```
>Tools.LogCommandWindowOutput cmdlog
```

 Tento příklad zastaví příkazy protokolování.

```
>Tools.LogCommandWindowOutput /off
```

 Tento příklad obnoví protokolování příkazů v dříve použitém souboru protokolu.

```
>Tools.LogCommandWindowOutput /on
```

## <a name="see-also"></a>Viz také
 [Příkazy](../../ide/reference/visual-studio-commands.md) [příkazového](../../ide/reference/command-window.md) řádku [find/Command](../../ide/find-command-box.md) v příkazu Visual Studio Command a Command [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
