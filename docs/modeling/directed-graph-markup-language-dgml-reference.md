---
title: Referenční dokumentace jazyka přímého značení grafů (DGML)
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 2eb13ad2b7b18b493e3de48d5b385c01e72857a2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49853841"
---
# <a name="directed-graph-markup-language-dgml-reference"></a>Referenční dokumentace jazyka přímého značení grafů (DGML)

Orientovaný jazyka přímého značení grafů (DGML) popisuje informace, které slouží k vizualizaci a provádět analýzu složitosti a je ve formátu použité k uchování map kódu v sadě Visual Studio. Ji používá jednoduché značky XML pro popis acyklických a cyklických orientované grafy. Orientovaný graf je sada uzlů, které jsou propojeny pomocí propojení neboli hran. Uzly a propojení mohou být použity pro reprezentaci síťových struktur, jako jsou například prvky v softwarovém projektu.

Všimněte si, že některých verzích sady Visual Studio podporují pouze podmnožinu funkcí jazyka DGML, naleznete v tématu [podporované verze pro nástroje architektury a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!NOTE]
> Při úpravách souboru .dgml usnadňuje technologie IntelliSense určení atributů, které jsou k dispozici pro každý prvek, a jejich hodnot. Pro určení barvy v atributu použijte názvy pro běžné barvy, například „Blue“ (modrá) nebo šestnáctkové hodnoty ARGB, jako je například „#ffa0b1c3“. Jazyk DGML používá malou podmnožinu formátů definice barev Windows Presentation Foundation (WPF). Další informace najdete v tématu [třída barvy](http://go.microsoft.com/fwlink/?LinkId=182345).

##  <a name="DGML"></a> Syntaxe jazyka DGML

Následující tabulka popisuje typy prvků, které se používají v jazyce DGML:

- `<DirectedGraph></DirectedGraph>`

   Tento prvek je kořenovým prvkem dokumentu mapy (.dgml) kód. V rámci tohoto prvku jsou všechny ostatní prvky jazyka DGML.

   Následující seznam popisuje volitelné atributy, které lze vložit:

   `Background` – Barva pozadí s mapou

   `BackgroundImage` -Umístění soubor obrázku, který se použije jako pozadí s mapou.

   `GraphDirection` – Když je na mapě nastaven na stromové rozložení (`Sugiyama`), uspořádá uzly tak, aby většina propojení tok v zadaném směru: `TopToBottom`, `BottomToTop`, `LeftToRight`, nebo `RightToLeft`. Zobrazit [změnit rozložení mapy](../modeling/browse-and-rearrange-code-maps.md#Selecting).

   `Layout` – Nastavte mapování na následující rozložení: `None`, `Sugiyama` (stromové rozložení), `ForceDirected` (rychlé clustery), nebo `DependencyMatrix`. Zobrazit [změnit rozložení mapy](../modeling/browse-and-rearrange-code-maps.md#Selecting).

   `NeighborhoodDistance` – Když na mapě nastaven na stromové rozložení nebo rychlé clustery, zobrazit pouze ty uzly, které mají zadaný počet (1-7) propojení z vybraných uzlů. Zobrazit [změnit rozložení mapy](../modeling/browse-and-rearrange-code-maps.md#Selecting).

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

   Tento volitelný prvek obsahuje seznam `<Node/>` prvky, které definují uzly na mapě. Další informace najdete v tématu `<Node/>` elementu.

  > [!NOTE]
  > Při odkazování nedefinovaného uzlu v `<Link/>` vytvoří element, mapy `<Node/>` element automaticky.

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

   Tento prvek definuje jeden uzel. Zobrazí se v rámci `<Nodes><Nodes/>` element seznamu.

   Tento prvek musí obsahovat následující atributy:

   `Id` – Jedinečný název uzlu a výchozí hodnota `Label` atribut, pokud žádný samostatný `Label` je zadán atribut. Tento název musí odpovídat `Source` nebo `Target` atribut odkazu, který na ni odkazuje.

   Následující seznam popisuje některé volitelné atributy, které lze vložit:

   `Label` – Na zobrazovaný název uzlu.

   Atributy stylu. V tématu [Přizpůsobení map kódu úpravou souborů DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

   `Category` – Název kategorie, který identifikuje prvky sdílející tento atribut. Další informace najdete v tématu `<Category/>` elementu.

   `Property` – Název vlastnosti identifikující prvky, které mají stejnou hodnotu vlastnosti. Další informace najdete v tématu `<Property/>` elementu.

   `Group` – Pokud uzel obsahuje další uzly, nastavte tento atribut `Expanded` nebo `Collapsed` zobrazení nebo skrytí jejich obsahu. Musí existovat `<Link/>` element, který zahrnuje `Category="Contains"` atribut a specifikuje nadřazený uzel jako zdrojový uzel a podřízený uzel jako cílový uzel. Zobrazit [seskupit elementy kódu](../modeling/customize-code-maps-by-editing-the-dgml-files.md#OrganizeNodes).

   `Visibility` – Nastavte tento atribut na `Visible`, `Hidden`, nebo `Collapsed`. Používá `System.Windows.Visibility`. Zobrazit [skrýt nebo zobrazit uzlům a propojením](../modeling/browse-and-rearrange-code-maps.md#HidingShowing).

   `Reference` – Nastavte tento atribut na připojení k dokumentu nebo adrese URL. Zobrazit [propojit dokumenty nebo adresy URL s prvky kódu a odkazy](../modeling/customize-code-maps-by-editing-the-dgml-files.md#AddReferences).

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

   Tento prvek obsahuje seznam `<Link>` prvky, které definují propojení mezi uzly. Další informace najdete v tématu `<Link/>` elementu.

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

   Tento prvek definuje jedno propojení, které připojuje zdrojový uzel k cílovému uzlu. Zobrazí se v rámci `<Links></Links>` element seznamu.

  > [!NOTE]
  > Pokud tento prvek odkazuje na nedefinovaný uzel, mapy dokumentu automaticky vytvoří uzel, který má zadané atributy, pokud existuje.

   Tento prvek musí obsahovat následující atributy:

   `Source` – Zdrojový uzel propojení

   `Target` – Cílový uzel propojení

   Následující seznam popisuje některé volitelné atributy, které lze vložit:

   `Label` – Na zobrazovaný název odkazu

   Atributy stylu. V tématu [Přizpůsobení map kódu úpravou souborů DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

   `Category` – Název kategorie, který identifikuje prvky sdílející tento atribut. Další informace najdete v tématu `<Category/>` elementu.

   `Property` – Název vlastnosti identifikující prvky, které mají stejnou hodnotu vlastnosti. Další informace najdete v tématu `<Property/>` elementu.

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

   Tento prvek obsahuje seznam `<Category/>` elementy. Další informace najdete v tématu `<Category/>` elementu.

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

   Tento prvek definuje `Category` atribut, který identifikuje prvky sdílející tento atribut. A `Category` atribut slouží k uspořádání elementů mapy, poskytování sdílených atributů prostřednictvím dědičnosti nebo definování dalších metadat.

   Tento prvek musí obsahovat následující atributy:

   `Id` – Jedinečný název kategorie a výchozí hodnota `Label` atribut, pokud žádný samostatný `Label` je zadán atribut.

   Následující seznam popisuje některé volitelné atributy, které lze vložit:

   `Label` -– Popisný název kategorie.

   `BasedOn` -Nadřazené kategorie, ze kterého `<Category/>` aktuálního elementu dědí.

   V příkladu tohoto prvku `FailedTest` kategorie dědí její `Stroke` atribut z `PassedTest` kategorie. Přečtěte si část "vytvořit hierarchické kategorie" v [mapy kódu přizpůsobit úpravou souborů DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

   Kategorie rovněž poskytují některé základní šablony chování, které řídí vzhled uzlů a propojení, při jejich zobrazení na mapě. V tématu [Přizpůsobení map kódu úpravou souborů DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

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

   Tento prvek obsahuje seznam `<Property/>` elementy. Další informace najdete v tématu `<Property/>` elementu.

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

   Tento prvek definuje `Property` atribut, který můžete použít pro přiřazení hodnoty k libovolnému DGML element nebo atribut, včetně kategorií a dalších vlastností.

   Tento prvek musí obsahovat následující atributy:

  - `Id` – Jedinečný název vlastnosti a výchozí hodnota `Label` atribut, pokud žádný samostatný `Label` je zadán atribut.

  - `DataType` -Typ dat uložených ve vlastnosti

    Pokud chcete, aby vlastnost zobrazila v **vlastnosti** okno, použijte `Label` vlastnosti a určit tak zobrazovaný název vlastnosti.

    Zobrazit [přiřadit kategorie pro prvky kódu a odkazy](../modeling/customize-code-maps-by-editing-the-dgml-files.md#AssignCategories).

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

###  <a name="AddAlias"></a> Aliasy pro běžně používané cesty

Nahrazení běžně používaných cest aliasy pomáhá zmenšit velikost souboru .dgml a snižuje čas potřebný k načtení nebo uložení souboru. Chcete-li vytvořit alias, přidejte `<Paths></Paths>` část na konec souboru .dgml. V této části, přidejte `<Path/>` prvek, který chcete definovat jako alias pro cestu:

```xml
<Paths>
   <Path Id="MyPathAlias" Value="C:\...\..." />
</Paths>
```

Chcete-li odkazovat na alias z prvku v souboru .dgml, uzavřete `Id` z \<cesta / > znakem dolaru ($) a závorkami (()):

```xml
<Nodes>
   <Node Id="MyNode" Reference="$(MyPathAlias)MyDocument.txt" />
</Nodes>
<Properties>
   <Property Id="Reference" Label="My Document" DataType="System.String" IsReference="True" />
</Properties>
```

## <a name="see-also"></a>Viz také

- [Mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md)
- [Použití map kódu k ladění aplikací](../modeling/use-code-maps-to-debug-your-applications.md)
- [Nalezení potenciálních problémů pomocí analyzátorů mapy kódu](../modeling/find-potential-problems-using-code-map-analyzers.md)