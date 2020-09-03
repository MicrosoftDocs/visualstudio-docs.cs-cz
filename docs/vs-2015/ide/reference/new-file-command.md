---
title: Nový soubor – příkaz | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.newfile
helpviewer_keywords:
- File.NewFile command
- New File command
ms.assetid: 767868d6-a525-425b-a43b-2198f636ab6b
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8e0d25d585f518c854ad6176ae4ae7a5f27b22ad
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671960"
---
# <a name="new-file-command"></a>Nový soubor – příkaz
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vytvoří nový soubor a otevře ho. Soubor se zobrazí ve složce různé soubory.

## <a name="syntax"></a>Syntaxe

```
File.NewFile [filename] [/t:templatename] [/editor:editorname]
```

## <a name="arguments"></a>Argumenty
 `filename` Volitelné. Název souboru Pokud není zadán žádný název, je zadán výchozí název. Pokud není uveden žádný název šablony, je vytvořen textový soubor.

## <a name="switches"></a>Přepínače
 /t: `templatename` volitelné. Určuje typ souboru, který se má vytvořit.

 Syntaxe/t: `templatename` argument odráží informace, které se nacházejí v dialogovém okně Nový soubor. Zadejte název kategorie následovaný zpětným lomítkem ( `\` ) a názvem šablony a uzavřete celý řetězec do uvozovek.

 Pokud například chcete vytvořit nový [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] zdrojový soubor, zadejte do argumentu/t: následující hodnotu `templatename` .

```
/t:"Visual C++\C++ File (.cpp)"
```

 Výše uvedený příklad ukazuje, že šablona souboru C++ je umístěna v kategorii Visual C++ v dialogovém okně **nový soubor** .

 /e: `editorname` volitelné. Název editoru, ve kterém bude soubor otevřen. Je-li zadán argument, ale není zadán žádný název editoru, zobrazí se dialogové okno **otevřít v** .

 Syntaxe/e: `editorname` argument používá názvy editoru tak, jak se zobrazí v dialogovém okně Otevřít v aplikaci uzavřené v uvozovkách.

 Chcete-li například otevřít soubor v editoru zdrojového kódu, zadejte následující příkaz pro parametr/e: `editorname` .

```
/e:"Source Code (text) Editor"
```

## <a name="example"></a>Příklad
 Tento příklad vytvoří novou webovou stránku "test1.htm" a otevře ji v editoru zdrojového kódu.

```
>File.NewFile test1 /t:"General\HTML Page" /e:"Source Code (text) Editor"
```

## <a name="see-also"></a>Viz také
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md) [Příkazové okno](../../ide/reference/command-window.md) příkazového řádku pro příkazy [sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md) příkazového [řádku](../../ide/reference/immediate-window.md) [find](../../ide/find-command-box.md)
