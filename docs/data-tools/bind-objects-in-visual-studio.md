---
title: Vlastní objekty datové vazby
description: Vytváření vazeb objektů jako datových zdrojů v aplikaci Visual Studio. Použijte vývojové nástroje pro práci s vlastními objekty jako zdroj dat ve vaší aplikaci.
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], object binding
- data [Visual Studio], binding to objects
- object binding
- binding, to objects
ms.assetid: ed743ce6-73af-45e5-a8ff-045eddaccc86
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: ea36249ecc0cfc266a650ca24d143e053f7fc0d9
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2020
ms.locfileid: "94382101"
---
# <a name="bind-objects-as-data-sources-in-visual-studio"></a>Vázání objektů jako datových zdrojů v aplikaci Visual Studio

Visual Studio poskytuje nástroje pro návrh pro práci s vlastními objekty jako zdroj dat ve vaší aplikaci. Chcete-li uložit data z databáze v objektu, který je svázán s ovládacími prvky uživatelského rozhraní, je doporučeným přístupem použití Entity Framework k vygenerování třídy nebo tříd. Entity Framework automaticky generuje všechen často používaný kód pro sledování změn, což znamená, že všechny změny místních objektů jsou automaticky uchovány do databáze při volání metody AcceptChanges na objekt Negenerickými. Další informace najdete v [dokumentaci Entity Framework](https://ef.readthedocs.org/en/latest/).

> [!TIP]
> Přístupy k vazbě objektů v tomto článku by měly být zváženy pouze v případě, že je vaše aplikace již založena na datových sadách. Tyto přístupy můžete použít také v případě, že už jste obeznámeni s datovými sadami a data, která budete zpracovávat, jsou tabulková a nepříliš složitá nebo příliš velká. V případě jednoduššího příkladu, který zahrnuje načítání dat přímo do objektů pomocí objektu DataReader a ruční aktualizace uživatelského rozhraní bez vazby, si přečtěte téma [Vytvoření jednoduché datové aplikace pomocí ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md).

## <a name="object-requirements"></a>Požadavky na objekty

Jediným požadavkem, aby vlastní objekty pracovaly s nástroji pro návrh dat v aplikaci Visual Studio je, že objekt potřebuje alespoň jednu veřejnou vlastnost.

Obecně platí, že vlastní objekty nevyžadují žádná konkrétní rozhraní, konstruktory nebo atributy, které by sloužily jako zdroj dat pro aplikaci. Pokud však chcete přetáhnout objekt z okna **zdroje dat** na návrhovou plochu pro vytvoření ovládacího prvku vázaného na data, a pokud objekt implementuje <xref:System.ComponentModel.ITypedList> <xref:System.ComponentModel.IListSource> rozhraní nebo, objekt musí mít výchozí konstruktor. V opačném případě Visual Studio nemůže vytvořit instanci objektu zdroje dat a při přetahování položky na návrhovou plochu zobrazí chybu.

## <a name="examples-of-using-custom-objects-as-data-sources"></a>Příklady použití vlastních objektů jako zdrojů dat

I když existují dlouhé způsoby implementace logiky aplikace při práci s objekty jako se zdrojem dat, pro databáze SQL existuje několik standardních operací, které lze zjednodušit pomocí objektů TableAdapter generovaných sadou Visual Studio. Tato stránka vysvětluje, jak implementovat tyto standardní procesy pomocí objekty TableAdapter. Neslouží jako vodítko pro vytváření vlastních objektů. Například budete obvykle provádět následující standardní operace bez ohledu na konkrétní implementaci vašich objektů nebo logiku aplikace:

- Načítání dat do objektů (obvykle z databáze).

- Vytváření typové kolekce objektů.

- Přidávání objektů do objektů a jejich odebírání z kolekce.

- Zobrazení dat objektu uživatelům na formuláři.

- Změna nebo úprava dat v objektu.

- Ukládání dat z objektů zpět do databáze.

### <a name="load-data-into-objects"></a>Načtení dat do objektů

V tomto příkladu načtete data do svých objektů pomocí objekty TableAdapter. Ve výchozím nastavení jsou objekty TableAdapter vytvořeny pomocí dvou druhů metod, které načítají data z databáze a naplňují tabulky dat.

- `TableAdapter.Fill`Metoda vyplní existující datovou tabulku datovými vrácenými daty.

- `TableAdapter.GetData`Metoda vrátí novou tabulku dat naplněnou daty.

Nejjednodušší způsob, jak načíst vlastní objekty s daty, je zavolat `TableAdapter.GetData` metodu, cyklicky procházet kolekci řádků v tabulce vrácených dat a každý objekt naplnit hodnotami v jednotlivých řádcích. Můžete vytvořit `GetData` metodu, která vrátí tabulku s vyplněnými daty pro libovolný dotaz přidaný do TableAdapter.

> [!NOTE]
> Visual Studio pojmenovává dotazy TableAdapter `Fill` a `GetData` ve výchozím nastavení je můžete změnit na libovolný platný název metody.

Následující příklad ukazuje, jak projít řádky v tabulce dat a naplnit objekt daty:

[!code-csharp[VbRaddataConnecting#4](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_1.cs)]
[!code-vb[VbRaddataConnecting#4](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_1.vb)]

### <a name="create-a-typed-collection-of-objects"></a>Vytvořit typovou kolekci objektů

Můžete vytvořit třídy kolekcí pro vaše objekty nebo použít typové kolekce, které jsou automaticky poskytovány [komponentou BindingSource](/dotnet/framework/winforms/controls/bindingsource-component).

Když vytváříte vlastní třídu kolekce pro objekty, doporučujeme, abyste dědili z <xref:System.ComponentModel.BindingList%601> . Tato obecná třída poskytuje funkce pro správu kolekce a také možnost vyvolat události, které odesílají oznámení do infrastruktury datových vazeb v model Windows Forms.

Automaticky vygenerovaná kolekce v nástroji <xref:System.Windows.Forms.BindingSource> používá <xref:System.ComponentModel.BindingList%601> pro svou typovou kolekci. Pokud vaše aplikace nevyžaduje další funkce, můžete kolekci udržovat v rámci <xref:System.Windows.Forms.BindingSource> . Další informace naleznete v tématu <xref:System.Windows.Forms.BindingSource.List%2A> vlastnost <xref:System.Windows.Forms.BindingSource> třídy.

> [!NOTE]
> Pokud vaše kolekce vyžaduje funkce, které nejsou poskytovány základní implementací <xref:System.ComponentModel.BindingList%601> , měli byste vytvořit vlastní kolekci, aby bylo možné přidat ke třídě podle potřeby.

Následující kód ukazuje, jak vytvořit třídu pro kolekci objektů se silným typem `Order` :

[!code-csharp[VbRaddataConnecting#8](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_2.cs)]
[!code-vb[VbRaddataConnecting#8](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_2.vb)]

### <a name="add-objects-to-a-collection"></a>Přidání objektů do kolekce

Objekty lze do kolekce přidat voláním `Add` metody třídy vlastní kolekce nebo z <xref:System.Windows.Forms.BindingSource> .

> [!NOTE]
> `Add`Metoda je automaticky poskytována pro vlastní kolekci, pokud je děděna z <xref:System.ComponentModel.BindingList%601> .

Následující kód ukazuje, jak přidat objekty do typové kolekce v <xref:System.Windows.Forms.BindingSource> :

[!code-csharp[VbRaddataConnecting#5](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_3.cs)]
[!code-vb[VbRaddataConnecting#5](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_3.vb)]

Následující kód ukazuje, jak přidat objekty do typové kolekce, která dědí z <xref:System.ComponentModel.BindingList%601> :

> [!NOTE]
> V tomto příkladu `Orders` je kolekce vlastností `Customer` objektu.

[!code-csharp[VbRaddataConnecting#6](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_4.cs)]
[!code-vb[VbRaddataConnecting#6](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_4.vb)]

### <a name="remove-objects-from-a-collection"></a>Odebrání objektů z kolekce

Objekty z kolekce můžete odebrat voláním `Remove` `RemoveAt` metody nebo třídy vlastní kolekce nebo z <xref:System.Windows.Forms.BindingSource> .

> [!NOTE]
> `Remove`Metody a `RemoveAt` jsou automaticky poskytovány pro vlastní kolekci, když převezmete z <xref:System.ComponentModel.BindingList%601> .

Následující kód ukazuje, jak vyhledat a odebrat objekty ze typové kolekce v <xref:System.Windows.Forms.BindingSource> s <xref:System.Windows.Forms.BindingSource.RemoveAt%2A> metodou:

[!code-csharp[VbRaddataConnecting#7](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_5.cs)]
[!code-vb[VbRaddataConnecting#7](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_5.vb)]

### <a name="display-object-data-to-users"></a>Zobrazení dat objektu uživatelům

Chcete-li zobrazit data v objektech uživatelů, vytvořte zdroj dat objektu pomocí průvodce **konfigurací zdroje dat** a pak přetáhněte celý objekt nebo jednotlivé vlastnosti do formuláře z okna **zdroje dat** .

### <a name="modify-the-data-in-objects"></a>Úprava dat v objektech

Chcete-li upravit data ve vlastních objektech, které jsou vázány na data model Windows Forms ovládacích prvků, jednoduše upravte data v vázaném ovládacím prvku (nebo přímo ve vlastnostech objektu). Architektura datové vazby aktualizuje data v objektu.

Pokud vaše aplikace vyžaduje sledování změn a vrácení navrhovaných změn na původní hodnoty, musíte tuto funkci implementovat v objektovém modelu. Příklady, jak tabulky dat udržují přehled o navrhovaných změnách, naleznete v tématech <xref:System.Data.DataRowState> , <xref:System.Data.DataSet.HasChanges%2A> a <xref:System.Data.DataTable.GetChanges%2A> .

### <a name="save-data-in-objects-back-to-the-database"></a>Uložení dat v objektech zpět do databáze

Uložte data zpět do databáze předáním hodnot z vašeho objektu do TableAdapter metod DBDirect.

Visual Studio vytvoří metody DBDirect, které lze spustit přímo proti databázi. Tyto metody nevyžadují objekty DataSet nebo DataTable.

|TableAdapter DBDirect – metoda|Popis|
| - |-----------------|
|`TableAdapter.Insert`|Přidá nové záznamy do databáze a umožní předat do jednotlivých hodnot sloupců jako parametry metody.|
|`TableAdapter.Update`|Aktualizuje existující záznamy v databázi. Metoda aktualizace přijímá původní a nové hodnoty sloupce jako parametry metody. Původní hodnoty se používají k vyhledání původního záznamu a k aktualizaci tohoto záznamu se použijí nové hodnoty.<br /><br /> `TableAdapter.Update`Metoda je také použita pro sjednocení změn v datové sadě zpět do databáze pomocí přebírání <xref:System.Data.DataSet> , <xref:System.Data.DataTable> , <xref:System.Data.DataRow> nebo pole <xref:System.Data.DataRow> s jako parametrů metody.|
|`TableAdapter.Delete`|Odstraní existující záznamy z databáze na základě původních hodnot sloupců předaných jako parametry metody.|

Chcete-li uložit data z kolekce objektů, smyčkou prostřednictvím kolekce objektů (například pomocí smyčky for-Next). Odešlete hodnoty pro každý objekt do databáze pomocí metod DBDirect TableAdapter.

Následující příklad ukazuje, jak použít `TableAdapter.Insert` metodu DBDirect pro přidání nového zákazníka přímo do databáze:

[!code-csharp[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_6.cs)]
[!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_6.vb)]

## <a name="see-also"></a>Viz také

- [Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
