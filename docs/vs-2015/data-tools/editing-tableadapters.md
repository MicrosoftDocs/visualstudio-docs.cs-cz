---
title: TableAdapters – úpravy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.datasource.dbtablefunctionwizard
- vs.datasource.datacomponentquerywizard
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], data component queries
- data [Visual Studio], TableAdapters
- TableAdapter Query Configuration Wizard
- data [Visual Studio], table adapter queries
ms.assetid: 8c06b306-24d0-4521-948d-07e3b7badd95
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: b242f8154f31391d168f2a41bfd00c01f037d87e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49877644"
---
# <a name="editing-tableadapters"></a>TableAdapters – úpravy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Někdy můžete chtít změna schématu tabulky adaptéru. K tomuto účelu upravit primární adaptéru `Fill` metody. Objekty TableAdapter jsou vytvářeny pomocí hlavního `Fill` metody, která definuje schématu přidružené tabulky dat. Hlavní `Fill` je založena na dotazu nebo uložené procedury jste zadali při původně nakonfigurován TableAdapter; je první – metoda (nejvyššího) v tabulce dat na [vytváření a úpravy typované datové sady](../data-tools/creating-and-editing-typed-datasets.md).  
  
 ![TableAdapter s více dotazy](../data-tools/media/tableadapter.gif "TableAdapter")  
  
 Všechny změny provedené na objektu TableAdapter je hlavní `Fill` metoda se projeví ve schématu přidružené tabulky dat. Například odebráním sloupce z dotazu v hlavním `Fill` metoda také odeberete sloupec z přidružené tabulky dat. Kromě toho odebrání sloupce z hlavního `Fill` metoda odeberete sloupec z jakékoliv další dotazy pro tohoto objektu TableAdapter.  
  
 Můžete použít **Průvodce nastavením dotazu TableAdapter** můžete vytvořit a upravit další dotazy pro TableAdapter. Tyto další dotazy musí odpovídat schématu tabulky, pokud vracejí skalární hodnota.  Další dotazy obsahovat název, který zadáte (třeba `CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, "Seattle")`.)  
  
#### <a name="to-start-the-tableadapter-query-configuration-wizard-with-a-new-query"></a>Spusťte Průvodce konfigurací dotazu TableAdapter s nový dotaz  
  
1.  Otevřete svou datovou sadu v **Návrhář Dataset**.  
  
2.  Pokud vytváříte nový dotaz, přetáhněte **dotazu** objektu z **datovou sadu** kartě **nástrojů** na <xref:System.Data.DataTable>, nebo vyberte **přidat dotaz**z místní nabídky objektu TableAdapter. Můžete také přetáhnout **dotazu** objektu na prázdnou oblast **Návrhář Dataset**, vytváří TableAdapter bez přidruženého <xref:System.Data.DataTable>. Tyto dotazy jsou omezené na vrácení jedné hodnoty (skalární) nebo provedení UPDATE, INSERT nebo odstranění příkazů na databázi. Další informace najdete v tématu [postupy: přidání globálních dotazů do TableAdapter](../data-tools/how-to-add-global-queries-to-a-tableadapter.md).  
  
3.  Na **vyberte datové připojení** stránce vyberte nebo vytvořte připojení dotazu bude použít.  
  
    > [!NOTE]
    >  Tato stránka se zobrazí, pouze když návrháře nelze určit správné připojení se má používat, nebo když jsou k dispozici žádná připojení.  
  
4.  Na **zvolit typ příkazu** stránky, vyberte z následujících metod načítání dat z databáze:  
  
    -   **Použití SQL** umožňuje zadat příkaz jazyka SQL k výběru data z databáze.  
  
    -   **Vytvořit novou úložnou proceduru** – tuto možnost má průvodce vytvořit nové uložené procedury (databáze) na základě zadaného příkazu SELECT.  
  
    -   **Použití stávajících uložených procedur** – tuto možnost použijte ke spuštění stávající úložnou proceduru při spuštění dotazu.  
  
#### <a name="to-start-the-tableadapter-query-configuration-wizard-on-an-existing-query"></a>Spusťte Průvodce konfigurací dotazu TableAdapter na existující dotaz  
  
-   Pokud upravujete stávající dotazu TableAdapter, klikněte pravým tlačítkem na dotaz a zvolte **konfigurovat** z místní nabídky.  
  
    > [!NOTE]
    >  Pravým tlačítkem myši na hlavním dotazu objektu TableAdapter rekonfiguruje TableAdapter a <xref:System.Data.DataTable> schématu, že kliknete pravým tlačítkem Další dotazu pro TableAdapter pouze nakonfiguruje vybraného dotazu. **Průvodce nastavením TableAdapter** změní konfiguraci definici třídy TableAdapter; **Průvodce nastavením dotazu TableAdapter** změní konfiguraci vybraného dotazu.  
  
## <a name="running-the-wizard"></a>Spuštění průvodce  
 Dotazy na, přetáhněte **Návrhář Dataset**, nebo nakonfigurovat existujících dotazů (uvedené pod první dotaz jakýkoli dotaz).  
  
 První dotaz v objektu TableAdapter je hlavním dotazem objektu TableAdapter. Úpravy tohoto hlavního dotazu otevře **Průvodce nastavením TableAdapter** a upravovat schéma tabulky dat objektu TableAdapter. Všechny dotazy, které jsou uvedené níže hlavního dotazu jsou další dotazy a budou nakonfigurováni s použitím **Průvodce nastavením dotazu TableAdapter**. Další informace o spuštění průvodce, naleznete v tématu [postupy: spuštění Průvodce konfigurací dotazu TableAdapter](http://msdn.microsoft.com/library/fc7b468e-3417-48a4-a8aa-cace8f99c24a).  
  
## <a name="choose-your-data-connection"></a>Vyberte datové připojení  
 Vyberte existující připojení ze seznamu připojení, nebo klikněte na tlačítko **nové připojení** vytvořit připojení k vaší databázi.  
  
 Po dokončení **vlastnosti připojení** dialogovém okně **podrobnosti připojení** oblasti se zobrazí jen pro čtení informací o vybraného zprostředkovatele, stejně jako připojovací řetězec.  
  
## <a name="save-the-connection-string-to-the-application-configuration-file"></a>Uložit připojovací řetězec do konfiguračního souboru aplikace  
 Zvolte **Ano, uložit připojení jako** k uložení připojovacího řetězce v konfiguračním souboru aplikace. Zadejte název připojení, nebo použít zadaný výchozí název.  
  
 Ukládání připojovacích řetězců v konfiguračním souboru aplikace zjednodušuje proces údržby aplikace, pokud se změní připojení k databázi. V případě změn v připojení k databázi můžete upravit připojovací řetězec do konfiguračního souboru aplikace. Díky tomu není nutné upravovat zdrojový kód a zkompilovat aplikaci znovu. Informace o úpravách připojovacího řetězce v konfiguračním souboru aplikace, najdete v tématu [postupy: uložení a úpravy připojovacích řetězců](~/E:/Repos/visualstudio-docs-pr/docs/data-tools/how-to-save-and-edit-connection-strings.md).  
  
> [!IMPORTANT]
>  Informace jsou uloženy v konfiguračním souboru aplikace jako prostý text. Chcete-li omezit riziko neoprávněného přístupu k citlivým údajům, je šifrování dat. Další informace najdete v tématu [šifrování a dešifrování dat](http://msdn.microsoft.com/en-us/22812ae8-e082-4eb1-a29b-21b6ee00c6b5).  
  
## <a name="use-sql-statements"></a>Použití příkazů jazyka SQL  
 Tato část vysvětluje, jak dokončit **Průvodce nastavením dotazu TableAdapter** při výběru **použít SQL příkazy** možnost.  
  
## <a name="choose-a-query-type"></a>Zvolit typ dotazu  
 Průvodce vytvoří několik typů dotazů v závislosti na požadavcích vaší aplikace. Můžete také vybrat dotazy, které vrací řádky dat (tabulku dat) nebo vyberte dotazy, který návratový skalární hodnota (jednu hodnotu jako `Count` nebo `Sum`).  
  
 Na **zvolit typ dotazu** stránky, vyberte typ dotaz, který vytvoří ze seznamu dostupných dotazů.  
  
> [!NOTE]
>  Vytvoření příkazu INSERT, UPDATE nebo DELETE nenahrazuje příkazy objektu TableAdapter, které se používají při volání objektu TableAdapter `Update` metody. Například výběrem aktualizace jako typ dotazu se vytvoří nový dotaz s názvem, který zadáte v průvodci později. Spusťte tento dotaz. po zavolání metody s názvem objektu TableAdapter. Volání objektu TableAdapter `Update` metoda provede příkazy vytvořené při konfiguraci původního objektu TableAdapter.  
  
## <a name="specify-a-sql-query-type-statement"></a>Zadejte SQL \<typ dotazu > – příkaz  
 Na **zadat příkaz jazyka SQL** stránky, zadejte příkaz jazyka SQL k provedení při volání metody dotazu.  
  
> [!TIP]
>  Průvodce poskytuje přístup k **Tvůrce dotazů**, vizuální nástroj pro vytváření příkazů jazyka SQL. Pokud chcete soubor otevřít, klikněte na tlačítko **Tvůrce dotazů** tlačítko.  
  
## <a name="choose-methods-to-generate"></a>Zvolit metody pro generování  
 Tato stránka poskytuje možnosti výběru, kterou metodu průvodce vygeneruje pro dotaz.  
  
 **Naplnit DataTable**  
 Vytvoří metodu pro vyplnění tabulky dat. Název tabulky dat předat jako parametr při volání této metody k vyplnění tabulky dat s vrácenými daty.  
  
 Volitelně můžete změnit výchozí název v **název metody** pole. Poskytují smysluplný název může být užitečné při práci s Tento dotaz v kódu.  
  
 **Vrátit tabulku DataTable**  
 Vytvoří metodu vracející tabulku plného data. V některých aplikací může být více třeba vrátit tabulku plného dat na rozdíl od vyplnění existující data tabulky s daty.  
  
 Volitelně můžete změnit výchozí název v **název metody** pole.  
  
## <a name="choose-function-name"></a>Zvolit název funkce  
 Zadejte název funkce. Vytváření dotazu TableAdapter přidá metodu do TableAdapter s názvem tady. Volejte tuto metodu za účelem provedení dotazu. Poskytují smysluplný název je užitečné, pokud pracujete s Tento dotaz v kódu.  
  
> [!NOTE]
>  Při vytvoření nových uložených procedur, zobrazí se výzva pro dva názvy. Křestní jméno je název uložené procedury v databázi vytvořena, druhý název je název metody na objektu TableAdapter, který se spustí při volání uložené procedury.  
  
## <a name="create-new-stored-procedures"></a>Vytvořit nové uložené procedury  
 Tato část vysvětluje, jak dokončit **Průvodce nastavením dotazu TableAdapter** při výběru **vytvořit nové uložené procedury** možnost.  
  
1. V **generovat uložené procedury** stránky, zadejte příkaz jazyka SQL k provedení při volání uložené procedury.  
  
   > [!NOTE]
   >  Průvodce poskytuje přístup k **Tvůrce dotazů**, vizuální nástroj pro vytváření příkazů jazyka SQL. Pokud chcete soubor otevřít, klikněte na tlačítko **Tvůrce dotazů** tlačítko.  
  
2. V **vytvořit úložné procedury** stránce, postupujte takto:  
  
   1. Zadejte název pro novou úložnou proceduru.  
  
   2. Určete, zda chcete vytvořit uloženou proceduru v podkladové databázi.  
  
      > [!NOTE]
      >  Možnost vytvořit uloženou proceduru v databázi se určuje podle nastavení zabezpečení pro konkrétní databáze.  
  
      **Zobrazit výsledky průvodce** stránka zobrazuje výsledky vytvoření dotazu TableAdapter. Pokud průvodce zjistí problémy, tato stránka obsahuje informace o této chybě.  
  
## <a name="use-existing-stored-procedures"></a>Použití stávajících uložených procedur  
 Tato část vysvětluje, jak dokončit **Průvodce nastavením dotazu TableAdapter** při výběru **použití stávajících uložených procedur** možnost.  
  
1.  Vyberte stávající úložnou proceduru z rozevíracího seznamu na **zvolit stávající úložnou proceduru** stránky průvodce.  
  
     **Parametry** a **výsledky** pro vybrané uložené procedury jsou zobrazeny pro odkaz.  
  
2.  Klikněte na tlačítko **Další**.  
  
## <a name="choose-the-shape-of-data-returned-by-the-stored-procedure"></a>Zvolit tvar dat vrácených uložené procedury  
 Typ dat vrácených vybranou úložnou proceduru určuje způsob, jak vytvořit průvodce metody TableAdapter.  
  
 Vyberte typ dat vrácených tímto dotazem.  
  
-   Výběr **tabulková data** otevře **zvolte metody k vytvoření** stránky (popsanou výš na tuto stránku nápovědy), což vám umožní určit typy metod, názvy metod a podpora stránkování, který se má vytvořit.  
  
-   Výběr **jednu hodnotu** vytvoří typová metoda, která vrátí jednu hodnotu. Tato volba otevře **zvolte název funkce** stránky (popsanou výš na tuto stránku nápovědy).  
  
-   Výběr **žádná hodnota** vytvoří typová metoda, která provede uloženou proceduru a očekává, že žádná data se mají vrátit. Tato volba otevře **zvolte název funkce** stránky (popsanou výš na tuto stránku nápovědy).  
  
## <a name="view-wizards-results"></a>Zobrazit výsledky průvodce  
 **Zobrazit výsledky průvodce** stránka zobrazuje výsledky vytvoření dotazu TableAdapter. Pokud průvodce zjistí problémy, zobrazí se podrobnosti na této stránce.  
  
## <a name="see-also"></a>Viz také  
 [TableAdapter – přehled](../data-tools/tableadapter-overview.md)   
 [Postupy: upravování dotazů TableAdapter](../data-tools/how-to-edit-tableadapter-queries.md)   
 [Návody k datům](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Vytvoření vazby ovládacích prvků Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Přehled datových aplikacích v sadě Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Připojování k datům v sadě Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Příprava aplikace pro příjem dat](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Načítají se Data do vaší aplikace](../data-tools/fetching-data-into-your-application.md)   
 [Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Úpravy dat v aplikaci](../data-tools/editing-data-in-your-application.md)   
 [Ověřování dat](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Ukládání dat](../data-tools/saving-data.md)