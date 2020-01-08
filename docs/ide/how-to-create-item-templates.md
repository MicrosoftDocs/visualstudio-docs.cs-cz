---
title: Vytváření šablon položek
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- item templates [Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 62004c5c96fa708f98ab49f4810ec2fc1c38eadc
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594718"
---
# <a name="how-to-create-item-templates"></a>Postupy: Tvorba šablon položek

V tomto článku se dozvíte, jak vytvořit šablonu položky pomocí **Průvodce exportem šablony**. Pokud šablony se skládají z více souborů, přečtěte si téma [postupy: vytváření šablon položek s více soubory](../ide/how-to-create-multi-file-item-templates.md).

## <a name="add-an-item-template-to-the-add-new-item-dialog-box"></a>Přidání šablony položky do dialogového okna Přidat novou položku

1. Vytvořte nebo otevřete projekt v sadě Visual Studio.

1. Přidání položky do projektu a změňte ji, pokud chcete.

1. Upravte soubor kódu k označení, kde by měla probíhat náhrada parametru. Další informace najdete v tématu [postupy: nahrazení parametrů v šabloně](../ide/how-to-substitute-parameters-in-a-template.md).

1. Na **projektu** nabídce zvolte **exportovat šablonu**.

1. Na **zvolte typ šablony** zvolte **šablony položky**, vyberte projekt, který obsahuje položku a klikněte na tlačítko **Další**.

1. Na **vyberte položky, které chcete exportovat** zvolte položku, kterou chcete vytvořit šablonu pro a pak zvolte **Další**.

1. Na **vybrat odkazy položky** vyberte odkazy na sestavení do šablony zahrnout, a klikněte na tlačítko **Další**.

1. Na **vyberte možnosti šablony** stránky, zadejte název šablony a volitelně také popis, obrázek ikony a obrázek náhledu a pak zvolte **Dokončit**.

    Soubory pro šablonu jsou přidány do *ZIP* souboru a zkopírován do adresáře, který jste zadali v průvodci. Výchozí umístění je *%USERPROFILE%\Documents\Visual Studio \<verze\>\My exportované šablony*.

1. Pokud jste nevybrali možnost **automaticky importovat šablonu do sady Visual Studio** v **Průvodce exportem šablony**, vyhledejte vyexportované šablony. Potom ho zkopírujte na adresář šablon položek uživatele. Výchozí umístění je *%USERPROFILE%\Documents\Visual Studio \<verze\>\Templates\ItemTemplates*.

1. Zavřete sadu Visual Studio a znovu ho otevřít.

1. Vytvořte nový projekt, nebo otevřete existující projekt a pak zvolte **projektu** > **přidat novou položku** nebo stiskněte klávesu **Ctrl** +  **SHIFT**+**A**.

   Šablona položky se zobrazí v **přidat novou položku** dialogové okno. Pokud jste přidali popisu **Průvodce exportem šablony**, popis se zobrazí na pravé straně dialogového okna.

## <a name="enable-the-item-template-to-be-used-in-a-universal-windows-app-project"></a>Povolit použití šablony položky v projektu univerzální aplikace pro Windows

Průvodce provádí velkou část práce, kterou vytvoření základní šablony, ale v mnoha případech budete muset ručně upravit *.vstemplate* souboru po exportu šablony. Například, pokud chcete, aby se zobrazí v položce **přidat novou položku** dialogové okno pro projekt univerzální aplikace pro Windows, je nutné provést několik kroků navíc.

1. Postupujte podle kroků v předchozí části pro export šablony položky.

1. Extrahovat *ZIP* soubor, který byl vytvořený a otevřít *.vstemplate* souboru v sadě Visual Studio.

1. Pro C# Universal Windows project, přidejte následující kód XML uvnitř `<TemplateData>` element:

   ```xml
   <TemplateID>Microsoft.CSharp.Class</TemplateID>
   ```

1. V sadě Visual Studio, uložte *.vstemplate* soubor a zavřete ho.

1. Zkopírujte a vložte *.vstemplate* zpět do souboru *ZIP* souboru.

     Pokud **kopírovat soubor** dialogové okno se zobrazí, zvolte **kopírovat a nahradit** možnost.

Teď můžete přidat položku založenou na šabloně pro Universal Windows project z **přidat novou položku** dialogové okno.

## <a name="enable-templates-for-specific-project-subtypes"></a>Povolit šablony pro konkrétní podtypy projektu

Můžete určit, že šablony objevit pouze pro pouze některé podtypů projektů, jako je například Windows, Office, databáze i na webu.

1. Vyhledejte `ProjectType` prvek *.vstemplate* soubor šablony položky.

1. Přidat [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) element ihned po `ProjectType` elementu.

1. Textová hodnota elementu nastavena na jednu z následujících hodnot:

    - Windows
    - Office
    - Databáze nástroje
    - Web

Například: `<ProjectSubType>Database</ProjectSubType>`.

Následující příklad ukazuje šablonu položky pro **Office** projekty.

```xml
<VSTemplate Version="2.0.0" Type="Item" Version="2.0.0">
   <TemplateData>
      <Name>Class</Name>
      <Description>An empty class file</Description>
      <Icon>Class.ico</Icon>
      <ProjectType>CSharp</ProjectType>
      <ProjectSubType>Office</ProjectSubType>
      <DefaultName>Class.cs</DefaultName>
   </TemplateData>
   <TemplateContent>
      <ProjectItem>Class1.cs</ProjectItem>
   </TemplateContent>
</VSTemplate>
```

## <a name="manually-create-an-item-template"></a>Ruční vytvoření šablony položky

V některých případech můžete chtít vytvořit šablonu položky ručně, od začátku.

1. Vytváření projektů a položek projektů.

2. Upravte položku projektu, dokud nebude připravený uložit jako šablonu.

3. Upravte soubor kódu k označení, kde nahrazení parametru by měl nastat, pokud kdekoli. Další informace o nahrazení parametru najdete v tématu [postupy: nahrazení parametrů v šabloně.](../ide/how-to-substitute-parameters-in-a-template.md)

4. Vytvořte soubor XML a uložit ji *.vstemplate* příponu souboru ve stejném adresáři jako soubor položky projektu.

5. Upravit *.vstemplate* soubor XML k poskytnutí metadat šablony položky. Další informace najdete v tématu [odkaz na schéma šablony (rozšiřitelnost)](../extensibility/visual-studio-template-schema-reference.md) a v příkladu v předchozí části.

6. Uložit *.vstemplate* soubor a zavřete ho.

7. V **Windows Explorer**, vyberte soubory, které chcete zahrnout do šablony. Klikněte pravým tlačítkem na výběr a zvolte **odeslat** > **komprimovanou složku (ZIP)** . Do jsou komprimované soubory, které jste vybrali *ZIP* souboru.

::: moniker range="vs-2017"

8. Kopírovat *ZIP* soubor a vložte ho do umístění šablon položek uživatele. Výchozí adresář je *%UserProfile%\Documents\Visual Studio 2017 \ Templates\ItemTemplates*. Další informace najdete v tématu [postupy: hledání a organizace šablon projektů a položek](../ide/how-to-locate-and-organize-project-and-item-templates.md).

::: moniker-end

::: moniker range=">=vs-2019"

8. Kopírovat *ZIP* soubor a vložte ho do umístění šablon položek uživatele. Výchozím adresářem je *%UserProfile%\Documents\Visual Studio 2019 \ Templates\ItemTemplates*. Další informace najdete v tématu [postupy: hledání a organizace šablon projektů a položek](../ide/how-to-locate-and-organize-project-and-item-templates.md).

::: moniker-end

## <a name="see-also"></a>Viz také:

- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
- [Postupy: vytváření šablon položek s více soubory](../ide/how-to-create-multi-file-item-templates.md)
- [Visual Studio odkaz na schéma šablon (rozšiřitelnost)](../extensibility/visual-studio-template-schema-reference.md)
