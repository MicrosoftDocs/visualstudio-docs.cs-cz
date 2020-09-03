---
title: Připojení k datům v databázi Access (model Windows Forms) | Microsoft Docs
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
- databases, connecting to
- databases, Access
- data [Visual Studio], connecting
- connecting to data, from Access databases
- Access databases, connecting
ms.assetid: 4159e815-d430-4ad0-a234-e4125fcbef18
caps.latest.revision: 32
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8426e9fcaa29bef36b6701c78d622f6f42fd1171
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651134"
---
# <a name="connect-to-data-in-an-access-database-windows-forms"></a>Připojení k datům v databázi Accessu (model Windows Forms)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocí sady Visual Studio se můžete připojit k databázi aplikace Access (buď k souboru. mdf, nebo k souboru. accdb). Po definování připojení se data zobrazí v okně **zdroje dat** . Odtud můžete přetáhnout tabulky nebo zobrazení do formulářů.

## <a name="prerequisites"></a>Předpoklady
 Chcete-li použít tyto postupy, potřebujete projekt aplikace model Windows Forms a buď databázi aplikace Access (soubor. accdb), nebo databázi Access 2000 – 2003 (soubor. mdb). Postupujte podle kroků odpovídajících vašemu typu souboru.

## <a name="creating-the-dataset-for-an-accdb-file"></a>Vytvoření datové sady pro soubor. accdb
 Pomocí následujícího postupu se můžete připojit k databázím vytvořeným prostřednictvím přístupu 2013, Office 365, Access 2010 nebo 2007.

#### <a name="to-create-the-dataset"></a>Vytvoření datové sady

1. Otevřete aplikaci model Windows Forms, ke které chcete připojit data.

2. V nabídce **zobrazení** vyberte **jiné**  >  **zdroje dat**Windows.

     ![Zobrazení dalších zdrojů dat Windows](../data-tools/media/viewdatasources.png "ViewDataSources")

3. V okně **zdroje dat** klikněte na tlačítko **Přidat nový zdroj dat**.

     ![Přidat nový zdroj dat](../data-tools/media/dataaddnewdatasource.png "dataAddNewDataSource")

4. Vyberte možnost **databáze** na stránce **Vybrat typ zdroje dat** a pak vyberte možnost **Další**.

5. Na stránce **Vyberte databázový model** vyberte **datová sada** a pak vyberte **Další**.

6. Na stránce **Vyberte datové připojení** vyberte **nové připojení** a nakonfigurujte nové datové připojení.

7. Změňte **zdroj dat** na **.NET Framework Zprostředkovatel dat pro OLE DB**.

     ![Změnit Zprostředkovatel dat na OLE DB](../data-tools/media/datachangedatasourceoledb.png "dataChangeDataSourceOLEDB")

    > [!IMPORTANT]
    > I když se datový zdroj **souboru databáze aplikace Microsoft Access (OLE DB)** může zdát jako správná volba, použijete tento typ zdroje dat pouze pro soubory databáze. mdb.

8. V **OLE DB poskytovateli**vyberte **systém Microsoft Office 12,0 přístup k databázovému stroji OLE DB poskytovatel**.

     ![Přístup k systém Microsoft Office 12,0 poskytovatele OLE DB](../data-tools/media/dataoledbprovideroffice12access.png "dataOLEDBProviderOffice12Access")

9. Do pole **název serveru nebo souboru**zadejte cestu a název souboru. accdb, ke kterému se chcete připojit, a pak vyberte **OK**.

    > [!NOTE]
    > Pokud má databázový soubor uživatelské jméno a heslo, zadejte je před výběrem **OK**.

10. Na stránce **Vyberte datové připojení** vyberte **Další** .

11. Klikněte na tlačítko **Další** na stránce **Uložit připojovací řetězec do konfiguračního souboru aplikace** .

12. Rozbalte uzel **tabulky** na stránce **zvolit objekty databáze** .

13. V datové sadě vyberte libovolné tabulky nebo zobrazení a pak vyberte **Dokončit**.

     Datová sada je přidána do projektu a tabulky a zobrazení se zobrazí v okně **zdroje dat** .

## <a name="creating-the-dataset-for-an-mdb-file"></a>Vytvoření datové sady pro soubor. mdb
 Datovou sadu vytvoříte spuštěním **Průvodce konfigurací zdroje dat**.

#### <a name="to-create-the-dataset"></a>Vytvoření datové sady

1. Otevřete aplikaci model Windows Forms, ke které chcete připojit data.

2. V nabídce **zobrazení** vyberte **jiné**  >  **zdroje dat**Windows.

     ![Zobrazení dalších zdrojů dat Windows](../data-tools/media/viewdatasources.png "ViewDataSources")

3. V okně **zdroje dat** klikněte na tlačítko **Přidat nový zdroj dat**.

4. Vyberte možnost **databáze** na stránce **Vybrat typ zdroje dat** a pak vyberte možnost **Další**.

5. Na stránce **Vyberte databázový model** vyberte **datová sada** a pak vyberte **Další**.

6. Na stránce **Vyberte datové připojení** vyberte **nové připojení** a nakonfigurujte nové datové připojení.

7. Pokud zdroj dat není **soubor databáze Microsoft Access (OLE DB)**, vyberte **změnit** , aby se otevřelo dialogové okno **změnit zdroj dat** , vyberte **soubor databáze Microsoft Access**a pak vyberte **OK**.

8. Do pole **název databázového souboru**zadejte cestu a název souboru. mdb, ke kterému se chcete připojit, a pak vyberte **OK**.

     ![Přidat soubor databáze přístupu k připojení](../data-tools/media/dataaddconnectionaccessmdb.png "dataAddConnectionAccessMDB")

9. Na stránce **Vyberte datové připojení** vyberte **Další** .

10. Klikněte na tlačítko **Další** na stránce **Uložit připojovací řetězec do konfiguračního souboru aplikace** .

11. Rozbalte uzel **tabulky** na stránce **zvolit objekty databáze** .

12. V datové sadě vyberte libovolné tabulky nebo zobrazení a pak vyberte **Dokončit**.

     Datová sada je přidána do projektu a tabulky a zobrazení se zobrazí v okně **zdroje dat** .

## <a name="security"></a>Zabezpečení
 Ukládání citlivých informací (například hesla) může ovlivnit zabezpečení aplikace. Bezpečnější způsob, jak řídit přístup k databázi, je ověřování systému Windows (označované také jako integrované zabezpečení). Další informace najdete v tématu [ochrana informací o připojení](https://msdn.microsoft.com/library/1471f580-bcd4-4046-bdaf-d2541ecda2f4).

## <a name="next-steps"></a>Další kroky
 Právě vytvořená datová sada je nyní k dispozici v okně **zdroje dat** . Nyní můžete provádět následující úlohy:

- V okně **zdroje dat** vyberte položky a přetáhněte je do formuláře (Další informace najdete v tématu [vázání model Windows Forms ovládacích prvků na data v aplikaci Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)).

- Otevřete zdroj dat v Návrhář datových sad, chcete-li přidat nebo upravit objekty, které tvoří datovou sadu.

- Přidejte logiku ověřování k <xref:System.Data.DataTable.ColumnChanging> události nebo <xref:System.Data.DataTable.RowChanging> tabulek dat v datové sadě (viz [ověření dat v datových sadách](../data-tools/validate-data-in-datasets.md)).

## <a name="see-also"></a>Viz také

 [Příprava aplikace pro příjem](https://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad) [ovládacích prvků datových vazeb na data v aplikaci Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md) [ověřování](https://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e) [návodů](https://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4) k datům