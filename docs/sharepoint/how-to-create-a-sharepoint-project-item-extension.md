---
title: 'Postupy: Vytvoření rozšíření položky projektu služby SharePoint | Microsoft Docs'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 345bfa49da4bf5d5b73fe1d3f209675fe2814de2
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015346"
---
# <a name="how-to-create-a-sharepoint-project-item-extension"></a>Postupy: Vytvoření rozšíření položky projektu služby SharePoint
  Vytvořte rozšíření položky projektu, pokud chcete přidat funkce do položky projektu služby SharePoint, která je již nainstalována v aplikaci Visual Studio. Další informace najdete v tématu věnovaném [rozšiřování položek projektu služby SharePoint](../sharepoint/extending-sharepoint-project-items.md).

### <a name="to-create-a-project-item-extension"></a>Vytvoření rozšíření položky projektu

1. Vytvořte projekt knihovny tříd.

2. Přidejte odkazy na následující sestavení:

    - Microsoft. VisualStudio. SharePoint

    - System. ComponentModel. složení

3. Vytvořte třídu, která implementuje <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> rozhraní.

4. Do třídy přidejte následující atributy:

    - <xref:System.ComponentModel.Composition.ExportAttribute>. Tento atribut umožňuje aplikaci Visual Studio vyhledat a načíst vaši <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> implementaci. Předejte <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> typ konstruktoru atributu.

    - <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. V rozšíření položky projektu tento atribut identifikuje položku projektu, kterou chcete rozšířit. Předejte ID položky projektu konstruktoru atributu. Seznam identifikátorů položek projektu, které jsou součástí sady Visual Studio, naleznete v části [extend SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md).

5. V implementaci <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> metody použijte členy parametru *projectItemType* k definování chování rozšíření. Tento parametr je <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> objekt, který poskytuje přístup k událostem definovaným v <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents> rozhraních a. Chcete-li získat přístup ke konkrétní instanci typu položky projektu, který rozšiřujete, zpracujte <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> události jako <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> a <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized> .

## <a name="example"></a>Příklad
 Následující příklad kódu ukazuje, jak vytvořit jednoduché rozšíření pro položku projektu přijímače událostí. Pokaždé, když uživatel přidá položku projektu příjemce události do projektu služby SharePoint, zapíše toto rozšíření zprávu do okna **výstup** a **Seznam chyb** okno.

 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#1](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/projectitemextension.cs#1)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#1](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/projectitemextension.vb#1)]

 V tomto příkladu se používá služba projektu SharePoint k zápisu zprávy do okna **výstupu** a v **Seznam chyb** okně. Další informace naleznete v tématu [použití služby projektu služby SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

## <a name="compile-the-code"></a>Kompilovat kód
 Tento příklad vyžaduje odkazy na následující sestavení:

- Microsoft. VisualStudio. SharePoint

- System. ComponentModel. složení

## <a name="deploy-the-extension"></a>Nasazení rozšíření
 Chcete-li nasadit rozšíření, vytvořte [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] balíček rozšíření (VSIX) pro sestavení a všechny další soubory, které chcete distribuovat s rozšířením. Další informace naleznete v tématu [nasazení rozšíření pro nástroje služby SharePoint v aplikaci Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Viz také:
- [Rozšiřování položek projektu služby SharePoint](../sharepoint/extending-sharepoint-project-items.md)
- [Návod: rozšiřování typu položky projektu služby SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
