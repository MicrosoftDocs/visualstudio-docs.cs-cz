---
title: Přidat existující projekt – příkaz
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- file.addexistingproject
helpviewer_keywords:
- Add Existing Project command
- File.AddExistingProject
ms.assetid: 71cf3e31-c76b-405b-ad6a-1b1bc654bd40
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 008802546d87bd44137c6d13ee2aef802877e308
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595875"
---
# <a name="add-existing-project-command"></a>Přidat existující projekt – příkaz
Přidá existující projekt do aktuálního řešení.

## <a name="syntax"></a>Syntaxe

```cmd
File.AddExistingProject filename
```

## <a name="arguments"></a>Argumenty
`filename`\
Nepovinný parametr. Úplná cesta a název projektu s rozšířením projektu, který chcete přidat do řešení.

Pokud `filename` argument obsahuje mezery, musí být uzavřen v uvozovkách.

Pokud není zadán žádný název souboru, příkaz otevře dialogové okno souboru, aby uživatel mohl vybrat projekt.

## <a name="remarks"></a>Poznámky
Automatické dokončování se při psaní pokusí najít správnou cestu a název souboru.

## <a name="example"></a>Příklad
Tento příklad [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] přidá projekt TestProject1 k aktuálnímu řešení.

```cmd
>File.AddExistingProject "c:\visual studio projects\TestProject1.vbproj"
```

## <a name="see-also"></a>Viz také

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Najít/Příkazové pole](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
