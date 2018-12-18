---
title: Přidat existující projekt – příkaz
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.addexistingproject
helpviewer_keywords:
- Add Existing Project command
- File.AddExistingProject
ms.assetid: 71cf3e31-c76b-405b-ad6a-1b1bc654bd40
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c030358eb071613e98d473845708b01235683ded
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704782"
---
# <a name="add-existing-project-command"></a>Přidat existující projekt – příkaz
Přidá k aktuálnímu řešení existujícího projektu.

## <a name="syntax"></a>Syntaxe

```cmd
File.AddExistingProject filename
```

## <a name="arguments"></a>Arguments
 `filename` Volitelný parametr. Úplná cesta a projekt název, s příponou projektu pro přidání do řešení.

 Pokud `filename` argument obsahuje mezery, musí být uzavřena v uvozovkách.

 Pokud není zadaný žádný název souboru, bude příkaz otevřete dialogové okno souboru, tento uživatel může zvolit projektu.

## <a name="remarks"></a>Poznámky
 Automatické doplňování, pokusí se najít správnou cestu a název souboru při psaní.

## <a name="example"></a>Příklad
 Tento příklad přidá [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projektu, TestProject1, k aktuálnímu řešení.

```cmd
>File.AddExistingProject "c:\visual studio projects\TestProject1.vbproj"
```

## <a name="see-also"></a>Viz také

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Pole najít/příkaz](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)