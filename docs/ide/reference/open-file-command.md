---
title: Otevřít soubor – příkaz
description: Přečtěte si o příkazu otevřít soubor a o tom, jak otevře existující soubor a umožňuje určit editor.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 96376c352d3019ba2efefc1f82e75e89a4ac2370
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935622"
---
# <a name="open-file-command"></a>Otevřít soubor – příkaz

Otevře existující soubor a umožňuje určit editor.

## <a name="syntax"></a>Syntaxe

```cmd
File.OpenFile filename [/e:editorname]
```

## <a name="arguments"></a>Argumenty

`filename`

Povinná hodnota. Úplná nebo částečná cesta a název souboru, který se má otevřít Cesty obsahující mezery musí být uzavřeny v uvozovkách.

## <a name="switches"></a>přepínače,

/e`editorname`

Nepovinný parametr. Název editoru, ve kterém bude soubor otevřen. Je-li zadán argument, ale není zadán žádný název editoru, zobrazí se dialogové okno **otevřít v** .

Syntaxe/e: `editorname` argument používá názvy editoru tak, jak se zobrazí v dialogovém okně Otevřít v aplikaci uzavřené v uvozovkách.

Chcete-li například otevřít soubor v editoru zdrojového kódu, zadejte následující příkaz pro parametr/e: `editorname` .

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

## <a name="see-also"></a>Viz také

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Okno Příkaz](../../ide/reference/command-window.md)
- [Příkazové podokno](../../ide/reference/immediate-window.md)
- [Pole Najít/příkaz](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
