---
title: Přidat existující položku – příkaz | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- project.addexistingitem
helpviewer_keywords:
- File.AddExistingItem command
- Add Existing Item command
ms.assetid: 41f56131-d4c7-4f81-83b7-bdac713ea870
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c2f636c2a0eb2cfdcebf383fdc7eea70f72cb90e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670226"
---
# <a name="add-existing-item-command"></a>Přidat existující položku – příkaz
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Přidá existující soubor do aktuálního řešení a otevře ho.

## <a name="syntax"></a>Syntaxe

```
File.AddExistingItem filename [/e:editorname]
```

## <a name="arguments"></a>Argumenty
 `filename` Požadovanou. Úplná cesta a název souboru s příponou položky, která se má přidat do aktuálního řešení. Pokud cesta nebo název souboru obsahují mezery, uzavřete celou cestu do uvozovek.

## <a name="switches"></a>Přepínače
 /e: `editorname` volitelné. Název editoru, ve kterém bude soubor otevřen. Je-li zadán argument, ale není zadán žádný název editoru, zobrazí se dialogové okno **otevřít v** .

 Syntaxe/e: `editorname` argument používá názvy editoru tak, jak se zobrazí v **dialogovém okně Otevřít v aplikaci**uzavřené v uvozovkách. Chcete-li například otevřít šablonu stylů v editoru zdrojového kódu, zadejte následující příkaz pro parametr/e: `editorname` .

```
/e:"Source Code (text) Editor"
```

## <a name="remarks"></a>Poznámky
 Automatické dokončování se snaží vyhledat správnou cestu a název souboru při psaní.

## <a name="example"></a>Příklad
 Tento příklad přidá soubor. Form1. frm do aktuálního řešení.

```
>File.AddExistingItem "C:\public\solution files\Form1.frm"
```

## <a name="see-also"></a>Viz také
 [Příkazy](../../ide/reference/visual-studio-commands.md) [příkazového](../../ide/reference/command-window.md) řádku [find/Command](../../ide/find-command-box.md) v příkazu Visual Studio Command a Command [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
