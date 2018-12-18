---
title: 'Postupy: přiřazení uložených procedur za účelem aktualizace, vložení a odstranění (O R Designer) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e88224ab-ff61-4a3a-b6b8-6f3694546cac
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4f65af06a275dc50afafc70fd95c9b93d9bba458
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49232710"
---
# <a name="how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-or-designer"></a>Postupy: přiřazení uložených procedur za účelem aktualizace, vložení a odstranění (O/R Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Uložené procedury lze přidat do Návrháře relací objektů a spustit jako typický <xref:System.Data.Linq.DataContext> metody. Můžete je také použít k přepsání výchozí [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] chování za běhu, který provádí vložení, aktualizace a odstranění při uložení změn z tříd entit k databázi (například při volání <xref:System.Data.Linq.DataContext.SubmitChanges%2A> metoda).  
  
> [!NOTE]
>  Pokud uložená procedura vrátí hodnoty, které se mají odeslat klientovi (například. hodnoty vypočítané v uložené proceduře aplikace), vytvoření výstupních parametrů v uložených procedurách. Pokud nemůžete použít výstupních parametrů, zápis přepsání implementace částečné metody, aniž byste museli spoléhat na generovaný návrhářem relací objektů. Databáze vygenerovala hodnoty členů muset být nastaven na odpovídající hodnoty po úspěšném dokončení operace INSERT nebo UPDATE. Další informace najdete v tématu [odpovědnosti pro vývojáře v přepisuje výchozí chování](http://msdn.microsoft.com/library/c6909ddd-e053-46a8-980c-0e12a9797be1).  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] databáze vygenerovala popisovače hodnoty automaticky pro identitu (automatické zvyšování čísla), rowguidcol (GUID databáze vygenerovala) a sloupce časového razítka. Databáze vygenerovala hodnoty v jiných typech sloupců neočekávaně způsobí hodnotu null. Na návratové hodnoty generovaných databází, měli byste ručně nastavit <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> k `true` a <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> na jednu z následujících akcí: <xref:System.Data.Linq.Mapping.AutoSync>, <xref:System.Data.Linq.Mapping.AutoSync>, nebo <xref:System.Data.Linq.Mapping.AutoSync>.  
  
## <a name="configuring-the-update-behavior-of-an-entity-class"></a>Konfigurace chování aktualizace třídy Entity  
 Ve výchozím nastavení, logika aktualizace databáze (vložení, aktualizace a odstranění) se změnami, které byly provedené v datech v [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] tříd entit poskytuje [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] modulu runtime. Modul runtime vytvoří výchozí příkazy Insert, Update a Delete, které jsou založeny na schéma tabulky (sloupec a informacemi o primárním klíči). Pokud výchozí chování není žádoucí, můžete provádět konfiguraci chování aktualizace přiřazením konkrétní uložené procedury k provedení potřebné operace vložení, aktualizace, a odstraní požadované pro manipulaci s daty v tabulce. Můžete také provést generování výchozího chování není, například při mapování tříd entit na zobrazení. Nakonec můžete přepsat výchozí chování aktualizace databáze vyžaduje přístup k tabulce prostřednictvím uložené procedury.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-assign-stored-procedures-to-override-the-default-behavior-of-an-entity-class"></a>Přiřazení uložených procedur potlačit výchozí chování třídy entity  
  
1.  Otevřít **technologie LINQ to SQL** soubor v návrháři. (Poklikejte na soubor .dbml v **Průzkumníka řešení**.)  
  
2.  V **Průzkumníka serveru**/**Průzkumník databáze**, rozbalte **uložené procedury** a vyhledejte uložené procedury, které chcete použít pro vložení, aktualizace, a/nebo odstranit příkazy třídy entity.  
  
3.  Uložená procedura přetáhněte do Návrháře relací objektů.  
  
     Uložená procedura se přidá do podokna metody jako <xref:System.Data.Linq.DataContext> metody. Další informace najdete v tématu [metod DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).  
  
4.  Vyberte třídu entity, pro které chcete používat uložené procedury k provedení aktualizace.  
  
5.  V **vlastnosti** okna, vyberte příkaz k přepsání (**vložit**, **aktualizace**, nebo **odstranit**).  
  
6.  Klikněte na tlačítko se třemi tečkami (...) vedle slov **používat Runtime** otevřít **konfigurace chování** dialogové okno.  
  
7.  Vyberte **přizpůsobit**.  
  
8.  Vyberte požadovanou uloženou proceduru v **vlastní** seznamu.  
  
9. Prohlédněte si seznam **argumenty metody** a **vlastnosti třídy** ověřit, jestli **argumenty metody** mapují na odpovídající **vlastnosti třídy**. Mapování původní argumenty metody (Original_*název argumentu ArgumentName*) na původní vlastnosti (*PropertyName* (původní)) pro příkazy Update a Delete.  
  
    > [!NOTE]
    >  Ve výchozím nastavení argumenty metody mapovat na vlastnosti třídy při názvy odpovídají. Ke změně vlastnosti, kterou už neodpovídá názvy mezi tabulkou a třídu entity, budete možná muset vybrat možnost vlastnost ekvivalentní třídu pro mapování na Pokud návrháře nelze určit správné mapování.  
  
10. Klikněte na tlačítko **OK** nebo **použít**.  
  
    > [!NOTE]
    >  Můžete pokračovat v konfiguraci chování pro každou kombinaci třídy nebo chování, tak dlouho, dokud kliknete **použít** po každé změně. Pokud změníte třídy nebo chování před kliknutím na **použít**, dialogové okno upozornění poskytuje možnost použity všechny změny se zobrazí.  
  
     Pokud chcete vrátit k použití logiky výchozí modul runtime pro aktualizace, klikněte na tři tečky vedle Insert, Update, nebo odstraňte příkaz v **vlastnosti** okna a pak vyberte **použít modul runtime** v  **Konfigurace chování** dialogové okno.  
  
## <a name="see-also"></a>Viz také  
 [Nástroje LINQ to SQL v sadě Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Návod: Vytvoření třídy LINQ to SQL (Návrhář O-R)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [Návod: Vytvoření uložené procedury aktualizace pro tabulku zákazníků Northwind](../data-tools/walkthrough-creating-update-stored-procedures-for-the-northwind-customers-table.md)   
 [Technologie LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Operace vložení, aktualizace a odstranění](http://msdn.microsoft.com/library/26a43a4f-83c9-4732-806d-bb23aad0ff6b)

