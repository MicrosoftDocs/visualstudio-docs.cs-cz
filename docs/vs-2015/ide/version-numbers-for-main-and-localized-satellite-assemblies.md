---
title: Čísla verzí pro hlavní a lokalizovaná satelitní sestavení | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- satellite assemblies, version numbers
- SatelliteContractVersionAttribute
- version numbers, assemblies
- assemblies [Visual Studio], version numbers
- versioning, assemblies
ms.assetid: 5489aea1-57b4-4561-9bb4-24d490269602
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aa064d875d5354ac4ae1fc5fdd8493c5efbbee01
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663047"
---
# <a name="version-numbers-for-main-and-localized-satellite-assemblies"></a>Čísla verzí pro hlavní a lokalizované satelitní sestavení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

<xref:System.Resources.SatelliteContractVersionAttribute>Třída poskytuje podporu správy verzí pro hlavní sestavení, které používá lokalizované prostředky prostřednictvím Správce prostředků. Použití na <xref:System.Resources.SatelliteContractVersionAttribute> hlavní sestavení aplikace umožňuje aktualizovat a znovu nasadit sestavení bez aktualizace jeho satelitních sestavení. Můžete například použít <xref:System.Resources.SatelliteContractVersionAttribute> třídu s aktualizací Service Pack, která nezavádí nové prostředky bez nutnosti opětovného sestavení a opětovného nasazení satelitních sestavení. Aby byly lokalizované prostředky k dispozici, verze satelitního kontraktu vašeho hlavního sestavení musí odpovídat <xref:System.Reflection.AssemblyVersionAttribute> třídě vašich satelitních sestavení. Je nutné zadat přesné číslo verze v <xref:System.Resources.SatelliteContractVersionAttribute> ; zástupné znaky, například "*", nejsou povoleny. Další informace najdete v tématu [načtení prostředků](https://msdn.microsoft.com/library/eca16922-1c46-4f68-aefe-e7a12283641f).

## <a name="updating-assemblies"></a>Aktualizace sestavení
 <xref:System.Resources.SatelliteContractVersionAttribute>Třída umožňuje aktualizovat hlavní sestavení bez nutnosti aktualizovat satelitní sestavení, nebo naopak. Po aktualizaci hlavního sestavení je číslo jeho verze sestavení změněno. Chcete-li pokračovat v používání stávajících satelitních sestavení, změňte číslo verze hlavního sestavení, ale číslo verze satelitního kontraktu ponechte stejné. Například v první verzi může být hlavní verze sestavení 1.0.0.0. Verze satelitního kontraktu a verze sestavení satelitního sestavení budou také 1.0.0.0. Pokud potřebujete aktualizovat hlavní sestavení pro aktualizaci Service Pack, můžete změnit verzi sestavení na 1.0.0.1 a zároveň zachovat verzi satelitního kontraktu a verzi sestavení satelitu jako 1.0.0.0.

 Pokud potřebujete aktualizovat satelitní sestavení, ale ne vaše hlavní sestavení, změňte <xref:System.Reflection.AssemblyVersionAttribute> satelitní sestavení. Spolu se satelitním sestavením bude nutné dodávat sestavení zásad, které uvádí, že vaše nové satelitní sestavení je kompatibilní s vaším starým satelitním sestavením. Další informace o zásadách najdete v tématu [jak modul runtime vyhledává sestavení](https://msdn.microsoft.com/library/772ac6f4-64d2-4cfb-92fd-58096dcd6c34).

 Následující kód ukazuje, jak nastavit verzi satelitního kontraktu. Kód lze umístit buď do skriptu sestavení, nebo do souboru AssemblyInfo. vb nebo AssemblyInfo.cs.

```vb
<Assembly: SatelliteContractVersionAttribute("4.3.2.1")>

```

```csharp
[assembly: SatelliteContractVersionAttribute("4.3.2.1")]
```

## <a name="see-also"></a>Viz také
 [Způsob, jakým modul runtime vyhledává sestavení](https://msdn.microsoft.com/library/772ac6f4-64d2-4cfb-92fd-58096dcd6c34) [nastavení atributů sestavení](https://msdn.microsoft.com/library/36a98a81-b5b5-4c19-912a-11f91eff7f4e) [zabezpečení a lokalizovaná satelitní sestavení](../ide/security-and-localized-satellite-assemblies.md) [lokalizace](../ide/localizing-applications.md) [a lokalizace aplikací](../ide/globalizing-and-localizing-applications.md)
