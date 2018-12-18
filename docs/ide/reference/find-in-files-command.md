---
title: Najít v souborech – příkaz
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.findinfiles
helpviewer_keywords:
- Edit.FindInFiles command
- find in files command
ms.assetid: 2fc78bfe-b339-4599-97f9-4cafd8a194d9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a4cf5078bb16d90744b83dfd99cf0c1da663149a
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33705018"
---
# <a name="find-in-files-command"></a>Najít v souborech – příkaz
Hledání souborů pomocí podmnožinu dostupných na možnostech **hledání v souborech** kartě **najít a nahradit** okno.

## <a name="syntax"></a>Syntaxe

```cmd
Edit.FindinFiles findwhat [/case] [/ext:extensions]
[/lookin:searchpath] [/names] [/options] [/reset] [/stop] [/sub]
[/text2] [/wild|/regex] [/word]
```

## <a name="arguments"></a>Arguments
 `findwhat` Vyžaduje se. Text tak, aby odpovídaly.

## <a name="switches"></a>Přepínače
 /Case nebo /c volitelné. Odpovídá dojít pouze v případě, že velká a malá písmena přesně shodovat s uvedenými v `findwhat` argument.

 /ext: `extensions` volitelné. Určuje příponám souborů pro soubory, které chcete vyhledávat. Pokud není zadaný, předchozí rozšíření se používá, pokud jeden jste dřív zadali.

 /lookin: `searchpath` volitelné. Adresář pro vyhledávání. Pokud cesta obsahuje mezery, uzavřete celý cesty do uvozovek.

 /Names nebo/n volitelné. Zobrazí seznam názvů souborů, které obsahují položky.

 / Options nebo /t volitelné. Zobrazí seznam aktuální nastavení možnosti Najít a nebude provádět vyhledávání.

 /Regex nebo /r volitelné. Používá předdefinované speciální znaky v `findwhat` argument jako zápisy, které představují vzory text místo literálové znaky. Úplný seznam regulárního výrazu znaky, najdete v části [regulární výrazy](../../ide/using-regular-expressions-in-visual-studio.md).

 / Reset nebo /e volitelné. Vrátí možnosti Najít obnoveno výchozí nastavení a nebude provádět vyhledávání.

 / stop volitelné. Aktuální operace vyhledávání zastaví, pokud je v průběhu. Hledání ignoruje všechny další argumenty při `/stop` byla zadána. K zastavení aktuální vyhledávání. například by zadejte následující operace:

```cmd
>Edit.FindinFiles /stop
```

 / Sub nebo /s volitelné. Vyhledá podsložky v adresáři zadaném v /lookin:`searchpath` argument.

 /Text2 nebo /2 volitelné. Zobrazí výsledky hledání v okně Najít 2 výsledky.

 /Wild nebo /l volitelné. Používá předdefinované speciální znaky v `findwhat` argument jako zápisy představující znak nebo posloupnost znaků.

 lze nebo /w volitelné. Vyhledá jenom celá slova.

## <a name="example"></a>Příklad
 Tento příklad hledá btnCancel v všechny .cls soubory umístěné ve složce "Moje projektů sady Visual Studio" a zobrazí informace shoda v okně Najít 2 výsledky.

```cmd
>Edit.FindinFiles btnCancel /lookin:"c:/My Visual Studio Projects" /ext:*.cls /text2
```

## <a name="see-also"></a>Viz také

- [Najít v souborech](../../ide/find-in-files.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Pole najít/příkaz](../../ide/find-command-box.md)
- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)