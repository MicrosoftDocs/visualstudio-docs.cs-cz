---
title: 'Postupy: vyhledání a uspořádání šablon projektů a položek | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- project templates [Visual Studio], locations
- custom template locations [Visual Studio]
- item templates, locations
- Visual Studio templates, locations
- project templates [Visual Studio], displaying
- templates [Visual Studio], locations
ms.assetid: 71f9ed52-c9c9-4818-9bce-c279ffaa0438
caps.latest.revision: 28
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b5f55de910eb77ec7ccbd205b78d5c95039e6b39
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651875"
---
# <a name="how-to-locate-and-organize-project-and-item-templates"></a>Postupy: Hledání a organizace projektů a šablon položek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Soubory šablon musí být umístěny v umístění, které aplikace Visual Studio rozpozná, aby se šablony zobrazily v dialogových oknech **Nový projekt** a **Přidat novou položku** . Můžete vytvořit vlastní podkategorie pro šablony, aby se podkategoriely také v uživatelském rozhraní.

## <a name="locating-templates"></a>Hledání šablon
 Ve výchozím nastavení Visual Studio hledá v šablonách projektů a položek dvě umístění. Pokud v těchto umístěních existuje komprimovaný soubor, který obsahuje soubor. vstemplate, šablona se zobrazí v dialogových oknech **Nový projekt** nebo **Přidat novou položku** .

### <a name="installed-templates"></a>Nainstalované šablony
 Ve výchozím nastavení se šablony nainstalované společně s produktem nacházejí v:

- \\*VisualStudioInstallationDirectory*\Common7\IDE\ItemTemplates \\*Language* \\*locale* \

- \\*VisualStudioInstallationDirectory*\Common7\IDE\ProjectTemplates \\*Language* \\*locale \\*

  Například následující adresář obsahuje šablony projektu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pro angličtinu:

  C: \\*VisualStudioInstallationDirectory*\Common7\IDE\ItemTemplates\VisualBasic\1033\

### <a name="custom-templates"></a>Vlastní šablony
 Ve výchozím nastavení se vlastní šablony nacházejí v těchto umístěních:

- \My Documents\Visual Studio *verze*\Templates\ProjectTemplates \\*Language* \

- \My Documents\Visual Studio *verze*\Templates\ItemTemplates \\*Language* \

  Například následující adresář obsahuje vlastní šablony [!INCLUDE[csprcs](../includes/csprcs-md.md)] projektu:

  C:\Documents and Settings\UserName\My Documents \\ < verze sady Visual Studio C#\> \templates\projecttemplates\visual \

  Vlastní šablony neobsahují podadresář pro lokalizované šablony. Výchozí adresář pro vlastní šablony můžete změnit v dialogovém okně **Možnosti** v části **Environment\Projects a řešení**.

## <a name="organizing-templates"></a>Uspořádání šablon
 Kategorie v dialogových oknech **Nový projekt** a **Přidat novou položku** odrážejí struktury adresářů, které existují v umístění nainstalované a vlastní šablony. Tyto adresářové struktury můžete upravit tak, aby byly vaší šablonou uspořádány způsobem, který vám dává smysl.

> [!NOTE]
> Nemůžete vytvořit novou kategorii na úrovni programovacího jazyka. Nové kategorie se dají vytvářet jenom v rámci jednotlivých jazyků.

 Pokud adresářové struktury pro nainstalované a vlastní šablony pro určitý jazyk nemají stejnou strukturu (to znamená, že některé adresáře v jedné složce, které neexistují pod druhou), jsou sady kategorií, které se zobrazí v **novém projektu** . dialog bude fúze všech kategorií.

### <a name="organizing-installed-templates"></a>Uspořádání nainstalovaných šablon
 Nainstalované šablony můžete uspořádat vytvořením podadresářů ve složce programovacího jazyka. Tyto podadresáře se zobrazí v dialogovém okně **Nový projekt** a **Přidat novou položku** jako virtuální složky v rámci jednotlivých jazyků.

##### <a name="to-create-new-installed-project-template-categories"></a>Chcete-li vytvořit nové kategorie nainstalovaných šablon projektu

1. Vytvořte složku ve složce jazyka nainstalovaného adresáře šablon. Chcete-li například vytvořit kategorii Office pro [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] šablony projektů, vytvořte následující adresář:

    \\*VisualStudioInstallationDirectory*\Common7\IDE\ProjectTemplates\VisualBasic\1033\Office\

2. Všechny šablony pro tuto kategorii umístěte do nové složky.

3. Zavřete všechny instance [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

4. V nabídce **Start** klikněte na příkaz **Spustit**, zadejte **příkaz cmd**a klikněte na tlačítko **OK**.

5. Na příkazovém řádku vyhledejte adresář, který obsahuje devenv. exe, a zadejte **devenv/installvstemplates**.

6. Spusťte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

7. V nabídce **soubor** klikněte na příkaz **Nový**a potom klikněte na **projekt**.

8. Ověřte, že se kategorie Office zobrazuje v dialogovém okně **Nový projekt** v podokně **typy projektů** v části [!INCLUDE[vbprvb](../includes/vbprvb-md.md)].

   Můžete také seskupit podmnožinu šablon položek projektu do vlastní složky.

##### <a name="to-create-new-installed-item-template-categories"></a>Vytvoření nových kategorií šablon nainstalované položky

1. Vytvořte složku ve složce jazyka nainstalovaného adresáře šablon. Chcete-li například vytvořit kategorii webu pro šablony [!INCLUDE[csprcs](../includes/csprcs-md.md)] položky, vytvořte následující adresář:

     \\*VisualStudioInstallationDirectory*\Common7\IDE\ItemTemplates\CSharp\1033\Web\

2. Všechny šablony pro tuto kategorii umístěte do nové složky.

3. Zavřete všechny instance [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

4. V nabídce **Start** klikněte na příkaz **Spustit**, zadejte **příkaz cmd**a klikněte na tlačítko **OK**.

5. Na příkazovém řádku vyhledejte adresář, který obsahuje devenv. exe, a zadejte **devenv/Setup**.

6. Spusťte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

7. Vytvořte projekt nebo otevřete existující projekt.

8. V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.

9. Ověřte, zda se kategorie web zobrazuje v dialogovém okně **Přidat novou položku** v podokně **typy projektů** .

### <a name="organizing-custom-templates"></a>Uspořádání vlastních šablon
 Vlastní šablony lze uspořádat do vlastních kategorií přidáním nových složek do umístění vlastní šablony. Dialogové okno **Nový projekt** odráží všechny změny, které provedete v kategoriích šablon.

##### <a name="to-create-new-custom-project-template-categories"></a>Vytvoření nových vlastních kategorií šablon projektů

1. Vytvořte složku ve složce jazyka v adresáři vlastních šablon projektu. Chcete-li například vytvořit kategorii HelloWorld pro šablony [!INCLUDE[csprcs](../includes/csprcs-md.md)], měli byste vytvořit následující adresář:

    \My Documents \\ < Visual Studio verze \> \Templates\ProjectTemplates\CSharp\HelloWorld\

2. Všechny šablony pro tuto kategorii umístěte do nové složky.

3. V nabídce **soubor** klikněte na příkaz **Nový**a potom klikněte na **projekt**.

4. Ověřte, že se kategorie HelloWorld zobrazí v dialogovém okně **Nový projekt** v podokně **typy projektů** v části [!INCLUDE[csprcs](../includes/csprcs-md.md)].

   Můžete také seskupit podmnožinu šablon vlastních položek do vlastní složky.

##### <a name="to-create-new-custom-item-template-categories"></a>Vytvoření nových kategorií šablon vlastních položek

1. Vytvořte složku ve složce jazyka v adresáři šablony vlastní položky. Chcete-li například vytvořit kategorii HelloWorld pro šablony [!INCLUDE[csprcs](../includes/csprcs-md.md)], vytvořte následující adresář:

     \My Documents \\ < Visual Studio verze \> \Templates\ItemTemplates\CSharp\HelloWorld\

2. Všechny šablony pro tuto kategorii umístěte do nové složky.

3. Vytvořte projekt nebo otevřete existující projekt.

4. V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.

5. Ověřte, že se kategorie HelloWorld zobrazí v dialogovém okně **Přidat novou položku** v podokně **typy projektů** .

### <a name="displaying-templates-in-parent-categories"></a>Zobrazení šablon v nadřazených kategoriích
 Můžete povolit šablony v podkategoriích, aby se zobrazily v jejich nadřazených kategoriích pomocí elementu `NumberOfParentCategoriesToRollUp` v souboru. vstemplate. Tyto kroky jsou u šablon projektů a položek identické.

##### <a name="to-display-templates-in-parent-categories"></a>Zobrazení šablon v nadřazených kategoriích

1. Vyhledejte soubor. zip, který obsahuje šablonu.

2. Extrahujte soubor. zip.

3. Otevřete soubor. vstemplate v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

4. Do prvku `TemplateData` přidejte prvek `NumberOfParentCategoriesToRollUp`. Například následující kód nastaví šablonu jako viditelnou v nadřazené kategorii, ale ne vyšší.

    ```
    <TemplateData>
        ...
        <NumberOfParentCategoriesToRollUp>
            1
        </NumberOfParentCategoriesToRollUp>
        ...
    </TemplateData>
    ```

5. Uložte a zavřete soubor. vstemplate.

6. Vyberte soubory v šabloně, klikněte pravým tlačítkem na výběr, klikněte na **Odeslat do**a pak klikněte na **Komprimovaná složka (ZIP)** . Soubory jsou komprimovány do souboru ZIP.

7. Odstraňte extrahované soubory šablon a starý soubor Template. zip.

8. Vložte nový soubor. zip do adresáře, kde byl odstraněný soubor. zip.

## <a name="see-also"></a>Viz také
 [Přizpůsobení šablon šablony](../ide/customizing-project-and-item-templates.md) [Visual Studio šablona schématu reference](../extensibility/visual-studio-template-schema-reference.md) [NumberOfParentCategoriesToRollUp (šablony sady Visual Studio)](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md) [Postupy: vytváření šablon projektů](../ide/how-to-create-project-templates.md) [Postupy: vytváření šablon položek](../ide/how-to-create-item-templates.md)
