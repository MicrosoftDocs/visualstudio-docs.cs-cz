---
title: Zpracování výjimky souběžnosti | Dokumentace Microsoftu
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
- concurrency control, exceptions
- datasets [Visual Basic], errors
- exception handling, concurrency issues
- data concurrency, walkthroughs
- updating datasets, errors
- concurrency control, walkthroughs
ms.assetid: 73ee9759-0a90-48a9-bf7b-9d6fc17bff93
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a3141f2480aabc2ce6aa7b10f99991fc5cba0d05
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50220414"
---
# <a name="handle-a-concurrency-exception"></a>Zpracování výjimky souběžnosti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Výjimky souběžnosti (<xref:System.Data.DBConcurrencyException>) jsou vyvolány, když dva uživatelé pokoušejí změnit na stejná data v databázi ve stejnou dobu. V tomto návodu vytvoříte aplikaci Windows, která ukazuje, jak zachytit <xref:System.Data.DBConcurrencyException>, vyhledejte řádek, který způsobil chybu a další strategie, jak ji zpracovat.  
  
 Tento názorný postup vás provede následující postup:  
  
1.  Vytvořte nový **aplikace Windows** projektu.  
  
2.  Vytvořit novou datovou sadu založenou na Northwind `Customers` tabulky.  
  
3.  Vytvořit formulář s <xref:System.Windows.Forms.DataGridView> zobrazit data.  
  
4.  Vyplnit data z datové sady `Customers` tabulky v databázi Northwind.  
  
5.  Použití [nástroje Visual Database Tools](http://msdn.microsoft.com/en-us/6b145922-2f00-47db-befc-bf351b4809a1) v sadě Visual Studio pro přímý přístup k `Customers` tabulka dat a změňte záznam.  
  
6.  Změnit stejného záznamu na jinou hodnotu, aktualizovat datovou sadu a pokusí se zapsat změny do databáze, což vede k chybě souběžnosti vyvolaných.  
  
7.  Zachytávat chyby a pak zobrazit různé verze záznamu, které uživateli umožňují určit, zda chcete pokračovat a aktualizaci databáze, nebo také aktualizaci zrušit.  
  
## <a name="prerequisites"></a>Požadavky  
 Pokud chcete dokončit tento návod, potřebujete:  
  
-   Přístup k ukázkové databázi Northwind pomocí oprávnění k provedení aktualizace. Další informace najdete v tématu [postupy: Instalace ukázkových databází](../data-tools/how-to-install-sample-databases.md).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které se zobrazí může lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici, kterou používáte. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="create-a-new-project"></a>Vytvoření nového projektu  
 Začnete vašeho návodu tak, že vytvoříte novou aplikaci pro Windows.  
  
#### <a name="to-create-a-new-windows-application-project"></a>Chcete-li vytvořit nový projekt aplikace Windows  
  
1.  Na **souboru** nabídky, vytvořte nový projekt.  
  
2.  V **typy projektů** podokně, vyberte programovací jazyk.  
  
3.  V **šablony** vyberte **aplikace Windows**.  
  
4.  Pojmenujte projekt `ConcurrencyWalkthrough`a pak vyberte **OK**.  
  
     Visual Studio přidá projekt do **Průzkumníka řešení** a zobrazí nový formulář v návrháři.  
  
## <a name="create-the-northwind-dataset"></a>Vytvořte datovou sadu Northwind  
 V této části vytvoříte datovou sadu s názvem `NorthwindDataSet`.  
  
#### <a name="to-create-the-northwinddataset"></a>Chcete-li vytvořit NorthwindDataSet  
  
1.  Na **Data** nabídce zvolte **zdroje přidat nová Data**.  
  
     [Průvodce konfigurací zdroje dat](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) otevře.  
  
2.  Na **zvolte typ zdroje dat**obrazovky, vyberte **databáze**.  
  
3.  Vyberte připojení ze seznamu dostupných připojení k ukázkové databázi Northwind. Pokud připojení není k dispozici v seznamu připojení, vyberte**nové připojení**  
  
    > [!NOTE]
    >  Pokud se připojujete k místní databázový soubor, vyberte **ne** když se zobrazí výzva, pokud byste chtěli přidat soubor do projektu.  
  
4.  Na **uložit připojovací řetězec do konfiguračního souboru aplikace**obrazovky, vyberte **Další**.  
  
5.  Rozbalte **tabulky** uzel a vyberte `Customers` tabulky. Výchozí název pro tuto datovou sadu by měl být `NorthwindDataSet`.  
  
6.  Vyberte **Dokončit** na datovou sadu přidat do projektu.  
  
## <a name="create-a-data-bound-datagridview-control"></a>Vytvoření ovládacího prvku DataGridView vázaný na data  
 V této části vytvoříte <xref:System.Windows.Forms.DataGridView> přetažením **zákazníkům** položky **zdroje dat** okna do formuláře Windows.  
  
#### <a name="to-create-a-datagridview-control-that-is-bound-to-the-customers-table"></a>Vytvoření ovládacího prvku DataGridView, který je vázán k tabulce Zákazníci  
  
1.  Na **Data** nabídce zvolte **zobrazit zdroje dat** otevřít **okna zdroje dat**.  
  
2.  V **zdroje dat** okna, rozbalte **NorthwindDataSet** uzlu a pak vyberte **zákazníkům** tabulky.  
  
3.  Vyberte šipku dolů na uzel tabulky a pak vyberte **DataGridView** v rozevíracím seznamu.  
  
4.  Přetáhněte tabulku na prázdnou oblast formuláře.  
  
     A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `CustomersDataGridView` a <xref:System.Windows.Forms.BindingNavigator> s názvem `CustomersBindingNavigator` jsou přidány do formuláře, který je vázán <xref:System.Windows.Forms.BindingSource>. Je to, v důsledku vázán na `Customers` tabulku v `NorthwindDataSet`.  
  
## <a name="test-the-form"></a>Testovací formulář  
 Teď můžete otestovat formulář, abyste měli jistotu, že se chová podle očekávání do této chvíle.  
  
#### <a name="to-test-the-form"></a>K otestování formuláře  
  
1.  Vyberte **F5** ke spuštění aplikace  
  
     Formulář se zobrazí s <xref:System.Windows.Forms.DataGridView> ovládacím prvkem, který je naplněný daty z `Customers` tabulky.  
  
2.  Na **ladění** nabídce vyberte možnost**Zastavit ladění**.  
  
## <a name="handleconcurrency-errors"></a>Handleconcurrency chyby  
 Způsob zpracování chyb je závisí na konkrétní obchodní pravidla, kterými se řídí vaše aplikace. V tomto návodu používáme následující strategie s ukázkovým jak tohandle došlo k chybě souběžnosti.  
  
 Applicationpresents uživatele s tři verze záznamu:  
  
- Aktuální záznam v databázi  
  
- Původní záznam, který je načten do datové sady  
  
- Navrhovaných změn v datové sadě  
  
  Uživatel je pak možné přepsat databázi navrhovaných verzí, nebo také aktualizaci zrušit a aktualizovat datovou sadu s novými hodnotami z databáze.  
  
#### <a name="to-enable-the-handling-of-concurrency-errors"></a>Povolit zpracování chyb souběžnosti  
  
1.  Vytvoření obslužné rutiny vlastních chyb.  
  
2.  Zobrazit možnosti pro uživatele.  
  
3.  Zpracování odpovědi uživatele.  
  
4.  Znovu odeslal aktualizaci nebo obnovit data v datové sadě.  
  
### <a name="addcode-to-handle-the-concurrency-exception"></a>Addcode ke zpracování výjimky souběžnosti  
 Když se pokusíte provést aktualizace a získá vyvolána výjimka, obvykle chcete udělat něco s informacemi, které poskytuje vyvolanou výjimku.  
  
 V této části přidáte kód, který se pokouší aktualizovat databázi. Můžete také zpracována <xref:System.Data.DBConcurrencyException> , která může získat vyvolána, stejně jako všechny ostatní výjimky.  
  
> [!NOTE]
>  `CreateMessage` a `ProcessDialogResults` metody se přidají později v tomto názorném postupu.  
  
##### <a name="to-add-error-handling-for-the-concurrency-error"></a>Přidání zpracování chyb pro došlo k chybě souběžnosti  
  
1.  Přidejte následující kód níže `Form1_Load` metody:  
  
     [!code-csharp[VbRaddataConcurrency#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#1)]
     [!code-vb[VbRaddataConcurrency#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#1)]  
  
2.  Nahradit `CustomersBindingNavigatorSaveItem_Click` metoda se má volat `UpdateDatabase` metodu tak, aby vypadala takto:  
  
     [!code-csharp[VbRaddataConcurrency#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#2)]
     [!code-vb[VbRaddataConcurrency#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#2)]  
  
### <a name="displaychoices-to-the-user"></a>Displaychoices uživateli  
 Kód, který jste právě napsal volání `CreateMessage` postupem zobrazíte informace o chybě pro uživatele. V tomto návodu použijete okno se zprávou k zobrazit různé verze záznamu pro uživatele. To umožňuje uživateli zvolit, jestli se má přepsat záznam změny nebo zrušit úpravy. Když uživatel vybere možnost (klikne na tlačítko) v okně se zprávou, je předán odpovědi `ProcessDialogResult` metody.  
  
##### <a name="to-create-the-message-to-display-to-the-user"></a>Chcete-li vytvořit zprávu zobrazit pro uživatele  
  
-   Vytvoření zprávy přidáním následujícího kódu **Editor kódu**. Tento kód níže zadejte `UpdateDatabase` metody.  
  
     [!code-csharp[VbRaddataConcurrency#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#4)]
     [!code-vb[VbRaddataConcurrency#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#4)]  
  
### <a name="process-the-users-response"></a>Zpracovat odpověď uživatele  
 Musíte také kód pro zpracování odpověď uživatele do pole zpráva. Možnostmi jsou buď přepsat aktuální záznam v databázi navrhované změny, nebo zahodit prováděné změny v místní a aktualizovat datovou tabulku s záznam, který je aktuálně v databázi. Pokud uživatel vybere Ano, <xref:System.Data.DataTable.Merge%2A> metoda je volána *preserveChanges* argument nastaven na `true`. To způsobí, že pokus o aktualizace bude úspěšné, protože původní verze záznamu nyní odpovídá záznam v databázi.  
  
##### <a name="to-process-the-user-input-from-the-message-box"></a>Uživatel zpracovat vstup z okna se zprávou  
  
-   Přidejte následující kód za kód, který byl přidán v předchozí části.  
  
     [!code-csharp[VbRaddataConcurrency#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#3)]
     [!code-vb[VbRaddataConcurrency#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#3)]  
  
## <a name="test-the-form"></a>Testovací formulář  
 Teď můžete otestovat formulář, abyste měli jistotu, že se chová podle očekávání. Pro simulaci narušení souběžného zpracování, budete muset změnit data v databázi po vyplnění NorthwindDataSet.  
  
#### <a name="to-test-the-form"></a>K otestování formuláře  
  
1.  Vyberte **F5** ke spuštění aplikace.  
  
2.  Po zobrazení formuláře necháte spuštěné a přejděte do integrovaného vývojového prostředí sady Visual Studio.  
  
3.  Na **zobrazení** nabídce zvolte **Průzkumníka serveru**.  
  
4.  V **Průzkumníka serveru**, rozbalte připojení, vaše aplikace používá a potom rozbalte **tabulky** uzlu.  
  
5.  Klikněte pravým tlačítkem myši **zákazníkům** tabulku a pak vyberte **zobrazit Data tabulky**.  
  
6.  V prvním záznamu (`ALFKI`) změnit `ContactName` k `Maria Anders2`.  
  
    > [!NOTE]
    >  Přejděte na jiný řádek pro potvrzení změn.  
  
7.  Přepněte `ConcurrencyWalkthrough`běží formuláře.  
  
8.  V první záznam ve formuláři (`ALFKI`), změňte`ContactName` k `Maria Anders1`.  
  
9. Vyberte **Uložit** tlačítko.  
  
     Došlo k chybě souběžnosti se vyvolá a zobrazí se okno se zprávou.  
  
10. Výběr **ne** zruší aktualizace a aktualizace datové sady s hodnotami, které jsou aktuálně v databázi. Výběr **Ano** navrhovanou hodnotu zapisuje do databáze.
  
## <a name="see-also"></a>Viz také

- [Ukládání dat zpět do databáze](../data-tools/save-data-back-to-the-database.md)