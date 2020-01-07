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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595953"
---
# <a name="new-file-command"></a>Nový soubor – příkaz
Vytvoří nový soubor a otevře ho. Soubor se zobrazí ve složce různé soubory.

## <a name="syntax"></a>Syntaxe

```cmd
File.NewFile [filename] [/t:templatename] [/editor:editorname]
```

## <a name="arguments"></a>Arguments
`filename`

Volitelné. Název souboru Pokud není zadán žádný název, je zadán výchozí název. Pokud není uveden žádný název šablony, je vytvořen textový soubor.

## <a name="switches"></a>Přepínače
/t:`templatename`\
Volitelné. Určuje typ souboru, který se má vytvořit.

Syntaxe argumentu/t:`templatename` zrcadlí informace, které se nacházejí v dialogovém okně Nový soubor. Zadejte název kategorie následovaný zpětným lomítkem (`\`) a názvem šablony a uzavřete celý řetězec v uvozovkách.

Chcete-li například vytvořit nový zdrojový soubor [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], zadejte následující příkaz pro argument/t:`templatename`.

```cmd
/t:"Visual C++\C++ File (.cpp)"
```

Výše uvedený příklad ukazuje, že C++ šablona souboru je umístěna v kategorii vizuálu C++ v dialogovém okně **nový soubor** .

/e:`editorname`\
Volitelné. Název editoru, ve kterém bude soubor otevřen. Je-li zadán argument, ale není zadán žádný název editoru, zobrazí se dialogové okno **otevřít v** .

Syntaxe parametru/e:`editorname` používá editory názvů, které se zobrazují v dialogovém okně Otevřít v programu, uzavřeném v uvozovkách.

Chcete-li například otevřít soubor v editoru zdrojového kódu, zadejte následující příkaz pro argument/e:`editorname`.

```cmd
/e:"Source Code (text) Editor"
```

## <a name="example"></a>Příklad
Tento příklad vytvoří novou webovou stránku "test1. htm" a otevře ji v editoru zdrojového kódu.

```cmd
>File.NewFile test1 /t:"General\HTML Page" /e:"Source Code (text) Editor"
```

## <a name="see-also"></a>Viz také:

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Příkazové podokno](../../ide/reference/immediate-window.md)
- [Pole Najít/příkaz](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
