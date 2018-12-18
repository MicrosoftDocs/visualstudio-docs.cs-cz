---
title: Najít – příkaz
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.find
helpviewer_keywords:
- Find command
- Edit.Find command
ms.assetid: f0c705dc-2b97-423d-abbf-5584d4827208
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fb84e7305797522c7e34e387357eedfdcd61e88f
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704184"
---
# <a name="find-command"></a>Najít – příkaz
Vyhledá soubory pomocí podmnožinu dostupných na možnostech **hledání v souborech** kartě **najít a nahradit** okno.

## <a name="syntax"></a>Syntaxe

```cmd
Edit.Find findwhat [/case] [/doc | /proc | /open | /sel]
[/markall] [/options] [/reset] [/up] [/wild | /regex] [/word]
```

## <a name="arguments"></a>Arguments
 `findwhat` Vyžaduje se. Text tak, aby odpovídaly.

## <a name="switches"></a>Přepínače
 /Case nebo /c volitelné. Odpovídá dojít pouze v případě, že velká a malá písmena přesně shodovat s uvedenými v `findwhat` argument.

 / DOC nebo /d volitelné. Vyhledá aktuálním dokumentu. Zadat pouze jeden z oborů dostupných vyhledávání `/doc`, `/proc`, `/open`, nebo `/sel`.

 /markall nebo /m volitelné. Umístí obrázek na každý řádek, který obsahuje shoda vyhledávání v aktuálním dokumentu.

 /Open nebo /o volitelné. Vyhledá všechny otevřené dokumenty, jako kdyby byly jeden dokument. Zadat pouze jeden z oborů dostupných vyhledávání `/doc`, `/proc`, `/open`, nebo `/sel`.

 / Options nebo /t volitelné. Zobrazí seznam aktuální nastavení možnosti Najít a nebude provádět vyhledávání.

 /proc nebo /p volitelné. Vyhledá pouze aktuální procedury. Zadat pouze jeden z oborů dostupných vyhledávání `/doc`, `/proc`, `/open`, nebo `/sel`.

 / Reset nebo /e volitelné. Vrátí možnosti Najít obnoveno výchozí nastavení a nebude provádět vyhledávání.

 /sel nebo /s volitelné. Vyhledá pouze aktuální výběr. Zadat pouze jeden z oborů dostupných vyhledávání `/doc`, `/proc`, `/open`, nebo `/sel`.

 /Up nebo /u volitelné. Vyhledávání z aktuálního umístění v souboru zpět na začátek souboru. Ve výchozím nastavení začne hledání v aktuální umístění v souboru a hledání na konci souboru.

 /Regex nebo /r volitelné. Používá předdefinované speciální znaky v `findwhat` argument jako zápisy, které představují vzory text místo literálové znaky. Úplný seznam regulárního výrazu znaky, najdete v části [regulární výrazy](../../ide/using-regular-expressions-in-visual-studio.md).

 /Wild nebo /l volitelné. Používá předdefinované speciální znaky v `findwhat` argument jako zápisy představující znak nebo posloupnost znaků.

 lze nebo /w volitelné. Vyhledá jenom celá slova.

## <a name="example"></a>Příklad
 Tento příklad provede malá a velká písmena vyhledejte slovo "somestring" v aktuálně vybraném části kódu.

```cmd
>Edit.Find somestring /sel /case
```

## <a name="see-also"></a>Viz také

- [Příkazové okno](../../ide/reference/command-window.md)
- [Pole najít/příkaz](../../ide/find-command-box.md)
- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)