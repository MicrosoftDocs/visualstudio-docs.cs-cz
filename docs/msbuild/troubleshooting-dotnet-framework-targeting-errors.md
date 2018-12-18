---
title: Řešení potíží s cílením na rozhraní .NET Framework | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: troubleshooting
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: bd1d899d3b3a84af2b07602b959dd031874e972c
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/19/2018
ms.locfileid: "39155448"
---
# <a name="troubleshoot-net-framework-targeting-errors"></a>Řešení potíží s cílením na rozhraní .NET Framework
Toto téma popisuje chyby nástroje MSBuild, kterým by mohlo dojít z důvodu odkazu problémy a jak můžete tyto chyby vyřešili.  
  
## <a name="you-have-referenced-a-project-or-assembly-that-targets-a-different-version-of-the-net-framework"></a>Mít odkazuje na projekt nebo sestavení, který cílí na jinou verzi rozhraní .NET Framework  
 Můžete vytvářet aplikace, které odkazují na projekty nebo sestavení, které cílí různé verze [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Například můžete vytvořit aplikaci, která cílí na profil klienta [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] , ale odkazuje na sestavení, které cílí na rozhraní .NET Framework 2.0. Nicméně, pokud vytvoříte projekt, který cílí na dřívější verzi nástroje [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], nemůžete nastavit odkaz v daném projektu na projekt nebo sestavení, které cílí na profil klienta pro [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] nebo [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] samotný. Chcete-li chybu vyřešit, ujistěte se, že vaše aplikace cílí na profil, nebo profily, které jsou kompatibilní s profilem, která je cílem projekty nebo sestavení, na které odkazuje vaše aplikace.  
  
## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework"></a>Znovu jste zaměřili projekt na jinou verzi rozhraní .NET Framework  
 Pokud změníte cílovou verzi [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] pro vaši aplikaci Visual Studio změní některé z odkazů, ale možná budete muset ručně aktualizovat některé odkazy. Například některé z výše uvedených chyb může dojít, pokud změníte aplikace k cíli [!INCLUDE[net_v35SP1_long](../msbuild/includes/net_v35sp1_long_md.md)] a že má prostředky nebo nastavení, které spoléhají na profil klienta pro aplikaci [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)].  
  
 Pokud chcete obejít nastavení aplikace, otevřete **Průzkumníka řešení**, zvolte **zobrazit všechny soubory**a pak upravte *app.config* souboru v editoru XML sady Visual Studio. Změňte verzi v nastavení tak, aby odpovídaly příslušnou verzi rozhraní .NET Framework. Například můžete změnit nastavení verze z 4.0.0.0 na 2.0.0.0. Podobně pro aplikaci, která se má přidat prostředky, otevřete **Průzkumníka řešení**, zvolte **zobrazit všechny soubory** tlačítko, rozbalte **Můj projekt** (Visual Basic) nebo **Vlastnosti** (C#) a pak upravte *Resources.resx* souboru v editoru XML sady Visual Studio. Změňte nastavení verze 2.0.0.0 z 4.0.0.0.  
  
 Pokud aplikace obsahuje prostředky, jako jsou ikony nebo rastrové obrázky nebo nastavení, jako je například připojovací řetězce dat, můžete také vyřešit chybu tak, že odeberete všechny položky na **nastavení** stránku **Návrháře projektu**a poté znovu přidejte požadovaná nastavení.  
  
## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework-and-references-do-not-resolve"></a>Znovu jste zaměřili projekt na jinou verzi rozhraní .NET Framework a odkazy nepřekládat  
 Pokud je výsledkem změny cílení projektu na jinou verzi [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], referencích nemůže vyřešit správně v některých případech. Explicitní plně kvalifikované odkazy na sestavení často způsobit potíže, ale ho mohli vyřešit odkazy, které nelze vyřešit odstraněním a jejich přidání do projektu. Jako alternativu můžete upravit soubor projektu a nahradit odkazy. Nejdřív odeberte odkazy na následující formu:  
  
```xml  
<Reference Include="System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089, processorArchitecture=MSIL" />  
```  
  
 Potom můžete nahradit je jednoduchý formulář:  
  
```xml  
<Reference Include="System.ServiceModel" />  
```  
  
> [!NOTE]
>  Po zavření a znovu otevřít projekt, měli byste také znovu vytvořit jej pro zajištění správně přeložit všechny odkazy.  
  
## <a name="see-also"></a>Viz také:  
 [Postupy: cílení na určitou verzi rozhraní .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md)   
 [Profil klienta rozhraní .NET framework](/dotnet/framework/deployment/client-profile)   
 [Cílení na konkrétní verzi rozhraní .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md)   
 [Cílení na více verzí](../msbuild/msbuild-multitargeting-overview.md)