---
title: Registrují se rozšíření .NET Framework | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- Add References dialog box, registering extensions of the .NET Framework
- MSBuild, registering extensions of the .NET Framework
- .NET Framework extensions, registering
ms.assetid: deee6f53-ea87-4b88-a120-bea589822e03
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a5963faa5acb72ab0c94ca6b346456d83276e361
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64831489"
---
# <a name="registering-extensions-of-the-net-framework"></a>Registrace rozšíření rozhraní .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete vyvíjet sestavení, které rozšiřuje konkrétní verzi .NET Framework. Chcete-li povolit zobrazení sestavení v dialogovém okně **Přidat odkazy** v aplikaci Visual Studio, je nutné přidat složku, která obsahuje tuto složku do systémového registru.  
  
 Předpokládejme například, že společnost společnost Trey Research vyvinula knihovnu, která rozšiřuje .NET Framework 4, a chce, aby se sestavení knihovny zobrazilo v dialogovém okně **Přidat odkazy** , když projekt cílí na .NET Framework 4. Také předpokládá, že sestavení jsou 32 bitová sestavení, která běží na 32m počítači 64 nebo v rozC:\TreyResearch\Extensions4\ch sestaveních, která běží 64 na 16bitovém počítači a která budou nainstalována do složky.  
  
 Tuto složku Zaregistrujte pomocí tohoto klíče: HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft \\ . NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch \\ . Zadejte klíč tuto výchozí hodnotu: C:\TreyResearch\Extensions4.  
  
> [!NOTE]
> Číslo buildu verze .NET Framework se může lišit.  
  
 K registraci 32 sestavení na 64 počítači použijte uzel Wow6432, například: HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node\Microsoft \\ . NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch \\ .  
  
## <a name="see-also"></a>Viz také  
 [Integrace sady Visual Studio](../msbuild/visual-studio-integration-msbuild.md)
