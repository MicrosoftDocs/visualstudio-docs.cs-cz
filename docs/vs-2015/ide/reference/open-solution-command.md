---
title: Otevřít příkaz řešení | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.opensolution
helpviewer_keywords:
- Open Solution command
- File.OpenSolution command
ms.assetid: 61de76c8-69d7-4cdb-b605-e132f45d05d9
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b9c9ab66d2885137e9c470f577996ab861b554d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671913"
---
# <a name="open-solution-command"></a>Otevřít řešení – příkaz
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Otevře existující řešení a zavře všechna další otevřená řešení.

## <a name="syntax"></a>Syntaxe

```
File.OpenSolution filename
```

## <a name="arguments"></a>Argumenty
 `Filename` Požadovanou. Úplná cesta a název souboru řešení, které se má otevřít

 Syntaxe `filename` argumentu vyžaduje, aby cesty obsahující mezery používaly uvozovky.

## <a name="remarks"></a>Poznámky
 Automatické dokončování se snaží vyhledat správnou cestu a název souboru při psaní.

## <a name="example"></a>Příklad
 Tento příklad otevře řešení test1. sln.

```
>File.OpenSolution "c:\MySolutions\Test1\Test1.sln"
```

## <a name="see-also"></a>Viz také
 [Příkazy](../../ide/reference/visual-studio-commands.md) [příkazového](../../ide/reference/command-window.md) řádku [find/Command](../../ide/find-command-box.md) v příkazu Visual Studio Command a Command [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
