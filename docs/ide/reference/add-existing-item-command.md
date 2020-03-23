---
title: Přidat existující položku – příkaz
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- project.addexistingitem
helpviewer_keywords:
- File.AddExistingItem command
- Add Existing Item command
ms.assetid: 41f56131-d4c7-4f81-83b7-bdac713ea870
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4d49f0fde7bbf13a1219296420b84970f4350860
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585701"
---
# <a name="add-existing-item-command"></a>Přidat existující položku – příkaz
Přidá existující soubor do aktuálního řešení a otevře jej.

## <a name="syntax"></a>Syntaxe

```cmd
File.AddExistingItem filename [/e:editorname]
```

## <a name="arguments"></a>Argumenty
`filename`\
Povinná hodnota. Úplná cesta a název souboru s příponou položky, kterou chcete přidat do aktuálního řešení. Pokud cesta k souboru nebo název souboru obsahuje mezery, uzavřete celou cestu do uvozovek.

## <a name="switches"></a>Přepínače
/e:`editorname`\
Nepovinný parametr. Název editoru, ve kterém bude soubor otevřen. Pokud je argument zadán, ale není zadán žádný název editoru, zobrazí se dialogové okno **Otevřít v** akci.

Syntaxe argumentu /e:`editorname` používá názvy editorů tak, jak jsou zobrazeny v **dialogovém okně Otevřít s**, které jsou uzavřeny v uvozovkách. Chcete-li například otevřít šablonu stylů v editoru zdrojového kódu,`editorname` zadejte pro argument /e: následující.

```cmd
/e:"Source Code (text) Editor"
```

## <a name="remarks"></a>Poznámky
Automatické dokončování se pokusí při psaní najít správnou cestu a název souboru.

## <a name="example"></a>Příklad
Tento příklad přidá soubor Form1.frm do aktuálního řešení.

```cmd
>File.AddExistingItem "C:\public\solution files\Form1.frm"
```

## <a name="see-also"></a>Viz také

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Najít/Příkazové pole](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
