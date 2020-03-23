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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594718"
---
# <a name="how-to-create-item-templates"></a>Postup: Vytvoření šablon položek

Tento článek ukazuje, jak vytvořit šablonu položky pomocí **Průvodce exportem šablony**. Pokud se šablona bude skládat z více souborů, [přečtěte si postup: Vytvoření šablon vícesouborových položek](../ide/how-to-create-multi-file-item-templates.md).

## <a name="add-an-item-template-to-the-add-new-item-dialog-box"></a>Přidání šablony položky do dialogového okna Přidat novou položku

1. Vytvořte nebo otevřete projekt v sadě Visual Studio.

1. Přidejte položku do projektu a upravte ji, pokud chcete.

1. Upravte soubor kódu a označte, kde má dojít k nahrazení parametru. Další informace naleznete v [tématu How to: Substitute parameters in a template](../ide/how-to-substitute-parameters-in-a-template.md).

1. V nabídce **Project** zvolte **Exportovat šablonu**.

1. Na stránce **Zvolit typ šablony** zvolte **Šablona položky**, vyberte projekt, který položku obsahuje, a pak zvolte **Další**.

1. Na stránce **Vybrat položku k exportu** vyberte položku, pro kterou chcete vytvořit šablonu, a pak zvolte **Další**.

1. Na stránce **Vybrat odkazy na položky** vyberte odkazy na sestavení, které chcete zahrnout do šablony, a pak zvolte **Další**.

1. Na stránce **Vybrat volby šablony** zadejte název šablony a volitelný popis, obrázek ikony a náhled obrazu a pak zvolte **Dokončit**.

    Soubory pro šablonu jsou přidány do souboru *ZIP* a zkopírovány do adresáře, který jste zadali v průvodci. Výchozí umístění je *%USERPROFILE%\Documents\Visual Studio \<version\>\My Exported Templates*.

1. Pokud jste nevybrali možnost **Automaticky importovat šablonu do sady Visual Studio** v **Průvodci exportem šablony**, vyhledejte exportovnou šablonu. Potom jej zkopírujte do adresáře šablony položky uživatele. Výchozí umístění je *%USERPROFILE%\Documents\Visual Studio \<version\>\Templates\ItemTemplates*.

1. Zavřete Visual Studio a znovu ji otevřete.

1. Vytvořte nový projekt nebo otevřete existující projekt a pak zvolte Přidat**novou položku** **v projektu** > nebo stiskněte **kombinaci kláves Ctrl**+**Shift**+**A**.

   Šablona položky se zobrazí v dialogovém okně **Přidat novou položku.** Pokud jste v **Průvodci exportem šablony přidali**popis , zobrazí se na pravé straně dialogového okna.

## <a name="enable-the-item-template-to-be-used-in-a-universal-windows-app-project"></a>Povolení použití šablony položky v projektu Universal App pro Windows

Průvodce provede velkou část práce při vytváření základní šablony, ale v mnoha případech je třeba ručně upravit soubor *.vstemplate* po exportu šablony. Pokud například chcete, aby se položka zobrazila v dialogovém okně **Přidat novou položku** pro projekt aplikace Universal pro Windows, musíte provést několik dalších kroků.

1. Podle pokynů v předchozí části exportujte šablonu položky.

1. Extrahujte soubor *ZIP,* který byl vytvořen, a otevřete soubor *.vstemplate* v sadě Visual Studio.

1. Pro projekt C# Universal Windows přidejte `<TemplateData>` do elementu následující XML:

   ```xml
   <TemplateID>Microsoft.CSharp.Class</TemplateID>
   ```

1. V sadě Visual Studio uložte soubor *.vstemplate* a zavřete jej.

1. Zkopírujte a vložte soubor *.vstemplate* zpět do souboru *ZIP.*

     Pokud se zobrazí dialogové okno **Kopírovat soubor,** zvolte volbu **Kopírovat a nahradit.**

Nyní můžete přidat položku založenou na této šabloně do projektu Univerzální windows z dialogového okna **Přidat novou položku.**

## <a name="enable-templates-for-specific-project-subtypes"></a>Povolení šablon pro určité podtypy projektů

Můžete určit, že šablona by se měla zobrazovat pouze pro určité podtypy projektů, jako je Windows, Office, Databáze nebo Web.

1. Vyhledejte `ProjectType` prvek v souboru *.vstemplate* pro šablonu položky.

1. Přidejte element [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) `ProjectType` bezprostředně za element.

1. Nastavte textovou hodnotu prvku na jednu z následujících hodnot:

    - Windows
    - Office
    - Databáze
    - Web

Například: `<ProjectSubType>Database</ProjectSubType>`.

Následující příklad ukazuje šablonu položky pro projekty **Office.**

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

1. Vytvořte položku projektu a projektu.

2. Upravte položku projektu, dokud nebude připravena k uložení jako šablona.

3. Upravte soubor kódu a označte, kde by mělo dojít k nahrazení parametru, pokud kdekoli. Další informace o nahrazení parametrů naleznete v [tématu How to: Substitute parameters in a template.](../ide/how-to-substitute-parameters-in-a-template.md)

4. Vytvořte soubor XML a uložte jej s příponou *.vstemplate* do stejného adresáře jako soubor položek projektu.

5. Upravte soubor *XML .vstemplate* a zadejte metadata šablony položky. Další informace naleznete v [tématu odkaz na schéma šablony (rozšiřitelnost)](../extensibility/visual-studio-template-schema-reference.md) a příklad v předchozí části.

6. Uložte soubor *.vstemplate* a zavřete jej.

7. V **Průzkumníkovi Windows**vyberte soubory, které chcete zahrnout do šablony. Klepněte pravým tlačítkem myši na výběr a zvolte **Odeslat** > **komprimovně (zip) složku**. Vybrané soubory jsou komprimovány do souboru *ZIP.*

::: moniker range="vs-2017"

8. Zkopírujte soubor *ZIP* a vložte jej do umístění šablony položky uživatele. Výchozí adresář je *%USERPROFILE%\Documents\Visual Studio 2017\Templates\ItemTemplates*. Další informace naleznete v [tématu Postup: Vyhledání a uspořádání šablon projektů a položek](../ide/how-to-locate-and-organize-project-and-item-templates.md).

::: moniker-end

::: moniker range=">=vs-2019"

8. Zkopírujte soubor *ZIP* a vložte jej do umístění šablony položky uživatele. Výchozí adresář je *%USERPROFILE%\Documents\Visual Studio 2019\Templates\ItemTemplates*. Další informace naleznete v [tématu Postup: Vyhledání a uspořádání šablon projektů a položek](../ide/how-to-locate-and-organize-project-and-item-templates.md).

::: moniker-end

## <a name="see-also"></a>Viz také

- [Vytvoření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
- [Postup: Vytvoření šablon vícesouborových položek](../ide/how-to-create-multi-file-item-templates.md)
- [Odkaz na schéma šablony sady Visual Studio (rozšiřitelnost)](../extensibility/visual-studio-template-schema-reference.md)
