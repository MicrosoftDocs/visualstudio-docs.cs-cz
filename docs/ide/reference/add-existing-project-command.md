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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bd6aca05758185f4df47688044f479b7bbe2829e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658817"
---
# <a name="add-existing-project-command"></a>Přidat existující projekt – příkaz
Přidá existující projekt k aktuálnímu řešení.

## <a name="syntax"></a>Syntaxe

```cmd
File.AddExistingProject filename
```

## <a name="arguments"></a>Arguments
`filename`\
Volitelné. Úplná cesta a název projektu s příponou projektu, který se má přidat do řešení.

Pokud argument `filename` obsahuje mezery, musí být uzavřen v uvozovkách.

Pokud není zadán žádný název souboru, příkaz otevře dialogové okno souboru, aby mohl uživatel vybrat projekt.

## <a name="remarks"></a>Poznámky
Automatické dokončování se snaží vyhledat správnou cestu a název souboru při psaní.

## <a name="example"></a>Příklad
Tento příklad přidá projekt [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] TestProject1 k aktuálnímu řešení.

```cmd
>File.AddExistingProject "c:\visual studio projects\TestProject1.vbproj"
```

## <a name="see-also"></a>Viz také

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Pole Najít/příkaz](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)