---
title: Přehled cílení na více verzí nástroje MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
ms.assetid: eecbcd65-9fbc-4307-a321-46d3c3b79b12
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f5b60f44dd1d32a9d19814b4d2194e7586d86865
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64784771"
---
# <a name="msbuild-multitargeting-overview"></a>Přehled cílení na více verzí nástroje MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocí nástroje MSBuild můžete zkompilovat aplikaci pro spuštění v libovolné z několika verzí .NET Framework a na některé z několika systémových platforem. Například můžete zkompilovat aplikaci pro spuštění na .NET Framework 2,0 na 32 platformě a zkompilovat stejnou aplikaci, která bude spuštěna na .NET Framework 4,5 64 na 64bitové platformě.  
  
> [!IMPORTANT]
> Navzdory názvu "cílení na více verzí" se projekt může zaměřit pouze na jedno rozhraní a vždy pouze na jednu platformu.  
  
 Jedná se o některé funkce cílení na MSBuild:  
  
- Můžete vyvíjet aplikaci, která cílí na starší verzi .NET Framework, například verze 2,0, 3,5 nebo 4.  
  
- Můžete cílit na jiné rozhraní než .NET Framework, například na rozhraní Silverlight.  
  
- Můžete cílit na *profil rozhraní*, což je předdefinovaná podmnožina cílové architektury.  
  
- Pokud se uvolní aktualizace Service Pack pro aktuální verzi .NET Framework, můžete na ni cílit.  
  
- Nástroj MSBuild cílí na to, že aplikace používá pouze funkce, které jsou k dispozici v cílovém rozhraní a platformě.  
  
## <a name="target-framework-and-platform"></a>Cílová architektura a platforma  
 *Cílová verze rozhraní .NET Framework* je verze .NET Framework, na které je projekt sestaven, a *cílová platforma* je systémovou platformou, na které je projekt sestaven.  Například můžete chtít cílit na aplikaci .NET Framework 2,0, která bude běžet na 32 platformě, která je kompatibilní s řadou procesorů 802x86 (x86). Kombinace cílového rozhraní a cílové platformy je označována jako *cílový kontext*. Další informace naleznete v tématu [Cílová architektura a cílová platforma](../msbuild/msbuild-target-framework-and-target-platform.md).  
  
## <a name="toolset-toolsversion"></a>Sada nástrojů (atribut ToolsVersion)  
 Sada nástrojů shromažďuje dohromady nástroje, úlohy a cíle, které se používají k vytvoření aplikace. Sada nástrojů obsahuje kompilátory, jako jsou csc.exe a vbc.exe, soubor Common TARGETS (Microsoft. Common. targets) a soubor běžné úlohy (Microsoft. Common. Tasks). Sadu nástrojů 4,5 lze použít k cílení na .NET Framework verze 2,0, 3,0, 3,5, 4 a 4,5. Sada nástrojů 2,0 se ale dá použít jenom k cílení na verzi .NET Framework 2,0. Další informace najdete v tématu [Sada nástrojů (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md).  
  
## <a name="reference-assemblies"></a>Referenční sestavení  
 Referenční sestavení, která jsou uvedena v sadě nástrojů, vám pomohou navrhovat a sestavovat aplikace. Tato referenční sestavení nepovolují pouze konkrétní cílové sestavení, ale také omezují komponenty a funkce v integrovaném vývojovém prostředí sady Visual Studio na ty, které jsou kompatibilní s cílem. Další informace naleznete v tématu [řešení sestavení v době návrhu](../msbuild/resolving-assemblies-at-design-time.md) .  
  
## <a name="configuring-targets-and-tasks"></a>Konfigurace cílů a úloh  
 Cíle a úlohy nástroje MSBuild můžete nakonfigurovat tak, aby běžely mimo proces s nástrojem MSBuild, abyste mohli cílit na kontexty, které jsou výrazně jiné než ten, na kterém je spuštěný.  Můžete například cílit na 32, .NET Framework 2,0 aplikace, zatímco vývojový počítač běží na platformě 64 s .NET Framework 4,5. Další informace najdete v tématu [Konfigurace cílů a úloh](../msbuild/configuring-targets-and-tasks.md).  
  
## <a name="troubleshooting"></a>Řešení potíží  
 Při pokusu o odkaz na sestavení, které není součástí cílového kontextu, může dojít k chybám. Další informace o těchto chybách a o tom, co s nimi dělat, najdete v tématu [řešení potíží s chybami cílení .NET Framework](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).
