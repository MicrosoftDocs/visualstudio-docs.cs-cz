---
title: Výpis zdrojového příkazu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Debug.ListSource
helpviewer_keywords:
- Debug.ListSource command
- list source command
- ListSource command
ms.assetid: e45f08d2-f4a3-49c3-9452-aa60508e2f74
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3f13689b6e3ac4db2d58c1def3a5d0dd05c219f2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672324"
---
# <a name="list-source-command"></a>Listovat zdroj – příkaz
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zobrazí zadané řádky zdrojového kódu.

## <a name="syntax"></a>Syntaxe

```
Debug.ListSource [/Count:number] [/Current] [/File:filename]
[/Line:number] [/ShowLineNumbers:yes|no]
```

## <a name="switches"></a>Přepínače
 /Count: `number` nepovinný. Určuje počet řádků, které se mají zobrazit.

 /Current je nepovinný. Zobrazuje aktuální řádek.

 /File: `filename` volitelné. Cesta k souboru, který se má zobrazit Pokud není zadán žádný název souboru, příkaz zobrazí zdrojový kód pro řádek aktuálního příkazu.

 /Line: `number` nepovinný. Zobrazuje konkrétní číslo řádku.

 /ShowLineNumbers: `yes|no` nepovinný. Určuje, zda se mají zobrazit čísla řádků.

## <a name="remarks"></a>Poznámky

## <a name="example"></a>Příklad
 Tento příklad uvádí zdrojový kód ze řádku 4 souboru Form1. vb s čísly řádků, které jsou viditelné.

```
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes
```

## <a name="see-also"></a>Viz také
 [Příkazové okno](../../ide/reference/command-window.md) pro [příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
