---
title: Listovat zdroj – příkaz
description: Přečtěte si o příkazu seznam zdrojů a o tom, jak se zobrazí zadané řádky zdrojového kódu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- Debug.ListSource
helpviewer_keywords:
- Debug.ListSource command
- list source command
- ListSource command
ms.assetid: e45f08d2-f4a3-49c3-9452-aa60508e2f74
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ae2463a3d8dd295fcba9bf264e1ad3fa250169d4
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305282"
---
# <a name="list-source-command"></a>Listovat zdroj – příkaz
Zobrazí zadané řádky zdrojového kódu.

## <a name="syntax"></a>Syntax

```
Debug.ListSource [/Count:number] [/Current] [/File:filename]
[/Line:number] [/ShowLineNumbers:yes|no]
```

## <a name="switches"></a>Přepínače
Výpočtu`number`

Nepovinný parametr. Určuje počet řádků, které se mají zobrazit.

/Current

Nepovinný parametr. Zobrazuje aktuální řádek.

Souborů`filename`

Nepovinný parametr. Cesta k souboru, který se má zobrazit Pokud není zadán žádný název souboru, příkaz zobrazí zdrojový kód pro řádek aktuálního příkazu.

Link`number`

Nepovinný parametr. Zobrazuje konkrétní číslo řádku.

Showlinenumberszobrazitčíslařádků`yes|no`

Nepovinný parametr. Určuje, zda se mají zobrazit čísla řádků.

## <a name="example"></a>Příklad
Tento příklad uvádí zdrojový kód ze řádku 4 souboru Form1. vb s čísly řádků, které jsou viditelné.

```
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes
```

## <a name="see-also"></a>Viz také

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)