---
title: Vytváření sloupců webu, typů obsahu a seznamů pro službu SharePoint | Microsoft Docs
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.ListDesigner.ContentTypeSetting
- VS.SharePointTools.ContentTypeDesigner.CommonPropertiesPage
- VS.SharePointTools.ListDesigner.CreatingLists
- VS.SharePointTools.ListDesigner.ListPage
- VS.SharePointTools.ListDesigner.ViewPage
- VS.SharePointTools.ListDesigner.CommonPropertiesPage
- VS.SharePointTools.ContentTypeDesigner.ColumnsPage
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 269be4aaf34e9b6c611a5d79ba38cddba04276bf
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585103"
---
# <a name="create-site-columns-content-types-and-lists-for-sharepoint"></a>Vytváření sloupců webu, typů obsahu a seznamů pro službu SharePoint
  Visual Studio poskytuje šablony položek projektu pro mnoho různých základních položek SharePointu, včetně *seznamů* a *typů obsahu*, které mohou zahrnovat sloupce (nebo *pole*) webu. Noví návrháři pro typy obsahu a seznamy vytvářejí tyto položky snadněji než kdy dřív.

## <a name="site-columns"></a>Sloupce webu
 Sloupce webu jsou jedním z nejvíce základních prvků, které lze přidat do projektu služby SharePoint. Sloupec webu představuje typ dat, jako je telefonní číslo, komentář nebo jméno města kontaktu v seznamu kontaktů.

 Šablona položky projektu sloupce nového webu usnadňuje vytváření sloupců webu, než je v dřívější verzi sady Visual Studio. Po vytvoření nového sloupce webu můžete upravit kód XML v souboru *Elements.xml* sloupce webu tak, aby obsahoval požadované informace, jako je jeho zobrazované jméno, datový typ a skupina, ve které chcete sloupec web zobrazit ve službě SharePoint. Další informace o sloupcích webu najdete v tématu [Úvod do sloupců](/previous-versions/office/developer/sharepoint-2010/ms450825(v=office.14)).

## <a name="content-types-and-lists"></a>Typy obsahu a seznamy
 Typy obsahu a seznamy jsou mezi nejčastěji používanými prvky na SharePointu.

 Typ obsahu definuje metadata, pracovní postup a chování pro kategorii položek v SharePointovém seznamu nebo v knihovně dokumentů. Můžete například vytvořit typ obsahu pro informace v seznamu kontaktů nebo v seznamu úkolů. Typ obsahu kontaktu může zahrnovat sloupce, jako je jméno, E-mail, telefonní číslo a adresa. Typ obsahu, který definujete na úrovni webu, je nezávislý na jakémkoli seznamu nebo knihovně dokumentů v lokalitě. Můžete použít stejný typ obsahu s různými seznamy nebo knihovnami dokumentů na webu služby SharePoint. Ve stejném seznamu nebo knihovně dokumentů můžete také použít několik typů obsahu.

 Seznam je kolekce informací na SharePointu, které můžete sdílet s ostatními. Seznamy se skládají z řádků sloupců, které obsahují data. Mezi příklady seznamů patří: seznam úkolů, seznam kontaktů a seznam oznámení.

 Nový typ obsahu a návrháři seznamů v nástroji [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] vytvářejí typy obsahu webu a seznam jsou mnohem jednodušší a intuitivnější než v dřívější verzi sady Visual Studio. Uživatelské rozhraní umožňuje vizuálně sestavovat typy a seznamy obsahu a umožňuje seřazení a seskupování dat v seznamech a používání hlaviček skupin. Další informace o typech obsahu najdete v tématu [typy obsahu](/previous-versions/office/developer/sharepoint-2010/ms479905(v=office.14)). Další informace o seznamech naleznete v tématu [formuláře seznamu](/previous-versions/office/developer/sharepoint-2010/aa543232(v=office.14)) a [zobrazení seznamu](/previous-versions/office/developer/sharepoint-2010/ff604021(v=office.14)).

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Návod: vytvoření sloupce webu, typu obsahu a seznamu pro službu SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)|Ukazuje, jak vytvořit sloupce webu, které se používají ve vlastním typu obsahu. Typ obsahu se pak použije ve vlastním seznamu.|

## <a name="see-also"></a>Viz také
- [Začínáme s vývojem na SharePointu 2010](/sharepoint/dev/)
