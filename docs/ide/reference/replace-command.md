---
title: Nahradit – příkaz
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
ms.openlocfilehash: 620e55938a9c96393d8cd7de6f238d3f98715d29
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596681"
---
# <a name="replace-command"></a>Nahradit – příkaz
Nahradí text v souborech pomocí podmnožiny voleb dostupných na kartě **Nahradit v souborech** v okně **Najít a nahradit.**

## <a name="syntax"></a>Syntaxe

```
Edit.Replace findwhat replacewith [/all] [/case]
[/doc|/proc|/open|/sel] [/hidden] [/options] [/reset] [/up]
[/wild|/regex] [/word]
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

/doc nebo /d

Nepovinný parametr. Prohledá pouze aktuální dokument. Zadejte pouze jeden z dostupných `/proc` `/open`oborů `/sel`hledání , `/doc`, , nebo .

/hidden nebo /h

Nepovinný parametr. Prohledá skrytý a sbalený text, například metadata ovládacího prvku v době návrhu, skrytou oblast obrysového dokumentu nebo sbalenou třídu nebo metodu.

/open nebo /o

Nepovinný parametr. Prohledává všechny otevřené dokumenty, jako by se jednalo o jeden dokument. Zadejte pouze jeden z dostupných `/proc` `/open`oborů `/sel`hledání , `/doc`, , nebo .

/options nebo /t

Nepovinný parametr. Zobrazí seznam aktuálního nastavení možností hledání a neprovede vyhledávání.

/proc nebo /p

Nepovinný parametr. Prohledá pouze aktuální postup. Zadejte pouze jeden z dostupných `/proc` `/open`oborů `/sel`hledání , `/doc`, , nebo .

/regulární výraz nebo /r

Nepovinný parametr. Používá předdefinované speciální znaky `findwhat` v argumentu jako zápisy, které představují vzorky textu spíše než literál znaky. Úplný seznam znaků regulárních výrazů naleznete [v tématu Regulární výrazy](../../ide/using-regular-expressions-in-visual-studio.md).

/reset nebo /e

Nepovinný parametr. Vrátí možnosti hledání do výchozího nastavení a neprovede hledání.

/sel nebo /s

Nepovinný parametr. Prohledá pouze aktuální výběr. Zadejte pouze jeden z dostupných `/proc` `/open`oborů `/sel`hledání , `/doc`, , nebo .

/nahoru nebo /u

Nepovinný parametr. Prohledává z aktuálního umístění v souboru směrem k horní části souboru. Ve výchozím nastavení hledání začíná v aktuálním umístění v souboru a postupují směrem k dolnímu částsouboru.

/wild nebo /l

Nepovinný parametr. Používá předdefinované speciální znaky `findwhat` v argumentu jako zápisy představující znak nebo posloupnost znaků.

/slovo nebo /w

Nepovinný parametr. Vyhledá pouze celá slova.

## <a name="example"></a>Příklad
Tento příklad `btnSend` nahradí `btnSubmit` ve všech otevřených dokumentech.

```
>Edit.Replace btnSend btnSubmit /open
```

## <a name="see-also"></a>Viz také

- [Hledání a nahrazení textu](../../ide/finding-and-replacing-text.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Najít/Příkazové pole](../../ide/find-command-box.md)
- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
