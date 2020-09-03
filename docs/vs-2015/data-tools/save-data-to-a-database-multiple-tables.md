---
title: Uložení dat do databáze (více tabulek) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c5c4d5fc73660c97bcb69957a93d2ff08f64e31c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655465"
---
# <a name="save-data-to-a-database-multiple-tables"></a>Uložení dat do databáze (více tabulek)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jedním z nejběžnějších scénářů při vývoji aplikací je zobrazení dat ve formuláři aplikace systému Windows, úpravy dat a odeslání aktualizovaných dat zpět do databáze. Tento návod vytvoří formulář, který zobrazí data ze dvou souvisejících tabulek, a ukazuje, jak upravit záznamy a uložit změny zpět do databáze. Tento příklad používá `Customers` tabulky a `Orders` z ukázkové databáze Northwind.

 Data v aplikaci můžete uložit zpět do databáze voláním `Update` metody TableAdapter. Když přetáhnete tabulky z okna **zdroje dat** do formuláře, je automaticky přidán kód potřebný k uložení dat. Všechny další tabulky, které jsou přidány do formuláře, vyžadují ruční přidání tohoto kódu. Tento návod ukazuje, jak přidat kód pro uložení aktualizací z více než jedné tabulky.

> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici, kterou používáte. Chcete-li změnit nastavení, v nabídce **nástroje** klikněte na položku **Nastavení importu a exportu** . Další informace naleznete v tématu [přizpůsobení nastavení vývoje v aplikaci Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

 Úlohy, které jsou znázorněné v tomto návodu, zahrnují:

- Vytvoření nového projektu **aplikace pro systém Windows** .

- Vytvoření a konfigurace zdroje dat v aplikaci pomocí [Průvodce konfigurací zdroje dat](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).

- Nastavení ovládacích prvků položek v [okně zdroje dat](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992). Další informace naleznete v tématu [nastavení ovládacího prvku, který má být vytvořen při přetahování z okna zdroje dat](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

- Vytváření ovládacích prvků vázaných na data přetažením položek z okna **zdroje dat** do formuláře.

- Úprava několika záznamů v každé tabulce datové sady.

- Úprava kódu pro odeslání aktualizovaných dat v datové sadě zpět do databáze.

## <a name="prerequisites"></a>Předpoklady
 Aby bylo možné dokončit tento návod, budete potřebovat:

- Přístup k ukázkové databázi Northwind.

## <a name="create-the-windows-application"></a>Vytvoření aplikace pro Windows
 Prvním krokem je vytvoření **aplikace pro Windows**. Přiřazení názvu k projektu je během tohoto kroku volitelné, ale přiřadíme mu název, protože plánujeme ho uložit později.

#### <a name="to-create-the-new-windows-application-project"></a>Vytvoření nového projektu aplikace pro systém Windows

1. V nabídce **soubor** vytvořte nový projekt.

2. Pojmenujte projekt `UpdateMultipleTablesWalkthrough` .

3. Vyberte **aplikace systému Windows**a pak vyberte **OK**. Další informace najdete v tématu [klientské aplikace](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     Projekt **UpdateMultipleTablesWalkthrough** je vytvořen a přidán do **Průzkumník řešení**.

## <a name="create-the-data-source"></a>Vytvoření zdroje dat
 Tento krok vytvoří zdroj dat z databáze Northwind pomocí **Průvodce konfigurací zdroje dat**. Abyste mohli vytvořit připojení, musíte mít přístup k ukázkové databázi Northwind.

#### <a name="to-create-the-data-source"></a>Vytvoření zdroje dat

1. V nabídce **data** vyberte možnost**Zobrazit zdroje dat**.

2. V okně **zdroje dat** vyberte možnost**Přidat nový zdroj dat** a spusťte **Průvodce konfigurací zdroje dat**.

3. Na obrazovce **Vybrat typ zdroje dat**vyberte **databáze**a pak vyberte **Další**.

4. Na obrazovce **Vybrat datové připojení**proveďte jednu z následujících akcí:

    - Pokud je připojení dat k ukázkové databázi Northwind k dispozici v rozevíracím seznamu, vyberte je.

         -nebo-

    - Vyberte **nové připojení** , aby se otevřelo dialogové okno **Přidat nebo upravit připojení** .

5. Pokud vaše databáze vyžaduje heslo, vyberte možnost zahrnutí citlivých dat a pak vyberte **Další**.

6. V části **Uložit připojovací řetězec do konfiguračního souboru aplikace**vyberte možnost **Další**.

7. Na obrazovce **zvolit vaše databázové objekty**rozbalte uzel **tabulky** .

8. Vyberte tabulky **zákazníci** a **objednávky** a pak vyberte **Dokončit**.

     **NorthwindDataSet** je přidán do projektu a tabulky se zobrazí v okně **zdroje dat** .

## <a name="set-the-controls-to-be-created"></a>Nastavit ovládací prvky, které se mají vytvořit
 V tomto návodu jsou data v `Customers` tabulce v rozložení **podrobností** , kde se zobrazují data v jednotlivých ovládacích prvcích. Data z `Orders` tabulky jsou v rozložení **mřížky** , které se zobrazí v <xref:System.Windows.Forms.DataGridView> ovládacím prvku.

#### <a name="to-set-the-drop-type-for-the-items-in-the-data-sources-window"></a>Nastavení typu přetažení pro položky v okně zdroje dat

1. V okně **zdroje dat** rozbalte uzel **Customers (zákazníci** ).

2. V uzlu **Customers (zákazníci** ) vyberte **Podrobnosti** ze seznamu řízení a změňte tak řízení tabulky **Customers** na jednotlivé ovládací prvky. Další informace naleznete v tématu [nastavení ovládacího prvku, který má být vytvořen při přetahování z okna zdroje dat](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

## <a name="create-the-data-bound-form"></a>Vytvoření formuláře vázaného na data
 Můžete vytvořit ovládací prvky vázané na data přetažením položek z okna **zdroje dat** do formuláře.

#### <a name="to-create-data-bound-controls-on-the-form"></a>Vytvoření ovládacích prvků vázaných na data ve formuláři

1. Přetáhněte hlavní uzel **Customers** z okna **zdroje dat** do formuláře **Form1**.

     Ovládací prvky vázané na data s popisnými popisky se zobrazí ve formuláři spolu s pruhem nástrojů ( <xref:System.Windows.Forms.BindingNavigator> ) pro procházení záznamů. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> a <xref:System.Windows.Forms.BindingNavigator> se zobrazí v zásobníku komponent.

2. Přetáhněte uzel souvisejících **objednávek** z okna **zdroje dat** do formuláře **Form1**.

    > [!NOTE]
    > Uzel souvisejících **objednávek** je umístěný pod sloupcem **Fax** a je podřízeným uzlem uzlu **Customers (zákazníci** ).

     <xref:System.Windows.Forms.DataGridView>Ovládací prvek a pruh nástrojů ( <xref:System.Windows.Forms.BindingNavigator> ) pro procházení záznamů se zobrazí ve formuláři. OrdersTableAdapter a <xref:System.Windows.Forms.BindingSource> zobrazí se v zásobníku komponent.

## <a name="addcode-to-update-the-database"></a>AddCode k aktualizaci databáze
 Databázi můžete aktualizovat voláním `Update` metod **zákazníků** a **objednávek** objekty TableAdapter. Ve výchozím nastavení je obslužná rutina události pro tlačítko **Uložit** objektu <xref:System.Windows.Forms.BindingNavigator> přidána do kódu formuláře, aby odesílala aktualizace databáze. Tento postup upraví kód tak, aby odesílal aktualizace ve správném pořadí. Tím se eliminuje možnost vyvolání chyb referenční integrity. Kód také implementuje zpracování chyb zabalením volání aktualizace do bloku try-catch. Kód můžete upravit tak, aby vyhovoval potřebám vaší aplikace.

> [!NOTE]
> Pro přehlednost tento návod nepoužívá transakci. Pokud však aktualizujete dvě nebo více souvisejících tabulek, zahrňte do transakce veškerou logiku aktualizace. Transakce je proces, který zaručuje, že všechny související změny v databázi budou úspěšné, než budou všechny změny potvrzeny. Další informace najdete v tématu [transakce a souběžnost](https://msdn.microsoft.com/library/f46570de-9e50-4fe6-8710-a8c31fa8569b).

#### <a name="to-add-update-logic-to-the-application"></a>Přidání logiky aktualizací do aplikace

1. Vyberte tlačítko **Uložit** na <xref:System.Windows.Forms.BindingNavigator> . Tím se otevře Editor kódu pro `bindingNavigatorSaveItem_Click` obslužnou rutinu události.

2. Nahraďte kód v obslužné rutině události pro volání `Update` metod souvisejícího objekty TableAdapter. Následující kód nejprve vytvoří tři dočasné tabulky dat, které uchovávají aktualizované informace pro každý <xref:System.Data.DataRowState> ( <xref:System.Data.DataRowState> , a <xref:System.Data.DataRowState> <xref:System.Data.DataRowState> ). Pak jsou aktualizace spouštěny ve správném pořadí. Kód by měl vypadat takto:

     [!code-csharp[VbRaddataSaving#10](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form4.cs#10)]
     [!code-vb[VbRaddataSaving#10](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form4.vb#10)]

## <a name="test-the-application"></a>Testování aplikace

#### <a name="to-test-the-application"></a>Testování aplikace

1. Vyberte **F5**.

2. Proveďte některé změny dat jednoho nebo více záznamů v každé tabulce.

3. Vyberte tlačítko **Uložit**.

4. Zkontrolujte hodnoty v databázi a ověřte, zda byly změny uloženy.

## <a name="next-steps"></a>Další kroky
 V závislosti na požadavcích vaší aplikace existuje několik kroků, které můžete chtít provést po vytvoření formuláře vázaného na data v aplikaci pro Windows. Mezi vylepšení, která je možné pro tento návod provést, patří:

- Přidání vyhledávací funkce do formuláře. Další informace najdete v tématu [Postup: Přidání parametrizovaného dotazu do aplikace model Windows Forms](https://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416).

- Úprava zdroje dat pro přidání nebo odebrání databázových objektů. Další informace naleznete v tématu [How to: Edit a DataSet](https://msdn.microsoft.com/library/f2dade5f-9c7a-4ddb-96a8-e0a39e50bfd3).

## <a name="see-also"></a>Viz také
 [Ukládání dat zpět do databáze](../data-tools/save-data-back-to-the-database.md)
