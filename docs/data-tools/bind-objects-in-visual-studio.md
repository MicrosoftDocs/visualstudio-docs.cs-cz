---
title: 'Vytvořit datovou vazbu s: vlastních objektů'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], object binding
- data [Visual Studio], binding to objects
- object binding
- binding, to objects
ms.assetid: ed743ce6-73af-45e5-a8ff-045eddaccc86
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: b7790f5205aa24a68505a1b34e97283aff05e13c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49950133"
---
# <a name="bind-objects-as-data-sources-in-visual-studio"></a>Vytvoření vazby objektů jako zdroje dat v sadě Visual Studio

Visual Studio poskytuje nástroje návrhu pro práci s vlastní objekty jako zdroj dat ve vaší aplikaci. Pokud chcete ukládat data z databáze v objektu, který svázat ovládací prvky uživatelského rozhraní, doporučený postup je mohli použít ke generování třídy nebo třídy rozhraní Entity Framework. Entity Framework automaticky generuje všechny často používaný text sledování změn kódu, což znamená, že změny místní objekty jsou automaticky zachované v databázi při volání metoda AcceptChanges DbSet objektu. Další informace najdete v tématu [dokumentace Entity Framework](https://ef.readthedocs.org/en/latest/).

> [!TIP]
> Přístupy k objektu vazby v tomto článku byste měli uvažovat pouze pokud je aplikace již založen na datové sady. Můžete také tyto přístupy Pokud jste už obeznámení s datovými sadami a data, která bude zpracovávat je tabulkový a příliš složitý nebo moc velký. Příklad ještě jednodušší, týkající se načítání dat přímo do objektů pomocí čtečky dat a ruční aktualizace uživatelského rozhraní bez vázání dat, naleznete v tématu [vytvoření jednoduché datové aplikace pomocí ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md).

## <a name="object-requirements"></a>Požadavky na objekt

Jediným požadavkem pro vlastní objekty pro práci s daty návrhových nástrojů v sadě Visual Studio je, že by objekt měl alespoň jednu veřejnou vlastnost.

Vlastní objekty obecně platí, nevyžadují žádné konkrétní rozhraní, konstruktory nebo atributy tak, aby fungoval jako zdroj dat pro aplikaci. Ale pokud budete chtít přetažením objektu z **zdroje dat** okno na návrhovou plochu vytvoříte ovládací prvek vázaný na data, a pokud objekt implementuje <xref:System.ComponentModel.ITypedList> nebo <xref:System.ComponentModel.IListSource> rozhraní, objekt musí mít výchozí hodnotu konstruktor. V opačném případě sady Visual Studio nelze vytvořit instanci objektu zdroje dat a zobrazí chyba, když přetáhnete položku na návrhovou plochu.

## <a name="examples-of-using-custom-objects-as-data-sources"></a>Příklady použití vlastních objektů jako zdroje dat

I když existují aplikací způsoby, jak implementovat logiku vaše aplikace při práci s objekty jako zdroj dat, pro SQL databáze existuje jsou několik standardních operací, které se dá zjednodušit pomocí objektů TableAdapter generovaný sady Visual Studio. Tato stránka vysvětluje, jak implementovat tyto standardní procesy pomocí objektů TableAdapter. Není určena jako vodítko pro vytváření vlastních objektů. Například se obvykle provádí následující standardní operace bez ohledu na konkrétní implementaci objekty nebo aplikace logiky:

-   Načítání dat do objektů (obvykle z databáze).

-   Vytvoření typové kolekci objektů.

-   Přidání objektů do a odebrání objektů z kolekce.

-   Zobrazení dat objektů pro uživatele ve formuláři.

-   Změna/úprava dat v objektu.

-   Ukládání dat z objektů zpět do databáze.

### <a name="load-data-into-objects"></a>Načtení dat do objektů

V tomto příkladu můžete načíst data do objektů pomocí objektů TableAdapter. Ve výchozím nastavení jsou objekty TableAdapter vytvořeny dva druhy metod, které načtou data z databáze a vkládání dat do tabulek.

-   `TableAdapter.Fill` Metoda vyplní existující data tabulky s daty vrácenými.

-   `TableAdapter.GetData` Metoda vrátí novou tabulku naplněný daty.

Nejjednodušší způsob, jak načíst vaše vlastní objekty s daty je volání `TableAdapter.GetData` metoda, procházení kolekce řádků v tabulce vrácená data a naplňte každý objekt pomocí hodnot v jednotlivých řádcích. Můžete vytvořit `GetData` metodu, která vrací tabulku naplněných daty pro libovolný dotaz přidaný do objektu TableAdapter.

> [!NOTE]
> Visual Studio názvy dotazů TableAdapter `Fill` a `GetData` ve výchozím nastavení, ale tyto názvy můžete změnit na libovolný platný název metody.

Následující příklad ukazuje, jak projít řádky v tabulce dat a naplnění objektu s daty:

[!code-csharp[VbRaddataConnecting#4](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_1.cs)]
[!code-vb[VbRaddataConnecting#4](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_1.vb)]

### <a name="create-a-typed-collection-of-objects"></a>Vytvořit kolekci typu objektů

Můžete vytvořit kolekce tříd pro objekty, nebo použít typu kolekce, které jsou automaticky poskytované [komponenty BindingSource](/dotnet/framework/winforms/controls/bindingsource-component).

Při vytváření vlastní kolekce tříd pro objekty, doporučujeme, abyste dědili z <xref:System.ComponentModel.BindingList%601>. Tato obecná třída poskytuje funkce pro správu kolekce, stejně jako schopnost vyvolat události, které odesílají oznámení k infrastruktuře datové vazby v modelu Windows Forms.

Automaticky generovanou kolekci v <xref:System.Windows.Forms.BindingSource> používá <xref:System.ComponentModel.BindingList%601> pro své zadané kolekce. Pokud vaše aplikace nevyžaduje žádné další funkce, díky čemuž můžete udržovat v rámci vaší kolekce <xref:System.Windows.Forms.BindingSource>. Další informace najdete v tématu <xref:System.Windows.Forms.BindingSource.List%2A> vlastnost <xref:System.Windows.Forms.BindingSource> třídy.

> [!NOTE]
> Pokud vaše kolekce vyžaduje funkce není k dispozici základní implementace <xref:System.ComponentModel.BindingList%601>, byste měli vytvořit vlastní kolekce, takže můžete přidat do třídy podle potřeby.

Následující kód ukazuje, jak vytvořit třídu pro kolekce silného typu `Order` objekty:

[!code-csharp[VbRaddataConnecting#8](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_2.cs)]
[!code-vb[VbRaddataConnecting#8](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_2.vb)]

### <a name="add-objects-to-a-collection"></a>Přidání objektů do kolekce

Přidání objektů do kolekce pomocí volání `Add` metodu ve vaší vlastní třídu kolekce nebo <xref:System.Windows.Forms.BindingSource>.

> [!NOTE]
> `Add` Metoda automaticky zajištěna pro vlastní shromažďování při dědit z <xref:System.ComponentModel.BindingList%601>.

Následující kód ukazuje, jak přidat objekty do zadané kolekce <xref:System.Windows.Forms.BindingSource>:

[!code-csharp[VbRaddataConnecting#5](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_3.cs)]
[!code-vb[VbRaddataConnecting#5](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_3.vb)]

 Následující kód ukazuje, jak přidat objekty do zadané kolekce, která dědí z <xref:System.ComponentModel.BindingList%601>:

> [!NOTE]
> V tomto příkladu `Orders` kolekce je vlastnost `Customer` objektu.

[!code-csharp[VbRaddataConnecting#6](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_4.cs)]
[!code-vb[VbRaddataConnecting#6](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_4.vb)]

### <a name="remove-objects-from-a-collection"></a>Odebrání objektů z kolekce

Odebrání objektů z kolekce voláním `Remove` nebo `RemoveAt` metodu ve vaší vlastní třídu kolekce nebo <xref:System.Windows.Forms.BindingSource>.

> [!NOTE]
> `Remove` a `RemoveAt` metody automaticky dostupné pro vaše vlastní kolekce při dědit z <xref:System.ComponentModel.BindingList%601>.

Následující kód ukazuje, jak vyhledat a odebrat objekty ze zadané kolekce <xref:System.Windows.Forms.BindingSource> s <xref:System.Windows.Forms.BindingSource.RemoveAt%2A> metody:

[!code-csharp[VbRaddataConnecting#7](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_5.cs)]
[!code-vb[VbRaddataConnecting#7](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_5.vb)]

### <a name="display-object-data-to-users"></a>Aby uživatelům zobrazovaly data objektu

Zobrazit data v objektech na uživatele, vytvořte zdroj dat objektu pomocí **konfigurace zdroje dat** průvodce a pak přetáhněte na formuláře z celý objekt nebo jednotlivé vlastnosti **zdroje dat**okna.

### <a name="modify-the-data-in-objects"></a>Změna dat v objektech

Upravit data ve vlastních objektů, které jsou vázané na data pro ovládací prvky Windows Forms, jednoduše upravte data vázaného ovládacího prvku (nebo přímo do vlastností objektu). Datová vazba architektura aktualizuje data v objektu.

Pokud vaše aplikace vyžaduje sledování změn a vrácení zadní navrhovaných změn na původní hodnoty, musíte tuto funkci implementovat v objektovém modelu. Příklady jak tabulek dat udržovat přehled o navrhovaných změn, naleznete v tématu <xref:System.Data.DataRowState>, <xref:System.Data.DataSet.HasChanges%2A>, a <xref:System.Data.DataTable.GetChanges%2A>.

### <a name="save-data-in-objects-back-to-the-database"></a>Ukládání dat v objektech zpět do databáze

Uložte data zpět do databáze předáním hodnoty z objektu do objektu TableAdapter dbdirect – metody.

Visual Studio vytvoří dbdirect – metody, které mohou být provedeny přímo na databázi. Tyto metody nevyžadují, aby objekty DataSet nebo DataTable.

|TableAdapter dbdirect – metody|Popis|
| - |-----------------|
|`TableAdapter.Insert`|Přidá nové záznamy k databázi a zajistěte tak předání hodnot jednotlivých sloupců jako parametry metod.|
|`TableAdapter.Update`|Aktualizace existujících záznamů v databázi. Metoda aktualizace trvá sloupec původní a nové hodnoty jako parametry metod. Původní hodnoty se používají pro vyhledání záznamu původní a nové hodnoty se používají k aktualizaci záznamu.<br /><br /> `TableAdapter.Update` Metoda slouží také k odsouhlasení provedením změn v datové sadě zpět do databáze, <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, nebo pole <xref:System.Data.DataRow>označují jako parametry metody.|
|`TableAdapter.Delete`|Odstraní existující záznamy z databáze založené na původní hodnoty ve sloupcích předané jako parametry metod.|

Chcete-li uložit data z kolekce objektů, projít kolekci objektů (například pomocí smyčky pro další). Odešlete hodnoty pro každý objekt v databázi pomocí TableAdapter dbdirect – metody.

Následující příklad ukazuje způsob použití `TableAdapter.Insert` dbdirect – metody pro přidání nového zákazníka přímo do databáze:

[!code-csharp[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_6.cs)]
[!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_6.vb)]

## <a name="see-also"></a>Viz také:

- [Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)