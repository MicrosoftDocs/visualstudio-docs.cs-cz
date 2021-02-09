---
title: Přidat vlastnost do vlastního typu položky projektu služby SharePoint
description: Přidejte vlastnost do vlastního typu položky projektu služby SharePoint. Vlastnost se zobrazí v okno Vlastnosti při výběru položky projektu v Průzkumník řešení.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b8f690b15f843af9337e16ee803509b72e85d7af
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889665"
---
# <a name="how-to-add-a-property-to-a-custom-sharepoint-project-item-type"></a>Postupy: Přidání vlastnosti do vlastního typu položky projektu služby SharePoint
  Při definování vlastního typu položky projektu služby SharePoint můžete přidat vlastnost do položky projektu. Vlastnost se zobrazí v okně **vlastnosti** , když je vybrána položka projektu v **Průzkumník řešení**.

 Následující postup předpokládá, že jste již definovali vlastní typ položky projektu služby SharePoint. Další informace naleznete v tématu [How to: define a Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

### <a name="to-add-a-property-to-a-definition-of-a-project-item-type"></a>Přidání vlastnosti do definice typu položky projektu

1. Definujte třídu s veřejnou vlastností, která představuje vlastnost, kterou přidáváte do vlastního typu položky projektu. Chcete-li přidat více vlastností do vlastního typu položky projektu, můžete definovat všechny vlastnosti ve stejné třídě nebo v různých třídách.

2. V <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metodě vaší <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> implementace zpracujte <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> událost parametru *ProjectItemTypeDefinition* .

3. V obslužné rutině události pro <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> událost přidejte instanci třídy Custom Properties do <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> kolekce parametrů argumenty události.

## <a name="example"></a>Příklad
 Následující příklad kódu ukazuje, jak přidat vlastnost s názvem **Příklad vlastnosti** do vlastního typu položky projektu.

 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#11](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#11)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#11](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#11)]

### <a name="understand-the-code"></a>Vysvětlení kódu
 Chcete-li zajistit, aby se stejná instance `CustomProperties` třídy použila při každém <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> výskytu události, příklad kódu uloží objekt Properties do <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> vlastnosti položky projektu, když dojde k první události. Kód načte tento objekt vždy, když dojde k této události znovu. Další informace o použití <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> vlastnosti pro uložení dat s položkami projektu naleznete v tématu [přidružte vlastní data k rozšířením nástrojů služby SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

 Chcete-li zachovat změny v hodnotě vlastnosti, přístupový objekt **set** pro `ExampleProperty` uloží novou hodnotu do <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> vlastnosti <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> objektu, ke kterému je přidružena vlastnost. Další informace o použití <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> vlastnosti pro uchovávání dat s položkami projektu naleznete v tématu [ukládání dat v rozšířeních systému projektu služby SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

### <a name="specify-the-behavior-of-custom-properties"></a>Určení chování vlastních vlastností
 Můžete definovat způsob zobrazení a chování vlastní vlastnosti v okně **vlastnosti** použitím atributů z <xref:System.ComponentModel> oboru názvů do definice vlastnosti. Následující atributy jsou užitečné v mnoha scénářích:

- <xref:System.ComponentModel.DisplayNameAttribute>: Určuje název vlastnosti, která se zobrazí v okně **vlastnosti** .

- <xref:System.ComponentModel.DescriptionAttribute>: Určuje řetězec popisu, který se zobrazí v dolní části okna **vlastnosti** , když je vybrána vlastnost.

- <xref:System.ComponentModel.DefaultValueAttribute>: Určuje výchozí hodnotu vlastnosti.

- <xref:System.ComponentModel.TypeConverterAttribute>: Určuje vlastní převod mezi řetězcem, který je zobrazen v okně **vlastnosti** , a hodnotou neřetězcové vlastnosti.

- <xref:System.ComponentModel.EditorAttribute>: Určuje vlastní editor, který se použije pro úpravu vlastnosti.

## <a name="compile-the-code"></a>Kompilovat kód
 Tyto příklady kódu vyžadují projekt knihovny tříd s odkazy na následující sestavení:

- Microsoft. VisualStudio. SharePoint

- System. ComponentModel. složení

## <a name="deploy-the-project-item"></a>Nasazení položky projektu
 Chcete-li povolit jiným vývojářům používat položku projektu, vytvořte šablonu projektu nebo šablonu položky projektu. Další informace naleznete v tématu [Vytvoření šablon položek a šablon projektů pro položky projektu služby SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 Chcete-li nasadit položku projektu, vytvořte [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] balíček rozšíření (VSIX) pro sestavení, šablonu a všechny další soubory, které chcete distribuovat s položkou projektu. Další informace naleznete v tématu [nasazení rozšíření pro nástroje služby SharePoint v aplikaci Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Viz také
- [Postupy: definování typu položky projektu SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)
- [Postupy: Přidání položky místní nabídky do vlastního typu položky projektu služby SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)
- [Definování vlastních typů položek projektu služby SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)
