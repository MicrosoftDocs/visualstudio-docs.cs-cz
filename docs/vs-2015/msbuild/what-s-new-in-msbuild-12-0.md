---
title: Co&#39;je nového v MSBuild 12,0 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
ms.assetid: 9976a6ad-c052-4017-b848-35b5ae4a2f66
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9d088844a3d8c1137b762b541b0393f939cdc194
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301288"
---
# <a name="what39s-new-in-msbuild-120"></a>Co&#39;je nového v MSBuild 12,0
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nástroj MSBuild je nyní nainstalován jako součást sady Visual Studio, nikoli jako součást .NET Framework. Aktuální číslo verze nástroje MSBuild je 12,0. Pokud chcete nástroj MSBuild nainstalovat samostatně, Stáhněte instalační balíček z nástroje [MSBuild stáhnout](https://go.microsoft.com/fwlink/?LinkId=309745).  
  
## <a name="changed-path"></a>Změněná cesta  
 Nástroj MSBuild je nyní nainstalován přímo pod *% ProgramFiles%* , například v adresáři C:\Program Files\MSBuild\\.  
  
## <a name="changed-properties"></a>Změněné vlastnosti  
 Následující vlastnosti nástroje MSBuild se změní v důsledku nového čísla verze:  
  
- `MSBuildToolsVersion` pro tuto verzi nástrojů je 12,0.  
  
- `MSBuildToolsPath` se teď%ProgramFiles%\MSBuild\12.0\bin na 32 operačních systémů nebo%ProgramFiles%\MSBuild\12.0\bin\amd64 na 64 operačních systémech.  
  
- hodnoty `ToolsVersion` najdete v HKLM\SOFTWARE\Microsoft\MSBuild\ToolsVersions\12.0 pro 32 operační systémy nebo HKLM\SOFTWARE\Wow6432Node\Microsoft\MSBuild\ToolsVersions\12.0 pro 64 operační systémy.  
  
- Vlastnosti `SDK35ToolsPath` a `SDK40ToolsPath` odkazují na sadu .NET Framework SDK, která je zabalena s touto verzí sady Visual Studio (například 8.1 A pro nástroje 4. X).  
  
## <a name="new-properties"></a>Nové vlastnosti  
  
- `MSBuildFrameworkToolsPath` je nová vlastnost, která má hodnotu%windir%\Microsoft.NET\Framework\v4.0.30319 v 32 operačních systémech nebo%windir%\Microsoft.NET\Framework64\v4.0.30319 v 64 operačních systémech. Toto je náhrada za `MSBuildToolsPath`, kterou lze použít k odkazování na .NET Framework nástroje a pomůcky.  
  
- `MSBuildToolsPath` a `MSBuildFrameworkToolsPath` mají 32 ekvivalenty (`MSBuildToolsPath32` a `MSBuildFrameworkToolsPath32`), které vždy odkazují na 32 umístění, bez ohledu na to, jestli se používá 32-bit 64 nebo 16bitový MSBuild.

## <a name="see-also"></a>Viz také
[MSBuild](msbuild.md)
