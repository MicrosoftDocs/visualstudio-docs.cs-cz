---
title: Vytváření šablon položek s více soubory
ms.date: 01/02/2018
ms.topic: how-to
helpviewer_keywords:
- Visual Studio templates, creating multi-file item templates
- multi-file item templates
- item templates, creating multi-file item templates
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 4a4f0c50fc0a3fe21da560356d3551ca85ef9d66
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85284422"
---
# <a name="how-to-create-multi-file-item-templates"></a>Postupy: vytváření šablon položek s více soubory

Šablony položek mohou určovat pouze jednu položku, někdy se však položka skládá z více souborů. Například šablona model Windows Forms položky vyžaduje následující tři soubory:

- Soubor, který obsahuje kód pro formulář

- Soubor, který obsahuje informace o návrháři pro formulář

- Soubor, který obsahuje vložené prostředky pro formulář

Šablony položek s více soubory vyžadují parametry, aby se zajistilo, že se při vytvoření položky použijí správné přípony souborů. Vytvoříte-li šablonu položky s více soubory pomocí **Průvodce exportem šablony**, jsou tyto parametry automaticky generovány a žádné další úpravy nejsou požadovány.

## <a name="use-the-export-template-wizard"></a>Použití Průvodce exportem šablony

Šablonu položky s více soubory můžete vytvořit stejným způsobem jako šablonu položky s jedním souborem. Viz [Postupy: vytváření šablon položek](../ide/how-to-create-item-templates.md). Na stránce **Vyberte položku, která má být exportována** v průvodci vyberte soubor, který obsahuje závislé soubory (například soubor formuláře model Windows Forms). Průvodce automaticky obsahuje všechny závislé soubory, jako jsou například návrháře a soubory prostředků, v šabloně.

## <a name="manually-create-a-multi-file-item-template"></a>Ruční vytvoření šablony položek s více soubory

1. Vytvořte šablonu položky, protože byste mohli ručně vytvořit šablonu položky s jedním souborem, ale zahrnout každý soubor, který tvoří položku s více soubory.

1. V souboru XML *. vstemplate* přidejte `ProjectItem` element pro každý jednotlivý soubor a přidejte do `TargetFileName` tohoto prvku atribut. Nastavte hodnotu `TargetFileName` atributu na *$fileinputname $. Přípona*souboru, kde *přípona* souboru je přípona souboru, který je součástí šablony. Příklad:

    ```xml
    <ProjectItem TargetFileName="$fileinputname$.vb">
        Form1.vb
    </ProjectItem>
    <ProjectItem TargetFileName="$fileinputname$.Designer.vb">
        Form1.Designer.vb
    </ProjectItem>
    <ProjectItem TargetFileName="$fileinputname$.resx">
        Form1.resx
    </ProjectItem>
    ```

     > [!NOTE]
     > Když je položka odvozená z této šablony přidána do projektu, názvy souborů budou odvozeny z názvu, který uživatel zadá v dialogovém okně **Přidat novou položku** .

1. Vyberte soubory, které chcete zahrnout do šablony, klikněte pravým tlačítkem myši na výběr a zvolte **Odeslat do**  >  **komprimované složky (ZIP)**.

   Soubory, které jste vybrali, se komprimují do souboru *zip* .

1. Zkopírujte soubor *. zip* do umístění šablony položky uživatele. Ve výchozím nastavení se jedná o adresář *%UserProfile%\Documents\Visual Studio \<Version\> \Templates\ItemTemplates*. Další informace najdete v tématu [Postupy: hledání a organizace šablon](../ide/how-to-locate-and-organize-project-and-item-templates.md).

1. Zavřete Visual Studio a potom ho znovu otevřete.

1. Vytvořte nový projekt nebo otevřete existující projekt a pak zvolte **projekt**  >  **Přidat novou položku** nebo stiskněte klávesovou **zkratku CTRL** + **SHIFT** + **a**.

   Šablona položky s více soubory se zobrazí v dialogovém okně **Přidat novou položku** .

## <a name="example"></a>Příklad

Následující příklad ukazuje šablonu model Windows Forms. Když je na základě této šablony vytvořena položka, názvy tří vytvořených souborů budou odpovídat názvu zadanému v dialogovém okně **Přidat novou položku** .

```xml
<VSTemplate Version="2.0.0" Type="Item"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>Multi-file Item Template</Name>
        <Icon>Icon.ico</Icon>
        <Description>An example of a multi-file item template</Description>
        <ProjectType>VisualBasic</ProjectType>
    </TemplateData>
    <TemplateContent>
        <ProjectItem TargetFileName="$fileinputname$.vb" SubType="Form">
            Form1.vb
        </ProjectItem>
        <ProjectItem TargetFileName="$fileinputname$.Designer.vb">
            Form1.Designer.vb
        </ProjectItem>
        <ProjectItem TargetFileName="$fileinputname$.resx">
            Form1.resx
        </ProjectItem>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Viz také

- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
- [Postupy: vytváření šablon položek](../ide/how-to-create-item-templates.md)
- [Parametry šablony](../ide/template-parameters.md)
- [Postupy: nahrazení parametrů v šabloně](../ide/how-to-substitute-parameters-in-a-template.md)
