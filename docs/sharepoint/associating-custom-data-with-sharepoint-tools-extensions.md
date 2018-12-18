---
title: Rozšíření nástrojů SharePoint přidružení vlastních dat | Dokumentace společnosti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3e174440411e54d0f3960035874bd3b84b392c57
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49939488"
---
# <a name="associate-custom-data-with-sharepoint-tools-extensions"></a>Přidružení vlastních dat k rozšíření nástrojů SharePoint
  Přidat vlastní data k určitým objektům v rozšíření nástrojů služby SharePoint. To je užitečné, když máte data v jedné části rozšíření, které chcete později získat přístup z jiného kódu v rozšíření. Namísto provádění vlastní způsob ukládání a přístup k datům, můžete přidružit data s objektem v rozšíření a pak později znovu načíst data ze stejného objektu.  
  
 Přidání vlastních dat do objektů je také užitečné, pokud chcete zachovat data, která je relevantní pro konkrétní položku v sadě Visual Studio. Rozšíření nástrojů služby SharePoint jsou načteny pouze jednou v sadě Visual Studio, tak rozšíření může pracovat několik různých položek (jako jsou projekty, položky, projektu nebo **Průzkumníka serveru** uzlů) v každém okamžiku. Pokud máte vlastní data, která je relevantní pouze pro určitou položku, můžete přidat data do objektu, který představuje tuto položku.  
  
 Při přidání vlastních dat do objektů v rozšíření nástrojů SharePoint data zachována. Data jsou k dispozici pouze během životnosti objektu. Jakmile je objekt uvolněn systémem uvolňování paměti, data budou ztracena.  
  
 Do rozšíření systému projektu služby SharePoint můžete také uložit data řetězce, který bude zachován po rozšíření je uvolněna. Další informace najdete v tématu [uložení dat do rozšíření systému projektu služby SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
## <a name="objects-that-can-contain-custom-data"></a>Objekty, které mohou obsahovat vlastní data
 Můžete přidat vlastní data do libovolného objektu v objektovém modelu serveru SharePoint nástroje, který implementuje <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> rozhraní. Toto rozhraní definuje pouze jednu vlastnost <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>, což je kolekce vlastních datových objektů. Následující typy implementovat <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject>:  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IMappedFolder>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IMenuItem>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectMember>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentContext>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition>  
  
## <a name="add-and-retrieve-custom-data"></a>Přidání a jejich načtení vlastních dat
 Přidání vlastních dat do objektu v rozšíření nástrojů služby SharePoint, získáte <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> vlastnost objektu, který má k přidání dat do a následné použití <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.Add%2A> způsob, jak přidat data do objektu.  
  
 Pokud chcete načíst vlastní data z objektu v rozšíření nástrojů služby SharePoint, získejte <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> vlastnosti objektu a pak použijte jednu z následujících metod:  
  
- <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.TryGetValue%2A>. Tato metoda vrátí **true** Pokud datový objekt existuje, nebo **false** Pokud neexistuje. Tuto metodu můžete použít k načtení instance hodnotové typy nebo typy odkazů.  
  
- <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.GetValue%2A>. Tato metoda vrací data objektu, pokud se neukončí, nebo **null** Pokud neexistuje. Tato metoda slouží pouze k načtení instance odkazových typů.  
  
  Následující příklad kódu určuje, zda určitá data objektu je již přidružena k položce projektu. Pokud datový objekt už není přidružená k položce projektu a pak kód přidá objekt, který má <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> vlastnosti položky projektu. Tento příklad v rámci většího příkladu najdete v tématu [postupy: Přidání vlastnosti do vlastního typu položky projektu SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).  
  
  [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#13)]
  [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#13)]  
  
## <a name="see-also"></a>Viz také:
 [Programování konceptů a funkcí pro rozšíření nástrojů SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)   
 [Návod: Vytvoření vlastní položky projektu akce pomocí šablony položky, část 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Návod: Rozšíření Průzkumníka serveru pro zobrazení částí webu](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Postupy: Přidání vlastnosti do projektů služby SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Postupy: Přidání vlastnosti do vlastního typu položky projektu SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
   
 
