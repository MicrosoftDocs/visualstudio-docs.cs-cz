---
title: Řešení potíží s cílením na rozhraní .NET Framework | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.FrameworkTargetingErrors
- MSBuild.ResolveAssemblyReference.FailedToResolveReferenceBecausePrimaryAssemblyInExclusionList
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], .NET Framework Client Profile
- multi-targeting
- multitargeting
- .NET Framework Client Profile
ms.assetid: 830e3e45-9a93-4279-a249-75b84599aefb
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: acadd858a1327380fc606bed36994ba0dda47169
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49280550"
---
# <a name="troubleshooting-net-framework-targeting-errors"></a>Řešení potíží s cílením na rozhraní .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Toto téma popisuje chyby nástroje MSBuild, kterým by mohlo dojít z důvodu odkazu problémy a jak můžete tyto chyby vyřešili.  
  
## <a name="you-have-referenced-a-project-or-assembly-that-targets-a-different-version-of-the-net-framework"></a>Mít odkazuje na projekt nebo sestavení, který cílí na jinou verzi rozhraní .NET Framework  
 Můžete vytvářet aplikace, které odkazují na projekty nebo sestavení, které cílí různé verze [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Například můžete vytvořit aplikaci, která cílí na profil klienta [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] , ale odkazuje na sestavení, které cílí na rozhraní .NET Framework 2.0. Nicméně, pokud vytvoříte projekt, který cílí na dřívější verzi nástroje [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], nemůžete nastavit odkaz v daném projektu na projekt nebo sestavení, které cílí na profil klienta pro [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] nebo [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] samotný. Chcete-li chybu vyřešit, ujistěte se, že vaše aplikace cílí na profil, nebo profily, které jsou kompatibilní s profilem, která je cílem projekty nebo sestavení, na které odkazuje vaše aplikace.  
  
## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework"></a>Znovu jste zaměřili projekt na jinou verzi rozhraní .NET Framework  
 Pokud změníte cílovou verzi [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] pro vaši aplikaci Visual Studio změní některé z odkazů, ale možná budete muset ručně aktualizovat některé odkazy. Například některé z výše uvedených chyb může dojít, pokud změníte aplikace k cíli [!INCLUDE[net_v35SP1_long](../includes/net-v35sp1-long-md.md)] a že má prostředky nebo nastavení, které spoléhají na profil klienta pro aplikaci [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)].  
  
 Pokud chcete obejít nastavení aplikace, otevřete **Průzkumníka řešení**, zvolte **zobrazit všechny soubory**a potom upravte soubor app.config v editoru XML sady Visual Studio. Změňte verzi v nastavení tak, aby odpovídaly příslušnou verzi rozhraní .NET Framework. Například můžete změnit nastavení verze z 4.0.0.0 na 2.0.0.0. Podobně pro aplikaci, která se má přidat prostředky, otevřete **Průzkumníka řešení**, zvolte **zobrazit všechny soubory** tlačítko, rozbalte **Můj projekt** (Visual Basic) nebo **Vlastnosti** (C#) a pak upravte Resources.resx souboru v editoru XML sady Visual Studio. Změňte nastavení verze 2.0.0.0 z 4.0.0.0.  
  
 Pokud aplikace obsahuje prostředky, jako jsou ikony nebo rastrové obrázky nebo nastavení, jako je například připojovací řetězce dat, můžete také vyřešit chybu tak, že odeberete všechny položky na **nastavení** stránku **Návrháře projektu**a poté znovu přidejte požadovaná nastavení.  
  
## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework-and-references-do-not-resolve"></a>Znovu jste zaměřili projekt na jinou verzi rozhraní .NET Framework a odkazy nepřekládat  
 Pokud je výsledkem změny cílení projektu na jinou verzi [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], referencích nemůže vyřešit správně v některých případech. Explicitní plně kvalifikované odkazy na sestavení často způsobit potíže, ale ho mohli vyřešit odkazy, které nelze vyřešit odstraněním a jejich přidání do projektu. Jako alternativu můžete upravit soubor projektu a nahradit odkazy. Nejdřív odeberte odkazy na následující formu:  
  
```  
<Reference Include="System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089, processorArchitecture=MSIL" />  
```  
  
 Potom můžete nahradit je jednoduchý formulář:  
  
```  
<Reference Include="System.ServiceModel" />  
```  
  
> [!NOTE]
>  Po zavření a znovu otevřít projekt, měli byste také znovu vytvořit jej pro zajištění správně přeložit všechny odkazy.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: cílení na určitou verzi rozhraní .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md)   
 [Profil klienta .NET framework](http://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1)   
 [Cílení na konkrétní rozhraní .NET Framework verze](../ide/targeting-a-specific-dotnet-framework-version.md)   
 [Cílení na více verzí](../msbuild/msbuild-multitargeting-overview.md)



