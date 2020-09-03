---
title: Zpracování výjimky souběžnosti | Microsoft Docs
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
- concurrency control, exceptions
- datasets [Visual Basic], errors
- exception handling, concurrency issues
- data concurrency, walkthroughs
- updating datasets, errors
- concurrency control, walkthroughs
ms.assetid: 73ee9759-0a90-48a9-bf7b-9d6fc17bff93
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1b3f9bdaf5107f805100b938212128d42c0263dd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670040"
---
# <a name="handle-a-concurrency-exception"></a>Zpracování výjimky souběžnosti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Výjimky souběžnosti ( <xref:System.Data.DBConcurrencyException> ) jsou vyvolány, když se dva uživatelé pokusí změnit stejná data v databázi ve stejnou chvíli. V tomto návodu vytvoříte aplikaci pro Windows, která ukazuje, jak zachytit <xref:System.Data.DBConcurrencyException> , najít řádek, který způsobil chybu, a Naučte se, jak ho zpracovat.

 Tento návod vás provede následujícím procesem:

1. Vytvořte nový projekt **aplikace pro Windows** .

2. Vytvořte novou datovou sadu založenou na `Customers` tabulce Northwind.

3. Vytvořte formulář s a <xref:System.Windows.Forms.DataGridView> zobrazíte data.

4. Naplňte datovou sadu daty z `Customers` tabulky v databázi Northwind.

5. Pomocí [nástrojů Visual Database Tools](https://msdn.microsoft.com/6b145922-2f00-47db-befc-bf351b4809a1) v aplikaci Visual Studio získáte přímý přístup k `Customers` tabulce dat a změně záznamu.

6. Změňte stejný záznam na jinou hodnotu, aktualizujte datovou sadu a pokuste se provést zápis změn do databáze, což vede k tomu, že dojde k chybě souběžnosti.

7. Zachyťte chybu, potom zobrazte různé verze záznamu a umožněte uživateli určit, zda chcete pokračovat a aktualizovat databázi nebo zrušit aktualizaci.

## <a name="prerequisites"></a>Požadavky
 Aby bylo možné dokončit tento návod, potřebujete:

- Přístup k ukázkové databázi Northwind s oprávněním k provádění aktualizací.

> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici, kterou používáte. Chcete-li změnit nastavení, v nabídce **nástroje** klikněte na položku **Nastavení importu a exportu** . Další informace naleznete v tématu [přizpůsobení nastavení vývoje v aplikaci Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="create-a-new-project"></a>Vytvoření nového projektu
 Svůj návod zahájíte vytvořením nové aplikace pro Windows.

#### <a name="to-create-a-new-windows-application-project"></a>Vytvoření nového projektu aplikace pro systém Windows

1. V nabídce **soubor** vytvořte nový projekt.

2. V podokně **typy projektů** vyberte programovací jazyk.

3. V podokně **šablony** vyberte možnost **aplikace systému Windows**.

4. Pojmenujte projekt `ConcurrencyWalkthrough` a pak vyberte **OK**.

     Visual Studio přidá projekt do **Průzkumník řešení** a v Návrháři zobrazí nový formulář.

## <a name="create-the-northwind-dataset"></a>Vytvoření datové sady Northwind
 V této části vytvoříte datovou sadu s názvem `NorthwindDataSet` .

#### <a name="to-create-the-northwinddataset"></a>Vytvoření NorthwindDataSet

1. V nabídce **data** klikněte na tlačítko **Přidat nový zdroj dat**.

     Otevře se [Průvodce konfigurací zdroje dat](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) .

2. Na obrazovce **Vybrat typ zdroje dat**vyberte **databáze**.

3. Vyberte připojení k ukázkové databázi Northwind ze seznamu dostupných připojení. Pokud připojení není v seznamu připojení k dispozici, vyberte**nové připojení** .

    > [!NOTE]
    > Pokud se připojujete k místnímu databázovému souboru, po zobrazení výzvy vyberte možnost **ne** , pokud chcete soubor přidat do projektu.

4. Na obrazovce **Uložit připojovací řetězec do konfiguračního souboru aplikace**vyberte **Další**.

5. Rozbalte uzel **tabulky** a vyberte `Customers` tabulku. Výchozí název pro datovou sadu by měl být `NorthwindDataSet` .

6. Vyberte **Dokončit** a přidejte datovou sadu do projektu.

## <a name="create-a-data-bound-datagridview-control"></a>Vytvoření ovládacího prvku DataGridView vázaného na data
 V této části vytvoříte <xref:System.Windows.Forms.DataGridView> přetažením položky **Customers (zákazníci** ) z okna **zdroje dat** do formuláře Windows.

#### <a name="to-create-a-datagridview-control-that-is-bound-to-the-customers-table"></a>Vytvoření ovládacího prvku DataGridView, který je svázán s tabulkou Customers

1. V nabídce **data** vyberte **Zobrazit zdroje dat** a otevřete tak **okno zdroje dat**.

2. V okně **zdroje dat** rozbalte uzel **NorthwindDataSet** a pak vyberte tabulku **zákazníci** .

3. Vyberte šipku dolů v uzlu tabulka a pak v rozevíracím seznamu vyberte **ovládací prvek DataGridView** .

4. Přetáhněte tabulku do prázdné oblasti formuláře.

     <xref:System.Windows.Forms.DataGridView>Ovládací prvek s názvem `CustomersDataGridView` a <xref:System.Windows.Forms.BindingNavigator> pojmenovaný `CustomersBindingNavigator` jsou přidány do formuláře vázaného na <xref:System.Windows.Forms.BindingSource> . To je v, je zapnuto svázání s `Customers` tabulkou v `NorthwindDataSet` .

## <a name="test-the-form"></a>Testování formuláře
 Nyní můžete testovat formulář, abyste se ujistili, že se chová podle očekávání do tohoto bodu.

#### <a name="to-test-the-form"></a>Testování formuláře

1. Vyberte **F5** pro spuštění aplikace.

     Formulář se zobrazí s <xref:System.Windows.Forms.DataGridView> ovládacím prvkem, který je vyplněn daty z `Customers` tabulky.

2. V nabídce **ladění** vyberte**Zastavit ladění**.

## <a name="handleconcurrency-errors"></a>Handleconcurrency chyby
 Způsob zpracování chyb závisí na konkrétním obchodním pravidla, která řídí vaši aplikaci. V tomto návodu použijeme následující strategii jako příklad, jak tohandle chybu souběžnosti.

 Applicationpresents uživatele se třemi verzemi záznamu:

- Aktuální záznam v databázi

- Původní záznam načtený do datové sady

- Navrhované změny v datové sadě

  Uživatel pak může přepsat databázi pomocí navržené verze, nebo aktualizaci zrušit a obnovit datovou sadu o nové hodnoty z databáze.

#### <a name="to-enable-the-handling-of-concurrency-errors"></a>Povolení zpracování chyb souběžnosti

1. Vytvořte vlastní obslužnou rutinu chyb.

2. Umožňuje zobrazit volby pro uživatele.

3. Zpracujte reakci uživatele.

4. Znovu odešlete aktualizaci nebo obnovte data v datové sadě.

### <a name="addcode-to-handle-the-concurrency-exception"></a>AddCode pro zpracování výjimky souběžnosti
 Když se pokusíte provést aktualizaci a vyvolá se výjimka, obecně chcete něco udělat s informacemi, které jsou poskytovány vyvolanou výjimkou.

 V této části přidáte kód, který se pokusí aktualizovat databázi. Také se pořídí všechny <xref:System.Data.DBConcurrencyException> , které mohou být vyvolány, a všechny další výjimky.

> [!NOTE]
> `CreateMessage`Metody a `ProcessDialogResults` budou přidány později v tomto návodu.

##### <a name="to-add-error-handling-for-the-concurrency-error"></a>Přidání zpracování chyb pro chybu souběžnosti

1. Do metody přidejte následující kód `Form1_Load` :

     [!code-csharp[VbRaddataConcurrency#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#1)]
     [!code-vb[VbRaddataConcurrency#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#1)]

2. Nahraďte `CustomersBindingNavigatorSaveItem_Click` metodu pro volání `UpdateDatabase` metody, aby vypadala takto:

     [!code-csharp[VbRaddataConcurrency#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#2)]
     [!code-vb[VbRaddataConcurrency#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#2)]

### <a name="displaychoices-to-the-user"></a>Displaychoices uživateli
 Kód, který jste právě napsal, volá `CreateMessage` proceduru, která uživateli zobrazí informace o chybě. V tomto návodu použijete okno se zprávou k zobrazení různých verzí záznamu pro uživatele. To uživateli umožňuje zvolit, jestli se má záznam přepsat, nebo zrušit úpravy. Jakmile uživatel vybere možnost (klikne na tlačítko) v okně se zprávou, odpověď je předána `ProcessDialogResult` metodě.

##### <a name="to-create-the-message-to-display-to-the-user"></a>Vytvoření zprávy, která se zobrazí uživateli

- Vytvořte zprávu přidáním následujícího kódu do **editoru kódu**. Zadejte tento kód pod `UpdateDatabase` metodou.

     [!code-csharp[VbRaddataConcurrency#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#4)]
     [!code-vb[VbRaddataConcurrency#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#4)]

### <a name="process-the-users-response"></a>Zpracovat reakci uživatele
 Také potřebujete kód pro zpracování reakce uživatele na okno se zprávou. Možnosti jsou buď k přepsání aktuálního záznamu v databázi navrhovanou změnou, nebo k opuštění místních změn a aktualizaci datové tabulky záznamem, který je aktuálně v databázi. Pokud uživatel zvolí Ano, <xref:System.Data.DataTable.Merge%2A> Metoda je volána s argumentem *PreserveChanges* nastaveným na `true` . Tím dojde k úspěšnému pokusu o aktualizaci, protože původní verze záznamu nyní odpovídá záznamu v databázi.

##### <a name="to-process-the-user-input-from-the-message-box"></a>Zpracování vstupu uživatele z okna se zprávou

- Pod kód, který byl přidán v předchozí části, přidejte následující kód.

     [!code-csharp[VbRaddataConcurrency#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#3)]
     [!code-vb[VbRaddataConcurrency#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#3)]

## <a name="test-the-form"></a>Testování formuláře
 Nyní můžete testovat formulář, abyste se ujistili, že se chová podle očekávání. Chcete-li simulovat porušení souběžnosti, je nutné změnit data v databázi po vyplnění NorthwindDataSet.

#### <a name="to-test-the-form"></a>Testování formuláře

1. Pro spuštění aplikace vyberte **F5** .

2. Po zobrazení formuláře ponechte spuštěný a přepněte se do integrovaného vývojového prostředí (IDE) sady Visual Studio.

3. V nabídce **zobrazení** vyberte možnost **Průzkumník serveru**.

4. V **Průzkumník serveru**rozbalte připojení, které aplikace používá, a potom rozbalte uzel **tabulky** .

5. Klikněte pravým tlačítkem myši na tabulku **Customers** a potom vyberte možnost **Zobrazit data tabulky**.

6. V prvním záznamu ( `ALFKI` ) změňte `ContactName` na `Maria Anders2` .

    > [!NOTE]
    > Změnu potvrďte tak, že přejdete na jiný řádek.

7. Přepněte do `ConcurrencyWalkthrough` běžícího formuláře.

8. V prvním záznamu ve formuláři ( `ALFKI` ) přejděte `ContactName` na `Maria Anders1` .

9. Vyberte tlačítko **Uložit**.

     Je vyvolána chyba souběžnosti a zobrazí se okno se zprávou.

10. Když vyberete možnost **ne** , aktualizace se aktualizuje a aktualizuje datovou sadu hodnotami, které jsou aktuálně v databázi. Výběrem možnosti **Ano** zapíšete navrhovanou hodnotu do databáze.

## <a name="see-also"></a>Viz také

- [Ukládání dat zpět do databáze](../data-tools/save-data-back-to-the-database.md)