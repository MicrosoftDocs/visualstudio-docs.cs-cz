---
title: Registrace rozšíření rozhraní .NET Framework | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add References dialog box, registering extensions of the .NET Framework
- MSBuild, registering extensions of the .NET Framework
- .NET Framework extensions, registering
ms.assetid: deee6f53-ea87-4b88-a120-bea589822e03
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: e7f79e04cc9afb4238c9f6292a99da684066a7d5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632859"
---
# <a name="register-extensions-of-the-net-framework"></a>Registrace rozšíření rozhraní .NET Framework

Můžete vyvinout sestavení, které rozšiřuje konkrétní verzi rozhraní .NET Framework. Chcete-li povolit zobrazení sestavení v dialogovém okně **Přidat odkazy** sady Visual Studio, je nutné přidat složku, která jej obsahuje, do systémového registru.

 Předpokládejme například, že společnost Trey Research vyvinula knihovnu, která rozšiřuje rozhraní .NET Framework 4, a chce, aby se sestavení knihovny zobrazila v dialogovém okně **Přidat odkazy,** když projekt cílí na rozhraní .NET Framework 4. Předpokládejme také, že sestavení jsou 32bitová sestavení spuštěná v 32bitovém počítači nebo 64bitová sestavení spuštěná v 64bitovém počítači a že budou nainstalována ve složce *C:\TreyResearch\Extensions4.\\ *

 Zaregistrujte tuto složku pomocí tohoto klíče: **\\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft . NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch\\**. Přidejte klíči tuto výchozí hodnotu: **C:\TreyResearch\Extensions4**.

> [!NOTE]
> Číslo sestavení verze rozhraní .NET Framework se může lišit.

 Chcete-li zaregistrovat 32bitové sestavení v 64bitovém počítači, použijte uzel Wow6432, **například:\\HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft . NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch\\**.

### <a name="see-also"></a>Viz také

- [Integrace se sadou Visual Studio](../msbuild/visual-studio-integration-msbuild.md)
