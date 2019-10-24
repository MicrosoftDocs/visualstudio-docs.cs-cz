---
title: Referenční dokumentace jazyka přímého značení grafů (DGML)
ms.date: 11/04/2016
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b038acd9527cae197223e288349e431e81ea6dd6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748412"
---
# <a name="directed-graph-markup-language-dgml-reference"></a>Referenční dokumentace jazyka přímého značení grafů (DGML)

Jazyk DGML (Directed Graph Markup Language) popisuje informace používané pro vizualizaci a provádění analýzy složitosti a je formát používaný k zachování map kódu v aplikaci Visual Studio. Používá k popisu cyklického a acyklickéhoho orientovaného grafu jednoduchý kód XML. Orientovaný graf je sada uzlů, které jsou propojeny pomocí propojení neboli hran. Uzly a propojení mohou být použity pro reprezentaci síťových struktur, jako jsou například prvky v softwarovém projektu.

Všimněte si, že některé verze sady Visual Studio podporují pouze podmnožinu funkcí DGML, viz [podpora verzí pro architektury a nástroje pro modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!NOTE]
> Při úpravách souboru .dgml usnadňuje technologie IntelliSense určení atributů, které jsou k dispozici pro každý prvek, a jejich hodnot. Pro určení barvy v atributu použijte názvy pro běžné barvy, například „Blue“ (modrá) nebo šestnáctkové hodnoty ARGB, jako je například „#ffa0b1c3“. Jazyk DGML používá malou podmnožinu formátů definice barev Windows Presentation Foundation (WPF). Další informace naleznete v tématu [Třída Colors](http://go.microsoft.com/fwlink/?LinkId=182345).

## <a name="DGML"></a>Syntaxe DGML

Následující tabulka popisuje typy prvků, které jsou používány v DGML:

- `<DirectedGraph></DirectedGraph>`

   Tento prvek je kořenovým prvkem dokumentu mapy kódu (. dgml). V rámci tohoto prvku jsou všechny ostatní prvky jazyka DGML.

   Následující seznam popisuje volitelné atributy, které lze vložit:

   `Background` – barva pozadí mapy

   `BackgroundImage` – umístění souboru obrázku, který se má použít jako pozadí mapy.

   `GraphDirection` – Pokud je mapa nastavená na rozložení stromu (`Sugiyama`), uspořádejte uzly tak, aby většina odkazů pokračovala v zadaném směru: `TopToBottom`, `BottomToTop`, `LeftToRight` nebo `RightToLeft`. Viz [Změna rozložení mapy](../modeling/browse-and-rearrange-code-maps.md#Selecting).

   `Layout` – nastavte mapu na následující rozložení: `None`, `Sugiyama` (rozložení stromové struktury), `ForceDirected` (rychlé clustery) nebo `DependencyMatrix`. Viz [Změna rozložení mapy](../modeling/browse-and-rearrange-code-maps.md#Selecting).

   `NeighborhoodDistance` – když je mapa nastavená na rozložení stromu nebo rychlé clustery, zobrazí se jenom ty uzly, které jsou zadané číslo (1-7) z odkazů z vybraných uzlů. Viz [Změna rozložení mapy](../modeling/browse-and-rearrange-code-maps.md#Selecting).

   Příklad:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" Background="Blue" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        ...
     </Nodes>
     <Links>
        ...
     </Links>
     <Categories>
        ...
     </Categories>
     <Properties>
        ...
     </Properties>
  </DirectedGraph>
  ```

- `<Nodes></Nodes>`

   Tento volitelný prvek obsahuje seznam `<Node/>` prvků, které definují uzly na mapě. Další informace naleznete v tématu `<Node/>` element.

  > [!NOTE]
  > Když odkazujete na nedefinovaný uzel v prvku `<Link/>`, mapa automaticky vytvoří prvek `<Node/>`.

   Příklad:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node ... />
     </Nodes>
     <Links>
        <Link ... />
     </Links>
  </DirectedGraph>
  ```

- `<Node/>`

   Tento prvek definuje jeden uzel. Zobrazí se v seznamu `<Nodes><Nodes/>` prvků.

   Tento prvek musí obsahovat následující atributy:

   `Id` – jedinečný název uzlu a výchozí hodnotu atributu `Label`, pokud není zadán žádný jiný atribut `Label`. Tento název musí odpovídat atributu `Source` nebo `Target` odkazu, který na něj odkazuje.

   Následující seznam popisuje některé volitelné atributy, které lze vložit:

   `Label` – zobrazovaný název uzlu.

   Atributy stylu. Další informace najdete v tématu [Přizpůsobení map kódu úpravou souborů DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

   `Category` – název kategorie, která identifikuje prvky, které sdílejí tento atribut. Další informace naleznete v tématu `<Category/>` element.

   `Property` – název vlastnosti, která identifikuje prvky, které mají stejnou hodnotu vlastnosti. Další informace naleznete v tématu `<Property/>` element.

   `Group` – Pokud uzel obsahuje další uzly, nastavte tento atribut na `Expanded` nebo `Collapsed` pro zobrazení nebo skrytí jeho obsahu. Musí existovat `<Link/>` element, který obsahuje atribut `Category="Contains"` a určuje nadřazený uzel jako zdrojový uzel a podřízený uzel jako cílový uzel. Viz [prvky kódu skupiny](../modeling/customize-code-maps-by-editing-the-dgml-files.md#OrganizeNodes).

   `Visibility` – nastavte tento atribut na `Visible`, `Hidden` nebo `Collapsed`. Používá `System.Windows.Visibility`. Viz [Skrytí nebo zobrazení uzlů a propojení](../modeling/browse-and-rearrange-code-maps.md#HidingShowing).

   `Reference` – nastavte tento atribut tak, aby se připojovat k dokumentu nebo adrese URL. Viz [odkazování dokumentů nebo adres URL na prvky kódu a odkazy](../modeling/customize-code-maps-by-editing-the-dgml-files.md#AddReferences).

   Příklad:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node Id="Driver" Label="Student" Category="Person" />
        <Node Id="Passenger" Label="Instructor" Category="Person" />
        <Node Id="Car" Label="Car" Category="Automobile" />
        <Node Id="Truck" Label="Truck" Category="Automobile" />
     </Nodes>
     <Links>
        <Link ... />
     </Links>
     <Categories>
        <Category Id="Person" Background="Orange" />
        <Category Id="Automobile" Background="Yellow"/>
     </Categories>
  </DirectedGraph>
  ```

- `<Links></Links>`

   Tento prvek obsahuje seznam `<Link>` prvků, které definují propojení mezi uzly. Další informace naleznete v tématu `<Link/>` element.

   Příklad:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Links>
        <Link ... />
     </Links>
  </DirectedGraph>
  ```

- `<Link/>`

   Tento prvek definuje jedno propojení, které připojuje zdrojový uzel k cílovému uzlu. Zobrazí se v seznamu `<Links></Links>` prvků.

  > [!NOTE]
  > Pokud tento prvek odkazuje na nedefinovaný uzel, dokument mapy automaticky vytvoří uzel, který má zadané atributy, pokud existují.

   Tento prvek musí obsahovat následující atributy:

   `Source` – zdrojový uzel odkazu

   `Target` – cílový uzel odkazu

   Následující seznam popisuje některé volitelné atributy, které lze vložit:

   `Label` – zobrazovaný název odkazu

   Atributy stylu. Další informace najdete v tématu [Přizpůsobení map kódu úpravou souborů DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

   `Category` – název kategorie, která identifikuje prvky, které sdílejí tento atribut. Další informace naleznete v tématu `<Category/>` element.

   `Property` – název vlastnosti, která identifikuje prvky, které mají stejnou hodnotu vlastnosti. Další informace naleznete v tématu `<Property/>` element.

   Příklad:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node Id="Driver" Label="Student" Category="Person" />
        <Node Id="Passenger" Label="Instructor" Category="Person" />
        <Node Id="Car" Label="Car" Category="Automobile" />
        <Node Id="Truck" Label="Truck" Category="Automobile" />
     </Nodes>
     <Links>
        <Category Id="Person" Background="Orange" />
        <Category Id="Automobile" Background="Yellow"/>
        <Link Source="Driver" Target="Car" Label="Passed" Stroke="Black" Background="Green" Category="PassedTest" />
        <Link Source="Driver" Target="Truck" Label="Failed" Stroke="Black" Background="Red" Category="PassedTest" />
     </Links>
  </DirectedGraph>
  ```

- `<Categories></Categories>`

   Tento prvek obsahuje seznam `<Category/>` prvků. Další informace naleznete v tématu `<Category/>` element.

   Příklad:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Categories>
         <Category ... />
     </Categories>
  </DirectedGraph>
  ```

- `<Category/>`

   Tento prvek definuje atribut `Category`, který slouží k identifikaci prvků, které sdílejí tento atribut. Atribut `Category` lze použít k uspořádání prvků map, k poskytnutí sdílených atributů prostřednictvím dědičnosti nebo k definování dalších metadat.

   Tento prvek musí obsahovat následující atributy:

   `Id` – jedinečný název kategorie a výchozí hodnota atributu `Label`, pokud není zadán žádný jiný atribut `Label`.

   Následující seznam popisuje některé volitelné atributy, které lze vložit:

   `Label` – popisný název kategorie.

   `BasedOn` – Nadřazená kategorie, ze které dědí `<Category/>` aktuálního prvku.

   V příkladu pro tento prvek kategorie `FailedTest` dědí svůj `Stroke` atribut z kategorie `PassedTest`. Viz "vytvoření hierarchických kategorií" v tématu [Přizpůsobení map kódu úpravou souborů DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

   Kategorie také poskytují některé základní chování šablony, které řídí vzhled uzlů a propojení, když jsou zobrazeny na mapě. Další informace najdete v tématu [Přizpůsobení map kódu úpravou souborů DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

   Příklad:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node Id="Driver" Label="Driver" Category="Person" />
        <Node Id="Car" Label="Car" Category="Automobile" />
        <Node Id="Truck" Label="Truck" Category="Automobile" />
        <Node Id="Passenger" Category="Person" />
     </Nodes>
     <Links>
        <Link Source="Driver" Target="Car" Label="Passed" Category="PassedTest" />
        <Link Source="Driver" Target="Truck" Label="Failed" Category="FailedTest" />
     </Links>
     <Categories>
        <Category Id="Person" Background="Orange" />
        <Category Id="Automobile" Background="Yellow"/>
        <Category Id="PassedTest" Label="Passed" Stroke="Black" Background="Green" />
        <Category Id="FailedTest" Label="Failed" BasedOn="PassedTest" Background="Red" />
     </Categories>
  </DirectedGraph>
  ```

- `<Properties></Properties>`

   Tento prvek obsahuje seznam `<Property/>` prvků. Další informace naleznete v tématu `<Property/>` element.

   Příklad:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Properties>
         <Property ... />
     </Properties>
  </DirectedGraph>
  ```

- `<Property/>`

   Tento prvek definuje atribut `Property`, který můžete použít k přiřazení hodnoty k jakémukoli DGML elementu nebo atributu, včetně kategorií a dalších vlastností.

   Tento prvek musí obsahovat následující atributy:

  - `Id` – jedinečný název vlastnosti a výchozí hodnota atributu `Label`, pokud není zadán žádný jiný atribut `Label`.

  - `DataType` – typ dat uložených vlastností

    Chcete-li, aby se vlastnost zobrazila v okně **vlastnosti** , použijte vlastnost `Label` k zadání zobrazovaného názvu vlastnosti.

    Viz [přiřazení kategorií k prvkům kódu a odkazům](../modeling/customize-code-maps-by-editing-the-dgml-files.md#AssignCategories).

    Příklad:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node Id="Driver" Label="Driver" Category="Person" DrivingAge="18"/>
        <Node Id="Car" Label="Car" Category="Automobile" />
        <Node Id="Truck" Label="Truck" Category="Automobile" />
        <Node Id="Passenger" Category="Person" />
     </Nodes>
     <Links>
        <Link Source="Driver" Target="Car" Label="Passed" Category="PassedTest" />
        <Link Source="Driver" Target="Truck" Label="Failed" Category="FailedTest" />
     </Links>
     <Categories>
        <Category Id="Person" Background="Orange" />
        <Category Id="Automobile" Background="Yellow"/>
        <Category Id="PassedTest" Label="Passed" Stroke="Black" Background="Green" />
        <Category Id="FailedTest" Label="Failed" BasedOn="PassedTest" Background="Red" />
     </Categories>
     <Properties>
         <Property Id="DrivingAge" Label="Driving Age" DataType="System.Int32" />
     </Properties>
  </DirectedGraph>
  ```

### <a name="AddAlias"></a>Aliasy pro běžně používané cesty

Nahrazení běžně používaných cest aliasy pomáhá zmenšit velikost souboru .dgml a snižuje čas potřebný k načtení nebo uložení souboru. Chcete-li vytvořit alias, přidejte část `<Paths></Paths>` na konec souboru. dgml. V této části přidejte `<Path/>` element pro definování aliasu pro cestu:

```xml
<Paths>
   <Path Id="MyPathAlias" Value="C:\...\..." />
</Paths>
```

Chcete-li odkazovat na alias z prvku v souboru. dgml, vložte `Id` elementu \<Path/> znakem dolaru ($) a závorkami (()):

```xml
<Nodes>
   <Node Id="MyNode" Reference="$(MyPathAlias)MyDocument.txt" />
</Nodes>
<Properties>
   <Property Id="Reference" Label="My Document" DataType="System.String" IsReference="True" />
</Properties>
```

## <a name="see-also"></a>Viz také:

- [Mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md)
- [Použití map kódu k ladění aplikací](../modeling/use-code-maps-to-debug-your-applications.md)
- [Nalezení potenciálních problémů pomocí analyzátorů mapy kódu](../modeling/find-potential-problems-using-code-map-analyzers.md)