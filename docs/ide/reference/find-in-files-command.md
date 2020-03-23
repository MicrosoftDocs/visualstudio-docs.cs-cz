---
title: Najít v souborech – příkaz
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- edit.findinfiles
helpviewer_keywords:
- Edit.FindInFiles command
- find in files command
ms.assetid: 2fc78bfe-b339-4599-97f9-4cafd8a194d9
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 87d313c29be1d5fb4f1be1febe9b5b7cd32e7e11
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75569579"
---
# <a name="find-in-files-command"></a>Najít v souborech – příkaz
Prohledávejte soubory pomocí podmnožiny možností dostupných na kartě **Najít v souborech** v okně **Najít a nahradit.**

## <a name="syntax"></a>Syntaxe

```cmd
Edit.FindinFiles findwhat [/case] [/ext:extensions]
[/lookin:searchpath] [/names] [/options] [/reset] [/stop] [/sub]
[/text2] [/wild|/regex] [/word]
```

## <a name="arguments"></a>Argumenty

`findwhat`\
Povinná hodnota. Text, který má odpovídat.

## <a name="switches"></a>Přepínače
/case nebo /c\
Nepovinný parametr. Shody dojít pouze v případě, že velká a `findwhat` malá písmena přesně odpovídají těm, které jsou zadány v argumentu.

/ext:`extensions`\
Nepovinný parametr. Určuje přípony souborů pro prohledávané soubory. Pokud není zadán, předchozí rozšíření se používá, pokud byl dříve zadán.

/lookin:`searchpath`\
Nepovinný parametr. Adresář k vyhledávání. Pokud cesta obsahuje mezery, uzavřete celou cestu do uvozovek.

/names or /n\
Nepovinný parametr. Zobrazí seznam názvů souborů, které obsahují shody.

/options nebo /t\
Nepovinný parametr. Zobrazí seznam aktuálního nastavení možností hledání a neprovede vyhledávání.

/regex nebo /r\
Nepovinný parametr. Používá předdefinované speciální znaky `findwhat` v argumentu jako zápisy, které představují vzorky textu spíše než literál znaky. Úplný seznam znaků regulárních výrazů naleznete [v tématu Regulární výrazy](../../ide/using-regular-expressions-in-visual-studio.md).

/reset nebo /e\
Nepovinný parametr. Vrátí možnosti hledání do výchozího nastavení a neprovede hledání.

/stop\
Nepovinný parametr. Zastaví aktuální operaci hledání, pokud probíhá. Hledání ignoruje všechny ostatní `/stop` argumenty, pokud byla zadána. Chcete-li například zastavit aktuální hledání, zadejte následující:

```cmd
>Edit.FindinFiles /stop
```

/sub nebo /s\
Nepovinný parametr. Prohledá podsložky v adresáři určeném`searchpath` v argumentu /lookin: .

/text2 nebo /2\
Nepovinný parametr. Zobrazí výsledky hledání v okně Najít výsledky 2.

/wild nebo /l\
Nepovinný parametr. Používá předdefinované speciální znaky `findwhat` v argumentu jako zápisy představující znak nebo posloupnost znaků.

/word nebo /w\
Nepovinný parametr. Vyhledá pouze celá slova.

## <a name="example"></a>Příklad
Tento příklad vyhledá btnCancel ve všech souborech CLS umístěných ve složce "Moje projekty sady Visual Studio" a zobrazí informace o shodě v okně Najít výsledky 2.

```cmd
>Edit.FindinFiles btnCancel /lookin:"c:/My Visual Studio Projects" /ext:*.cls /text2
```

## <a name="see-also"></a>Viz také

- [Najít v souborech](../../ide/find-in-files.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Najít/Příkazové pole](../../ide/find-command-box.md)
- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
