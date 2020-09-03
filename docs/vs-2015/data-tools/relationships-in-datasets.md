---
title: Vztahy v datových sadách | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- vbData.Microsoft.VSDesigner.DataSource.DesignRelation
- vbdata.Microsoft.VSDesigner.DataSource.DesignRelation
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- relationships, about relationships
- datasets [Visual Basic], relationships
- relationships, datasets
ms.assetid: cfe274f0-71fe-40f6-994e-7c7f6273c9ba
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: eb13ad7db9a4f13ce9bf983ce6327045f885f4d8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652889"
---
# <a name="relationships-in-datasets"></a>Relace v datových sadách
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Datové sady, které obsahují související tabulky dat, používají <xref:System.Data.DataRelation> objekty k reprezentaci vztahu nadřazený-podřízený mezi tabulkami a k vrácení souvisejících záznamů od sebe. Přidání souvisejících tabulek do datových sad pomocí **Průvodce konfigurací zdroje dat**nebo **Návrhář datových sad**vytvoří a nakonfiguruje <xref:System.Data.DataRelation> objekt pro vás.

 <xref:System.Data.DataRelation>Objekt provádí dvě funkce:

- Může zpřístupnit záznamy související se záznamem, se kterým pracujete. Poskytuje podřízené záznamy, pokud jste v nadřazeném záznamu ( <xref:System.Data.DataRow.GetChildRows%2A> ) a nadřazeného záznamu, pokud pracujete s podřízeným záznamem ( <xref:System.Data.DataRow.GetParentRow%2A> ).

- Může vynutit omezení pro referenční integritu, například odstranění souvisejících podřízených záznamů při odstraňování nadřazeného záznamu.

  Je důležité pochopit rozdíl mezi skutečným spojením a funkcí <xref:System.Data.DataRelation> objektu. V pravdivém spojení jsou záznamy pořízeny z nadřazených a podřízených tabulek a vloženy do jediné ploché sady záznamů. Při použití objektu není <xref:System.Data.DataRelation> vytvořena žádná nová sada záznamů. Místo toho objekt DataRelation sleduje relaci mezi tabulkami a udržuje nadřazené a podřízené záznamy synchronizované.

## <a name="datarelation-objects-and-constraints"></a>Objekty a omezení DataRelation
 <xref:System.Data.DataRelation>Objekt se také používá k vytvoření a prosazování následujících omezení:

- Jedinečné omezení, které zaručuje, že sloupec v tabulce neobsahuje žádné duplicity.

- Omezení cizího klíče, které lze použít k udržení referenční integrity mezi nadřazenou a podřízenou tabulkou v datové sadě.

  Omezení, která zadáte v <xref:System.Data.DataRelation> objektu, jsou implementována automatickým vytvářením vhodných objektů nebo vlastností nastavení. Pokud vytvoříte omezení cizího klíče pomocí <xref:System.Data.DataRelation> objektu, instance <xref:System.Data.ForeignKeyConstraint> třídy jsou přidány do <xref:System.Data.DataRelation> <xref:System.Data.DataRelation.ChildKeyConstraint%2A> vlastnosti objektu.

  Jedinečné omezení je implementováno buď pouhým nastavením <xref:System.Data.DataColumn.Unique%2A> Vlastnosti datového sloupce `true` nebo přidáním instance <xref:System.Data.UniqueConstraint> třídy do <xref:System.Data.DataRelation> <xref:System.Data.DataRelation.ParentKeyConstraint%2A> vlastnosti objektu. Informace o pozastavení omezení v datové sadě naleznete v tématu vypnutí [omezení při naplňování datové sady](../data-tools/turn-off-constraints-while-filling-a-dataset.md).

### <a name="referential-integrity-rules"></a>Pravidla referenční integrity
 V rámci omezení cizího klíče můžete zadat pravidla referenční integrity, která se aplikují na tři body:

- Když se aktualizuje nadřazený záznam

- Při odstranění nadřazeného záznamu

- Když je změna přijata nebo zamítnuta

  Pravidla, která lze provést, jsou uvedena ve <xref:System.Data.Rule> výčtu a jsou uvedena v následující tabulce.

|Pravidlo omezení pro cizí klíč|Akce|
|----------------------------------|------------|
|<xref:System.Data.Rule>|Změna (aktualizace nebo odstranění) vytvořená u nadřazeného záznamu je také vytvořena v souvisejících záznamech v podřízené tabulce.|
|<xref:System.Data.Rule>|Podřízené záznamy nejsou odstraněny, ale cizí klíč v podřízených záznamech je nastaven na hodnotu <xref:System.DBNull> . S tímto nastavením můžou být podřízené záznamy ponechány jako "osamocené" – to znamená, že nemají žádný vztah k nadřazeným záznamům. **Poznámka:**  Použití tohoto pravidla může mít za následek neplatnou data v podřízené tabulce.|
|<xref:System.Data.Rule>|Cizí klíč v souvisejících podřízených záznamech je nastaven na výchozí hodnotu (zavedenou <xref:System.Data.DataColumn.DefaultValue%2A> vlastností sloupce).|
|<xref:System.Data.Rule>|V souvisejících podřízených záznamech není provedena žádná změna. S tímto nastavením můžou podřízené záznamy obsahovat odkazy na neplatné nadřazené záznamy.|

 Další informace o aktualizacích v tabulkách datové sady najdete v tématu [uložení dat zpět do databáze](../data-tools/save-data-back-to-the-database.md).

### <a name="constraint-only-relations"></a>Vztahy pouze s omezením
 Při vytváření <xref:System.Data.DataRelation> objektu máte možnost určit, že relace bude použita pouze k vynutit omezení – to znamená, že nebude použito také pro přístup k souvisejícím záznamům. Pomocí této možnosti můžete vygenerovat datovou sadu, která je poněkud efektivnější a která obsahuje méně metod, než je jedna se schopností souvisejících záznamů. Nebudete ale mít přístup k souvisejícím záznamům. Relace jenom s omezením například brání v odstranění nadřazeného záznamu, který má podřízené záznamy a nelze k podřízeným záznamům přistupovat prostřednictvím nadřazeného objektu.

## <a name="manually-creating-a-data-relation-in-the-dataset-designer"></a>Ruční vytvoření relace dat v Návrhář datových sad
 Při vytváření datových tabulek pomocí nástrojů pro návrh dat v aplikaci Visual Studio se vztahy vytvoří automaticky, pokud se informace mohou shromažďovat ze zdroje dat. Pokud ručně přidáte tabulky dat z karty **datová sada** na **panelu nástrojů**, bude pravděpodobně nutné vytvořit relaci ručně. Informace o tom, jak vytvářet <xref:System.Data.DataRelation> objekty programově, najdete v tématu [Přidání datových vztahů](https://msdn.microsoft.com/library/a4a564fb-c1c4-4135-b6c2-b030e51195e4).

 Relace mezi tabulkami dat se zobrazí jako řádky v **Návrhář datových sad**s klíčovým a nekonečným glyfem znázorňujícím aspekt vztahu 1: n. Ve výchozím nastavení se na návrhové ploše nezobrazí název relationshipCommentEnd ID = ' 1c8c78e19b7fa441 '.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-create-a-relationship-between-two-data-tables"></a>Vytvoření relace mezi dvěma datovými tabulkami

1. Otevřete datovou sadu v **Návrhář datových sad**. Další informace najdete v tématu [Postup: otevření datové sady v Návrhář datových sad](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).

2. Přetáhněte objekt **vztahu** z panelu nástrojů **datové sady** do tabulky podřízených dat v relaci.

     Otevře se dialogové okno **vztah** , naplnění **podřízeného pole tabulky** tabulkou, do které jste přetáhli objekt **relace** .

3. Vyberte nadřazenou tabulku z pole **nadřazená tabulka** . Nadřazená tabulka obsahuje záznamy na straně jedna relace 1: n.

4. Ověřte, že je v poli **podřízená tabulka** zobrazená správná podřízená tabulka. Podřízená tabulka obsahuje záznamy na straně "mnoho" relace 1: n.

5. Do pole **název** zadejte název vztahu nebo ponechte výchozí název založený na vybraných tabulkách. Toto je název skutečného <xref:System.Data.DataRelation> objektu v kódu.

6. Vyberte sloupce, které se připojují k tabulkám ve **sloupcích klíče** a v seznamech **cizích klíčů** .

7. Vyberte, zda chcete vytvořit relaci, omezení nebo obojí. Informace najdete v tématu [Úvod do objektů DataRelation](https://msdn.microsoft.com/library/89d8a881-8265-41f2-a88b-61311ab06192).

8. Zaškrtněte nebo zrušte zaškrtnutí políčka **vnořené relace** . Výběrem této možnosti nastavíte <xref:System.Data.DataRelation.Nested%2A> vlastnost na hodnotu `true` a způsobí to, že podřízené řádky relace budou vnořené do nadřazeného sloupce, pokud jsou tyto řádky zapsány jako data XML nebo synchronizovány s <xref:System.Xml.XmlDataDocument> . Další informace najdete v tématu [vnořování datových vztahů](https://msdn.microsoft.com/library/9530f9c9-dd98-4b93-8cdb-40d7f1e8d0ab).

9. Nastavte pravidla, která se mají vyhovět při provádění změn záznamů v těchto tabulkách. Další informace naleznete v tématu <xref:System.Data.Rule>.

10. Kliknutím na tlačítko **OK** vytvořte relaci. Čára relace se zobrazí v návrháři mezi dvěma tabulkami.

#### <a name="to-display-a-relation-name-in-the-dataset-designer"></a>Chcete-li zobrazit název vztahu v Návrhář datových sad

1. Otevřete datovou sadu v **Návrhář datových sad**. Další informace najdete v tématu [Postup: otevření datové sady v Návrhář datových sad](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).

2. V nabídce **data** vyberte příkaz **Zobrazit popisky relací** , aby se zobrazil název vztahu. Zrušením zaškrtnutí tohoto příkazu skryjte název vztahu.
