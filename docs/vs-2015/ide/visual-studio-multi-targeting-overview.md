---
title: Přehled možností cílení na více | Dokumentace Microsoftu
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], targeting .NET Framework version
- multi-targeting [Visual Studio]
- multitargeting [Visual Studio]
ms.assetid: b1702c33-0672-4ebc-b779-2b324d6ea880
caps.latest.revision: 39
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e9e8b53c5bd4d6045d7582c24be865ae216f1114
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851091"
---
# <a name="visual-studio-multi-targeting-overview"></a>Přehled cílení na více verzí sady Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V této verzi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], můžete určit verzi [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , která je vyžadována pro vaši aplikaci. Proto pokud chcete používat tuto verzi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dalším vývoji projektu, který jste započali v dřívější verzi, není nutné změnit cílový rámec. Můžete také vytvořit řešení, které obsahuje projekty zaměřené na různé verze rozhraní Framework. Cílení rozhraní také pomáhá zajistit, že aplikace používá pouze funkce, které jsou k dispozici v zadané verzi rozhraní framework.

> [!TIP]
> Můžete také směrovat aplikace pro různé platformy. Další informace najdete v tématu [cílení na více verzí](../msbuild/msbuild-multitargeting-overview.md)

## <a name="framework-targeting-features"></a>Funkce cílení rozhraní
 Cílení rozhraní zahrnuje následující funkce:

- Když otevřete projekt, který se zaměřuje na starší verzi [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] můžete automaticky upgradovat nebo ponechat cíl tak, jak je.

- Když vytvoříte projekt, můžete určit verzi [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , kterou chcete cílit.

- Můžete změnit verzi [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] existující projekt cílí.

- Můžete cílit na jinou verzi [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] v různé projekty ve stejném řešení.

- Při změně verze [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , který je projekt cílen [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] provede všechny potřebné změny odkazů a konfiguračních souborů.

  Když pracujete na projektu, který se zaměřuje na starší verzi [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], Visual Studio dynamicky provádí následující změny vývojové prostředí, následujícím způsobem:

- Filtruje položky **nový projekt** dialogovém okně **přidat novou položku** dialogovém okně **přidat nový odkaz** dialogovém okně a **přidat odkaz na službu** kde vynechává volby, které nejsou dostupné v cílených verzích.

- Filtruje vlastní ovládací prvky v **nástrojů** a odeberte ty, které nejsou dostupné v cílených verzích zobrazil pouze nejnovější ovládací prvky, když jsou k dispozici více ovládacích prvků.

- Filtruje nabídku technologie IntelliSense, která vynechává funkce jazyka, které nejsou dostupné v cílených verzích.

- Filtruje vlastnosti v **vlastnosti** okno, aby byly vynechány ty, které nejsou dostupné v cílených verzích.

- Filtruje možnosti nabídky, aby byly vynechány možnosti, které nejsou dostupné v cílených verzích.

- V případě sestavení používá verzi kompilátoru a možnosti kompilátoru, které jsou vhodné pro cílovou verzi.

> [!NOTE]
> Cílení rozhraní není zárukou, že vaše aplikace bude pracovat správně. Je nutné otestovat vaši aplikaci a ujistit se, že běží před cílovou verzi. Nelze zaměřit verze systému, které jsou starší než .NET Framework 2.0.

## <a name="selecting-a-target-framework-version"></a>Výběr cílové verze rozhraní
 Při vytváření projektu vyberte cílovou [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] verze **nový projekt** dialogové okno. Seznam dostupných šablon projektu je filtrován podle výběru. V existujícím projektu, můžete změnit cíl [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] verze v dialogovém okně Vlastnosti projektu. Další informace najdete v tématu [postupy: cílení na určitou verzi rozhraní .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

> [!NOTE]
> V edicích Express sady Visual Studio, nelze nastavit cílové rozhraní **nový projekt** dialogové okno.

## <a name="resolving-system-and-user-assembly-references"></a>Řešení systému a odkazy na sestavení uživatele
 K cílení na určitou verzi rozhraní .NET Framework, musíte nejprve nainstalovat odpovídající odkazy na sestavení. Odkazy na sestavení pro rozhraní .NET Framework verze 2.0, 3.0 a 3.5 jsou zahrnuty v rozhraní .NET Framework 3.5 SP1, který si můžete stáhnout z [Microsoft Download Center, Microsoft Visual Studio](https://www.microsoft.com/download/details.aspx?id=25150) webu. Odkazy na sestavení pro rozhraní .NET Framework 3.5 Client Profile, .NET Framework 4, .NET Framework 4 Client Profile a Silverlight jsou také k dispozici [stahování sady Visual Studio](https://msdn.microsoft.com/vstudio/bb984878.aspx) webu.

> [!NOTE]
> Rozhraní .NET Framework client profile je podmnožinou rozhraní .NET Framework, která poskytuje omezenou sadu knihoven a funkcí. Další informace o profilech klienta naleznete v tématu [rozhraní .NET Framework Client Profile](https://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1).

 **Přidat odkaz** dialogové okno zakáže sestavení systému, které se netýkají cílové [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] verzi tak, že není možné je přidat do projektu neúmyslně. (Systémová sestavení jsou soubory DLL, které jsou součástí [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] verze.) Odkazy, které patří do verze rozhraní, která je novější než cílová verze, nebudou přeloženy a ovládací prvky, které závisejí na takovém odkazu, nelze přidat. Pokud chcete povolit takový odkaz, resetuje [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] cíli projektu na takový, který obsahuje odkaz.  Další informace najdete v tématu [Úvod do Návrháře projektu](https://msdn.microsoft.com/898dd854-c98d-430c-ba1b-a913ce3c73d7).

 Další informace o odkazech na sestavení naleznete v tématu [překlad sestavení v době návrhu](../msbuild/resolving-assemblies-at-design-time.md).

## <a name="enabling-linq"></a>Povolení LINQ
 Pokud je cílem rozhraní .NET Framework 3.5 nebo novější, odkaz na System.Core a import na úrovni projektu pro System.Linq (v pouze v jazyce Visual Basic) jsou přidány automaticky. Pokud chcete používat funkce LINQ, musíte také zapnout možnost Infer (v pouze v jazyce Visual Basic). Reference a import jsou automaticky odebrány při změně cíle na starší verzi rozhraní .NET Framework. Další informace najdete v tématu [postupy: vytvoření projektu LINQ](https://msdn.microsoft.com/library/a929e653-09a3-44be-881f-68ca33f192b2).

## <a name="see-also"></a>Viz také
[Cílení](../msbuild/msbuild-multitargeting-overview.md) [na více verzí
.NET Framework cílením na ASP.NET webové projekty](https://msdn.microsoft.com/library/8b8145a9-62f6-4fc4-8a83-47b0487cbe76)
[kompatibility platforem a systémových požadavků](/visualstudio/productinfo/vs2015-compatibility-vs)
