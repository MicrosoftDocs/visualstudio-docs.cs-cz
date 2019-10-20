---
title: Nahradit v souborech – příkaz | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.replaceinfiles
helpviewer_keywords:
- Edit.ReplaceInFiles command
- Replace In Files command
- ReplaceInFiles command
ms.assetid: f116066a-4f65-4f2c-94ef-12cbd8cfb598
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3d5088366548c9f92d04f1b65a3afc378db29d6a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665609"
---
# <a name="replace-in-files-command"></a>Nahradit v souborech – příkaz
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Nahradí text v souborech pomocí podmnožiny možností, které jsou k dispozici na kartě **nahradit v souborech** okna **Najít a nahradit** .

## <a name="syntax"></a>Syntaxe

```
Edit.ReplaceinFiles findwhat replacewith [/all] [/case]
[/ext:extensions] [/keep] [/lookin:searchpath] [/options] [/regex]
[/reset] [/stop] [/sub] [/text2] [/wild] [/word]
```

## <a name="arguments"></a>Arguments
 `findwhat` nutné. Text, který se má shodovat.

 `replacewith` nutné. Text, který má být nahrazen odpovídajícím textem

## <a name="switches"></a>Přepínače
 /All nebo/a volitelné. Nahradí všechny výskyty hledaného textu náhradním textem.

 /Case nebo/c volitelné. Shody se objeví pouze v případě, že se velká a malá písmena přesně shodují s hodnotami zadanými v argumentu `findwhat`.

 /EXT: `extensions` nepovinný. Určuje přípony souborů pro soubory, které mají být prohledány.

 /Keep nebo/k volitelné. Určuje, že všechny změněné soubory zůstanou otevřené.

 /Lookin: `searchpath` nepovinný. Adresář, který chcete vyhledat. Pokud cesta obsahuje mezery, uzavřete celou cestu do uvozovek.

 /Options nebo/t volitelné. Zobrazí seznam aktuálních nastavení možností hledání a neprovádí hledání.

 /Regex nebo/r volitelné. Používá předem definované speciální znaky v argumentu `findwhat` jako notace, které reprezentují vzory textu, nikoli literální znaky. Úplný seznam znaků regulárních výrazů naleznete v tématu [regulární výrazy](../../ide/using-regular-expressions-in-visual-studio.md).

 /Reset po vyčištění nebo/e volitelné. Vrátí možnosti hledání do jejich výchozího nastavení a neprovádí hledání.

 /stop nepovinný. Zastaví aktuální operaci hledání, pokud právě probíhá. Při zadání `/stop` parametr nahradit ignoruje všechny ostatní argumenty. Pokud například chcete zastavit aktuální nahrazení, zadejte následující:

```
>Edit.ReplaceinFiles /stop
```

 /Sub nebo/s volitelné. Vyhledá podsložky v adresáři zadaném v argumentu/Lookin: `searchpath`.

 /Text2 nebo/2 volitelné. Zobrazí výsledky náhrady v okně **výsledky hledání 2** .

 /Wild nebo/l volitelné. Používá předem definované speciální znaky v argumentu `findwhat` jako notace, které reprezentují znak nebo sekvenci znaků.

 /Word nebo/w volitelné. Vyhledá pouze celá slova.

## <a name="example"></a>Příklad
 Tento příklad vyhledá `btnCancel` a nahradí jej `btnReset` ve všech souborech. CLS umístěných ve složce "Moje projekty sady Visual Studio" a zobrazí informace o nahrazení v okně **výsledky hledání 2** .

```
>Edit.ReplaceinFiles btnCancel btnReset /lookin:"c:/my visual studio projects" /ext:.cls /text2
```

## <a name="see-also"></a>Viz také
 [Hledání a nahrazování textu](../../ide/finding-and-replacing-text.md) [nahrazení v](../../ide/replace-in-files.md) [okně](../../ide/reference/command-window.md) soubory – [pole Najít/příkaz](../../ide/find-command-box.md) [Visual Studio příkazy](../../ide/reference/visual-studio-commands.md) sady Visual [Studio aliasy příkazů](../../ide/reference/visual-studio-command-aliases.md) sady Visual Studio
