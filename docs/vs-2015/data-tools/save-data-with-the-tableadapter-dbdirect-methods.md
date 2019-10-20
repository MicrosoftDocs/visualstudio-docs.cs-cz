---
title: Uložení dat pomocí metod TableAdapter DBDirect | Microsoft Docs
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
- TableAdapters, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], TableAdapter
ms.assetid: 74a6773b-37e1-4d96-a39c-63ee0abf49b1
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ce987f5ef90448c41da45a39c62710b968e11199
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655425"
---
# <a name="save-data-with-the-tableadapter-dbdirect-methods"></a>Ukládání dat pomocí metod TableAdapter DBDirect
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento návod poskytuje podrobné pokyny pro spuštění příkazů SQL přímo proti databázi pomocí metod DBDirect TableAdapter. Metody DBDirect pro TableAdapter poskytují jemnou úroveň kontroly nad aktualizacemi databáze. Můžete je použít ke spuštění specifických příkazů SQL a uložených procedur voláním individuálních metod `Insert`, `Update` a `Delete` podle potřeby vaší aplikace (na rozdíl od přetížené `Update` metody, která provádí aktualizaci, vložení a příkazy odstranit vše v jednom volání).

 V tomto návodu se naučíte:

- Vytvořte novou **aplikaci pro Windows**.

- Vytvořte a nakonfigurujte datovou sadu pomocí [Průvodce konfigurací zdroje dat](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).

- Vyberte ovládací prvek, který má být vytvořen ve formuláři při přetahování položek z okna **zdroje dat** . Další informace naleznete v tématu [nastavení ovládacího prvku, který má být vytvořen při přetahování z okna zdroje dat](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

- Vytvořte formulář vázaný na data přetažením položek z okna **zdroje dat** do formuláře.

- Přidejte metody pro přímý přístup k databázi a provádění vložení, aktualizace a odstranění.

## <a name="prerequisites"></a>Požadavky
 Aby bylo možné dokončit tento návod, budete potřebovat:

- Přístup k ukázkové databázi Northwind.

## <a name="create-a-windows-application"></a>Vytvoření aplikace pro Windows
 Prvním krokem je vytvoření **aplikace pro Windows**.

#### <a name="to-create-the-new-windows-project"></a>Vytvoření nového projektu Windows

1. V aplikaci Visual Studio v nabídce **soubor** vytvořte nový **projekt**.

2. Pojmenujte projekt **TableAdapterDbDirectMethodsWalkthrough**.

3. Vyberte **aplikace systému Windows**a pak vyberte **OK**. Další informace najdete v tématu [klientské aplikace](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     Projekt **TableAdapterDbDirectMethodsWalkthrough** je vytvořen a přidán do **Průzkumník řešení**.

## <a name="create-a-data-source-from-your-database"></a>Vytvoření zdroje dat z databáze
 Tento krok používá **Průvodce konfigurací zdroje dat** k vytvoření zdroje dat založeného na `Region` tabulce v ukázkové databázi Northwind. Abyste mohli vytvořit připojení, musíte mít přístup k ukázkové databázi Northwind.

#### <a name="to-create-the-data-source"></a>Vytvoření zdroje dat

1. V nabídce **data** vyberte možnost **Zobrazit zdroje dat**.

2. V okně **zdroje dat** vyberte možnost **Přidat nový zdroj dat** a spusťte **Průvodce konfigurací zdroje dat**.

3. Na obrazovce **Vybrat typ zdroje dat** vyberte **databáze**a pak vyberte **Další**.

4. Na obrazovce **Vybrat datové připojení** proveďte jednu z následujících akcí:

    - Pokud je připojení dat k ukázkové databázi Northwind k dispozici v rozevíracím seznamu, vyberte je.

         -nebo-

    - Vyberte **nové připojení** , aby se spustilo dialogové okno **Přidat nebo upravit připojení** .

5. Pokud vaše databáze vyžaduje heslo, vyberte možnost zahrnutí citlivých dat a pak vyberte **Další**.

6. Na obrazovce **Uložit připojovací řetězec do konfiguračního souboru aplikace** vyberte **Další**.

7. Na obrazovce **zvolit vaše databázové objekty** rozbalte uzel **tabulky** .

8. Vyberte tabulku `Region` a pak vyberte **Dokončit**.

     **NorthwindDataSet** je přidán do projektu a tabulka `Region` se zobrazí v okně **zdroje dat** .

## <a name="addcontrols-to-the-form-to-display-the-data"></a>Addcontrols na formulář pro zobrazení dat
 Vytvořte ovládací prvky vázané na data přetažením položek z okna **zdroje dat** do formuláře.

#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Vytvoření ovládacích prvků vázaných na data ve formuláři Windows

- Přetáhněte uzel hlavní **oblast** z okna **zdroje dat** do formuláře.

     Na formuláři se zobrazí ovládací prvek <xref:System.Windows.Forms.DataGridView> a pruh nástrojů (<xref:System.Windows.Forms.BindingNavigator>) pro procházení záznamů. V zásobníku komponent se zobrazí [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), RegionTableAdapter, <xref:System.Windows.Forms.BindingSource> a <xref:System.Windows.Forms.BindingNavigator>.

#### <a name="to-add-buttons-that-will-call-the-individual-tableadapter-dbdirect-methods"></a>Chcete-li přidat tlačítka, která budou volat jednotlivé metody DbDirect TableAdapter

1. Přetáhněte tři ovládací prvky <xref:System.Windows.Forms.Button> z **panelu nástrojů** na **Form1** (pod **RegionDataGridView**).

2. Pro každé tlačítko nastavte následující vlastnosti **názvu** a **textu** .

    |Name|Text|
    |----------|----------|
    |`InsertButton`|**Zadat**|
    |`UpdateButton`|**Aktualizace**|
    |`DeleteButton`|**Delete**|

#### <a name="to-add-code-to-insert-new-records-into-the-database"></a>Přidání kódu pro vložení nových záznamů do databáze

1. Vyberte **InsertButton** a vytvořte obslužnou rutinu události pro událost Click a otevřete formulář v editoru kódu.

2. @No__t_0 obslužnou rutinu události nahraďte následujícím kódem:

     [!code-csharp[VbRaddataSaving#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs#1)]
     [!code-vb[VbRaddataSaving#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb#1)]

#### <a name="to-add-code-to-update-records-in-the-database"></a>Přidání kódu pro aktualizaci záznamů v databázi

1. Poklikejte na **UpdateButton** a vytvořte obslužnou rutinu události pro událost Click a otevřete formulář v editoru kódu.

2. @No__t_0 obslužnou rutinu události nahraďte následujícím kódem:

     [!code-csharp[VbRaddataSaving#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs#2)]
     [!code-vb[VbRaddataSaving#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb#2)]

#### <a name="to-add-code-to-delete-records-from-the-database"></a>Přidání kódu pro odstranění záznamů z databáze

1. Vyberte **DeleteButton** a vytvořte obslužnou rutinu události pro událost Click a otevřete formulář v editoru kódu.

2. @No__t_0 obslužnou rutinu události nahraďte následujícím kódem:

     [!code-csharp[VbRaddataSaving#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs#3)]
     [!code-vb[VbRaddataSaving#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb#3)]

## <a name="run-the-application"></a>Spuštění aplikace

#### <a name="to-run-the-application"></a>Spuštění aplikace

- Pro spuštění aplikace vyberte **F5** .

- Vyberte tlačítko **Vložit** a ověřte, že se nový záznam zobrazí v mřížce.

- Klikněte na tlačítko **aktualizovat** a ověřte, zda je záznam v mřížce aktualizován.

- Vyberte tlačítko **Odstranit** a ověřte, zda je záznam odebrán z mřížky.

## <a name="next-steps"></a>Další kroky
 V závislosti na požadavcích vaší aplikace existuje několik kroků, které můžete chtít provést po vytvoření formuláře vázaného na data. Mezi vylepšení, která je možné pro tento návod provést, patří:

- Přidání vyhledávací funkce do formuláře. Další informace najdete v tématu [Postup: Přidání parametrizovaného dotazu do aplikace model Windows Forms](https://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416).

- Přidáním dalších tabulek do datové sady výběrem možnosti **Konfigurovat datovou sadu pomocí Průvodce** v okně **zdroje dat** . Můžete přidat ovládací prvky, které zobrazují související data přetažením souvisejících uzlů do formuláře.

## <a name="see-also"></a>Viz také
 [Ukládání dat zpět do databáze](../data-tools/save-data-back-to-the-database.md)
