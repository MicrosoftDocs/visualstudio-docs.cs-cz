---
title: Poradce při potížích s chybami cílení rozhraní .NET Framework | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 1c496fd457e80220bb2ea4a2f032cef9508d9dcb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631598"
---
# <a name="troubleshoot-net-framework-targeting-errors"></a>Poradce při potížích s chybami cílení rozhraní .NET Framework

Toto téma popisuje chyby MSBuild, ke kterým může dojít z důvodu problémů s odkazy a jak je lze vyřešit.

## <a name="you-have-referenced-a-project-or-assembly-that-targets-a-different-version-of-the-net-framework"></a>Odkazovali jste na projekt nebo sestavení, které cílí na jinou verzi rozhraní .NET Framework.

 Můžete vytvořit aplikace, které odkazují na projekty nebo sestavení, které cílí na různé verze rozhraní .NET Framework. Můžete například vytvořit aplikaci, která cílí na profil klienta pro rozhraní .NET Framework 4, ale odkazuje na sestavení, které se zaměřuje na rozhraní .NET Framework 2.0. Pokud však vytvoříte projekt, který cílí na starší verzi rozhraní .NET Framework, nelze v tomto projektu nastavit odkaz na projekt nebo sestavení, které cílí na profil klienta pro rozhraní .NET Framework 4 nebo rozhraní .NET Framework 4. Chcete-li chybu vyřešit, ujistěte se, že vaše aplikace cílí na profil nebo profily, které jsou kompatibilní s profilem, na který cílí projekty nebo sestavení, na které vaše aplikace odkazuje.

## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework"></a>Přeřadili jste projekt na jinou verzi rozhraní .NET Framework.

 Pokud změníte cílovou verzi rozhraní .NET Framework pro vaši aplikaci, Visual Studio změní některé odkazy, ale bude pravděpodobně nutné aktualizovat některé odkazy ručně. Například jedna z výše uvedených chyb může dojít, pokud změníte aplikaci na cílovou rozhraní .NET Framework 3.5 Service Pack 1 a tato aplikace má prostředky nebo nastavení, které jsou závislé na profilu klienta pro rozhraní .NET Framework 4.

 Chcete-li obejít nastavení aplikace, otevřete **Průzkumníka řešení**, zvolte **Zobrazit všechny soubory**a upravte soubor *app.config* v editoru XML sady Visual Studio. Změňte verzi v nastavení tak, aby odpovídala příslušné verzi rozhraní .NET Framework. Můžete například změnit nastavení verze z 4.0.0.0 na 2.0.0.0. Podobně pro aplikaci, která přidala prostředky, otevřete **Průzkumníka řešení**, zvolte tlačítko **Zobrazit všechny soubory,** **rozbalte můj projekt** (Visual Basic) nebo **vlastnosti** (C#) a upravte soubor *Resources.resx* v editoru XML sady Visual Studio. Změňte nastavení verze z 4.0.0.0 na 2.0.0.0.

 Pokud vaše aplikace obsahuje prostředky, jako jsou ikony nebo rastrové mapy nebo nastavení, jako jsou řetězce připojení dat, můžete chybu také vyřešit odebráním všech položek na stránce **Nastavení** **návrháře projektu** a opětovným přidáním požadovaných nastavení.

## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework-and-references-do-not-resolve"></a>Přecílili jste projekt na jinou verzi rozhraní .NET Framework a odkazy neřeší

 Pokud znovu zacílíte projekt na jinou verzi rozhraní .NET Framework, odkazy nemusí správně vyřešit v některých případech. Explicitní plně kvalifikované odkazy na sestavení často způsobit tento problém, ale můžete jej vyřešit odebráním odkazy, které nelze vyřešit a potom je přidat zpět do projektu. Jako alternativu můžete upravit soubor projektu a nahradit odkazy. Nejprve odeberete odkazy na následující formulář:

```xml
<Reference Include="System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089, processorArchitecture=MSIL" />
```

 Pak je nahradíte jednoduchým formulářem:

```xml
<Reference Include="System.ServiceModel" />
```

> [!NOTE]
> Po zavření a opětovném otevření projektu byste jej měli také znovu sestavit, abyste zajistili, že všechny odkazy budou správně řešit.

## <a name="see-also"></a>Viz také

- [Postup: Cílení na verzi rozhraní .NET Framework](../ide/visual-studio-multi-targeting-overview.md)
- [Profil klienta rozhraní .NET Framework](/dotnet/framework/deployment/client-profile)
- [Přehled cílení na rozhraní](../ide/visual-studio-multi-targeting-overview.md)
- [Multicílení](../msbuild/msbuild-multitargeting-overview.md)
