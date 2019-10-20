---
title: Vytváření webových šablon
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, Web
- templates [Visual Studio], Web
- Web templates [Visual Studio]
- project templates [Visual Studio], Web
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7d121d9b970d8012aaf177c0a232cd21f6fe85d9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645819"
---
# <a name="how-to-manually-create-web-templates"></a>Postupy: Ruční vytvoření webových šablon

Vytvoření webové šablony se liší od vytváření jiných druhů šablon. Vzhledem k tomu, že se šablony webových projektů zobrazí v dialogovém okně **Přidat nový web** a položky webového projektu jsou rozděleny podle programovacího jazyka, musí soubor *vstemplate* určit šablonu jako webovou šablonu a identifikovat programovací jazyk.

> [!NOTE]
> Webové šablony musí obsahovat prázdný soubor *. webproj* a musí být odkazován v souboru *vstemplate* v atributu `File` `Project` elementu. I když webové projekty nevyžadují soubor projektu *. proj* , je nutné vytvořit tento zástupný soubor pro správné fungování webové šablony.

## <a name="to-manually-create-a-web-template"></a>Ruční vytvoření webové šablony

1. Vytvořte webový projekt.

2. Upravte nebo odstraňte soubory v projektu nebo přidejte nové soubory do projektu.

3. Vytvořte soubor XML a uložte ho s příponou názvu souboru *vstemplate* ve stejném adresáři jako váš projekt. Nepřidejte ho do projektu v aplikaci Visual Studio.

4. Úpravou souboru *vstemplate* XML poskytněte metadata šablony projektu. Další informace najdete v následujícím [příkladu](#example).

5. Vyhledejte prvek `ProjectType` v souboru *vstemplate* a nastavte textovou hodnotu na `Web`.

6. Po elementu `ProjectType` přidejte prvek `ProjectSubType` a nastavte textovou hodnotu na programovací jazyk šablony. Programovací jazyk může být jedna z následujících hodnot:

   - CSharp
   - VisualBasic

     Příklad:

     ```xml
     <TemplateData>
       ...
       <ProjectType>Web</ProjectType>
       <ProjectSubType>CSharp</ProjectSubType>
       ...
     </TemplateData>
     ```

7. Vyberte soubory v šabloně (to zahrnuje *vstemplate* soubor), klikněte pravým tlačítkem na výběr a zvolte **Odeslat do**  > **Komprimovaná složka (ZIP)** . Soubory jsou komprimovány do souboru *zip* .

8. Soubor šablony *. zip* vložte do adresáře šablon projektu sady Visual Studio. Ve výchozím nastavení je tento adresář *%UserProfile%\Documents\Visual Studio \<Version \> \projecttemplates*.

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

## <a name="see-also"></a>Viz také:

- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
- [Referenční dokumentace schématu šablon sady Visual Studio (rozšiřitelnost)](../extensibility/visual-studio-template-schema-reference.md)
