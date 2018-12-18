---
title: Ukládání dat pomocí TableAdapter dbdirect – metody | Dokumentace Microsoftu
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
- TableAdapters, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], TableAdapter
ms.assetid: 74a6773b-37e1-4d96-a39c-63ee0abf49b1
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6b7a7ec1d244f8bf711f0d1aaf4726c910846357
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219715"
---
# <a name="save-data-with-the-tableadapter-dbdirect-methods"></a>Ukládání dat pomocí metod TableAdapter DBDirect
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Tento názorný postup obsahuje podrobné pokyny ke spouštění příkazů SQL přímo proti databázi s použitím dbdirect – metody třídy TableAdapter. Dbdirect – metody třídy TableAdapter poskytovat jemné úroveň kontroly nad aktualizace databáze. Můžete je použít ke spuštění konkrétních příkazů jazyka SQL a uložených procedur voláním jednotlivých `Insert`, `Update`, a `Delete` metody podle potřeb vaší aplikace (na rozdíl od přetížené `Update` metodu, která provádí aktualizace Příkazů INSERT a DELETE vše v jednom volání).  
  
 V tomto návodu se dozvíte, jak:  
  
-   Vytvořte nový **aplikace Windows**.  
  
-   Vytvoření a konfigurace datové sady [Průvodce konfigurací zdroje dat](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).  
  
-   Vyberte ovládací prvek, který má být vytvořen ve formuláři při přetažení položek z **zdroje dat** okna. Další informace najdete v tématu [nastavení ovládacího prvku, který má být vytvořen při přetažení z okna zdroje dat](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Vytvoření formuláře vázané na data přetažením položek z **zdroje dat** okna do formuláře.  
  
-   Přidejte metody k přímému přístupu k databázi a provést vložení, aktualizace a odstranění...  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat:  
  
-   Přístup k ukázkové databázi Northwind. Další informace najdete v tématu [postupy: Instalace ukázkových databází](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="create-a-windows-application"></a>Vytvoření aplikace Windows  
 Prvním krokem je vytvoření **aplikace Windows**.  
  
#### <a name="to-create-the-new-windows-project"></a>Vytvoření nového projektu Windows  
  
1.  V sadě Visual Studio na **souboru** nabídky, vytvořte nový **projektu**.  
  
2.  Pojmenujte projekt **TableAdapterDbDirectMethodsWalkthrough**.  
  
3.  Vyberte **aplikace Windows**a pak vyberte **OK**. Další informace najdete v tématu [klientské aplikace](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     **TableAdapterDbDirectMethodsWalkthrough** projekt je vytvořen a přidán do **Průzkumníka řešení**.  
  
## <a name="create-a-data-source-from-your-database"></a>Vytvoření zdroje dat z databáze  
 Tento krok používá **Průvodce konfigurací zdroje dat** vytvořit zdroj dat na základě `Region` tabulky v ukázkové databázi Northwind. Musíte mít přístup k ukázkové databázi Northwind k vytvoření připojení. Informace o nastavení ukázkové databáze Northwind naleznete v tématu [postupy: Instalace ukázkových databází](../data-tools/how-to-install-sample-databases.md).  
  
#### <a name="to-create-the-data-source"></a>Vytvoření zdroje dat  
  
1.  Na **Data** nabídce vyberte možnost **zobrazit zdroje dat**.  
  
2.  V **zdroje dat** okně **přidat nový zdroj dat** spustit **Průvodce konfigurací zdroje dat**.  
  
3.  Na **zvolte typ zdroje dat** obrazovky, vyberte **databáze**a pak vyberte **Další**.  
  
4.  Na **vyberte datové připojení** obrazovky, proveďte jednu z následujících akcí:  
  
    -   Pokud je připojení dat k ukázkové databázi Northwind k dispozici v rozevíracím seznamu, vyberte je.  
  
         -nebo-  
  
    -   Vyberte **nové připojení** ke spuštění **přidat/změnit připojení** dialogové okno.  
  
5.  Pokud vaše databáze vyžaduje heslo, vyberte možnost zahrnutí důvěrných osobních údajů a pak vyberte **Další**.  
  
6.  Na **uložit připojovací řetězec do konfiguračního souboru aplikace** obrazovky, vyberte **Další**.  
  
7.  Na **zvolte vaše databázové objekty** obrazovky, rozbalte **tabulky** uzlu.  
  
8.  Vyberte `Region` tabulku a pak vyberte **Dokončit**.  
  
     **NorthwindDataSet** se přidá do vašeho projektu a `Region` se zobrazí v tabulce **zdroje dat** okna.  
  
## <a name="addcontrols-to-the-form-to-display-the-data"></a>Addcontrols do formuláře pro zobrazení dat  
 Vytvoření ovládacích prvků vázaných na data přetažením položek z **zdroje dat** okna do formuláře.  
  
#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Vytvoření dat vázané ovládací prvky na formuláři Windows  
  
-   Přetáhněte hlavní **oblasti** uzlu z **zdroje dat** okna do formuláře.  
  
     A <xref:System.Windows.Forms.DataGridView> ovládacího prvku a pruh nástrojů (<xref:System.Windows.Forms.BindingNavigator>) pro procházení záznamů se zobrazí ve formuláři. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [RegionTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, a <xref:System.Windows.Forms.BindingNavigator> zobrazují v panelu komponent.  
  
#### <a name="to-add-buttons-that-will-call-the-individual-tableadapter-dbdirect-methods"></a>Přidat tlačítka, který bude volat jednotlivé třídy TableAdapter dbdirect – metody  
  
1.  Přetáhněte tři <xref:System.Windows.Forms.Button> ovládacích prvků z **nástrojů** do **Form1** (dole **RegionDataGridView**).  
  
2.  Nastavte následující **název** a **Text** vlastnosti na každé tlačítko.  
  
    |Název|Text|  
    |----------|----------|  
    |`InsertButton`|**Vložit**|  
    |`UpdateButton`|**Aktualizace**|  
    |`DeleteButton`|**Delete**|  
  
#### <a name="to-add-code-to-insert-new-records-into-the-database"></a>Přidat kód pro vkládání nových záznamů do databáze  
  
1.  Vyberte **InsertButton** vytvořit obslužnou rutinu události pro událost click a otevřete formulář v editoru kódu.  
  
2.  Nahradit `InsertButton_Click` obslužné rutiny události s následujícím kódem:  
  
     [!code-csharp[VbRaddataSaving#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs#1)]
     [!code-vb[VbRaddataSaving#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb#1)]  
  
#### <a name="to-add-code-to-update-records-in-the-database"></a>Chcete-li přidat kód k aktualizaci záznamů v databázi  
  
1.  Dvakrát klikněte **UpdateButton** vytvořit obslužnou rutinu události pro událost click a otevřete formulář v editoru kódu.  
  
2.  Nahradit `UpdateButton_Click` obslužné rutiny události s následujícím kódem:  
  
     [!code-csharp[VbRaddataSaving#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs#2)]
     [!code-vb[VbRaddataSaving#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb#2)]  
  
#### <a name="to-add-code-to-delete-records-from-the-database"></a>Chcete-li přidat kód k odstranění záznamů z databáze  
  
1.  Vyberte **DeleteButton** vytvořit obslužnou rutinu události pro událost click a otevřete formulář v editoru kódu.  
  
2.  Nahradit `DeleteButton_Click` obslužné rutiny události s následujícím kódem:  
  
     [!code-csharp[VbRaddataSaving#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs#3)]
     [!code-vb[VbRaddataSaving#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb#3)]  
  
## <a name="run-the-application"></a>Spuštění aplikace  
  
#### <a name="to-run-the-application"></a>Ke spuštění aplikace  
  
-   Vyberte **F5** ke spuštění aplikace.  
  
-   Vyberte **vložit** tlačítko a ověřte, že nový záznam se zobrazí v mřížce.  
  
-   Vyberte **aktualizace** tlačítko a ověřte, že záznam se aktualizuje v mřížce.  
  
-   Vyberte **odstranit** tlačítko a ověřte, že záznam se odebere z mřížky.  
  
## <a name="next-steps"></a>Další kroky  
 V závislosti na požadavcích aplikace existuje několik kroků, které můžete chtít provést po vytvoření formuláře vázané na data. Mezi vylepšení, která je možné pro tento návod provést, patří:  
  
-   Přidání vyhledávací funkce do formuláře. Další informace najdete v tématu [postupy: Přidání aplikace modelu Windows Forms s parametry dotazu](http://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416).  
  
-   Přidání další tabulky do datové sady výběrem **konfigurace datové sady pomocí průvodce** v rámci **zdroje dat** okna. Můžete přidat ovládací prvky zobrazující související data přetažením související uzly na formuláři. Další informace najdete v tématu [postupy: zobrazení souvisejících dat ve formulářové aplikaci Windows](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md).  
  
## <a name="see-also"></a>Viz také  
 [Ukládání dat zpět do databáze](../data-tools/save-data-back-to-the-database.md)

