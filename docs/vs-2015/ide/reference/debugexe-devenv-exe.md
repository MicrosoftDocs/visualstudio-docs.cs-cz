---
title: -DebugExe (devenv. exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /DebugExe switch
- DebugExe switch
- /DebugExe [devenv.exe]
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f472add6b821693d1d48397e878db19e707e2868
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660806"
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Otevře zadaný spustitelný soubor, který se má ladit.

## <a name="syntax"></a>Syntaxe

```
Devenv /debugexe ExecutableFile
```

## <a name="arguments"></a>Arguments
 `ExecutableFile` nutné. Cesta a název souboru s příponou. exe.

 Pokud se soubor. exe nenajde nebo neexistuje, nezobrazí se žádné upozornění nebo chyba a [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] se spustí normálně.

## <a name="remarks"></a>Poznámky
 Všechny řetězce za parametrem `ExecutableFile` jsou do tohoto souboru předány jako argumenty.

## <a name="example"></a>Příklad
 Následující příklad otevře soubor `MyApplication.exe` pro ladění.

```
Devenv.exe /debugexe MyApplication.exe
```

## <a name="see-also"></a>Viz také
 [Devenv – přepínače příkazového řádku](../../ide/reference/devenv-command-line-switches.md)
