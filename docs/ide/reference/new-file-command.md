---
title: Nový soubor – příkaz
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- file.newfile
helpviewer_keywords:
- File.NewFile command
- New File command
ms.assetid: 767868d6-a525-425b-a43b-2198f636ab6b
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5fe8a99ee59a347fdcb7cff601b75139760630f7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595953"
---
# <a name="new-file-command"></a>Nový soubor – příkaz
Vytvoří nový soubor a otevře jej. Soubor se zobrazí ve složce Různé soubory.

## <a name="syntax"></a>Syntaxe

```cmd
File.NewFile [filename] [/t:templatename] [/editor:editorname]
```

## <a name="arguments"></a>Argumenty
`filename`

Nepovinný parametr. Název souboru. Pokud není zadán žádný název, je k dispozici výchozí název. Pokud není uveden žádný název šablony, vytvoří se textový soubor.

## <a name="switches"></a>Přepínače
/t:`templatename`\
Nepovinný parametr. Určuje typ souboru, který má být vytvořen.

Hodnota /t:`templatename` syntaxe argumentu zrcadlí informace nalezené v dialogovém okně Nový soubor. Zadejte název kategorie následovaný zpětným`\`lomítkem ( ) a názvem šablony a uzavřete celý řetězec do uvozovek.

Chcete-li například [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] vytvořit nový zdrojový soubor, zadejte pro`templatename` argument /t: následující.

```cmd
/t:"Visual C++\C++ File (.cpp)"
```

Výše uvedený příklad ukazuje, že šablona souboru C++ je umístěna v kategorii Visual C++ v dialogovém okně **Nový soubor.**

/e:`editorname`\
Nepovinný parametr. Název editoru, ve kterém bude soubor otevřen. Pokud je argument zadán, ale není zadán žádný název editoru, zobrazí se dialogové okno **Otevřít v** akci.

Syntaxe argumentu /e:`editorname` používá názvy editorů tak, jak se zobrazují v dialogovém okně Otevřít s, uzavřeném v uvozovkách.

Chcete-li například otevřít soubor v editoru zdrojového kódu, zadejte pro argument /e:`editorname` následující.

```cmd
/e:"Source Code (text) Editor"
```

## <a name="example"></a>Příklad
Tento příklad vytvoří novou webovou stránku "test1.htm" a otevře ji v editoru zdrojového kódu.

```cmd
>File.NewFile test1 /t:"General\HTML Page" /e:"Source Code (text) Editor"
```

## <a name="see-also"></a>Viz také

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Příkazové podokno](../../ide/reference/immediate-window.md)
- [Najít/Příkazové pole](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
