---
title: Cílová architektura a cílová platforma nástroje MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
ms.assetid: df6517c5-edd6-4cc4-97ad-b3cdfc78e799
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1a550b4a6634604594da0893e3f420fd9c38ca3c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68181040"
---
# <a name="msbuild-target-framework-and-target-platform"></a>Cílová architektura a cílová platforma nástroje MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Projekt může být sestaven pro spuštění na *cílovém rozhraní*, což je konkrétní verze .NET Framework a *cílovou platformu*, která je konkrétní softwarovou architekturou.  Můžete například cílit na aplikaci tak, aby běžela na .NET Framework 2,0 na 32 platformě, která je kompatibilní s řadou procesorů 802x86 (x86). Kombinace cílového rozhraní a cílové platformy je označována jako *cílový kontext*.  
  
## <a name="target-framework-and-profile"></a>Cílová architektura a profil  
 Cílová architektura je konkrétní verze [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , na kterou je projekt sestaven, aby běžel. Specifikace cílové architektury je povinná, protože umožňuje funkce kompilátoru a odkazy na sestavení, které jsou výhradně pro tuto verzi rozhraní.  
  
 V současné době jsou k dispozici následující verze .NET Framework pro použití:  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]2,0 (obsaženo v aplikaci Visual Studio 2005)  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]3,0 (zahrnuto v [!INCLUDE[wiprlhext](../includes/wiprlhext-md.md)] )  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]3,5 (zahrnuto v [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)] )  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]4 (zahrnuté v aplikaci Visual Studio 2010)  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]4,5 (zahrnuto v [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] )  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]4.5.1 (zahrnutý v [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] )  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]4.5.2  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]4,6 (zahrnuto v [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] )  
  
  Verze .NET Framework se od sebe liší v seznamu sestavení, která jsou dostupná pro referenci. Například nemůžete sestavovat aplikace Windows Presentation Foundation (WPF), pokud projekt necílí na .NET Framework verze 3,0 nebo vyšší.  
  
  Cílová architektura je určena ve `TargetFrameworkVersion` vlastnosti v souboru projektu. Cílovou architekturu projektu můžete změnit pomocí stránky vlastností projektu v integrovaném vývojovém prostředí (IDE) sady Visual Studio. Další informace najdete v tématu [Postup: cílení na verzi .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md). Dostupné hodnoty pro `TargetFrameworkVersion` jsou `v2.0` ,,,, `v3.0` `v3.5` `v4.0` `v4.5` ,, a `v4.5.1` `v4.5.2` `v4.6` .  
  
```  
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>  
```  
  
 *Cílový profil* je podmnožinou cílového rozhraní. Například profil klienta .NET Framework 4 neobsahuje odkazy na sestavení nástroje MSBuild.  
  
 Cílový profil je zadán ve `TargetFrameworkProfile` vlastnosti v souboru projektu. Cílový profil můžete změnit pomocí ovládacího prvku cílový – rozhraní na stránkách vlastností projektu v rozhraní IDE. Další informace najdete v tématu [Postup: cílení na verzi .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
```  
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>  
<TargetFrameworkProfile>Client</TargetFrameworkProfile>  
```  
  
## <a name="target-platform"></a>Cílová platforma  
 *Platforma* je kombinací hardwaru a softwaru, který definuje konkrétní běhové prostředí. Příklad:  
  
- `x86` Určuje 32 operační systém Windows, který běží na procesoru Intel 80x86 nebo jeho ekvivalent.  
  
- `Xbox` označuje platformu Microsoft Xbox 360.  
  
  *Cílová platforma* je konkrétní platforma, na které je projekt sestaven. Cílová platforma je určena ve `Platform` vlastnosti Build v souboru projektu. Cílovou platformu můžete změnit pomocí stránky vlastností projektu nebo **Configuration Manager** v integrovaném vývojovém prostředí.  
  
```  
<PropertyGroup>  
   <Platform>x86</Platform>  
</PropertyGroup>  
  
```  
  
 *Cílová konfigurace* je podmnožinou cílové platformy. Například `x86``Debug` konfigurace nezahrnuje většinu optimalizací kódu. Cílová konfigurace je určena ve `Configuration` vlastnosti Build v souboru projektu. Cílovou konfiguraci můžete změnit pomocí stránky vlastností projektu nebo **Configuration Manager**.  
  
```  
<PropertyGroup>  
   <Platform>x86</Platform>  
   <Configuration>Debug</Configuration>  
<PropertyGroup>  
  
```  
  
## <a name="see-also"></a>Viz také  
 [Cílení na více verzí](../msbuild/msbuild-multitargeting-overview.md)
