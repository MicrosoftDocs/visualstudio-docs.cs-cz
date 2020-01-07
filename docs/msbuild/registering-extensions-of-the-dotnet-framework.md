---
title: Registrují se rozšíření .NET Framework | Microsoft Docs
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
ms.openlocfilehash: 1957bae45504e5654b3ed63c9fa0821a7f4c8758
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596759"
---
# <a name="register-extensions-of-the-net-framework"></a>Registrovat rozšíření .NET Framework
Můžete vyvíjet sestavení, které rozšiřuje konkrétní verzi .NET Framework. Chcete-li povolit zobrazení sestavení v dialogovém okně **Přidat odkazy** v aplikaci Visual Studio, je nutné přidat složku, která obsahuje tuto složku do systémového registru.

 Předpokládejme například, že společnost společnost Trey Research vyvinula knihovnu, která rozšiřuje .NET Framework 4, a chce, aby se sestavení knihovny zobrazilo v dialogovém okně **Přidat odkazy** , když projekt cílí na .NET Framework 4. Také předpokládá, že sestavení jsou 32 bitová sestavení, která běží na 32m počítači 64 nebo v rozC:\TreyResearch\Extensions4ch sestaveních, která běží 64 na 16bitovém počítači a která budou nainstalována do složky *\\ho* .

 Tuto složku Zaregistrujte pomocí tohoto klíče: **HKEY_LOCAL_MACHINE \software\microsoft\\. NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch\\** . Zadejte klíč tuto výchozí hodnotu: **C:\TreyResearch\Extensions4**.

> [!NOTE]
> Číslo buildu verze .NET Framework se může lišit.

 K registraci 32 sestavení na 64 počítači použijte uzel Wow6432, například: **HKEY_LOCAL_MACHINE \software\wow6432node\microsoft\\. NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch\\** .

### <a name="see-also"></a>Viz také:
- [Integrace sady Visual Studio](../msbuild/visual-studio-integration-msbuild.md)
