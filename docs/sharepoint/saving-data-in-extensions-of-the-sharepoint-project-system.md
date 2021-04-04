---
title: Ukládání dat v rozšířeních systému projektu služby SharePoint | Microsoft Docs
titleSuffix: ''
description: Naučte se, jak uložit řetězcová data, která se přetrvají po ukončení projektu služby SharePoint, který obsahuje rozšíření.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
helpviewer_keywords:
- SharePoint project items, saving string data
- project items [SharePoint development in Visual Studio], saving string data
- projects [SharePoint development in Visual Studio], saving string data
- SharePoint projects, saving string data
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 87e05ba763095a818cc5db6f92828e6259d30e73
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217434"
---
# <a name="save-data-in-extensions-of-the-sharepoint-project-system"></a>Uložení dat v rozšířeních systému projektu služby SharePoint
  Když rozšíříte systém projektu služby SharePoint, můžete uložit řetězcová data, která se budou přetrvávat po zavření projektu služby SharePoint. Data jsou obvykle přidružena k určité položce projektu nebo samotnému projektu.

 Pokud máte data, která není nutné zachovat, můžete data přidat do libovolného objektu v objektovém modelu nástrojů služby SharePoint, který implementuje <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> rozhraní. Další informace najdete v tématu [přidružení vlastních dat k rozšířením nástrojů služby SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

## <a name="save-data-that-is-associated-with-a-project-item"></a>Uložit data přidružená k položce projektu
 Pokud máte data, která jsou spojena s konkrétní položkou projektu služby SharePoint, jako je například hodnota vlastnosti, kterou přidáte do položky projektu, můžete uložit data do souboru *. spdata* pro položku projektu. K tomu použijte <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> vlastnost <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> objektu. Data, která přidáte do této vlastnosti, jsou uložena v elementu **ExtensionData –** v souboru *. spdata* pro položku projektu. Další informace naleznete v tématu [ExtensionData – element](../sharepoint/extensiondata-element.md).

 Následující příklad kódu ukazuje, jak použít <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> vlastnost k uložení hodnoty řetězcové vlastnosti, která je definována ve vlastním typu položky projektu služby SharePoint. Chcete-li zobrazit tento příklad v kontextu většího příkladu, přečtěte si téma [Postup: Přidání vlastnosti do vlastního typu položky projektu služby SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb" id="Snippet14":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs" id="Snippet14":::

## <a name="save-data-that-is-associated-with-a-project"></a>Uložit data přidružená k projektu
 Pokud máte data na úrovni projektu, jako je hodnota vlastnosti, kterou přidáte do projektů služby SharePoint, můžete data uložit do souboru projektu (soubor *. csproj* nebo *. vbproj* ) nebo do souboru možností uživatele projektu (soubor *. csproj. User* nebo *. vbproj. User* ). Soubor, na který se rozhodnete ukládat data, závisí na tom, jak chcete data používat:

- Chcete-li, aby data byla k dispozici všem vývojářům, kteří otevřou projekt služby SharePoint, uložte data do souboru projektu. Tento soubor je vždy vrácen se změnami do databází správy zdrojových kódů, takže data v tomto souboru jsou k dispozici ostatním vývojářům, kteří si projekt vyhradí.

- Chcete-li, aby data byla k dispozici pouze pro aktuálního vývojáře, který má projekt služby SharePoint otevřen v aplikaci Visual Studio, uložte data do souboru možností uživatele projektu. Tento soubor není obvykle vrácen se změnami do databází správy zdrojových kódů, takže data v tomto souboru nejsou k dispozici ostatním vývojářům, kteří si projekt zarezervují.

### <a name="save-data-to-the-project-file"></a>Uložit data do souboru projektu
 Chcete-li uložit data do souboru projektu, převeďte <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> objekt na <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> objekt a pak použijte <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> metodu. Následující příklad kódu ukazuje, jak použít tuto metodu k uložení hodnoty vlastnosti projektu do souboru projektu. Chcete-li zobrazit tento příklad v kontextu většího vzorku, přečtěte si téma [Postup: Přidání vlastnosti do projektů služby SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb" id="Snippet3":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs" id="Snippet3":::

 Další informace o převodu <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> objektů na jiné typy v modelu automatizačních objektů sady Visual Studio nebo modelu integračních objektů naleznete v tématu [Převod mezi systémovými typy projektů SharePoint a jinými typy projektů aplikace Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).

### <a name="save-data-to-the-project-user-option-file"></a>Uložit data do souboru možností uživatele projektu
 Chcete-li uložit data do souboru možností uživatele projektu, použijte <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> vlastnost <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> objektu. Následující příklad kódu ukazuje, jak tuto vlastnost použít k uložení hodnoty vlastnosti projektu do souboru možností uživatele projektu. Chcete-li zobrazit tento příklad v kontextu většího vzorku, přečtěte si téma [Postup: Přidání vlastnosti do projektů služby SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb" id="Snippet2":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs" id="Snippet2":::

## <a name="see-also"></a>Viz také
- [Rozšíří systém projektu služby SharePoint.](../sharepoint/extending-the-sharepoint-project-system.md)
- [Přidružit vlastní data k rozšířením nástrojů služby SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)
- [Převod mezi systémovými typy projektů SharePoint a jinými typy projektů Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
