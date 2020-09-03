---
title: 'Postupy: vytváření šablon položek s více soubory | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, creating multi-file item templates
- multi-file item templates
- item templates, creating multi-file item templates
ms.assetid: fe3c4257-e383-4c80-b8af-c5c521959c33
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e70039f361ac3410a8ddcccb0f139d8bdcb32ed9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668095"
---
# <a name="how-to-create-multi-file-item-templates"></a>Postupy: Tvorba šablon položek s více soubory
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Šablony položek mohou určovat pouze jednu položku, někdy se však položka skládá z více souborů. Například šablona položky model Windows Forms pro Visual Basic vyžaduje následující tři soubory:

- Soubor. vb, který obsahuje kód pro formulář.

- Soubor. Designer. vb, který obsahuje informace o návrháři formuláře.

- Soubor. resx, který obsahuje vložené prostředky pro formulář.

  Šablony položek s více soubory vyžadují parametry, aby bylo zajištěno, že budou použity správné přípony názvů souborů, když je položka vytvořena v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Pokud vytvoříte šablonu položky pomocí průvodce **exportem šablony** , tyto parametry se automaticky vygenerují a žádné další úpravy se nevyžadují. Následující kroky vysvětlují, jak použít parametry k zajištění toho, aby se vytvořily správné přípony názvů souborů.

### <a name="to-manually-create-a-multi-file-item-template"></a>Ruční vytvoření šablony položek s více soubory

1. Vytvořte šablonu položky, protože byste vytvořili šablonu položky s jedním souborem. Další informace naleznete v tématu [How to: Create Item Templates](../ide/how-to-create-item-templates.md).

2. Přidejte `TargetFileName` atributy ke každému `ProjectItem` elementu. Nastavte hodnoty `TargetFileName` atributů na $fileinputname $.* Přípona*souboru, kde *přípona* souboru je přípona názvu souboru, který je součástí šablony. Příklad:

    ```
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

     Když je položka odvozená z této šablony přidána do projektu, názvy souborů budou založené na názvu, který uživatel zadal v dialogovém okně **Přidat novou položku** .

3. Vyberte soubory, které chcete zahrnout do šablony, klikněte pravým tlačítkem myši na výběr, klikněte na **Odeslat do**a pak klikněte na **zkomprimovanou (ZIP) složku**. Soubory, které jste vybrali, se komprimují do souboru ZIP.

4. Vložte soubor. zip do umístění šablony položky uživatele. Ve výchozím nastavení se jedná o adresář \My Documents\Visual Studio *verze*\Templates\ItemTemplates \\ . Další informace najdete v tématu [Postupy: hledání a organizace šablon](../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="example"></a>Příklad
 Následující příklad ukazuje [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] šablonu model Windows Forms. Když je na základě této šablony vytvořena položka, názvy tří vytvořených souborů budou odpovídat názvu zadanému v dialogovém okně **Přidat novou položku** .

```
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
 [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md) [Postupy: vytvoření šablon položek](../ide/how-to-create-item-templates.md) [parametry šablony](../ide/template-parameters.md) [Postupy: nahrazení parametrů v šabloně](../ide/how-to-substitute-parameters-in-a-template.md)
