---
title: Najít příkaz | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.find
helpviewer_keywords:
- Find command
- Edit.Find command
ms.assetid: f0c705dc-2b97-423d-abbf-5584d4827208
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6ce0e4a3aaca752cbdeda0a83e469977306c3404
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657686"
---
# <a name="find-command"></a>Najít – příkaz
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vyhledá soubory pomocí podmnožiny možností dostupných na kartě **najít v souborech** okna **Najít a nahradit** .

## <a name="syntax"></a>Syntaxe

```
Edit.Find findwhat [/case] [/doc | /proc | /open | /sel]
[/markall] [/options] [/reset] [/up] [/wild | /regex] [/word]
```

## <a name="arguments"></a>Argumenty
 `findwhat` Požadovanou. Text, který se má shodovat.

## <a name="switches"></a>Přepínače
 /Case nebo/c volitelné. Shody se objeví pouze v případě, že velká a malá písmena přesně odpovídají znakům zadaným v `findwhat` argumentu.

 /doc nebo/d volitelné. Vyhledá pouze aktuální dokument. Zadejte pouze jeden z dostupných oborů hledání,, `/doc` , `/proc` `/open` nebo `/sel` .

 /markall nebo/m volitelné. Umístí grafiku na každý řádek, který obsahuje shodu hledání v rámci aktuálního dokumentu.

 /Open nebo/o volitelné. Vyhledá všechny otevřené dokumenty, jako by se jednalo o jeden dokument. Zadejte pouze jeden z dostupných oborů hledání,, `/doc` , `/proc` `/open` nebo `/sel` .

 /Options nebo/t volitelné. Zobrazí seznam aktuálních nastavení možností hledání a neprovádí hledání.

 /Proc nebo/p volitelné. Vyhledá pouze aktuální proceduru. Zadejte pouze jeden z dostupných oborů hledání,, `/doc` , `/proc` `/open` nebo `/sel` .

 /Reset po vyčištění nebo/e volitelné. Vrátí možnosti hledání do jejich výchozího nastavení a neprovádí hledání.

 /SEL nebo/s volitelné. Vyhledá pouze aktuální výběr. Zadejte pouze jeden z dostupných oborů hledání,, `/doc` , `/proc` `/open` nebo `/sel` .

 /up nebo/u je nepovinný. Vyhledá z aktuálního umístění v souboru směrem k začátku souboru. Ve výchozím nastavení vyhledávání začíná na aktuálním umístění v souboru a hledá na konci souboru.

 /Regex nebo/r volitelné. Používá předem definované speciální znaky v `findwhat` argumentu jako notace, které reprezentují vzory textu, nikoli literální znaky. Úplný seznam znaků regulárních výrazů naleznete v tématu [regulární výrazy](../../ide/using-regular-expressions-in-visual-studio.md).

 /Wild nebo/l volitelné. Používá předdefinované speciální znaky v `findwhat` argumentu jako notace, které reprezentují znak nebo sekvenci znaků.

 /Word nebo/w volitelné. Vyhledává pouze celá slova.

## <a name="example"></a>Příklad
 V tomto příkladu se v aktuálně vybrané části kódu provede hledání s rozlišováním velkých a malých písmen pro slovo "someString".

```
>Edit.Find somestring /sel /case
```

## <a name="see-also"></a>Viz také
 [Příkazové okno](../../ide/reference/command-window.md) [Najít/příkaz](../../ide/find-command-box.md) [aplikace Visual Studio příkazy](../../ide/reference/visual-studio-commands.md) sady Visual Studio [aliasy](../../ide/reference/visual-studio-command-aliases.md) příkazů sady Visual Studio
