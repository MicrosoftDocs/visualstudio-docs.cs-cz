---
title: Vytváření šablon vícenásobného projektu
ms.date: 04/17/2019
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, creating multi-project
- project templates, multi-project
- multi-project templates
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 6da7464f5e22e186edff7671744c2605bee3c9ad
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591083"
---
# <a name="how-to-create-multi-project-templates"></a>Postupy: vytváření šablon vícenásobného projektu

Šablony vícenásobných projektů slouží jako kontejnery pro dva nebo více projektů. Při vytváření projektu, který je založen na šabloně více projektů, je každý projekt v šabloně přidán do řešení.

Šablona více projektů obsahuje dvě nebo více šablon projektů a kořenovou šablonu typu **Project**.

Víceprojektové šablony chovat jinak než jeden projekt šablony. Mají následující jedinečné charakteristiky:

- Jednotlivé projekty v šabloně více projektů nelze přiřadit názvy, pokud je šablona použita k vytvoření nového projektu. Místo toho použijte **ProjectName** atribut na **ProjectTemplateLink** prvek *vstemplate* souboru zadejte název pro každý projekt.

- Víceprojektové šablony může obsahovat projekty pro různé jazyky, ale samotné celého šablony lze pouze v jedné kategorii. Zadat kategorii šablony v **ProjectType** elementu *vstemplate* souboru.

Víceprojektové šablony musí obsahovat následující položky do komprimované *ZIP* souboru:

- Kořenové *vstemplate* soubor pro celý víceprojektové šabloně. Tento kořenový soubor *vstemplate* obsahuje metadata, která se zobrazí v dialogovém okně, kde vytvoříte nový projekt. Také určuje, kde najít soubory *vstemplate* pro projekty v šabloně. Tento soubor musí být umístěn v kořenovém adresáři *ZIP* souboru.

- Dvě nebo více složek, které obsahují soubory, které jsou požadovány pro dokončení šablony projektu. Složky zahrne všechny soubory kódu pro projekt a také *vstemplate* souboru projektu.

Například víceprojektové šabloně *ZIP* soubor, který má dva projekty může mít následující soubory a adresáře:

- *MultiProjectTemplate.vstemplate*
- *\Project1\MyTemplate.vstemplate*
- *\Project1\Project1.vbproj*
- *\Project1\Class.vb*
- *\Project2\MyTemplate.vstemplate*
- *\Project2\Project2.vbproj*
- *\Project2\Class.vb*

Kořen *vstemplate* soubor pro víceprojektové šabloně se liší od jednoprojektové šablony následujícími způsoby:

- **Typ** atribut **VSTemplate** element má hodnotu **ProjectGroup** místo **projektu**. Příklad:

    ```xml
    <VSTemplate Version="2.0.0" Type="ProjectGroup"
        xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    ```

- **TemplateContent** obsahuje element **projectcollection –** element, který má jeden nebo více **ProjectTemplateLink** prvky, které definují cesty *vstemplate* soubory zahrnuté projektů. Příklad:

    ```xml
    <TemplateContent>
        <ProjectCollection>
            <ProjectTemplateLink>
                Project1\MyTemplate.vstemplate
            </ProjectTemplateLink>
            <ProjectTemplateLink>
                Project2\MyTemplate.vstemplate
            </ProjectTemplateLink>
        </ProjectCollection>
    </TemplateContent>
    ```

> [!TIP]
> Pokud chcete, aby se šablona více projektů zobrazila v dialogovém okně Nový projekt, nikoli v jednotlivých projektech, které obsahuje, označte vnitřní šablony jako [skryté](../extensibility/hidden-element-visual-studio-templates.md). Příklad:
>
> ```xml
> <VSTemplate Type="Project" ... >
>     <TemplateData>
>         ...
>         <Hidden>true</Hidden>
>     </TemplateData>
>     ...
> </VSTemplate>
> ```

## <a name="create-a-multi-project-template-from-an-existing-solution"></a>Vytvoření šablony s více projekty z existujícího řešení

1. Vytvoření řešení a přidejte dva nebo více projektů.

2. Přizpůsobení projektů, dokud nebudou připravené nelze exportovat do šablony.

   > [!TIP]
   > Pokud používáte [parametry šablony](template-parameters.md) a chcete odkazovat na proměnné z nadřazené šablony, prefixujte název parametru s `ext_`. Například `$ext_safeprojectname$`. Také nastavte atribut **CopyParameters** elementu **ProjectTemplateLink** na **hodnotu true**.
   >
   > ```xml
   > <ProjectTemplateLink ProjectName="MyProject" CopyParameters="true">...</ProjectTemplateLink>
   > ```

3. Na **projektu** nabídce zvolte **exportovat šablonu**.

   **Průvodce exportem šablony** otevře.

4. Na **zvolte typ šablony** stránce **šablonu projektu**. Vyberte jeden z projektů, které chcete exportovat do šablony, a poté zvolte možnost **Další**. (Tento postup se opakuje pro každý projekt v řešení.)

5. Na **vyberte možnosti šablony** stránky, zadejte název a volitelný popis, ikona a image ve verzi preview pro šablonu. Zvolte **Dokončit**.

   Projekt se exportuje do *ZIP* souboru a je umístěná v zadané výstupní umístění.

   > [!NOTE]
   > Každý projekt musí být exportován do šablony zvlášť, takže zopakujte předchozí kroky pro každý projekt v řešení.

6. Vytvořte adresář pro šablony, s podadresář pro každý projekt.

7. Extrahujte obsah každého projektu *ZIP* soubor do odpovídající podadresář, který jste vytvořili.

8. V základním adresáři vytvořte soubor XML s *.vstemplate* příponu souboru. Tento soubor obsahuje metadata pro víceprojektové šabloně. Viz příklad, který následuje pro strukturu souboru. Nezapomeňte zadat relativní cestu pro každý projekt *vstemplate* souboru.

9. Vyberte všechny soubory v adresáři základní a z nabídky, klikněte pravým tlačítkem nebo kontext, zvolte **odeslat** > **komprimovanou složku (ZIP)** .

   Do jsou komprimované soubory a složky *ZIP* souboru.

10. Kopírovat *ZIP* soubor do adresáře projektu šablony uživatele. Ve výchozím nastavení, je tento adresář *%USERPROFILE%\Documents\Visual Studio \<verze\>\Templates\ProjectTemplates*.

11. V aplikaci Visual Studio vyberte **soubor** > **Nový** > **projekt** a ověřte, zda se zobrazí vaše šablona.

## <a name="two-project-example"></a>Příklad dvou projektu

Tento příklad ukazuje základní kořenové víceprojektové *vstemplate* souboru. V tomto příkladu obsahuje šablona dva projekty **My Windows Application** a **My Class Library**. **ProjectName** atribut na **ProjectTemplateLink** prvek určuje název, který je přiřazen do projektu.

> [!TIP]
> Pokud **ProjectName** atribut není zadán, název *vstemplate* soubor se používá jako název projektu.

```xml
<VSTemplate Version="2.0.0" Type="ProjectGroup"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>Multi-Project Template Sample</Name>
        <Description>An example of a multi-project template</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>VisualBasic</ProjectType>
    </TemplateData>
    <TemplateContent>
        <ProjectCollection>
            <ProjectTemplateLink ProjectName="My Windows Application">
                WindowsApp\MyTemplate.vstemplate
            </ProjectTemplateLink>
            <ProjectTemplateLink ProjectName="My Class Library">
                ClassLib\MyTemplate.vstemplate
            </ProjectTemplateLink>
        </ProjectCollection>
    </TemplateContent>
</VSTemplate>
```

## <a name="example-with-solution-folders"></a>Příklad se složkami řešení

V tomto příkladu **SolutionFolder** elementu a rozdělit do dvou skupin, projekty **matematické třídy** a **grafických tříd**. Šablona má čtyři projekty, z nichž dva jsou umístěny ve složce jednotlivých řešení.

```xml
<VSTemplate Version="2.0.0" Type="ProjectGroup"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>Multi-Project Template Sample</Name>
        <Description>An example of a multi-project template</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>VisualBasic</ProjectType>
    </TemplateData>
    <TemplateContent>
        <ProjectCollection>
            <SolutionFolder Name="Math Classes">
                <ProjectTemplateLink ProjectName="MathClassLib1">
                    MathClassLib1\MyTemplate.vstemplate
                </ProjectTemplateLink>
                <ProjectTemplateLink ProjectName="MathClassLib2">
                    MathClassLib2\MyTemplate.vstemplate
                </ProjectTemplateLink>
            </SolutionFolder>
            <SolutionFolder Name="Graphics Classes">
                <ProjectTemplateLink ProjectName="GraphicsClassLib1">
                    GraphicsClassLib1\MyTemplate.vstemplate
                </ProjectTemplateLink>
                <ProjectTemplateLink ProjectName="GraphicsClassLib2">
                    GraphicsClassLib2\MyTemplate.vstemplate
                </ProjectTemplateLink>
            </SolutionFolder>
        </ProjectCollection>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Viz také:

- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
- [Postupy: vytváření šablon projektu](../ide/how-to-create-project-templates.md)
- [Visual Studio odkaz na schéma šablon (rozšiřitelnost)](../extensibility/visual-studio-template-schema-reference.md)
- [SolutionFolder – element (šablony sady Visual Studio)](../extensibility/solutionfolder-element-visual-studio-templates.md)
- [ProjectTemplateLink – element (šablony sady Visual Studio)](../extensibility/projecttemplatelink-element-visual-studio-templates.md)
