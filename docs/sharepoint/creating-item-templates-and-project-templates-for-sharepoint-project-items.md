---
title: Šablony položek/šablony projektů pro položky projektu služby SharePoint
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, creating custom templates
- .spdata files
- projects [SharePoint development in Visual Studio], creating custom templates
- SharePoint projects, creating custom templates
- SharePoint development in Visual Studio, creating custom project and item templates
- project items [SharePoint development in Visual Studio], creating custom templates
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 65bbd58bf9b3e0b399603a083615daccc382a98f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72981164"
---
# <a name="create-item-templates-and-project-templates-for-sharepoint-project-items"></a>Vytváření šablon položek a šablon projektů pro položky projektu služby SharePoint

Při definování vlastního typu položky projektu služby SharePoint jej můžete přidružit k šabloně položky nebo šabloně projektu. Toto přidružení umožňuje jiným vývojářům používat položku projektu v aplikaci Visual Studio. Můžete také vytvořit průvodce pro šablonu.

Například Visual Studio nezahrnuje šablonu projektu nebo šablonu položky pro přidání pole na web služby SharePoint. Můžete definovat typ položky projektu služby SharePoint, který představuje pole a poté vytvořit šablonu položky, kterou mohou jiní vývojáři použít k přidání položky pole do projektu služby SharePoint. Nebo můžete vytvořit šablonu projektu, aby mohli vývojáři vytvořit nový projekt služby SharePoint, který obsahuje položku pole. V obou případech můžete také poskytnout průvodce, který se zobrazí, když vývojáři použijí vaši šablonu. Tento průvodce může shromažďovat informace od vývojářů ke konfiguraci nové položky nebo projektu.

Šablony položek a šablony projektů jsou soubory *. zip* , které obsahují soubory používané v aplikaci Visual Studio k vytvoření položky projektu nebo projektu. Další informace o základech šablon položek a šablon projektů naleznete v tématu [Create Project and Item Templates](../ide/creating-project-and-item-templates.md).

## <a name="create-item-templates"></a>Vytváření šablon položek
 Při vytváření šablony položky pro položku projektu služby SharePoint jsou vždy vyžadovány některé soubory a volitelné soubory, které mohou být použity některými typy položek projektu. Návod, který ukazuje, jak definovat typ položky projektu SharePoint a vytvořit pro ni šablonu položky, naleznete v tématu [Návod: Vytvoření vlastní položky projektu akce pomocí šablony položky, část 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).

 V následující tabulce jsou uvedeny požadované soubory pro vytvoření šablony položky pro položku projektu služby SharePoint.

|Požadovaný soubor|Popis|
|-------------------|-----------------|
|Soubor *. spdata*|Tento soubor XML určuje obsah a výchozí chování položky projektu. Tento soubor musí být zahrnutý v šabloně položky. Další informace o obsahu souborů *. spdata* naleznete v tématu Referenční dokumentace [schématu položek projektu služby SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md).|
|Soubor *. vstemplate* .|Tento soubor poskytuje aplikaci Visual Studio s informacemi požadovanými pro zobrazení šablony v dialogovém okně **Přidat novou položku** a vytvoření položky projektu ze šablony. Tento soubor musí být zahrnutý v šabloně položky. Další informace najdete v tématu [soubory metadat šablony sady Visual Studio](/previous-versions/visualstudio/visual-studio-2010/xsxc3ete\(v\=vs.100\)).|
|Sestavení rozšíření sady Visual Studio, které implementuje <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> rozhraní.|Toto sestavení definuje chování položky projektu za běhu. Toto sestavení musí být součástí balíčku VSIX se šablonou položky. Další informace naleznete v tématech [definování vlastních typů položek projektu služby SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md) a [nasazení rozšíření pro nástroje služby SharePoint v aplikaci Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).|

 V následující tabulce jsou uvedeny některé nejběžnější volitelné soubory, které mohou být zahrnuty do šablony položky. Některé typy položek projektu mohou vyžadovat jiné soubory, které zde nejsou uvedeny.

| Volitelný soubor | Popis |
|----------------------| - |
| *Elements.xml* | Soubor *elementu funkce* . Tento soubor definuje uživatelské rozhraní a chování vlastního nastavení vytvořeného položkou projektu. Každý typ přizpůsobení, jako jsou například instance seznamů, typy obsahu nebo vlastní akce, má jiné schéma, které definuje obsah tohoto souboru. Další informace najdete v tématu [stavební blok: funkce](/previous-versions/office/developer/sharepoint-2010/ee537350(v=office.14)) a [schémata funkcí](/previous-versions/office/developer/sharepoint-2010/ms414322(v=office.14)). |
| *Schema.xml* | Soubor schématu pro definice seznamu. Další informace naleznete v tématu [stavební blok: seznamy a knihovny dokumentů](/previous-versions/office/developer/sharepoint-2010/ee534985(v=office.14)) a [Schema.xml](/previous-versions/office/developer/sharepoint-2010/ms459356(v=office.14)). |
| *. WebPart* | *Definiční soubor webové části* . Tento soubor obsahuje nastavení vlastností pro webovou část. Další informace naleznete v tématu [stavební blok: webové části](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)). |
| *. ascx* | Soubor ASP.NET UserControl Tento soubor definuje uživatelské rozhraní vizuální webové části. |
| *. aspx* | ASP.NET stránkovací soubor. Tento soubor obsahuje kód XML, který definuje stránku aplikace. |
| soubory *. cs* nebo *. vb* | Tyto soubory kódu definují chování přizpůsobení SharePointu, které mají programovací model, který je k dispozici v jazyce Visual C# nebo Visual Basic kódu, jako jsou stránky aplikace, webové části a pracovní postupy. |

## <a name="create-project-templates"></a>Vytváření šablon projektu
 Při vytváření šablony projektu služby SharePoint jsou vždy vyžadovány některé soubory a volitelné soubory, které mohou být používány některými typy projektů. Projekty SharePoint obvykle obsahují alespoň jednu položku SharePointového projektu. To však není vyžadováno. Můžete například definovat šablonu projektu služby SharePoint, která je určena k použití pouze k nasazení řešení služby SharePoint vytvořených v jiných projektech.

 Návod, který ukazuje, jak definovat typ položky projektu služby SharePoint a vytvořit pro něj šablonu projektu, naleznete v tématu [Návod: vytvoření položky projektu sloupce webu pomocí šablony projektu, část 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).

 V následující tabulce jsou uvedeny soubory, které musí být zahrnuty v šabloně projektu služby SharePoint.

|Požadovaný soubor|Popis|
|-------------------|-----------------|
|Soubor *. vstemplate*|Tento soubor poskytuje aplikaci Visual Studio s informacemi požadovanými pro zobrazení šablony v dialogovém okně **Nový projekt** a vytvoření projektu ze šablony. Další informace najdete v tématu [soubory metadat šablony sady Visual Studio](/previous-versions/visualstudio/visual-studio-2010/xsxc3ete\(v\=vs.100\)).|
|Soubor *. csproj* nebo *. vbproj*|Toto je soubor projektu. Definuje obsah a nastavení konfigurace projektu.|
|*Package. Package*|Tento soubor definuje balíček pro nasazení projektu. Použijete-li návrháře balíčku k přizpůsobení balíčku řešení pro projekt, sada Visual Studio ukládá data o balíčku řešení v tomto souboru.<br /><br /> Když vytváříte vlastní šablonu projektu služby SharePoint, doporučujeme zahrnout do souboru *Package. Package* pouze minimální požadovaný obsah a nakonfigurovat balíček řešení pomocí rozhraní API v <xref:Microsoft.VisualStudio.SharePoint.Packages> oboru názvů v rozšíření, které je přidruženo k šabloně projektu. Pokud to uděláte, šablona projektu je chráněna před budoucími změnami struktury souboru *Package. Package* . Příklad, který ukazuje, jak vytvořit soubor *Package. Package* pouze s minimálním požadovaným obsahem, najdete v tématu [Návod: vytvoření položky projektu sloupce webu pomocí šablony projektu, část 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).<br /><br /> Chcete-li upravit soubor *Package. Package* přímo, můžete ověřit obsah pomocí schématu v *% Program Files (x86)% \ Microsoft Visual Studio 11.0 \ Xml\Schemas\PackageModelSchema.xsd*.|
|*Package.Template.xml*|Tento soubor poskytuje základ pro soubor manifestu řešení (*manifest.xml*) pro balíček řešení služby SharePoint (*. wsp*), který je vygenerován z projektu. Můžete přidat obsah do tohoto souboru, pokud chcete určit chování, které není určeno pro změny uživatelů typu projektu. Další informace najdete v tématu [stavební blok: řešení](/previous-versions/office/developer/sharepoint-2010/ee537008(v=office.14)) a [schéma řešení](/sharepoint/dev/schema/solution-schema).<br /><br /> Při sestavování balíčku řešení z projektu aplikace Visual Studio sloučí obsah *balíčku. Package* a *Package.Template.xml* souborů do souboru manifestu řešení. Další informace o sestavování balíčků řešení naleznete v tématu [How to: Create a web Solution Package using a Tasks MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).|

 V následující tabulce jsou uvedeny volitelné soubory, které mohou být zahrnuty v šabloně projektu.

|Volitelný soubor|Popis|
|-------------------|-----------------|
|SharePoint – položky projektu|Můžete zahrnout jeden nebo více souborů. spdata, které definují typy položek projektu služby SharePoint. Každý soubor *. spdata* musí mít odpovídající <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> implementaci v sestavení rozšíření, které je součástí balíčku VSIX se šablonou projektu. Další informace naleznete v tématu [Create Item Templates](#create-item-templates).<br /><br /> Projekty SharePoint obvykle obsahují alespoň jednu položku SharePointového projektu. To však není vyžadováno.|
|*\<featureName>. funkce*|Tento soubor definuje funkci SharePointu, která se používá k seskupení několika položek projektu pro nasazení. Při použití návrháře funkcí k přizpůsobení funkce v projektu aplikace Visual Studio ukládá data o funkci do tohoto souboru. Pokud chcete seskupit položky projektu do různých funkcí, můžete zahrnout více souborů *. Features* .<br /><br /> Když vytváříte vlastní šablonu projektu služby SharePoint, doporučujeme zahrnout do každého souboru *. Feature* pouze minimální požadovaný obsah a nakonfigurovat funkce pomocí rozhraní API v <xref:Microsoft.VisualStudio.SharePoint.Features> oboru názvů v rozšíření, které je přidruženo k šabloně projektu. Pokud to uděláte, šablona projektu je chráněna před budoucími změnami struktury souboru *. Feature* . Příklad, jak vytvořit soubor *. Feature* pouze s minimálním požadovaným obsahem, najdete v tématu [Návod: vytvoření položky projektu sloupce webu pomocí šablony projektu, část 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).<br /><br /> Chcete-li upravit soubor *. Features* přímo, můžete ověřit obsah pomocí schématu v *% Program Files (x86)% \ Microsoft Visual Studio 11.0 \ Xml\Schemas\FeatureModelSchema.xsd*.|
|*\<featureName>.Template.xml*|Tento soubor poskytuje základ pro soubor manifestu funkce (*Feature.xml*) pro každou funkci, která je vygenerována z projektu. Můžete přidat obsah do tohoto souboru, pokud chcete určit chování, které není určeno pro změny uživatelů typu projektu. Další informace najdete v tématu [stavební blok: funkce](/previous-versions/office/developer/sharepoint-2010/ee537350(v=office.14)) a [Feature.xml](/sharepoint/dev/schema/feature-xml-files) soubory.<br /><br /> Při sestavování balíčku řešení z projektu Visual Studio sloučí obsah každé dvojice souborů * \<featureName> . feature* a * \<featureName>.Template.xml* souborů do souboru manifestu funkce. Další informace o sestavování balíčků řešení naleznete v tématu [How to: Create a web Solution Package using a Tasks MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).|

## <a name="create-wizards-for-item-templates-and-project-templates"></a>Vytvoření průvodců pro šablony položek a šablony projektů
 Po definování typu položky projektu SharePoint a jeho přidružení k položce nebo šabloně projektu můžete také vytvořit průvodce. Průvodce se zobrazí, když vývojář použije šablonu položky k přidání položky SharePointového projektu do projektu, nebo když vývojář používá šablonu projektu k vytvoření nového projektu, který obsahuje položku SharePointového projektu. Průvodce lze použít ke shromažďování informací od vývojářů a k inicializaci nové položky projektu služby SharePoint.

 Postupy, které ukazují, jak vytvořit průvodce pro šablony položek a šablony projektů, naleznete v tématu [Návod: Vytvoření vlastní položky projektu akce pomocí šablony položky, část 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md) a [Návod: vytvoření položky projektu sloupce webu pomocí šablony projektu, část 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

## <a name="see-also"></a>Viz také

- [Definování vlastních typů položek projektu služby SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Návod: Vytvoření vlastní položky projektu akce pomocí šablony položky, část 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Návod: Vytvoření vlastní položky projektu akce pomocí šablony položky, část 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [Návod: vytvoření položky projektu sloupce webu pomocí šablony projektu, část 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [Návod: vytvoření položky projektu sloupce webu pomocí šablony projektu, část 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)
- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
