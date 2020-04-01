---
title: Cílené rozhraní .NET
ms.date: 03/31/2020
ms.topic: conceptual
helpviewer_keywords:
- targeting .NET Framework [Visual Studio]
- framework targeting [Visual Studio]
- .NET framework targeting [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 48d770f5d88e19c749c1a1e657c369089d4c7afb
ms.sourcegitcommit: ce3d0728ec1063ab548dac71c8eaf26d20450acc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2020
ms.locfileid: "80472732"
---
# <a name="framework-targeting-overview"></a>Přehled cílení na rozhraní

V sadě Visual Studio můžete určit verzi rozhraní .NET, na kterou má projekt cílit. Cílení na architekturu pomáhá zaručit, že aplikace používá pouze funkce, které jsou k dispozici v zadané verzi rozhraní. Aby se aplikace rozhraní .NET Framework spouštěla v jiném počítači, musí být verze architektury, na kterou se aplikace zaměřuje, kompatibilní s verzí rozhraní framework, která je nainstalována v počítači.

Řešení sady Visual Studio může obsahovat projekty, které cílí na různé verze rozhraní .NET.  Všimněte si však, že můžete sestavit pouze proti jedné verzi rozhraní .NET buď pomocí odkazpodmínek pro jedno sestavení nebo rekurzivně sestavit různé binární soubory pro každou verzi.  Další informace o cílových architekturách naleznete [v tématu Target Frameworks](/dotnet/standard/frameworks).

> [!TIP]
> Můžete také cílit na aplikace pro různé platformy. Další informace naleznete v tématu [Multitargeting](../msbuild/msbuild-multitargeting-overview.md).

## <a name="framework-targeting-features"></a>Funkce cílení na rozhraní

Cílení na architekturu zahrnuje následující funkce:

- Při otevření projektu, který se zaměřuje na starší verzi architektury, Visual Studio můžete automaticky upgradovat projekt nebo ponechat cíl jako-je.

- Při vytváření projektu rozhraní .NET Framework můžete zadat verzi rozhraní .NET Framework, na kterou chcete cílit.

- Můžete [cílit na více architektur](/dotnet/standard/frameworks#how-to-specify-target-frameworks) v jednom projektu.

- Můžete cílit na jinou verzi rozhraní .NET v každém z několika projektů ve stejném řešení.

- Můžete změnit verzi rozhraní .NET, na kterou cílí existující projekt.

   Změníte-li verzi rozhraní .NET, na kterou se projekt zaměřuje, provede visual studio požadované změny odkazů a konfiguračních souborů.

Při práci na projektu, který se zaměřuje na starší verzi architektury, Visual Studio dynamicky mění vývojové prostředí takto:

- Filtruje položky v dialogovém okně **Přidat novou položku,** v dialogovém okně **Přidat novou referenci** a v dialogovém okně **Přidat odkaz na službu,** aby vynechaly volby, které nejsou v cílové verzi k dispozici.

- Filtruje vlastní ovládací prvky v **panelu nástrojů,** aby odstranily ty, které nejsou k dispozici v cílové verzi, a zobrazí pouze nejaktuálnější ovládací prvky, pokud je k dispozici více ovládacích prvků.

- Filtruje **technologie IntelliSense** tak, aby vynechaly jazykové funkce, které nejsou v cílové verzi k dispozici.

- Filtruje vlastnosti v okně **Vlastnosti** vynechat ty, které nejsou k dispozici v cílové verzi.

- Filtruje možnosti nabídky, aby vynechaly možnosti, které nejsou k dispozici v cílové verzi.

- Pro sestavení používá verzi kompilátoru a možnosti kompilátoru, které jsou vhodné pro cílovou verzi.

> [!NOTE]
> - Cílení na architekturu nezaručuje, že vaše aplikace bude fungovat správně. Je nutné otestovat aplikaci a ujistěte se, že běží proti cílové verzi.
> - Nelze cílit na verze rozhraní pod rozhraním .NET Framework 2.0.

## <a name="select-a-target-framework-version"></a>Výběr verze cílového frameworku

Při vytváření projektu rozhraní .NET Framework můžete po výběru šablony projektu vybrat cílovou verzi rozhraní .NET Framework. Seznam dostupných rozhraní obsahuje nainstalované verze architektury, které jsou použitelné pro vybraný typ šablony. U šablon projektů non-.NET Framework, například šablon .NET Core, se nezobrazí rozevírací seznam **Framework.**

::: moniker range="vs-2017"

![Rozbalovací období rámce ve VS 2017](media/vside-newproject-framework.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Rozbalovací období rámce ve VS 2019](media/vs-2019/configure-new-project-framework.png)

::: moniker-end

## <a name="change-the-target-framework"></a>Změna cílového rámce

V existujícím projektu jazyka Visual Basic, C#, nebo F# změníte cílovou verzi .NET v dialogovém okně vlastností projektu. Informace o tom, jak změnit cílovou verzi pro projekty jazyka C++, najdete [v tématu Jak upravit cílovou architekturu a sadu nástrojů platformy.](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)

1. V **Průzkumníku řešení**otevřete nabídku po kliknutí pravým tlačítkem myši pro projekt, který chcete změnit, a pak zvolte **Vlastnosti**.

1. V levém sloupci okna **Vlastnosti** zvolte kartu **Aplikace.**

   ![Karta Aplikace vlastností projektu](../ide/media/vs_slnexplorer_properties_applicationtab.png)

   > [!NOTE]
   > Po vytvoření aplikace UPW nelze změnit cílovou verzi systému Windows nebo .NET.

1. V seznamu **Cílová architektura** vyberte požadovanou verzi.

1. V zobrazeném dialogovém okně ověření zvolte tlačítko **Ano.**

   Projekt se uvolní. Když se znovu načte, cílí na verzi .NET, kterou jste právě vybrali.

> [!NOTE]
> Pokud váš kód obsahuje odkazy na jinou verzi rozhraní .NET, než na kterou jste cílí, mohou se při kompilaci nebo spuštění kódu zobrazit chybové zprávy. Chcete-li tyto chyby vyřešit, upravte odkazy. Viz [Poradce při potížích s chybami cílení .NET](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).

> [!TIP]
> V závislosti na cílovém rámci může být v souboru projektu reprezentována následujícími způsoby:
>
> - Pro aplikaci .NET Core:`<TargetFramework>netcoreapp2.1</TargetFramework>`
> - Pro aplikaci .NET Standard:`<TargetFramework>netstandard2.0</TargetFramework>`
> - Pro aplikaci rozhraní .NET Framework:`<TargetFrameworkVersion>v4.7.2</TargetFrameworkVersion>`

## <a name="resolve-system-and-user-assembly-references"></a>Řešení odkazů na sestavení systému a uživatele

Chcete-li cílit na verzi rozhraní .NET, musíte nejprve nainstalovat příslušné odkazy na sestavení. Vývojářské balíčky pro různé verze rozhraní .NET si můžete stáhnout na stránce [ke stažení rozhraní .NET.](https://www.microsoft.com/net/download/windows)

U projektů rozhraní .NET Framework zakáže dialogové okno **Přidat odkaz** systémová sestavení, která se netýkala cílové verze rozhraní .NET Framework, aby je nebylo možné neúmyslně přidat do projektu. (Systémová sestavení jsou soubory *DLL,* které jsou součástí verze rozhraní .NET Framework.) Odkazy, které patří do verze architektury, která je vyšší než cílová verze se nevyřeší a ovládací prvky, které závisí na takový odkaz nelze přidat. Pokud chcete takový odkaz povolit, obnovte cíl rozhraní .NET Framework projektu na ten, který obsahuje odkaz.

Další informace o odkazech na sestavení naleznete [v tématu Řešení sestavení v době návrhu](../msbuild/resolving-assemblies-at-design-time.md).

## <a name="enable-linq"></a>Povolit LINQ

Když cílíte na rozhraní .NET Framework 3.5 nebo novější, automaticky <xref:System.Linq> se přidá odkaz na **System.Core** a import na úrovni projektu (pouze v jazyce Visual Basic). Pokud chcete používat funkce LINQ, musíte `Option Infer` také zapnout (pouze v jazyce Visual Basic). Odkaz a import se automaticky odeberou, pokud změníte cíl na starší verzi rozhraní .NET Framework. Další informace naleznete v [tématu Práce s LINQ](/dotnet/csharp/tutorials/working-with-linq).

## <a name="see-also"></a>Viz také

- [Cílové architektury](/dotnet/standard/frameworks)
- [Multicílení (MSBuild)](../msbuild/msbuild-multitargeting-overview.md)
- [Postup: Úprava cílového rozhraní a sady nástrojů platformy (C++)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)
