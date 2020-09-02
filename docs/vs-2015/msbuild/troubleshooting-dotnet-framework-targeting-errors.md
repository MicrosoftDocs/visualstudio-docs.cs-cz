---
title: Řešení potíží s chybami cílení .NET Framework | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ae55e34f929acca6c708dfc39477f3bd6546f53f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703788"
---
# <a name="troubleshooting-net-framework-targeting-errors"></a>Řešení potíží s cílením na rozhraní .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma popisuje chyby nástroje MSBuild, ke kterým může dojít kvůli problémům s referencí a o tom, jak tyto chyby vyřešit.  
  
## <a name="you-have-referenced-a-project-or-assembly-that-targets-a-different-version-of-the-net-framework"></a>Odkazovali jste na projekt nebo sestavení, které cílí na jinou verzi .NET Framework  
 Můžete vytvářet aplikace, které odkazují na projekty nebo sestavení, které cílí na různé verze [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . Můžete například vytvořit aplikaci, která cílí na profil klienta pro, [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] ale odkazuje na sestavení, které cílí na .NET Framework 2,0. Nicméně pokud vytvoříte projekt, který se zaměřuje na starší verzi [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , nemůžete nastavit odkaz v tomto projektu na projekt nebo sestavení, které cílí na profil klienta pro [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] nebo [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] samotný. Pokud chcete chybu vyřešit, ujistěte se, že vaše aplikace cílí na profil nebo profily, které jsou kompatibilní s profilem, který cílí na projekty nebo sestavení, na které vaše aplikace odkazuje.  
  
## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework"></a>Přesměrovali jste projekt na jinou verzi .NET Framework  
 Pokud změníte cílovou verzi [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] aplikace, Visual Studio změní některé odkazy, ale možná budete muset některé odkazy aktualizovat ručně. Například jedna z výše zmíněných chyb může nastat, pokud změníte aplikaci na cílovou [!INCLUDE[net_v35SP1_long](../includes/net-v35sp1-long-md.md)] a tato aplikace má prostředky nebo nastavení závislé na profilu klienta pro [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] .  
  
 Chcete-li pracovat s nastavením aplikace, otevřete **Průzkumník řešení**, zvolte možnost **Zobrazit všechny soubory**a pak upravte soubor app.config v editoru XML sady Visual Studio. Změňte verzi v nastavení tak, aby odpovídala příslušné verzi .NET Framework. Například můžete změnit nastavení verze z 4.0.0.0 na 2.0.0.0. Podobně pro aplikaci, která má přidané prostředky, otevřete **Průzkumník řešení**, zvolte tlačítko **Zobrazit všechny soubory** , rozbalte **můj projekt** (Visual Basic) nebo **vlastnosti** (C#) a pak upravte soubor Resources. resx v editoru XML aplikace Visual Studio. Změňte nastavení verze z 4.0.0.0 na 2.0.0.0.  
  
 Pokud má vaše aplikace prostředky, jako jsou ikony nebo rastrové obrázky nebo nastavení, například řetězce datových připojení, můžete také vyřešit chybu odebráním všech položek na stránce **Nastavení** **Návrháře projektu** a pak znovu přidat požadovaná nastavení.  
  
## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework-and-references-do-not-resolve"></a>Přesměrovali jste projekt na jinou verzi .NET Framework a odkazy nebudou přeloženy  
 Pokud změníte cíl projektu na jinou verzi [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , odkazy se v některých případech nemusí správně vyřešit. Explicitní plně kvalifikované odkazy na sestavení často způsobují tento problém, ale lze je vyřešit odebráním odkazů, které se nevyřeší a následně jejich přidáním zpět do projektu. Alternativně můžete upravit soubor projektu a nahradit tak odkazy. Nejprve odeberte odkazy z tohoto formuláře:  
  
```  
<Reference Include="System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089, processorArchitecture=MSIL" />  
```  
  
 Pak je nahradíte jednoduchým formulářem:  
  
```  
<Reference Include="System.ServiceModel" />  
```  
  
> [!NOTE]
> Po zavření a opětovném otevření projektu byste ho měli také znovu sestavit, aby se zajistilo správné řešení všech odkazů.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: cílení na verzi .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md)   
 [.NET Framework profil klienta](https://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1)   
 [Cílení na konkrétní verzi .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md)   
 [Cílení na více verzí](../msbuild/msbuild-multitargeting-overview.md)
