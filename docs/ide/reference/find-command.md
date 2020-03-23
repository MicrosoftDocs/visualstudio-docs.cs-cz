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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 288fb294ab712713d6be116f46ca159ea40a6e67
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595641"
---
# <a name="find-command"></a>Najít – příkaz
Prohledává soubory pomocí podmnožiny možností dostupných na kartě **Najít v souborech** v okně **Najít a nahradit.**

## <a name="syntax"></a>Syntaxe

```cmd
Edit.Find findwhat [/case] [/doc | /proc | /open | /sel]
[/markall] [/options] [/reset] [/up] [/wild | /regex] [/word]
```

## <a name="arguments"></a>Argumenty
`findwhat`Požadované. Text, který má odpovídat.

## <a name="switches"></a>Přepínače
/case nebo /c\
Nepovinný parametr. Shody dojít pouze v případě, že velká a `findwhat` malá písmena přesně odpovídají těm, které jsou zadány v argumentu.

/doc nebo /d\
Nepovinný parametr. Prohledá pouze aktuální dokument. Zadejte pouze jeden z dostupných `/proc` `/open`oborů `/sel`hledání , `/doc`, , nebo .

/markall nebo /m\
Nepovinný parametr. Umístí grafiku na každý řádek, který obsahuje shodu hledání v aktuálním dokumentu.

/open nebo /o\
Nepovinný parametr. Prohledává všechny otevřené dokumenty, jako by se jednalo o jeden dokument. Zadejte pouze jeden z dostupných `/proc` `/open`oborů `/sel`hledání , `/doc`, , nebo .

/options nebo /t\
Nepovinný parametr. Zobrazí seznam aktuálního nastavení možností hledání a neprovede vyhledávání.

/proc nebo /p\
Nepovinný parametr. Prohledá pouze aktuální postup. Zadejte pouze jeden z dostupných `/proc` `/open`oborů `/sel`hledání , `/doc`, , nebo .

/reset nebo /e\
Nepovinný parametr. Vrátí možnosti hledání do výchozího nastavení a neprovede hledání.

/sel nebo /s\
Nepovinný parametr. Prohledá pouze aktuální výběr. Zadejte pouze jeden z dostupných `/proc` `/open`oborů `/sel`hledání , `/doc`, , nebo .

/nahoru nebo /u\
Nepovinný parametr. Prohledá z aktuálního umístění v souboru směrem k začátku souboru. Ve výchozím nastavení hledání začíná v aktuálním umístění v souboru a hledání ke konci souboru.

/regex nebo /r\
Nepovinný parametr. Používá předdefinované speciální znaky `findwhat` v argumentu jako zápisy, které představují vzorky textu spíše než literál znaky. Úplný seznam znaků regulárních výrazů naleznete [v tématu Regulární výrazy](../../ide/using-regular-expressions-in-visual-studio.md).

/wild nebo /l\
Nepovinný parametr. Používá předdefinované speciální znaky `findwhat` v argumentu jako zápisy představující znak nebo posloupnost znaků.

/word nebo /w\
Nepovinný parametr. Vyhledá pouze celá slova.

## <a name="example"></a>Příklad
Tento příklad provádí hledání rozlišování velkých a malých písmen pro slovo "somestring" v aktuálně vybrané části kódu.

```cmd
>Edit.Find somestring /sel /case
```

## <a name="see-also"></a>Viz také

- [Příkazové okno](../../ide/reference/command-window.md)
- [Najít/Příkazové pole](../../ide/find-command-box.md)
- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
