---
title: Nový soubor – příkaz
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.newfile
helpviewer_keywords:
- File.NewFile command
- New File command
ms.assetid: 767868d6-a525-425b-a43b-2198f636ab6b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8b4d68f53343b2523347f89977fe2bd602d64742
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2018
ms.locfileid: "39179954"
---
# <a name="new-file-command"></a>Nový soubor – příkaz
Vytvoří nový soubor a otevře jej. Soubor se zobrazí ve složce ostatní soubory.

## <a name="syntax"></a>Syntaxe

```cmd
File.NewFile [filename] [/t:templatename] [/editor:editorname]
```

## <a name="arguments"></a>Arguments
 `filename`

 Volitelné. Název souboru. Pokud je zadaný žádný název, výchozí název zadán. Pokud je uvedený žádný název šablony, se vytvoří textový soubor.

## <a name="switches"></a>Přepínače
 t:`templatename`

 Volitelné. Určuje typ souboru, který se má vytvořit.

 T:`templatename` argument syntaxe odráží informace nacházející se v dialogovém okně Nový soubor. Zadejte název kategorie, za nímž následuje zpětné lomítko (`\`) a šablony, zadejte název a uzavřete celý řetězec v uvozovkách.

 Například vytvořte novou [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] zdrojového souboru, zadali byste následující t:`templatename` argument.

```cmd
/t:"Visual C++\C++ File (.cpp)"
```

 Výše uvedený příklad určuje, že soubor C++ šablona se nachází v kategorii Visual C++ v **nový soubor** dialogové okno.

 / e:`editorname`

 Volitelné. Název editoru, ve kterém chcete soubor otevřít. Pokud je zadán argument, ale žádný editor název je zadán, **otevřít v** zobrazí se dialogové okno.

 / E:`editorname` argument syntaxe používá názvy editoru, jak se objeví v dialogovém okně Otevřít s, do uvozovek.

 Například by pro otevření souboru v editoru zdrojového kódu, zadejte následující pro / e:`editorname` argument.

```cmd
/e:"Source Code (text) Editor"
```

## <a name="example"></a>Příklad
 Tento příklad vytvoří novou webovou stránku "test1.htm" a otevře v editoru zdrojového kódu.

```cmd
>File.NewFile test1 /t:"General\HTML Page" /e:"Source Code (text) Editor"
```

## <a name="see-also"></a>Viz také

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Příkazové podokno](../../ide/reference/immediate-window.md)
- [Pole najít/příkaz](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)