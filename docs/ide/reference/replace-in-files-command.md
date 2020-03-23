---
title: Nahradit v souborech – příkaz
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- edit.replaceinfiles
helpviewer_keywords:
- Edit.ReplaceInFiles command
- Replace In Files command
- ReplaceInFiles command
ms.assetid: f116066a-4f65-4f2c-94ef-12cbd8cfb598
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 96f7d7ae0ea5eaf0de1a6fa4357e2750cdd8c22e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565471"
---
# <a name="replace-in-files-command"></a>Nahradit v souborech – příkaz
Nahradí text v souborech pomocí podmnožiny voleb dostupných na kartě **Nahradit v souborech** v okně **Najít a nahradit.**

## <a name="syntax"></a>Syntaxe

```
Edit.ReplaceinFiles findwhat replacewith [/all] [/case]
[/ext:extensions] [/keep] [/lookin:searchpath] [/options] [/regex]
[/reset] [/stop] [/sub] [/text2] [/wild] [/word]
```

## <a name="arguments"></a>Argumenty
`findwhat`

Povinná hodnota. Text, který má odpovídat.

`replacewith`

Povinná hodnota. Text, který má nahradit odpovídající text.

## <a name="switches"></a>Přepínače
/všechny nebo /a

Nepovinný parametr. Nahradí všechny výskyty hledaného textu náhradním textem.

/case nebo /c

Nepovinný parametr. Shody dojít pouze v případě, že velká a `findwhat` malá písmena přesně odpovídají těm, které jsou zadány v argumentu.

/ext:`extensions`

Nepovinný parametr. Určuje přípony souborů pro prohledávané soubory.

/keep nebo /k

Nepovinný parametr. Určuje, že všechny upravené soubory zůstanou otevřené.

/lookin:`searchpath`

Nepovinný parametr. Adresář k vyhledávání. Pokud cesta obsahuje mezery, uzavřete celou cestu do uvozovek.

/options nebo /t

Nepovinný parametr. Zobrazí seznam aktuálního nastavení možností hledání a neprovede vyhledávání.

/regulární výraz nebo /r

Nepovinný parametr. Používá předdefinované speciální znaky `findwhat` v argumentu jako zápisy, které představují vzorky textu spíše než literál znaky. Úplný seznam znaků regulárních výrazů naleznete [v tématu Regulární výrazy](../../ide/using-regular-expressions-in-visual-studio.md).

/reset nebo /e

Nepovinný parametr. Vrátí možnosti hledání do výchozího nastavení a neprovede hledání.

/stop

Nepovinný parametr. Zastaví aktuální operaci hledání, pokud probíhá. Nahradit ignoruje všechny ostatní `/stop` argumenty, pokud byla zadána. Chcete-li například zastavit aktuální náhradu, zadejte následující:

```
>Edit.ReplaceinFiles /stop
```

/sub nebo /s

Nepovinný parametr. Prohledá podsložky v adresáři určeném`searchpath` v argumentu /lookin: .

/text2 nebo /2

Nepovinný parametr. Zobrazí výsledky nahrazení v okně **Najít výsledky 2.**

/wild nebo /l

Nepovinný parametr. Používá předdefinované speciální znaky `findwhat` v argumentu jako zápisy představující znak nebo posloupnost znaků.

/slovo nebo /w

Nepovinný parametr. Vyhledá pouze celá slova.

## <a name="example"></a>Příklad
Tento příklad vyhledá `btnCancel` a nahradí `btnReset` jej ve všech souborech CLS umístěných ve složce "moje projekty visual studio" a zobrazí náhradní informace v okně **Najít výsledky 2.**

```
>Edit.ReplaceinFiles btnCancel btnReset /lookin:"c:/my visual studio projects" /ext:.cls /text2
```

## <a name="see-also"></a>Viz také

- [Hledání a nahrazení textu](../../ide/finding-and-replacing-text.md)
- [Nahradit v souborech](../../ide/replace-in-files.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Najít/Příkazové pole](../../ide/find-command-box.md)
- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
