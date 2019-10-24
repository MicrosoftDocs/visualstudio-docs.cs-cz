---
title: Najít – příkaz
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- edit.find
helpviewer_keywords:
- Find command
- Edit.Find command
ms.assetid: f0c705dc-2b97-423d-abbf-5584d4827208
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9ab914d62053b5cbefe92ee0ce8356c10dad82e6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748762"
---
# <a name="find-command"></a>Najít – příkaz
Vyhledá soubory pomocí podmnožiny možností dostupných na kartě **najít v souborech** okna **Najít a nahradit** .

## <a name="syntax"></a>Syntaxe

```cmd
Edit.Find findwhat [/case] [/doc | /proc | /open | /sel]
[/markall] [/options] [/reset] [/up] [/wild | /regex] [/word]
```

## <a name="arguments"></a>Arguments
`findwhat` nutné. Text, který se má shodovat.

## <a name="switches"></a>Přepínače
/Case nebo/c\
Volitelné. Shody se objeví pouze v případě, že velká a malá písmena přesně odpovídají znakům zadaným v argumentu `findwhat`.

/doc nebo/D\
Volitelné. Vyhledá pouze aktuální dokument. Zadejte pouze jeden z dostupných oborů hledání, `/doc`, `/proc`, `/open` nebo `/sel`.

/markall nebo/m\
Volitelné. Umístí grafiku na každý řádek, který obsahuje shodu hledání v rámci aktuálního dokumentu.

/Open nebo/o\
Volitelné. Vyhledá všechny otevřené dokumenty, jako by se jednalo o jeden dokument. Zadejte pouze jeden z dostupných oborů hledání, `/doc`, `/proc`, `/open` nebo `/sel`.

/Options nebo/T\
Volitelné. Zobrazí seznam aktuálních nastavení možností hledání a neprovádí hledání.

/Proc nebo/p\
Volitelné. Vyhledá pouze aktuální proceduru. Zadejte pouze jeden z dostupných oborů hledání, `/doc`, `/proc`, `/open` nebo `/sel`.

/Reset po vyčištění nebo/e\
Volitelné. Vrátí možnosti hledání do jejich výchozího nastavení a neprovádí hledání.

/SEL nebo/s\
Volitelné. Vyhledá pouze aktuální výběr. Zadejte pouze jeden z dostupných oborů hledání, `/doc`, `/proc`, `/open` nebo `/sel`.

/up nebo/u\
Volitelné. Vyhledá z aktuálního umístění v souboru směrem k začátku souboru. Ve výchozím nastavení vyhledávání začíná na aktuálním umístění v souboru a hledá na konci souboru.

/Regex nebo/r\
Volitelné. Používá předem definované speciální znaky v argumentu `findwhat` jako notace, které reprezentují vzory textu, nikoli literální znaky. Úplný seznam znaků regulárních výrazů naleznete v tématu [regulární výrazy](../../ide/using-regular-expressions-in-visual-studio.md).

/Wild nebo/l\
Volitelné. Používá předem definované speciální znaky v argumentu `findwhat` jako notace, které reprezentují znak nebo sekvenci znaků.

/Word nebo/W\
Volitelné. Vyhledává pouze celá slova.

## <a name="example"></a>Příklad
V tomto příkladu se v aktuálně vybrané části kódu provede hledání s rozlišováním velkých a malých písmen pro slovo "someString".

```cmd
>Edit.Find somestring /sel /case
```

## <a name="see-also"></a>Viz také:

- [Příkazové okno](../../ide/reference/command-window.md)
- [Pole Najít/příkaz](../../ide/find-command-box.md)
- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)