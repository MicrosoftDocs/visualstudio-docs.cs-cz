---
title: 'Postupy: definování typu položky projektu SharePoint | Microsoft Docs'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ae709bf2d81e2b8b00dc984602c0426fdf272ebd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016855"
---
# <a name="how-to-define-a-sharepoint-project-item-type"></a>Postupy: definování typu položky projektu SharePoint
  Definujte typ položky projektu, pokud chcete vytvořit vlastní položku projektu služby SharePoint. Další informace naleznete v tématu [definování vlastních typů položek projektu služby SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md).

### <a name="to-define-a-project-item-type"></a>Definování typu položky projektu

1. Vytvořte projekt knihovny tříd.

2. Přidejte odkazy na následující sestavení:

    - Microsoft. VisualStudio. SharePoint

    - System. ComponentModel. složení

3. Vytvořte třídu, která implementuje <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> rozhraní.

4. Do třídy přidejte následující atributy:

    - <xref:System.ComponentModel.Composition.ExportAttribute>. Tento atribut umožňuje aplikaci Visual Studio vyhledat a načíst vaši <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> implementaci. Předejte <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> typ konstruktoru atributu.

    - <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. V definici typu položky projektu určuje tento atribut identifikátor řetězce pro novou položku projektu. Doporučujeme použít formát *název společnosti*. *název funkce* , který vám umožní zajistit, aby všechny položky projektu měly jedinečný název.

    - <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute>. Tento atribut určuje ikonu, která se zobrazí pro tuto položku projektu v **Průzkumník řešení**. Tento atribut je nepovinný. Pokud ho nepoužijete pro třídu, Visual Studio zobrazí výchozí ikonu pro položku projektu. Pokud tento atribut nastavíte, předejte plně kvalifikovaný název ikony nebo rastrového obrázku, který je vložen do sestavení.

5. V implementaci <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metody použijte členy parametru *ProjectItemTypeDefinition* k definování chování typu položky projektu. Tento parametr je <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> objekt, který poskytuje přístup k událostem definovaným v <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents> rozhraních a. Chcete-li získat přístup ke konkrétní instanci typu položky projektu, zpracujte <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> události jako <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> a <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized> .

## <a name="example"></a>Příklad
 Následující příklad kódu ukazuje, jak definovat jednoduchý typ položky projektu. Tento typ položky projektu zapíše zprávu do okna **výstup** a **Seznam chyb** okno, když uživatel přidá položku projektu tohoto typu do projektu.

 [!code-vb[SPExtensibility.ProjectSystemExtension.General#2](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/projectitemtype.vb#2)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#2](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/projectitemtype.cs#2)]

 V tomto příkladu se používá služba projektu SharePoint k zápisu zprávy do okna **výstupu** a v **Seznam chyb** okně. Další informace naleznete v tématu [použití služby projektu služby SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

## <a name="compile-the-code"></a>Kompilovat kód
 Tento příklad vyžaduje odkazy na následující sestavení:

- Microsoft. VisualStudio. SharePoint

- System. ComponentModel. složení

## <a name="deploy-the-project-item"></a>Nasazení položky projektu
 Chcete-li povolit jiným vývojářům používat položku projektu, vytvořte šablonu projektu nebo šablonu položky projektu. Další informace naleznete v tématu [Vytvoření šablon položek a šablon projektů pro položky projektu služby SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 Chcete-li nasadit položku projektu, vytvořte [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] balíček rozšíření (VSIX) pro sestavení, šablonu a všechny další soubory, které chcete distribuovat s položkou projektu. Další informace naleznete v tématu [nasazení rozšíření pro nástroje služby SharePoint v aplikaci Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Viz také
- [Definování vlastních typů položek projektu služby SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Vytváření šablon položek a šablon projektů pro položky projektu služby SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Návod: Vytvoření vlastní položky projektu akce pomocí šablony položky, část 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Návod: vytvoření položky projektu sloupce webu pomocí šablony projektu, část 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [Postupy: Přidání vlastnosti do vlastního typu položky projektu služby SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
- [Postupy: Přidání položky místní nabídky do vlastního typu položky projektu služby SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)
