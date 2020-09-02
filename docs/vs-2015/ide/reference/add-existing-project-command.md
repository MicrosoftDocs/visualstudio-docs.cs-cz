---
title: Přidat existující příkaz projektu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.addexistingproject
helpviewer_keywords:
- Add Existing Project command
- File.AddExistingProject
ms.assetid: 71cf3e31-c76b-405b-ad6a-1b1bc654bd40
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 73d8e54938659920227b3614046b8a8f933023ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670218"
---
# <a name="add-existing-project-command"></a>Přidat existující projekt – příkaz
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Přidá existující projekt k aktuálnímu řešení.

## <a name="syntax"></a>Syntaxe

```
File.AddExistingProject filename
```

## <a name="arguments"></a>Argumenty
 `filename` Volitelné. Úplná cesta a název projektu s příponou projektu, který se má přidat do řešení.

 Pokud `filename` argument obsahuje mezery, musí být uzavřen v uvozovkách.

 Pokud není zadán žádný název souboru, příkaz otevře dialogové okno souboru, aby mohl uživatel vybrat projekt.

## <a name="remarks"></a>Poznámky
 Automatické dokončování se snaží vyhledat správnou cestu a název souboru při psaní.

## <a name="example"></a>Příklad
 Tento příklad přidá [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] projekt TestProject1 do aktuálního řešení.

```
>File.AddExistingProject "c:\visual studio projects\TestProject1.vbproj"
```

## <a name="see-also"></a>Viz také
 [Příkazy](../../ide/reference/visual-studio-commands.md) [příkazového](../../ide/reference/command-window.md) řádku [find/Command](../../ide/find-command-box.md) v příkazu Visual Studio Command a Command [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
