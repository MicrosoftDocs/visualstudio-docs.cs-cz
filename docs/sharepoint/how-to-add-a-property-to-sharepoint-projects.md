---
title: 'Postupy: Přidání vlastnosti do projektů služby SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: eb72b0546b504e2df1a7e93ea9d4def350143d1d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "86015919"
---
# <a name="how-to-add-a-property-to-sharepoint-projects"></a>Postupy: Přidání vlastnosti do projektů služby SharePoint
  K přidání vlastnosti do libovolného projektu služby SharePoint lze použít rozšíření projektu. Vlastnost se zobrazí v okně **vlastnosti** , když je projekt vybrán v **Průzkumník řešení**.

 Následující postup předpokládá, že jste již vytvořili rozšíření projektu. Další informace naleznete v tématu [Postupy: Vytvoření rozšíření projektu služby SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

### <a name="to-add-a-property-to-a-sharepoint-project"></a>Přidání vlastnosti do projektu služby SharePoint

1. Definujte třídu s veřejnou vlastností, která představuje vlastnost, kterou přidáváte do projektů služby SharePoint. Pokud chcete přidat více vlastností, můžete definovat všechny vlastnosti ve stejné třídě nebo v různých třídách.

2. V <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> metodě vaší <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> implementace zpracujte <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> událost parametru *ProjectService* .

3. V obslužné rutině události pro <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> událost přidejte instanci třídy Properties do <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectPropertiesRequestedEventArgs.PropertySources%2A> kolekce parametrů argumenty události.

## <a name="example"></a>Příklad
 Následující příklad kódu ukazuje, jak přidat dvě vlastnosti do projektů služby SharePoint. Jedna vlastnost uchovává svá data v souboru možností uživatele projektu (soubor *. csproj. User* nebo *. vbproj. User* ). Druhá vlastnost uchovává svá data v souboru projektu (soubor *. csproj* nebo *. vbproj* ).

 [!code-vb[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#1)]
 [!code-csharp[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#1)]

### <a name="understand-the-code"></a>Vysvětlení kódu
 Chcete-li zajistit, aby se stejná instance `CustomProjectProperties` třídy použila při každém <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> výskytu události, příklad kódu přidá objekt Properties do <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> Vlastnosti projektu, když dojde k první události. Kód načte tento objekt vždy, když dojde k této události znovu. Další informace o použití <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> Vlastnosti k přidružení dat k projektům naleznete v tématu [přidružte vlastní data k rozšířením nástrojů služby SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

 Chcete-li zachovat změny v hodnotách vlastností, přístupové objekty **set** pro vlastnosti používají následující rozhraní API:

- `CustomUserFileProperty` používá <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> vlastnost k uložení své hodnoty do souboru možností uživatele projektu.

- `CustomProjectFileProperty` používá <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> metodu k uložení své hodnoty do souboru projektu.

  Další informace o zachování dat v těchto souborech naleznete v tématu [uložení dat v rozšíření systému projektu služby SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

### <a name="specify-the-behavior-of-custom-properties"></a>Určení chování vlastních vlastností
 Můžete definovat způsob zobrazení a chování vlastní vlastnosti v okně **vlastnosti** použitím atributů z <xref:System.ComponentModel> oboru názvů do definice vlastnosti. Následující atributy jsou užitečné v mnoha scénářích:

- <xref:System.ComponentModel.DisplayNameAttribute>: Určuje název vlastnosti, která se zobrazí v okně **vlastnosti** .

- <xref:System.ComponentModel.DescriptionAttribute>: Určuje řetězec popisu, který se zobrazí v dolní části okna **vlastnosti** , když je vybrána vlastnost.

- <xref:System.ComponentModel.DefaultValueAttribute>: Určuje výchozí hodnotu vlastnosti.

- <xref:System.ComponentModel.TypeConverterAttribute>: Určuje vlastní převod mezi řetězcem, který je zobrazen v okně **vlastnosti** , a hodnotou neřetězcové vlastnosti.

- <xref:System.ComponentModel.EditorAttribute>: Určuje vlastní editor, který se použije pro úpravu vlastnosti.

## <a name="compile-the-code"></a>Kompilovat kód
 Tento příklad vyžaduje odkazy na následující sestavení:

- Microsoft. VisualStudio. SharePoint

- Microsoft. VisualStudio. Shell

- Microsoft. VisualStudio. Shell. Interop

- Microsoft. VisualStudio. Shell. Interop. 8.0

- System. ComponentModel. složení

## <a name="deploy-the-extension"></a>Nasazení rozšíření
 Chcete-li nasadit rozšíření, vytvořte [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] balíček rozšíření (VSIX) pro sestavení a všechny další soubory, které chcete distribuovat s rozšířením. Další informace naleznete v tématu [nasazení rozšíření pro nástroje služby SharePoint v aplikaci Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Viz také
- [Rozšiřování projektů SharePoint](../sharepoint/extending-sharepoint-projects.md)
- [Postupy: Vytvoření rozšíření projektu služby SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)
- [Postupy: Přidání položky místní nabídky do projektů služby SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)
- [Rozšíří systém projektu služby SharePoint.](../sharepoint/extending-the-sharepoint-project-system.md)
