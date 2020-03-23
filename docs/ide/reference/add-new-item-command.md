---
title: Přidat novou položku – příkaz
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- project.addnewitem
helpviewer_keywords:
- Add New Item command
- File.AddNewItem command
ms.assetid: 63b7df32-db83-463b-bbe7-7ff011fe5298
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 38be691ae7c49ffbd6c98c9e4beb25b6ebb021b6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585688"
---
# <a name="add-new-item-command"></a>Přidat novou položku – příkaz
Přidá novou položku řešení, například .htm, .css, .txt nebo frameset do aktuálního řešení a otevře ji.

## <a name="syntax"></a>Syntaxe

```cmd
File.AddNewItem [filename] [/t:templatename] [/e:editorname]
```

## <a name="arguments"></a>Argumenty
`filename`\
Nepovinný parametr. Cesta a název souboru položky, kterou chcete přidat do řešení.

## <a name="switches"></a>Přepínače
/t:`templatename`\
Nepovinný parametr. Určuje typ souboru, který má být vytvořen. Pokud není uveden žádný název šablony, je ve výchozím nastavení vytvořen textový soubor.

Syntaxe`templatename` argumentu /t zrcadlí informace nalezené v dialogovém okně **Přidat novou položku řešení.** Je nutné zadat celou kategorii následovanou typem souboru, oddělit název kategorie`\`od typu souboru zpětným lomítkem ( ) a uzavřít celý řetězec do uvozovek.

Chcete-li například vytvořit nový textový soubor, zadejte pro`templatename` argument /t: následující.

```cmd
/t:"General\Style Sheet"
```

/e:`editorname`\
Nepovinný parametr. Název editoru, ve kterém bude soubor otevřen. Pokud je argument zadán, ale není zadán žádný název editoru, zobrazí se dialogové okno **Otevřít v** akci.

Syntaxe argumentu /e:`editorname` používá názvy editorů tak, jak jsou zobrazeny v **dialogovém okně Otevřít s**, které jsou uzavřeny v uvozovkách.

Chcete-li například otevřít šablonu stylů v editoru zdrojového kódu,`editorname` zadejte pro argument /e: následující.

```cmd
/e:"Source Code (text) Editor"
```

## <a name="example"></a>Příklad
Tento příklad přidá novou položku řešení MyHTMLpg do aktuálního řešení.

```cmd
>File.AddNewItem MyHTMLpg /t:"General\HTML Page"
```

## <a name="see-also"></a>Viz také

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Najít/Příkazové pole](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
