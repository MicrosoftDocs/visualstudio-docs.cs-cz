---
title: 'Postupy: připojení k datům v databázi | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- databases, connecting to
- data sources, databases
- data [Visual Studio], connecting to databases
- data sources, creating
- database connections
ms.assetid: 6c56e54e-8834-4297-85aa-cc1a443ba556
caps.latest.revision: 55
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: e75de3c81270449da6fe6bb504b476b912f51583
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49273803"
---
# <a name="how-to-connect-to-data-in-a-database"></a>Postupy: Připojování k datům v databázi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio můžete použít k připojení aplikace k databázi. Po vytvoření datového připojení, sada Visual Studio generuje datový model, který vaše aplikace používá k interakci s daty v databázi. Objekty v datovém modelu se zobrazí v [okna zdroje dat](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992). Potom můžete vytvořit ovládací prvky vázané na data přetažením položek z **okna zdroje dat** na návrhovou plochu. Další informace najdete v tématu [vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
 Toto téma obsahuje pokyny pro připojení k databázi a vytvoření následujících typů datových modelů:  
  
-   Datová sada  
  
-   Entity Data Model (EDM)  
  
> [!NOTE]
>  Visual Studio můžete také použít k vytvoření LINQ na třídy SQL z databáze. Však třídy LINQ to SQL nejsou uvedeny v **zdroje dat** okna a proto je nelze přetáhnout do návrháře k vytvoření ovládacích prvků vázaných na data. Další informace o vytvoření LINQ na třídy SQL z databáze najdete v tématu [postupy: vytvoření třídy LINQ to SQL namapovaných na tabulky a zobrazení (O/R Designer)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
##  <a name="dataset"></a> Připojení k databázi a vytvoření datové sady  
 Když vytvoříte datovou sadu, která je založena na databázi, Visual Studio vytvoří sadu tříd, které představují programovatelné zobrazení dat. Hlavní třída se nazývá *zadaná datová sada*. Zadaná datová sada obsahuje objekty tabulky dat, které představují tabulky v databázi. Další informace o definovaných datových sadách najdete v tématu [datovou sadu nástrojů v sadě Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).  
  
 Po vytvoření datové sady můžete vytvořit ovládací prvky WPF nebo Windows Forms vázané na data přetažením objektů datové sady z okna zdroje dat do Návrháře WPF nebo Windows Forms.  
  
#### <a name="to-connect-your-application-to-a-database-and-create-a-dataset"></a>Připojení aplikace k databázi a vytvoření datové sady  
  
1.  Otevřete existující projekt v sadě Visual Studio, nebo vytvořte nový projekt.  
  
2.  Na **Data** nabídky, klikněte na tlačítko **přidat nový zdroj dat**.  
  
     **Průvodce konfigurací zdroje dat** otevře.  
  
3.  Na **zvolte typ zdroje dat** stránce **databáze**a potom klikněte na tlačítko **Další**.  
  
4.  Na **vyberte databázový Model** stránce **datovou sadu**a potom klikněte na tlačítko **Další**.  
  
5.  Na **vyberte datové připojení** stránky, vyberte datové připojení ze seznamu dostupných připojení a pak klikněte na tlačítko **Další**.  
  
     Pokud požadované datové připojení není k dispozici, vytvořte nové připojení pomocí následujících kroků v [vytváření nového připojení k databázi](#CreatingDataConnection).  
  
6.  Na **uložit připojovací řetězec do souboru konfigurace aplikace** stránky, můžete volitelně vymazat **Ano, uložit připojení jako** zaškrtávací políčko, pokud chcete uložit připojovací řetězec přímo v zkompilovaný aplikace. Ve výchozím nastavení připojení se uloží v konfiguračním souboru aplikace. Další informace najdete v tématu [postupy: uložení a úpravy připojovacích řetězců](~/E:/Repos/visualstudio-docs-pr/docs/data-tools/how-to-save-and-edit-connection-strings.md).  
  
7.  Na **zvolte vaše databázové objekty** vyberte databázové objekty, které budete používat ve vaší aplikaci. Máte také možnost nahradit výchozí **název datové sady**.  
  
8.  Klikněte na tlačítko **Dokončit**. Právě vytvořená datová sada je nyní k dispozici v **zdroje dat** okna.  
  
    > [!NOTE]
    >  Pokud **zdroje dat** není otevřené okno, klikněte na tlačítko **zobrazit zdroje dat** na **Data** nabídce otevřete okno.  
  
9. Nyní můžete přetáhnout položky z **zdroje dat** okno do Návrháře WPF, návrháře Windows Forms nebo [návrháře komponent](http://msdn.microsoft.com/library/61a3a450-5b15-465e-bd9a-72a6c8c2b282) k vytvoření ovládacích prvků vázaných na data. Další informace najdete v tématu [vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
##  <a name="edm"></a> Připojení k databázi a vytvoření modelu Entity Data Model  
 Při vytváření datového modelu Entity, která je založena na databázi, Visual Studio vytvoří sadu tříd, které představují programovatelné zobrazení dat. Další informace o datových modelech Entity a ADO.NET Entity Framework naleznete v tématu [přehled Entity Framework](http://msdn.microsoft.com/library/a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0).  
  
 Po vytvoření modelu Entity Data Model můžete vytvořit ovládací prvky WPF vázané na data přetažením objektů entity z okna zdroje dat do Návrháře WPF.  
  
#### <a name="to-connect-your-application-to-a-database-and-create-an-entity-data-model"></a>Připojení aplikace k databázi a vytvoření modelu Entity Data Model  
  
1.  Otevřete existující projekt v sadě Visual Studio, nebo vytvořte nový projekt.  
  
2.  Postupujte podle pokynů **Průvodce datovým modelem Entity** pro připojení k databázi a určení obsahu modelu. Další informace najdete v tématu [postupy: vytvoření nové edmx soubor](http://msdn.microsoft.com/en-us/beb8189e-e51c-4051-839c-9902c224abf2).  
  
3.  Po dokončení **Průvodce datovým modelem Entity**, vytvoříte modelu Entity Data Model otevře v Návrháři Entity Data Model Designer a datové objekty, které jsou teď dostupné v **zdroje dat** okna.  
  
    > [!NOTE]
    >  Pokud **zdroje dat** není otevřené okno, klikněte na tlačítko **zobrazit zdroje dat** na **Data** nabídce otevřete okno.  
  
4.  Pokud je otevřený Návrhář WPF, nyní můžete přetáhnout položky z **zdroje dat** do okna návrháře k vytvoření ovládacích prvků, které jsou vázány na modelu Entity Data Model. Další informace najdete v tématu [ovládací prvky WPF vytvoření vazby k datům v sadě Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md).  
  
     Pokud Návrhář Windows Forms je otevřen, nelze přetáhnout položky **zdroje dat** do návrháře. Chcete-li vytvořit ovládací prvky, které jsou vázány na modelu Entity Data Model, musí se projekt sestavil, přidat nový zdroj dat objektu, který je založen na modelu Entity Data Model a potom tyto objekty přetáhnout do návrháře.  
  
##  <a name="CreatingDataConnection"></a> Vytváří se nové připojení databáze  
 Při použití **Průvodce konfigurací zdroje dat**nebo **Průvodce datovým modelem Entity**, je nutné zadat připojení k databázi, kterou chcete použít. Pokud již nemáte připojení k databázi, proveďte následující kroky k vytvoření připojení.  
  
 Tyto pokyny předpokládají, že jste už začali **Průvodce konfigurací zdroje dat** nebo **Průvodce datovým modelem Entity** jak je popsáno v [připojení k databázi a vytvoření datové sady ](#dataset) a [připojení k databázi a vytvoření modelu Entity Data Model](#edm).  
  
#### <a name="to-create-a-new-database-connection"></a>Chcete-li vytvořit nové připojení databáze  
  
1.  Na **vyberte datové připojení** stránku **Průvodce konfigurací zdroje dat** nebo **Průvodce datovým modelem Entity**, klikněte na tlačítko **novépřipojení**.  
  
     Dojde k jedné z následujících akcí:  
  
    -   Pokud jste již vytvořili datové připojení v sadě Visual Studio **přidat připojení** zobrazí se dialogové okno.  
  
    -   Pokud se jedná o první datové připojení, které jste vytvořili v sadě Visual Studio **zvolit zdroj dat** zobrazí dialogové okno. Vyberte typ, který chcete připojit a potom klikněte na databázi **OK** zobrazíte **přidat připojení** dialogové okno.  
  
2.  V **přidat připojení** dialogového okna zadejte požadované informace. **Přidat připojení** dialogové okno se liší pro každý typ dat zprostředkovatele.  
  
    > [!NOTE]
    >  Pokud vybraný **zdroj dat** v **přidat připojení** dialogové okno není zdrojem dat, kterou chcete připojit, klikněte na tlačítko **změnu** otevřít **Change Data Zdroj** dialogové okno a potom vyberte jiný zdroj dat.  
  
3.  V **přidat připojení** dialogové okno, klikněte na tlačítko **OK**.  
  
     Můžete vrátit **vyberte datové připojení** stránku **Průvodce konfigurací zdroje dat** nebo **Průvodce datovým modelem Entity**.  
  
4.  Na **vyberte datové připojení** stránky, zkontrolujte, že je vybrána nové datové připojení a pak klikněte na tlačítko **Další**.  
  
5.  Dokončení zbývajících kroků **Průvodce konfigurací zdroje dat** nebo **Průvodce datovým modelem Entity**.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Ukládání citlivých informací (například hesla) může ovlivnit zabezpečení aplikace. Bezpečnější způsob, jak řídit přístup k databázi, je ověřování systému Windows (označované také jako integrované zabezpečení). Další informace najdete v tématu [chrání informace o připojení](http://msdn.microsoft.com/library/1471f580-bcd4-4046-bdaf-d2541ecda2f4).  
  
## <a name="see-also"></a>Viz také  
 [Přidat nové zdroje dat](../data-tools/add-new-data-sources.md)   
 [Návody k datům](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Vytvoření vazby ovládacích prvků Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Připojování k datům v sadě Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Připojení ke zdroji dat](http://msdn.microsoft.com/library/9abc3f92-1be3-4e1a-b360-762dc689650e)