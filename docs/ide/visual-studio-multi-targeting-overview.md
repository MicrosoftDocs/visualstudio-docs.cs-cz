---
title: Cílené rozhraní .NET Framework
ms.date: 02/06/2018
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
ms.openlocfilehash: ec81b38ab68c327f25c9f94b6329a700e2662383
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594120"
---
# <a name="framework-targeting-overview"></a>Přehled cílení na rozhraní

V aplikaci Visual Studio můžete určit verzi rozhraní .NET, na kterou má být projekt cílen. Cílení na rozhraní pomáhá zaručit, že aplikace používá pouze funkce, které jsou k dispozici v zadané verzi rozhraní. Aby mohla aplikace .NET Framework běžet na jiném počítači, verze rozhraní, na kterou aplikace cílí, musí být kompatibilní s verzí rozhraní, která je v počítači nainstalovaná.

Řešení sady Visual Studio může obsahovat projekty, které cílí na různé verze rozhraní .NET.

Další informace o cílových rozhraních naleznete v tématu [cílová rozhraní](/dotnet/standard/frameworks).

> [!TIP]
> Můžete také směrovat aplikace pro různé platformy. Další informace najdete v tématu [cílení na více verzí](../msbuild/msbuild-multitargeting-overview.md).

## <a name="framework-targeting-features"></a>Funkce cílení rozhraní Framework

Cílení rozhraní zahrnuje následující funkce:

- Když otevřete projekt, který se zaměřuje na starší verzi rozhraní .NET Framework, Visual Studio může automaticky upgradovat projekt nebo ponechat cíl tak, jak je.

- Při vytváření projektu .NET Framework můžete určit verzi .NET Framework, na kterou chcete cílit.

- Můžete [cílit na více platforem](/dotnet/standard/frameworks#how-to-specify-target-frameworks) v jednom projektu.

- V každém z několika projektů ve stejném řešení můžete cílit na jinou verzi rozhraní .NET.

- Můžete změnit verzi rozhraní .NET, na kterou existující projekt cílí.

   Když změníte verzi rozhraní .NET, na kterou projekt cílí, provede aplikace Visual Studio všechny požadované změny odkazů a konfiguračních souborů.

Když pracujete na projektu, který se zaměřuje na předchozí verzi rozhraní, Visual Studio dynamicky změní vývojové prostředí následujícím způsobem:

- Filtruje položky **přidat novou položku** dialogovém okně **přidat nový odkaz** dialogovém okně a **přidat odkaz na službu** kde vynechává volby, které nejsou k dispozici v Cílová verze.

- Filtruje vlastní ovládací prvky v **nástrojů** a odeberte ty, které nejsou dostupné v cílených verzích zobrazil pouze nejnovější ovládací prvky, když jsou k dispozici více ovládacích prvků.

- Filtruje **IntelliSense** , aby vynechal funkce jazyka, které nejsou dostupné v cílové verzi.

- Filtruje vlastnosti v okně **vlastnosti** , aby vynechal ty, které nejsou k dispozici v cílové verzi.

- Filtruje možnosti nabídky a vynechává možnosti, které nejsou dostupné v cílové verzi.

- V případě sestavení používá verzi kompilátoru a možnosti kompilátoru, které jsou vhodné pro cílovou verzi.

> [!NOTE]
> - Cílení rozhraní není zárukou, že vaše aplikace bude pracovat správně. Je nutné otestovat vaši aplikaci a ujistit se, že běží před cílovou verzi.
> - Verze rozhraní Framework nelze cílit .NET Framework 2,0.

## <a name="select-a-target-framework-version"></a>Vyberte cílovou verzi rozhraní framework

Při vytváření projektu .NET Framework můžete po výběru šablony projektu vybrat cílovou verzi .NET Framework. Seznam dostupných rozhraní obsahuje nainstalované verze architektur, které se dají použít pro typ vybrané šablony. V případě šablon projektů non-.NET Framework, jako jsou například šablony .NET Core, **se rozevírací seznam rozhraní nezobrazí** .

::: moniker range="vs-2017"

![Rozevírací seznam rozhraní ve VS 2017](media/vside-newproject-framework.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Rozevírací seznam rozhraní ve VS 2019](media/vs-2019/configure-new-project-framework.png)

::: moniker-end

## <a name="change-the-target-framework"></a>Změna cílového rozhraní .NET Framework

V existující Visual Basic, C#nebo F# projektu, můžete cílovou verzi rozhraní .NET změnit v dialogovém okně Vlastnosti projektu. Informace o tom, jak změnit cílovou verzi pro C++ projekty, naleznete v tématu [jak upravit cílové rozhraní a sadu nástrojů platformy](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset) .

1. V **Průzkumník řešení**otevřete nabídku kliknutím pravým tlačítkem u projektu, který chcete změnit, a poté zvolte možnost **vlastnosti**.

1. V levém sloupci **vlastnosti** okna, vyberte **aplikace** kartu.

   ![Karta aplikace vlastností projektu](../ide/media/vs_slnexplorer_properties_applicationtab.png)

   > [!NOTE]
   > Po vytvoření aplikace UWP nemůžete změnit cílovou verzi buď Windows, nebo .NET.

1. V **Cílová architektura** , zvolte verzi, která chcete.

1. V dialogovém okně ověřování, který se zobrazí, zvolte **Ano** tlačítko.

   Projekt se uvolní. Po opětovném načtení se cílí na verzi rozhraní .NET, kterou jste právě zvolili.

> [!NOTE]
> Pokud váš kód obsahuje odkazy na jinou verzi rozhraní .NET, než na kterou cílíte, chybové zprávy se mohou zobrazit při kompilaci nebo spuštění kódu. Chcete-li tyto chyby vyřešit, upravte odkazy. Viz [řešení chyb cílení na rozhraní .NET](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).

> [!TIP]
> V závislosti na cílové architektuře může být v souboru projektu reprezentována následujícími způsoby:
>
> - Pro aplikaci .NET Core: `<TargetFramework>netcoreapp2.1</TargetFramework>`
> - Pro aplikaci .NET Standard: `<TargetFramework>netstandard2.0</TargetFramework>`
> - Pro aplikaci .NET Framework: `<TargetFrameworkVersion>v4.7.2</TargetFrameworkVersion>`

## <a name="resolve-system-and-user-assembly-references"></a>Přeložit odkazy na sestavení systémových a uživatelských

Chcete-li cílit na verzi rozhraní .NET, je nutné nejprve nainstalovat příslušné odkazy na sestavení. Sady Developer Pack pro různé verze rozhraní .NET si můžete stáhnout na stránce [soubory ke stažení pro rozhraní .NET](https://www.microsoft.com/net/download/windows) .

Pro .NET Framework projekty, dialogové okno **Přidat odkaz** zakáže systémová sestavení, která se nevztahují na cílovou .NET Framework verzi, aby se nedala neúmyslně přidat do projektu. (Systémová sestavení jsou soubory *DLL* , které jsou součástí .NET Framework verze.) Odkazy, které patří do verze rozhraní, která je vyšší než cílová verze, nebudou přeloženy a ovládací prvky, které závisejí na takovém odkazu, nelze přidat. Pokud chcete takový odkaz povolit, resetujte .NET Framework cíl projektu na jednu, která obsahuje odkaz.

Další informace o odkazech na sestavení naleznete v tématu [přeložit sestavení v době návrhu](../msbuild/resolving-assemblies-at-design-time.md).

## <a name="enable-linq"></a>Povolení jazyka LINQ

Pokud je cílem rozhraní .NET Framework 3.5 nebo novější, odkaz na **System.Core** a import na úrovni projektu pro <xref:System.Linq> (v pouze v jazyce Visual Basic) jsou přidány automaticky. Pokud chcete používat funkce LINQ, musíte také zapnout `Option Infer` na (v pouze v jazyce Visual Basic). Reference a import jsou automaticky odebrány při změně cíle na starší verzi rozhraní .NET Framework. Další informace najdete v tématu [pracovat s technologií LINQ](/dotnet/csharp/tutorials/working-with-linq).

## <a name="see-also"></a>Viz také:

- [Cílové architektury](/dotnet/standard/frameworks)
- [Cílení na více verzí (MSBuild)](../msbuild/msbuild-multitargeting-overview.md)
- [Postupy: Úprava na cílové rozhraní framework a sadu nástrojů platformy (C++)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)
