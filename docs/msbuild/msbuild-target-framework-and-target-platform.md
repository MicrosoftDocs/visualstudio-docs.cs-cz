---
title: Nástroj MSBuild Cílová architektura a cílová platforma | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
ms.assetid: df6517c5-edd6-4cc4-97ad-b3cdfc78e799
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bfb45efc199ea1f643c71bdc19a90862bb6c5dd6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49916059"
---
# <a name="msbuild-target-framework-and-target-platform"></a>MSBuild cílová rozhraní framework a cílová platforma
Projekt se dají spouštět na *Cílová architektura*, což je konkrétní verzi rozhraní .NET Framework a *cílovou platformu*, což je zejména softwarovou architekturu.  Například můžete zacílit aplikaci pro spuštění v rozhraní .NET Framework 2.0 na 32bitové platformě, která je kompatibilní s 802 x 86 procesorů ("x86"). Kombinace Cílová architektura a cílová platforma se označuje jako *cílový kontext*.  
  
## <a name="target-framework-and-profile"></a>Cílové rozhraní framework a profil  
 Je konkrétní verzi rozhraní .NET framework [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] , který váš projekt se vytvořil pro spuštění na. Specifikace rozhraní .NET framework je povinné, protože umožňuje kompilátoru funkce a odkazy na sestavení, které jsou výhradně pro tuto verzi rozhraní framework.  
  
 V současné době jsou k dispozici pro použití následující verze rozhraní .NET Framework:  
  
- [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 2.0 (zahrnutý v sadě Visual Studio 2005)  
  
- [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 3.0 (součástí [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)])  
  
- [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 3.5 (součástí [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)])  
  
- [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.5.2  
  
- [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.6 (součástí [!INCLUDE[vs_dev14](../misc/includes/vs_dev14_md.md)])  

- [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.6.1  

- [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.6.2  

- [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.7  

- [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.7.1  

Verze rozhraní .NET Framework v seznamu sestavení, že každý zpřístupní odkazovat navzájem liší. Například nelze sestavit aplikace Windows Presentation Foundation (WPF), pokud váš projekt cílí na rozhraní .NET Framework verze 3.0 nebo vyšší.  

Cílová architektura, která je zadána v `TargetFrameworkVersion` vlastnost v souboru projektu. Pomocí stránky vlastností projektu v sadě Visual Studio integrované vývojové prostředí (IDE) můžete změnit cílový rámec pro projekt. Další informace najdete v tématu [postupy: cílení na určitou verzi rozhraní .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md). Dostupné hodnoty pro `TargetFrameworkVersion` jsou `v2.0`, `v3.0`, `v3.5`, `v4.5.2`, `v4.6`, `v4.6.1`, `v4.6.2`, `v4.7`, a `v4.7.1`.  
  
```xml  
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>  
```  
  
 A *cílový profil* je podmnožinou rozhraní .NET framework. Profil klienta .NET Framework 4 například nezahrnuje odkazy na sestavení nástroje MSBuild.  
  
 Cílový profil určen ve `TargetFrameworkProfile` vlastnost v souboru projektu. Cílový profil můžete změnit pomocí ovládacího prvku cílovou architekturu na stránkách vlastností projektu v integrovaném vývojovém prostředí. Další informace najdete v tématu [postupy: cílení na určitou verzi rozhraní .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
```xml  
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>  
<TargetFrameworkProfile>Client</TargetFrameworkProfile>  
```  
  
## <a name="target-platform"></a>Cílová platforma  
 A *platformy* je kombinaci hardwaru a softwaru, který definuje konkrétní běhového prostředí. Například  
  
-   `x86` Určuje 32bitová verze operačního systému Windows, který je spuštěn na procesoru Intel 80 x 86 nebo jeho ekvivalent.  

-   `x64` Určuje 64bitová verze operačního systému Windows, který je spuštěn na procesoru Intel x64 nebo jeho ekvivalent.
  
-   `Xbox` Určuje platformu Microsoft Xbox 360.  

A *cílovou platformu* je konkrétní platformu, kterou váš projekt se vytvořil pro spuštění na. Cílová platforma je zvolena v `PlatformTarget` vlastnost v souboru projektu sestavení. Pomocí stránky vlastností projektu můžete změnit cílovou platformu nebo **nástroje Configuration Manager** v integrovaném vývojovém prostředí.  

```xml  
<PropertyGroup>  
   <PlatformTarget>x86</PlatformTarget>  
</PropertyGroup>  

```  

A *cílovou konfiguraci* je podmnožinou cílovou platformu. Například `x86``Debug` konfigurace nezahrnuje většiny optimalizací pro kód. Cílové konfigurace je určena v `Configuration` vlastnost v souboru projektu sestavení. Můžete změnit cílovou konfiguraci pomocí stránky vlastností projektu nebo **nástroje Configuration Manager**.  

```xml  
<PropertyGroup>  
   <PlatformTarget>x86</PlatformTarget>  
   <Configuration>Debug</Configuration>  
<PropertyGroup>  
  
```  

## <a name="see-also"></a>Viz také:  
 [Cílení na více verzí](../msbuild/msbuild-multitargeting-overview.md)
