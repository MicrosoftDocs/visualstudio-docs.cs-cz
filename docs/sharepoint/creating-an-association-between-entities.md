---
title: Vytvoření přidružení mezi entitami | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 22ac00ac48f4fe907e4fb4215992b49227f39961
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/22/2018
ms.locfileid: "36325460"
---
# <a name="create-an-association-between-entities"></a>Vytvoření přidružení mezi entitami
  Je možné definovat vztahy mezi entity v modelu Business Data Connectivity (BDC) tak, že vytvoříte přidružení. Visual Studio generuje metody, které poskytují informace o každé přidružení příjemci modelu. Tyto metody mohou být spotřebovávána webových částí služby SharePoint, seznamy nebo vlastních aplikací zobrazíte relace mezi daty v uživatelském rozhraní (UI).  
  
## <a name="create-an-association"></a>Vytvoření přidružení
 Vytvoření přidružení výběrem **přidružení** ovládací prvek v sadě Visual Studio **sada nástrojů**, zvolit první entity (označovaný jako zdrojové entitě) a pak vyberete druhý entity (volat cílové entity). Můžete definovat podrobnosti o přidružení v **přidružení Editor**. Další informace najdete v tématu [postupy: vytvoření přidružení mezi entitami](../sharepoint/how-to-create-an-association-between-entities.md).  
  
## <a name="association-methods"></a>Přidružení metody
 Aplikace jako webové části služby SharePoint firemní data využívat přidružení při volání metody ve třídě služby entity. Můžete přidat metody k třídě služby entity tak, že je vyberete **přidružení Editor**.  
  
 Ve výchozím nastavení **přidružení Editor** přidá metodu přidružení navigace na zdrojové a cílové entity. Metodu přidružení navigace ve zdrojové entitě umožňuje příjemci k načtení seznamu cílové entity. Metodu přidružení navigace v cílové entitě umožňuje příjemci k načtení zdrojové entity, která má vztah k cílové entity.  
  
 Je nutné přidat kód pro každé z těchto metod vrátit příslušné informace. Můžete také přidat další typy metod pro podporu pokročilejší scénáře. Další informace o každém z těchto metod najdete v tématu [podporované operace](http://go.microsoft.com/fwlink/?LinkId=169286).  
  
## <a name="types-of-associations"></a>Typy přidružení
 Můžete vytvořit dva typy přidružení v Návrháři BDC: cizí klíč na základě přidružení a přidružení cizího bez kódu.  
  
### <a name="foreign-key-based-association"></a>Přidružení cizího na základě klíčů
 Můžete vytvořit přidružení cizího klíče na základě vytvořením souvislosti identifikátor ve zdrojové entitě na typ popisovače definované v cílové entitě. Tento vztah umožňuje příjemci ve model zajistit lepší uživatelského rozhraní pro své uživatele. Například formuláře v aplikaci Outlook, která umožňuje uživateli vytvořit prodejní objednávky, která můžete zobrazit zákazníků v rozevíracím seznamu; nebo seznam prodeje objednávek ve službě SharePoint, která umožní uživatelům otevřete stránku profilu pro zákazníka.  
  
 Chcete-li vytvořit přidružení cizího na základě klíčů, se týkají identifikátory a zadejte popisovače, které sdílejí stejný název a typ. Můžete například vytvořit cizí klíč na základě přidružení mezi `Contact` entity a `SalesOrder` entity. `SalesOrder` Vrátí entity `ContactID` deskriptor typů v rámci návratový parametr vyhledávací nebo specifická metoda Finder metod. Obě popisovače typu se zobrazí v **přidružení Editor**. K vytvoření relace cizího klíče na základě mezi `Contact` entity a `SalesOrder` entity, vyberte `ContactID` identifikátor vedle každého z těchto polí.  
  
 Přidejte kód k metodě přidružení Navigátor zdrojové entity, která vrátí kolekci entit cílový. Následující příklad vrátí prodeje objednávek kontaktu.  
  
 [!code-csharp[SP_BDC#7](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#7)]
 [!code-vb[SP_BDC#7](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#7)]  
  
 Přidejte kód metodu přidružení Navigátor cílové entity, která vrátí zdrojové entity. Následující příklad vrátí kontakt vztahující se k řádku.  
  
 [!code-csharp[SP_BDC#8](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs#8)]
 [!code-vb[SP_BDC#8](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb#8)]  
  
### <a name="foreign-keyless-association"></a>Přidružení cizího bez kódu
 Přidružení můžete vytvořit bez mapování identifikátorů na pole Typ popisovače. Tento druh přidružení vytvořte, pokud zdrojové entitě nemá přímou relaci s entitou, na cílový. Například `SalesOrderDetail` tabulka neobsahuje cizí klíč, který se mapuje na primární klíč v `Contact` tabulky.  
  
 Pokud chcete zobrazit informace v `SalesOrderDetail` tabulku, která má vztah k `Contact`, můžete vytvořit cizí bez kódu přidružení mezi `Contact` entity a `SalesOrderDetail` entity.  
  
 V metodě přidružení navigace `Contact` entity, návratový `SalesOrderDetail` entity spojování tabulek, nebo volání uložené procedury.  
  
 Následující příklad vrátí podrobnosti o všech prodeje objednávek podle spojování tabulek.  
  
 [!code-csharp[SP_BDC#9](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#9)]
 [!code-vb[SP_BDC#9](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#9)]  
  
 V metodě přidružení navigace `SalesOrderDetail` entity, vrátí související `Contact`. Následující příklad ukazuje to.  
  
 [!code-csharp[SP_BDC#10](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs#10)]
 [!code-vb[SP_BDC#10](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb#10)]  
  
## <a name="see-also"></a>Viz také:
 [Navrhování modelu připojení obchodních dat](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Postupy: vytvoření přidružení mezi entitami](../sharepoint/how-to-create-an-association-between-entities.md)  
  
 
