---
title: Vytváření přidružení mezi entitami | Microsoft Docs
description: Vytvořte přidružení mezi entitami v modelu služby připojení obchodních dat (BDC). Seznamte se s metodami přidružení a typy přidružení.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.Association_Dialog
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d40c4e5c5d61b9da3cdbdd3fe96f45c4a0cff929
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2021
ms.locfileid: "106213963"
---
# <a name="create-an-association-between-entities"></a>Vytvoření přidružení mezi entitami
  Vytvořením přidružení můžete definovat vztahy mezi entitami v modelu služby připojení obchodních dat. Visual Studio generuje metody, které poskytují uživatelům modelu informace o jednotlivých přidruženích. Tyto metody mohou být využívány webovými částmi, seznamy nebo vlastními aplikacemi služby SharePoint pro zobrazení relací dat v uživatelském rozhraní (UI).

## <a name="create-an-association"></a>Vytvořit přidružení
 Vytvořte přidružení výběrem ovládacího prvku **přidružení** v sadě **nástrojů sady** Visual Studio, zvolením první entity (označované jako zdrojová entita) a následným zvolením druhé entity (označované jako Cílová entita). Podrobnosti o přidružení můžete definovat v **editoru přidružení**. Další informace najdete v tématu [Postupy: vytvoření přidružení mezi entitami](../sharepoint/how-to-create-an-association-between-entities.md).

## <a name="association-methods"></a>Metody asociace
 Aplikace, jako jsou webové části obchodní data služby SharePoint, využívají přidružení voláním metod ve třídě služby entity. Můžete přidat metody do třídy služby entity tím, že je vyberete v **editoru přidružení**.

 Ve výchozím nastavení přidá **Editor přidružení** metodu navigace přidružení ke zdrojové a cílové entitě. Navigační metoda přidružení ve zdrojové entitě umožňuje uživatelům načíst seznam cílových entit. Navigační metoda přidružení v cílové entitě umožňuje příjemcům načíst zdrojovou entitu, která se vztahuje k cílové entitě.

 Chcete-li vracet příslušné informace, je nutné přidat kód ke každé z těchto metod. Můžete také přidat další typy metod pro podporu pokročilejších scénářů. Další informace o jednotlivých metodách najdete v tématu [podporované operace](/previous-versions/office/developer/sharepoint-2010/ee557363(v=office.14)).

## <a name="types-of-associations"></a>Typy přidružení
 V Návrháři služby BDC můžete vytvořit dva typy přidružení: přidružení založená na cizím klíči a cizí bez klíčů přidružení.

### <a name="foreign-key-based-association"></a>Přidružení na základě cizího klíče
 Můžete vytvořit přidružení založené na cizím klíči s identifikátorem ve zdrojové entitě pro typy popisovačů definovaných v cílové entitě. Tento vztah umožňuje uživatelům modelu poskytovat vylepšené uživatelské rozhraní pro své uživatele. Například formulář v aplikaci Outlook, který uživateli umožňuje vytvořit prodejní objednávku, která může zobrazit zákazníky v rozevíracím seznamu. nebo seznam prodejních objednávek ve službě SharePoint, který umožňuje uživatelům otevřít stránku profilu pro zákazníka.

 Chcete-li vytvořit přidružení založené na cizím klíči, přiřaďte identifikátory a deskriptory typů, které sdílejí stejný název a typ. Můžete například vytvořit přidružení založené na cizím klíči mezi `Contact` entitou a `SalesOrder` entitou. `SalesOrder`Entita vrátí `ContactID` popisovač typu jako součást návratového parametru vyhledávacích metod nebo specifických vyhledávacích metod. Popisovače typu se zobrazí v **editoru přidružení**. Chcete-li vytvořit relaci založenou na cizím klíči mezi `Contact` entitou a `SalesOrder` entitou, vyberte `ContactID` identifikátor vedle každého z těchto polí.

 Přidejte kód do metody navigátoru přidružení zdrojové entity, která vrací kolekci cílových entit. Následující příklad vrátí prodejní objednávky kontaktu.

 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs" id="Snippet7":::
 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb" id="Snippet7":::

 Přidejte kód do metody navigátoru přidružení cílové entity, která vrací zdrojovou entitu. Následující příklad vrátí kontakt, který se vztahuje k prodejní objednávce.

 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs" id="Snippet8":::
 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb" id="Snippet8":::

### <a name="foreign-keyless-association"></a>Přidružení cizího bez klíčů
 Můžete vytvořit přidružení bez mapování identifikátorů k deskriptorům typu pole. Tento druh přidružení vytvořte v případě, že zdrojová entita nemá přímý vztah s cílovou entitou. Tabulka například nemá `SalesOrderDetail` cizí klíč, který se mapuje na primární klíč v `Contact` tabulce.

 Pokud chcete zobrazit informace v `SalesOrderDetail` tabulce, která souvisí s `Contact` , můžete vytvořit zahraniční přidružení bez klíčů mezi `Contact` entitou a `SalesOrderDetail` entitou.

 V metodě navigace přidružení `Contact` entity vraťte `SalesOrderDetail` entity připojením tabulek nebo voláním uložené procedury.

 Následující příklad vrátí podrobnosti o všech prodejních objednávkách spojováním tabulek.

 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs" id="Snippet9":::
 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb" id="Snippet9":::

 V metodě navigace přidružení `SalesOrderDetail` entity vraťte související `Contact` . Následující příklad ukazuje to.
                                                                            
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs" id="Snippet10":::
 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb" id="Snippet10":::

## <a name="see-also"></a>Viz také
- [Návrh modelu připojení obchodních dat](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Postupy: vytvoření přidružení mezi entitami](../sharepoint/how-to-create-an-association-between-entities.md)
