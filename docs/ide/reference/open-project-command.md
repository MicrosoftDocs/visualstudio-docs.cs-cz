---
title: otevřít projekt – příkaz
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- file.openproject
- file.opensolution
helpviewer_keywords:
- op command
- File.OpenProject command
- Open Project command
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 97c1034fbbafa04af2d62526fdbb48812d64e050
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75565809"
---
# <a name="open-project-command"></a>Otevřít projekt – příkaz

Otevře existující projekt nebo řešení.

## <a name="syntax"></a>Syntaxe

```cmd
File.OpenProject filename
```

## <a name="arguments"></a>Arguments

`filename`

Požadováno. Úplná cesta a název souboru projektu nebo řešení, který se má otevřít

> [!NOTE]
> Syntaxe argumentu `filename` vyžaduje, aby cesty obsahující mezery používaly uvozovky.

## <a name="remarks"></a>Poznámky

Automatické dokončování se snaží vyhledat správnou cestu a název souboru při psaní.

Tento příkaz není k dispozici při ladění.

## <a name="example"></a>Příklad

Následující příklad otevře Visual Basic projektu **test1**:

```cmd
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"
```

## <a name="see-also"></a>Viz také:

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [okno Příkaz](../../ide/reference/command-window.md)
- [Pole Najít/příkaz](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
