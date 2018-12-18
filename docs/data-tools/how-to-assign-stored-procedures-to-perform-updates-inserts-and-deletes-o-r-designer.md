---
title: Pomocí uložené procedury provést aktualizaci, insert a delete v technologii Linq to SQL Návrhář relací objektů
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e88224ab-ff61-4a3a-b6b8-6f3694546cac
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: b7fd690997b7d7b58f8d1c1f84ea7f471d4fe496
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089773"
---
# <a name="how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-or-designer"></a>Postupy: přiřazení uložené procedury k provedení aktualizací, vložení a odstranění (Návrhář relací objektů)

Uložené procedury lze přidat do **Návrhář relací objektů** a provést, protože typické <xref:System.Data.Linq.DataContext> metody. Můžete také používají pro přepsat výchozí nastavení LINQ SQL runtime chování, které provádí vložení, aktualizace a odstraní po uložení změn z tříd entit k databázi (například při volání metody <xref:System.Data.Linq.DataContext.SubmitChanges%2A> metoda).

> [!NOTE]
> Pokud uložená procedura vrací hodnoty, které mají být odesílány zpět do klienta (například výpočtu hodnot v uložené proceduře), vytvořte výstupní parametry v uložené procedury. Pokud nemůžete použít výstupní parametry, zapsat implementace částečné metody aniž byste museli spoléhat na přepsání generované Návrhář relací objektů. Členy generované hodnoty musí být nastavena na odpovídající hodnoty po úspěšném dokončení operace INSERT nebo UPDATE. Další informace najdete v tématu [odpovědnosti vývojáře v přepsání výchozí chování](/dotnet/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior).

> [!NOTE]
> Technologie LINQ to SQL zpracovává generované hodnoty automaticky identity (automatického přírůstku), rowguidcol (generované GUID) a sloupce časového razítka. Generované hodnoty v jiné typy sloupců povede neočekávaně hodnotu null. K návratu hodnot generované databáze, měli byste ručně nastavit <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> k **true** a <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> na jednu z následujících: [AutoSync.Always](<xref:System.Data.Linq.Mapping.AutoSync.Always>), [AutoSync.OnInsert ](<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>), nebo [AutoSync.OnUpdate](<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate>).

## <a name="configure-the-update-behavior-of-an-entity-class"></a>Konfigurace chování aktualizace třídu Entity

Ve výchozím nastavení je logika pro aktualizace databáze (vložení, aktualizace a odstranění) změny, které byly provedeny k datům v technologii LINQ a tříd entit SQL poskytovaný LINQ to SQL runtime. Modul runtime vytvoří výchozí příkazy INSERT, UPDATE a DELETE, které jsou založeny na schéma tabulky (sloupec a informace o primárním klíči). Pokud není výchozí chování žádoucí, můžete provádět konfiguraci chování aktualizace přiřazením konkrétní uložené procedury pro provádění nezbytné vložení, aktualizace a odstranění potřebné k manipulaci s daty v tabulce. Můžete také k tomu generování výchozí chování není, například pokud vaše třídy entity mapování na zobrazení. Nakonec můžete přepsat výchozí chování aktualizace, pokud databáze vyžaduje přístup k tabulce prostřednictvím uložených procedur.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-assign-stored-procedures-to-override-the-default-behavior-of-an-entity-class"></a>Přiřadit uložené procedury přepsat výchozí chování třídu entity

1.  Otevřete **technologie LINQ to SQL** souboru v návrháři. (Dvakrát klikněte **dbml** souboru v **Průzkumníku řešení**.)

2.  V **Průzkumníka serveru** nebo **Průzkumník databáze**, rozbalte položku **uložené procedury** a vyhledejte uložené procedury, které chcete použít pro příkaz Insert, Update, nebo odstranit příkazy třídy entity.

3.  Přetáhněte uložené procedury na **Návrhář relací objektů**.

     Uložená procedura se přidá do podokna metody jako <xref:System.Data.Linq.DataContext> metoda. Další informace najdete v tématu [DataContext metody (Návrhář relací objektů)](../data-tools/datacontext-methods-o-r-designer.md).

4.  Vyberte třídu entity, pro který chcete pomocí uložené procedury k provedení aktualizace.

5.  V **vlastnosti** okně vyberte příkaz pro přepsání (**vložit**, **aktualizace**, nebo **odstranit**).

6.  Klikněte na tlačítko se třemi tečkami (...) vedle slova **modulu Runtime použijte** otevřete **nakonfigurovat chování** dialogové okno.

7.  Vyberte **přizpůsobit**.

8.  Vyberte požadovanou uloženou proceduru v **přizpůsobit** seznamu.

9. Zkontrolujte seznam **metoda argumenty** a **vlastnosti třídy** ověřit, jestli **metoda argumenty** mapy na příslušné **vlastnosti třídy**. Mapování původní metoda argumenty (`Original_<ArgumentName>`) na původní vlastnosti (`<PropertyName> (Original)`) pro `Update` a `Delete` příkazy.

    > [!NOTE]
    > Ve výchozím nastavení metoda argumenty mapovat na vlastnosti třídy když se názvy shodují. Pokud se změnila vlastnost, kterou názvy shodovat už mezi tabulkou a třídu entity, můžete chtít, vyberte vlastnost ekvivalentní třídy mapovat Pokud návrháře nemůže určit správné mapování.

10. Klikněte na tlačítko **OK** nebo **použít**.

    > [!NOTE]
    >  Můžete pokračovat, dokud po kliknutí na tlačítko Konfigurovat chování pro každou kombinaci třídy a chování **použít** po každé změně. Pokud změníte třídu nebo chování před kliknutím na **použít**, dialogové okno upozornění se zobrazí a poskytuje možnost použít změny.

Chcete-li vrátit zpět k používání výchozí logiku modulu runtime pro aktualizace, klikněte na tlačítko se třemi tečkami vedle **vložit**, **aktualizace**, nebo **odstranit** příkazu v **vlastnosti**  okna a potom vyberte **využití modulu runtime** v **nakonfigurovat chování** dialogové okno.

## <a name="see-also"></a>Viz také:

- [Technologie LINQ to SQL nástroje v sadě Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Metody DataContext](../data-tools/datacontext-methods-o-r-designer.md)
- [Technologie LINQ to SQL (rozhraní .NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
- [Vložit, aktualizovat a odstranit operace (rozhraní .NET Framework)](/dotnet/framework/data/adonet/sql/linq/insert-update-and-delete-operations)