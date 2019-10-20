---
title: Otevřít soubor – příkaz | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.openfile
helpviewer_keywords:
- Open File command
- File.OpenFile command
- of command
ms.assetid: a51a83fc-e3c6-4fa2-8882-8b7b6c0a6406
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1c8dcf35e4c045db0d9acd45e2eb307a31ba39f1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671933"
---
# <a name="open-file-command"></a>Otevřít soubor – příkaz
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Otevře existující soubor a umožňuje určit editor.

## <a name="syntax"></a>Syntaxe

```
File.OpenFile filename [/e:editorname]
```

## <a name="arguments"></a>Arguments
 `filename` nutné. Úplná nebo částečná cesta a název souboru, který se má otevřít Cesty obsahující mezery musí být uzavřeny v uvozovkách.

## <a name="switches"></a>Přepínače
 /e: `editorname` volitelné. Název editoru, ve kterém bude soubor otevřen. Je-li zadán argument, ale není zadán žádný název editoru, zobrazí se dialogové okno **otevřít v** .

 Syntaxe parametru/e: `editorname` používá editory názvů, které se zobrazují v dialogovém okně Otevřít v programu, uzavřeném v uvozovkách.

 Chcete-li například otevřít soubor v editoru zdrojového kódu, zadejte následující příkaz pro argument/e: `editorname`.

```
/e:"Source Code (text) Editor"
```

## <a name="remarks"></a>Poznámky
 Při zadávání cesty se automatické dokončování pokusí vyhledat správnou cestu a název souboru.

## <a name="example"></a>Příklad
 Tento příklad otevře soubor style "test1. css" v editoru zdrojového kódu.

```
>File.OpenFile "C:\My Projects\project1\Test1.css" /e:"Source Code (text) Editor"
```

## <a name="see-also"></a>Viz také
 [](../../ide/reference/visual-studio-commands.md) [Příkazové okno](../../ide/reference/command-window.md) příkazového řádku pro příkazy [sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md) příkazového [řádku](../../ide/reference/immediate-window.md) [find](../../ide/find-command-box.md)
