---
title: Připojení k datům v databázi aplikace Access (Windows Forms)
ms.date: 09/15/2017
ms.topic: conceptual
helpviewer_keywords:
- databases, connecting to
- databases, Access
- data [Visual Studio], connecting
- connecting to data, from Access databases
- Access databases, connecting
ms.assetid: 4159e815-d430-4ad0-a234-e4125fcbef18
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 33981ac76d8c502d56571a112ee8cd1e0c11dce0
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2018
ms.locfileid: "52304573"
---
# <a name="connect-to-data-in-an-access-database-windows-forms"></a>Připojení k datům v databázi aplikace Access (Windows Forms)

Můžete připojit k databázi aplikace Access (buď *.mdf* souboru nebo *.accdb* souboru) pomocí sady Visual Studio. Po definování připojení se data zobrazí v **zdroje dat** okna. Odtud můžete přetáhnout tabulky nebo zobrazení do formulářů.

## <a name="prerequisites"></a>Požadavky

Pokud chcete použít tyto postupy, potřebujete projekt aplikace Windows Forms a databáze aplikace Access (*.accdb* soubor) nebo databázi aplikace Access 2000-2003 (*.mdb* souboru). Postupujte podle kroků odpovídajících vašemu typu souboru.

## <a name="creating-the-dataset-for-an-accdb-file"></a>Vytvoření datové sady pro soubor .accdb

Můžete připojit k databázím vytvořeným pomocí aplikace Access 2013, Office 365, Access 2010 nebo 2007 přístup pomocí následujícího postupu.

### <a name="to-create-the-dataset"></a>Vytvoření datové sady

1.  Otevřete aplikaci Windows Forms, ke kterému chcete připojit data.

2.  Chcete-li otevřít **zdroje dat** okno na **zobrazení** nabídce vyberte možnost **ostatní Windows** > **zdroje dat**.

     ![Zobrazení zdrojů dat Windows](../data-tools/media/viewdatasources.png)

3.  V **zdroje dat** okna, klikněte na tlačítko **přidat nový zdroj dat**.

     **Průvodce konfigurací zdroje dat** otevře.

4.  Vyberte **databáze** na **zvolte typ zdroje dat** stránce a pak vyberte **Další**.

5.  Vyberte **datovou sadu** na **vyberte databázový Model** stránce a pak vyberte **Další**.

6.  Na **vyberte datové připojení** stránce **nové připojení** konfigurace nové datové připojení.

     **Přidat připojení** zobrazí se dialogové okno.

7.  Vyberte **změnu** vedle **zdroj dat** textového pole.

     **Změnit zdroj dat** zobrazí se dialogové okno.

8.  V seznamu zdrojů dat, zvolte  **\<jiných\>**. V **poskytovatele dat** rozevíracího seznamu, vyberte **zprostředkovatele dat .NET Framework pro OLE DB**, klikněte na tlačítko **OK**.

9. Zpátky **přidat připojení** dialogovém okně vyberte **Office 12.0 Access Database modulu zprostředkovatele Microsoft OLE DB** z **zprostředkovatele OLE DB** rozevíracího seznamu.

     ![OLE DB poskytovatele Microsoft Office 12.0 Access](../data-tools/media/dataoledbprovideroffice12access.png)

     > [!NOTE]
     > Pokud nevidíte **Office 12.0 Access Database modulu zprostředkovatele Microsoft OLE DB** ve zprostředkovateli OLE DB rozevíracího seznamu, budete muset nainstalovat [ovladač systému Office 2007: součásti pro připojení dat](https://www.microsoft.com/download/confirmation.aspx?id=23734).

9. V **serveru nebo název souboru** textového pole zadejte cestu a název souboru *.accdb* souboru, kterou chcete připojit a pak vyberte **OK**. (Pokud má soubor databáze uživatelské jméno a heslo, zadejte, je před výběrem **OK**.)

10. Vyberte **Další** na **vyberte datové připojení** stránky.

     Může se zobrazit dialogové okno informující o datový soubor není v aktuálním projektu. Vyberte **Ano** nebo **ne**.

11. Vyberte **Další** na **uložit připojovací řetězec do konfiguračního souboru aplikace** stránky.

12. Rozbalte **tabulky** uzlu **zvolte vaše databázové objekty** stránky.

13. Vyberte jakékoli tabulky a zobrazení v datové sadě a pak vyberte **Dokončit**.

     Do projektu je přidána datová sada a tabulky a zobrazení se zobrazí **zdroje dat** okna.

## <a name="create-the-dataset-for-an-mdb-file"></a>Vytvoření datové sady pro soubor .mdb

Vytvořte datovou sadu spuštěním **Průvodce konfigurací zdroje dat**.

### <a name="to-create-the-dataset"></a>Vytvoření datové sady

1.  Otevřete aplikaci Windows Forms, ke kterému chcete připojit data.

2.  Na **zobrazení** nabídce vyberte možnost **ostatní Windows** > **zdroje dat**.

     ![Zobrazení zdrojů dat Windows](../data-tools/media/viewdatasources.png)

3.  V **zdroje dat** okna, klikněte na tlačítko **přidat nový zdroj dat**.

     **Průvodce konfigurací zdroje dat** otevře.

4.  Vyberte **databáze** na **zvolte typ zdroje dat** stránce a pak vyberte **Další**.

5.  Vyberte **datovou sadu** na **vyberte databázový Model** stránce a pak vyberte **Další**.

6.  Na **vyberte datové připojení** stránce **nové připojení** konfigurace nové datové připojení.

7.  Pokud zdroj dat není **soubor databáze Microsoft Access (OLE DB)** vyberte **změnu** otevřít **změnit zdroj dat** dialogové okno a vyberte **Microsoft Přístup k souboru databáze**a pak vyberte **OK**.

8.  V **název souboru databáze**, zadejte cestu a název *.mdb* souboru, kterou chcete připojit a pak vyberte **OK**.

     ![Přidat připojení souboru databáze aplikace Access](../data-tools/media/dataaddconnectionaccessmdb.png)

9. Vyberte **Další** na **vyberte datové připojení** stránky.

10. Vyberte **Další** na **uložit připojovací řetězec do konfiguračního souboru aplikace** stránky.

11. Rozbalte **tabulky** uzlu **zvolte vaše databázové objekty** stránky.

12. Vyberte jakékoli tabulky a zobrazení v datové sadě a pak vyberte **Dokončit**.

     Do projektu je přidána datová sada a tabulky a zobrazení se zobrazí **zdroje dat** okna.

## <a name="security"></a>Zabezpečení

Ukládání citlivých informací (například hesla) může ovlivnit zabezpečení aplikace. Bezpečnější způsob, jak řídit přístup k databázi, je ověřování systému Windows (označované také jako integrované zabezpečení). Další informace najdete v tématu [ochrana informací o připojení](/dotnet/framework/data/adonet/protecting-connection-information).

## <a name="next-steps"></a>Další kroky

Je teď dostupná v datové sadě, kterou jste právě vytvořili **zdroje dat** okna. Nyní můžete provést kteroukoli z následujících úloh:

-   Vyberte položky v **zdroje dat** okno a přetáhněte je na svůj formulář (naleznete v tématu [ovládací prvky vazby Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)).

-   Otevřít zdroj dat v **Návrhář Dataset** můžete přidat nebo upravit objekty, které tvoří datové sady.

-   Přidejte logiku ověřování k <xref:System.Data.DataTable.ColumnChanging> nebo <xref:System.Data.DataTable.RowChanging> události tabulek dat v datové sadě (naleznete v tématu [ověření dat v datových sadách](../data-tools/validate-data-in-datasets.md)).

## <a name="see-also"></a>Viz také:

- [Přidání připojení](../data-tools/add-new-connections.md)