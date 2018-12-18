---
title: Vytvoření a konfigurace objektů TableAdapter
ms.date: 09/01/2017
ms.topic: conceptual
helpviewer_keywords:
- table adapters, creating
- creating TableAdapters
- data [Visual Studio], creating data components
- data [Visual Studio], TableAdapters
- data [Visual Studio], creating table adapters
ms.assetid: 08630d69-0d6c-4e8f-b42d-2922f45f8415
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: b720072d5ccd695ff1e7006bda5221ae00db06ef
ms.sourcegitcommit: 3a11feebad45a0dd4ac45efcbfdf172fce46e1de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2018
ms.locfileid: "39582343"
---
# <a name="create-and-configure-tableadapters"></a>Vytvoření a konfigurace objektů TableAdapter

Objekty TableAdapter umožňují komunikaci mezi aplikací a databází. Připojení k databázi, spouštění dotazů nebo uložených procedur a buď vrátí nová data tabulky nebo zadejte existující <xref:System.Data.DataTable> s vrácenými daty. Objekty TableAdapter lze také odeslat aktualizovaná data z aplikace zpět do databáze.

Objekty TableAdapter jsou vytvořeny pro vás při provádění jednoho z následujících akcí:

- Přetažení databázových objektů z **Průzkumníka serveru** do **Návrhář Dataset**.

- Spusťte Průvodce konfigurací zdroje dat a vyberte buď **databáze** nebo **webová služba** typ zdroje dat.

   ![Průvodce konfigurací zdroje dat v sadě Visual Studio](media/data-source-configuration-wizard.png)

Můžete také vytvořit nový TableAdapter a konfigurace se zdrojem dat přetažením z objektu typu TableAdapter **nástrojů** do prázdné oblasti v **Návrhář Dataset** povrchu.

Úvod do prvků TableAdapters, naleznete v tématu [vyplnění datové sady s použitím objektů TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="use-the-tableadapter-configuration-wizard"></a>Použití Průvodce nastavením TableAdapter

Spustit **Průvodce nastavením TableAdapter** vytvořit nebo upravit objekty TableAdapter a jejich přidružené datové tabulky. Kliknutím pravým tlačítkem myši na něj v můžete nakonfigurovat stávajícího TableAdapter **Návrhář Dataset**.

![raddata Průvodce konfigurací adaptéru tabulky](../data-tools/media/raddata-table-adapter-configuration-wizard.png)

Pokud přetáhnete nového TableAdapter z panelu nástrojů při **Návrhář Dataset** se zaměřit, spuštěn průvodce a pokynů, které lze určit, jaká data zdrojového objektu TableAdapter se má připojit k. Na další stránce průvodce požádá, jaký druh příkazy, měla by používat ke komunikaci s databází, příkazy SQL nebo úložné procedury. (Nezobrazí to při konfiguraci, která je už přidružený zdroj dat objektu TableAdapter.)

- Máte možnost vytvořit novou úložnou proceduru v podkladové databázi, pokud máte správná oprávnění pro databázi. Pokud tato oprávnění nemáte, to nebude možné.

- Můžete také spouštět existující uložené procedury pro **vyberte**, **vložit**, **aktualizace**, a **odstranit** příkazy TableAdapter. Uloženou proceduru, která je přiřazena **aktualizace** příkazu, například se spustí, když `TableAdapter.Update()` metoda je volána.

Mapování parametrů z vybranou úložnou proceduru na odpovídající sloupce v datové tabulce. Například, pokud uložená procedura přijme parametr s názvem `@CompanyName` , který předá do `CompanyName` sloupec v tabulce, nastaven **zdrojový sloupec** z `@CompanyName` parametr `CompanyName`.

> [!NOTE]
> Uložené procedury, která je přiřazena k příkazu SELECT se spustí zavoláním metody TableAdapter s názvy v dalším kroku v průvodci. Výchozí metodou je `Fill`, takže je kód, který se obvykle používá ke spuštění procedury SELECT `TableAdapter.Fill(tableName)`. Pokud změníte výchozí název z `Fill`, nahraďte `Fill` s názvem přiřadit a "TableAdapter" nahraďte skutečným názvem objektu TableAdapter (například `CustomersTableAdapter`).

- Výběr **vytvořit metody k odeslání aktualizací přímo do databáze** možnost je ekvivalentní k nastavení `GenerateDBDirectMethods` vlastnost na hodnotu true. Možnost není dostupná, když původní příkaz jazyka SQL neposkytuje dostatek informací, nebo dotaz není možné aktualizovat dotaz. Tato situace může nastat, například v **připojení** dotazy a dotazy, které vracejí hodnotu single (skalární).

**Rozšířené možnosti** v průvodci umožňují:

- Generovat příkazy INSERT, UPDATE a DELETE založené na příkazu SELECT, který je definován na **generovat SQL příkazy** stránky
- Použít optimistické řízení souběžnosti
- Určete, jestli chcete aktualizovat datovou tabulku po vložení a spuštění příkazů UPDATE

## <a name="configure-a-tableadapters-fill-method"></a>Konfigurace metody Fill objektu TableAdapter

Někdy můžete chtít změna schématu tabulky objektu TableAdapter. K tomuto účelu upravit primární objektu TableAdapter `Fill` metody. Objekty TableAdapter jsou vytvářeny s primární `Fill` metody, která definuje schématu přidružené tabulky dat. Primární `Fill` je založena na dotazu nebo uložené procedury, které jste zadali při původně nakonfigurován TableAdapter. Jedná se o první (nejvyššího) metodu pod tabulkou dat v návrháři datových sad.

![TableAdapter s více dotazy](../data-tools/media/tableadapter.gif)

Všechny změny provedené na objektu TableAdapter je hlavní `Fill` metoda se projeví ve schématu přidružené tabulky dat. Například odebráním sloupce z dotazu v hlavním `Fill` metoda také odeberete sloupec z přidružené tabulky dat. Kromě toho odebrání sloupce z hlavního `Fill` metoda odeberete sloupec z jakékoliv další dotazy pro tohoto objektu TableAdapter.

Průvodce konfigurací dotazu TableAdapter slouží k vytvoření a úprava další dotazy pro TableAdapter. Tyto další dotazy musí odpovídat schématu tabulky, pokud vracejí skalární hodnota.  Každý další dotaz má název, který zadáte.

Následující příklad ukazuje, jak volat další dotaz s názvem `FillByCity`:

`CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, "Seattle")`

### <a name="to-start-the-tableadapter-query-configuration-wizard-with-a-new-query"></a>Spusťte Průvodce konfigurací dotazu TableAdapter s nový dotaz

1.  Otevřete svou datovou sadu v **Návrhář Dataset**.

2.  Pokud vytváříte nový dotaz, přetáhněte **dotazu** objektu z **datovou sadu** kartě **nástrojů** na <xref:System.Data.DataTable>, nebo vyberte **přidat dotaz**z místní nabídky objektu TableAdapter. Můžete také přetáhnout **dotazu** objektu na prázdnou oblast **Návrhář Dataset**, vytváří TableAdapter bez přidruženého <xref:System.Data.DataTable>. Tyto dotazy můžete pouze vrátí jednu hodnotu (skalární) nebo spuštění UPDATE, INSERT nebo odstranit příkazů na databázi.

3.  Na **vyberte datové připojení** obrazovky, vyberte nebo vytvořte připojení, které budou používat dotaz.

    > [!NOTE]
    > Tato obrazovka se zobrazí, pouze když návrháře nelze určit správné připojení se má používat, nebo když jsou k dispozici žádná připojení.

4.  Na **zvolit typ příkazu** obrazovky, vyberte z následujících metod načítání dat z databáze:

    - **Použití SQL** umožňuje typ příkazu SQL vyberte data z databáze.

    - **Vytvořit novou úložnou proceduru** umožňuje má průvodce vytvoříte nový uložené procedury (databáze) na základě zadaného příkazu SELECT.

    - **Použití stávajících uložených procedur** umožňuje spouštět stávající úložnou proceduru při spuštění dotazu.

### <a name="to-start-the-tableadapter-query-configuration-wizard-on-an-existing-query"></a>Spusťte Průvodce konfigurací dotazu TableAdapter na existující dotaz

- Pokud upravujete stávající dotazu TableAdapter, klikněte pravým tlačítkem na dotaz a klikněte na tlačítko **konfigurovat** z místní nabídky.

    > [!NOTE]
    > Pravým tlačítkem myši na hlavním dotazu objektu TableAdapter rekonfiguruje TableAdapter a <xref:System.Data.DataTable> schématu. Pravým tlačítkem myši dalšího dotazu pro TableAdapter, ale nakonfiguruje pouze vybraný dotaz. **Průvodce nastavením TableAdapter** změní konfiguraci definici třídy TableAdapter při **Průvodce nastavením dotazu TableAdapter** změní konfiguraci vybraného dotazu.

### <a name="to-add-a-global-query-to-a-tableadapter"></a>Chcete-li přidat globální dotaz TableAdapter

- Globální dotazy jsou dotazy SQL, které vrací jedinou hodnotu (skalární) nebo žádnou hodnotu. Globální funkce obvykle provádění databázových operací, jako je například vložení, aktualizace a odstranění. Také se agregují informace, jako je počet zákazníků v tabulce nebo celkové poplatky pro všechny položky v určitém pořadí.

     Přidávání globálních dotazů přetažením **dotazu** objektu z **datovou sadu** karty **nástrojů** na prázdnou oblast **Návrhář Dataset**.

- Zadejte dotaz, který provede požadovanou úlohu, například `SELECT COUNT(*) AS CustomerCount FROM Customers`.

    > [!NOTE]
    > Přetahování **dotazu** objekt přímo **Návrhář Dataset** vytvoří metodu, která vrací pouze skalární hodnoty (single). Při dotazu nebo uložené procedury, které jste vybrali může vrátit více než jednu hodnotu, vrátí metoda, která se vytvoří pomocí Průvodce pouze jednu hodnotu. Dotaz může například vrátit první sloupec prvního řádku vracená data.

## <a name="see-also"></a>Viz také:

- [Vyplnění datové sady s použitím objektů TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)