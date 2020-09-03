---
title: Přizpůsobení map kódu úpravou souborů DGML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- dependency graphs, creating path aliases
- dependency graphs, linking items to nodes
- graph documents, creating path aliases
- dependency graphs, grouping nodes
- graph documents, editing
- graph documents, linking items to nodes
- graph documents, customizing
- graph documentings, assigning categories and properties
- dependency graphs, editing
- dependency graphs, customizing
- graph documents, grouping nodes
- dependency graphs, assigning categories and properties
ms.assetid: a2e141f4-4fd8-4611-b236-6b9e7bc54fc1
caps.latest.revision: 93
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5d4f3f701bf0a6d11c40e4cc4435b1bbe910f55f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663133"
---
# <a name="customize-code-maps-by-editing-the-dgml-files"></a>Přizpůsobení map kódu úpravou souborů DGML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Chcete-li přizpůsobit mapu kódu, můžete upravit soubor. dgml (Directed Graph Markup Language) mapy. Můžete například upravit prvky a zadat vlastní styly, přiřadit vlastnosti a kategorie k prvkům kódu a propojením nebo propojit dokumenty nebo adresy URL s prvky kódu nebo odkazy. Další informace o elementech DGML naleznete v tématu [Reference k jazyku DGML (Direct Graph Markup Language)](../modeling/directed-graph-markup-language-dgml-reference.md).

 Upravte soubor. dgml mapy kódu v textovém editoru nebo editoru XML. Pokud je mapa součástí řešení sady Visual Studio, vyberte ji v **Průzkumník řešení**, otevřete místní nabídku a zvolte možnost **otevřít v** **editoru XML (text)**.

> [!NOTE]
> Chcete-li vytvořit mapy kódu, je nutné mít Visual Studio Enterprise. Když upravíte mapu kódu v aplikaci Visual Studio, vyčistí všechny nepoužívané prvky DGML a atributy jejich odstraněním při uložení souboru. dgml. Také automaticky vytvoří prvky kódu při ručním přidání nových odkazů. Při ukládání souboru .dgml mohou být všechny atributy, které byly přidány do prvku, uspořádány podle abecedy.

## <a name="group-code-elements"></a><a name="OrganizeNodes"></a> Seskupit prvky kódu
 Můžete přidat nové skupiny nebo převést existující uzly na skupinu.

1. Otevřete soubor. dgml v textovém editoru nebo editoru XML.

2. Chcete-li převést prvek kódu na skupinu, vyhledejte `<Node/>` prvek pro daný prvek kódu.

    \- ani

    Chcete-li přidat novou skupinu, vyhledejte `<Nodes>` část. Přidejte nový `<Node/>` element.

3. V `<Node/>` elementu přidejte `Group` atribut pro určení, zda se skupina zobrazuje jako rozbalená nebo sbalená. Příklad:

   ```xml
   <Nodes>
      <Node Id="MyFirstGroup" Group="Expanded" />
      <Node Id="MySecondGroup" Group="Collapsed" />
   </Nodes>
   ```

4. V `<Links>` části se ujistěte, že `<Link/>` pro každou relaci mezi prvkem kódu skupiny a jeho podřízenými prvky kódu existují prvky, které mají následující atributy:

   - `Source`Atribut, který určuje prvek kódu skupiny

   - `Target`Atribut, který určuje podřízený element kódu

   - `Category`Atribut, který určuje `Contains` vztah mezi prvkem kódu skupiny a jeho podřízeným elementem kódu

     Příklad:

   ```xml
   <Links>
      <Link Category="Contains" Source="MyFirstNewGroup" Target="FirstGroupChildOne" />
      <Link Category ="Contains" Source="MyFirstNewGroup" Target="FirstGroupChildTwo" />
      <Link Category ="Contains" Source="MySecondNewGroup" Target="SecondGroupChildOne" />
      <Link Category="Contains" Source="MySecondNewGroup" Target="SecondGroupChildTwo" />
   </Links>
   ```

    Další informace o `Category` atributu naleznete v tématu [přiřazení kategorií k prvkům kódu a propojením](#AssignCategories).

## <a name="change-the-style-of-the-map"></a><a name="ChangeGraphStyle"></a> Změnit styl mapy
 Můžete změnit barvu pozadí a barvu ohraničení mapy úpravou souboru. dgml mapy. Chcete-li změnit styl prvků kódu a odkazů, přečtěte si téma [Změna stylu prvků kódu a odkazů](#Highlight).

1. Otevřete soubor. dgml v textovém editoru nebo editoru XML.

2. V `<DirectedGraph>` elementu přidejte libovolné z následujících atributů pro změnu stylu:

     Barva pozadí

    ```xml
    Background="ColorNameOrHexadecimalValue"
    ```

     Barva ohraničení

    ```xml
    Stroke="StrokeValue"
    ```

     Příklad:

    ```xml
    <DirectedGraph Background="Green" xmlns="http://schemas.microsoft.com/vs/2009/dgml" >
       ...
       ...
    </DirectedGraph>
    ```

## <a name="change-the-style-of-code-elements-and-links"></a><a name="Highlight"></a> Změna stylu prvků kódu a odkazů

### <a name="CreateCustomStyles"></a>
 Vlastní styly lze použít pro následující prvky kódu:

- Jednoduché prvky kódu a odkazy

- Skupiny prvků kódu a odkazy

- Skupiny prvků kódu a odkazy na základě určitých podmínek

> [!TIP]
> Pokud máte opakující se styly napříč mnoha prvky kódu nebo odkazy, můžete zvážit použití kategorie na tyto prvky kódu nebo odkazy a poté použití stylu na tuto kategorii. Další informace naleznete v tématu [přiřazení kategorií prvkům kódu a propojení](#AssignCategories) a [přiřazení vlastností prvkům kódu a propojením](#AssignProperties).

##### <a name="to-apply-a-custom-style-to-a-single-code-element"></a>Použití vlastního stylu na jeden prvek kódu

1. Otevřete soubor. dgml v textovém editoru nebo editoru XML.

2. Vyhledejte element elementu kódu `<Node/>` . Přidejte libovolné z těchto atributů pro přizpůsobení stylu:

     Barva pozadí

    ```xml
    Background="ColorNameOrHexadecimalValue"
    ```

     Obrys

    ```xml
    Stroke="ColorNameOrHexadecimalValue"
    ```

     Tloušťka obrysu

    ```xml
    StrokeThickness="StrokeValue"
    ```

     Barva textu

    ```xml
    Foreground="ColorNameOrHexadecimalValue"
    ```

     Ikona

    ```xml
    Icon="IconFilePathLocation"
    ```

     Velikost textu

    ```xml
    FontSize="FontSizeValue"
    ```

     Textový typ

    ```xml
    FontFamily="FontFamilyName"
    ```

     Tloušťka textu

    ```xml
    FontWeight="FontWeightValue"
    ```

     Styl textu

    ```xml
    FontStyle="FontStyleName"
    ```

     Například můžete zadat `Italic` jako styl textu.

     Textura

    ```xml
    Style="Glass"
    ```

     - ani

    ```xml
    Style="Plain"
    ```

     Obrazec

     Chcete-li tvar nahradit ikonou, nastavte `Shape` vlastnost na hodnotu `None` a nastavte `Icon` vlastnost na cestu k souboru ikony.

    ```xml
    Shape="ShapeFilePathLocation"
    ```

     Příklad:

    ```xml
    <Nodes>
       <Node Id="MyNode" Background="#FF008000" Stroke="#FF000000"
       Foreground="#FFFFFFFF" Icon="...\Icons\Globe.png"/>
    </Nodes>
    ```

##### <a name="to-apply-a-custom-style-to-a-single-link"></a>Aplikace vlastního stylu na jedno propojení

1. Otevřete soubor. dgml v textovém editoru nebo editoru XML.

2. Vyhledejte `<Link/>` prvek, který obsahuje jak názvy elementu zdrojového kódu, tak element cílového kódu.

3. V `<Link/>` elementu přidejte libovolný z následujících atributů pro přizpůsobení stylu:

     Barva obrysu a šipky

    ```xml
    Stroke="ColorNameOrHexadecimalValue"
    ```

     Tloušťka obrysu

    ```xml
    StrokeThickness="StrokeValue"
    ```

     Styl obrysu

    ```xml
    StrokeDashArray="StrokeArrayValues"
    ```

     Příklad:

    ```xml
    <Links>
       <Link Source="MyFirstNode" Target="MySecondNode" Background="Green" Stroke="#FF000000" StrokeDashArray="2,2"/>
    </Links>
    ```

##### <a name="to-apply-custom-styles-to-a-group-of-code-elements-or-links"></a>Použití vlastních stylů pro skupinu prvků kódu nebo odkazů

1. Otevřete soubor. dgml v textovém editoru nebo editoru XML.

2. Pokud `<Styles></Styles>` element neexistuje, přidejte jej pod `<DirectedGraph></DirectedGraph>` element za `<Links></Links>` element.

3. V `<Styles></Styles>` elementu pod `<Style/>` prvkem a určete následující atributy:

   - `TargetType="Node` &#124; `Link | Graph"`

   - `GroupLabel="`*NameInLegendBox*`"`

   - `ValueLabel="`*NameInStylePickerBox*`"`

     Pro použití vlastního stylu na všechny cílové typy nepoužívejte podmínku.

##### <a name="to-apply-a-conditional-style-to-groups-of-code-elements-or-links"></a>Použití podmíněného stylu pro skupiny prvků kódu nebo odkazů

1. Otevřete soubor. dgml v textovém editoru nebo editoru XML.

2. V `<Style/>` elementu přidejte `<Condition/>` element, který obsahuje `Expression` atribut pro určení výrazu, který vrací logickou hodnotu.

    Příklad:

   ```xml
   <Condition Expression="MyCategory"/>
   ```

    - ani

   ```xml
   <Condition Expression="MyCategory > 100"/>
   ```

    - ani

   ```xml
   <Condition Expression="HasCategory('MyCategory')"/>
   ```

    Tento výraz používá následující syntaxi BNF (Backus-Naur Form):

    \<Expression> :: = \<BinaryExpression> &#124; \<UnaryExpression> &#124; "(" \<Expression> ) "&#124; \<MemberBindings> &#124; \<Literal> &#124; \<Number>

    \<BinaryExpression>::= \<Expression> \<Operator>\<Expression>

    \<UnaryExpression> ::= "!" \<Expression> &#124; "+" \<Expression> &#124; "-" \<Expression>

    \<Operator> :: = "<" &#124; " \<=" &#124; "=" &#124; "> =" &#124; ">" &#124; "! =" &#124; "nebo" &#124; "a" &#124; "+" &#124; "*" &#124; "/" &#124; "-"

    \<MemberBindings> :: = \<MemberBindings> &#124; \<MemberBinding> "." \<MemberBinding>

    \<MemberBinding> :: = \<MethodCall> &#124; \<PropertyGet>

    \<MethodCall> ::= \<Identifier> "(" \<MethodArgs> ")"

    \<PropertyGet> :: = Identifikátor

    \<MethodArgs> :: = \<Expression> &#124; \<Expression> "," \<MethodArgs> &#124; \<empty>

    \<Identifier> ::= [^. ]*

    \<Literal> :: = řetězcový literál s jedním nebo dvojitým uvozovkami

    \<Number> :: = řetězec číslic s volitelnou desetinnou čárkou

    Můžete zadat více `<Condition/>` prvků, které musí všechny mít hodnotu true pro použití stylu.

3. Na dalším řádku za `<Condition/>` prvkem přidejte jeden nebo více `<Setter/>` prvků pro určení `Property` atributu a fixní `Value` atribut nebo počítaný atribut, který `Expression` má být použit pro mapu, prvky kódu nebo odkazy, které splňují podmínku.

    Příklad:

   ```xml
   <Setter Property="BackGround" Value="Green"/>
   ```

   Jako jednoduchý kompletní příklad následující podmínka Určuje, že se prvek kódu zobrazuje zeleně nebo červeně na základě toho, jestli `Passed` je jeho kategorie nastavená na `True` nebo `False` :

```xml
<?xml version="1.0" encoding="utf-8"?>
<DirectedGraph xmlns="http://schemas.microsoft.com/vs/2009/dgml">
   <Nodes>
      <Node Id="MyFirstNode" Passed="True" />
      <Node Id="MySecondNode" Passed="False" />
   </Nodes>
   <Links>
   </Links>
   <Styles>
      <Style TargetType="Node" GroupLabel="Passed" ValueLabel="True">
         <Condition Expression="Passed='True'"/>
         <Setter Property="Background" Value="Green"/>
      </Style>
      <Style TargetType="Node" GroupLabel="Passed" ValueLabel="False">
         <Condition Expression="Passed='False'"/>
         <Setter Property="Background" Value="Red"/>
      </Style>
   </Styles>
</DirectedGraph>
```

 Následující tabulka obsahuje některé ukázkové podmínky, které lze použít:

 Nastavte velikost písma jako funkci počtu řádků kódu, čímž se také změní velikost elementu kódu. Tento příklad používá jeden podmíněný výraz pro nastavení více vlastností `FontSize` a `FontFamily` .

```xml
<?xml version="1.0" encoding="utf-8"?>
<DirectedGraph xmlns="http://schemas.microsoft.com/vs/2009/dgml">
<Nodes>
   <Node Id="Class1" LinesOfCode ="200" />
   <Node Id="Class2" LinesOfCode ="1000" />
   <Node Id="Class3" LinesOfCode ="20" />
</Nodes>
<Properties>
   <Property Id="LinesOfCode" Label="LinesOfCode" Description="LinesOfCode" DataType="System.Int32" />
</Properties>
<Styles>
   <Style TargetType="Node" GroupLabel="LinesOfCode" ValueLabel="Function">
      <Condition Expression="LinesOfCode > 0" />
      <Setter Property="FontSize" Expression="Math.Max(9,Math.Sqrt(LinesOfCode))" />
      <Setter Property="FontFamily" Value="Papyrus" />
   </Style>
</Styles>
</DirectedGraph>
```

 Nastaví barvu pozadí prvku kódu na základě `Coverage` Vlastnosti. Styly jsou vyhodnocovány v pořadí, ve kterém jsou zobrazeny, podobně jako `if-else` příkazy.

 V tomto příkladu:

1. Pokud `Coverage` je > 80, nastavte `Background` vlastnost na zelenou.

2. Jinak `Coverage` , pokud je > 50, nastavte `Background` vlastnost na odstín oranžová na základě hodnoty `Coverage` Vlastnosti.

3. V opačném případě nastavte `Background` vlastnost na odstín červené na základě hodnoty `Coverage` Vlastnosti.

```xml
<?xml version="1.0" encoding="utf-8"?>
<DirectedGraph xmlns="http://schemas.microsoft.com/vs/2009/dgml">
<Nodes>
   <Node Id="Class1" Coverage="58" />
   <Node Id="Class2" Coverage="95" />
   <Node Id="Class3" Coverage="32" />
</Nodes>
<Properties>
   <Property Id="Coverage" Label="Coverage" Description="Code coverage as a percentage of blocks" DataType="Double" />
</Properties>
<Styles>
   <Style TargetType="Node" GroupLabel="Coverage" ValueLabel="Good">
      <Condition Expression="Coverage > 80" />
      <Setter Property="Background" Value="Green" />
   </Style>
   <Style TargetType="Node" GroupLabel="Coverage" ValueLabel="OK">
      <Condition Expression="Coverage > 50" />
      <Setter Property="Background" Expression="Color.FromRgb(180 * Math.Max(1, (80 - Coverage) / 30), 180, 0)" />
   </Style>
   <Style TargetType="Node" GroupLabel="Coverage" ValueLabel="Bad">
      <Setter Property="Background" Expression="Color.FromRgb(180, 180 * Coverage / 50, 0)" />
   </Style>
</Styles>
</DirectedGraph>
```

 Nastavte `Shape` vlastnost na `None` tak, aby ikona nahradila tvar. Pomocí `Icon` vlastnosti určete umístění ikony.

```xml
<DirectedGraph xmlns="http://schemas.microsoft.com/vs/2009/dgml">
<Nodes>
   <Node Id="Automation" Category="Test" Label="Automation" />
   <Node Id="C# Provider" Category="Provider" Label="C# Provider" />
</Nodes>
<Categories>
   <Category Id="Provider" Icon="...\Icons\Module.png" Shape="None" />
   <Category Id="Test" Icon="...\Icons\Page.png" Shape="None" />
</Categories>
<Properties>
   <Property Id="Icon" DataType="System.String" />
   <Property Id="Label" Label="Label" Description="Displayable label of an Annotatable object" DataType="System.String" />
   <Property Id="Shape" DataType="System.String" />
</Properties>
<Styles>
   <Style TargetType="Node" GroupLabel="Group" ValueLabel="Has category">
      <Condition Expression="HasCategory('Group')" />
      <Setter Property="Background" Value="#80008080" />
   </Style>
   <Style TargetType="Node">
      <Setter Property="HorizontalAlignment" Value="Center" />
   </Style>
</Styles>
</DirectedGraph>
```

## <a name="assign-properties-to-code-elements-and-links"></a><a name="AssignProperties"></a> Přiřadit vlastnosti k prvkům kódu a odkazům
 Můžete uspořádat prvky kódu a odkazy tím, že jim přiřadíte vlastnosti. Můžete například vybrat prvky kódu, které mají specifické vlastnosti, abyste je mohli seskupit, změnit jejich styl nebo je skrýt.

#### <a name="to-assign-a-property-to-a-code-element"></a>Přiřazení vlastnosti prvku kódu

1. Otevřete soubor. dgml v textovém editoru nebo editoru XML.

2. Vyhledejte `<Node/>` prvek pro daný prvek kódu. Zadejte název vlastnosti a její hodnotu. Příklad:

    ```xml
    <Nodes>
       <Node Id="MyNode" MyPropertyName="PropertyValue" />
    </Nodes>
    ```

3. Přidejte `<Property/>` element do `<Properties>` oddílu a určete tak atributy, jako je zobrazovaný název a datový typ:

    ```xml
    <Properties>
       <Property Id="MyPropertyName" Label="My Property" DataType="System.DataType"/>
    </Properties>
    ```

#### <a name="to-assign-a-property-to-a-link"></a>Přiřazení vlastnosti propojení

1. Otevřete soubor. dgml v textovém editoru nebo editoru XML.

2. Vyhledejte `<Link/>` prvek, který obsahuje jak názvy elementu zdrojového kódu, tak element cílového kódu.

3. V `<Node/>` elementu zadejte název vlastnosti a její hodnotu. Příklad:

    ```xml
    <Links>
       <Link Source="MyFirstNode" Target="MySecondNode" MyPropertyName="PropertyValue" />
    </Links>
    ```

4. Přidejte `<Property/>` element do `<Properties>` oddílu a určete tak atributy, jako je zobrazovaný název a datový typ:

    ```xml
    <Properties>
       <Property Id="MyPropertyName" Label="My Property Name" DataType="System.DataType"/>
    </Properties>
    ```

## <a name="assign-categories-to-code-elements-and-links"></a><a name="AssignCategories"></a> Přiřazení kategorií prvkům kódu a odkazům
 Následující části ukazují, jak lze uspořádat prvky kódu přiřazením kategorií k těmto prvkům a jak lze vytvořit hierarchické kategorie, které vám pomohou organizovat prvky kódu a přidávat atributy do podřízených kategorií pomocí dědičnosti.

#### <a name="to-assign-a-category-to-a-code-element"></a>Přiřazení kategorie k elementu kódu

- Otevřete soubor. dgml v textovém editoru nebo editoru XML.

- Vyhledejte `<Node/>` prvek prvku kódu, který chcete.

- V `<Node/>` elementu přidejte `Category` atribut pro určení názvu kategorie. Příklad:

    ```xml
    <Nodes>
       <Node Id="MyNode" Category="MyCategory" />
    </Nodes>
    ```

     Přidejte `<Category/>` element do `<Categories>` oddílu, abyste mohli použít `Label` atribut k určení zobrazovaného textu pro tuto kategorii:

    ```xml
    <Categories>
       <Category Id="MyCategory" Label="My Category" />
    </Categories>
    ```

#### <a name="to-assign-a-category-to-a-link"></a>Přiřazení kategorie propojení

1. Otevřete soubor. dgml v textovém editoru nebo editoru XML.

2. Vyhledejte `<Link/>` prvek, který obsahuje jak názvy elementu zdrojového kódu, tak element cílového kódu.

3. V `<Link/>` elementu přidejte `Category` atribut pro určení názvu kategorie. Příklad:

    ```xml
    <Links>
       <Link Source="MyFirstNode" Target="MySecondNode" Category="MyCategory"
    </Links>
    ```

4. Přidejte `<Category/>` element do `<Categories>` oddílu, abyste mohli použít `Label` atribut k určení zobrazovaného textu pro tuto kategorii:

    ```xml
    <Categories>
       <Category Id="MyCategory" Label="My Category" />
    </Categories>
    ```

#### <a name="to-create-hierarchical-categories"></a>Vytvoření hierarchických kategorií

1. Otevřete soubor. dgml v textovém editoru nebo editoru XML.

2. Přidejte `<Category/>` element pro nadřazenou kategorii a pak přidejte `BasedOn` atribut do elementu podřízené kategorie `<Category/>` .

     Příklad:

    ```xml
    <Nodes>
       <Node Id="MyFirstNode" Label="My First Node" Category= "MyCategory" />
       <Node Id="MySecondNode" Label="My Second Node" />
    </Nodes>
    <Links>
       <Link Source="MyFirstNode" Target="MySecondNode" />
    </Links>
    <Categories>
       <Category Id="MyCategory" Label="My Category" BasedOn="MyParentCategory"/>
       <Category Id="MyParentCategory" Label="My Parent Category" Background="Green"/>
    </Categories>
    ```

     V tomto příkladu je pozadí zelené, `MyFirstNode` protože jeho `Category` atribut dědí `Background` atribut `MyParentCategory` .

## <a name="link-documents-or-urls-to-code-elements-and-links"></a><a name="AddReferences"></a> Propojení dokumentů a adres URL s prvky kódu a odkazy
 Dokumenty nebo adresy URL můžete propojit s prvky kódu nebo odkazy úpravou souboru. dgml mapy a přidáním `Reference` atributu do `<Node/>` prvku prvku kódu nebo `<Link/>` elementu pro odkaz. Pak můžete tento obsah otevřít a zobrazit z prvku kódu nebo odkazu. `Reference`Atribut určuje cestu k tomuto obsahu. To může být cesta relativní k umístění souboru .dgml nebo absolutní cesta.

> [!CAUTION]
> Pokud použijete relativní cestu a soubor .dgml bude přesunut do jiného umístění, pak tuto cestu nebude možné interpretovat. Při pokusu o otevření a zobrazení propojeného obsahu, dojde k chybě oznamující, že obsah nelze zobrazit.

 Například může být vhodné propojit následující prvky kódu:

- Chcete-li popsat změny třídy, můžete propojit adresu URL prvku pracovního kódu, dokumentu nebo jiného souboru. dgml k elementu kódu pro třídu.

- Diagram vrstev můžete propojit s prvkem kódu skupiny, který představuje vrstvu v logické architektuře softwaru.

- Chcete-li zobrazit další informace o komponentě, která zpřístupňuje rozhraní, můžete propojit diagram komponent k elementu kódu pro toto rozhraní.

- Propojení prvku kódu s Team Foundation Server pracovní položky nebo chyby nebo nějaké další informace, které se vztahují k elementu kódu.

#### <a name="to-link-a-document-or-url-to-a-code-element"></a>Odkazování dokumentu nebo adresy URL na prvek kódu

1. Otevřete soubor. dgml v textovém editoru nebo editoru XML.

2. Vyhledejte `<Node/>` prvek prvku kódu, který chcete.

3. Proveďte jednu z úloh z následující tabulky:

    Jeden prvek kódu

   - V `<Node/>` elementu nebo `<Link/>` přidejte `Reference` atribut pro určení umístění elementu kódu.

     > [!NOTE]
     > Každý prvek může mít pouze jeden `Reference` atribut.

     Příklad:

   ```xml
   <Nodes>
      <Node Id="MyNode" Reference="MyDocument.txt" />
   </Nodes>
   <Properties>
      <Property Id="Reference" Label="My Document" DataType="System.String" IsReference="True" />
   </Properties>
   ```

    Více elementů kódu

   1. V `<Node/>` elementu nebo `<Link/>` přidejte nový atribut pro určení umístění každého odkazu.

   2. V `<Properties>` části:

      1. Přidejte `<Property/>` element pro každý nový typ odkazu.

      2. Nastavte `Id` atribut na název nového referenčního atributu.

      3. Přidejte `IsReference` atribut a nastavte jej na hodnotu, `True` Chcete-li, aby se odkaz zobrazil v místní nabídce prvku kódu **Přejít na odkaz** .

      4. Použijte `Label` atribut k určení zobrazovaného textu v místní nabídce **Přejít na odkaz** elementu kódu.

      Příklad:

   ```xml
   <Nodes>
      <Node Id="MyNode" SequenceDiagram="MySequenceDiagram.sequencediagram" ActiveBugs="MyActiveBugs.wiq"/>
   </Nodes>
   <Properties>
      <Property Id="SequenceDiagram" Label="My Sequence Diagram" DataType="System.String" IsReference="True" />
      <Property Id="ActiveBugs" Label="Active Bugs" DataType="System.String" IsReference="True" />
   </Properties>
   ```

    Na mapě se název prvku kódu zobrazuje podtrženo. Když otevřete místní nabídku pro prvek kódu nebo odkaz, zobrazí se místní nabídka **Přejít na odkaz** , která obsahuje prvky propojeného kódu, které můžete vybrat.

4. Použijte `ReferenceTemplate` atribut k určení společného řetězce, jako je například adresa URL, která je používána více odkazy namísto opakování řetězce v odkazu.

    `ReferenceTemplate`Atribut určuje zástupný symbol pro hodnotu odkazu. V následujícím příkladu bude `{0}` zástupný symbol v `ReferenceTemplate` atributu nahrazen hodnotami `MyFirstReference` `MySecondReference` atributů a v `<Node/>` elementu pro vytvoření úplné cesty:

   ```xml
   <Nodes>
      <Node Id="MyNode" MyFirstReference="MyFirstDocument" MySecondReference="MySecondDocument"/>
      <Node Id="MySecondNode" MyFirstReference="AnotherFirstDocument" MySecondReference="AnotherSecondDocument"/>
   </Nodes>
   <Properties>
      <Property Id="MyFirstReference" Label="My First Document" DataType="System.String" IsReference="True" ReferenceTemplate="http://www.Fabrikam.com/FirstDocuments/{0}.asp"/>
      <Property Id="MySecondReference" Label="My Second Document" DataType="System.String" IsReference="True" ReferenceTemplate=" http://www.Fabrikam.com/SecondDocuments/{0}.asp"/>
   </Properties>
   ```

5. Chcete-li zobrazit odkazový prvek kódu nebo prvky kódu z mapy, otevřete místní nabídku pro prvek kódu nebo odkaz. Zvolte **Přejít na odkaz** a poté prvek kódu.

## <a name="see-also"></a>Viz také
 [Mapování závislostí ve vašich řešeních](../modeling/map-dependencies-across-your-solutions.md) [použití map kódu k ladění aplikací](../modeling/use-code-maps-to-debug-your-applications.md) [hledání potenciálních problémů pomocí analyzátorů mapy kódu](../modeling/find-potential-problems-using-code-map-analyzers.md) [procházení a změna uspořádání](../modeling/browse-and-rearrange-code-maps.md) [odkazů na jazyk DGML (Direct Graph Markup Language)](../modeling/directed-graph-markup-language-dgml-reference.md) mapy kódu