---
title: DataRelation – použijte k vytvoření vztahů mezi tabulkami
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vbData.Microsoft.VSDesigner.DataSource.DesignRelation
- vbdata.Microsoft.VSDesigner.DataSource.DesignRelation
helpviewer_keywords:
- relationships, about relationships
- datasets [Visual Basic], relationships
- relationships, datasets
ms.assetid: cfe274f0-71fe-40f6-994e-7c7f6273c9ba
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 812b464fe3e9742309a1ce6918d8d6b383101bf8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49864121"
---
# <a name="create-relationships-between-datasets"></a>Vytváření vztahů mezi tabulkami
Datové sady, které obsahují data související tabulky použijte <xref:System.Data.DataRelation> objekty představují nadřazené a podřízené relace mezi tabulkami a vrácení souvisejících záznamů od sebe. Přidání souvisejících tabulek do datové sady s použitím **Průvodce konfigurací zdroje dat**, nebo **Návrhář Dataset**, vytvoří a nakonfiguruje <xref:System.Data.DataRelation> objekt za vás.

<xref:System.Data.DataRelation> Objekt provádí dvě funkce:

-   Může být k dispozici záznamy související s záznamu, na které pracujete. Pokud jste v nadřazený záznam poskytuje podřízené záznamy (<xref:System.Data.DataRow.GetChildRows%2A>) a nadřazený záznam, pokud pracujete s podřízeného záznamu (<xref:System.Data.DataRow.GetParentRow%2A>).

-   To můžete vynutit omezení referenční integrity, jako je například odstranění související podřízené záznamy, když odstraníte záznam nadřazené.

Je důležité pochopit rozdíl mezi true spojení a funkce <xref:System.Data.DataRelation> objektu. True spojení jsou záznamy na základě nadřazené a podřízené tabulky a vloží do jednoho ploché sady záznamů. Při použití <xref:System.Data.DataRelation> objektu, je vytvořen bez nové sady záznamů. Místo toho DataRelation sleduje relace mezi tabulkami a udržuje nadřazené a podřízené záznamy synchronizované.

## <a name="datarelation-objects-and-constraints"></a>DataRelation – objekty a omezení
A <xref:System.Data.DataRelation> objektu se používá také vytvářet a vynucovat následující omezení:

-   Jedinečné omezení, což zaručuje, že sloupce v tabulce neobsahuje duplicitní položky.

-   Omezení cizího klíče, který může sloužit k udržení referenční integrity mezi nadřazenou a podřízenou tabulku v datové sadě.

Omezení, která zadáte <xref:System.Data.DataRelation> objektu jsou implementovány automaticky vytváří odpovídající objekty nebo nastavením vlastnosti. Pokud vytvoříte omezení foreign key s použitím <xref:System.Data.DataRelation> objektu, instance <xref:System.Data.ForeignKeyConstraint> třídy jsou přidány do <xref:System.Data.DataRelation> objektu <xref:System.Data.DataRelation.ChildKeyConstraint%2A> vlastnost.

Jedinečné omezení je implementováno buď jednoduše nastavením <xref:System.Data.DataColumn.Unique%2A> vlastnost sloupec dat na `true` nebo přidáním instance <xref:System.Data.UniqueConstraint> třídu <xref:System.Data.DataRelation> objektu <xref:System.Data.DataRelation.ParentKeyConstraint%2A> vlastnost. Informace o pozastavení omezení v datové sadě, naleznete v tématu [vypnutí omezení při naplňování datové sady](../data-tools/turn-off-constraints-while-filling-a-dataset.md).

### <a name="referential-integrity-rules"></a>Pravidla referenční integritu
Jako součást omezení cizího klíče můžete zadat referenční integritu pravidla, která se použijí na třech místech:

-   Při aktualizaci nadřazený záznam

-   Při odstranění nadřazený záznam

-   Kdy je změna přijímat nebo odmítat.

Pravidla, které můžete použít jsou určené v <xref:System.Data.Rule> výčtu a jsou uvedeny v následující tabulce.

|Pravidlo omezení pro cizí klíč|Akce|
| - |------------|
|<xref:System.Data.Rule.Cascade>|Také je provedena změna (update nebo delete) provedených na nadřazený záznam související záznamy v podřízené tabulce.|
|<xref:System.Data.Rule.SetNull>|Podřízené záznamy se neodstraní, ale nastavení cizí klíče v podřízené záznamy <xref:System.DBNull>. S tímto nastavením může být ponecháno podřízené záznamy "osamocené položky" – to znamená, že nemají žádný vztah k nadřazené záznamy. **Poznámka:** pomocí tohoto pravidla může vést k neplatná data v podřízené tabulce.|
|<xref:System.Data.Rule.SetDefault>|Cizí klíče v související podřízené záznamy je nastavena na výchozí hodnotu (podle sloupce <xref:System.Data.DataColumn.DefaultValue%2A> vlastnost).|
|<xref:System.Data.Rule.None>|Související podřízené záznamy se neprovedly žádné změny. S tímto nastavením může obsahovat podřízené záznamy odkazy na neplatný nadřazené záznamy.|

Další informace o aktualizacích v tabulkách datové sady, naleznete v tématu [uložit data zpět do databáze](../data-tools/save-data-back-to-the-database.md).

### <a name="constraint-only-relations"></a>Pouze pro omezení relací
Když vytvoříte <xref:System.Data.DataRelation> objektu, máte možnost určit, že relace lze použít pouze k vynucení omezení – to znamená, ho také se nepoužije pro přístup k souvisejících záznamů. Tuto možnost můžete použít ke generování datovou sadu, která je efektivnější a který obsahuje metody méně než jedna možnost související záznamy. Nebudete ale moci přistupovat k souvisejících záznamů. Například pouze omezení relace zabraňuje odstranění nadřazený záznam, který má stále podřízené záznamy a podřízené záznamy nelze přistupovat prostřednictvím nadřazené.

## <a name="manually-creating-a-data-relation-in-the-dataset-designer"></a>Ruční vytvoření vztahu data v návrháři datových sad
Při vytváření datových tabulek pomocí nástrojů pro návrh dat v sadě Visual Studio vztahy se vytvoří automaticky, pokud ze zdroje dat se dají shromáždit informace. Pokud chcete ručně přidat tabulky dat z **datovou sadu** karty **nástrojů**, možná budete muset ručně vytvořit relaci. Další informace o vytváření <xref:System.Data.DataRelation> prostřednictvím kódu programu, najdete v článku objekty [přidání datových relací](/dotnet/framework/data/adonet/dataset-datatable-dataview/adding-datarelations).

Relace mezi tabulkami dat zobrazovat jako řádky v **Návrhář Dataset**, s klíči a nekonečno piktogram znázorňující aspekt vztah jeden mnoho. Ve výchozím nastavení se nezobrazí název relace na návrhové ploše.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-create-a-relationship-between-two-data-tables"></a>K vytvoření vztahu mezi dvěma datovými tabulkami

1.  Otevřete svou datovou sadu v **Návrhář Dataset**. Další informace najdete v tématu [návod: vytvoření datové sady v návrháři datových sad](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2.  Přetáhněte **vztah** objektu z **datovou sadu** nástrojů do podřízené tabulky dat v relaci.

     **Vztah** otevře se dialogové okno, naplnění **podřízenou tabulku** pole s tabulkou, kterou jste přetáhli **vztah** objekt.

3.  Vyberte nadřazené tabulky z **nadřazená tabulka** pole. Nadřazená tabulka obsahuje záznamy na straně "1" vztah jeden mnoho.

4.  Zkontrolujte, jestli je v zobrazuje správné podřízené tabulky **podřízenou tabulku** pole. Podřízené tabulky obsahuje záznamy na straně "n" vztah jeden mnoho.

5.  Zadejte název pro relaci v **název** pole, nebo ponechte výchozí název založený na vybrané tabulky. Toto je název aplikace skutečný <xref:System.Data.DataRelation> objekt v kódu.

6.  Vyberte sloupce, které spojení tabulek v **sloupce klíčů** a **sloupce cizího klíče** seznamy.

7.  Vyberte, jestli chcete vytvořit relaci nebo omezení.

8.  Zaškrtněte nebo zrušte zaškrtnutí **vnořené relace** pole. Výběr, tato možnost nastaví <xref:System.Data.DataRelation.Nested%2A> vlastnost `true`, a to způsobí, že podřízené řádky vztahu, chcete-li být vnořen v rámci nadřazeného sloupce, když jsou tyto řádky zapisují jako XML data nebo synchronizovat se službou <xref:System.Xml.XmlDataDocument>. Další informace najdete v tématu [vnoření datových relací](/dotnet/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations).

9. Nastavení pravidel vynucení když děláte změny na záznamy v těchto tabulkách. Další informace naleznete v tématu <xref:System.Data.Rule>.

10. Klikněte na tlačítko **OK** a vytvořit tak relaci. Vztahu čáry se zobrazí v Návrháři mezi dvěma tabulkami.

#### <a name="to-display-a-relation-name-in-the-dataset-designer"></a>Chcete-li zobrazit název relace v návrháři datových sad

1.  Otevřete svou datovou sadu v **Návrhář Dataset**. Další informace najdete v tématu [návod: vytvoření datové sady v návrháři datových sad](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2.  Z **Data** nabídku, vyberte **zobrazení popisků relací** příkazu můžete zobrazit název vztahu. Tento příkaz Skrýt název vztahu vymažte.

## <a name="see-also"></a>Viz také:

- [Vytvoření a konfigurace datových sad v sadě Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)