---
title: 'Postupy: přiřazení uložených procedur pro provádění aktualizací, vkládání a odstraňování (O-R Designer) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: e88224ab-ff61-4a3a-b6b8-6f3694546cac
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2054a55f0633d5d4add51fee2e933d9f4d829fcf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72609972"
---
# <a name="how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-or-designer"></a>Postupy: přiřazení uložených procedur pro provádění aktualizací, vkládání a odstraňování (Návrhář O/R)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uložené procedury lze přidat do návrháře O/R a spustit jako typické metody <xref:System.Data.Linq.DataContext>. Lze je také použít k přepsání výchozího [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] běhového chování, které provádí vložení, aktualizace a odstranění, když jsou změny uloženy z tříd entit do databáze (například při volání metody <xref:System.Data.Linq.DataContext.SubmitChanges%2A>).

> [!NOTE]
> Pokud uložená procedura vrátí hodnoty, které je třeba odeslat zpět klientovi (například hodnoty vypočtené v uložené proceduře), vytvořte výstupní parametry v uložených procedurách. Pokud nemůžete použít výstupní parametry, zapište implementaci částečné metody, nemusíte se spoléhat na přepsání vygenerovaná návrhářem O/R. Po úspěšném dokončení operací vložení nebo aktualizace musí být členové namapované na hodnoty generované databází nastaveny na příslušné hodnoty. Další informace najdete v tématu [zodpovědnosti vývojáře při přepisu výchozího chování](https://msdn.microsoft.com/library/c6909ddd-e053-46a8-980c-0e12a9797be1).

> [!NOTE]
> [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] zpracovává hodnoty generované databázemi automaticky pro sloupce identity (automatické zvýšení), ROWGUIDCOL (GUID generovaný identifikátor GUID) a časové razítko. Hodnoty generované databází v jiných typech sloupců neočekávaně způsobí hodnotu null. Chcete-li vrátit hodnoty generované databází, je třeba ručně nastavit <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> `true` a <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> na jednu z následujících možností: <xref:System.Data.Linq.Mapping.AutoSync>, <xref:System.Data.Linq.Mapping.AutoSync> nebo <xref:System.Data.Linq.Mapping.AutoSync>.

## <a name="configuring-the-update-behavior-of-an-entity-class"></a>Konfigurace chování aktualizace pro třídu entity
 Ve výchozím nastavení logika aktualizace databáze (vložení, aktualizace a odstranění) se změnami provedenými v datech v [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] třídy entit je poskytována modulem runtime [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]. Modul runtime vytvoří výchozí příkazy INSERT, Update a DELETE, které jsou založeny na schématu tabulky (informace o sloupci a primárním klíči). Pokud výchozí chování není žádoucí, můžete nakonfigurovat chování aktualizace přiřazením specifických uložených procedur pro provádění nezbytných vložení, aktualizací a odstranění potřebných k manipulaci s daty v tabulce. To lze provést také v případě, že se výchozí chování negeneruje, například když vaše třídy entit budou mapovány na zobrazení. Nakonec můžete přepsat výchozí chování aktualizace, když databáze vyžaduje přístup k tabulce prostřednictvím uložených procedur.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-assign-stored-procedures-to-override-the-default-behavior-of-an-entity-class"></a>Přiřazení uložených procedur pro přepsání výchozího chování třídy entity

1. Otevřete soubor **LINQ to SQL** v návrháři. (Poklikejte na soubor. dbml v **Průzkumník řešení**.)

2. V **Průzkumník serveru** /**Průzkumníku databáze**rozbalte **uložené procedury** a vyhledejte uložené procedury, které chcete použít pro příkazy INSERT, Update a Delete třídy entity.

3. Přetáhněte uloženou proceduru do návrháře O/R.

     Uložená procedura je přidána do podokna metody jako metoda <xref:System.Data.Linq.DataContext>. Další informace naleznete v tématu [metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

4. Vyberte třídu entity, pro kterou chcete použít uloženou proceduru pro provádění aktualizací.

5. V okně **vlastnosti** vyberte příkaz, který chcete přepsat (**Vložit**, **aktualizovat**nebo **Odstranit**).

6. Klikněte na tlačítko se třemi tečkami (...) vedle slov **použít modul runtime** k otevření dialogového okna **Konfigurovat chování** .

7. Vyberte **přizpůsobit**.

8. V seznamu **přizpůsobit** vyberte požadovanou uloženou proceduru.

9. Zkontrolujte seznam **argumentů metody** a **vlastností třídy** a ověřte, zda jsou **argumenty metody** namapovány na příslušné **vlastnosti třídy**. Namapujte argumenty původní metody (Original_*argumentu*) na původní vlastnosti (*PropertyName* (originál)) pro příkazy Update a DELETE.

    > [!NOTE]
    > Ve výchozím nastavení jsou argumenty metody mapovány na vlastnosti třídy, pokud se názvy shodují. Pokud se názvy změněných vlastností již neshodují mezi tabulkou a třídou entity, může být nutné vybrat vlastnost ekvivalentní třídy pro mapování na, pokud Návrhář nemůže určit správné mapování.

10. Klikněte na tlačítko **OK** nebo **použít**.

    > [!NOTE]
    > Můžete pokračovat v konfiguraci chování pro každou kombinaci třídy/chování, pokud kliknete na **použít** po provedení každé změny. Pokud změníte třídu nebo chování předtím, než kliknete na **použít**, zobrazí se dialogové okno s upozorněním, které vám nabídne možnost použít změny.

     Chcete-li se vrátit k používání výchozí logiky modulu runtime pro aktualizace, klikněte na tři tečky vedle příkazu Vložit, aktualizovat nebo odstranit v okně **vlastnosti** a pak v dialogovém okně **Konfigurovat chování** vyberte **použít modul runtime** .

## <a name="see-also"></a>Viz také
 Postupy LINQ to SQL v metodách DataContext [v nástroji Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [(o/r Designer)](../data-tools/datacontext-methods-o-r-designer.md) [: vytváření tříd LINQ to SQL (o-r Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [operací vložení, aktualizace a odstranění](https://msdn.microsoft.com/library/26a43a4f-83c9-4732-806d-bb23aad0ff6b)
