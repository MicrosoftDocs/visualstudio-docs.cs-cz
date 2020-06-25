---
title: Vytváření šablon vícenásobného projektu
ms.date: 04/17/2019
ms.topic: how-to
helpviewer_keywords:
- Visual Studio templates, creating multi-project
- project templates, multi-project
- multi-project templates
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: b71af98c7d72e0b3a510f3968f3d0770cd5401df
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85284409"
---
# <a name="how-to-create-multi-project-templates"></a>Postupy: vytváření šablon více projektů

Šablony vícenásobných projektů slouží jako kontejnery pro dva nebo více projektů. Při vytváření projektu, který je založen na šabloně více projektů, je každý projekt v šabloně přidán do řešení.

Šablona více projektů obsahuje dvě nebo více šablon projektů a kořenovou šablonu typu **Project**.

Šablony více projektů se chovají jinak než jednotlivé šablony projektů. Mají tyto jedinečné charakteristiky:

- Jednotlivé projekty v šabloně více projektů nelze přiřadit názvy, pokud je šablona použita k vytvoření nového projektu. Místo toho použijte atribut **ProjectName** v elementu **ProjectTemplateLink** v souboru *vstemplate* k zadání názvu pro každý projekt.

- Šablony více projektů mohou obsahovat projekty pro různé jazyky, ale celou samotnou šablonu lze umístit pouze do jedné kategorie. V elementu **ProjectType** souboru *vstemplate* zadejte kategorii šablony.

Šablona více projektů musí zahrnovat následující položky, které jsou komprimovány do souboru *. zip* :

- Kořenový soubor *vstemplate* pro celou šablonu více projektů. Tento kořenový soubor *vstemplate* obsahuje metadata, která se zobrazí v dialogovém okně, kde vytvoříte nový projekt. Také určuje, kde najít soubory *vstemplate* pro projekty v šabloně. Tento soubor se musí nacházet v kořenovém adresáři souboru *. zip* .

- Dvě nebo více složek, které obsahují soubory, které jsou požadovány pro úplnou šablonu projektu. Složky obsahují všechny soubory kódu projektu a také soubor *vstemplate* pro projekt.

Například soubor *. zip* šablony pro více projektů, který má dva projekty, může obsahovat následující soubory a adresáře:

- *MultiProjectTemplate. vstemplate*
- *\Project1\MyTemplate.vstemplate*
- *\Project1\Project1.vbproj*
- *\Project1\Class.vb*
- *\Project2\MyTemplate.vstemplate*
- *\Project2\Project2.vbproj*
- *\Project2\Class.vb*

Kořenový soubor *vstemplate* pro šablonu s více projekty se liší od šablony jednoho projektu následujícími způsoby:

- Atribut **Type** elementu **vstemplate** má hodnotu typu **projekt** namísto **projektu**. Příklad:

    ```xml
    <VSTemplate Version="2.0.0" Type="ProjectGroup"
        xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    ```

- Element **TemplateContent** obsahuje prvek **ProjectCollection** , který obsahuje jeden nebo více **ProjectTemplateLink** prvků, které definují cesty k souborům *vstemplate* zahrnutých projektů. Příklad:

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

1. Vytvořte řešení a přidejte dva nebo více projektů.

2. Přizpůsobte projekty, dokud nebudou připravené k exportu do šablony.

   > [!TIP]
   > Pokud používáte [parametry šablony](template-parameters.md) a chcete odkazovat na proměnné z nadřazené šablony, předponu název parametru použijte `ext_` . Například, `$ext_safeprojectname$`. Také nastavte atribut **CopyParameters** elementu **ProjectTemplateLink** na **hodnotu true**.
   >
   > ```xml
   > <ProjectTemplateLink ProjectName="MyProject" CopyParameters="true">...</ProjectTemplateLink>
   > ```

3. V nabídce **projekt** vyberte položku **Exportovat šablonu**.

   Otevře se **Průvodce exportem šablony** .

4. Na stránce **zvolit typ šablony** vyberte možnost **Šablona projektu**. Vyberte jeden z projektů, které chcete exportovat do šablony, a poté zvolte možnost **Další**. (Tento postup se opakuje pro každý projekt v řešení.)

5. Na stránce **Vybrat možnosti šablony** zadejte název a volitelný popis, ikonu a náhled obrázku pro šablonu. Klikněte na tlačítko **Dokončit**.

   Projekt je exportován do souboru *. zip* a umístěn do zadaného umístění výstupu.

   > [!NOTE]
   > Každý projekt musí být exportován do šablony samostatně, proto opakujte předchozí kroky pro každý projekt v řešení.

6. Vytvořte adresář pro šablonu s podadresářem pro každý projekt.

7. Extrahujte obsah každého souboru *. zip* projektu do odpovídajícího podadresáře, který jste vytvořili.

8. V základním adresáři vytvořte soubor XML s příponou *. vstemplate* souboru. Tento soubor obsahuje metadata pro šablonu více projektů. Podívejte se na příklad, který následuje pro strukturu souboru. Nezapomeňte zadat relativní cestu k souboru *vstemplate* každého projektu.

9. Vyberte všechny soubory v základním adresáři a v místní nabídce klikněte pravým tlačítkem nebo na příkaz **Odeslat do**  >  **komprimované složky (ZIP)**.

   Soubory a složky jsou komprimovány do souboru *zip* .

10. Zkopírujte soubor *. zip* do adresáře uživatelských šablon projektu. Ve výchozím nastavení je tento adresář *%UserProfile%\Documents\Visual Studio \<version\> \Templates\ProjectTemplates*.

11. V aplikaci Visual Studio vyberte **soubor**  >  **Nový**  >  **projekt** a ověřte, zda se zobrazí vaše šablona.

## <a name="two-project-example"></a>Příklad pro dva projekty

Tento příklad ukazuje základní soubor. *vstemplate* kořen více projektů. V tomto příkladu má šablona dva projekty, **Moje aplikace Windows** a **Moje knihovna tříd**. Atribut **ProjectName** v elementu **ProjectTemplateLink** Určuje název, který je daný projektu.

> [!TIP]
> Pokud atribut **ProjectName** není zadán, bude název souboru *vstemplate* použit jako název projektu.

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

V tomto příkladu se používá element **SolutionFolder –** k rozdělení projektů do dvou skupin, tříd **Math** a **grafických tříd**. Šablona má čtyři projekty, z nichž dva jsou umístěny do každé složky řešení.

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
- [Postupy: vytváření šablon projektů](../ide/how-to-create-project-templates.md)
- [Referenční dokumentace schématu šablon sady Visual Studio (rozšiřitelnost)](../extensibility/visual-studio-template-schema-reference.md)
- [SolutionFolder – – element (šablony sady Visual Studio)](../extensibility/solutionfolder-element-visual-studio-templates.md)
- [ProjectTemplateLink – element (šablony sady Visual Studio)](../extensibility/projecttemplatelink-element-visual-studio-templates.md)
