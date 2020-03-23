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
ms.openlocfilehash: 6c211773f20ab4643b62c8c71fc6ae6581a91987
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "72747893"
---
# <a name="list-source-command"></a>Listovat zdroj – příkaz
Zobrazí zadané řádky zdrojového kódu.

## <a name="syntax"></a>Syntaxe

```
Debug.ListSource [/Count:number] [/Current] [/File:filename]
[/Line:number] [/ShowLineNumbers:yes|no]
```

## <a name="switches"></a>Přepínače
/Počet:`number`

Nepovinný parametr. Určuje počet řádků, které se mají zobrazit.

/Aktuální

Nepovinný parametr. Zobrazuje aktuální řádek.

/Soubor:`filename`

Nepovinný parametr. Cesta k souboru, který chcete zobrazit. Pokud není zadán žádný název souboru, příkaz zobrazí zdrojový kód pro řádek aktuálního příkazu.

/Čára:`number`

Nepovinný parametr. Zobrazí konkrétní číslo řádku.

/ZobrazitČísla:`yes|no`

Nepovinný parametr. Určuje, zda se mají zobrazit čísla řádků.

## <a name="example"></a>Příklad
V tomto příkladu je uveden zdrojový kód z řádku 4 souboru Form1.vb s viditelnými čísly řádků.

```
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes
```

## <a name="see-also"></a>Viz také

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)