---
title: Vytváření šablon položek
description: Naučte se používat Průvodce exportem šablony k vytvoření šablony položky v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: how-to
helpviewer_keywords:
- item templates [Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: abf058526a6ff48a37d4c7585e7deabe1decb14a
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/24/2020
ms.locfileid: "95597272"
---
# <a name="how-to-create-item-templates"></a>Postupy: vytváření šablon položek

V tomto článku se dozvíte, jak vytvořit šablonu položky pomocí **Průvodce exportem šablony**. Pokud se vaše šablona skládá z více souborů, přečtěte si téma [Postupy: vytváření šablon položek s více](../ide/how-to-create-multi-file-item-templates.md)soubory.

## <a name="add-an-item-template-to-the-add-new-item-dialog-box"></a>Přidání šablony položky do dialogového okna Přidat novou položku

1. Vytvořte nebo otevřete projekt v aplikaci Visual Studio.

1. Přidejte položku do projektu a upravte ji, pokud chcete.

1. Upravte soubor kódu tak, aby označoval, kde by mělo dojít k nahrazení parametru. Další informace naleznete v tématu [How to: dosadit Parameters in a Template](../ide/how-to-substitute-parameters-in-a-template.md).

1. V nabídce **projekt** vyberte položku **Exportovat šablonu**.

1. Na stránce **zvolit typ šablony** zvolte **položku Šablona položky**, vyberte projekt, který obsahuje položku, a klikněte na tlačítko **Další**.

1. Na stránce **Vybrat položku pro export** zvolte položku, pro kterou chcete vytvořit šablonu, a pak zvolte možnost **Další**.

1. Na stránce **vybrat odkazy na položku** vyberte odkazy na sestavení, které chcete do šablony zahrnout, a poté zvolte možnost **Další**.

1. Na stránce **Vybrat možnosti šablony** zadejte název šablony a volitelný popis, obrázek ikony a obrázek náhledu a pak zvolte **Dokončit**.

    Soubory pro šablonu jsou přidány do souboru *zip* a zkopírovány do adresáře, který jste zadali v průvodci. Výchozí umístění je *%UserProfile%\Documents\Visual Studio \<version\> \My Exported Templates*.

1. Pokud jste nevybrali možnost **automaticky importovat šablonu do sady Visual Studio** v **Průvodci exportem šablony**, vyhledejte exportovanou šablonu. Pak ho zkopírujte do adresáře šablony položky uživatele. Výchozím umístěním je *%UserProfile%\Documents\Visual Studio \<version\> \Templates\ItemTemplates*.

1. Zavřete Visual Studio a potom ho znovu otevřete.

1. Vytvořte nový projekt nebo otevřete existující projekt a pak zvolte **projekt**  >  **Přidat novou položku** nebo stiskněte klávesovou **zkratku CTRL** + **SHIFT** + **a**.

   Šablona položky se zobrazí v dialogovém okně **Přidat novou položku** . Pokud jste přidali popis v **Průvodci exportem šablony**, popis se zobrazí na pravé straně dialogového okna.

## <a name="enable-the-item-template-to-be-used-in-a-universal-windows-app-project"></a>Povolit použití šablony položky v projektu univerzální aplikace pro Windows

Průvodce provede celou práci, která vytvoří základní šablonu, ale v mnoha případech je nutné ručně upravit soubor *. vstemplate* po vyexportování šablony. Například pokud chcete, aby se položka zobrazila v dialogovém okně **Přidat novou položku** pro projekt univerzální aplikace pro Windows, je nutné provést několik dalších kroků.

1. Chcete-li exportovat šablonu položky, postupujte podle kroků v předchozí části.

1. Rozbalte soubor *. zip* , který byl vytvořen, a otevřete soubor *. vstemplate* v aplikaci Visual Studio.

1. V případě univerzálního projektu pro Windows v jazyce C# přidejte do elementu následující kód XML `<TemplateData>` :

   ```xml
   <TemplateID>Microsoft.CSharp.Class</TemplateID>
   ```

1. V aplikaci Visual Studio uložte soubor *. vstemplate* a zavřete ho.

1. Zkopírujte a vložte soubor *. vstemplate* zpátky do souboru *. zip* .

     Pokud se zobrazí dialogové okno **Kopírovat soubor** , vyberte možnost **Kopírovat a nahradit** .

Nyní můžete přidat položku na základě této šablony do univerzálního projektu pro Windows z dialogového okna **Přidat novou položku** .

## <a name="enable-templates-for-specific-project-subtypes"></a>Povolit šablony pro konkrétní podtypy projektu

Můžete určit, že by šablona měla být zobrazena pouze pro některé podtypy projektu, jako je například Windows, Office, databáze nebo Web.

1. Vyhledejte `ProjectType` prvek v souboru *. vstemplate* pro šablonu položky.

1. Přidejte element [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) hned za `ProjectType` element.

1. Nastavte textovou hodnotu prvku na jednu z následujících hodnot:

    - Windows
    - Office
    - databáze
    - Web

Příklad: `<ProjectSubType>Database</ProjectSubType>`.

Následující příklad ukazuje šablonu položky pro projekty **systému Office** .

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

V některých případech je vhodné vytvořit šablonu položky ručně, od nuly.

1. Vytvořte projekt a položku projektu.

2. Upravte položku projektu, dokud není připravena k uložení jako šablony.

3. Upravte soubor s kódem tak, aby označoval, kde by se měla objevit náhrada parametrů, pokud je kdekoli. Další informace o nahrazení parametru naleznete v tématu [How to: dosadit Parameters in a Template.](../ide/how-to-substitute-parameters-in-a-template.md)

4. Vytvořte soubor XML a uložte ho s příponou *. vstemplate* do stejného adresáře jako soubor položky projektu.

5. Úpravou souboru XML *. vstemplate* poskytněte metadata šablony položky. Další informace naleznete v tématu [Referenční dokumentace schématu šablony (rozšiřitelnost)](../extensibility/visual-studio-template-schema-reference.md) a příklad v předchozí části.

6. Uložte soubor *. vstemplate* a zavřete ho.

7. V **Průzkumníku Windows** vyberte soubory, které chcete zahrnout do šablony. Klikněte pravým tlačítkem myši na výběr a vyberte možnost **Odeslat do**  >  **komprimované složky (ZIP)**. Soubory, které jste vybrali, se komprimují do souboru *zip* .

::: moniker range="vs-2017"

8. Zkopírujte soubor *. zip* a vložte ho do umístění šablony položky uživatele. Výchozí adresář je *%UserProfile%\Documents\Visual Studio 2017 \ Templates\ItemTemplates*. Další informace naleznete v tématu [How to: vyhledání a uspořádání šablon projektů a položek](../ide/how-to-locate-and-organize-project-and-item-templates.md).

::: moniker-end

::: moniker range=">=vs-2019"

8. Zkopírujte soubor *. zip* a vložte ho do umístění šablony položky uživatele. Výchozím adresářem je *%UserProfile%\Documents\Visual Studio 2019 \ Templates\ItemTemplates*. Další informace naleznete v tématu [How to: vyhledání a uspořádání šablon projektů a položek](../ide/how-to-locate-and-organize-project-and-item-templates.md).

::: moniker-end

## <a name="see-also"></a>Viz také

- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
- [Postupy: vytváření šablon položek s více soubory](../ide/how-to-create-multi-file-item-templates.md)
- [Referenční dokumentace schématu šablon sady Visual Studio (rozšiřitelnost)](../extensibility/visual-studio-template-schema-reference.md)
