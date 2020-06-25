---
title: Vytváření šablon projektu
ms.date: 01/02/2018
ms.topic: how-to
f1_keywords:
- VS.ExportTemplateWizard
helpviewer_keywords:
- project templates [Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: e6f168244971a348cdb7938af463538d0fa2acaf
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85284383"
---
# <a name="how-to-create-project-templates"></a>Postupy: vytváření šablon projektů

V tomto tématu se dozvíte, jak vytvořit šablonu pomocí **Průvodce exportem šablony**, který zabalí šablonu do souboru *. zip* .

## <a name="use-the-export-template-wizard"></a>Použití Průvodce exportem šablony

1. Vytvořte projekt.

    > [!NOTE]
    > Při pojmenování projektu, který bude zdrojem pro šablonu, použijte pouze platné znaky identifikátoru. V opačném případě mohou v projektech, které jsou vytvořeny z šablony, dojít k chybám kompilace. Další informace o platných znacích identifikátorů naleznete v tématu [deklarované názvy elementů (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names) nebo [identifikátory (C++)](/cpp/cpp/identifiers-cpp). Alternativně můžete použít [parametry šablony](../ide/template-parameters.md) k použití "bezpečných" názvů pro třídy a obory názvů.

2. Upravte projekt, dokud nebude připravený k exportu jako šablony. Například můžete chtít upravit soubory kódu, aby označovaly, kde by mělo dojít k nahrazení parametru. Viz [Postupy: nahrazení parametrů v šabloně](../ide/how-to-substitute-parameters-in-a-template.md).

3. V nabídce **projekt** vyberte položku **Exportovat šablonu**.

   Otevře se **Průvodce exportem šablony** .

4. Na stránce **zvolit typ šablony** vyberte možnost **Šablona projektu**. Vyberte projekt, který chcete exportovat do šablony, a klikněte na tlačítko **Další**.

::: moniker range="vs-2017"

5. Na stránce **Vybrat možnosti šablony** zadejte název a volitelný popis, ikonu a náhled obrázku pro šablonu. Tyto položky se zobrazí v dialogovém okně **Nový projekt** . Klikněte na tlačítko **Dokončit**.

   Projekt je exportován do souboru *. zip* a umístěn do zadaného umístění výstupu a v případě, že je vybrán, importován do sady Visual Studio.

Chcete-li najít šablonu v dialogovém okně **Nový projekt** , rozbalte položku **nainstalováno** a poté rozbalte kategorii, která odpovídá `ProjectType` prvku v souboru *. vstemplate* . Například soubor *. vstemplate* , který obsahuje, `<ProjectType>CSharp</ProjectType>` se zobrazí ve výchozím nastavení v části **nainstalováno**  >  **Visual C#**. Šablonu můžete uspořádat do podadresáře typu projektu pouhým vytvořením složky v tomto adresáři a umístěním souboru *. zip* šablony. Další informace najdete v tématu [Postupy: hledání a organizace šablon](../ide/how-to-locate-and-organize-project-and-item-templates.md).

::: moniker-end

::: moniker range=">=vs-2019"

5. Na stránce **Vybrat možnosti šablony** zadejte název a volitelný popis, ikonu a náhled obrázku pro šablonu. Tyto položky se zobrazí v dialogovém okně, kde vytvoříte nový projekt. Klikněte na tlačítko **Dokončit**.

   Projekt je exportován do souboru *. zip* a umístěn do zadaného umístění výstupu a v případě, že je vybrán, importován do sady Visual Studio.

Chcete-li najít šablonu v dialogovém okně, kde vytvoříte nový projekt, vyhledejte je podle názvu nebo posuňte seznam se seznamem. (Filtrování založené na jazyce nebo typu projektu není aktuálně možné pro uživatelské šablony.)

::: moniker-end

## <a name="other-ways-to-create-project-templates"></a>Další způsoby vytváření šablon projektů

Můžete vytvořit šablony projektu ručně shromažďováním souborů, které projekt tvoří, do složky a vytvořením souboru XML *. vstemplate* s příslušnými metadaty. Další informace najdete v tématu [Postupy: Ruční vytvoření webových šablon](../ide/how-to-manually-create-web-templates.md).

Pokud máte nainstalovanou sadu Visual Studio SDK, můžete zabalit dokončenou šablonu do souboru VSIX pro nasazení pomocí šablony **projektu VSIX** . Další informace najdete v tématu [Začínáme se šablonou projektu VSIX](../extensibility/getting-started-with-the-vsix-project-template.md).

## <a name="see-also"></a>Viz také

- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
- [Postupy: vytváření šablon položek](../ide/how-to-create-item-templates.md)
- [Začínáme se šablonou projektu VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)
