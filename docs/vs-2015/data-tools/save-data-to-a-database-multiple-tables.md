---
title: Ukládání dat do databáze (více tabulek) | Dokumentace Microsoftu
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
- updating datasets, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], updating
ms.assetid: 7ebe03da-ce8c-4cbc-bac0-a2fde4ae4d07
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 986df2d58c9a8955c9de9b45edaa5276b2e68bfb
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50218400"
---
# <a name="save-data-to-a-database-multiple-tables"></a>Uložení dat do databáze (více tabulek)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Jedním z nejběžnějších scénářů při vývoji aplikace je zobrazení dat na formulář v nástrojích pro aplikace Windows, upravte údaje a odeslat aktualizovaná data zpět do databáze. Tento návod vytvoří formulář, který zobrazuje data ze dvou souvisejících tabulek a ukazuje, jak upravovat záznamy a změny uložit zpět do databáze. V tomto příkladu `Customers` a `Orders` tabulek z ukázkové databáze Northwind.  
  
 Data můžete uložit ve vaší aplikaci zpět do databáze pomocí volání `Update` metody třídy TableAdapter. Při přetažení tabulky z **zdroje dat** okna do formuláře, kód, který je potřeba k uložení dat se automaticky přidá. Žádné další tabulky, které jsou přidány k formuláři vyžadují ruční přidání tohoto kódu. Tento návod ukazuje, jak přidat kód pro uložení aktualizací z více než jedné tabulky.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které se zobrazí může lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici, kterou používáte. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Úlohy v tomto návodu zahrnují:  
  
-   Vytvoření nového **aplikace Windows** projektu.  
  
-   Vytvoření a konfigurace zdroje dat ve vaší aplikaci se [Průvodce konfigurací zdroje dat](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).  
  
-   Ovládací prvky položek v nastavení [okna zdroje dat](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992). Další informace najdete v tématu [nastavení ovládacího prvku, který má být vytvořen při přetažení z okna zdroje dat](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Vytváření ovládacích prvků vázaných na data přetažením položek z **zdroje dat** okna do formuláře.  
  
-   Úprava několik záznamů ve všech tabulkách v datové sadě.  
  
-   Úprava kódu pro odesílání aktualizovaná data v datové sadě zpět do databáze.  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat:  
  
-   Přístup k ukázkové databázi Northwind.  Další informace najdete v tématu [postupy: Instalace ukázkových databází](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="create-the-windows-application"></a>Vytvoření aplikace Windows  
 Prvním krokem je vytvoření **aplikace Windows**. Přiřazení názvu projektu během tohoto kroku je volitelné, ale. poskytneme mu název protože plánujeme při uložení později.  
  
#### <a name="to-create-the-new-windows-application-project"></a>Chcete-li vytvořit nový projekt aplikace Windows  
  
1.  Na **souboru** nabídky, vytvořte nový projekt.  
  
2.  Pojmenujte projekt `UpdateMultipleTablesWalkthrough`.  
  
3.  Vyberte **aplikace Windows**a pak vyberte **OK**. Další informace najdete v tématu [klientské aplikace](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     **UpdateMultipleTablesWalkthrough** projekt je vytvořen a přidán do **Průzkumníka řešení**.  
  
## <a name="create-the-data-source"></a>Vytvoření zdroje dat  
 Tento krok vytváří zdroj dat v databázi Northwind pomocí průvodce **Průvodce konfigurací zdroje dat**. Musíte mít přístup k ukázkové databázi Northwind k vytvoření připojení. Informace o nastavení ukázkové databáze Northwind naleznete v tématu [postupy: Instalace ukázkových databází](../data-tools/how-to-install-sample-databases.md).  
  
#### <a name="to-create-the-data-source"></a>Vytvoření zdroje dat  
  
1.  Na **Data** nabídce vyberte možnost**zobrazit zdroje dat**.  
  
2.  V **zdroje dat** okně**přidat nový zdroj dat** spustit **Průvodce konfigurací zdroje dat**.  
  
3.  Na **zvolte typ zdroje dat**obrazovky, vyberte **databáze**a pak vyberte **Další**.  
  
4.  Na **vyberte datové připojení**obrazovky proveďte následující:  
  
    -   Pokud je připojení dat k ukázkové databázi Northwind k dispozici v rozevíracím seznamu, vyberte je.  
  
         -nebo-  
  
    -   Vyberte **nové připojení** otevřít **přidat/změnit připojení** dialogové okno.  
  
5.  Pokud vaše databáze vyžaduje heslo, vyberte možnost zahrnutí důvěrných osobních údajů a pak vyberte **Další**.  
  
6.  Na **uložit připojovací řetězec do konfiguračního souboru aplikace**vyberte **Další**.  
  
7.  Na **zvolte vaše databázové objekty**obrazovky, rozbalte **tabulky** uzlu.  
  
8.  Vyberte **zákazníkům** a **objednávky** tabulky a pak vyberte **Dokončit**.  
  
     **NorthwindDataSet** se přidá do vašeho projektu a tabulky se zobrazí v **zdroje dat** okna.  
  
## <a name="set-the-controls-to-be-created"></a>Můžete nastavit řízení, který se má vytvořit  
 V tomto návodu, data v `Customers` tabulka se **podrobnosti** rozložení, ve kterém se zobrazí data v jednotlivých ovládacích prvků. Data z `Orders` tabulka se **mřížky** rozložení, které se zobrazí v <xref:System.Windows.Forms.DataGridView> ovládacího prvku.  
  
#### <a name="to-set-the-drop-type-for-the-items-in-the-data-sources-window"></a>Chcete-li nastavit typ přetažení pro položky v okně zdrojů dat.  
  
1.  V **zdroje dat** okna, rozbalte **zákazníkům** uzlu.  
  
2.  Na **zákazníkům** uzlu, vyberte **podrobnosti** ovládací prvek seznamu můžete změnit kontrolu **zákazníkům** tabulky do jednotlivých ovládacích prvků. Další informace najdete v tématu [nastavení ovládacího prvku, který má být vytvořen při přetažení z okna zdroje dat](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
## <a name="create-the-data-bound-form"></a>Vytvoření formuláře vázané na data  
 Můžete vytvořit ovládací prvky vázané na data přetažením položek z **zdroje dat** okna do formuláře.  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>Vytvoření ovládacích prvků vázaných na data ve formuláři  
  
1.  Přetáhněte hlavní **zákazníkům** uzlu z **zdroje dat** okna do **Form1**.  
  
     Ovládací prvky vázaných dat pomocí popisků se zobrazí ve formuláři, spolu s pruh nástrojů (<xref:System.Windows.Forms.BindingNavigator>) pro procházení záznamů. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, a <xref:System.Windows.Forms.BindingNavigator> zobrazují v panelu komponent.  
  
2.  Přetáhněte související **objednávky** uzlu z **zdroje dat** okna do **Form1**.  
  
    > [!NOTE]
    >  Související **objednávky** uzel se nachází pod **Fax** sloupce a je podřízený uzel **zákazníkům** uzlu.  
  
     A <xref:System.Windows.Forms.DataGridView> ovládacího prvku a pruh nástrojů (<xref:System.Windows.Forms.BindingNavigator>) pro procházení záznamů se zobrazí ve formuláři. [OrdersTableAdapter](../data-tools/tableadapter-overview.md) a <xref:System.Windows.Forms.BindingSource> zobrazují v panelu komponent.  
  
## <a name="addcode-to-update-the-database"></a>Addcode aktualizovat databázi  
 Databáze můžete aktualizovat pomocí volání `Update` metody **zákazníkům** a **objednávky** objekty TableAdapter. Ve výchozím nastavení, obslužná rutina události **Uložit** tlačítko<xref:System.Windows.Forms.BindingNavigator> je přidán do formuláře kód k odeslání aktualizací do databáze. Tento postup upravuje kód k odesílání aktualizací ve správném pořadí. Tím se eliminuje možnost vyvolání chyby referenční integrity. Kód také implementuje obalením volání update v bloku try-catch – zpracování chyb. Můžete upravit kód tak, aby odpovídaly potřebám vaší aplikace.  
  
> [!NOTE]
>  Tento návod pro přehlednost nepoužívá transakce. Pokud chcete aktualizovat dvě nebo více souvisejících tabulek, ale obsahovat veškerou logiku aktualizací v rámci transakce. Transakce je proces, který zaručuje, že všechny související změny do databáze úspěšní, než se změny potvrdí. Další informace najdete v tématu [transakce a souběžnost](http://msdn.microsoft.com/library/f46570de-9e50-4fe6-8710-a8c31fa8569b).  
  
#### <a name="to-add-update-logic-to-the-application"></a>Chcete-li přidat logiku aktualizací do aplikace  
  
1.  Vyberte **Uložit** tlačítko <xref:System.Windows.Forms.BindingNavigator>. Otevře se Editor kódu `bindingNavigatorSaveItem_Click` obslužné rutiny události.  
  
2.  Nahraďte kód v obslužné rutině události pro volání `Update` metody související objekty TableAdapter. Následující kód nejprve vytvoří tři tabulky dočasných dat pro uložení aktualizované informace pro každý <xref:System.Data.DataRowState> (<xref:System.Data.DataRowState>, <xref:System.Data.DataRowState>, a <xref:System.Data.DataRowState>). Aktualizace jsou pak spusťte ve správném pořadí. Kód by měl vypadat nějak takto:  
  
     [!code-csharp[VbRaddataSaving#10](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form4.cs#10)]
     [!code-vb[VbRaddataSaving#10](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form4.vb#10)]  
  
## <a name="test-the-application"></a>Testování aplikace  
  
#### <a name="to-test-the-application"></a>Testování aplikace  
  
1.  Vyberte **F5**.  
  
2.  Některé změny dat z jednoho nebo více záznamů v každé tabulce.  
  
3.  Vyberte **Uložit** tlačítko.  
  
4.  Zkontrolujte hodnoty v databázi a ověřte, že se změny uložily.  
  
## <a name="next-steps"></a>Další kroky  
 V závislosti na požadavcích aplikace existuje několik kroků, které můžete chtít provést po vytvoření formuláře vázané na data v aplikaci Windows. Mezi vylepšení, která je možné pro tento návod provést, patří:  
  
-   Přidání vyhledávací funkce do formuláře. Další informace najdete v tématu [postupy: Přidání aplikace modelu Windows Forms s parametry dotazu](http://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416).  
  
-   Úprava zdroje dat s přidáváním a odebíráním databázové objekty. Další informace najdete v tématu [postupy: upravování datové sady](http://msdn.microsoft.com/library/f2dade5f-9c7a-4ddb-96a8-e0a39e50bfd3).  
  
## <a name="see-also"></a>Viz také  
 [Ukládání dat zpět do databáze](../data-tools/save-data-back-to-the-database.md)

