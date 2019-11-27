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
ms.openlocfilehash: 6a816981b41dd8ca2a2119bbd99c776c6a7e2436
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74296886"
---
# <a name="visual-studio-multi-targeting-overview"></a>Přehled cílení na více verzí sady Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V této verzi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]můžete určit verzi [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], která je vyžadována pro vaši aplikaci. Proto pokud chcete použít tuto verzi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pro pokračování v vývoji projektu, který jste spustili v dřívější verzi, nemusíte měnit cíl rozhraní. Můžete také vytvořit řešení, které obsahuje projekty zaměřené na různé verze rozhraní Framework. Cílení rozhraní také pomáhá zajistit, že aplikace používá pouze funkce, které jsou k dispozici v zadané verzi rozhraní framework.

> [!TIP]
> Můžete také směrovat aplikace pro různé platformy. Další informace najdete v tématu [cílení](../msbuild/msbuild-multitargeting-overview.md) na více verzí

## <a name="framework-targeting-features"></a>Funkce cílení rozhraní
 Cílení rozhraní zahrnuje následující funkce:

- Když otevřete projekt, který se zaměřuje na starší verzi [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] ho může automaticky upgradovat nebo ponechat cíl tak, jak je.

- Při vytváření projektu můžete určit verzi [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], na kterou chcete cílit.

- Můžete změnit verzi [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], na kterou existující projekt cílí.

- V každém z několika projektů ve stejném řešení můžete cílit na jinou verzi [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

- Když změníte verzi [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], na kterou projekt cílí, [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] provede všechny požadované změny odkazů a konfiguračních souborů.

  Když pracujete na projektu, který se zaměřuje na starší verzi [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], Visual Studio dynamicky změní vývojové prostředí následujícím způsobem:

- Filtruje položky v dialogovém okně **Nový projekt** , v dialogovém okně **Přidat novou položku** , v dialogovém okně **Přidat nový odkaz** a v dialogovém okně **Přidat odkaz na službu** , aby vynechal volby, které nejsou k dispozici v cílové verzi.

- Filtruje vlastní ovládací prvky v **sadě nástrojů** k odebrání těch, které nejsou k dispozici v cílové verzi, a k zobrazení pouze těch nejaktuálnějších ovládacích prvků, když je k dispozici více ovládacích prvků.

- Filtruje nabídku technologie IntelliSense, která vynechává funkce jazyka, které nejsou dostupné v cílených verzích.

- Filtruje vlastnosti v okně **vlastnosti** , aby vynechal ty, které nejsou k dispozici v cílové verzi.

- Filtruje možnosti nabídky, aby byly vynechány možnosti, které nejsou dostupné v cílených verzích.

- V případě sestavení používá verzi kompilátoru a možnosti kompilátoru, které jsou vhodné pro cílovou verzi.

> [!NOTE]
> Cílení rozhraní není zárukou, že vaše aplikace bude pracovat správně. Je nutné otestovat vaši aplikaci a ujistit se, že běží před cílovou verzi. Nelze zaměřit verze systému, které jsou starší než .NET Framework 2.0.

## <a name="selecting-a-target-framework-version"></a>Výběr cílové verze rozhraní
 Když vytvoříte projekt, v dialogovém okně **Nový projekt** vyberte cílovou verzi [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Seznam dostupných šablon projektu je filtrován podle výběru. V existujícím projektu můžete změnit cílovou [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] verzi v dialogovém okně Vlastnosti projektu. Další informace najdete v tématu [Postup: cílení na verzi .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

> [!NOTE]
> V edicích Express sady Visual Studio nelze nastavit cílovou architekturu v dialogovém okně **Nový projekt** .

## <a name="resolving-system-and-user-assembly-references"></a>Řešení systému a odkazy na sestavení uživatele
 K cílení na určitou verzi rozhraní .NET Framework, musíte nejprve nainstalovat odpovídající odkazy na sestavení. Odkazy na sestavení pro verze .NET Framework 2,0, 3,0 a 3,5 jsou součástí .NET Framework 3,5 SP1, kterou si můžete stáhnout z webu [Microsoft Download Center, Microsoft Visual Studio](https://www.microsoft.com/download/details.aspx?id=25150) Web. Odkazy na sestavení pro profil klienta .NET Framework 3,5, .NET Framework 4, profil .NET Framework 4 klienta a program Silverlight jsou také k dispozici na webu [soubory ke stažení pro Visual Studio](https://go.microsoft.com/fwlink/?LinkId=179687) .

> [!NOTE]
> Rozhraní .NET Framework client profile je podmnožinou rozhraní .NET Framework, která poskytuje omezenou sadu knihoven a funkcí. Další informace o profilech klienta najdete v tématu [.NET Framework profil klienta](https://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1).

 Dialogové okno **Přidat odkaz** zakáže systémová sestavení, která se netýkají cílové verze [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], aby se nedala přidat do projektu neúmyslně. (Systémová sestavení jsou soubory DLL, které jsou součástí [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] verze.) Odkazy, které patří do verze rozhraní, která je novější než cílová verze, nebudou přeloženy a ovládací prvky, které závisejí na takovém odkazu, nelze přidat. Pokud chcete takový odkaz povolit, resetujte [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] cíl projektu na jednu, která obsahuje odkaz.  Další informace naleznete v tématu [Úvod do Návrháře projektu](https://msdn.microsoft.com/898dd854-c98d-430c-ba1b-a913ce3c73d7).

 Další informace o odkazech na sestavení naleznete v tématu [řešení sestavení v době návrhu](../msbuild/resolving-assemblies-at-design-time.md).

## <a name="enabling-linq"></a>Povolení LINQ
 Pokud je cílem rozhraní .NET Framework 3.5 nebo novější, odkaz na System.Core a import na úrovni projektu pro System.Linq (v pouze v jazyce Visual Basic) jsou přidány automaticky. Pokud chcete používat funkce LINQ, musíte také zapnout možnost Infer (v pouze v jazyce Visual Basic). Reference a import jsou automaticky odebrány při změně cíle na starší verzi rozhraní .NET Framework. Další informace naleznete v tématu [How to: Create a LINQ Project](https://msdn.microsoft.com/library/a929e653-09a3-44be-881f-68ca33f192b2).

## <a name="see-also"></a>Viz také
[Cílení](../msbuild/msbuild-multitargeting-overview.md) [na více verzí
.NET Framework cílením na ASP.NET webové projekty](https://msdn.microsoft.com/library/8b8145a9-62f6-4fc4-8a83-47b0487cbe76)
[kompatibility platforem a systémových požadavků](/visualstudio/productinfo/vs2015-compatibility-vs)
