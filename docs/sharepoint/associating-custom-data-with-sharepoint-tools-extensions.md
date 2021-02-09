---
title: Přidružení vlastních dat k rozšíření nástrojů služby SharePoint | Microsoft Docs
description: Přidružte vlastní data k rozšířením nástrojů služby SharePoint. Podívejte se na seznam objektů, které mohou obsahovat vlastní data. Přidejte a načtěte vlastní data.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], associating custom data
- project items [SharePoint development in Visual Studio], associating custom data
- SharePoint project items, associating custom data
- SharePoint projects, associating custom data
- SharePoint development in Visual Studio, extensibility features
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1b4722f04ae46f85d7cc70dadf6127330e8f6616
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851711"
---
# <a name="associate-custom-data-with-sharepoint-tools-extensions"></a>Přidružit vlastní data k rozšířením nástrojů služby SharePoint
  Můžete přidat vlastní data do určitých objektů v rozšířeních nástrojů služby SharePoint. To je užitečné v případě, že máte data v jedné části rozšíření, ke kterým chcete získat přístup později z jiného kódu v rozšíření. Namísto implementace vlastního způsobu ukládání a přístupu k datům můžete přidružit data k objektu v rozšíření a následně načíst data ze stejného objektu později.

 Přidávání vlastních dat do objektů je také užitečné, pokud chcete zachovat data, která jsou relevantní pro konkrétní položku v aplikaci Visual Studio. Rozšíření nástrojů služby SharePoint jsou načtena pouze jednou v aplikaci Visual Studio, takže vaše rozšíření může kdykoli fungovat s několika různými položkami (například projekty, položky projektu nebo uzly **Průzkumník serveru** ). Máte-li vlastní data, která jsou relevantní pouze pro konkrétní položku, můžete přidat data do objektu, který tuto položku představuje.

 Když přidáte vlastní data do objektů v rozšířeních nástrojů služby SharePoint, data nebudou uchována. Data jsou k dispozici pouze během životnosti objektu. Po uvolnění objektu uvolňováním paměti dojde ke ztrátě dat.

 V rozšíření systému projektu služby SharePoint můžete také uložit řetězcová data, která se přetrvají po uvolnění rozšíření. Další informace naleznete v tématu [ukládání dat v rozšířeních systému projektu služby SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

## <a name="objects-that-can-contain-custom-data"></a>Objekty, které mohou obsahovat vlastní data
 Můžete přidat vlastní data do libovolného objektu v objektovém modelu nástrojů služby SharePoint, který implementuje <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> rozhraní. Toto rozhraní definuje pouze jednu vlastnost, <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> která je kolekcí vlastních datových objektů. Následující typy implementují <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> :

- <xref:Microsoft.VisualStudio.SharePoint.IMappedFolder>

- <xref:Microsoft.VisualStudio.SharePoint.IMenuItem>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectMember>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>

- <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentContext>

- <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode>

- <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType>

- <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition>

## <a name="add-and-retrieve-custom-data"></a>Přidat a načíst vlastní data
 Chcete-li přidat vlastní data do objektu v rozšíření nástrojů služby SharePoint, Získejte <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> vlastnost objektu, do které chcete přidat data, a poté použijte <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.Add%2A> metodu pro přidání dat do objektu.

 Chcete-li načíst vlastní data z objektu v rozšíření nástrojů služby SharePoint, Získejte <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> vlastnost objektu a pak použijte jednu z následujících metod:

- <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.TryGetValue%2A>. Tato metoda vrátí **hodnotu true** , pokud datový objekt existuje, nebo **false** , pokud neexistuje. Tuto metodu můžete použít k načtení instancí typů hodnot nebo odkazových typů.

- <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.GetValue%2A>. Tato metoda vrátí datový objekt, pokud je ukončen, nebo **hodnotu null** , pokud neexistuje. Tuto metodu lze použít pouze k načtení instancí typů odkazů.

  Následující příklad kódu určuje, zda je určitý datový objekt již přidružen k položce projektu. Pokud datový objekt již není přidružen k položce projektu, kód přidá objekt do <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> vlastnosti položky projektu. Chcete-li zobrazit tento příklad v kontextu většího příkladu, přečtěte si téma [Postup: Přidání vlastnosti do vlastního typu položky projektu služby SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).

  [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#13)]
  [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#13)]

## <a name="see-also"></a>Viz také
- [Programování konceptů a funkcí pro rozšíření nástrojů služby SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)
- [Návod: Vytvoření vlastní položky projektu akce pomocí šablony položky, část 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Návod: rozšíření Průzkumník serveru pro zobrazení webových částí](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [Postupy: Přidání vlastnosti do projektů služby SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
- [Postupy: Přidání vlastnosti do vlastního typu položky projektu služby SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
