---
title: Vytváření šablon položek s více soubory
ms.date: 01/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, creating multi-file item templates
- multi-file item templates
- item templates, creating multi-file item templates
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: dd2cbe6d7a0ff586c0e673a6eb0e3d42aa4dec4e
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065406"
---
# <a name="how-to-create-multi-file-item-templates"></a>Postupy: vytváření šablon položek s více soubory

Šablony položek může zadat jenom jednu položku, ale někdy položky skládá z více souborů. Například šablonu položky Windows Forms vyžaduje následující tři soubory:

- Soubor, který obsahuje kód pro formulář

- Soubor, který obsahuje informace o návrháři formuláře

- Soubor, který obsahuje vložené prostředky pro formulář

Šablony položek s více soubory vyžadují parametry k zajištění toho, že rozšíření správného souboru se používají při vytvoření položky. Pokud jste vytvořili pomocí šablon položek s více soubory **Průvodce exportem šablony**tyto parametry jsou automaticky generovány a žádné další úpravy je povinný.

## <a name="to-create-a-multi-file-item-template-by-using-the-export-template-wizard"></a>Vytvoření šablony položek s více soubory s použitím Průvodce exportem šablony

Stejným způsobem můžete vytvořit šablonu vícesouborové položce, stejně jako šablonu položky jedním souborem. Zobrazit [postup: Tvorba šablon položek s](../ide/how-to-create-item-templates.md). Na **vyberte položky, které chcete exportovat** stránku průvodce, vyberte soubor, který má závislé soubory (například soubor formuláře Windows Forms). Průvodce automaticky obsahuje všechny závislé soubory, jako je například návrháře a soubory prostředků v šabloně.

## <a name="to-manually-create-a-multi-file-item-template"></a>Ruční vytvoření šablony položek s více soubory

1. Vytvořte šablonu položky, jako je by ručně vytvořit šablonu položky jeden soubor, ale zahrnout všechny soubory, které představuje vícesouborové položce.

1. V *.vstemplate* XML přidejte `ProjectItem` – element pro jednotlivé uživatele a přidejte `TargetFileName` atribut na tento element. Nastavte hodnotu `TargetFileName` atribut *$fileinputname$. FileExtension*, kde *FileExtension* je příponu souboru, který bude zahrnut v šabloně. Příklad:

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
     > Když do projektu se přidá položka odvozená z této šablony, názvy souborů odvodí z názvu, který uživatel zadá **přidat novou položku** dialogové okno.

1. Vyberte soubory, které chcete zahrnout do vaší šablony, klikněte pravým tlačítkem na výběr a zvolte **odeslat** > **komprimovanou složku (ZIP)**.

   Do jsou komprimované soubory, které jste vybrali *ZIP* souboru.

1. Kopírovat *ZIP* soubor do umístění šablon položek uživatele. Ve výchozím adresáři je *%USERPROFILE%\Documents\Visual Studio \<verze\>\Templates\ItemTemplates*. Další informace najdete v tématu [postupy: hledání a organizace šablon](../ide/how-to-locate-and-organize-project-and-item-templates.md).

1. Zavřete sadu Visual Studio a znovu ho otevřít.

1. Vytvořte nový projekt, nebo otevřete existující projekt a pak zvolte **projektu** > **přidat novou položku** nebo stiskněte klávesu **Ctrl** +  **SHIFT**+**A**.

   Šablony položek s více soubory se zobrazí v **přidat novou položku** dialogové okno.

## <a name="example"></a>Příklad

Následující příklad ukazuje šablonu formulářů Windows. Když je vytvořena položka na základě této šablony, názvy tři soubory vytvořené bude shodovat s názvem zadaného v **přidat novou položku** dialogové okno.

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

## <a name="see-also"></a>Viz také:

- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
- [Postupy: Tvorba šablon položek](../ide/how-to-create-item-templates.md)
- [Parametry šablony](../ide/template-parameters.md)
- [Postupy: nahrazení parametrů v šabloně](../ide/how-to-substitute-parameters-in-a-template.md)