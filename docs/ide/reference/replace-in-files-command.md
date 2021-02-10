---
title: Nahradit v souborech – příkaz
description: Přečtěte si o příkazu nahradit v souborech a o tom, jak nahrazuje text v souborech pomocí některé z možností, které jsou k dispozici na kartě nahradit v souborech okna Najít a nahradit.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 32980161281cf36c54ad15d536870a96694a461a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99958008"
---
# <a name="replace-in-files-command"></a>Nahradit v souborech – příkaz
Nahradí text v souborech pomocí podmnožiny možností, které jsou k dispozici na kartě **nahradit v souborech** okna **Najít a nahradit** .

## <a name="syntax"></a>Syntaxe

```
Edit.ReplaceinFiles findwhat replacewith [/all] [/case]
[/ext:extensions] [/keep] [/lookin:searchpath] [/options] [/regex]
[/reset] [/stop] [/sub] [/text2] [/wild] [/word]
```

## <a name="arguments"></a>Argumenty
`findwhat`

Povinná hodnota. Text, který se má shodovat.

`replacewith`

Povinná hodnota. Text, který má být nahrazen odpovídajícím textem

## <a name="switches"></a>přepínače,
/All nebo/a

Nepovinný parametr. Nahradí všechny výskyty hledaného textu náhradním textem.

/Case nebo/c

Nepovinný parametr. Shody se objeví pouze v případě, že se velká a malá písmena přesně shodují s hodnotami zadanými v `findwhat` argumentu.

rozšířeného `extensions`

Nepovinný parametr. Určuje přípony souborů pro soubory, které mají být prohledány.

/Keep nebo/k

Nepovinný parametr. Určuje, že všechny změněné soubory zůstanou otevřené.

oblasthledání `searchpath`

Nepovinný parametr. Adresář, který chcete vyhledat. Pokud cesta obsahuje mezery, uzavřete celou cestu do uvozovek.

/Options nebo/t

Nepovinný parametr. Zobrazí seznam aktuálních nastavení možností hledání a neprovádí hledání.

/Regex nebo/r

Nepovinný parametr. Používá předem definované speciální znaky v `findwhat` argumentu jako notace, které reprezentují vzory textu, nikoli literální znaky. Úplný seznam znaků regulárních výrazů naleznete v tématu [regulární výrazy](../../ide/using-regular-expressions-in-visual-studio.md).

/Reset po vyčištění nebo/e

Nepovinný parametr. Vrátí možnosti hledání do jejich výchozího nastavení a neprovádí hledání.

/stop

Nepovinný parametr. Zastaví aktuální operaci hledání, pokud právě probíhá. Při nahrazení se ignoruje všechny ostatní argumenty `/stop` , pokud je zadaný. Pokud například chcete zastavit aktuální nahrazení, zadejte následující:

```
>Edit.ReplaceinFiles /stop
```

/Sub nebo/s

Nepovinný parametr. Vyhledá podsložky v adresáři zadaném v argumentu/Lookin: `searchpath` .

/Text2 nebo/2

Nepovinný parametr. Zobrazí výsledky náhrady v okně **výsledky hledání 2** .

/Wild nebo/l

Nepovinný parametr. Používá předdefinované speciální znaky v `findwhat` argumentu jako notace, které reprezentují znak nebo sekvenci znaků.

/Word nebo/w

Nepovinný parametr. Vyhledá pouze celá slova.

## <a name="example"></a>Příklad
Tento příklad vyhledá `btnCancel` a nahradí ho `btnReset` ve všech souborech. CLS umístěných ve složce Moje projekty sady Visual Studio a zobrazí informace o nahrazení v okně **výsledky hledání 2** .

```
>Edit.ReplaceinFiles btnCancel btnReset /lookin:"c:/my visual studio projects" /ext:.cls /text2
```

## <a name="see-also"></a>Viz také

- [Hledání a nahrazení textu](../../ide/finding-and-replacing-text.md)
- [Nahradit v souborech](../../ide/replace-in-files.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Pole Najít/příkaz](../../ide/find-command-box.md)
- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
