---
title: Vytvoření položky šablony a šablony projektů pro položky projektu služby SharePoint | Dokumentace Microsoftu
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d181891fb36645e4f246aa0c2238c12ea1dc4903
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296005"
---
# <a name="create-item-templates-and-project-templates-for-sharepoint-project-items"></a>Vytváření šablon položek a projektů pro položky projektu SharePoint
  Při definování vlastního typu položky projektu služby SharePoint můžete přidružit ho šabloně položky nebo šablony projektu. Toto přidružení umožňuje ostatním vývojářům použít položku projektu v sadě Visual Studio. Můžete také vytvořit průvodce pro šablony.

 Například Visual Studio neobsahuje šablonu projektu nebo šablony položky pro přidání pole s webem služby SharePoint. Můžete definovat typ položky projektu služby SharePoint, který představuje pole a pak vytvořit šablony položky, ostatní vývojáři můžete použít k přidání položky pole do projektu služby SharePoint. Nebo můžete vytvořit šablonu projektu tak, aby vývojáři mohou vytvořit nový projekt služby SharePoint, který má položku pole. V obou případech můžete také zadat průvodce, který se zobrazí, když vývojáři pomocí šablony. Tento průvodce může shromažďovat informace od vývojářů pro konfiguraci nové položky nebo projektu.

 Šablony položek a šablony projektů jsou *ZIP* soubory, které obsahují soubory, které umožňují pomocí sady Visual Studio vytvořte projekt nebo položku projektu. Další informace o základní informace o šablon položek a projektů, naleznete v tématu [vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md).

## <a name="create-item-templates"></a>Vytváření šablon položek
 Když vytvoříte šablonu položky pro položky projektu služby SharePoint, existují některé soubory, které jsou vždy povinné a volitelné soubory, které by mohly používat určitých typů položek projektu. Názorný postup ukazuje, jak definovat typ položky projektu služby SharePoint a vytvoří se pro něj šablony položky, naleznete v tématu [návod: vytvoření vlastní položky projektu akce pomocí šablony položky, část 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).

 V následující tabulce jsou uvedeny požadované soubory k vytvoření šablony položky pro položky Sharepointového projektu.

|Požadovaný soubor|Popis|
|-------------------|-----------------|
|*.Spdata* souboru|Tento soubor XML určuje obsah a výchozí chování položky projektu. Tento soubor musí být součástí šablony položky. Další informace o obsahu *.spdata* soubory, naleznete v tématu [referenční dokumentace schématu položek projektu služby SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md).|
|A *.vstemplate* souboru.|Tento soubor poskytuje informace potřebné k zobrazení šablony v sadě Visual Studio **přidat novou položku** dialogové okno a vytvoření položky projektu z šablony. Tento soubor musí být součástí šablony položky. Další informace najdete v tématu [soubory metadat šablony Visual Studio](/previous-versions/visualstudio/visual-studio-2010/xsxc3ete\(v\=vs.100\)).|
|Sestavení rozšíření sady Visual Studio, který implementuje <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> rozhraní.|Toto sestavení definuje chování položky projektu. Toto sestavení musí být součástí balíčku souboru VSIX pomocí šablony položky. Další informace najdete v tématu [definování vlastních typů položek projektu služby SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md) a [nasadit rozšíření pro nástroje služby SharePoint v sadě Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).|

 V následující tabulce jsou uvedeny některé nejběžnější volitelné soubory, které mohou být zahrnuty v šabloně položky. Některé typy položek projektu může vyžadovat další soubory, které tu nejsou uvedené.


| Volitelný soubor | Popis |
|----------------------| - |
| *Elements.XML* | A *elementu funkce* souboru. Tento soubor definuje uživatelské rozhraní a chování přizpůsobení vytvořené položky projektu. Každý typ vlastního nastavení, jako je například instance seznamů, typů obsahu nebo vlastních akcí, má jiné schéma, který definuje obsah tohoto souboru. Další informace najdete v tématu [stavebním blokem: funkce](http://go.microsoft.com/fwlink/?LinkId=169183) a [funkce schémata](http://go.microsoft.com/fwlink/?LinkId=169192). |
| *Souboru Schema.XML* | Soubor schématu definice seznamu. Další informace najdete v tématu [stavebním blokem: seznamy a knihovny dokumentů](http://go.microsoft.com/fwlink/?LinkId=177792) a [Schema.xml](http://go.microsoft.com/fwlink/?LinkId=177793). |
| *soubor WebPart* | A *webovou část definice* souboru. Tento soubor obsahuje nastavení vlastností pro webové části. Další informace najdete v tématu [stavebním blokem: webové části](http://go.microsoft.com/fwlink/?LinkId=177791). |
| *.ascx* | Soubor uživatelský ovládací prvek technologie ASP.NET. Tento soubor definuje uživatelské rozhraní vizuální webové části. |
| *aspx* | Soubor stránky technologie ASP.NET. Tento soubor obsahuje kód XML, který definuje stránky aplikace. |
| *.cs* nebo *.vb* soubory | Tyto soubory kódu definuje chování přizpůsobení Sharepointu, které mají programovací model, který je přístupný z Vizuálu C# nebo kódu jazyka Visual Basic, například stránky aplikace, webové části a pracovních postupů. |

## <a name="create-project-templates"></a>Vytváření šablon projektu
 Když vytvoříte šablonu projektu služby SharePoint, existují některé soubory, které jsou vždy požadované a volitelné soubory, které by mohly používat určité typy projektů. Projekty SharePoint obvykle zahrnují aspoň jedna položka Sharepointového projektu. To však není povinné. Můžete například definovat šablonu projektu služby SharePoint, který se má použít pouze k nasazení řešení služby SharePoint vytvoří v jiných projektech.

 Návod, jak definovat typ položky projektu služby SharePoint a vytvoří se šablona projektu pro něj najdete v tématu [návod: vytvoření položky projektu sloupce webu pomocí šablony projektu, část 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).

 Následující tabulka uvádí soubory, které musí být součástí šablona projektu služby SharePoint.

|Požadovaný soubor|Popis|
|-------------------|-----------------|
|A *.vstemplate* souboru|Tento soubor poskytuje informace potřebné k zobrazení šablony v sadě Visual Studio **nový projekt** dialogové okno a vytvoření projektu ze šablony. Další informace najdete v tématu [soubory metadat šablony Visual Studio](/previous-versions/visualstudio/visual-studio-2010/xsxc3ete\(v\=vs.100\)).|
|A *.csproj* nebo *.vbproj* souboru|Jedná se o soubor projektu. Definuje obsah a nastavení konfigurace projektu.|
|*Package.Package*|Tento soubor definuje balíček pro nasazení pro projekt. Při použití návrháře balíčků k přizpůsobení balíčku řešení pro váš projekt sady Visual Studio ukládá data o balíčku pro řešení v tomto souboru.<br /><br /> Při vytváření vlastní šablona projektu služby SharePoint, doporučujeme vám, že složku zahrnujete pouze minimální požadovaný obsah v *Package.package* souboru a konfiguraci balíčku řešení pomocí rozhraní API v <xref:Microsoft.VisualStudio.SharePoint.Packages> obor názvů v rozšíření, která je přidružená k šabloně projektu. Pokud to uděláte, šablony projektu je chráněný před budoucí změny struktury *Package.package* souboru. Příklad, který ukazuje, jak vytvořit *Package.package* obsah souboru s pouze minimálním předpokladem naleznete v tématu [návod: vytvoření položky projektu sloupce webu pomocí šablony projektu, část 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).<br /><br /> Pokud chcete změnit *Package.package* souboru přímo, můžete ověřit obsah pomocí schématu v *% Program Files (Visual Studio 11.0\Xml\Schemas\PackageModelSchema.xsd x86)%\Microsoft* .|
|*Package.Template.xml*|Tento soubor poskytuje základ pro řešení soubor manifestu (*manifest.xml*) balíčku řešení služby SharePoint (*.wsp*), který je generován z projektu. Pokud chcete zadat některé rysy chování sady, který není určený k jejich změně uživatelé typu projektu, můžete přidat obsah do tohoto souboru. Další informace najdete v tématu [stavebním blokem: řešení](http://go.microsoft.com/fwlink/?LinkId=169186) a [řešení schématu](http://go.microsoft.com/fwlink/?LinkId=177794).<br /><br /> Při vytváření balíčku řešení z projektu sady Visual Studio sloučí obsah *Package.package* a *Package.Template.xml* soubor manifestu souborů do řešení. Další informace o vytváření balíčků řešení najdete v tématu [postupy: vytvoření balíčku řešení SharePoint pomocí úloh nástroje MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).|

 Následující tabulka uvádí volitelné soubory, které mohou být součástí šablony projektu.

|Volitelný soubor|Popis|
|-------------------|-----------------|
|SharePoint – položky projektu|Může obsahovat jeden nebo více souborů .spdata, které definují typů položek projektu služby SharePoint. Každý *.spdata* soubor musí mít odpovídající <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> provádění v rozšíření sestavení, který je zahrnutý v balíčku souboru VSIX pomocí šablony projektu. Další informace najdete v tématu [vytváření šablon položek](#creatingitemtemplates).<br /><br /> Projekty SharePoint obvykle zahrnují aspoň jedna položka Sharepointového projektu. To však není povinné.|
|*\<featureName > .feature*|Tento soubor definuje funkce služby SharePoint, který slouží k seskupení několik položek projektu pro nasazení. Při použití návrháře funkcí k přizpůsobení funkce ve vašem projektu, Visual Studio ukládá data o funkci v tomto souboru. Pokud chcete seskupit položky projektu do jiné funkce, může obsahovat více *.feature* soubory.<br /><br /> Když vytvoříte vlastní šablona projektu služby SharePoint, doporučujeme zahrnout pouze minimální požadovaný obsah v každém *.feature* souboru a konfiguraci funkcí s použitím rozhraní API v <xref:Microsoft.VisualStudio.SharePoint.Features> obor názvů v rozšíření, který je spojen se šablonou projektu. Pokud to uděláte, šablony projektu je chráněný před budoucí změny struktury *.feature* souboru. Příklad, který ukazuje, jak vytvořit *.feature* obsah souboru s pouze minimálním předpokladem naleznete v tématu [návod: vytvoření položky projektu sloupce webu pomocí šablony projektu, část 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).<br /><br /> Pokud chcete upravit *.feature* souboru přímo, můžete ověřit obsah pomocí schématu v *% Program Files (x86)%\Microsoft sady Visual Studio 11.0\Xml\Schemas\FeatureModelSchema.xsd*.|
|*\<featureName >. Template.XML*|Tento soubor poskytuje základ pro soubor manifestu funkce (*Feature.xml*) pro jednotlivé funkce, který je generován z projektu. Pokud chcete zadat některé rysy chování sady, který není určený k jejich změně uživatelé typu projektu, můžete přidat obsah do tohoto souboru. Další informace najdete v tématu [stavebním blokem: funkce](http://go.microsoft.com/fwlink/?LinkId=169183) a [Feature.xml](http://go.microsoft.com/fwlink/?LinkId=177795) soubory.<br /><br /> Při vytváření balíčku řešení z projektu sady Visual Studio slučuje obsah každý pár  *\<featureName > .feature* souboru a  *\<featureName >. Template.xml* soubory do funkce soubor manifestu. Další informace o vytváření balíčků řešení najdete v tématu [postupy: vytvoření balíčku řešení SharePoint pomocí úloh nástroje MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).|

## <a name="create-wizards-for-item-templates-and-project-templates"></a>Vytváření průvodců pro šablony položek a šablony projektů
 Po definování typu položky projektu služby SharePoint a přidružte jej k šablonu položky nebo projektu, můžete také vytvořit průvodce. Průvodce zobrazí, když vývojář používá šablonu položky pro přidání položky projektu služby SharePoint do projektu, nebo když vývojář používá šablonu projektu pro vytvoření nového projektu, který obsahuje položku Sharepointového projektu. Průvodce můžete použít ke shromažďování informací od vývojářů a inicializujte novou položku Sharepointového projektu.

 Návody, které ukazují, jak vytvořit průvodce pro šablony položek a šablony projektů, naleznete v tématu [návod: vytvoření vlastní akce položky projektu pomocí šablony položky, část 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md) a [návod: vytvoření webu položky projektu sloupce pomocí šablony projektu, část 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

## <a name="see-also"></a>Viz také:

- [Definování vlastních typů položek projektu služby SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Návod: Vytvoření vlastní položky projektu akce pomocí šablony položky, část 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Návod: Vytvoření vlastní položky projektu akce pomocí šablony položky, část 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [Návod: Vytvoření položky projektu sloupce webu pomocí šablony projektu, část 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [Návod: Vytvoření položky projektu sloupce webu pomocí šablony projektu, část 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)
- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
