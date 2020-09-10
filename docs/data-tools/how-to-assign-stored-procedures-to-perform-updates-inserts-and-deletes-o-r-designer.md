---
title: Použití uložených procedur v LINQ to SQL k aktualizaci dat
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: e88224ab-ff61-4a3a-b6b8-6f3694546cac
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: ba6ee706a7c18545a17683233e30283559542890
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2020
ms.locfileid: "89743009"
---
# <a name="how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-or-designer"></a>Postupy: Přiřazení uložených procedur za účelem aktualizací, vkládání a odstraňování (Návrhář relací objektů)

Uložené procedury lze přidat do **návrháře o/R** a spustit jako typické <xref:System.Data.Linq.DataContext> metody. Lze je také použít k přepsání výchozího LINQ to SQL chování při spuštění, které provádí vložení, aktualizace a odstranění, když jsou změny uloženy z tříd entit do databáze (například při volání <xref:System.Data.Linq.DataContext.SubmitChanges%2A> metody).

> [!NOTE]
> Pokud uložená procedura vrátí hodnoty, které je třeba odeslat zpět klientovi (například hodnoty vypočtené v uložené proceduře), vytvořte výstupní parametry v uložených procedurách. Pokud nemůžete použít výstupní parametry, zapište implementaci částečné metody, nemusíte se spoléhat na přepsání vygenerovaná návrhářem O/R. Po úspěšném dokončení operací vložení nebo aktualizace musí být členové namapované na hodnoty generované databází nastaveny na příslušné hodnoty. Další informace najdete v tématu [zodpovědnosti vývojáře při přepisu výchozího chování](/dotnet/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior).

> [!NOTE]
> LINQ to SQL zpracovává hodnoty generované databázemi automaticky pro sloupce identity (automatické zvýšení), ROWGUIDCOL (GUID generovaný identifikátor GUID) a časové razítko. Hodnoty generované databází v jiných typech sloupců neočekávaně způsobí hodnotu null. Chcete-li vrátit hodnoty generované databází, je třeba ručně nastavit <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> **hodnotu true** a <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> jednu z následujících možností: [AutoSync. Always](<xref:System.Data.Linq.Mapping.AutoSync.Always>), [AutoSync. při vložení](<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>)nebo [AutoSync. inupdate](<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate>).

## <a name="configure-the-update-behavior-of-an-entity-class"></a>Konfigurace chování aktualizace třídy entity

Ve výchozím nastavení logika aktualizace databáze (vložení, aktualizace a odstranění) se změnami provedenými v datech v LINQ to SQL třídy entit je poskytována modulem runtime LINQ to SQL. Modul runtime vytvoří výchozí příkazy INSERT, UPDATE a DELETE, které jsou založeny na schématu tabulky (informace o sloupci a primárním klíči). Pokud výchozí chování není žádoucí, můžete nakonfigurovat chování aktualizace přiřazením specifických uložených procedur pro provádění nezbytných vložení, aktualizací a odstranění potřebných k manipulaci s daty v tabulce. To lze provést také v případě, že se výchozí chování negeneruje, například když vaše třídy entit budou mapovány na zobrazení. Nakonec můžete přepsat výchozí chování aktualizace, když databáze vyžaduje přístup k tabulce prostřednictvím uložených procedur.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-assign-stored-procedures-to-override-the-default-behavior-of-an-entity-class"></a>Přiřazení uložených procedur pro přepsání výchozího chování třídy entity

1. Otevřete soubor **LINQ to SQL** v návrháři. (Poklikejte na soubor **. dbml** v **Průzkumník řešení**.)

2. V **Průzkumník serveru** nebo **Průzkumníku databáze**rozbalte **uložené procedury** a vyhledejte uložené procedury, které chcete použít pro příkazy INSERT, Update a Delete třídy entity.

3. Přetáhněte uloženou proceduru do **návrháře o/R**.

     Uložená procedura je přidána do podokna metody jako <xref:System.Data.Linq.DataContext> metoda. Další informace naleznete v tématu [metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

4. Vyberte třídu entity, pro kterou chcete použít uloženou proceduru pro provádění aktualizací.

5. V okně **vlastnosti** vyberte příkaz, který chcete přepsat (**Vložit**, **aktualizovat**nebo **Odstranit**).

6. Klikněte na tlačítko se třemi tečkami (...) vedle slov **použít modul runtime** k otevření dialogového okna **Konfigurovat chování** .

7. Vyberte **Přizpůsobit**.

8. V seznamu **přizpůsobit** vyberte požadovanou uloženou proceduru.

9. Zkontrolujte seznam **argumentů metody** a **vlastností třídy** a ověřte, zda jsou **argumenty metody** namapovány na příslušné **vlastnosti třídy**. Namapujte argumenty původní metody ( `Original_<ArgumentName>` ) na původní vlastnosti ( `<PropertyName> (Original)` ) pro `Update` `Delete` příkazy a.

    > [!NOTE]
    > Ve výchozím nastavení jsou argumenty metody mapovány na vlastnosti třídy, pokud se názvy shodují. Pokud se názvy změněných vlastností již neshodují mezi tabulkou a třídou entity, může být nutné vybrat vlastnost ekvivalentní třídy pro mapování na, pokud Návrhář nemůže určit správné mapování.

10. Klikněte na tlačítko **OK** nebo **použít**.

    > [!NOTE]
    > Můžete pokračovat v konfiguraci chování pro každou kombinaci třídy a chování, pokud kliknete na **použít** po provedení každé změny. Pokud změníte třídu nebo chování předtím, než kliknete na **použít**, zobrazí se dialogové okno s upozorněním a nabídne vám možnost použít změny.

Chcete-li se vrátit k používání výchozí logiky modulu runtime pro aktualizace, klikněte na tři tečky vedle příkazu **Vložit**, **aktualizovat**nebo **Odstranit** v okně **vlastnosti** a pak v dialogovém okně **Konfigurovat chování** vyberte **použít modul runtime** .

## <a name="see-also"></a>Viz také:

- [Nástroje LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Metody DataContext](../data-tools/datacontext-methods-o-r-designer.md)
- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
- [Operace vložení, aktualizace a odstranění (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/insert-update-and-delete-operations)
