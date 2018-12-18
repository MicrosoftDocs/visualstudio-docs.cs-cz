---
title: Vytvoření a konfigurace objektů TableAdapter | Dokumentace Microsoftu
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
- table adapters, creating
- creating TableAdapters
- data [Visual Studio], creating data components
- data [Visual Studio], TableAdapters
- data [Visual Studio], creating table adapters
ms.assetid: 08630d69-0d6c-4e8f-b42d-2922f45f8415
caps.latest.revision: 33
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 03cb6c67b4887762885a0cb920eb928359b4708b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49917645"
---
# <a name="create-and-configure-tableadapters"></a>Vytvoření a konfigurace objektů TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Objekty TableAdapter umožňují komunikaci mezi aplikací a databází. Připojení k databázi, spouštění dotazů nebo uložených procedur a buď vrátí nová data tabulky nebo zadejte existující <xref:System.Data.DataTable> s vrácenými daty. Objekty TableAdapter lze také odeslat aktualizovaná data z aplikace zpět do databáze.  
  
 Objekty TableAdapter jsou vytvořeny pro vás při provádění jednoho z následujících akcí:  
  
- Spustit [Průvodce konfigurací zdroje dat](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) a vyberte buď **databáze** nebo **webová služba** typ zdroje dat.  
  
- Přetažení databázových objektů z [Průzkumníka serveru](http://msdn.microsoft.com/library/4ea29b3b-bbb2-45e4-9082-eaf635c41c4d) do **Návrhář Dataset**.  
  
  Můžete vytvořit nový TableAdapter a nakonfigurovat zdroj dat objektu TableAdapter přetáhněte z panelu nástrojů do prázdné oblasti v **Návrhář Dataset** povrchu.  
  
  Úvod do prvků TableAdapters, naleznete v tématu [vyplnění datové sady s použitím objektů TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md).  
  
  [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="use-the-tableadapter-configuration-wizard"></a>Použití Průvodce nastavením TableAdapter  
 Spustit **Průvodce nastavením TableAdapter** vytvořit nebo upravit objekty TableAdapter a jejich přidružené datové tabulky. Kliknutím pravým tlačítkem myši na něj v můžete nakonfigurovat stávajícího TableAdapter **Návrhář Dataset**.  
  
 ![raddata Průvodce konfigurací adaptéru tabulky](../data-tools/media/raddata-table-adapter-configuration-wizard.png "raddata Průvodce konfigurací adaptéru tabulky")  
  
 Pokud přetáhnete nového TableAdapter z panelu nástrojů při **Návrhář Dataset** je aktivní, výzev průvodce lze určit, které zdroj dat objektu TableAdapter se má připojit k a jaký druh příkazy by měl používat pro komunikaci se databáze, příkazy SQL nebo úložné procedury. Pokud konfigurujete, který je už přidružený zdroj dat objektu TableAdapter to neuvidíte.  
  
-   Použití **vytvořit metody k odeslání aktualizací přímo do databáze** možnost je ekvivalentní k nastavení `GenerateDBDirectMethods` vlastnost na hodnotu true. Možnost není dostupná, když původní příkaz jazyka SQL neposkytuje dostatek informací, nebo dotaz není možné aktualizovat dotaz. Tato situace může nastat, například v **připojení** dotazy a dotazy, které vracejí hodnotu single (skalární).  
  
-   Máte možnost vytvořit novou úložnou proceduru v podkladové databázi, pokud máte správná oprávnění pro databázi. Pokud tato oprávnění nemáte, to nebude možné.  
  
-   Můžete také spouštět existující uložené procedury pro **vyberte**, **vložit**, **aktualizace**, a **odstranit** příkazy TableAdapter. Uloženou proceduru, která je přiřazena **aktualizace** příkazu, například se spustí, když `TableAdapter.Update()` metoda je volána.  
  
     Mapování parametrů z vybranou úložnou proceduru na odpovídající sloupce v datové tabulce. Například, pokud uložená procedura přijme parametr s názvem `@CompanyName` , který předá do `CompanyName` sloupec v tabulce, nastaven **zdrojový sloupec** z `@CompanyName` parametr `CompanyName`.  
  
    > [!NOTE]
    >  Uložené procedury, která je přiřazena k příkazu SELECT se spustí zavoláním metody TableAdapter s názvy v dalším kroku v průvodci. Výchozí metodou je `Fill`, takže je kód, který se obvykle používá ke spuštění procedury SELECT `TableAdapter.Fill(tableName)`. Pokud změníte výchozí název z `Fill`, nahraďte `Fill` s názvem přiřadit a "TableAdapter" nahraďte skutečným názvem objektu TableAdapter (například `CustomersTableAdapter`).  
  
-   **Rozšířené možnosti** v průvodci umožňují vytvořit příkazy INSERT, UPDATE a DELETE založené na příkazu SELECT, který je definován na **generovat SQL příkazy** stránky. Použít optimistické řízení souběžnosti a určete, jestli Pokud chcete aktualizovat datovou tabulku po INSERT, UPDATE a příkazy jsou spustit.  
  
## <a name="configure-a-tableadapters-fill-method"></a>Konfigurace metody Fill objektu TableAdapter  
 Někdy můžete chtít změna schématu tabulky objektu TableAdapter. K tomuto účelu upravit primární objektu TableAdapter `Fill` metody. Objekty TableAdapter jsou vytvářeny s primární `Fill` metody, která definuje schématu přidružené tabulky dat. Primární `Fill` je založena na dotazu nebo uložené procedury, které jste zadali při původně nakonfigurován TableAdapter. Jedná se o první (nejvyššího) metodu pod tabulkou dat v návrháři datových sad.  
  
 ![TableAdapter s více dotazy](../data-tools/media/tableadapter.gif "TableAdapter")  
  
 Všechny změny provedené na objektu TableAdapter je hlavní `Fill` metoda se projeví ve schématu přidružené tabulky dat. Například odebráním sloupce z dotazu v hlavním `Fill` metoda také odeberete sloupec z přidružené tabulky dat. Kromě toho odebrání sloupce z hlavního `Fill` metoda odeberete sloupec z jakékoliv další dotazy pro tohoto objektu TableAdapter.  
  
 Průvodce konfigurací dotazu TableAdapter slouží k vytvoření a úprava další dotazy pro TableAdapter. Tyto další dotazy musí odpovídat schématu tabulky, pokud vracejí skalární hodnota.  Další dotazy mají názvy, které zadáte (třeba `CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, "Seattle")`.)  
  
#### <a name="to-start-the-tableadapter-query-configuration-wizard-with-a-new-query"></a>Spusťte Průvodce konfigurací dotazu TableAdapter s nový dotaz  
  
1.  Otevřete svou datovou sadu v **Návrhář Dataset**.  
  
2.  Pokud vytváříte nový dotaz, přetáhněte **dotazu** objektu z **datovou sadu** kartě **nástrojů** na <xref:System.Data.DataTable>, nebo vyberte **přidat dotaz**z místní nabídky objektu TableAdapter. Můžete také přetáhnout **dotazu** objektu na prázdnou oblast **Návrhář Dataset**, vytváří TableAdapter bez přidruženého <xref:System.Data.DataTable>. Tyto dotazy můžete pouze vrátí jednu hodnotu (skalární) nebo spuštění UPDATE, INSERT nebo odstranit příkazů na databázi.  
  
3.  Na **vyberte datové připojení** obrazovky, vyberte nebo vytvořte připojení, které budou používat dotaz.  
  
    > [!NOTE]
    >  Tato obrazovka se zobrazí, pouze když návrháře nelze určit správné připojení se má používat, nebo když jsou k dispozici žádná připojení.  
  
4.  Na **zvolit typ příkazu** obrazovky, vyberte z následujících metod načítání dat z databáze:  
  
    -   **Použití SQL** umožňuje typ příkazu SQL vyberte data z databáze.  
  
    -   **Vytvořit novou úložnou proceduru** umožňuje má průvodce vytvoříte nový uložené procedury (databáze) na základě zadaného příkazu SELECT.  
  
    -   **Použití stávajících uložených procedur** umožňuje spouštět stávající úložnou proceduru při spuštění dotazu.  
  
#### <a name="to-start-the-tableadapter-query-configuration-wizard-on-an-existing-query"></a>Spusťte Průvodce konfigurací dotazu TableAdapter na existující dotaz  
  
-   Pokud upravujete stávající dotazu TableAdapter, klikněte pravým tlačítkem na dotaz a klikněte na tlačítko **konfigurovat** z místní nabídky.  
  
    > [!NOTE]
    >  Pravým tlačítkem myši na hlavním dotazu objektu TableAdapter rekonfiguruje TableAdapter a <xref:System.Data.DataTable> schématu. Pravým tlačítkem myši dalšího dotazu pro TableAdapter, ale nakonfiguruje pouze vybraný dotaz. **Průvodce nastavením TableAdapter** změní konfiguraci definici třídy TableAdapter, zatímco Průvodce konfigurací dotazu TableAdapter změní konfiguraci vybraného dotazu.  
  
#### <a name="to-add-a-global--query-to-a-tableadapter"></a>Chcete-li přidat globální dotaz TableAdapter  
  
-   *Globální dotazy* jsou dotazy SQL, které vrací jedinou hodnotu (skalární) nebo žádnou hodnotu. Globální funkce obvykle provádění databázových operací, jako je vložení, aktualizace, odstraní. Také se agregují informace, jako je počet zákazníků v tabulce nebo celkové poplatky pro všechny položky v určitém pořadí.  
  
     Přidávání globálních dotazů přetažením **dotazu** objektu z **datovou sadu** karty **nástrojů** na prázdnou oblast **Návrhář Dataset**.  
  
-   Zadejte dotaz, který provede požadovanou úlohu, například `SELECT COUNT(*) AS CustomerCount FROM Customers`.  
  
    > [!NOTE]
    >  Přetahování **dotazu** objekt přímo **Návrhář Dataset** vytvoří metodu, která vrací pouze skalární hodnoty (single). Při dotazu nebo uložené procedury, které jste vybrali může vrátit více než jednu hodnotu, vrátí metoda, která se vytvoří pomocí Průvodce pouze jednu hodnotu. Dotaz může například vrátit první sloupec prvního řádku vracená data.  
  
## <a name="see-also"></a>Viz také  
 [Vyplnění datových sad pomocí objektů TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)

