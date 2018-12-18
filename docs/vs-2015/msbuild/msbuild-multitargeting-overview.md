---
title: Přehled cílení na více verzí nástroje MSBuild | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eecbcd65-9fbc-4307-a321-46d3c3b79b12
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da5d8d5aae19bee458a6d0750cb0d8cd4efa8c4d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49243816"
---
# <a name="msbuild-multitargeting-overview"></a>Přehled cílení na více verzí nástroje MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Pomocí nástroje MSBuild můžete zkompilovat aplikaci pro spuštění v jedné z několika verzí rozhraní .NET Framework a v jedné z několika platformách systému. Například můžete zkompilovat aplikaci pro spuštění v rozhraní .NET Framework 2.0 na 32bitové platformě a zkompilovat stejnou aplikaci spustit v rozhraní .NET Framework 4.5 na 64bitové platformě.  
  
> [!IMPORTANT]
>  Bez ohledu název "cílení na více verzí" můžete projekt cílit pouze jedno rozhraní a pouze jedné platformy najednou.  
  
 Toto jsou některé funkce cílí na MSBuild:  
  
-   Můžete vyvíjet aplikace, která se zaměřuje na starší verzi rozhraní .NET Framework, například verze 2.0, 3.5 nebo 4.  
  
-   Můžete cílit rozhraní než .NET Framework, například rozhraní Silverlight.  
  
-   Můžete cílit *profil rozhraní*, což je předdefinovaná podmnožina cílového rozhraní framework.  
  
-   Pokud bude vydána aktualizace service pack pro aktuální verzi rozhraní .NET Framework, může ji zaměřit.  
  
-   Cílení na MSBuild zaručuje, že aplikace používá pouze funkce, které jsou k dispozici v cíleného rozhraní a platformu.  
  
## <a name="target-framework-and-platform"></a>Cílové architektury a platformy  
 A *Cílová architektura* je verze rozhraní .NET Framework, která je vytvořená projekt spustit, a *cílovou platformu* je platforma systému sestavení ke spuštění v projektu.  Můžete například chtít cílová aplikace rozhraní .NET Framework 2.0 na 32bitové platformě, která je kompatibilní s 802 x 86 procesorů (x86) spuštění. Kombinace Cílová architektura a cílová platforma se označuje jako *cílový kontext*. Další informace najdete v tématu [Cílová architektura a cílová platforma](../msbuild/msbuild-target-framework-and-target-platform.md).  
  
## <a name="toolset-toolsversion"></a>Sada nástrojů (atribut ToolsVersion)  
 Sada nástrojů shromažďuje společně nástroje, úlohy a cíle, které se používají k vytvoření aplikace. Sada nástrojů obsahuje kompilátory jako csc.exe a vbc.exe, běžné souboru cíle (cílů microsoft.common.targets), a běžné úkoly souborů (microsoft.common.tasks). Rozhraní 4.5 sadu nástrojů lze použít na cílové rozhraní .NET Framework verze 2.0, 3.0, 3.5, 4 a 4.5. Ale 2.0 nástrojů jde použít jenom k cílení rozhraní .NET Framework verze 2.0. Další informace najdete v tématu [sada nástrojů (atribut ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md).  
  
## <a name="reference-assemblies"></a>Referenční sestavení  
 Referenční sestavení, které jsou uvedeny v sadu nástrojů můžete navrhovat a sestavovat aplikace. Tyto referenční sestavení jenom povolit konkrétní cíl sestavení, ale také na ty, které jsou kompatibilní s cílem omezit komponenty a funkce v integrovaném vývojovém prostředí sady Visual Studio. Další informace najdete v tématu [překlad sestavení v době návrhu](../msbuild/resolving-assemblies-at-design-time.md)  
  
## <a name="configuring-targets-and-tasks"></a>Konfigurace cílů a úloh  
 Můžete nakonfigurovat cíle nástroje MSBuild a aby úlohy běžely na více instancí procesu pomocí nástroje MSBuild tak, že je možné cílit na kontextu, které se značně liší než ten, který spustíte v.  Aplikace rozhraní .NET Framework 2.0 32-bit, například můžete cílit na 64bitové platformě s rozhraním .NET Framework 4.5 je spuštěn vývojovém počítači. Další informace najdete v tématu [konfigurace cílů a úloh](../msbuild/configuring-targets-and-tasks.md).  
  
## <a name="troubleshooting"></a>Poradce při potížích  
 Pokud se pokusíte k odkazování na sestavení, které není součástí cílový kontext, mohou se vyskytnout chyby. Další informace o těchto chyb a co dělat, o nich najdete v tématu [řešení chyb cílí na .NET Framework](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).



