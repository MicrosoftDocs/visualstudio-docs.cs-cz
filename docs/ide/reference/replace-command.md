---
title: Nahradit – příkaz
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.replace
helpviewer_keywords:
- Edit.Replace command
- Replace command
ms.assetid: a15767f1-5a3d-44f5-8c77-7b0f1157f340
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5b712ee88526585d24ffd7b22fadbbf015c3d131
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
ms.locfileid: "31949942"
---
# <a name="replace-command"></a>Nahradit – příkaz
Nahradí text v souborech pomocí podmnožinu dostupných v možnostech **nahradit v souborech** kartě **najít a nahradit** okno.

## <a name="syntax"></a>Syntaxe

```
Edit.Replace findwhat replacewith [/all] [/case]
[/doc|/proc|/open|/sel] [/hidden] [/options] [/reset] [/up]
[/wild|/regex] [/word]
```

## <a name="arguments"></a>Arguments
 `findwhat`

 Požadováno. Text tak, aby odpovídaly.

 `replacewith`

 Požadováno. Text nahrazen odpovídající text.

## <a name="switches"></a>Přepínače
 / all nebo /

 Volitelné. Nahradí všechny výskyty hledaný text Nahrazovací text.

 /Case nebo /c

 Volitelné. Odpovídá dojít pouze v případě, kdy velká a malá písmena přesně shodovat platformám zadaným v `findwhat` argument.

 / DOC nebo/d

 Volitelné. Vyhledá aktuálním dokumentu. Zadat pouze jeden z oborů dostupných vyhledávání `/doc`, `/proc`, `/open`, nebo `/sel`.

 / hidden nebo /h

 Volitelné. Vyhledá skryté a sbalené text, například metadata ovládacího prvku návrhu skrytá oblasti dokument popsané nebo sbalené třída nebo metoda.

 /Open nebo /o

 Volitelné. Vyhledá všechny otevřené dokumenty, jako kdyby byly jeden dokument. Zadat pouze jeden z oborů dostupných vyhledávání `/doc`, `/proc`, `/open`, nebo `/sel`.

 / Options nebo/t.

 Volitelné. Zobrazí seznam aktuální nastavení možnosti Najít a nebude provádět vyhledávání.

 /proc nebo /p

 Volitelné. Vyhledá pouze aktuální procedury. Zadat pouze jeden z oborů dostupných vyhledávání `/doc`, `/proc`, `/open`, nebo `/sel`.

 /Regex nebo /r

 Volitelné. Používá předdefinované speciální znaky v `findwhat` argument jako zápisy, které představují vzory text místo literálové znaky. Úplný seznam regulárního výrazu znaky, najdete v části [regulární výrazy](../../ide/using-regular-expressions-in-visual-studio.md).

 / Reset nebo /e

 Volitelné. Vrátí možnosti Najít obnoveno výchozí nastavení a nebude provádět vyhledávání.

 /sel nebo /s

 Volitelné. Vyhledá pouze aktuální výběr. Zadat pouze jeden z oborů dostupných vyhledávání `/doc`, `/proc`, `/open`, nebo `/sel`.

 /Up nebo /u

 Volitelné. Vyhledávání z aktuálního umístění v souboru k horní části souboru. Ve výchozím nastavení začne hledání v aktuální umístění v souboru a záloh ve spodní části souboru.

 /Wild nebo/l

 Volitelné. Používá předdefinované speciální znaky v `findwhat` argument jako zápisy představující znak nebo posloupnost znaků.

 lze nebo /w

 Volitelné. Vyhledá jenom celá slova.

## <a name="example"></a>Příklad
 Tento příklad nahrazuje `btnSend` s `btnSubmit` ve všech otevřít dokumenty.

```
>Edit.Replace btnSend btnSubmit /open
```

## <a name="see-also"></a>Viz také

- [Hledání a nahrazení textu](../../ide/finding-and-replacing-text.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Pole najít/příkaz](../../ide/find-command-box.md)
- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)