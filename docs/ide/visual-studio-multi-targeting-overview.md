---
title: Cílové rozhraní .NET Framework
ms.date: 02/06/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- targeting .NET Framework [Visual Studio]
- multi-targeting [Visual Studio]
- multitargeting [Visual Studio]
- framework targeting [Visual Studio]
- .NET framework targeting [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: e0004678b62b9deba97d31815de577721008f77d
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53058295"
---
# <a name="visual-studio-multi-targeting-overview"></a>Přehled možností cílení na více Visual Studio

V sadě Visual Studio můžete zadat verzi nebo profil, který chcete svůj projekt cílit na rozhraní .NET Framework. Pro spuštění v jiném počítači, který musí být aplikace cílena kompatibilní s verzí rozhraní Framework, který je nainstalován v počítači verzi rozhraní Framework aplikace.

Můžete také vytvořit řešení, které obsahuje projekty zaměřené na různé verze rozhraní Framework. Cílení rozhraní pomáhá zaručit, že aplikace používá pouze funkce, které jsou k dispozici v zadané verzi rozhraní framework.

> [!TIP]
> Můžete také směrovat aplikace pro různé platformy. Další informace najdete v tématu [cílení na více verzí](../msbuild/msbuild-multitargeting-overview.md).

## <a name="framework-targeting-features"></a>Funkce cílení rozhraní Framework

Cílení rozhraní zahrnuje následující funkce:

- Když otevřete projekt, který se zaměřuje na starší verzi [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], Visual Studio automaticky upgradovat nebo ponechat cíl jako-je.

- Když vytvoříte projekt, můžete určit verzi [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] , kterou chcete cílit.

- Můžete změnit verzi [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] existující projekt cílí.

- Můžete cílit na jinou verzi [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] v různé projekty ve stejném řešení.

- Při změně verze [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] , který je projekt cílen [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] provede všechny potřebné změny odkazů a konfiguračních souborů.

Když pracujete na projektu, který se zaměřuje na starší verzi [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], Visual Studio dynamicky provádí následující změny vývojové prostředí, následujícím způsobem:

- Filtruje položky **přidat novou položku** dialogovém okně **přidat nový odkaz** dialogovém okně a **přidat odkaz na službu** kde vynechává volby, které nejsou k dispozici v Cílová verze.

- Filtruje vlastní ovládací prvky v **nástrojů** a odeberte ty, které nejsou dostupné v cílených verzích zobrazil pouze nejnovější ovládací prvky, když jsou k dispozici více ovládacích prvků.

- Filtruje **IntelliSense** která vynechává funkce jazyka, které nejsou dostupné v cílených verzích.

- Filtruje vlastnosti v **vlastnosti** okno, aby byly vynechány ty, které nejsou dostupné v cílených verzích.

- Filtruje možnosti nabídky, aby byly vynechány možnosti, které nejsou dostupné v cílených verzích.

- V případě sestavení používá verzi kompilátoru a možnosti kompilátoru, které jsou vhodné pro cílovou verzi.

> [!NOTE]
> Cílení rozhraní není zárukou, že vaše aplikace bude pracovat správně. Je nutné otestovat vaši aplikaci a ujistit se, že běží před cílovou verzi. Nelze zaměřit verze systému, které jsou starší než .NET Framework 2.0.

## <a name="select-a-target-framework-version"></a>Vyberte cílovou verzi rozhraní framework

Při vytváření projektu vyberte cílovou verzi rozhraní .NET Framework v **nový projekt** dialogové okno. Seznam dostupných rozhraní obsahuje nainstalované verze architektur, které se dají použít pro typ vybrané šablony. Pro typy šablon, které nevyžadují rozhraní .NET Framework, například šablony .NET Core **Framework** rozevíracího seznamu je skrytá.

![Rozhraní Framework rozevírací seznam v dialogovém okně Nový projekt](media/vside-newproject-framework.png)

V existujícím projektu, můžete změnit cíl [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] verze v dialogovém okně Vlastnosti projektu. Další informace najdete v tématu [postupy: cílení na určitou verzi rozhraní .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

## <a name="resolve-system-and-user-assembly-references"></a>Přeložit odkazy na sestavení systémových a uživatelských

K cílení na určitou verzi rozhraní .NET Framework, musíte nejprve nainstalovat odpovídající odkazy na sestavení. Můžete stáhnout balíčky pro vývojáře pro různé verze rozhraní .NET Framework [.NET stáhne](https://www.microsoft.com/net/download/windows) stránky.

**Přidat odkaz** dialogové okno zakáže sestavení systému, které se netýkají cílové [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] verzi tak, že není možné je přidat do projektu neúmyslně. (Systémová sestavení jsou *.dll* soubory, které jsou součástí [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] verze.) Odkazy, které patří do verze rozhraní, které je vyšší než cílová verze, neposkytne řešení a ovládací prvky, které jsou závislé na takovém odkazu nelze přidat. Pokud chcete povolit takový odkaz, resetuje [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] cíli projektu na takový, který obsahuje odkaz.  Další informace najdete v tématu [postupy: cílení na určitou verzi rozhraní .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

Další informace o odkazech na sestavení naleznete v tématu [přeložit sestavení v době návrhu](../msbuild/resolving-assemblies-at-design-time.md).

## <a name="enable-linq"></a>Povolení jazyka LINQ

Pokud je cílem rozhraní .NET Framework 3.5 nebo novější, odkaz na **System.Core** a import na úrovni projektu pro <xref:System.Linq> (v pouze v jazyce Visual Basic) jsou přidány automaticky. Pokud chcete používat funkce LINQ, musíte také zapnout `Option Infer` na (v pouze v jazyce Visual Basic). Reference a import jsou automaticky odebrány při změně cíle na starší verzi rozhraní .NET Framework. Další informace najdete v tématu [pracovat s technologií LINQ](/dotnet/csharp/tutorials/working-with-linq).

## <a name="see-also"></a>Viz také:

- [Cílení na více verzí (MSBuild)](../msbuild/msbuild-multitargeting-overview.md)
- [Postupy: Úprava na cílové rozhraní framework a sadu nástrojů platformy (C++)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)