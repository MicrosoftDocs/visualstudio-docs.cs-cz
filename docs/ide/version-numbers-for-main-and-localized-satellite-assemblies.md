---
title: Čísla verzí pro hlavní a lokalizované satelitní sestavení
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- satellite assemblies, version numbers
- SatelliteContractVersionAttribute
- version numbers, assemblies
- assemblies [Visual Studio], version numbers
- versioning, assemblies
ms.assetid: 5489aea1-57b4-4561-9bb4-24d490269602
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cbc74d746453c5d8e60161004a5b56a2c21915dd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49882592"
---
# <a name="version-numbers-for-main-and-localized-satellite-assemblies"></a>Čísla verzí pro hlavní a lokalizované satelitní sestavení
<xref:System.Resources.SatelliteContractVersionAttribute> Třída poskytuje podporu správy verzí pro hlavní sestavení, které používá lokalizované prostředky prostřednictvím Resource Manageru. Použití <xref:System.Resources.SatelliteContractVersionAttribute> k aplikaci hlavní sestavení umožňuje aktualizace a opětovné nasazení sestavení bez aktualizace jeho satelitních sestavení. Například můžete použít <xref:System.Resources.SatelliteContractVersionAttribute> třídy s aktualizací service pack, který nemá zavést nové prostředky bez znovu sestavovat a nasazovat satelitních sestavení. Pro lokalizované prostředky k dispozici, musí odpovídat verze satelitního kontraktu sestavení hlavní <xref:System.Reflection.AssemblyVersionAttribute> třídy satelitních sestavení. Zadejte číslo verze přesně v <xref:System.Resources.SatelliteContractVersionAttribute>; zástupné znaky, jako "*" nejsou povoleny. Další informace najdete v tématu [načíst prostředky](/dotnet/framework/resources/retrieving-resources-in-desktop-apps).

## <a name="update-assemblies"></a>Aktualizovat sestavení
 <xref:System.Resources.SatelliteContractVersionAttribute> Třída umožňuje aktualizovat bez nutnosti aktualizovat satelitní sestavení do hlavního sestavení nebo naopak. Když se aktualizuje hlavní sestavení, číslo verze sestavení se změní. Pokud chcete pokračovat v používání existujícího satelitní sestavení, změňte číslo verze hlavní sestavení, ale ponechat stejné číslo verze satelitního kontraktu. Například v první verzi může být vaše hlavní sestavení verze 1.0.0.0. Verze satelitního kontraktu sestavení verzi satelitního sestavení také to 1.0.0.0. Pokud je potřeba aktualizovat vaše hlavní sestavení pro aktualizace service pack, můžete změnit verzi sestavení 1.0.0.1, při zachování verze satelitního kontraktu a verze pro satelitní sestavení jako 1.0.0.0.

 Pokud je potřeba aktualizovat satelitní sestavení, ale není hlavním sestavení, můžete změnit <xref:System.Reflection.AssemblyVersionAttribute> satelitní sestavení. Spolu se satelitním sestavením bude mít k odeslání zásady sestavení, která uvádí, že vaše nové satelitní sestavení je kompatibilní s původní satelitní sestavení. Další informace o zásadách najdete v tématu [jak běhové prostředí vyhledává sestavení](/dotnet/framework/deployment/how-the-runtime-locates-assemblies).

 Následující kód ukazuje, jak nastavit verze satelitního kontraktu. Kód je možné použít ve skriptu sestavení nebo v *AssemblyInfo.vb* nebo *AssemblyInfo.cs* souboru.

```vb
<Assembly: SatelliteContractVersionAttribute("4.3.2.1")>
```

```csharp
[assembly: SatelliteContractVersionAttribute("4.3.2.1")]
```

## <a name="see-also"></a>Viz také:

- [Jak běhové prostředí vyhledává sestavení](/dotnet/framework/deployment/how-the-runtime-locates-assemblies)
- [Nastavení atributů sestavení](/dotnet/framework/app-domains/set-assembly-attributes)
- [Zabezpečení a lokalizovaná satelitní sestavení](../ide/security-and-localized-satellite-assemblies.md)
- [Lokalizace aplikací](../ide/localizing-applications.md)
- [Globalizace a lokalizace aplikací](../ide/globalizing-and-localizing-applications.md)