---
title: Vytváření šablon vícesouborových položek
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, creating multi-file item templates
- multi-file item templates
- item templates, creating multi-file item templates
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: e8a6e5358a87e3d64b341c89b8ffd4cd3cf3e325
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593730"
---
# <a name="how-to-create-multi-file-item-templates"></a>Postup: Vytvoření šablon vícesouborových položek

Šablony položek mohou určit pouze jednu položku, ale někdy je položka tvořena více soubory. Například šablona položky formulářů systému Windows vyžaduje následující tři soubory:

- Soubor obsahující kód formuláře

- Soubor, který obsahuje informace o návrháři formuláře

- Soubor obsahující vložené prostředky formuláře

Šablony víceřádkových položek vyžadují parametry, aby bylo zajištěno, že při vytvoření položky budou použity správné přípony souborů. Pokud vytvoříte šablonu vícesouborové položky pomocí **Průvodce exportem šablony**, budou tyto parametry automaticky generovány a nebudou nutné žádné další úpravy.

## <a name="use-the-export-template-wizard"></a>Použití Průvodce exportem šablony

Šablonu vícesouborové položky můžete vytvořit stejným způsobem jako šablona položky s jedním souborem. Viz [Postup: Vytvoření šablon položek](../ide/how-to-create-item-templates.md). Na stránce **Vybrat položku k exportu** průvodce vyberte soubor, který má závislé soubory (například soubor formuláře formuláře systému Windows). Průvodce do šablony automaticky zahrne všechny závislé soubory, například soubory návrháře a prostředků.

## <a name="manually-create-a-multi-file-item-template"></a>Ruční vytvoření šablony vícesouborové položky

1. Vytvořte šablonu položky tak, jako byste ručně vytvořili šablonu položky s jedním souborem, ale zahrňte každý soubor, který tvoří položku s více soubory.

1. V souboru *XML .vstemplate* přidejte `ProjectItem` prvek pro každý `TargetFileName` jednotlivý soubor a přidejte atribut k tomuto prvku. Nastavte hodnotu `TargetFileName` atributu na *$fileinputname$. FileExtension*, kde *FileExtension* je přípona souboru, který je součástí šablony. Například:

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
     > Když je položka odvozená z této šablony přidána do projektu, budou názvy souborů odvozeny od názvu, který uživatel zadá v dialogovém okně **Přidat novou položku.**

1. Vyberte soubory, které mají být zahrnuty do šablony, klikněte pravým tlačítkem myši na výběr a zvolte **Odeslat do** > **komprimované (zip) složky**.

   Vybrané soubory jsou komprimovány do souboru *ZIP.*

1. Zkopírujte soubor *ZIP* do umístění šablony položky uživatele. Ve výchozím nastavení je adresář *%USERPROFILE%\Documents\Visual Studio \<Version\>\Templates\ItemTemplates*. Další informace naleznete v [tématu How to: Locate and organize templates](../ide/how-to-locate-and-organize-project-and-item-templates.md).

1. Zavřete Visual Studio a znovu ji otevřete.

1. Vytvořte nový projekt nebo otevřete existující projekt a pak zvolte Přidat**novou položku** **v projektu** > nebo stiskněte **kombinaci kláves Ctrl**+**Shift**+**A**.

   Šablona vícesouborové položky se zobrazí v dialogovém okně **Přidat novou položku.**

## <a name="example"></a>Příklad

Následující příklad ukazuje šablonu Windows Forms. Při vytvoření položky na základě této šablony se názvy tří vytvořených souborů budou shodovat s názvem zadaným v dialogovém okně **Přidat novou položku.**

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

- [Vytvoření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
- [Postup: Vytvoření šablon položek](../ide/how-to-create-item-templates.md)
- [Parametry šablony](../ide/template-parameters.md)
- [Postup: Nahrazení parametrů v šabloně](../ide/how-to-substitute-parameters-in-a-template.md)
