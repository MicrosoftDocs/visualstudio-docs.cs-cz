---
title: Co&#39;s novinkou v MSBuild 12,0 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
ms.assetid: 9976a6ad-c052-4017-b848-35b5ae4a2f66
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ba733b7ef20c9a03ad19d9847a4046e4d72ebdef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75844458"
---
# <a name="what39s-new-in-msbuild-120"></a>Co&#39;s novinkou v MSBuild 12,0
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nástroj MSBuild je nyní nainstalován jako součást sady Visual Studio, nikoli jako součást .NET Framework. Aktuální číslo verze nástroje MSBuild je 12,0. Pokud chcete nástroj MSBuild nainstalovat samostatně, Stáhněte instalační balíček z nástroje [MSBuild stáhnout](https://www.microsoft.com/download/details.aspx?id=40760).  
  
## <a name="changed-path"></a>Změněná cesta  
 Nástroj MSBuild je nyní nainstalován přímo pod *% ProgramFiles%*– například v adresáři C:\Program Files\MSBuild \\ .  
  
## <a name="changed-properties"></a>Změněné vlastnosti  
 Následující vlastnosti nástroje MSBuild se změní v důsledku nového čísla verze:  
  
- `MSBuildToolsVersion` pro tuto verzi nástrojů je to 12,0.  
  
- `MSBuildToolsPath` Teď se%ProgramFiles%\MSBuild\12.0\bin na 32 operačních systémů nebo%ProgramFiles%\MSBuild\12.0\bin\amd64 na 64 operačních systémech.  
  
- `ToolsVersion` hodnoty najdete v HKLM\SOFTWARE\Microsoft\MSBuild\ToolsVersions\12.0 pro 32 operační systémy nebo HKLM\SOFTWARE\Wow6432Node\Microsoft\MSBuild\ToolsVersions\12.0 pro 64 operační systémy.  
  
- `SDK35ToolsPath`Vlastnosti a `SDK40ToolsPath` odkazují na sadu .NET Framework SDK, která je zabalena s touto verzí sady Visual Studio (například 8.1 a pro nástroje 4. X).  
  
## <a name="new-properties"></a>Nové vlastnosti  
  
- `MSBuildFrameworkToolsPath` je nová vlastnost, která má hodnotu%windir%\Microsoft.NET\Framework\v4.0.30319 v 32 operačních systémech nebo%windir%\Microsoft.NET\Framework64\v4.0.30319 v 64 operačních systémech. Tato náhrada je náhradou `MSBuildToolsPath` , kterou lze použít k ukázání na .NET Framework nástroje a pomůcky.  
  
- `MSBuildToolsPath` a `MSBuildFrameworkToolsPath` mají 32 ekvivalenty – `MSBuildToolsPath32` a `MSBuildFrameworkToolsPath32` , které vždy odkazují na 32 umístění, bez ohledu na to, jestli se používá 32-bit 64 nebo 16bitový MSBuild.

## <a name="see-also"></a>Viz také
[Nástroji](msbuild.md)
