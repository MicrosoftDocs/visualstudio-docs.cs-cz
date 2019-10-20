---
title: Najít v souborech – příkaz | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.findinfiles
helpviewer_keywords:
- Edit.FindInFiles command
- find in files command
ms.assetid: 2fc78bfe-b339-4599-97f9-4cafd8a194d9
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 831a67fe567c2e6ae1e288d1bc7ee91026ff2273
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651028"
---
# <a name="find-in-files-command"></a>Najít v souborech – příkaz
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vyhledejte soubory pomocí podmnožiny možností dostupných na kartě **najít v souborech** okna **Najít a nahradit** .

## <a name="syntax"></a>Syntaxe

```
Edit.FindinFiles findwhat [/case] [/ext:extensions]
[/lookin:searchpath] [/names] [/options] [/reset] [/stop] [/sub]
[/text2] [/wild|/regex] [/word]
```

## <a name="arguments"></a>Arguments
 `findwhat` nutné. Text, který se má shodovat.

## <a name="switches"></a>Přepínače
 /Case nebo/c volitelné. Shody se objeví pouze v případě, že velká a malá písmena přesně odpovídají znakům zadaným v argumentu `findwhat`.

 /EXT: `extensions` nepovinný. Určuje přípony souborů pro soubory, které mají být prohledány. Pokud není zadaný, použije se předchozí rozšíření, pokud se dřív zadal.

 /Lookin: `searchpath` nepovinný. Adresář, který chcete vyhledat. Pokud cesta obsahuje mezery, uzavřete celou cestu do uvozovek.

 /Names nebo/n volitelné. Zobrazí seznam názvů souborů, které obsahují shody.

 /Options nebo/t volitelné. Zobrazí seznam aktuálních nastavení možností hledání a neprovádí hledání.

 /Regex nebo/r volitelné. Používá předem definované speciální znaky v argumentu `findwhat` jako notace, které reprezentují vzory textu, nikoli literální znaky. Úplný seznam znaků regulárních výrazů naleznete v tématu [regulární výrazy](../../ide/using-regular-expressions-in-visual-studio.md).

 /Reset po vyčištění nebo/e volitelné. Vrátí možnosti hledání do jejich výchozího nastavení a neprovádí hledání.

 /stop nepovinný. Zastaví aktuální operaci hledání, pokud právě probíhá. Při zadání `/stop` bude hledání ignorovat všechny ostatní argumenty. Pokud například chcete zastavit aktuální hledání, zadejte následující:

```
>Edit.FindinFiles /stop
```

 /Sub nebo/s volitelné. Vyhledá podsložky v adresáři zadaném v argumentu/Lookin: `searchpath`.

 /Text2 nebo/2 volitelné. Zobrazí výsledky hledání v okně výsledky hledání 2.

 /Wild nebo/l volitelné. Používá předem definované speciální znaky v argumentu `findwhat` jako notace, které reprezentují znak nebo sekvenci znaků.

 /Word nebo/w volitelné. Vyhledává pouze celá slova.

## <a name="example"></a>Příklad
 Tento příklad vyhledá btnCancel ve všech souborech. CLS umístěných ve složce Moje projekty sady Visual Studio a v okně výsledky hledání 2 zobrazí informace o shodě.

```
>Edit.FindinFiles btnCancel /lookin:"c:/My Visual Studio Projects" /ext:*.cls /text2
```

## <a name="see-also"></a>Viz také
 Pole [najít v souborech](../../ide/find-in-files.md) – [příkaz](../../ide/reference/command-window.md) [Najít/příkazové](../../ide/find-command-box.md) okno [Visual Studio příkazy](../../ide/reference/visual-studio-commands.md) sady Visual Studio [Aliasy příkazů](../../ide/reference/visual-studio-command-aliases.md) sady Visual Studio
