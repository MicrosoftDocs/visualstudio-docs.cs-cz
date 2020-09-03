---
title: Přehled programovacího modelu rozšíření nástrojů služby SharePoint
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio, extending tools
- SharePoint development in Visual Studio, extensibility object models
- SharePoint development in Visual Studio, extending tools
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 160751e7f580ede458232f98dc753a1145094f57
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72985148"
---
# <a name="overview-of-the-programming-model-of-sharepoint-tools-extensions"></a>Přehled programovacího modelu rozšíření nástrojů služby SharePoint
  Při vytváření rozšíření pro nástroje služby SharePoint v aplikaci Visual Studio začínáte implementací jednoho nebo více rozhraní rozšíření, která jsou zpřístupněna pomocí nástrojů služby SharePoint. Ve většině případů budete k implementaci funkcí v rozšíření používat také další typy poskytované nástroji SharePoint. V některých scénářích můžete také použít typy v jiných objektových modelech poskytovaných aplikací Visual Studio a SharePoint. Je nutné pochopit účel každého z těchto objektových modelů a zjistit, jak je lze vzájemně používat k vytváření rozšíření pro nástroje služby SharePoint.

## <a name="extend-the-sharepoint-tools-by-implementing-extensibility-interfaces"></a>Rozšíření nástrojů služby SharePoint implementací rozhraní rozšíření
 Visual Studio používá rozhraní Managed Extensibility Framework (MEF) v .NET Framework 4 k poskytnutí modelu rozšiřitelnosti pro nástroje služby SharePoint. MEF je rozhraní API (implementované v sestavení System. ComponentModel. složení), které umožňuje aplikacím vystavit body rozšiřitelnosti a zjišťovat a načítat rozšíření za běhu. Další informace o MEF naleznete v tématu [Managed Extensibility Framework &#40;mef&#41;](/dotnet/framework/mef/index).

 Chcete-li rozšíření nástrojů služby SharePoint, implementujte jedno nebo více rozhraní rozšíření, která jsou zpřístupněna v rámci sady Visual Studio. Pro implementaci rozhraní je nutné také použít <xref:System.ComponentModel.Composition.ExportAttribute> a další atributy specifické pro nástroje služby SharePoint. Následující tabulka uvádí rozhraní, která lze implementovat pro rozšiřování nástrojů služby SharePoint.

|Rozhraní|Popis|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>|Implementujte toto rozhraní pro definování nového typu položky projektu služby SharePoint. Příklad naleznete v tématu [How to: define a typu položky projektu SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).|
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>|Implementujte toto rozhraní pro rozšiřování typu položky projektu služby SharePoint, která je již nainstalována v aplikaci Visual Studio. Příklad naleznete v tématu [Postupy: Vytvoření rozšíření položky projektu služby SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).|
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>|Implementujte toto rozhraní pro rozšiřování projektů SharePoint. Příklad naleznete v tématu [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep>|Implementujte toto rozhraní pro definování nového kroku nasazení, který lze provést při nasazení nebo odvolání položky projektu služby SharePoint. Příklad naleznete v tématu [Návod: Vytvoření vlastního kroku nasazení pro projekty služby SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>|Implementujte toto rozhraní, abyste rozšířili existující uzel pod uzlem **připojení služby SharePoint** v okně **Průzkumník serveru** . Příklad naleznete v tématu [How to: extend a Node SharePoint in Průzkumník serveru](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>|Implementujte toto rozhraní pro definování nového typu uzlu v uzlu **připojení služby SharePoint** v okně **Průzkumník serveru** . Příklad naleznete v tématu [How to: extend a Node SharePoint in Průzkumník serveru](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule>|Implementujte toto rozhraní a definujte vlastní ověřovací pravidlo funkce. Příklad najdete v tématu [Postup: Vytvoření vlastní funkce a pravidel ověřování balíčku pro řešení služby SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule>|Implementací tohoto rozhraní můžete definovat vlastní ověřovací pravidlo balíčku. Příklad najdete v tématu [Postup: Vytvoření vlastní funkce a pravidel ověřování balíčku pro řešení služby SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).|

 Po implementaci rozšíření nástrojů služby SharePoint je nutné nasadit sestavení rozšíření v balíčku rozšíření sady Visual Studio (VSIX), aby sada Visual Studio mohla vyhledat a načíst rozšíření. Další informace naleznete v tématu [nasazení rozšíření pro nástroje služby SharePoint v aplikaci Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="understand-the-object-models-that-you-use-in-sharepoint-tools-extensions"></a>Pochopení objektových modelů, které používáte v rozšířeních nástrojů služby SharePoint
 K dispozici je několik modelů objektů, které můžete použít při vytváření rozšíření pro nástroje služby SharePoint:

- *Objektový model nástrojů služby SharePoint*. Tento objektový model poskytuje rozhraní rozšíření, které implementujete pro vytváření rozšíření nástrojů služby SharePoint a další související typy.

- *Modely automatizace a objekty integrace sady Visual Studio*. Tyto objektové modely použijte pro přístup k funkcím sady Visual Studio, které jsou nad rámec modelu objektů nástrojů služby SharePoint.

    > [!NOTE]
    > Můžete převést některé objekty v objektovém modelu nástrojů služby SharePoint na objekty v modelech automatizace a objektů integrace sady Visual Studio a naopak, pomocí služby projektu služby SharePoint. Další informace naleznete v tématu [Převod mezi systémovými typy projektů SharePoint a jinými typy projektů aplikace Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).

- *Modely a objekty klienta serveru SharePoint*. Pomocí těchto objektových modelů můžete upravit web služby SharePoint nebo načíst data z webu služby SharePoint z kontextu rozšíření nástrojů služby SharePoint.

### <a name="sharepoint-tools-object-model"></a>Objektový model nástrojů služby SharePoint
 Každé rozšíření nástrojů služby SharePoint používá typy v objektovém modelu nástrojů služby SharePoint k definování základního chování a funkce rozšíření. Následující tabulky popisují obory názvů, které jsou zahrnuty v tomto objektovém modelu, sestavením, které je obsahuje.

#### <a name="microsoftvisualstudiosharepointdll"></a>Microsoft.VisualStudio.SharePoint.dll

|Obor názvů|Popis|
|-|-|
|<xref:Microsoft.VisualStudio.SharePoint>|Obsahuje typy, které slouží k rozšiřování a automatizaci systému projektu služby SharePoint. Můžete například zvětšit předdefinované projekty služby SharePoint a položky projektu, nebo můžete vytvořit vlastní položky projektu. Další informace najdete v tématu věnovaném [roztažení systému projektu služby SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Deployment>|Obsahuje typy, které slouží k rozšiřování procesu nasazení pro projekty služby SharePoint, jako je například vytváření vlastních kroků nasazení a konfigurace nasazení. Další informace najdete v tématu věnovaném [rozšiřování balení a nasazení služby SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Explorer>|Obsahuje typy, které slouží k rozšiřování uzlů v uzlu **připojení služby SharePoint** v okně **Průzkumník serveru** , nebo pro definování nových typů uzlů. Další informace najdete v tématu věnovaném [rozšiřování uzlu připojení služby SharePoint v Průzkumník serveru](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Features>|Obsahuje typy, které používáte pro přístup k definicím funkcí v projektu služby SharePoint.|
|<xref:Microsoft.VisualStudio.SharePoint.Packages>|Obsahuje typy, které používáte pro přístup k definici balíčku v řešení služby SharePoint.|
|<xref:Microsoft.VisualStudio.SharePoint.Validation>|Obsahuje typy, které slouží k přizpůsobení funkce a chování ověření balíčku pro projekty služby SharePoint. Další informace najdete v tématu [Postupy: vytváření vlastních funkcí a pravidel ověřování balíčku pro řešení služby SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).|

#### <a name="microsoftvisualstudiosharepointcommandsdll"></a>Microsoft.VisualStudio.SharePoint.Commands.dll

|Obor názvů|Popis|
|-|-|
|<xref:Microsoft.VisualStudio.SharePoint.Commands>|Obsahuje typy, které lze použít k vytvoření vlastních *příkazů služby SharePoint*. Příkaz služby SharePoint je metoda, která volá do objektového modelu serveru SharePoint z rozšíření nástrojů služby SharePoint. Další informace naleznete v tématu [volání do objektových modelů služby SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).|

#### <a name="microsoftvisualstudiosharepointexplorerextensionsdll"></a>Microsoft.VisualStudio.SharePoint.Explorer.Extensions.dll

|Obor názvů|Popis|
|-|-|
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions>|Obsahuje typy, které můžete použít k získání informací o předdefinovaných **Průzkumník serveru** uzlech, které představují jednotlivé komponenty na webu služby SharePoint, jako je například uzel, který představuje seznam, pole nebo typ obsahu. Další informace najdete v tématu věnovaném [rozšiřování uzlu připojení služby SharePoint v Průzkumník serveru](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).|

### <a name="visual-studio-automation-object-model"></a>Model automatizačních objektů sady Visual Studio
 Objektový model automatizace sady Visual Studio poskytuje rozhraní API, která můžete použít k automatizaci projektů sady Visual Studio a rozhraní IDE. Model objektu sady Visual Studio použijte k provádění úloh souvisejících s projektem, které nejsou specifické pro projekty služby SharePoint, nebo k provádění dalších obecných úloh automatizace v aplikaci Visual Studio. Tradičně se tento objektový model často používá v doplňcích a makrech sady Visual Studio, ale můžete ho použít také v rozšířeních nástrojů služby SharePoint.

 Hlavní část modelu objektu automatizace sady Visual Studio je definována v sestavení *EnvDTE.dll* . Sestavení *EnvDTE \\ \<version> . dll* poskytují další funkce, které byly představeny v určitých verzích sady Visual Studio. Tato sestavení jsou součástí sady Visual Studio.

 Další informace o modelu automatizačních objektů naleznete v tématu [Referenční dokumentace sady Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md).

### <a name="visual-studio-integration-object-model"></a>Model integračních objektů sady Visual Studio
 Model integračních objektů poskytuje rozhraní API, která lze použít k přidání funkcí do sady Visual Studio vytvořením *VSPackage*. VSPackage je modul, který rozšiřuje prostředí Visual Studio IDE tím, že poskytuje vlastní funkce, jako jsou například okna nástrojů, editory, návrháři, služby a projekty.

 Model integračních objektů můžete použít, pokud chcete přidat novou funkci sady Visual Studio, která bude použita s vestavěnými nástroji služby SharePoint. Například pokud vytvoříte vlastní položku projektu služby SharePoint, která představuje vlastní akci pro web služby SharePoint, můžete také vytvořit VSPackage, který implementuje návrháře pro vlastní akci. Můžete přidružit návrháře k vlastní akci přidáním položky místní nabídky do položky projektu, která představuje vlastní akci v **Průzkumník řešení**. Návrháře můžete otevřít tak, že otevřete jeho místní nabídku (buď kliknutím pravým tlačítkem myši na položku projektu vlastní akce, nebo výběrem možnosti a následným výběrem klávesy **SHIFT** + **F10** ) a kliknutím na **tlačítko otevřít**.

 Tento objektový model je definován v sadě sestavení, která jsou součástí sady Visual Studio SDK. Mezi hlavní sestavení v tomto objektovém modelu patří *Microsoft.VisualStudio.Shell.11.0.dll*, *Microsoft.VisualStudio.Shell.Interop.dll*a *Microsoft.VisualStudio.OLE.Interop.dll*.

 Další informace o modelu integračních objektů naleznete v tématu [Přehled modelu automatizace](../extensibility/internals/automation-model-overview.md) a [Referenční dokumentace sady Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md).

### <a name="sharepoint-object-models"></a>Objektové modely služby SharePoint
 Rozšíření nástrojů služby SharePoint mohou používat rozhraní API služby SharePoint k úpravě webu služby SharePoint nebo k načítání dat z webu služby SharePoint. [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] a [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] poskytují dva různé objektové modely: serverový objektový model a klientský objektový model.

 Rozhraní API můžete použít buď v objektovém modelu v rozšíření nástrojů služby SharePoint, ale každý objektový model má některé výhody a nevýhody v kontextu rozšíření nástrojů služby SharePoint. Další informace naleznete v tématu [volání do objektových modelů služby SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

|Objektový model|Popis|
|------------------|-----------------|
|Objektový model serveru|Objektový model serveru poskytuje přístup ke všem funkcím, které [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] a [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] zveřejňuje programově. Tento objektový model je navržený tak, aby ho mohli používat řešení SharePoint, která běží na SharePointovém serveru. Většina tohoto objektového modelu je definována v sestavení *Microsoft.SharePoint.dll* . Další informace o objektovém modelu serveru naleznete v tématu [použití modelu objektu na straně serveru služby SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/ee538251(v=office.14)).|
|Objektový model klienta|Objektový model klienta je podmnožinou objektového modelu serveru, který lze použít pro spolupráci se službou SharePoint data ze vzdáleného klienta nebo serveru. Je navržena tak, aby minimalizovala počet zpátečních cest, které je nutné provést, aby bylo možné provádět běžné úkoly. Většina objektového modelu klienta je definována v sestaveních *Microsoft.SharePoint.Client.dll* a *Microsoft.SharePoint.Client.Runtime.dll* . Další informace o objektovém modelu klienta najdete v tématu [model objektu spravovaného klienta](/previous-versions/office/developer/sharepoint-2010/ee537247(v=office.14)).|

## <a name="see-also"></a>Viz také
- [Rozšiřování nástrojů služby SharePoint v aplikaci Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [Volání do objektových modelů služby SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Použití služby projektu SharePoint](../sharepoint/using-the-sharepoint-project-service.md)
