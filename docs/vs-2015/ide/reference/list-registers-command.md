---
title: Listovat příkaz pro Registry | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listregisters
helpviewer_keywords:
- list registers command
- Debug.ListRegisters command
- ListRegisters command
ms.assetid: 19a9d789-f6c9-46b3-b1f6-4934fc33e055
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3476244d3044eb80dbfce3559479421b012cc5fa
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659503"
---
# <a name="list-registers-command"></a>Listovat registry – příkaz
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zobrazí hodnotu vybraných registrů a umožňuje upravit seznam registrů, které se mají zobrazit.

## <a name="syntax"></a>Syntaxe

```
Debug.ListRegisters [/Display [{register|registerGroup}...]] [/List]
[/Watch [{register|registerGroup}...]]
[/Unwatch [{register|registerGroup}...]]
```

## <a name="switches"></a>Přepínače
 /Display [{`register`&#124; `registerGroup`}...] Zobrazí hodnoty zadaného `register` nebo `registerGroup`. Pokud není zadána žádná `register` ani `registerGroup`, zobrazí se výchozí seznam registrů. Pokud není zadán žádný přepínač, chování je stejné. Příklad:

 `Debug.ListRegisters /Display eax`

 je ekvivalentem

 `Debug.ListRegisters eax`

 /List zobrazí všechny skupiny registrů v seznamu.

 /Watch [{`register`&#124; `registerGroup`}...] Přidá do seznamu jednu nebo více `register` nebo `registerGroup` hodnot.

 /Unwatch [{`register`&#124; `registerGroup`}...] Odebere ze seznamu jednu nebo více `register` nebo `registerGroup` hodnot.

## <a name="remarks"></a>Poznámky
 Alias `r` lze použít místo `Debug.ListRegisters`.

## <a name="example"></a>Příklad
 V tomto příkladu se k zobrazení hodnot `Flags` skupiny registru používá `r` aliasu `Debug.ListRegisters`.

```
r /Display Flags
```

## <a name="see-also"></a>Viz také
 Základy ladění [příkazů sady Visual Studio](../../ide/reference/visual-studio-commands.md) [: registruje okno](../../debugger/debugging-basics-registers-window.md) [Postupy: použití okna Registry](../../debugger/how-to-use-the-registers-window.md)
