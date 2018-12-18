---
title: Ukládání dat do rozšíření systému projektu služby SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
helpviewer_keywords:
- SharePoint project items, saving string data
- project items [SharePoint development in Visual Studio], saving string data
- projects [SharePoint development in Visual Studio], saving string data
- SharePoint projects, saving string data
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 74228b5259b733c91397eb1b40a2485daea8b79e
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120201"
---
# <a name="save-data-in-extensions-of-the-sharepoint-project-system"></a>Uložení dat v rozšíření systému projektu služby SharePoint
  Při rozšíření systému projektu služby SharePoint, řetězec data, která je uchována po zavření projektu služby SharePoint můžete uložit. Data jsou obvykle související s položkou konkrétní projekt nebo pomocí samotného projektu.  
  
 Pokud máte data, která není potřeba zachovat, můžete přidat data do všech objektů v modelu objektu nástroje služby SharePoint, který implementuje <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> rozhraní. Další informace najdete v tématu [rozšíření nástrojů přidružení vlastních dat se službou SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
## <a name="save-data-that-is-associated-with-a-project-item"></a>Uložení dat, který je přidružen položka projektu
 Pokud máte data, která souvisí s konkrétní položka projektu služby SharePoint, jako je například hodnotu vlastnosti, která přidáte do položka projektu, můžete uložit data, která mají *.spdata* soubor pro položku projektu. Chcete-li to provést, použijte <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> vlastnost <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> objektu. Data, která přidáte do této vlastnosti se ukládají na **ExtensionData –** element v *.spdata* soubor pro položku projektu. Další informace najdete v tématu [ExtensionData – Element](../sharepoint/extensiondata-element.md).  
  
 Následující příklad kódu ukazuje, jak používat <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> vlastnost uložte hodnotu vlastnosti řetězce, který je definován v vlastního typu položky projektu služby SharePoint. Tady je příklad v rámci většího příkladu najdete v sekci [postupy: Přidání vlastnosti do vlastního typu položky projektu služby SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#14)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#14)]  
  
## <a name="save-data-that-is-associated-with-a-project"></a>Uložení dat, který je přidružený k projektu
 Pokud máte data na úrovni projektu, například hodnotu vlastnosti, která přidáte do projektů služby SharePoint, můžete data uložit do souboru projektu ( *.csproj* souboru nebo *.vbproj* soubor) nebo možnost uživatelů projektu soubor ( *. csproj.user* souboru nebo *. vbproj.user* souboru). Soubor, který můžete uložit data v závisí na způsob dat, který se má použít:  
  
-   Pokud chcete data, která mají být k dispozici pro všechny vývojáře, kteří otevření projektu služby SharePoint, uložte data do souboru projektu. Tento soubor je vždy zaškrtnuto k databázím zdroj ovládacího prvku, takže data v tomto souboru je k dispozici pro ostatní vývojáři, kteří podívejte se na projektu.  
  
-   Pokud chcete data, která mají být k dispozici pouze pro aktuální vývojář, který má projektu služby SharePoint, otevřete v sadě Visual Studio, uložte data do souboru projektu uživatele možnost. Tento soubor není zaregistrováno obvykle k databázím zdroj ovládacího prvku, tak data v tomto souboru nejsou k dispozici pro ostatní vývojáři, kteří podívejte se na projektu.  
  
### <a name="save-data-to-the-project-file"></a>Uložení dat do souboru projektu
 Chcete-li uložit data do souboru projektu, převeďte <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> do objektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> objektu a pak použít <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> metoda. Následující příklad kódu ukazuje, jak pomocí této metody můžete uložit do souboru projektu hodnotu vlastnosti projektu. Tady je příklad v kontextu větší ukázky najdete v sekci [postupy: Přidání vlastnosti do projektů služby SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  
  
 [!code-vb[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#3)]
 [!code-csharp[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#3)]  
  
 Další informace o převodu <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> najdete v části objekty na jiné typy v sadě Visual Studio automatizace objektový model nebo objektový model integrace [převod mezi systémovými typy projektů SharePoint a jinými typy projektů Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).  
  
### <a name="save-data-to-the-project-user-option-file"></a>Uložení dat do souboru projektu uživatele možnost
 Chcete-li uložit data do projektu uživatele možnost soubor, použijte <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> vlastnost <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> objektu. Následující příklad kódu ukazuje, jak pomocí této vlastnosti můžete uložit hodnotu vlastnosti projektu do souboru projektu uživatele možnost. Tady je příklad v kontextu větší ukázky najdete v sekci [postupy: Přidání vlastnosti do projektů služby SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  
  
 [!code-vb[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#2)]
 [!code-csharp[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#2)]  
  
## <a name="see-also"></a>Viz také:
 [Rozšíření systému projektu služby SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Přidružení vlastních dat k rozšíření nástrojů SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)   
 [Převod mezi systémovými typy projektů SharePoint a jinými typy projektů Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)  
  
