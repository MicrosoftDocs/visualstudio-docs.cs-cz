---
title: 'Postupy: vytvoření přidružení mezi entitami | Microsoft Docs'
description: Definování vztahů mezi entitami v modelu služby připojení obchodních dat (BDC) vytvořením přidružení v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- AssociationGroupTool
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associations between entities
- BDC [SharePoint development in Visual Studio], associations between entities
- Business Data Connectivity service [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associate external content types
- Business Data Connectivity service [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], associate external content types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e736e0befe8aaf9a6c090615d0c43bb3f3116dbf
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/18/2020
ms.locfileid: "94849841"
---
# <a name="how-to-create-an-association-between-entities"></a>Postupy: vytvoření přidružení mezi entitami
  Vytvořením přidružení můžete definovat vztahy mezi entitami v modelu služby připojení obchodních dat. Visual Studio generuje metody, které poskytují uživatelům modelu informace o jednotlivých přidruženích. Tyto metody mohou být využívány webovými částmi, seznamy nebo vlastními aplikacemi služby SharePoint pro zobrazení relací dat v uživatelském rozhraní (UI).

 V Návrháři služby BDC můžete vytvořit dva typy přidružení: přidružení založená na cizím klíči a cizí bez klíčů přidružení. Další informace najdete v tématu [vytvoření přidružení mezi entitami](../sharepoint/creating-an-association-between-entities.md).

### <a name="to-create-an-association-between-entities"></a>Vytvoření přidružení mezi entitami

1. Na kartě **BusinessDataConnectivity** sady **nástrojů** vyberte položku **přidružení** .

2. V Návrháři BDC Zvolte zdrojovou entitu a pak zvolte cílovou entitu.

     Zobrazí se **Editor přidružení** .

3. Pokud chcete vytvořit přidružení založené na cizím klíči, zaškrtněte políčko **je přidružení cizího klíče** .

    1. Ve sloupci **ID zdroje** v tabulce **mapování identifikátorů** vyberte identifikátor vedle každého odpovídajícího popisovače typu, který se zobrazí ve sloupci **pole** .

         Například ve sloupci **ID zdroje** vyberte možnost `ContactID` vedle `ReadList.salesOrderList.SalesOrderList.SalesOrder.ContactID` deskriptoru typu a `ReadItem.salesOrder.SalesOrder.ContactID` popisovače typu.

4. Pokud chcete vytvořit přidružení cizího bez klíčů, zrušte zaškrtnutí políčka **je přidružení cizího klíče** .

5. Klikněte na tlačítko **OK** .

6. V Návrháři BDC se zobrazí čára, která představuje přidružení mezi zdrojovou entitou a cílovou entitou.

     Visual Studio přidá metodu navigátoru asociace do třídy služby cílové entity a třídy služby zdrojové entity. Další informace o metodách navigace v přidružení najdete v tématu [podporované operace](/previous-versions/office/developer/sharepoint-2010/ee557363(v=office.14)).

7. V metodě navigátor přidružení zdrojové entity přidejte kód, který vrátí kolekci cílových entit.

8. V metodě navigátoru přidružení cílové entity přidejte kód, který vrátí související zdrojovou entitu.

     Příklady metod navigátoru přidružení najdete v tématu [vytvoření přidružení mezi entitami](../sharepoint/creating-an-association-between-entities.md).

## <a name="see-also"></a>Viz také
- [Vytvoření přidružení mezi entitami](../sharepoint/creating-an-association-between-entities.md)
- [Návrh modelu připojení obchodních dat](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Postupy: Přidání vyhledávací metody](../sharepoint/how-to-add-a-finder-method.md)
- [Postupy: Přidání konkrétní vyhledávací metody](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Postupy: Přidání metody autora](../sharepoint/how-to-add-a-creator-method.md)
- [Postupy: Přidání metody odstranění](../sharepoint/how-to-add-a-deleter-method.md)
- [Postupy: Přidání aktualizační metody](../sharepoint/how-to-add-an-updater-method.md)
- [Přehled nástrojů pro návrh modelu služby BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Postupy: Přidání parametru do metody](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Postupy: definování instance metody](../sharepoint/how-to-define-a-method-instance.md)
- [Postupy: definování deskriptoru typu pro parametr](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [Návod: Vytvoření externího seznamu ve službě SharePoint s použitím obchodních dat](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)
