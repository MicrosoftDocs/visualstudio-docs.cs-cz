---
title: Vytvoření a konfigurace objekty TableAdapter | Microsoft Docs
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
- table adapters, creating
- creating TableAdapters
- data [Visual Studio], creating data components
- data [Visual Studio], TableAdapters
- data [Visual Studio], creating table adapters
ms.assetid: 08630d69-0d6c-4e8f-b42d-2922f45f8415
caps.latest.revision: 33
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9a2136960dfcbbbcf63fbefeb16d527793d4b939
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72631041"
---
# <a name="create-and-configure-tableadapters"></a>Vytvoření a konfigurace objektů TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Objekty TableAdapter umožňují komunikaci mezi aplikací a databází. Připojují se k databázi, spouštějí dotazy nebo uložené procedury a buď vracejí novou tabulku dat, nebo vyplní existující data <xref:System.Data.DataTable> pomocí vrácených dat. Objekty TableAdapter může také odesílat aktualizované údaje z vaší aplikace zpátky do databáze.

 Objekty TableAdapter se vytvoří za vás, když provedete jednu z následujících akcí:

- Spusťte [Průvodce konfigurací zdroje dat](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) a vyberte buď **databázi** , nebo typ zdroje dat **webové služby** .

- Přetáhněte objekty databáze z [Průzkumník serveru](https://msdn.microsoft.com/library/4ea29b3b-bbb2-45e4-9082-eaf635c41c4d) do **Návrhář datových sad**.

  Můžete vytvořit novou TableAdapter a nakonfigurovat ji se zdrojem dat přetažením TableAdapter ze sady nástrojů do prázdné oblasti **Návrhář datových sad** povrchu.

  Úvod do objekty TableAdapter najdete v tématu [vyplnění datových sad pomocí objekty TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md).

  [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="use-the-tableadapter-configuration-wizard"></a>Použití Průvodce konfigurací TableAdapter
 Spusťte **Průvodce konfigurací TableAdapter** a vytvořte nebo upravte objekty TableAdapter a jejich přidružené Datatabulky. Existující TableAdapter můžete nakonfigurovat tak, že na něj kliknete pravým tlačítkem na **Návrhář datových sad**.

 ![Průvodce konfigurací adaptéru raddata Table](../data-tools/media/raddata-table-adapter-configuration-wizard.png "Průvodce konfigurací adaptéru raddata Table")

 Pokud přetáhnete novou TableAdapter ze sady nástrojů, když je **Návrhář datových sad** aktivní, Průvodce vás vyzve, abyste určili, ke kterému zdroji dat se TableAdapter má připojit, a jaký druh příkazů by měl používat ke komunikaci s databází, příkazy SQL nebo uloženými procedurami. Tato konfigurace se nezobrazuje, pokud konfigurujete TableAdapter, která je už přidružená ke zdroji dat.

- Použití **metod Create k odeslání aktualizací přímo do databáze** je ekvivalentní nastavení `GenerateDBDirectMethods` vlastnosti na hodnotu true. Možnost není k dispozici, pokud původní příkaz SQL neposkytuje dostatek informací nebo dotaz není dotazem s možností aktualizace. Tato situace může nastat například v dotazech **Join** a dotazech, které vracejí jednu (skalární) hodnotu.

- Pokud máte správná oprávnění pro databázi, máte možnost vytvořit novou uloženou proceduru v podkladové databázi. Pokud tato oprávnění nemáte, nebude to možnost.

- Můžete se také rozhodnout spouštět existující uložené procedury pro příkazy **Select**, **INSERT**, **Update**a **Delete** v TableAdapter. Uloženou proceduru, která je přiřazena k příkazu **Update** , je například spuštěna při `TableAdapter.Update()` volání metody.

     Namapujte parametry z vybrané uložené procedury do odpovídajících sloupců v tabulce dat. Například pokud uložená procedura akceptuje parametr s názvem `@CompanyName` , který předává do `CompanyName` sloupce v tabulce, nastavte **zdrojový sloupec** `@CompanyName` parametru na `CompanyName` .

    > [!NOTE]
    > Uloženou proceduru, která je přiřazena k příkazu SELECT, je spuštěna voláním metody TableAdapter, kterou jste si pojmenovat v dalším kroku průvodce. Výchozí metoda je `Fill` , takže kód, který se obvykle používá ke spuštění procedury SELECT, je `TableAdapter.Fill(tableName)` . Pokud změníte výchozí název z `Fill` , nahraďte `Fill` názvem, který přiřadíte, a nahraďte "TableAdapter" skutečným názvem TableAdapter (například `CustomersTableAdapter` ).

- **Rozšířené možnosti** v průvodci umožňují generovat příkazy INSERT, Update a DELETE na základě příkazu SELECT, který je definován na stránce **Generovat příkazy SQL** . Použijte optimistickou souběžnost a určete, zda má být tabulka dat aktualizována po spuštění příkazů INSERT a UPDATE.

## <a name="configure-a-tableadapters-fill-method"></a>Konfigurace metody Fill TableAdapter
 Někdy možná budete chtít změnit schéma tabulky TableAdapter. K tomu je potřeba upravit primární `Fill` metodu TableAdapter. Objekty TableAdapter jsou vytvořeny s primární `Fill` metodou definující schéma přidružené datové tabulky. Primární `Fill` Metoda je založena na dotazu nebo uložené proceduře, kterou jste zadali při původní konfiguraci TableAdapter. Je první (nejvyšší) metodou v tabulce dat v Návrháři DataSet.

 ![TableAdapter s více dotazy](../data-tools/media/tableadapter.gif "TableAdapter")

 Všechny změny, které provedete v hlavní metodě TableAdapter, `Fill` se projeví ve schématu přidružené tabulky dat. Například odebrání sloupce z dotazu v `Fill` metodě Main také odebere sloupec z přidružené tabulky dat. Kromě toho odebráním sloupce z metody Main `Fill` odeberete sloupec z dalších dotazů na tento TableAdapter.

 Průvodce konfigurací dotazu TableAdapter můžete použít k vytvoření a úpravě dalších dotazů pro TableAdapter. Tyto další dotazy musí odpovídat schématu tabulky, pokud nevrátí skalární hodnotu.  Další dotazy mají názvy, které zadáte (například `CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, "Seattle")` .)

#### <a name="to-start-the-tableadapter-query-configuration-wizard-with-a-new-query"></a>Spuštění Průvodce konfigurací dotazu TableAdapter s novým dotazem

1. Otevřete datovou sadu v **Návrhář datových sad**.

2. Pokud vytváříte nový dotaz, přetáhněte objekt **dotazu** z karty **datová sada** na **panelu nástrojů** na <xref:System.Data.DataTable> , nebo vyberte možnost **Přidat dotaz** z místní nabídky TableAdapter. Objekt **dotazu** lze také přetáhnout do prázdné oblasti **Návrhář datových sad**, čímž se vytvoří TableAdapter bez přidruženého objektu <xref:System.Data.DataTable> . Tyto dotazy mohou vracet pouze jednotlivé (skalární) hodnoty nebo příkazy pro aktualizaci, vložení nebo odstranění v databázi.

3. Na obrazovce **Vybrat datové připojení** vyberte nebo vytvořte připojení, které bude dotaz používat.

    > [!NOTE]
    > Tato obrazovka se zobrazí pouze v případě, že Návrhář nemůže určit správné připojení, nebo když nejsou k dispozici žádná připojení.

4. Na obrazovce **Zvolte typ příkazu** vyberte z následujících metod načítání dat z databáze následující metody:

    - **Pomocí příkazů SQL** můžete zadat příkaz SQL pro výběr dat z databáze.

    - Možnost **vytvořit novou uloženou proceduru** vám umožní průvodce vytvořit novou uloženou proceduru (v databázi) na základě zadaného příkazu SELECT.

    - **Pomocí existujících uložených procedur** můžete spustit existující uloženou proceduru při spuštění dotazu.

#### <a name="to-start-the-tableadapter-query-configuration-wizard-on-an-existing-query"></a>Spuštění Průvodce konfigurací dotazu TableAdapter pro existující dotaz

- Pokud upravujete existující dotaz TableAdapter, klikněte na něj pravým tlačítkem myši a potom v místní nabídce zvolte možnost **Konfigurovat** .

    > [!NOTE]
    > Kliknutím pravým tlačítkem na hlavní dotaz TableAdapter překonfigurujete TableAdapter a <xref:System.Data.DataTable> schéma. Když ale kliknete pravým tlačítkem na další dotaz na TableAdapter, nakonfiguruje se jenom vybraný dotaz. **Průvodce konfigurací TableAdapter** překonfiguruje definici TableAdapter, zatímco Průvodce konfigurací dotazů TableAdapter znovu nakonfiguruje pouze vybraný dotaz.

#### <a name="to-add-a-global--query-to-a-tableadapter"></a>Přidání globálního dotazu do TableAdapter

- *Globální dotazy* jsou dotazy SQL, které vracejí jednu (skalární) hodnotu nebo žádnou hodnotu. Globální funkce obvykle provádějí databázové operace, jako jsou vložení, aktualizace a odstranění. Také agregují informace, například počet zákazníků v tabulce nebo celkové poplatky za všechny položky v určitém pořadí.

     Globální dotazy můžete přidat přetažením objektu **dotazu** z karty **datová sada** v sadě **nástrojů** do prázdné oblasti **Návrhář datových sad**.

- Zadejte dotaz, který provede požadovanou úlohu, například `SELECT COUNT(*) AS CustomerCount FROM Customers` .

    > [!NOTE]
    > Přetažení objektu **dotazu** přímo na **Návrhář datových sad** vytvoří metodu, která vrátí pouze skalární (jednoduchou) hodnotu. Přestože vybraný dotaz nebo uložená procedura může vracet více než jednu hodnotu, metoda, která je vytvořena průvodcem, vrací pouze jednu hodnotu. Dotaz může například vracet první sloupec prvního řádku vrácených dat.

## <a name="see-also"></a>Viz také
 [Vyplnění datových sad pomocí objektů TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)
