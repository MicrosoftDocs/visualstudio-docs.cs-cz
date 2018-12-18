---
title: Listovat zdroj – příkaz
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Debug.ListSource
helpviewer_keywords:
- Debug.ListSource command
- list source command
- ListSource command
ms.assetid: e45f08d2-f4a3-49c3-9452-aa60508e2f74
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 03a5d0699fced4d01d439942081b359454bcf476
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
ms.locfileid: "31943615"
---
# <a name="list-source-command"></a>Listovat zdroj – příkaz
Zobrazí zadané řádků zdrojového kódu.

## <a name="syntax"></a>Syntaxe

```
Debug.ListSource [/Count:number] [/Current] [/File:filename]
[/Line:number] [/ShowLineNumbers:yes|no]
```

## <a name="switches"></a>Přepínače
 / Počet:`number`

 Volitelné. Určuje počet řádků určených k zobrazení.

 / Aktuální

 Volitelné. Zobrazuje aktuálního řádku.

 Nebo souborů:`filename`

 Volitelné. Cesta souboru, který se zobrazí. Pokud není zadaný žádný název souboru, příkaz zobrazí zdrojový kód pro řádek aktuální příkaz.

 / Řádku:`number`

 Volitelné. Zobrazuje číslo konkrétní řádku.

 / ShowLineNumbers:`yes|no`

 Volitelné. Určuje, jestli se mají zobrazovat čísla řádků.

## <a name="example"></a>Příklad
 Tento příklad uvádí zdrojového kódu z řádku 4 souboru Form1.vb, s čísla řádků, které jsou viditelné.

```
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes
```

## <a name="see-also"></a>Viz také

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)