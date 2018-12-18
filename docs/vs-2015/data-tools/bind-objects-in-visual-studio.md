---
title: Vytvoření vazby objektů
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
- data [Visual Studio], object binding
- data [Visual Studio], binding to objects
- object binding
- binding, to objects
ms.assetid: ed743ce6-73af-45e5-a8ff-045eddaccc86
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 875ea4491fa91063339008362d132b4416afe2af
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065003"
---
# <a name="bind-objects-in-visual-studio"></a>Vytvoření vazby objektů v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


Visual Studio poskytuje nástroje návrhu pro práci s vlastní objekty jako zdroj dat ve vaší aplikaci. Pokud chcete ukládat data z databáze v objektu, který svázat ovládací prvky uživatelského rozhraní, doporučený postup je mohli použít ke generování třídy nebo třídy rozhraní Entity Framework. Entity Frameworkautogenerates všechny často používaný text sledování změn kódu, což znamená, že jakékoli změny místní objekty jsou automaticky ukládají do databáze při volání metoda AcceptChanges DbSet objektu.    Další informace najdete v tématu [dokumentace Entity Framework](https://ef.readthedocs.org/en/latest/).

> [!TIP]
>  Přístupy k objektu vazby v tomto článku byste měli uvažovat pouze pokud je aplikace již založen na datové sady. Tyto přístupy lze také pokud jste už obeznámení s datovými sadami a data, která bude zpracovávat je tabulkový a příliš složitý nebo moc velký. Příklad ještě jednodušší, týkající se načítání dat přímo do objektů pomocí čtečky dat a ruční aktualizace uživatelského rozhraní bez vázání dat, naleznete v tématu [vytvoření jednoduché datové aplikace pomocí ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md).

## <a name="object-requirements"></a>Požadavky na objekt
 Jediným požadavkem pro vlastní objekty pro práci s daty návrhových nástrojů v sadě Visual Studio je, že by objekt měl alespoň jednu veřejnou vlastnost.

 Vlastní objekty obecně platí, nevyžadují žádné konkrétní rozhraní, konstruktory nebo atributy tak, aby fungoval jako zdroj dat pro aplikaci. Ale pokud budete chtít přetažením objektu z **zdroje dat** okno na návrhovou plochu vytvoříte ovládací prvek vázaný na data, a pokud objekt implementuje <xref:System.ComponentModel.ITypedList> nebo <xref:System.ComponentModel.IListSource> rozhraní, objekt musí mít výchozí hodnotu konstruktor. V opačném případě sady Visual Studio nelze vytvořit instanci objektu zdroje dat a zobrazí chyba, když přetáhnete položku na návrhovou plochu.

## <a name="examples-of-using-custom-objects-as-data-sources"></a>Příklady použití vlastních objektů jako zdroje dat
 I když existují aplikací způsoby, jak implementovat logiku vaše aplikace při práci s objekty jako zdroj dat, pro SQL databáze existuje jsou několik standardních operací, které se dá zjednodušit pomocí objektů TableAdapter generované – Visual Studio. Tato stránka vysvětluje, jak implementovat tyto standardní procesy pomocí TableAdapters.It není určen jako vodítko pro vytváření vlastních objektů. Například se obvykle provádí následující standardní operace bez ohledu na konkrétní implementaci objekty nebo aplikace logiky:

-   Načítání dat do objektů (obvykle z databáze).

-   Vytvoření typové kolekci objektů.

-   Přidání objektů do a odebrání objektů z kolekce.

-   Zobrazení dat objektů pro uživatele ve formuláři.

-   Změna/úprava dat v objektu.

-   Ukládání dat z objektů zpět do databáze.

> [!NOTE]
>  Pokud chcete lépe pochopit a poskytuje kontext pro příkladech na této stránce, doporučujeme provést následující: [návod: připojování k datům v objektech (Windows Forms)](http://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05). Tento návod vytvoří objekty zde popsané.

### <a name="loaddata-into-objects"></a>Loaddata do objektů
 V tomto příkladu můžete načíst data do objektů pomocí objektů TableAdapter. Ve výchozím nastavení jsou objekty TableAdapter vytvořeny dva druhy metod, které načtou data z databáze a vkládání dat do tabulek.

- `TableAdapter.Fill` Metoda vyplní existující data tabulky s daty vrácenými.

- `TableAdapter.GetData` Metoda vrátí novou tabulku naplněný daty.

  Nejjednodušší způsob, jak načíst vaše vlastní objekty s daty je volání `TableAdapter.GetData` metoda, procházení kolekce řádků v tabulce vrácená data a naplňte každý objekt pomocí hodnot v jednotlivých řádcích. Můžete vytvořit `GetData` metodu, která vrací tabulku naplněných daty pro libovolný dotaz přidaný do objektu TableAdapter.

> [!NOTE]
>  Visual Studio názvy dotazů TableAdapter `Fill` a `GetData` ve výchozím nastavení, ale tyto názvy můžete změnit na libovolný platný název metody.

 Následující příklad ukazuje, jak projít řádky v tabulce dat a naplnění objektu s daty:

 [!code-csharp[VbRaddataConnecting#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Form1.cs#4)]
 [!code-vb[VbRaddataConnecting#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Form1.vb#4)]

### <a name="create-a-typed-collection-of-objects"></a>Vytvořit kolekci typu objektů
 Můžete vytvořit kolekce tříd pro objekty, nebo použít typu kolekce, které jsou automaticky poskytované [komponenty BindingSource](http://msdn.microsoft.com/library/3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9).

 Při vytváření vlastní kolekce tříd pro objekty, doporučujeme, abyste dědili z <xref:System.ComponentModel.BindingList%601>. Tato obecná třída poskytuje funkce pro správu kolekce, stejně jako schopnost vyvolat události, které odesílají oznámení k infrastruktuře datové vazby v modelu Windows Forms.

 Kolekce automaticky generovány v <xref:System.Windows.Forms.BindingSource> používá <xref:System.ComponentModel.BindingList%601> pro své zadané kolekce. Pokud vaše aplikace nevyžaduje další funkce, pak můžete udržovat v rámci vaší kolekce <xref:System.Windows.Forms.BindingSource>. Další informace najdete v tématu <xref:System.Windows.Forms.BindingSource.List%2A> vlastnost <xref:System.Windows.Forms.BindingSource> třídy.

> [!NOTE]
>  Pokud vaše kolekce vyžaduje funkce není k dispozici základní implementace <xref:System.ComponentModel.BindingList%601>, byste měli vytvořit vlastní kolekce, takže můžete přidat do třídy podle potřeby.

 Následující kód ukazuje, jak vytvořit třídu pro kolekce silného typu `Order` objekty:

 [!code-csharp[VbRaddataConnecting#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#8)]
 [!code-vb[VbRaddataConnecting#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#8)]

### <a name="addobjects-to-a-collection"></a>Addobjects do kolekce
 Přidání objektů do kolekce pomocí volání `Add` metodu ve vaší vlastní třídu kolekce nebo <xref:System.Windows.Forms.BindingSource>.

 Příklad přidání do kolekce pomocí <xref:System.Windows.Forms.BindingSource>, najdete v článku `LoadCustomers` metoda ve [návod: připojování k datům v objektech (Windows Forms)](http://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05).

 Příklad přidání objektů do vlastní kolekce, najdete v článku `LoadOrders` metoda [návod: připojování k datům v objektech (Windows Forms)](http://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05).

> [!NOTE]
>  `Add` Metoda automaticky zajištěna pro vlastní shromažďování při dědit z <xref:System.ComponentModel.BindingList%601>.

 Následující kód ukazuje, jak přidat objekty do zadané kolekce <xref:System.Windows.Forms.BindingSource>:

 [!code-csharp[VbRaddataConnecting#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#5)]
 [!code-vb[VbRaddataConnecting#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#5)]

 Následující kód ukazuje, jak přidat objekty do zadané kolekce, která dědí z <xref:System.ComponentModel.BindingList%601>:

> [!NOTE]
>  V tomto příkladu `Orders` kolekce je vlastnost `Customer` objektu.

 [!code-csharp[VbRaddataConnecting#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#6)]
 [!code-vb[VbRaddataConnecting#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#6)]

### <a name="removeobjects-from-a-collection"></a>Removeobjects z kolekce
 Odebrání objektů z kolekce voláním `Remove` nebo `RemoveAt` metodu ve vaší vlastní třídu kolekce nebo <xref:System.Windows.Forms.BindingSource>.

> [!NOTE]
>  `Remove` a `RemoveAt` metody automaticky dostupné pro vaše vlastní kolekce při dědit z <xref:System.ComponentModel.BindingList%601>.

 Následující kód ukazuje, jak vyhledat a odebrat objekty ze zadané kolekce <xref:System.Windows.Forms.BindingSource> s <xref:System.Windows.Forms.BindingSource.RemoveAt%2A> metody:

 [!code-csharp[VbRaddataConnecting#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#7)]
 [!code-vb[VbRaddataConnecting#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#7)]

### <a name="displayobject-data-to-users"></a>DisplayObject data pro uživatele
 Zobrazit data v objektech na uživatele, vytvořte zdroj dat objektu pomocí **konfigurace zdroje dat** průvodce a pak přetáhněte na formuláře z celý objekt nebo jednotlivé vlastnosti **zdroje dat**okna.

### <a name="modify-the-data-in-objects"></a>Změna dat v objektech
 Upravit data ve vlastních objektů, které jsou vázané na data pro ovládací prvky Windows Forms, jednoduše upravte data vázaného ovládacího prvku (nebo přímo do vlastností objektu). Datová vazba architektura aktualizuje data v objektu.

 Pokud vaše aplikace vyžaduje sledování změn a vrácení zadní navrhovaných změn na původní hodnoty, musíte tuto funkci implementovat v objektovém modelu. Příklady jak tabulek dat udržovat přehled o navrhovaných změn, naleznete v tématu <xref:System.Data.DataRowState>, <xref:System.Data.DataSet.HasChanges%2A>, a <xref:System.Data.DataTable.GetChanges%2A>.

### <a name="savedata-in-objects-back-to-the-database"></a>SaveData v objektech zpět do databáze
 Uložte data zpět do databáze předáním hodnoty z objektu do objektu TableAdapter dbdirect – metody.

 Visual Studio vytvoří dbdirect – metody, které mohou být provedeny přímo na databázi. Tyto metody nevyžadují, aby objekty DataSet nebo DataTable.

|TableAdapter dbdirect – metody|Popis|
|----------------------------------|-----------------|
|`TableAdapter.Insert`|Přidá nové záznamy k databázi a zajistěte tak předání hodnot jednotlivých sloupců jako parametry metod.|
|`TableAdapter.Update`|Aktualizace existujících záznamů v databázi. Metoda aktualizace trvá sloupec původní a nové hodnoty jako parametry metod. Původní hodnoty se používají pro vyhledání záznamu původní a nové hodnoty se používají k aktualizaci záznamu.<br /><br /> `TableAdapter.Update` Metoda slouží také k odsouhlasení provedením změn v datové sadě zpět do databáze, <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, nebo pole <xref:System.Data.DataRow>označují jako parametry metody.|
|`TableAdapter.Delete`|Odstraní existující záznamy z databáze založené na původní hodnoty ve sloupcích předané jako parametry metod.|

 Chcete-li uložit data z kolekce objektů, projít kolekci objektů (například pomocí smyčky pro další). Odešlete hodnoty pro každý objekt v databázi pomocí TableAdapter dbdirect – metody.

 Následující příklad ukazuje způsob použití `TableAdapter.Insert` dbdirect – metody pro přidání nového zákazníka přímo do databáze:

 [!code-csharp[VbRaddataSaving#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#23)]
 [!code-vb[VbRaddataSaving#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#23)]

## <a name="see-also"></a>Viz také
 [Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
