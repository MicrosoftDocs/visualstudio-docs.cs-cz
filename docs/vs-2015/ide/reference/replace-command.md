---
title: Nahradit příkaz | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.replace
helpviewer_keywords:
- Edit.Replace command
- Replace command
ms.assetid: a15767f1-5a3d-44f5-8c77-7b0f1157f340
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7ba633999925e86b753dbd815babe6e52c75ca53
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665619"
---
# <a name="replace-command"></a>Nahradit – příkaz
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Nahradí text v souborech pomocí podmnožiny možností, které jsou k dispozici na kartě **nahradit v souborech** okna **Najít a nahradit** .

## <a name="syntax"></a>Syntaxe

```
Edit.Replace findwhat replacewith [/all] [/case]
[/doc|/proc|/open|/sel] [/hidden] [/options] [/reset] [/up]
[/wild|/regex] [/word]
```

## <a name="arguments"></a>Arguments
 `findwhat` nutné. Text, který se má shodovat.

 `replacewith` nutné. Text, který má být nahrazen odpovídajícím textem

## <a name="switches"></a>Přepínače
 /All nebo/a volitelné. Nahradí všechny výskyty hledaného textu náhradním textem.

 /Case nebo/c volitelné. Shody se objeví pouze v případě, že se velká a malá písmena přesně shodují s hodnotami zadanými v argumentu `findwhat`.

 /doc nebo/d volitelné. Vyhledá pouze aktuální dokument. Zadejte pouze jeden z dostupných oborů hledání, `/doc`, `/proc`, `/open` nebo `/sel`.

 /Hidden nebo/h Volitelné. Vyhledává skrytý a sbalený text, například metadata ovládacího prvku v době návrhu, skryté oblasti naznačeného dokumentu nebo sbalené třídy nebo metody.

 /Open nebo/o volitelné. Vyhledá všechny otevřené dokumenty, jako by se jednalo o jeden dokument. Zadejte pouze jeden z dostupných oborů hledání, `/doc`, `/proc`, `/open` nebo `/sel`.

 /Options nebo/t volitelné. Zobrazí seznam aktuálních nastavení možností hledání a neprovádí hledání.

 /Proc nebo/p volitelné. Vyhledá pouze aktuální proceduru. Zadejte pouze jeden z dostupných oborů hledání, `/doc`, `/proc`, `/open` nebo `/sel`.

 /Regex nebo/r volitelné. Používá předem definované speciální znaky v argumentu `findwhat` jako notace, které reprezentují vzory textu, nikoli literální znaky. Úplný seznam znaků regulárních výrazů naleznete v tématu [regulární výrazy](../../ide/using-regular-expressions-in-visual-studio.md).

 /Reset po vyčištění nebo/e volitelné. Vrátí možnosti hledání do jejich výchozího nastavení a neprovádí hledání.

 /SEL nebo/s volitelné. Vyhledá pouze aktuální výběr. Zadejte pouze jeden z dostupných oborů hledání, `/doc`, `/proc`, `/open` nebo `/sel`.

 /up nebo/u je nepovinný. Vyhledá z aktuálního umístění v souboru směrem k hornímu okraji souboru. Ve výchozím nastavení vyhledávání začíná na aktuálním umístění v souboru a předá směrem k dolnímu okraji souboru.

 /Wild nebo/l volitelné. Používá předem definované speciální znaky v argumentu `findwhat` jako notace, které reprezentují znak nebo sekvenci znaků.

 /Word nebo/w volitelné. Vyhledává pouze celá slova.

## <a name="example"></a>Příklad
 Tento příklad nahrazuje `btnSend` `btnSubmit` ve všech otevřených dokumentech.

```
>Edit.Replace btnSend btnSubmit /open
```

## <a name="see-also"></a>Viz také
 [Hledání a nahrazování textového](../../ide/finding-and-replacing-text.md) [okna příkazového řádku](../../ide/reference/command-window.md) [Najít/příkaz](../../ide/find-command-box.md) [Visual Studio příkazy](../../ide/reference/visual-studio-commands.md) sady Visual Studio [Aliasy příkazů](../../ide/reference/visual-studio-command-aliases.md) sady Visual Studio
