---
title: Přidat existující položku – příkaz
description: Přečtěte si o příkazu Přidat existující položku a o tom, jak přidá existující soubor do aktuálního řešení a otevře ho.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 43c9e7d5947796bb1598bf9dc02420b31e43d167
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933827"
---
# <a name="add-existing-item-command"></a>Přidat existující položku – příkaz
Přidá existující soubor do aktuálního řešení a otevře ho.

## <a name="syntax"></a>Syntaxe

```cmd
File.AddExistingItem filename [/e:editorname]
```

## <a name="arguments"></a>Argumenty
`filename`\
Povinná hodnota. Úplná cesta a název souboru s příponou položky, která se má přidat do aktuálního řešení. Pokud cesta nebo název souboru obsahují mezery, uzavřete celou cestu do uvozovek.

## <a name="switches"></a>přepínače,
/e `editorname`\
Nepovinný parametr. Název editoru, ve kterém bude soubor otevřen. Je-li zadán argument, ale není zadán žádný název editoru, zobrazí se dialogové okno **otevřít v** .

Syntaxe/e: `editorname` argument používá názvy editoru tak, jak se zobrazí v **dialogovém okně Otevřít v aplikaci** uzavřené v uvozovkách. Chcete-li například otevřít šablonu stylů v editoru zdrojového kódu, zadejte následující příkaz pro parametr/e: `editorname` .

```cmd
/e:"Source Code (text) Editor"
```

## <a name="remarks"></a>Poznámky
Automatické dokončování se snaží vyhledat správnou cestu a název souboru při psaní.

## <a name="example"></a>Příklad
Tento příklad přidá soubor. Form1. frm do aktuálního řešení.

```cmd
>File.AddExistingItem "C:\public\solution files\Form1.frm"
```

## <a name="see-also"></a>Viz také

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Pole Najít/příkaz](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
