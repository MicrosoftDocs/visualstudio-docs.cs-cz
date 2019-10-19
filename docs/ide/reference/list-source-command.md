---
title: Listovat zdroj – příkaz
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- Debug.ListSource
helpviewer_keywords:
- Debug.ListSource command
- list source command
- ListSource command
ms.assetid: e45f08d2-f4a3-49c3-9452-aa60508e2f74
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3123479d819662905020c27060e1234bd01c9077
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610506"
---
# <a name="list-source-command"></a>Listovat zdroj – příkaz
Zobrazí zadané řádky zdrojového kódu.

## <a name="syntax"></a>Syntaxe

```
Debug.ListSource [/Count:number] [/Current] [/File:filename]
[/Line:number] [/ShowLineNumbers:yes|no]
```

## <a name="switches"></a>Přepínače
/Count: `number`

Volitelné. Určuje počet řádků, které se mají zobrazit.

/Current

Volitelné. Zobrazuje aktuální řádek.

/File: `filename`

Volitelné. Cesta k souboru, který se má zobrazit Pokud není zadán žádný název souboru, příkaz zobrazí zdrojový kód pro řádek aktuálního příkazu.

/Line: `number`

Volitelné. Zobrazuje konkrétní číslo řádku.

/ShowLineNumbers: `yes|no`

Volitelné. Určuje, zda se mají zobrazit čísla řádků.

## <a name="example"></a>Příklad
Tento příklad uvádí zdrojový kód ze řádku 4 souboru Form1. vb s čísly řádků, které jsou viditelné.

```
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes
```

## <a name="see-also"></a>Viz také

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)