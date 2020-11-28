---
title: Nahradit – příkaz
description: Přečtěte si o příkazu Replace a o tom, jak nahrazuje text v souborech pomocí podmnožiny možností, které jsou k dispozici na kartě nahradit v souborech okna Najít a nahradit.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- edit.replace
helpviewer_keywords:
- Edit.Replace command
- Replace command
ms.assetid: a15767f1-5a3d-44f5-8c77-7b0f1157f340
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2db7b59c1982f706cc6d2b18039870871ffa1039
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304041"
---
# <a name="replace-command"></a>Nahradit – příkaz
Nahradí text v souborech pomocí podmnožiny možností, které jsou k dispozici na kartě **nahradit v souborech** okna **Najít a nahradit** .

## <a name="syntax"></a>Syntaxe

```
Edit.Replace findwhat replacewith [/all] [/case]
[/doc|/proc|/open|/sel] [/hidden] [/options] [/reset] [/up]
[/wild|/regex] [/word]
```

## <a name="arguments"></a>Argumenty
`findwhat`

Povinná hodnota. Text, který se má shodovat.

`replacewith`

Povinná hodnota. Text, který má být nahrazen odpovídajícím textem

## <a name="switches"></a>Přepínače
/All nebo/a

Nepovinný parametr. Nahradí všechny výskyty hledaného textu náhradním textem.

/Case nebo/c

Nepovinný parametr. Shody se objeví pouze v případě, že se velká a malá písmena přesně shodují s hodnotami zadanými v `findwhat` argumentu.

/doc nebo/d

Nepovinný parametr. Vyhledá pouze aktuální dokument. Zadejte pouze jeden z dostupných oborů hledání,, `/doc` , `/proc` `/open` nebo `/sel` .

/Hidden nebo/h

Nepovinný parametr. Vyhledává skrytý a sbalený text, například metadata ovládacího prvku v době návrhu, skryté oblasti naznačeného dokumentu nebo sbalené třídy nebo metody.

/Open nebo/o

Nepovinný parametr. Vyhledá všechny otevřené dokumenty, jako by se jednalo o jeden dokument. Zadejte pouze jeden z dostupných oborů hledání,, `/doc` , `/proc` `/open` nebo `/sel` .

/Options nebo/t

Nepovinný parametr. Zobrazí seznam aktuálních nastavení možností hledání a neprovádí hledání.

/Proc nebo/p

Nepovinný parametr. Vyhledá pouze aktuální proceduru. Zadejte pouze jeden z dostupných oborů hledání,, `/doc` , `/proc` `/open` nebo `/sel` .

/Regex nebo/r

Nepovinný parametr. Používá předem definované speciální znaky v `findwhat` argumentu jako notace, které reprezentují vzory textu, nikoli literální znaky. Úplný seznam znaků regulárních výrazů naleznete v tématu [regulární výrazy](../../ide/using-regular-expressions-in-visual-studio.md).

/Reset po vyčištění nebo/e

Nepovinný parametr. Vrátí možnosti hledání do jejich výchozího nastavení a neprovádí hledání.

/SEL nebo/s

Nepovinný parametr. Vyhledá pouze aktuální výběr. Zadejte pouze jeden z dostupných oborů hledání,, `/doc` , `/proc` `/open` nebo `/sel` .

/up nebo/u

Nepovinný parametr. Vyhledá z aktuálního umístění v souboru směrem k hornímu okraji souboru. Ve výchozím nastavení vyhledávání začíná na aktuálním umístění v souboru a předá směrem k dolnímu okraji souboru.

/Wild nebo/l

Nepovinný parametr. Používá předdefinované speciální znaky v `findwhat` argumentu jako notace, které reprezentují znak nebo sekvenci znaků.

/Word nebo/w

Nepovinný parametr. Vyhledává pouze celá slova.

## <a name="example"></a>Příklad
Tento příklad nahrazuje `btnSend` `btnSubmit` ve všech otevřených dokumentech.

```
>Edit.Replace btnSend btnSubmit /open
```

## <a name="see-also"></a>Viz také

- [Hledání a nahrazení textu](../../ide/finding-and-replacing-text.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Pole Najít/příkaz](../../ide/find-command-box.md)
- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
