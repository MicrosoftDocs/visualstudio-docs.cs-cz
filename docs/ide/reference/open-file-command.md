---
title: Otevřít soubor – příkaz
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- file.openfile
helpviewer_keywords:
- Open File command
- File.OpenFile command
- of command
ms.assetid: a51a83fc-e3c6-4fa2-8882-8b7b6c0a6406
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 50e29e3182a19c9f3a667d41725327110b415fd0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591512"
---
# <a name="open-file-command"></a>Otevřít soubor, příkaz

Otevře existující soubor a umožní zadat editor.

## <a name="syntax"></a>Syntaxe

```cmd
File.OpenFile filename [/e:editorname]
```

## <a name="arguments"></a>Argumenty

`filename`

Povinná hodnota. Úplná nebo částečná cesta a název souboru, který chcete otevřít. Cesty obsahující mezery musí být uzavřeny v uvozovkách.

## <a name="switches"></a>Přepínače

/e:`editorname`

Nepovinný parametr. Název editoru, ve kterém bude soubor otevřen. Pokud je argument zadán, ale není zadán žádný název editoru, zobrazí se dialogové okno **Otevřít v** akci.

Syntaxe argumentu /e:`editorname` používá názvy editorů tak, jak se zobrazují v dialogovém okně Otevřít s, uzavřeném v uvozovkách.

Chcete-li například otevřít soubor v editoru zdrojového kódu, zadejte pro argument /e:`editorname` následující.

```cmd
/e:"Source Code (text) Editor"
```

## <a name="remarks"></a>Poznámky

Při zadávání cesty se automatické dokončování pokusí najít správnou cestu a název souboru.

## <a name="example"></a>Příklad

Tento příklad otevře soubor stylu "Test1.css" v editoru zdrojového kódu.

```cmd
>File.OpenFile "C:\My Projects\project1\Test1.css" /e:"Source Code (text) Editor"
```

## <a name="see-also"></a>Viz také

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Okamžité okno](../../ide/reference/immediate-window.md)
- [Pole Najít/Příkaz](../../ide/find-command-box.md)
- [Aliasy příkazů Visual Studia](../../ide/reference/visual-studio-command-aliases.md)
