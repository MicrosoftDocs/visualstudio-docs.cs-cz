---
title: Nástroj MSBuild Cílová architektura a cílová platforma | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: df6517c5-edd6-4cc4-97ad-b3cdfc78e799
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 74ca7eb25aac26eb66628ea76be502e4a244a2bd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49923365"
---
# <a name="msbuild-target-framework-and-target-platform"></a>Cílová architektura a cílová platforma nástroje MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Projekt se dají spouštět na *Cílová architektura*, což je konkrétní verzi rozhraní .NET Framework a *cílovou platformu*, což je zejména softwarovou architekturu.  Například můžete zacílit aplikaci pro spuštění v rozhraní .NET Framework 2.0 na 32bitové platformě, která je kompatibilní s 802 x 86 procesorů ("x86"). Kombinace Cílová architektura a cílová platforma se označuje jako *cílový kontext*.  
  
## <a name="target-framework-and-profile"></a>Cílové rozhraní Framework a profil  
 Je konkrétní verzi rozhraní .NET framework [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , který váš projekt se vytvořil pro spuštění na. Specifikace rozhraní .NET framework je povinné, protože umožňuje kompilátoru funkce a odkazy na sestavení, které jsou výhradně pro tuto verzi rozhraní framework.  
  
 V současné době jsou k dispozici pro použití následující verze rozhraní .NET Framework:  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 2.0 (zahrnutý v sadě Visual Studio 2005)  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 3.0 (součástí [!INCLUDE[wiprlhext](../includes/wiprlhext-md.md)])  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 3.5 (součástí [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)])  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 4 (zahrnutý v sadě Visual Studio 2010)  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 4.5 (součástí [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)])  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 4.5.1 (součástí [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)])  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 4.5.2  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 4.6 (součástí [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)])  
  
  Verze rozhraní .NET Framework v seznamu sestavení, že každý zpřístupní odkazovat navzájem liší. Například nelze sestavit aplikace Windows Presentation Foundation (WPF), pokud váš projekt cílí na rozhraní .NET Framework verze 3.0 nebo vyšší.  
  
  Cílová architektura, která je zadána v `TargetFrameworkVersion` vlastnost v souboru projektu. Pomocí stránky vlastností projektu v sadě Visual Studio integrované vývojové prostředí (IDE) můžete změnit cílový rámec pro projekt. Další informace najdete v tématu [postupy: cílení na určitou verzi rozhraní .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md). Dostupné hodnoty pro `TargetFrameworkVersion` jsou `v2.0`, `v3.0`, `v3.5`, `v4.0`, `v4.5`, `v4.5.1`, `v4.5.2`, a `v4.6`.  
  
```  
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>  
```  
  
 A *cílový profil* je podmnožinou rozhraní .NET framework. Profil klienta .NET Framework 4 například nezahrnuje odkazy na sestavení nástroje MSBuild.  
  
 Cílový profil určen ve `TargetFrameworkProfile` vlastnost v souboru projektu. Cílový profil můžete změnit pomocí ovládacího prvku cílovou architekturu na stránkách vlastností projektu v integrovaném vývojovém prostředí. Další informace najdete v tématu [postupy: cílení na určitou verzi rozhraní .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
```  
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>  
<TargetFrameworkProfile>Client</TargetFrameworkProfile>  
```  
  
## <a name="target-platform"></a>Cílová platforma  
 A *platformy* je kombinaci hardwaru a softwaru, který definuje konkrétní běhového prostředí. Například  
  
- `x86` Určuje 32bitová verze operačního systému Windows, který je spuštěn na procesoru Intel 80 x 86 nebo jeho ekvivalent.  
  
- `Xbox` Určuje platformu Microsoft Xbox 360.  
  
  A *cílovou platformu* je konkrétní platformu, kterou váš projekt se vytvořil pro spuštění na. Cílová platforma je zvolena v `Platform` vlastnost v souboru projektu sestavení. Pomocí stránky vlastností projektu můžete změnit cílovou platformu nebo **nástroje Configuration Manager** v integrovaném vývojovém prostředí.  
  
```  
<PropertyGroup>  
   <Platform>x86</Platform>  
</PropertyGroup>  
  
```  
  
 A *cílovou konfiguraci* je podmnožinou cílovou platformu. Například `x86``Debug` konfigurace nezahrnuje většiny optimalizací pro kód. Cílové konfigurace je určena v `Configuration` vlastnost v souboru projektu sestavení. Můžete změnit cílovou konfiguraci pomocí stránky vlastností projektu nebo **nástroje Configuration Manager**.  
  
```  
<PropertyGroup>  
   <Platform>x86</Platform>  
   <Configuration>Debug</Configuration>  
<PropertyGroup>  
  
```  
  
## <a name="see-also"></a>Viz také  
 [Cílení na více verzí](../msbuild/msbuild-multitargeting-overview.md)



