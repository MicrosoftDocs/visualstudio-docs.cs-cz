---
title: Příkaz pro přidání nové položky | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- project.addnewitem
helpviewer_keywords:
- Add New Item command
- File.AddNewItem command
ms.assetid: 63b7df32-db83-463b-bbe7-7ff011fe5298
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e6237ace96799961683b0b0431f5dad3ab679e24
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670198"
---
# <a name="add-new-item-command"></a>Přidat novou položku – příkaz
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Přidá novou položku řešení, jako je například. htm,. CSS,. txt nebo FRAMESET, do aktuálního řešení a otevře se.

## <a name="syntax"></a>Syntaxe

```
File.AddNewItem [filename] [/t:templatename] [/e:editorname]
```

## <a name="arguments"></a>Arguments
 `filename` volitelné. Cesta a název souboru položky, která se má přidat do řešení

## <a name="switches"></a>Přepínače
 /t: `templatename` volitelné. Určuje typ souboru, který se má vytvořit. Pokud není zadán žádný název šablony, je ve výchozím nastavení vytvořen textový soubor.

 Syntaxe argumentu/t: `templatename` zrcadlí informace, které se nacházejí v dialogovém okně **Přidat novou položku řešení** . Je nutné zadat celou kategorii, za kterou následuje typ souboru, oddělení názvu kategorie od typu souboru zpětným lomítkem (`\`) a uzavřením celého řetězce v uvozovkách.

 Pokud například chcete vytvořit nový textový soubor, zadejte do argumentu/t: `templatename` následující text.

```
/t:"General\Style Sheet"
```

 /e: `editorname` volitelné. Název editoru, ve kterém bude soubor otevřen. Je-li zadán argument, ale není zadán žádný název editoru, zobrazí se dialogové okno **otevřít v** .

 Syntaxe parametru/e: `editorname` používá editory názvů, které se zobrazují v **dialogovém okně Otevřít v programu**, uzavřeném v uvozovkách.

 Chcete-li například otevřít šablonu stylů v editoru zdrojového kódu, zadejte následující příkaz pro argument/e: `editorname`.

```
/e:"Source Code (text) Editor"
```

## <a name="example"></a>Příklad
 Tento příklad přidá novou položku řešení MyHTMLpg do aktuálního řešení.

```
>File.AddNewItem MyHTMLpg /t:"General\HTML Page"
```

## <a name="see-also"></a>Viz také
 [Příkazy](../../ide/reference/visual-studio-commands.md) [příkazového](../../ide/reference/command-window.md) řádku [find/Command](../../ide/find-command-box.md) v příkazu Visual Studio Command a Command [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
