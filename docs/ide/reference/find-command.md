---
title: Najít – příkaz
description: Přečtěte si o příkazu find a o tom, jak prohledává soubory pomocí podmnožiny možností dostupných na kartě najít v souborech okna Najít a nahradit.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- edit.find
helpviewer_keywords:
- Find command
- Edit.Find command
ms.assetid: f0c705dc-2b97-423d-abbf-5584d4827208
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e28062f54426e2810acf29bdd64955998ea088cd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852541"
---
# <a name="find-command"></a>Najít – příkaz
Vyhledá soubory pomocí podmnožiny možností dostupných na kartě **najít v souborech** okna **Najít a nahradit** .

## <a name="syntax"></a>Syntaxe

```cmd
Edit.Find findwhat [/case] [/doc | /proc | /open | /sel]
[/markall] [/options] [/reset] [/up] [/wild | /regex] [/word]
```

## <a name="arguments"></a>Argumenty
`findwhat` Požadovanou. Text, který se má shodovat.

## <a name="switches"></a>přepínače,
/Case nebo/c\
Nepovinný parametr. Shody se objeví pouze v případě, že velká a malá písmena přesně odpovídají znakům zadaným v `findwhat` argumentu.

/doc nebo/D\
Nepovinný parametr. Vyhledá pouze aktuální dokument. Zadejte pouze jeden z dostupných oborů hledání,, `/doc` , `/proc` `/open` nebo `/sel` .

/markall nebo/m\
Nepovinný parametr. Umístí grafiku na každý řádek, který obsahuje shodu hledání v rámci aktuálního dokumentu.

/Open nebo/o\
Nepovinný parametr. Vyhledá všechny otevřené dokumenty, jako by se jednalo o jeden dokument. Zadejte pouze jeden z dostupných oborů hledání,, `/doc` , `/proc` `/open` nebo `/sel` .

/Options nebo/T\
Nepovinný parametr. Zobrazí seznam aktuálních nastavení možností hledání a neprovádí hledání.

/Proc nebo/p\
Nepovinný parametr. Vyhledá pouze aktuální proceduru. Zadejte pouze jeden z dostupných oborů hledání,, `/doc` , `/proc` `/open` nebo `/sel` .

/Reset po vyčištění nebo/e\
Nepovinný parametr. Vrátí možnosti hledání do jejich výchozího nastavení a neprovádí hledání.

/SEL nebo/s\
Nepovinný parametr. Vyhledá pouze aktuální výběr. Zadejte pouze jeden z dostupných oborů hledání,, `/doc` , `/proc` `/open` nebo `/sel` .

/up nebo/u\
Nepovinný parametr. Vyhledá z aktuálního umístění v souboru směrem k začátku souboru. Ve výchozím nastavení vyhledávání začíná na aktuálním umístění v souboru a hledá na konci souboru.

/Regex nebo/r\
Nepovinný parametr. Používá předem definované speciální znaky v `findwhat` argumentu jako notace, které reprezentují vzory textu, nikoli literální znaky. Úplný seznam znaků regulárních výrazů naleznete v tématu [regulární výrazy](../../ide/using-regular-expressions-in-visual-studio.md).

/Wild nebo/l\
Nepovinný parametr. Používá předdefinované speciální znaky v `findwhat` argumentu jako notace, které reprezentují znak nebo sekvenci znaků.

/Word nebo/W\
Nepovinný parametr. Vyhledává pouze celá slova.

## <a name="example"></a>Příklad
V tomto příkladu se v aktuálně vybrané části kódu provede hledání s rozlišováním velkých a malých písmen pro slovo "someString".

```cmd
>Edit.Find somestring /sel /case
```

## <a name="see-also"></a>Viz také

- [Příkazové okno](../../ide/reference/command-window.md)
- [Pole Najít/příkaz](../../ide/find-command-box.md)
- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
