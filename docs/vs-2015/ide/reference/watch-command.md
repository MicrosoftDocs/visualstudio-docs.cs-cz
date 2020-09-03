---
title: Kukátko – příkaz | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.watch
helpviewer_keywords:
- Watch command
- Debug.Watch command
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 18e585064bb50db7a0497c6b96e428a662e953ab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72604833"
---
# <a name="watch-command"></a>Kukátko – příkaz
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vytvoří a otevře zadanou instanci okna **kukátka** . Okno **kukátka** můžete použít k výpočtu hodnot proměnných, výrazů a registrů pro úpravu těchto hodnot a k uložení výsledků.

## <a name="syntax"></a>Syntaxe

```
Debug.Watch[index]
```

## <a name="arguments"></a>Argumenty
 `index` Požadovanou. Číslo instance okna Kukátko.

## <a name="remarks"></a>Poznámky
 `index`Hodnota musí být celé číslo. Platné hodnoty jsou 1, 2, 3 nebo 4.

## <a name="example"></a>Příklad

```
>Debug.Watch1
```

## <a name="see-also"></a>Viz také
 [Automatické hodnoty a místní okna](../../debugger/autos-and-locals-windows.md) [Postupy: Úprava hodnoty v okně proměnné](https://msdn.microsoft.com/library/36f464ab-c900-4c0b-9ab3-557b3d9cdab5) [Postupy: použití dialogového okna QuickWatch dialogová](https://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867) [Visual Studio Commands](../../ide/reference/visual-studio-commands.md) [okna](../../ide/reference/command-window.md) [Najít/příkaz](../../ide/find-command-box.md) příkazy sady Visual Studio příkazy pro hledání/příkazy příkazového řádku sady [Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
