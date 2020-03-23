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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591083"
---
# <a name="how-to-create-multi-project-templates"></a>Postup: Vytvoření šablon pro více projektů

Šablony vícenásobných projektů slouží jako kontejnery pro dva nebo více projektů. Když vytvoříte projekt, který je založen na šabloně více projektů, každý projekt v šabloně je přidán do řešení.

Šablona pro více projektů obsahuje dvě nebo více šablon projektu a kořenovou šablonu typu **ProjectGroup**.

Šablony pro více projektů se chovají jinak než šablony jednoho projektu. Mají následující jedinečné vlastnosti:

- Jednotlivé projekty v šabloně více projektů nelze přiřadit názvy, pokud je šablona použita k vytvoření nového projektu. Místo toho použijte atribut **ProjectName** na elementu **ProjectTemplateLink** v souboru *vstemplate* k určení názvu pro každý projekt.

- Šablony více projektů mohou obsahovat projekty pro různé jazyky, ale celá šablona sama o sobě může být zařazena pouze do jedné kategorie. Zadejte kategorii šablony v elementu **ProjectType** souboru *vstemplate.*

Šablona pro více projektů musí obsahovat následující položky komprimované do souboru *ZIP:*

- Kořenový soubor *vstemplate* pro celou šablonu více projektů. Tento *kořenový soubor vstemplate* obsahuje metadata, která se zobrazí v dialogovém okně, kde vytvoříte nový projekt. Také určuje, kde najít *vstemplate* soubory pro projekty v šabloně. Tento soubor musí být umístěn v kořenovém adresáři souboru *ZIP.*

- Dvě nebo více složek, které obsahují soubory, které jsou požadovány pro kompletní šablonu projektu. Složky obsahují všechny soubory kódu pro projekt a také *vstemplate* soubor pro projekt.

Například soubor *zip* šablony více projektů, který má dva projekty, může mít následující soubory a adresáře:

- *Šablona MultiProjectTemplate.vstemplate*
- *\Project1\MyTemplate.vstemplate*
- *\Project1\Project1.vbproj*
- *\Project1\Class.vb*
- *\Project2\MyTemplate.vstemplate*
- *\Project2\Project2.vbproj*
- *\Project2\Class.vb*

Kořenový soubor *vstemplate* pro šablonu více projektů se liší od šablony jednoho projektu následujícími způsoby:

- Atribut **Type** prvku **VSTemplate** má hodnotu **ProjectGroup** namísto **aplikace Project**. Například:

    ```xml
    <VSTemplate Version="2.0.0" Type="ProjectGroup"
        xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    ```

- Prvek **TemplateContent** obsahuje prvek **ProjectCollection,** který obsahuje jeden nebo více prvků **ProjectTemplateLink,** které definují cesty k souborům *vstemplate* zahrnutých projektů. Například:

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
> Pokud chcete, aby se šablona více projektů zobrazovala pouze v novém dialogovém okně projektu, nikoli v jednotlivých projektech, které obsahuje, označte vnitřní šablony jako [skryté](../extensibility/hidden-element-visual-studio-templates.md). Například:
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

## <a name="create-a-multi-project-template-from-an-existing-solution"></a>Vytvoření šablony pro více projektů z existujícího řešení

1. Vytvořte řešení a přidejte dva nebo více projektů.

2. Přizpůsobte projekty, dokud nebudou připraveny k exportu do šablony.

   > [!TIP]
   > Pokud používáte [parametry šablony](template-parameters.md) a chcete odkazovat na proměnné z nadřazené `ext_`šablony, předpona název parametru s . Například, `$ext_safeprojectname$`. Nastavte také atribut **CopyParameters** prvku **ProjectTemplateLink** na **hodnotu true**.
   >
   > ```xml
   > <ProjectTemplateLink ProjectName="MyProject" CopyParameters="true">...</ProjectTemplateLink>
   > ```

3. V nabídce **Project** zvolte **Exportovat šablonu**.

   Otevře se **Průvodce exportem šablony.**

4. Na stránce **Zvolit typ šablony** vyberte **Šablona projektu**. Vyberte jeden z projektů, které chcete exportovat do šablony, a pak zvolte **Další**. (Tyto kroky zopakujete pro každý projekt v řešení.)

5. Na stránce **Vybrat možnosti šablony** zadejte název a volitelný popis, ikonu a náhled obrázku pro šablonu. Zvolte **Dokončit**.

   Projekt je exportován do souboru *ZIP* a umístěn do zadaného výstupního umístění.

   > [!NOTE]
   > Každý projekt musí být exportován do šablony samostatně, proto opakujte předchozí kroky pro každý projekt v řešení.

6. Vytvořte adresář pro šablonu s podadresářem pro každý projekt.

7. Extrahujte obsah souboru *ZIP* každého projektu do odpovídajícího podadresáře, který jste vytvořili.

8. V základním adresáři vytvořte soubor XML s příponou *.vstemplate.* Tento soubor obsahuje metadata pro šablonu více projektů. Podívejte se na příklad, který následuje pro strukturu souboru. Nezapomeňte zadat relativní cestu k souboru *vstemplate* každého projektu.

9. Vyberte všechny soubory v základním adresáři a v nabídce pravým tlačítkem nebo v místní nabídce zvolte **Odeslat** > **komprimovně (zip) složku**.

   Soubory a složky jsou komprimovány do souboru *ZIP.*

10. Zkopírujte soubor *ZIP* do adresáře šablony projektu uživatele. Ve výchozím nastavení je tento adresář *%USERPROFILE%\Documents\Visual Studio \<verze\>\Templates\ProjectTemplates*.

11. V Sadě Visual Studio zvolte **Soubor** > **nový** > **projekt** a ověřte, že se vaše šablona zobrazí.

## <a name="two-project-example"></a>Příklad dvou projektů

Tento příklad ukazuje základní kořenový soubor *vstemplate* pro více projektů. V tomto příkladu má šablona dva projekty, **Moje aplikace systému Windows** a Moje **knihovna tříd**. Atribut **ProjectName** v elementu **ProjectTemplateLink** určuje název, který je projektu přidělen.

> [!TIP]
> Pokud není zadán atribut **ProjectName,** název souboru *vstemplate* se použije jako název projektu.

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

Tento příklad používá **SolutionFolder** element rozdělit projekty do dvou skupin, **Matematické třídy** a **grafické třídy**. Šablona má čtyři projekty, z nichž dva jsou umístěny v každé složce řešení.

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

## <a name="see-also"></a>Viz také

- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
- [Postup: Vytvoření šablon projektů](../ide/how-to-create-project-templates.md)
- [Odkaz na schéma šablony sady Visual Studio (rozšiřitelnost)](../extensibility/visual-studio-template-schema-reference.md)
- [Element SolutionFolder (šablony sady Visual Studio)](../extensibility/solutionfolder-element-visual-studio-templates.md)
- [Element ProjectTemplateLink (šablony sady Visual Studio)](../extensibility/projecttemplatelink-element-visual-studio-templates.md)
