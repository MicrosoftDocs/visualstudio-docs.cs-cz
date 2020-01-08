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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591512"
---
# <a name="open-file-command"></a>Otevřít soubor – příkaz

Otevře existující soubor a umožňuje určit editor.

## <a name="syntax"></a>Syntaxe

```cmd
File.OpenFile filename [/e:editorname]
```

## <a name="arguments"></a>Arguments

`filename`

Požadováno. Úplná nebo částečná cesta a název souboru, který se má otevřít Cesty obsahující mezery musí být uzavřeny v uvozovkách.

## <a name="switches"></a>Přepínače

/e:`editorname`

Volitelné. Název editoru, ve kterém bude soubor otevřen. Je-li zadán argument, ale není zadán žádný název editoru, zobrazí se dialogové okno **otevřít v** .

Syntaxe parametru/e:`editorname` používá editory názvů, které se zobrazují v dialogovém okně Otevřít v programu, uzavřeném v uvozovkách.

Chcete-li například otevřít soubor v editoru zdrojového kódu, zadejte následující příkaz pro argument/e:`editorname`.

```cmd
/e:"Source Code (text) Editor"
```

## <a name="remarks"></a>Poznámky

Při zadávání cesty se automatické dokončování pokusí vyhledat správnou cestu a název souboru.

## <a name="example"></a>Příklad

Tento příklad otevře soubor style "test1. css" v editoru zdrojového kódu.

```cmd
>File.OpenFile "C:\My Projects\project1\Test1.css" /e:"Source Code (text) Editor"
```

## <a name="see-also"></a>Viz také:

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [okno Příkaz](../../ide/reference/command-window.md)
- [Příkazové okno](../../ide/reference/immediate-window.md)
- [Pole Najít/příkaz](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
