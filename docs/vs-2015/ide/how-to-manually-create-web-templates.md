---
title: 'Postupy: Ruční vytvoření webových šablon | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, Web
- templates [Visual Studio], Web
- Web templates [Visual Studio]
- project templates [Visual Studio], Web
ms.assetid: 731c4027-a152-48c5-bfc4-93490bf1949f
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4bf604e747158c651f284c6463c2c2f65ae3c47a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651805"
---
# <a name="how-to-manually-create-web-templates"></a>Postupy: Ruční vytvoření webových šablon
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vytvoření webové šablony se liší od vytváření jiných druhů šablon. Vzhledem k tomu, že se šablony webových projektů zobrazí v dialogovém okně **Přidat nový web** a položky webového projektu jsou rozděleny podle programovacího jazyka, musí soubor. vstemplate určovat šablonu jako webovou šablonu a identifikovat programovací jazyk.

> [!NOTE]
> Webové šablony musí obsahovat prázdný soubor. webproj, který je určen pomocí `File` atributu `Project` elementu. I když webové projekty nevyžadují soubory projektu, je tento soubor vyžadován, aby webová šablona fungovala správně.

### <a name="to-manually-create-a-web-template"></a>Ruční vytvoření webové šablony

1. Vytvořte webový projekt.

2. Upravte nebo odstraňte soubory v projektu nebo přidejte nové soubory do projektu.

3. Vytvořte soubor XML a uložte ho pomocí přípony názvu souboru. vstemplate ve stejném adresáři jako váš projekt. Nepřidejte ho do projektu v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

4. Vytvořte soubor XML. vstemplate pro poskytnutí metadat šablony projektu. Další informace najdete v příkladu v následující části.

5. Vyhledejte `ProjectType` element v souboru. vstemplate a nastavte textovou hodnotu na `Web` .

6. Za `ProjectType` element přidejte `ProjectSubType` element a nastavte textovou hodnotu na programovací jazyk šablony. Programovací jazyk může být jedna z následujících hodnot:

   - CSharp

   - VisualBasic

     Příklad:

   ```
   <TemplateData>
       ...
       <ProjectType>Web</ProjectType>
       <ProjectSubType>CSharp</ProjectSubType>
       ...
   </TemplateData>
   ```

7. Vyberte soubory v šabloně (to zahrnuje soubor. vstemplate), klikněte pravým tlačítkem myši na výběr, klikněte na **Odeslat do**a pak klikněte na **komprimovanou (ZIP) složku**. Soubory jsou komprimovány do souboru ZIP.

8. Soubor šablony. zip vložte do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] adresáře šablon projektu. Ve výchozím nastavení se jedná o adresář \My Documents\Visual Studio *verze*\My Exported Templates \\ .

## <a name="example"></a>Příklad
 Následující příklad ukazuje základní soubor. vstemplate pro šablonu webového projektu.

```
<VSTemplate Version="2.0.0" Type="Project"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>
    <TemplateData>
        <Name>MyWebProjecStarterKit</Name>
        <Description>A simple Web template</Description>
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
 [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md) – [referenční informace ke schématu šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
