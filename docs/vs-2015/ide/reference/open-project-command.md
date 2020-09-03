---
title: Otevřít příkaz projektu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.openproject
helpviewer_keywords:
- op command
- File.OpenProject command
- Open Project command
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 99596442f3aef9e4cb2d890438d29b96cdf4f083
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671925"
---
# <a name="open-project-command"></a>Otevřít projekt – příkaz
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Otevře existující projekt.

## <a name="syntax"></a>Syntaxe

```
File.OpenProject filename
```

## <a name="arguments"></a>Argumenty
 `filename` Požadovanou. Úplná cesta a název souboru projektu, který se má otevřít

 Syntaxe `filename` argumentu vyžaduje, aby cesty obsahující mezery používaly uvozovky.

## <a name="remarks"></a>Poznámky
 Automatické dokončování se snaží vyhledat správnou cestu a název souboru při psaní.

 Tento příkaz není k dispozici při ladění.

## <a name="example"></a>Příklad
 Tento příklad otevře [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] projekt, test1.

```
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"
```

## <a name="see-also"></a>Viz také
 [Příkazy](../../ide/reference/visual-studio-commands.md) [příkazového](../../ide/reference/command-window.md) řádku [find/Command](../../ide/find-command-box.md) v příkazu Visual Studio Command a Command [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
