---
title: 'Postupy: Přidání vlastnosti do rozšíření položky projektu služby SharePoint | Microsoft Docs'
titleSuffix: ''
description: Použijte rozšíření položky projektu SharePoint pro přidání vlastnosti do jakékoli položky SharePointového projektu, která je již nainstalována v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3d721c8d4f381e99a814852839de0e808d326b3a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889639"
---
# <a name="how-to-add-a-property-to-a-sharepoint-project-item-extension"></a>Postupy: Přidání vlastnosti do rozšíření položky projektu služby SharePoint
  K přidání vlastnosti do libovolné položky SharePointového projektu, která je již nainstalována v aplikaci Visual Studio, lze použít rozšíření položky projektu. Vlastnost se zobrazí v okně **vlastnosti** , když je vybrána položka projektu v **Průzkumník řešení**.

 Následující postup předpokládá, že jste již vytvořili rozšíření položky projektu. Další informace naleznete v tématu [Postupy: Vytvoření rozšíření položky projektu služby SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

### <a name="to-add-a-property-to-a-project-item-extension"></a>Přidání vlastnosti do rozšíření položky projektu

1. Definujte třídu s veřejnou vlastností, která představuje vlastnost, kterou přidáváte do typu položky projektu. Chcete-li přidat více vlastností k typu položky projektu, můžete definovat všechny vlastnosti ve stejné třídě nebo v různých třídách.

2. V <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> metodě vaší <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> implementace zpracujte <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> událost parametru *projectItemType* .

3. V obslužné rutině události pro <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> událost přidejte instanci třídy Properties do <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> kolekce parametrů argumenty události.

## <a name="example"></a>Příklad
 Následující příklad kódu ukazuje, jak přidat vlastnost s názvem **Příklad vlastnosti** do položky projektu přijímače událostí.

 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemextensionproperty.cs#8)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemextensionproperty.vb#8)]

### <a name="understand-the-code"></a>Vysvětlení kódu
 Chcete-li zajistit, aby se stejná instance `CustomProperties` třídy použila při každém <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> výskytu události, příklad kódu přidá objekt Properties do <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> vlastnosti položky projektu, když dojde k první události. Kód načte tento objekt vždy, když dojde k této události znovu. Další informace o použití <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> Vlastnosti k přidružení dat k položkám projektu naleznete v tématu [přidružte vlastní data k rozšířením nástrojů služby SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

 Chcete-li zachovat změny v hodnotě vlastnosti, přístupový objekt **set** pro `ExampleProperty` uloží novou hodnotu do <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> vlastnosti <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> objektu, ke kterému je přidružena vlastnost. Další informace o použití <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> vlastnosti pro uchovávání dat s položkami projektu naleznete v tématu [ukládání dat v rozšířeních systému projektu služby SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

### <a name="specify-the-behavior-of-custom-properties"></a>Určení chování vlastních vlastností
 Můžete definovat způsob zobrazení a chování vlastní vlastnosti v okně **vlastnosti** použitím atributů z <xref:System.ComponentModel> oboru názvů do definice vlastnosti. Následující atributy jsou užitečné v mnoha scénářích:

- <xref:System.ComponentModel.DisplayNameAttribute>: Určuje název vlastnosti, která se zobrazí v okně **vlastnosti** .

- <xref:System.ComponentModel.DescriptionAttribute>: Určuje řetězec popisu, který se zobrazí v dolní části okna **vlastnosti** , když je vybrána vlastnost.

- <xref:System.ComponentModel.DefaultValueAttribute>: Určuje výchozí hodnotu vlastnosti.

- <xref:System.ComponentModel.TypeConverterAttribute>: Určuje vlastní převod mezi řetězcem, který je zobrazen v okně **vlastnosti** , a hodnotou neřetězcové vlastnosti.

- <xref:System.ComponentModel.EditorAttribute>: Určuje vlastní editor, který se použije pro úpravu vlastnosti.

## <a name="compile-the-code"></a>Kompilovat kód
 Tyto příklady vyžadují projekt knihovny tříd s odkazy na následující sestavení:

- Microsoft. VisualStudio. SharePoint

- System. ComponentModel. složení

## <a name="deploy-the-extension"></a>Nasazení rozšíření
 Chcete-li nasadit rozšíření, vytvořte [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] balíček rozšíření (VSIX) pro sestavení a všechny další soubory, které chcete distribuovat s rozšířením. Další informace naleznete v tématu [nasazení rozšíření pro nástroje služby SharePoint v aplikaci Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Viz také
- [Postupy: Vytvoření rozšíření položky projektu služby SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)
- [Postupy: Přidání položky místní nabídky do rozšíření položky projektu služby SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)
- [Rozšiřování položek projektu služby SharePoint](../sharepoint/extending-sharepoint-project-items.md)
- [Návod: rozšiřování typu položky projektu služby SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
