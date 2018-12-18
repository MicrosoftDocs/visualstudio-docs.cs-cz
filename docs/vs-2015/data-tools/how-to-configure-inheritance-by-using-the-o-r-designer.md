---
title: 'Postupy: Konfigurace dědičnosti pomocí návrháře O R | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e594af12-e777-434a-bc08-7dd2dac84cdc
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7a6c8e4b2da87185c41157b8d03bd59b37188a43
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49222687"
---
# <a name="how-to-configure-inheritance-by-using-the-or-designer"></a>Postupy: Konfigurace dědičnosti pomocí Návrháře relací objektů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
[!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]) Podporují koncept dědičnosti jedné tabulky, jak často je implementován v relačních systémech. V dědičnosti jedné tabulky je izolované databáze tabulku, která obsahuje pole pro informace o nadřazené i podřízené informace. Sloupec diskriminátoru s relačními daty, obsahuje hodnotu, která určuje, která třída libovolný záznam patří.  
  
 Představte si třeba osoby tabulku, která obsahuje všechny uživatele náhradník společnosti. Někteří lidé jsou zaměstnanci a někteří lidé jsou správci. Osoby tabulka obsahuje sloupec s názvem `EmployeeType` , který má hodnotu 1 pro manažery a hodnota 2 pro zaměstnance; to je sloupec diskriminátoru. V tomto scénáři můžete vytvořit podtřídu zaměstnanců a naplnit třída se pouze záznamy, které mají `EmployeeType` hodnotu 2. Můžete také odebrat sloupce, které se nevztahují z každé třídy.  
  
 Vytvoření objektu modelu, který používá dědičnosti (a odpovídá relační data) může být trochu matoucí. Následující postup popisuje kroky potřebné ke konfiguraci dědičnosti pomocí Návrháře relací objektů. Podle obecných kroků bez ohledu na existující tabulky a sloupce může být obtížné, proto poskytuje návod, který používá data. Podrobné pokyny krok za krokem konfigurace dědičnosti pomocí [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], naleznete v tématu [návod: vytvoření třídy LINQ to SQL děděním pomocí jedné tabulky (O/R Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md).  
  
### <a name="to-create-inherited-data-classes"></a>Chcete-li vytvořit zděděné datových tříd  
  
1.  Otevřít [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] tak, že přidáte **třídy LINQ to SQL** položky do existujícího projektu jazyka Visual Basic nebo C#.  
  
2.  Přetáhněte tabulku, kterou chcete použít jako základní třídy na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
3.  Přetáhněte kopii tabulky do druhé [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] a přejmenujte jej. Jedná se o odvozené třídy nebo podtřídy.  
  
4.  Klikněte na tlačítko **dědičnosti** v **Návrhář relací objektů** karty **nástrojů**a potom klikněte na podtřídu (tabulky, které jste přejmenovali) a připojte ho k základní třídy.  
  
    > [!NOTE]
    >  Klikněte na tlačítko **dědičnosti** položky v **nástrojů** a uvolněte tlačítko myši, klikněte na druhé kopie třídy, kterou jste vytvořili v kroku 3 a pak klikněte na první třídy, kterou jste vytvořili v kroku 2. První třídy bude odkazovat na šipku v linii dědičnosti.  
  
5.  V každé třídě odstraňte všechny vlastnosti objektu, které nechcete zobrazit a které nejsou používány pro přidružení. Dojde k chybě při pokusu odstranit objekt vlastnosti používané pro přidružení: [vlastnost \<název vlastnosti > nejde odstranit, protože se účastní asociace \<název přidružení >](../data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name.md).  
  
    > [!NOTE]
    >  Protože odvozené třídy dědí vlastnosti definované v její základní třídě, stejné sloupce se nedá definovat v každé třídě. (Sloupce jsou implementovány jako vlastnosti). Vytvoření sloupce v odvozené třídě můžete povolit tak, že nastavíte modifikátor dědičnosti na vlastnost v základní třídě. Další informace najdete v tématu [NOT IN sestavení: přepsání vlastností a metod](http://msdn.microsoft.com/en-us/2167e8f5-1225-4b13-9ebd-02591ba90213).  
  
6.  Vybrat čáru dědičnosti v [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
7.  V **vlastnosti** okno, nastaveno **vlastnost diskriminátoru** název sloupce, který se používá k rozlišení záznamy ve třídách.  
  
8.  Nastavte **hodnota diskriminátoru odvozené třídy** k hodnotě v databázi, která se označí jako zděděný typ záznamu. (Toto je hodnota, která je uložena v sloupec diskriminátoru, která slouží k určení zděděné třídy.)  
  
9. Nastavte **hodnota diskriminátoru základní třídy** vlastnost na hodnotu, která se označí jako základní typ záznamu. (Toto je hodnota, která je uložena v sloupec diskriminátoru, která slouží k určení základní třídy.)  
  
10. Volitelně můžete také nastavit **výchozí dědičnost** vlastnosti k určení typu v hierarchii dědičnosti, který se používá při načítání řádků, které neodpovídají žádné definované kód dědičnosti. Jinými slovy, pokud má záznam hodnotu v jeho sloupec diskriminátoru, která se neshoduje s hodnotu buď **hodnota diskriminátoru odvozené třídy** nebo **hodnota diskriminátoru základní třídy** vlastnosti, záznam načte typ určený jako **výchozí dědičnost**.  
  
## <a name="see-also"></a>Viz také  
 [Nástroje LINQ to SQL v sadě Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Návod: Vytvoření třídy LINQ to SQL (Návrhář O-R)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [Připravte si, co je nového pro vývoj aplikací Data v sadě Visual Studio 2012](http://msdn.microsoft.com/en-us/3d50d68f-5f44-4915-842f-6d42fce793f1)   
 [Přístup k datům v sadě Visual Studio](../data-tools/accessing-data-in-visual-studio.md)   
 [Technologie LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Návod: Vytvoření třídy LINQ to SQL s použitím dědičnosti jedné tabulky (O/R Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)   
 [NENÍ v sestavení: Dědičnost v jazyce Visual Basic](http://msdn.microsoft.com/en-us/e5e6e240-ed31-4657-820c-079b7c79313c)   
 [Dědičnost](http://msdn.microsoft.com/library/81d64ee4-50f9-4d6c-a8dc-257c348d2eea)

