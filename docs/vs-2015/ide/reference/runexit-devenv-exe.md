---
title: -Runexit (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- runexit Devenv switch
- Devenv, /runexit switch
- /runexit Devenv switch
ms.assetid: bfc94875-5fc0-4110-b961-d59c0b403790
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6d1158a12de8b8adfe20fa6d045b756abf8d7b3c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665496"
---
# <a name="runexit-devenvexe"></a>/Runexit (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zkompiluje a spustí zadaný projekt nebo řešení a potom zavře integrované vývojové prostředí (IDE).

## <a name="syntax"></a>Syntaxe

```
devenv /runexit {SolutionName|ProjectName}
```

## <a name="arguments"></a>Argumenty
 `SolutionName` Požadovanou. Úplná cesta a název souboru řešení.

 `ProjectName` Požadovanou. Úplná cesta a název souboru projektu.

## <a name="remarks"></a>Poznámky
 Zkompiluje a spustí zadaný projekt nebo řešení podle nastavení určeného pro aktivní konfiguraci řešení. Tento přepínač minimalizuje rozhraní IDE během spuštění projektu nebo řešení a ukončí prostředí IDE po dokončení běhu projektu nebo řešení.

- Uzavřete řetězce, které obsahují mezery, do dvojitých uvozovek.

- Souhrnné informace, včetně chyb, lze zobrazit v **příkazovém** okně nebo v jakémkoli souboru protokolu, který je zadán s `/out` přepínačem.

## <a name="example"></a>Příklad
 Tento příklad spustí řešení `MySolution` v minimalizovaném integrovaném vývojovém prostředí pomocí aktivní konfigurace nasazení a pak ukončí rozhraní IDE.

```
devenv /runexit "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Viz také
 [Příkazového řádku Devenv – přepínače](../../ide/reference/devenv-command-line-switches.md) [/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md) [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md) [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md) [/out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
