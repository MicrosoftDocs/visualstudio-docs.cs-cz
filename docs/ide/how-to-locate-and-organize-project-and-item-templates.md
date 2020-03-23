---
title: Vyhledání šablon
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- project templates [Visual Studio], locations
- item templates [Visual Studio], locations
- template locations [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 480f583bb997a19bc84fcfbe6824c12a3c638784
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591044"
---
# <a name="how-to-locate-and-organize-project-and-item-templates"></a>Postup: Vyhledání a uspořádání šablon projektů a položek

Aby se soubory šablon mohly zobrazit v novém projektu a v dialogových oknech nové položky, musí být umístěny na známém místě.

::: moniker range="vs-2017"

Můžete také vytvořit vlastní podkategorie v umístění šablony uživatele a kategorie se zobrazí v dialogových oknech **Nový projekt** a Přidat **novou položku.**

::: moniker-end

## <a name="locate-templates"></a>Vyhledání šablon

Nainstalované šablony a uživatelské šablony jsou uloženy ve dvou různých umístěních.

### <a name="installed-templates"></a>Nainstalované šablony

Ve výchozím nastavení jsou šablony nainstalované v sadě Visual Studio umístěny v:

::: moniker range="vs-2017"

- *%ProgramFiles(x86)%\\vydání\\Microsoft Visual\\\<Studio \\2017>Common7\IDE\ProjectTemplates\\<Jazyk\> \\<ID národního prostředí\>*

- *%ProgramFiles(x86)%\\Vydání\\Microsoft Visual\\\<Studia 2017>\Common7\IDE\Šablony položek\\<jazyk\> \\<ID národního prostředí\>*

Například následující adresář má šablony položek jazyka Visual Basic pro angličtinu (LCID 1033):

*C:\\\\Programové soubory (x86) Microsoft Visual Studio\\\\\\\\\\2017\\Community\\Common7 IDE ItemTemplates VisualBasic 1033*

::: moniker-end

::: moniker range=">=vs-2019"

- *%ProgramFiles(x86)%\\vydání\\Microsoft Visual\\\<Studio \\2019>Common7\IDE\ProjectTemplates\\<Jazyk\> \\<ID národního prostředí\>*

- *%ProgramFiles(x86)%\\Vydání\\Microsoft Visual\\\<Studia 2019>\Common7\IDE\Šablony položek\\<jazyk\> \\<ID národního prostředí\>*

Například následující adresář má šablony položek jazyka Visual Basic pro angličtinu (LCID 1033):

*C:\\\\Programové soubory (x86) Microsoft Visual Studio\\\\\\\\\\2019\\Community\\Common7 IDE ItemTemplates VisualBasic 1033*

::: moniker-end

### <a name="user-templates"></a>Uživatelské šablony

Pokud přidáte komprimovaný soubor (*ZIP),* který obsahuje soubor *.vstemplate* do adresáře šablony uživatele, zobrazí se šablona v novém projektu a v dialogových oknech nové položky. Ve výchozím nastavení jsou uživatelské šablony umístěny v:

::: moniker range="vs-2017"

- *%USERPROFILE%\Documents\Visual Studio 2017\Templates\ProjectTemplates*

- *%USERPROFILE%\Documents\Visual Studio 2017\Templates\ItemTemplates*

Například následující adresář obsahuje šablony uživatelských projektů pro C#:

- *C:\Users\UserName\Documents\Visual Studio 2017\Templates\ProjectTemplates\Visual C #*

::: moniker-end

::: moniker range=">=vs-2019"

- *%USERPROFILE%\Documents\Visual Studio 2019\Templates\ProjectTemplates*

- *%USERPROFILE%\Documents\Visual Studio 2019\Templates\ItemTemplates*

Například následující adresář obsahuje šablony uživatelských projektů pro C#:

- *C:\Users\UserName\Documents\Visual Studio 2019\Templates\ProjectTemplates\Visual C #*

::: moniker-end

> [!TIP]
> Známé umístění uživatelských šablon můžete změnit v části**Projekty**a > **umístění**řešení**možnosti** >  **nástroje** > .

::: moniker range="vs-2017"

## <a name="organize-templates"></a>Uspořádání šablon

Kategorie v dialogových oknech **Nový projekt** a Přidat **novou položku** odrážejí struktury adresářů, které existují v umístěních nainstalované šablony a uživatelské šablony. Uživatelské šablony lze uspořádat do svých vlastních kategorií přidáním nových složek do adresáře uživatelských šablon. V dialogových oknech **Nový projekt** a Přidat **novou položku** se zobrazí všechny změny, které provedete v kategoriích uživatelských šablon.

> [!NOTE]
> Novou kategorii nelze vytvořit na úrovni programovacího jazyka. Nové kategorie lze vytvořit pouze v rámci každého jazyka.

### <a name="create-new-user-project-template-categories"></a>Vytvořit nové kategorie šablon uživatelského projektu

1. Vytvořte složku ve složce programovacího jazyka v adresáři šablony projektu uživatele. Chcete-li například vytvořit kategorii **HelloWorld** pro šablony projektu jazyka C#, vytvořte následující adresář:

    - *\%USERPROFILE%\Documents\Visual Studio \<Version\>\Templates\ProjectTemplates\Visual C#\HelloWorld*

1. Umístěte všechny šablony pro tuto kategorii do nové složky.

1. V nabídce **Soubor** zvolte **Nový** > **projekt**.

   Kategorie **HelloWorld** se zobrazí v dialogovém okně **Nový projekt** v části **Nainstalovaný** > **visual c#**.

### <a name="create-new-user-item-template-categories"></a>Vytvořit nové kategorie šablon uživatelských položek

1. Vytvořte složku ve složce programovacího jazyka v adresáři šablony uživatelských položek. Chcete-li například vytvořit kategorii **HelloWorld** pro šablony položek jazyka C#, vytvořte následující adresář:

    - *\%USERPROFILE%\Documents\Visual Studio \<Version\>\Templates\ItemTemplates\Visual C#\HelloWorld*

1. Umístěte všechny šablony pro tuto kategorii do nové složky.

1. Vytvořte projekt nebo otevřete existující projekt. Potom v nabídce **Projekt** zvolte **Přidat novou položku**.

   Kategorie **HelloWorld** se zobrazí v dialogovém okně **Přidat novou položku** v části **Nainstalované** > **položky Visual C#**.

### <a name="display-templates-in-parent-categories"></a>Zobrazení šablon v nadřazených kategoriích

Pomocí `NumberOfParentCategoriesToRollUp` prvku v souboru *.vstemplate* můžete povolit zobrazení šablon v podkategoriích v nadřazených kategoriích. Tyto kroky jsou stejné pro šablony projektů a šablony položek.

1. Vyhledejte soubor *ZIP* obsahující šablonu.

1. Extrahujte soubor *ZIP.*

1. Otevřete soubor *.vstemplate* v sadě Visual Studio.

1. V `TemplateData` prvku přidejte `NumberOfParentCategoriesToRollUp` prvek. Například následující kód zviditelní šablonu v nadřazené kategorii, ale ne vyšší.

    ```xml
    <TemplateData>
        ...
        <NumberOfParentCategoriesToRollUp>
            1
        </NumberOfParentCategoriesToRollUp>
        ...
    </TemplateData>
    ```

1. Uložte a zavřete soubor *.vstemplate.*

1. Vyberte soubory v šabloně, klepněte pravým tlačítkem myši na výběr a zvolte **Odeslat do** > **komprimované (zip) složky**.

   Soubory jsou komprimovány do souboru *ZIP.*

1. Odstraňte extrahované soubory šablon a starý soubor *ZIP* šablony.

1. Vložte nový soubor *ZIP* do adresáře, ve které byl odstraněn ý soubor *ZIP.*

::: moniker-end

## <a name="see-also"></a>Viz také

- [Přizpůsobení šablon](../ide/customizing-project-and-item-templates.md)
- [Odkaz na schéma šablony sady Visual Studio (rozšiřitelnost)](../extensibility/visual-studio-template-schema-reference.md)
- [NumberOfParentCategoriesToRollUp (šablony sady Visual Studio)](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)
- [Postup: Vytvoření šablon projektů](../ide/how-to-create-project-templates.md)
- [Postup: Vytvoření šablon položek](../ide/how-to-create-item-templates.md)
