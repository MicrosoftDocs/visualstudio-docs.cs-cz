---
title: Vytváření šablon projektu
ms.date: 01/02/2018
ms.topic: conceptual
f1_keywords:
- VS.ExportTemplateWizard
helpviewer_keywords:
- project templates [Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: f4caebfdc4e61b683e0f1407d1522f6da2328fcf
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591070"
---
# <a name="how-to-create-project-templates"></a>Postup: Vytvoření šablon projektů

Toto téma ukazuje, jak vytvořit šablonu pomocí **Průvodce exportem šablony**, který ji zabalí do souboru *ZIP.*

## <a name="use-the-export-template-wizard"></a>Použití Průvodce exportem šablony

1. Vytvořte projekt.

    > [!NOTE]
    > Při pojmenování projektu, který bude zdrojem šablony, používejte pouze platné znaky identifikátoru. V opačném případě může dojít k chybám kompilace v projektech, které jsou vytvořeny ze šablony. Další informace o platných znakech identifikátorů naleznete v [tématu Deklarované názvy prvků (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names) nebo [identifikátory (C++).](/cpp/cpp/identifiers-cpp) Alternativně můžete použít [parametry šablony](../ide/template-parameters.md) k použití "bezpečných" názvů pro třídy a obory názvů.

2. Upravte projekt, dokud nebude připraven k exportu jako šablona. Můžete například upravit soubory kódu, které označují, kde má dojít k nahrazení parametrů. Viz [Postup: Nahrazení parametrů v šabloně](../ide/how-to-substitute-parameters-in-a-template.md).

3. V nabídce **Project** zvolte **Exportovat šablonu**.

   Otevře se **Průvodce exportem šablony.**

4. Na stránce **Zvolit typ šablony** vyberte **Šablona projektu**. Vyberte projekt, který chcete exportovat do šablony, a pak zvolte **Další**.

::: moniker range="vs-2017"

5. Na stránce **Vybrat možnosti šablony** zadejte název a volitelný popis, ikonu a náhled obrázku pro šablonu. Tyto položky se zobrazí v dialogovém okně **Nový projekt.** Zvolte **Dokončit**.

   Projekt je exportován do souboru *ZIP* a umístěn do zadaného výstupního umístění a pokud je vybrán, importován do sady Visual Studio.

Chcete-li najít šablonu v dialogovém okně **Nový projekt,** **rozbalte možnost Nainstalováno** a potom rozbalte kategorii, která odpovídá `ProjectType` prvku v souboru *.vstemplate.* Například soubor *.vstemplate,* `<ProjectType>CSharp</ProjectType>` který obsahuje, se ve výchozím nastavení zobrazí v části **Nainstalováno** > **Visual C#**. Šablonu můžete uspořádat do podadresáře typu projektu pouhým vytvořením složky v tomto adresáři a umístěním souboru *ZIP* šablony. Další informace naleznete v [tématu How to: Locate and organize templates](../ide/how-to-locate-and-organize-project-and-item-templates.md).

::: moniker-end

::: moniker range=">=vs-2019"

5. Na stránce **Vybrat možnosti šablony** zadejte název a volitelný popis, ikonu a náhled obrázku pro šablonu. Tyto položky se zobrazí v dialogovém okně, ve kterém vytvoříte nový projekt. Zvolte **Dokončit**.

   Projekt je exportován do souboru *ZIP* a umístěn do zadaného výstupního umístění a pokud je vybrán, importován do sady Visual Studio.

Chcete-li najít šablonu v dialogovém okně, ve kterém vytváříte nový projekt, vyhledejte ji podle názvu nebo procházejte seznamem. (Filtrování na základě jazyka nebo typu projektu není v současné době možné pro uživatelské šablony.)

::: moniker-end

## <a name="other-ways-to-create-project-templates"></a>Další způsoby vytváření šablon projektů

Šablony projektů můžete vytvořit ručně shromážděním souborů, které tvoří projekt, do složky a vytvořením souboru *XML .vstemplate* s příslušnými metadaty. Další informace naleznete v [tématu Postup: Ruční vytváření webových šablon](../ide/how-to-manually-create-web-templates.md).

Pokud máte nainstalovanou sadu Visual Studio SDK, můžete zabalit dokončenou šablonu do souboru VSIX pro nasazení pomocí šablony **Projektu VSIX.** Další informace naleznete [v tématu Začínáme se šablonou projektu VSIX](../extensibility/getting-started-with-the-vsix-project-template.md).

## <a name="see-also"></a>Viz také

- [Vytvoření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
- [Postup: Vytvoření šablon položek](../ide/how-to-create-item-templates.md)
- [Začínáme se šablonou projektu VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)
