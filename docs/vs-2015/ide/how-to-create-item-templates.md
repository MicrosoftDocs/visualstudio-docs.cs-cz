---
title: 'Postupy: vytváření šablon položek | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- project item templates, XML reference
- project item templates, custom template locations
- project item templates, creating
- project item templates, metadata files
ms.assetid: 77bc53d4-d607-4820-a032-7e3b365891b5
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c9edc79002a4a2d7c2fe135d7eb4669f5f010599
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668080"
---
# <a name="how-to-create-item-templates"></a>Postupy: Vytváření šablon položek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Postup v [prvním postupu](#to-add-a-custom-project-item-template-to-the-add-new-item-dialog-box) tohoto tématu ukazuje, jak vytvořit šablonu položky pomocí průvodce **exportem šablony** . Pokud se vaše šablona skládá z více souborů, přečtěte si téma [Postupy: vytváření šablon položek s více](../ide/how-to-create-multi-file-item-templates.md)soubory.

 Průvodce provede spoustu práce při vytváření základní šablony, ale v mnoha případech budete muset ručně upravit soubor. vstemplate po exportu šablony. Například pokud chcete, aby se položka zobrazila v dialogovém okně **Přidat novou položku** pro projekt aplikace [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)], bude nutné provést několik dalších kroků. [Druhý postup](#to-enable-the-item-template-to-be-used-in-a-store-project) v tomto tématu vám pomůže tento úkol provést.

 V některých případech možná budete chtít vytvořit šablonu položky ručně od začátku. [Třetí postup](#to-enable-templates-for-specific-project-sub-types) ukazuje, jak to provést.

 Informace o prvcích, které lze použít v souboru. vstemplate, naleznete v referenčních informacích k [schématu šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md) .

### <a name="to-add-a-custom-project-item-template-to-the-add-new-item-dialog-box"></a>Přidání vlastní šablony položky projektu do dialogového okna Přidat novou položku

1. Vytvořte nebo otevřete projekt v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

2. Přidejte položku do projektu a upravte ji, pokud chcete.

3. Upravte soubor kódu tak, aby označoval, kde by mělo dojít k nahrazení parametru. Další informace naleznete v tématu [How to: dosadit Parameters in a Template](../ide/how-to-substitute-parameters-in-a-template.md).

4. V nabídce **soubor** klikněte na položku **Exportovat šablonu**.

5. Klikněte na **položku Šablona položky**, vyberte projekt, který obsahuje položku, a klikněte na tlačítko **Další**.

6. Vyberte položku, pro kterou chcete vytvořit šablonu, a klikněte na tlačítko **Další**.

7. Vyberte odkazy na sestavení, které chcete zahrnout do šablony, a klikněte na **Další**.

8. Zadejte název souboru ikony, obrázek náhledu, název šablony a popis šablony a klikněte na **Dokončit**.

     Soubory pro šablonu se přidají do souboru. zip a zkopírují se do libovolného adresáře, který zadáte v dialogovém okně. Výchozí umístění je **.. \Users \\ < username \> \Documents\Visual Studio \<Version > \My Exported Templates \\** Folder.

    > [!WARNING]
    > V dřívějších verzích sady Visual Studio je výchozí umístění **.. \Users \\ < username \> \Documents\Visual Studio \<Version > \Templates\ItemTemplates**.

### <a name="to-enable-the-item-template-to-be-used-in-a-store-project"></a>Povolení použití šablony položky v projektu úložiště

1. Chcete-li exportovat šablonu položky, postupujte podle kroků v postupu výše.

2. Extrahujte soubor. vstemplate ze souboru. zip, který byl zkopírován do.. \Users \\*username*\Documents\Visual Studio *verze*\Templates\itemtemplates\. (nebo složky **Moje exportované šablony**).

3. Otevřete soubor. vstemplate v aplikaci Visual Studio.

4. V případě projektu Windows 8.1 C# Store v souboru. vstemplate přidejte následující kód XML v rámci otevírací a ukončovací značky `<TemplateData>`: `<TemplateGroupID>WinRT-Managed</TemplateGroupID>`.

    Projekt C++ Windows 8.1 Store používá hodnotu `WinRT-Native-6.3`. Pro Windows 10 a další typy projektů naleznete v tématu [TemplateGroupID – element (šablony sady Visual Studio)](../extensibility/templategroupid-element-visual-studio-templates.md).

    Následující příklad ukazuje celý obsah souboru. vstemplate po přidání řádku XML `<TemplateGroupID>WinRT-Managed</TemplateGroupID>`. Tento příklad je specifický pro C# projekty. Můžete upravit \<ProjectType > a \< prvky > [TemplateGroupID –](../extensibility/templategroupid-element-visual-studio-templates.md)a určit tak další typy jazyka a projektu.

   ```xml
   <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">
     <TemplateData>
       <DefaultName>MyItemStoreTemplate.xaml</DefaultName>
       <Name>MyItemStoreTemplate</Name>
       <Description>This is an example itemtemplate</Description>
       <ProjectType>CSharp</ProjectType>
       <SortOrder>10</SortOrder>
       <Icon>__TemplateIcon.ico</Icon>
       <TemplateGroupID>WinRT-Managed</TemplateGroupID>
     </TemplateData>
     <TemplateContent>
       <References />
       <ProjectItem SubType="Designer" TargetFileName="$fileinputname$.xaml" ReplaceParameters="true">MyItemTemplate.xaml</ProjectItem>
       <ProjectItem SubType="Code" TargetFileName="$fileinputname$.xaml.cs" ReplaceParameters="true">MyItemTemplate.xaml.cs</ProjectItem>
     </TemplateContent>
   </VSTemplate>
   ```

    Další možné hodnoty TemplateGroupID – naleznete v tématu [TemplateGroupID – element (šablony sady Visual Studio)](../extensibility/templategroupid-element-visual-studio-templates.md)). Úplný odkaz na dokončeno. vstemplate najdete v tématu [referenční informace schématu šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md) .

5. V aplikaci Visual Studio uložte soubor. vstemplate a zavřete ho.

6. Zkopírujte a vložte soubor. vstemplate zpátky do souboru. zip, který je umístěn v.. \Users \\*username*\Documents\Visual Studio *verze*\templates\itemtemplates\..

    Pokud se zobrazí dialogové okno **Kopírovat soubor** , vyberte možnost **Kopírovat a nahradit** .

   Nyní můžete přidat položku na základě této šablony do [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] projektu pomocí dialogového okna **Přidat novou položku** .

   Další informace o názvech parametrů naleznete v tématu [template Parameters](../ide/template-parameters.md).

### <a name="to-enable-templates-for-specific-project-sub-types"></a>Chcete-li povolit šablony pro konkrétní dílčí typy projektu

1. Vývojové prostředí vám umožní zpřístupnit položky projektu z dialogového okna Přidat položku pro určité projekty. Tento postup slouží k zpřístupnění vlastních položek pro projekty Windows, web, Office nebo databáze.

    Vyhledejte element ProjectType v souboru. vstemplate pro šablonu položky.

    Přidejte element [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) hned za prvek ProjectType.

2. Nastavte textovou hodnotu prvku na jednu z následujících hodnot:

   1. Windows

   2. Office

   3. Databáze

   4. Web

      Například: `<ProjectSubType>Database</ProjectSubType>`.

      Následující příklad ukazuje šablonu položky, která je k dispozici pro projekty systému Office.

   ```
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

### <a name="to-manually-create-an-item-template-without-using-the-export-template-wizard"></a>Ruční vytvoření šablony položky bez použití Průvodce exportem šablony

1. Vytvořte projekt a položku projektu.

2. Upravte položku projektu, dokud není připravena k uložení jako šablony.

3. V případě potřeby upravte soubor kódu tak, aby označoval, kde by měla být nahrazena parametr. Další informace o nahrazení parametru naleznete v tématu How to: dosadit Parameters in a Template.

4. Vytvořte soubor XML a uložte ho pomocí přípony názvu souboru. vstemplate ve stejném adresáři jako vaše šablona nové položky.

5. Vytvořte soubor XML. vstemplate k poskytnutí metadat šablony položky. Další informace naleznete v tématu [Referenční dokumentace schématu šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md) a příklad v předchozí části.

6. Uložte soubor. vstemplate a zavřete ho.

7. V Průzkumníku Windows vyberte soubory, které chcete zahrnout do šablony, klikněte pravým tlačítkem myši na výběr, klikněte na Odeslat do a pak klikněte na Komprimovaná složka (ZIP). Soubory, které jste vybrali, se komprimují do souboru ZIP.

8. Zkopírujte soubor. zip a vložte ho do umístění šablony položky uživatele. V aplikaci Visual Studio 2015 je výchozí adresář.. \Users \\ < username \> \Documents\Visual Studio 2015 \ Templates\ItemTemplates \\. Další informace naleznete v tématu How to: vyhledání a uspořádání šablon projektů a položek.

## <a name="see-also"></a>Viz také
 [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md) [Postupy: vytváření šablon položek s více soubory odkaz na](../ide/how-to-create-multi-file-item-templates.md) [schéma šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
