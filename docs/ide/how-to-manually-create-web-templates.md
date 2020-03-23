---
title: Vytváření webových šablon
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, Web
- templates [Visual Studio], Web
- Web templates [Visual Studio]
- project templates [Visual Studio], Web
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 245b20dd9cad465129d6c79c38e53b6379c2c09c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591005"
---
# <a name="how-to-manually-create-web-templates"></a>Postup: Ruční vytváření webových šablon

Vytvoření webové šablony se liší od vytváření jiných druhů šablon. Vzhledem k tomu, že šablony webových projektů se zobrazují v dialogovém okně **Přidat nový web** a položky webového projektu jsou rozděleny do kategorií podle programovacího jazyka, musí soubor *vstemplate* určit šablonu jako webovou šablonu a identifikovat programovací jazyk.

> [!NOTE]
> Webové šablony musí obsahovat prázdný soubor *.webproj* a musí být odkazovány `File` v souboru *vstemplate* v atributu `Project` prvku. Přestože webové projekty nevyžadují soubor projektu *.proj,* je nutné vytvořit tento soubor se zakázaným inzerováním, aby webová šablona fungovala správně.

## <a name="to-manually-create-a-web-template"></a>Ruční vytvoření webové šablony

1. Vytvořte webový projekt.

2. Upravte nebo odstraňte soubory v projektu nebo přidejte do projektu nové soubory.

3. Vytvořte soubor XML a uložte jej s příponou *vstemplate,* ve stejném adresáři jako váš projekt. Nepřidávejte jej do projektu v sadě Visual Studio.

4. Upravte soubor *XML vstemplate* a zajistěte metadata šablony projektu. Další informace naleznete v [následujícím příkladu](#example).

5. Vyhledejte `ProjectType` prvek v souboru *vstemplate* a `Web`nastavte textovou hodnotu na .

6. Za `ProjectType` element, `ProjectSubType` přidejte prvek a nastavte textovou hodnotu do programovacího jazyka šablony. Programovací jazyk může být jednou z následujících hodnot:

   - Csharp
   - Visualbasic

     Například:

     ```xml
     <TemplateData>
       ...
       <ProjectType>Web</ProjectType>
       <ProjectSubType>CSharp</ProjectSubType>
       ...
     </TemplateData>
     ```

7. Vyberte soubory v šabloně (to zahrnuje soubor *vstemplate),* klepněte pravým tlačítkem myši na výběr a zvolte **Odeslat do** > **komprimované (zip) složky**. Soubory jsou komprimovány do souboru *ZIP.*

8. Vložte soubor šablony *ZIP* do adresáře šablony projektu sady Visual Studio. Ve výchozím nastavení je tento adresář *%USERPROFILE%\Documents\Visual Studio \<Version\>\ProjectTemplates*.

## <a name="example"></a>Příklad

Následující příklad ukazuje základní soubor *vstemplate* pro šablonu webového projektu:

```xml
<VSTemplate Version="2.0.0" Type="Project"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyWebProjecStarterKit</Name>
        <Description>A simple web template</Description>
        <Icon>icon.ico</Icon>
        <ProjectType>Web</ProjectType>
        <ProjectSubType>CSharp</ProjectSubType>
        <DefaultName>WebSite</DefaultName>
    </TemplateData>
    <TemplateContent>
        <Project File="WebApplication.webproj">
            <ProjectItem>icon.ico</ProjectItem>
            <ProjectItem OpenInEditor="true">Default.aspx</ProjectItem>
            <ProjectItem>Default.aspx.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Viz také

- [Vytvoření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
- [Odkaz na schéma šablony sady Visual Studio (rozšiřitelnost)](../extensibility/visual-studio-template-schema-reference.md)
