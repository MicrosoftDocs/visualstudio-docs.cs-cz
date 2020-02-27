---
title: Řešení potíží s chybami cílení .NET Framework | Microsoft Docs
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
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77631598"
---
# <a name="troubleshoot-net-framework-targeting-errors"></a>Řešení potíží s chybami cílení .NET Framework

Toto téma popisuje chyby nástroje MSBuild, ke kterým může dojít kvůli problémům s referencí a o tom, jak tyto chyby vyřešit.

## <a name="you-have-referenced-a-project-or-assembly-that-targets-a-different-version-of-the-net-framework"></a>Odkazovali jste na projekt nebo sestavení, které cílí na jinou verzi .NET Framework

 Můžete vytvářet aplikace, které odkazují na projekty nebo sestavení, které cílí na různé verze .NET Framework. Můžete například vytvořit aplikaci, která cílí na profil klienta .NET Framework 4, ale odkazuje na sestavení, které cílí na .NET Framework 2,0. Pokud však vytvoříte projekt, který se zaměřuje na starší verzi .NET Framework, nemůžete v tomto projektu nastavit odkaz na projekt nebo sestavení, které cílí na profil klienta .NET Framework 4 nebo .NET Framework 4. Pokud chcete chybu vyřešit, ujistěte se, že vaše aplikace cílí na profil nebo profily, které jsou kompatibilní s profilem, který cílí na projekty nebo sestavení, na které vaše aplikace odkazuje.

## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework"></a>Přesměrovali jste projekt na jinou verzi .NET Framework

 Pokud změníte cílovou verzi .NET Framework pro vaši aplikaci, Visual Studio změní některé odkazy, ale možná budete muset některé odkazy aktualizovat ručně. Například jedna z výše uvedených chyb může nastat, pokud změníte aplikaci na cílovou verzi .NET Framework 3,5 Service Pack 1 a tato aplikace obsahuje prostředky nebo nastavení, které jsou závislé na profilu klienta pro .NET Framework 4.

 Chcete-li pracovat s nastavením aplikace, otevřete **Průzkumník řešení**, zvolte možnost **Zobrazit všechny soubory**a pak upravte soubor *App. config* v editoru XML aplikace Visual Studio. Změňte verzi v nastavení tak, aby odpovídala příslušné verzi .NET Framework. Například můžete změnit nastavení verze z 4.0.0.0 na 2.0.0.0. Podobně pro aplikaci, která má přidané prostředky, otevřete **Průzkumník řešení**, zvolte tlačítko **Zobrazit všechny soubory** , rozbalte **můj projekt** (Visual Basic) nebo **vlastnosti** (C#) a pak upravte soubor *Resources. resx* v editoru XML aplikace Visual Studio. Změňte nastavení verze z 4.0.0.0 na 2.0.0.0.

 Pokud má vaše aplikace prostředky, jako jsou ikony nebo rastrové obrázky nebo nastavení, například řetězce datových připojení, můžete také vyřešit chybu odebráním všech položek na stránce **Nastavení** **Návrháře projektu** a pak znovu přidat požadovaná nastavení.

## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework-and-references-do-not-resolve"></a>Přesměrovali jste projekt na jinou verzi .NET Framework a odkazy nebudou přeloženy

 Pokud změníte cíl projektu na jinou verzi .NET Framework, odkazy se v některých případech nemusí správně vyřešit. Explicitní plně kvalifikované odkazy na sestavení často způsobují tento problém, ale lze je vyřešit odebráním odkazů, které se nevyřeší a následně jejich přidáním zpět do projektu. Alternativně můžete upravit soubor projektu a nahradit tak odkazy. Nejprve odeberte odkazy z tohoto formuláře:

```xml
<Reference Include="System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089, processorArchitecture=MSIL" />
```

 Pak je nahradíte jednoduchým formulářem:

```xml
<Reference Include="System.ServiceModel" />
```

> [!NOTE]
> Po zavření a opětovném otevření projektu byste ho měli také znovu sestavit, aby se zajistilo správné řešení všech odkazů.

## <a name="see-also"></a>Viz také

- [Postupy: cílení na verzi .NET Framework](../ide/visual-studio-multi-targeting-overview.md)
- [.NET Framework profil klienta](/dotnet/framework/deployment/client-profile)
- [Přehled cílení na rozhraní](../ide/visual-studio-multi-targeting-overview.md)
- [Cílení na více verzí](../msbuild/msbuild-multitargeting-overview.md)
