---
title: Připojení k datům v accessové databázi
description: Zjistěte, jak se připojit k datům v databázi Access (soubor. mdb nebo soubor. accdb. accdb) v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 07/18/2019
ms.topic: how-to
helpviewer_keywords:
- data [Visual Studio], connecting
- connecting to data, Access databases
- Access databases, connecting
ms.assetid: 4159e815-d430-4ad0-a234-e4125fcbef18
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 156acfd56789ec13201738e72c6df283e257e94f
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436859"
---
# <a name="connect-to-data-in-an-access-database"></a>Připojení k datům v accessové databázi

Pomocí sady Visual Studio se můžete připojit k databázi aplikace Access (soubor *. mdb* nebo soubor *. accdb* ). Po definování připojení se data zobrazí v okně **zdroje dat** . Odtud můžete přetáhnout tabulky nebo zobrazení na návrhovou plochu.

## <a name="prerequisites"></a>Předpoklady

Chcete-li použít tyto postupy, potřebujete projekt model Windows Forms nebo WPF a buď databázi aplikace Access (soubor *. accdb* ), nebo databázi Access 2000-2003 (soubor *. mdb* ). Postupujte podle kroků odpovídajících vašemu typu souboru.

## <a name="create-a-dataset-for-an-accdb-file"></a>Vytvoření datové sady pro soubor. accdb

Pomocí následujícího postupu se připojte k databázím vytvořeným pomocí Microsoft 365, Access 2013, Access 2010 nebo Access 2007.

1. Otevřete projekt aplikace model Windows Forms nebo WPF v aplikaci Visual Studio.

2. Chcete-li otevřít okno **zdroje dat** , vyberte v nabídce **zobrazení** položku **jiné**  >  **zdroje dat** systému Windows.

   ![Zobrazení dalších zdrojů dat Windows](../data-tools/media/viewdatasources.png)

3. V okně **zdroje dat** klikněte na tlačítko **Přidat nový zdroj dat**.

   Otevře se **Průvodce konfigurací zdroje dat** .

4. Vyberte možnost **databáze** na stránce **Vybrat typ zdroje dat** a pak vyberte možnost **Další**.

5. Na stránce **Vyberte databázový model** vyberte **datová sada** a pak vyberte **Další**.

6. Na stránce **Vyberte datové připojení** vyberte **nové připojení** a nakonfigurujte nové datové připojení.

   Otevře se dialogové okno **Přidat připojení** .

7. Pokud **zdroj dat** není nastaven na **soubor databáze aplikace Microsoft Access** , vyberte tlačítko **změnit** .

   Otevře se dialogové okno **změnit zdroj dat** . V seznamu zdrojů dat vyberte **soubor databáze aplikace Microsoft Access**. V rozevíracím seznamu **Zprostředkovatel dat** vyberte **pro OLE DB možnost .NET Framework Zprostředkovatel dat** a pak zvolte **OK**.

8. Klikněte na tlačítko **Procházet** vedle **pole název souboru databáze** a poté přejděte k souboru *. accdb* a zvolte možnost **otevřít**.

9. Zadejte uživatelské jméno a heslo (v případě potřeby) a pak zvolte **OK**.

10. Na stránce **Vyberte datové připojení** vyberte **Další** .

    Může se zobrazit dialogové okno s oznámením, že datový soubor není v aktuálním projektu. Vyberte **Ano** nebo **ne**.

11. Klikněte na tlačítko **Další** na stránce **Uložit připojovací řetězec do konfiguračního souboru aplikace** .

12. Rozbalte uzel **tabulky** na stránce **zvolit objekty databáze** .

13. Vyberte tabulky nebo zobrazení, které chcete zahrnout do datové sady, a pak vyberte **Dokončit**.

    Datová sada je přidána do projektu a tabulky a zobrazení se zobrazí v okně **zdroje dat** .

## <a name="create-a-dataset-for-an-mdb-file"></a>Vytvoření datové sady pro soubor. mdb

Pomocí následujícího postupu se připojte k databázím vytvořeným pomocí přístupu 2000-2003.

1. Otevřete projekt aplikace model Windows Forms nebo WPF v aplikaci Visual Studio.

2. V nabídce **zobrazení** vyberte **jiné**  >  **zdroje dat** Windows.

   ![Zobrazení dalších zdrojů dat Windows](../data-tools/media/viewdatasources.png)

3. V okně **zdroje dat** klikněte na tlačítko **Přidat nový zdroj dat**.

    Otevře se **Průvodce konfigurací zdroje dat** .

4. Vyberte možnost **databáze** na stránce **Vybrat typ zdroje dat** a pak vyberte možnost **Další**.

5. Na stránce **Vyberte databázový model** vyberte **datová sada** a pak vyberte **Další**.

6. Na stránce **Vyberte datové připojení** vyberte **nové připojení** a nakonfigurujte nové datové připojení.

7. Pokud zdroj dat není **soubor databáze Microsoft Access (OLE DB)** , vyberte **změnit** , aby se otevřelo dialogové okno **změnit zdroj dat** , vyberte **soubor databáze Microsoft Access** a pak vyberte **OK**.

8. Do pole **název databázového souboru** zadejte cestu a název souboru *. mdb* , ke kterému se chcete připojit, a pak vyberte **OK**.

   ![Přidat soubor databáze přístupu k připojení](../data-tools/media/add-connection-access-db.png)

9. Na stránce **Vyberte datové připojení** vyberte **Další** .

10. Klikněte na tlačítko **Další** na stránce **Uložit připojovací řetězec do konfiguračního souboru aplikace** .

11. Rozbalte uzel **tabulky** na stránce **zvolit objekty databáze** .

12. V datové sadě vyberte libovolné tabulky nebo zobrazení a pak vyberte **Dokončit**.

    Datová sada je přidána do projektu a tabulky a zobrazení se zobrazí v okně **zdroje dat** .

## <a name="next-steps"></a>Další kroky

Datová sada, kterou jste právě vytvořili, je k dispozici v okně **zdroje dat** . Nyní můžete provádět následující úlohy:

- V okně **zdroje dat** vyberte položky a přetáhněte je na formulář nebo návrhovou plochu (viz téma [vazba model Windows Forms ovládací prvky na data v nástroji Visual Studio nebo v](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) tématu [Přehled datové vazby WPF](/dotnet/desktop-wpf/data/data-binding-overview)).

- Otevřete zdroj dat v **Návrhář datových sad** , chcete-li přidat nebo upravit objekty, které tvoří datovou sadu.

- Přidejte logiku ověřování k <xref:System.Data.DataTable.ColumnChanging> události nebo <xref:System.Data.DataTable.RowChanging> tabulek dat v datové sadě (viz [ověření dat v datových sadách](../data-tools/validate-data-in-datasets.md)).

## <a name="see-also"></a>Viz také

- [Přidání připojení](../data-tools/add-new-connections.md)
- [Přehled datové vazby WPF](/dotnet/framework/wpf/data/data-binding-overview)
- [model Windows Forms datové vazby](/dotnet/framework/winforms/data-binding-and-windows-forms)
