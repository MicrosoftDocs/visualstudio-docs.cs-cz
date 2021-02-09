---
title: Najít v souborech – příkaz
description: Přečtěte si informace o příkazu find a o tom, jak prohledává soubory pomocí některých možností, které jsou k dispozici na kartě najít v souborech okna Najít a nahradit.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6fc824a7166e3bbaba84bd49e89f1fdf30b65761
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908960"
---
# <a name="find-in-files-command"></a>Najít v souborech – příkaz
Vyhledejte soubory pomocí podmnožiny možností dostupných na kartě **najít v souborech** okna **Najít a nahradit** .

## <a name="syntax"></a>Syntaxe

```cmd
Edit.FindinFiles findwhat [/case] [/ext:extensions]
[/lookin:searchpath] [/names] [/options] [/reset] [/stop] [/sub]
[/text2] [/wild|/regex] [/word]
```

## <a name="arguments"></a>Argumenty

`findwhat`\
Povinná hodnota. Text, který se má shodovat.

## <a name="switches"></a>přepínače,
/Case nebo/c\
Nepovinný parametr. Shody se objeví pouze v případě, že velká a malá písmena přesně odpovídají znakům zadaným v `findwhat` argumentu.

rozšířeného `extensions`\
Nepovinný parametr. Určuje přípony souborů pro soubory, které mají být prohledány. Pokud není zadaný, použije se předchozí rozšíření, pokud se dřív zadal.

oblasthledání `searchpath`\
Nepovinný parametr. Adresář, který chcete vyhledat. Pokud cesta obsahuje mezery, uzavřete celou cestu do uvozovek.

/Names nebo/n\
Nepovinný parametr. Zobrazí seznam názvů souborů, které obsahují shody.

/Options nebo/T\
Nepovinný parametr. Zobrazí seznam aktuálních nastavení možností hledání a neprovádí hledání.

/Regex nebo/r\
Nepovinný parametr. Používá předem definované speciální znaky v `findwhat` argumentu jako notace, které reprezentují vzory textu, nikoli literální znaky. Úplný seznam znaků regulárních výrazů naleznete v tématu [regulární výrazy](../../ide/using-regular-expressions-in-visual-studio.md).

/Reset po vyčištění nebo/e\
Nepovinný parametr. Vrátí možnosti hledání do jejich výchozího nastavení a neprovádí hledání.

/stop
Nepovinný parametr. Zastaví aktuální operaci hledání, pokud právě probíhá. Při hledání se ignorují všechny ostatní argumenty `/stop` , pokud je zadaný. Pokud například chcete zastavit aktuální hledání, zadejte následující:

```cmd
>Edit.FindinFiles /stop
```

/Sub nebo/s\
Nepovinný parametr. Vyhledá podsložky v adresáři zadaném v argumentu/Lookin: `searchpath` .

/Text2 nebo/2 \
Nepovinný parametr. Zobrazí výsledky hledání v okně výsledky hledání 2.

/Wild nebo/l\
Nepovinný parametr. Používá předdefinované speciální znaky v `findwhat` argumentu jako notace, které reprezentují znak nebo sekvenci znaků.

/Word nebo/W\
Nepovinný parametr. Vyhledává pouze celá slova.

## <a name="example"></a>Příklad
Tento příklad vyhledá btnCancel ve všech souborech. CLS umístěných ve složce Moje projekty sady Visual Studio a v okně výsledky hledání 2 zobrazí informace o shodě.

```cmd
>Edit.FindinFiles btnCancel /lookin:"c:/My Visual Studio Projects" /ext:*.cls /text2
```

## <a name="see-also"></a>Viz také

- [Najít v souborech](../../ide/find-in-files.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Pole Najít/příkaz](../../ide/find-command-box.md)
- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
