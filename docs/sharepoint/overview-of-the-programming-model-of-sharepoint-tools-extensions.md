---
title: Přehled modelu programování SharePoint rozšíření nástrojů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio, extending tools
- SharePoint development in Visual Studio, extensibility object models
- SharePoint development in Visual Studio, extending tools
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 82309d00d45ab6ac801297a55371cf9be5620440
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49829479"
---
# <a name="overview-of-the-programming-model-of-sharepoint-tools-extensions"></a>Přehled programovacího modelu SharePoint rozšíření nástrojů
  Při vytváření rozšíření pro nástroje služby SharePoint v sadě Visual Studio, můžete začít implementací jeden nebo více rozhraní rozšíření, které jsou vystaveny nástroje služby SharePoint. Ve většině případů bude také použít jiné typy poskytované nástroje služby SharePoint k implementaci funkcí v rozšíření. V některých scénářích můžete také použít typy v jiné objektové modely, které poskytuje Visual Studio a SharePoint. Musí pochopit účel každé z těchto objektové modely a vědět, jak pomocí nich mezi sebou můžete vytvořit rozšíření pro nástroje služby SharePoint.  

## <a name="extend-the-sharepoint-tools-by-implementing-extensibility-interfaces"></a>Rozšíření nástrojů SharePoint prostřednictvím implementace rozhraní rozšíření
 Visual Studio využívá Managed Extensibility Framework (MEF) v rozhraní .NET Framework 4 poskytuje model rozšiřitelnosti pro nástroje služby SharePoint. MEF je rozhraní API (implementované v sestavení System.ComponentModel.Composition), která umožňuje aplikacím vystavit bodů rozšiřitelnosti a zjišťovat a načíst rozšíření za běhu. Další informace o rozhraní MEF, naleznete v tématu [Managed Extensibility Framework &#40;MEF&#41;](/dotnet/framework/mef/index).  

 K rozšíření nástrojů služby SharePoint, implementujte jeden nebo více rozhraní rozšíření, které jsou přístupné pomocí sady Visual Studio. Musíte taky použít <xref:System.ComponentModel.Composition.ExportAttribute>, a pro atributy další SharePoint nástroje specifické pro danou implementaci rozhraní podle potřeby. V následující tabulce jsou uvedeny rozhraní, které můžete implementovat pro rozšíření nástrojů služby SharePoint.  

|Rozhraní|Popis|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>|Implementace tohoto rozhraní k definování nového typu položky Sharepointového projektu. Příklad najdete v tématu [postupy: definování typu položky projektu SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>|Implementace tohoto rozhraní pro rozšíření typu položky projektu služby SharePoint, která je již nainstalována v sadě Visual Studio. Příklad najdete v tématu [postupy: vytváření rozšíření položky projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>|Implementace tohoto rozhraní k rozšíření projektů SharePoint. Příklad najdete v tématu [postupy: vytváření rozšíření projektu služby SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep>|Implementace tohoto rozhraní stanovit nový krok nasazení, které mohou být provedeny, když se položky projektu služby SharePoint nasazen nebo stažen. Příklad najdete v tématu [návod: vytvoření vlastního kroku nasazení pro projekty SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>|Implementovat toto rozhraní k rozšíření existující uzel v rámci **připojení služby SharePoint** uzlu **Průzkumníka serveru** okno. Příklad najdete v tématu [postupy: rozšíření uzlu služby SharePoint v Průzkumníku serveru](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>|Implementovat toto rozhraní k definování nového typu uzlu **připojení služby SharePoint** uzlu **Průzkumníka serveru** okna. Příklad najdete v tématu [postupy: rozšíření uzlu služby SharePoint v Průzkumníku serveru](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule>|Implementace tohoto rozhraní stanovit funkce vlastní ověřovací pravidlo. Příklad najdete v tématu [postupy: vytvoření vlastní funkce a balíku ověřovacích pravidel pro řešení služby SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule>|Implementace tohoto rozhraní k definování vlastní balíček ověřovacího pravidla. Příklad najdete v tématu [postupy: vytvoření vlastní funkce a balíku ověřovacích pravidel pro řešení služby SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).|  

 Po implementaci rozšíření nástrojů služby SharePoint, je nutné nasadit sestavení rozšíření v balíčku sady Visual Studio extension (VSIX) umožňuje zjišťovat a načíst rozšíření Visual Studio. Další informace najdete v tématu [nasadit rozšíření pro nástroje služby SharePoint v sadě Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  

## <a name="understand-the-object-models-that-you-use-in-sharepoint-tools-extensions"></a>Vysvětlení objektové modely, které můžete použít rozšíření nástrojů SharePoint
 Existuje několik objektové modely, které můžete použít při vytváření rozšíření pro nástroje služby SharePoint:  

-   *Nástroje služby SharePoint objektu modelu*. Tento objektový model poskytuje rozhraní rozšíření, které můžete implementovat pro vytvoření rozšíření nástrojů služby SharePoint a dalších souvisejících typů.  

-   *Visual Studio automatizace a integrace objektové modely*. Tyto modely objektů použijte pro přístup k Visual Studio funkce, které jsou nad rámec objektového modelu SharePoint tools.  

    > [!NOTE]  
    >  Můžete převést některé objekty v objektového modelu SharePoint tools na objekty v sadě Visual Studio automatizaci a integraci objektové modely a naopak, použití služby projektu služby SharePoint. Další informace najdete v tématu [převod mezi systémovými typy projektů SharePoint a jinými typy projektů Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).  

-   *SharePoint server a klienta objektové modely*. Tyto modely objektů použijte k úpravě webu služby SharePoint nebo k načtení dat z webu služby SharePoint z kontextu rozšíření nástrojů služby SharePoint.  

### <a name="sharepoint-tools-object-model"></a>Nástroje objektového modelu SharePoint
 Každé rozšíření nástrojů SharePoint používá typy v objektovém modelu serveru SharePoint nástroje k určení základní chování a funkce rozšíření. Následující tabulky popisují obory názvů, které jsou zahrnuty v tomto modelu objektu sestavení, který je obsahuje.

#### <a name="microsoftvisualstudiosharepointdll"></a>Microsoft.VisualStudio.SharePoint.dll    

|Obor názvů|Popis|  
|-|-|  
|<xref:Microsoft.VisualStudio.SharePoint>|Obsahuje typy, které používáte pro rozšíření a automatizaci systému Sharepointových projektů. Například můžete rozšířit vestavěné projekty SharePoint a položky projektu, nebo můžete vytvořit vlastní položky projektu. Další informace najdete v tématu [rozšíření systému projektu služby SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Deployment>|Obsahuje typy, které můžete použít k rozšíření procesu nasazení pro projekty služby SharePoint, jako je například vytváření kroky nasazení a konfigurace nasazení. Další informace najdete v tématu [balení a nasazení rozšíření SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Explorer>|Obsahuje typy, které používáte pro rozšíření uzlů v rámci **připojení služby SharePoint** uzlu **Průzkumníka serveru** okno, nebo k definování nových typů uzlů. Další informace najdete v tématu [rozšíření uzlu připojení služby SharePoint v Průzkumníku serveru](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Features>|Obsahuje typy, které používáte pro přístup k definici funkce v projektu služby SharePoint.|  
|<xref:Microsoft.VisualStudio.SharePoint.Packages>|Obsahuje typy, které používáte pro přístup k definici balíčku v řešení služby SharePoint.|  
|<xref:Microsoft.VisualStudio.SharePoint.Validation>|Obsahuje typy, které můžete použít k přizpůsobení funkce a balíku chování ověřování pro projekty služby SharePoint. Další informace najdete v tématu [postupy: vytvoření vlastní funkce a balíku ověřovacích pravidel pro řešení služby SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).| 

#### <a name="microsoftvisualstudiosharepointcommandsdll"></a>Microsoft.VisualStudio.SharePoint.Commands.dll

|Obor názvů|Popis|  
|-|-|  
|<xref:Microsoft.VisualStudio.SharePoint.Commands>|Obsahuje typy, které můžete použít k vytvoření vlastních *příkazů služby SharePoint*. Příkaz serveru SharePoint je metoda, která volá do objektového modelu serveru SharePoint z rozšíření nástrojů služby SharePoint. Další informace najdete v tématu [volání do objektových modelů služby SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).|

#### <a name="microsoftvisualstudiosharepointexplorerextensionsdll"></a>Microsoft.VisualStudio.SharePoint.Explorer.Extensions.dll

|Obor názvů|Popis|  
|-|-| 
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions>|Obsahuje typy, které vám umožní získat informace o předdefinovaných **Průzkumníka serveru** uzly, které představují jednotlivé součásti na Sharepointovém webu, jako je například uzel, který představuje seznam, pole nebo typ obsahu. Další informace najdete v tématu [rozšíření uzlu připojení služby SharePoint v Průzkumníku serveru](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).|  

### <a name="visual-studio-automation-object-model"></a>Model objektu automatizace aplikace Visual Studio
 Model objektu automatizace sady Visual Studio poskytuje rozhraní API, která vám umožní automatizovat projektů sady Visual Studio a rozhraní IDE. Použijte model objektu sady Visual Studio, provádět úlohy související s projektem, které nejsou specifické pro projekty SharePoint nebo provádět další úlohy obecné automatizace v sadě Visual Studio. Tradičně tento objektový model se často používá v doplňky sady Visual Studio a makra, ale můžete ho použít také v rozšíření nástrojů služby SharePoint.  

 Hlavní část objektového modelu automatizace sady Visual Studio je definován v *EnvDTE.dll* sestavení. *EnvDTE\\<version>.dll* sestavení poskytují další funkce, která byla zavedena v konkrétní verze sady Visual Studio. Tato sestavení jsou součástí sady Visual Studio.  

 Další informace o modelu automatizačních objektů naleznete v tématu [referenční dokumentace jazyka Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md).  

### <a name="visual-studio-integration-object-model"></a>Objektový model sady Visual Studio integrace
 Integrace objektový model poskytuje rozhraní API, která slouží k přidání funkcí do sady Visual Studio tak, že vytvoříte *VSPackage*. VSPackage je modul, který je rozšířením rozhraní IDE sady Visual Studio poskytuje vlastní funkce, jako je například okna nástrojů, editory, návrháře, služby a projekty.  

 Pokud chcete přidat nové funkce sady Visual Studio, který se použije pomocí integrovaných nástrojů služby SharePoint, můžete použít objektový model integrace. Například pokud vytvoříte vlastní položky projektu služby SharePoint, který představuje vlastní akce pro web služby SharePoint, můžete také vytvořit VSPackage, která implementuje návrháře pro vlastní akci. Můžete přidružit návrháři vlastní akce přidáním položky místní nabídky do položky projektu, který představuje vlastní akce v **Průzkumníka řešení**. Můžete otevřít návrháře tak, že otevřete místní nabídku (kliknutím pravým tlačítkem myši vlastní položky projektu akce nebo jej vyberete a potom kliknete **Shift**+**F10** klíče) a následným výběrem možnosti **Otevřít**.  

 Tento objektový model je definován v sadě sestavení, které jsou součástí sady Visual Studio SDK. Mezi hlavní sestavení v tomto modelu objektu patří *Microsoft.VisualStudio.Shell.11.0.dll*, *Microsoft.VisualStudio.Shell.Interop.dll*, a  *Microsoft.VisualStudio.OLE.Interop.dll*.  

 Další informace o integraci objektový model, najdete v části [přehled modelu automatizace](/visualstudio/extensibility/internals/automation-model-overview) a [referenční dokumentace jazyka Visual Studio SDK](/visualstudio/extensibility/visual-studio-sdk-reference).  

### <a name="sharepoint-object-models"></a>Objektových modelů služby SharePoint
 Rozšíření nástrojů služby SharePoint můžete použít rozhraní API služby SharePoint k úpravě webu služby SharePoint nebo k načtení dat z webu služby SharePoint. [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] a [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] poskytují dvou různých objektových modelů: objektový model serveru a objektového modelu klienta.  

 Rozhraní API můžete použít v objektovém modelu v rozšíření nástrojů služby SharePoint, ale každý model objektu má některé výhody a nevýhody v rámci rozšíření nástrojů služby SharePoint. Další informace najdete v tématu [volání do objektových modelů služby SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).  

|Objektový model|Popis|  
|------------------|-----------------|  
|Objektový model serveru|Objektový model serveru poskytuje přístup ke všem funkcím, které [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] a [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] zveřejnit prostřednictvím kódu programu. Tento objektový model je navržená pro řešení služby SharePoint, které běží na serveru SharePoint. Většina tento objektový model je definován v *Microsoft.SharePoint.dll* sestavení. Další informace o objektovém modelu serveru najdete v tématu [pomocí objektového modelu SharePoint Foundation na straně serveru](http://go.microsoft.com/fwlink/?LinkId=177796).|  
|Model klientského objektu|Objektového modelu klienta je podmnožinou objektový model serveru, který umožňuje vzájemnou spolupráci se službami data služby SharePoint ze vzdáleného klienta nebo serveru. Je určená k minimalizaci počet zpátečních cest, které je třeba spustit provádění běžných úloh. Většina objektového modelu klienta je definována v *sestavení Microsoft.SharePoint.Client.dll* a *Microsoft.SharePoint.Client.Runtime.dll* sestavení. Další informace o objektovém modelu klienta najdete v tématu [spravované objektového modelu klienta](http://go.microsoft.com/fwlink/?LinkId=177797).|  

## <a name="see-also"></a>Viz také:
 [Rozšíření nástrojů SharePoint v sadě Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Volání do objektových modelů služby SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Použití služby projektu SharePoint](../sharepoint/using-the-sharepoint-project-service.md)  

