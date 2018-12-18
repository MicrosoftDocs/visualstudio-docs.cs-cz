---
title: 'Postupy: Přidání vlastnosti do projektů služby SharePoint | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c956da1df5507d2efecb3ff72f034d54fb377eb5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49898407"
---
# <a name="how-to-add-a-property-to-sharepoint-projects"></a>Postupy: Přidání vlastnosti do projektů služby SharePoint
  Rozšíření projektu můžete použít k přidání vlastnosti do jakéhokoli projektu SharePoint. Vlastnost se zobrazí v **vlastnosti** okno, když je projekt určený v **Průzkumníka řešení**.  
  
 Následující postup předpokládá, že jste již vytvořili projekt rozšíření. Další informace najdete v tématu [postupy: vytváření rozšíření projektu služby SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
### <a name="to-add-a-property-to-a-sharepoint-project"></a>Přidání vlastnosti do projektu SharePoint  
  
1.  Definice třídy s veřejné vlastnosti, která reprezentuje vlastnost, kterou chcete přidat do projektů služby SharePoint. Pokud chcete přidat více vlastností, můžete definovat všechny vlastnosti ve stejné třídě nebo v různých tříd.  
  
2.  V <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> metodu vaše <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> implementace, popisovač <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> událost *projectService* parametru.  
  
3.  V obslužné rutině události pro <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> události, přidá instanci třídy vlastnosti má <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectPropertiesRequestedEventArgs.PropertySources%2A> kolekce parametr argumenty události.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak přidat dvě vlastnosti do projektů služby SharePoint. Jednu vlastnost nevyřeší svá data v souboru projektu uživatelské možnosti ( *. csproj.user* souboru nebo *. vbproj.user* souboru). Jiné vlastnosti nevyřeší svoje data v souboru projektu (*.csproj* souboru nebo *.vbproj* souboru).  
  
 [!code-vb[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#1)]
 [!code-csharp[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#1)]  
  
### <a name="understand-the-code"></a>Vysvětlení kódu  
 Chcete-li zajistit stejnou instanci `CustomProjectProperties` třída se používá pokaždé, když <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> dojde k události, příklad kódu přidá vlastnosti objektu, který chcete <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> vlastnost projektu první, když dojde k této události. Kód načte tento objekt pokaždé, když se tato událost bude opakovat. Další informace o používání <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> vlastnost pro přidružení data s projekty, naleznete v tématu [rozšíření nástrojů přidružení vlastních dat se Sharepointem](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
 Zachovat změny hodnot vlastností **nastavit** přistupující objekty vlastností, použijte následující rozhraní API:  
  
- `CustomUserFileProperty` používá <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> vlastnost uložte jeho hodnota pro možnost uživatelského souboru projektu.  
  
- `CustomProjectFileProperty` používá <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> metody uložte jeho hodnotu do souboru projektu.  
  
  Další informace o zachování dat v těchto souborech najdete v tématu [ukládání dat do rozšíření systému projektu služby SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
### <a name="specify-the-behavior-of-custom-properties"></a>Zadejte chování vlastní vlastnosti  
 Můžete definovat, jak vlastní vlastnosti se zobrazí a jak se bude chovat v **vlastnosti** okna s použitím atributů z <xref:System.ComponentModel> oboru názvů v definici vlastnosti. Následující atributy jsou užitečné v mnoha scénářích:  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>: Určuje název vlastnosti, která se zobrazí **vlastnosti** okna.  
  
-   <xref:System.ComponentModel.DescriptionAttribute>: Určuje popis řetězec, který se zobrazí v dolní části **vlastnosti** okno, pokud je vybrána vlastnost.  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>: Určuje výchozí hodnotu vlastnosti.  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>: Určuje vlastní převod mezi řetězci, který se zobrazí v **vlastnosti** okna a hodnotu vlastnosti jiné než řetězec.  
  
-   <xref:System.ComponentModel.EditorAttribute>: Určuje vlastní editor použít ke změně vlastnosti.  
  
## <a name="compile-the-code"></a>Kompilace kódu  
 Tento příklad vyžaduje odkazy na následující sestavení:  
  
-   Microsoft.VisualStudio.SharePoint
-    
-   Microsoft.VisualStudio.Shell
-     
-   Microsoft.VisualStudio.Shell.Interop
-     
-   Microsoft.VisualStudio.Shell.Interop.8.0
-     
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-extension"></a>Nasazení rozšíření  
 Chcete-li nasadit rozšíření, vytvořte [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] extension (VSIX) balíčku pro sestavení a všechny další soubory, které chcete distribuovat s příponou. Další informace najdete v tématu [nasadit rozšíření pro nástroje služby SharePoint v sadě Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Viz také:
 [Rozšíření projektů SharePoint](../sharepoint/extending-sharepoint-projects.md)   
 [Postupy: vytváření rozšíření projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [Postupy: Přidání položky místní nabídky do projektů služby SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [Rozšíření systému projektu služby SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  
