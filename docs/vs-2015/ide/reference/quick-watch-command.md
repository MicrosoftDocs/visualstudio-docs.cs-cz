---
title: Příkaz pro Rychlé kukátko | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.quickwatch
helpviewer_keywords:
- Quick Watch command
- Debug.Quickwatch command
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: da9ba9572e121a9eba74cd8d624789032f1bb4a1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665660"
---
# <a name="quick-watch-command"></a>Rychlé kukátko – příkaz
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zobrazí vybraný nebo zadaný text v poli výraz v [dialogovém okně QuickWatch](https://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867). Toto dialogové okno můžete použít k výpočtu aktuální hodnoty proměnné nebo výrazu rozpoznaného ladicím programem nebo obsahu registru. Kromě toho můžete změnit hodnotu libovolné nekonstantní proměnné nebo obsah jakéhokoli registru.

## <a name="syntax"></a>Syntaxe

```
Debug.QuickWatchq [text]
```

## <a name="arguments"></a>Arguments
 `text` volitelné. Text, který se má přidat do dialogového okna **QuickWatch** .

## <a name="remarks"></a>Poznámky
 Pokud je hodnota `text` vynechána, je aktuálně vybraný text nebo slovo na kurzoru přidáno do okno Kukátko.

## <a name="example"></a>Příklad

```
>Debug.QuickWatch
```

## <a name="see-also"></a>Viz také
 [Postupy: použití dialogového okna QuickWatch](https://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867) [](../../ide/reference/visual-studio-commands.md) [příkazového](../../ide/reference/command-window.md) řádku [Najít/příkaz](../../ide/find-command-box.md) sady Visual Studio – [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
