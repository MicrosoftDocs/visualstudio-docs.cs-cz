---
title: Hledání šablon
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- project templates [Visual Studio], locations
- item templates [Visual Studio], locations
- template locations [Visual Studio]
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f9035e63fd172727f3bfae44e18a0727599d4edc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645883"
---
# <a name="how-to-locate-and-organize-project-and-item-templates"></a>Postupy: vyhledání a uspořádání šablon projektů a položek

Soubory šablon musí být umístěny ve známém umístění, aby byly zobrazeny v dialogových oknech Nový projekt a nová položka.

::: moniker range="vs-2017"

Můžete také vytvořit vlastní podkategorie v umístění uživatelské šablony a kategorie se zobrazí v dialogových oknech **Nový projekt** a **Přidat novou položku** .

::: moniker-end

## <a name="locate-templates"></a>Hledání šablon

Nainstalované šablony a uživatelské šablony jsou uloženy ve dvou různých umístěních.

### <a name="installed-templates"></a>Nainstalované šablony

Ve výchozím nastavení jsou šablony nainstalované se sadou Visual Studio umístěny v těchto umístěních:

::: moniker range="vs-2017"

- *% ProgramFiles (x86)% \\Microsoft Visual Studio \\2017 \\ \<edition > \\Common7 \IDE\ProjectTemplates \\ < jazyk \> \\ < ID národního prostředí \>*

- *% ProgramFiles (x86)% \\Microsoft Visual Studio \\2017 \\ \<edition > \Common7\IDE\ItemTemplates \\ < language \> \\ < ID národního prostředí \>*

Například následující adresář obsahuje šablony Visual Basic položek pro angličtinu (LCID 1033):

*C: \\Program soubory (x86) \\Microsoft sady Visual Studio \\2017 \\Community \\Common7 \\IDE \\ItemTemplates \\VisualBasic \\1033*

::: moniker-end

::: moniker range=">=vs-2019"

- *% ProgramFiles (x86)% \\Microsoft Visual Studio \\2019 \\ \<edition > \\Common7 \IDE\ProjectTemplates \\ < jazyk \> \\ < ID národního prostředí \>*

- *% ProgramFiles (x86)% \\Microsoft Visual Studio \\2019 \\ \<edition > \Common7\IDE\ItemTemplates \\ < language \> \\ < ID národního prostředí \>*

Například následující adresář obsahuje šablony Visual Basic položek pro angličtinu (LCID 1033):

*C: \\Program soubory (x86) \\Microsoft sady Visual Studio \\2019 \\Community \\Common7 \\IDE \\ItemTemplates \\VisualBasic \\1033*

::: moniker-end

### <a name="user-templates"></a>Uživatelské šablony

Pokud přidáte komprimovaný soubor ( *. zip*), který obsahuje soubor *. vstemplate* do adresáře šablony uživatele, šablona se zobrazí v dialogových oknech Nový projekt a nová položka. Ve výchozím nastavení se šablony uživatelů nacházejí v těchto umístěních:

::: moniker range="vs-2017"

- *%USERPROFILE%\Documents\Visual Studio 2017 \ Templates\ProjectTemplates*

- *%USERPROFILE%\Documents\Visual Studio 2017 \ Templates\ItemTemplates*

Například následující adresář má šablony uživatelských projektů pro C#:

- *C:\Users\UserName\Documents\Visual Studio 2017 \ Templates\ProjectTemplates\VisualC#*

::: moniker-end

::: moniker range=">=vs-2019"

- *%USERPROFILE%\Documents\Visual Studio 2019 \ Templates\ProjectTemplates*

- *%USERPROFILE%\Documents\Visual Studio 2019 \ Templates\ItemTemplates*

Například následující adresář má šablony uživatelských projektů pro C#:

- *C:\Users\UserName\Documents\Visual Studio 2019 \ Templates\ProjectTemplates\VisualC#*

::: moniker-end

> [!TIP]
> Můžete změnit známé umístění pro šablony uživatelů v **nástrojích**  > **Možnosti**  > **projekty a řešení**  > **umístění**.

::: moniker range="vs-2017"

## <a name="organize-templates"></a>Uspořádání šablon

Kategorie v dialogových oknech **Nový projekt** a **Přidat novou položku** odrážejí struktury adresářů, které existují v nainstalované šabloně a umístění šablon uživatele. Uživatelské šablony lze uspořádat do vlastních kategorií přidáním nových složek do adresáře šablon uživatele. Dialogová okna **Nový projekt** a **Přidat novou položku** zobrazí všechny změny, které provedete v kategoriích uživatelských šablon.

> [!NOTE]
> Nemůžete vytvořit novou kategorii na úrovni programovacího jazyka. Nové kategorie se dají vytvářet jenom v rámci jednotlivých jazyků.

### <a name="create-new-user-project-template-categories"></a>Vytvořit nové kategorie šablon projektů uživatele

1. Vytvořte složku ve složce programovací jazyk v adresáři šablon uživatelských projektů. Chcete-li například vytvořit kategorii **HelloWorld** pro C# šablony projektu, vytvořte následující adresář:

    - *\%USERPROFILE% \ Documents\Visual Studio \<Version \> \Templates\ProjectTemplates\Visual C#\HelloWorld*

1. Všechny šablony pro tuto kategorii umístěte do nové složky.

1. V nabídce **soubor** vyberte možnost **Nový** > **projekt**.

   Kategorie **HelloWorld** se zobrazí v dialogovém okně **Nový projekt** v části **nainstalované** > **vizuál C#** .

### <a name="create-new-user-item-template-categories"></a>Vytvořit nové kategorie šablon uživatelských položek

1. Vytvořte složku ve složce programovací jazyk v adresáři šablon položky uživatele. Chcete-li například vytvořit kategorii **HelloWorld** pro C# šablony položek, vytvořte následující adresář:

    - *\%USERPROFILE% \ Documents\Visual Studio \<Version \> \Templates\ItemTemplates\Visual C#\HelloWorld*

1. Všechny šablony pro tuto kategorii umístěte do nové složky.

1. Vytvořte projekt nebo otevřete existující projekt. Pak v nabídce **projekt** zvolte možnost **Přidat novou položku**.

   Kategorie **HelloWorld** se zobrazí v dialogovém okně **Přidat novou položku** v části **nainstalované** > **vizuální C# položky**.

### <a name="display-templates-in-parent-categories"></a>Zobrazit šablony v nadřazených kategoriích

Můžete povolit šablony v podkategoriích, aby se zobrazily v jejich nadřazených kategoriích pomocí elementu `NumberOfParentCategoriesToRollUp` v souboru *. vstemplate* . Tyto kroky jsou u šablon projektů a položek stejné.

1. Vyhledejte soubor *. zip* , který obsahuje šablonu.

1. Extrahujte soubor *. zip* .

1. Otevřete soubor *. vstemplate* v aplikaci Visual Studio.

1. Do prvku `TemplateData` přidejte prvek `NumberOfParentCategoriesToRollUp`. Například následující kód nastaví šablonu jako viditelnou v nadřazené kategorii, ale ne vyšší.

    ```xml
    <TemplateData>
        ...
        <NumberOfParentCategoriesToRollUp>
            1
        </NumberOfParentCategoriesToRollUp>
        ...
    </TemplateData>
    ```

1. Uložte a zavřete soubor *. vstemplate* .

1. Vyberte soubory v šabloně, klikněte pravým tlačítkem na výběr a zvolte **Odeslat do** > **Komprimovaná složka (ZIP)** .

   Soubory jsou komprimovány do souboru *zip* .

1. Odstraňte extrahované soubory šablon a starý soubor template *. zip* .

1. Vložte nový soubor *. zip* do adresáře, kde byl odstraněný soubor *. zip* .

::: moniker-end

## <a name="see-also"></a>Viz také:

- [Přizpůsobení šablon](../ide/customizing-project-and-item-templates.md)
- [Referenční dokumentace schématu šablon sady Visual Studio (rozšiřitelnost)](../extensibility/visual-studio-template-schema-reference.md)
- [NumberOfParentCategoriesToRollUp (šablony sady Visual Studio)](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)
- [Postupy: vytváření šablon projektů](../ide/how-to-create-project-templates.md)
- [Postupy: vytváření šablon položek](../ide/how-to-create-item-templates.md)