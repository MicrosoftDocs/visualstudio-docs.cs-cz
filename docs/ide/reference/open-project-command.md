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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565809"
---
# <a name="open-project-command"></a>Otevřít příkaz projektu

Otevře existující projekt nebo řešení.

## <a name="syntax"></a>Syntaxe

```cmd
File.OpenProject filename
```

## <a name="arguments"></a>Argumenty

`filename`

Povinná hodnota. Úplná cesta a název souboru projektu nebo řešení, které chcete otevřít.

> [!NOTE]
> Syntaxe argumentu `filename` vyžaduje, aby cesty, které obsahují mezery, používaly uvozovky.

## <a name="remarks"></a>Poznámky

Automatické dokončování se pokusí při psaní najít správnou cestu a název souboru.

Tento příkaz není k dispozici při ladění.

## <a name="example"></a>Příklad

Následující příklad otevře projekt Visual Basic **Test1**:

```cmd
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"
```

## <a name="see-also"></a>Viz také

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Pole Najít/Příkaz](../../ide/find-command-box.md)
- [Aliasy příkazů Visual Studia](../../ide/reference/visual-studio-command-aliases.md)
