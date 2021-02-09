---
title: Cílené rozhraní .NET Framework
description: Naučte se, jak určit verzi .NET Framework, na kterou má projekt cílit, aby aplikace mohla využívat pouze funkce, které jsou k dispozici v zadané verzi.
ms.date: 03/31/2020
ms.topic: overview
helpviewer_keywords:
- targeting .NET Framework [Visual Studio]
- framework targeting [Visual Studio]
- .NET framework targeting [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: d29f40c6e6e43f81eefc287bf28141be6ca7feb7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873928"
---
# <a name="framework-targeting-overview"></a>Přehled cílení na rozhraní

V aplikaci Visual Studio můžete určit verzi rozhraní .NET, na kterou má být projekt cílen. Cílení na rozhraní pomáhá zaručit, že aplikace používá pouze funkce, které jsou k dispozici v zadané verzi rozhraní. Aby mohla aplikace .NET Framework běžet na jiném počítači, verze rozhraní, na kterou aplikace cílí, musí být kompatibilní s verzí rozhraní, která je v počítači nainstalovaná.

Řešení sady Visual Studio může obsahovat projekty, které cílí na různé verze rozhraní .NET.  Nicméně Všimněte si, že můžete vytvořit pouze v rámci jedné verze rozhraní .NET buď pomocí referenčních podmíněných pro jedno sestavení, nebo rekurzivně sestavit různé binární soubory pro každou verzi.  Další informace o cílových rozhraních naleznete v tématu [cílová rozhraní](/dotnet/standard/frameworks).

> [!TIP]
> Můžete také cílit na aplikace pro různé platformy. Další informace najdete v tématu [cílení](../msbuild/msbuild-multitargeting-overview.md)na více verzí.

## <a name="framework-targeting-features"></a>Rozhraní cílící na funkce

Cílení na rámec zahrnuje tyto funkce:

- Když otevřete projekt, který se zaměřuje na starší verzi rozhraní .NET Framework, Visual Studio může automaticky upgradovat projekt nebo ponechat cíl tak, jak je.

- Při vytváření projektu .NET Framework můžete určit verzi .NET Framework, na kterou chcete cílit.

- Můžete [cílit na více platforem](/dotnet/standard/frameworks#how-to-specify-target-frameworks) v jednom projektu.

- V každém z několika projektů ve stejném řešení můžete cílit na jinou verzi rozhraní .NET.

- Můžete změnit verzi rozhraní .NET, na kterou existující projekt cílí.

   Když změníte verzi rozhraní .NET, na kterou projekt cílí, provede aplikace Visual Studio všechny požadované změny odkazů a konfiguračních souborů.

Když pracujete na projektu, který se zaměřuje na předchozí verzi rozhraní, Visual Studio dynamicky změní vývojové prostředí následujícím způsobem:

- Filtruje položky v dialogovém okně **Přidat novou položku** , v dialogovém okně **Přidat nový odkaz** a v dialogovém okně **Přidat odkaz na službu** k vynechání voleb, které nejsou v cílové verzi k dispozici.

- Filtruje vlastní ovládací prvky v **sadě nástrojů** k odebrání těch, které nejsou k dispozici v cílové verzi, a k zobrazení pouze těch nejaktuálnějších ovládacích prvků, když je k dispozici více ovládacích prvků.

- Filtruje **IntelliSense** , aby vynechal funkce jazyka, které nejsou dostupné v cílové verzi.

- Filtruje vlastnosti v okně **vlastnosti** , aby vynechal ty, které nejsou k dispozici v cílové verzi.

- Filtruje možnosti nabídky a vynechává možnosti, které nejsou dostupné v cílové verzi.

- Pro sestavení používá verzi kompilátoru a možnosti kompilátoru, které jsou vhodné pro cílovou verzi.

> [!NOTE]
> - Cílení na rámec nezaručuje, že vaše aplikace bude fungovat správně. Musíte otestovat aplikaci, abyste se ujistili, že běží na cílové verzi.
> - Verze rozhraní Framework nelze cílit .NET Framework 2,0.

## <a name="select-a-target-framework-version"></a>Vyberte cílovou verzi rozhraní .NET Framework.

Při vytváření projektu .NET Framework můžete po výběru šablony projektu vybrat cílovou verzi .NET Framework. Seznam dostupných architektur zahrnuje verze nainstalovaných rozhraní, které se vztahují na vybraný typ šablony. V případě šablon projektů non-.NET Framework, jako jsou například šablony .NET Core, **se rozevírací seznam rozhraní nezobrazí** .

::: moniker range="vs-2017"

![Rozevírací seznam rozhraní ve VS 2017](media/vside-newproject-framework.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Rozevírací seznam rozhraní ve VS 2019](media/vs-2019/configure-new-project-framework.png)

::: moniker-end

## <a name="change-the-target-framework"></a>Změna cílového rozhraní .NET Framework

V existujícím projektu Visual Basic, C# nebo F # můžete cílovou verzi rozhraní .NET změnit v dialogovém okně Vlastnosti projektu. Informace o tom, jak změnit cílovou verzi pro projekty v jazyce C++, naleznete v tématu [jak upravit cílové rozhraní a sadu nástrojů platformy](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset) .

1. V **Průzkumník řešení** otevřete nabídku kliknutím pravým tlačítkem u projektu, který chcete změnit, a poté zvolte možnost **vlastnosti**.

1. V levém sloupci okna **vlastnosti** vyberte kartu **aplikace** .

   ![Karta aplikace vlastností projektu](../ide/media/vs_slnexplorer_properties_applicationtab.png)

   > [!NOTE]
   > Po vytvoření aplikace UWP nemůžete změnit cílovou verzi buď Windows, nebo .NET.

1. V seznamu **cílové rozhraní** vyberte požadovanou verzi.

1. V dialogovém okně ověření, které se zobrazí, klikněte na tlačítko **Ano** .

   Projekt se uvolní. Po opětovném načtení se cílí na verzi rozhraní .NET, kterou jste právě zvolili.

> [!NOTE]
> Pokud váš kód obsahuje odkazy na jinou verzi rozhraní .NET, než na kterou cílíte, chybové zprávy se mohou zobrazit při kompilaci nebo spuštění kódu. Chcete-li tyto chyby vyřešit, upravte odkazy. Viz [řešení chyb cílení na rozhraní .NET](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).

> [!TIP]
> V závislosti na cílové architektuře může být v souboru projektu reprezentována následujícími způsoby:
>
> - Pro aplikaci .NET Core: `<TargetFramework>netcoreapp2.1</TargetFramework>`
> - Pro .NET Standard aplikaci: `<TargetFramework>netstandard2.0</TargetFramework>`
> - Pro .NET Framework aplikaci: `<TargetFrameworkVersion>v4.7.2</TargetFrameworkVersion>`

## <a name="resolve-system-and-user-assembly-references"></a>Překlad systémových a uživatelských odkazů na sestavení

Chcete-li cílit na verzi rozhraní .NET, je nutné nejprve nainstalovat příslušné odkazy na sestavení. Sady Developer Pack pro různé verze rozhraní .NET si můžete stáhnout na stránce [soubory ke stažení pro rozhraní .NET](https://www.microsoft.com/net/download/windows) .

Pro .NET Framework projekty, dialogové okno **Přidat odkaz** zakáže systémová sestavení, která se nevztahují na cílovou .NET Framework verzi, aby se nedala neúmyslně přidat do projektu. (Systémová sestavení jsou soubory *DLL* , které jsou součástí .NET Framework verze.) Odkazy, které patří do verze rozhraní, která je vyšší než cílová verze, nebudou přeloženy a ovládací prvky, které závisejí na takovém odkazu, nelze přidat. Pokud chcete takový odkaz povolit, resetujte .NET Framework cíl projektu na jednu, která obsahuje odkaz.

Další informace o odkazech na sestavení naleznete v tématu věnovaném [překladu sestavení v době návrhu](../msbuild/resolving-assemblies-at-design-time.md).

## <a name="enable-linq"></a>Povolit LINQ

Pokud cílíte na .NET Framework 3,5 nebo novější, přidají se automaticky odkaz na **System. Core** a import na úrovni projektu pro <xref:System.Linq> (jenom v Visual Basic). Pokud chcete používat funkce LINQ, musíte také zapnout `Option Infer` (jenom v Visual Basic). Odkaz a import se odeberou automaticky, pokud změníte cíl na dřívější verzi .NET Framework. Další informace najdete v tématu [práce s LINQ](/dotnet/csharp/tutorials/working-with-linq).

## <a name="see-also"></a>Viz také

- [Cílové architektury](/dotnet/standard/frameworks)
- [Cílení na více verzí (MSBuild)](../msbuild/msbuild-multitargeting-overview.md)
- [Postupy: Změna cílové architektury a sady nástrojů platformy (C++)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)
