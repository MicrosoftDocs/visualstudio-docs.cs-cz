---
title: 'Postupy: vytváření šablon položek | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project item templates, XML reference
- project item templates, custom template locations
- project item templates, creating
- project item templates, metadata files
ms.assetid: 77bc53d4-d607-4820-a032-7e3b365891b5
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8559fb8b32b83d352bd9ec82cf426903aff13a19
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49863625"
---
# <a name="how-to-create-item-templates"></a>Postupy: Vytváření šablon položek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kroky v [prvního postupu](../ide/how-to-create-item-templates.md#export_template) tohoto tématu ukazují, jak vytvořit šablonu položky pomocí **exportovat šablonu** průvodce. Pokud šablony se skládají z více souborů, přečtěte si téma [postupy: vytváření šablon položek vícesouborové](../ide/how-to-create-multi-file-item-templates.md).  
  
 Průvodce provede spoustu práce pro vytvoření základní šablony, ale v mnoha případech budete muset ručně upravit soubor .vstemplate poté, co jste exportovali šablonu. Například, pokud chcete, aby se zobrazí v položce **přidat novou položku** dialogové okno pro [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] projekt aplikace, budete muset provést několik kroků navíc. [Druhý postup](../ide/how-to-create-item-templates.md#modify_template) v tomto tématu pomáhá tento úkol provést.  
 
 V některých případech může chcete nebo muset ručně vytvořit šablonu položky od začátku. [Třetí postup](../ide/how-to-create-item-templates.md#create_template) ukazuje, jak to provést.  
  
 Zobrazit [Visual Studio odkaz na schéma šablon](../extensibility/visual-studio-template-schema-reference.md) informace o prvcích, které lze použít v souboru .vstemplate.  
  
### <a name="to-add-a-custom-project-item-template-to-the-add-new-item-dialog-box"></a>Chcete-li přidat vlastní šablonu položky projektu do dialogového okna Přidat novou položku  
  
1.  Vytvořte nebo otevřete projekt v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
2.  Přidání položky do projektu a změňte ji, pokud chcete.  
  
3.  Upravte soubor kódu k označení, kde by měla probíhat náhrada parametru. Další informace najdete v tématu [jak: náhradní parametry v šabloně](../ide/how-to-substitute-parameters-in-a-template.md).  
  
4.  Na **souboru** nabídky, klikněte na tlačítko **exportovat šablonu**.  
  
5.  Klikněte na tlačítko **šablony položky**, vyberte projekt, který obsahuje položku a klikněte na tlačítko **Další**.  
  
6.  Vyberte položku, pro kterou chcete vytvořit šablonu a klikněte na tlačítko **Další**.  
  
7.  Vyberte odkazy na sestavení do šablony zahrnout, a klikněte na **Další**.  
  
8.  Zadejte název souboru ikony, náhled obrázku, název šablony a popis šablony a klikněte na tlačítko **Dokončit**.  
  
     Soubory pro šablonu jsou přidány do souboru ZIP a zkopírovány jakékoli adresáře, zadejte v dialogovém okně. Výchozí umístění je **... \Users\\< uživatelské jméno\>\Documents\Visual Studio \<verze > \My exportované šablony\\**  složky.  
  
    > [!WARNING]
    >  V dřívějších verzích sady Visual Studio, je výchozí umístění **... \Users\\< uživatelské jméno\>\Documents\Visual Studio \<verze > \Templates\ItemTemplates**.  
  
### <a name="to-enable-the-item-template-to-be-used-in-a-store-project"></a>K povolení šablony položky, který se má použít v projektu úložiště  
  
1. Postupujte podle kroků v postupu výše pro export šablony položky.  
  
2. Extrahujte soubor .vstemplate ze souboru .zip, který byl zkopírován do... \Users\\*uživatelské jméno*\Documents\Visual Studio *verze*\Templates\ItemTemplates\ (nebo **exportované šablony**) složky.  
  
3. Otevřete soubor .vstemplate v sadě Visual Studio.  
  
4. Pro Windows 8.1 ukládání projektu C#, v souboru .vstemplate přidejte následující kód XML v rámci otevírací a zavírací `<TemplateData>` značky: `<TemplateGroupID>WinRT-Managed</TemplateGroupID>`.  
  
    Úložiště projektu C++ Windows 8.1 používá hodnotu `WinRT-Native-6.3`. Windows 10 a jinými typy projektů naleznete v tématu [templategroupid – Element (šablony sady Visual Studio)](../extensibility/templategroupid-element-visual-studio-templates.md).  
  
    Následující příklad ukazuje celý obsah souboru .vstemplate po řádku kódu XML `<TemplateGroupID>WinRT-Managed</TemplateGroupID>` do něj byl přidán. V tomto příkladu je specifické pro projekty jazyka C#. Můžete upravit <ProjectTpe> a \< [templategroupid –](../extensibility/templategroupid-element-visual-studio-templates.md)> prvků, které mají určit další typy jazyka a projektu.  
  
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
  
    Další možné templategroupid – hodnoty, najdete v části [templategroupid – Element (šablony sady Visual Studio)](../extensibility/templategroupid-element-visual-studio-templates.md)). Odkaz na kompletní .vstemplate naleznete v tématu [Visual Studio odkaz na schéma šablon](../extensibility/visual-studio-template-schema-reference.md)  
  
5. V sadě Visual Studio uložte soubor .vstemplate a zavřete ho.  
  
6. Zkopírujte a vložte soubor .vstemplate zpět do souboru .zip, který je umístěný v... \Users\\*uživatelské jméno*\Documents\Visual Studio *verze*\Templates\ItemTemplates\ složky.  
  
    Pokud **kopírovat soubor** dialogové okno se zobrazí, zvolte **kopírovat a nahradit** možnost.  
  
   Teď můžete přidat položku založenou na této šabloně [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] projektu pomocí **přidat novou položku** dialogové okno.  
  
   Další informace o názvy parametrů najdete v tématu [parametry šablony](../ide/template-parameters.md).  
  
### <a name="to-enable-templates-for-specific-project-sub-types"></a>K povolení šablony pro konkrétní dílčí typy projektů  
  
1. Vývojové prostředí umožňuje zpřístupnit položky projektu z dialogového okna Přidat položku pro určité projekty. Tímto postupem můžete zpřístupnit vlastní položky pro Windows, Web, Office nebo databázových projektů.  
  
    ProjectType – element vyhledejte v souboru .vstemplate šablony položky.  
  
    Přidat [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) element ihned po ProjectType – element.  
  
2. Textová hodnota elementu nastavena na jednu z následujících hodnot:  
  
   1. Windows  
  
   2. Office  
  
   3. Databáze  
  
   4. Web  
  
      Příklad: `<ProjectSubType>Database</ProjectSubType>`.  
  
      Následující příklad ukazuje šablonu položky k dispozici pro projekty sady Office.  
  
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
  
### <a name="to-manually-create-an-item-template-without-using-the-export-template-wizard"></a>Ruční vytvoření šablony položky bez použití průvodce Exportovat šablonu  
  
1.  Vytváření projektů a položek projektů.  
  
2.  Upravte položku projektu, dokud nebude připravený uložit jako šablonu.  
  
3.  Podle potřeby upravte soubor kódu k označení, kde by měl nastat nahrazení parametru. Další informace o nahrazení parametru najdete v tématu Postupy: náhradní parametry v šabloně.  
  
4.  Vytvořte soubor XML a uložit pomocí příponu názvu souboru .vstemplate ve stejném adresáři jako novou šablonu položky.  
  
5.  Autor XML souboru .vstemplate k poskytnutí metadat šablony položky. Další informace najdete v tématu [Visual Studio odkaz na schéma šablon](../extensibility/visual-studio-template-schema-reference.md) a v příkladu v předchozí části.  
  
6.  Uložte soubor .vstemplate a zavřete ho.  
  
7.  V Průzkumníku Windows vyberte soubory, které chcete zahrnout do šablony, klikněte pravým tlačítkem na výběr, klikněte na tlačítko Odeslat a klikněte na složku komprimované. Do souboru .zip jsou komprimované soubory, které jste vybrali.  
  
8.  Soubor ZIP zkopírujte a vložte ho do umístění šablon položek uživatele. V sadě Visual Studio 2015 je výchozí adresář... \Users\\< uživatelské jméno\>\Documents\Visual Studio 2015\Templates\ItemTemplates\\. Další informace najdete v tématu Postupy: vyhledání a organizace šablon projektů a položek.  
  
## <a name="see-also"></a>Viz také  
 [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)   
 [Postupy: vytváření šablon položek s více soubory](../ide/how-to-create-multi-file-item-templates.md)   
 [Odkaz na schéma šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)