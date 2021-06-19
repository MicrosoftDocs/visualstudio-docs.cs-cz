---
title: Přizpůsobení map kódu úpravou souborů DGML
description: Zjistěte, jak přizpůsobit mapu kódu úpravou souboru .dgml (Directed Graph Markup Language).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5b7c94834aeb6aa82efdb53dead97e26daa667c0
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389485"
---
# <a name="customize-code-maps-by-editing-the-dgml-files"></a>Přizpůsobení map kódu úpravou souborů DGML

Pokud chcete přizpůsobit mapu kódu, můžete upravit jeho soubor .dgml (Directed Graph Markup Language). Můžete například upravit prvky a zadat vlastní styly, přiřadit vlastnosti a kategorie k prvkům kódu a odkazům nebo propojit dokumenty nebo adresy URL s elementy kódu nebo odkazy. Další informace o prvcích DGML najdete v [referenčních informacích k jazyku DGML (Directed Graph Markup Language).](../modeling/directed-graph-markup-language-dgml-reference.md)

Upravte soubor .dgml mapy kódu v textovém editoru nebo editoru XML. Pokud je mapa součástí vašeho Visual Studio, vyberte ji v **Průzkumník řešení**, otevřete místní nabídku a zvolte Otevřít **v** editoru **XML (Text).**

> [!NOTE]
> Pokud chcete vytvořit mapy kódu, musíte mít Visual Studio Enterprise edici. Když upravíte mapu kódu v Visual Studio, vyčistí všechny nepoužívané prvky a atributy DGML jejich odstraněním při ukládání souboru .dgml. Vytváří také prvky kódu automaticky, když ručně přidáte nové odkazy. Při ukládání souboru .dgml mohou být všechny atributy, které byly přidány do prvku, uspořádány podle abecedy.

## <a name="group-code-elements"></a><a name="OrganizeNodes"></a> Seskupení elementů kódu
 Můžete přidat nové skupiny nebo převést existující uzly do skupiny.

1. Otevřete soubor .dgml v textovém editoru nebo editoru XML.

2. Chcete-li převést prvek kódu na skupinu, `<Node/>` najděte element pro tento prvek kódu.

    \- nebo –

    Pokud chcete přidat novou skupinu, najděte `<Nodes>` oddíl . Přidejte nový `<Node/>` prvek.

3. V `<Node/>` elementu přidejte atribut `Group` , který určuje, jestli se skupina zobrazí rozbalená nebo sbalená. Příklad:

   ```xml
   <Nodes>
      <Node Id="MyFirstGroup" Group="Expanded" />
      <Node Id="MySecondGroup" Group="Collapsed" />
   </Nodes>
   ```

4. V části se ujistěte, že element, který má následující atributy, existuje pro každou relaci mezi elementem kódu skupiny a jeho `<Links>` `<Link/>` podřízenými elementy kódu:

   - Atribut, `Source` který určuje prvek kódu skupiny

   - Atribut, `Target` který určuje podřízený element kódu

   - Atribut, který určuje vztah mezi elementem kódu skupiny `Category` a `Contains` jeho podřízeným elementem kódu

     Příklad:

   ```xml
   <Links>
      <Link Category="Contains" Source="MyFirstNewGroup" Target="FirstGroupChildOne" />
      <Link Category ="Contains" Source="MyFirstNewGroup" Target="FirstGroupChildTwo" />
      <Link Category ="Contains" Source="MySecondNewGroup" Target="SecondGroupChildOne" />
      <Link Category="Contains" Source="MySecondNewGroup" Target="SecondGroupChildTwo" />
   </Links>
   ```

    Další informace o atributu najdete v tématu Přiřazení kategorií prvkům kódu a `Category` [odkazům](#AssignCategories).

## <a name="change-the-style-of-the-map"></a><a name="ChangeGraphStyle"></a> Změna stylu mapy
 Barvu pozadí a barvu ohraničení mapy můžete změnit úpravou souboru .dgml mapy. Pokud chcete změnit styl elementů kódu a odkazů, podívejte se na část Změna stylu [elementů kódu a odkazů](#Highlight).

1. Otevřete soubor .dgml v textovém editoru nebo editoru XML.

2. V `<DirectedGraph>` elementu přidejte některý z následujících atributů a změňte jeho styl:

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

## <a name="change-the-style-of-code-elements-and-links"></a><a name="Highlight"></a> Změna stylu elementů kódu a odkazů

### <a name="CreateCustomStyles"></a>
 Vlastní styly můžete použít na následující elementy kódu:

- Jednotlivé elementy kódu a odkazy

- Skupiny elementů kódu a odkazů

- Skupiny elementů kódu a odkazů na základě určitých podmínek

> [!TIP]
> Pokud používáte opakující se styly v mnoha prvcích kódu nebo odkazech, můžete zvážit použití kategorie na tyto elementy nebo odkazy kódu a pak použít styl pro tuto kategorii. Další informace najdete v tématu [Přiřazení kategorií elementům kódu](#AssignCategories) a Odkazy a Přiřazení vlastností k [prvkům kódu](#AssignProperties)a Odkazy .

##### <a name="to-apply-a-custom-style-to-a-single-code-element"></a>Použití vlastního stylu na jeden prvek kódu

1. Otevřete soubor .dgml v textovém editoru nebo editoru XML.

2. Vyhledejte element elementu `<Node/>` kódu. Pokud chcete přizpůsobit svůj styl, přidejte některý z těchto atributů:

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

     Můžete například zadat `Italic` jako styl textu.

     Textura

    ```xml
    Style="Glass"
    ```

     - nebo –

    ```xml
    Style="Plain"
    ```

     Tvar

     Pokud chcete tvar nahradit ikonou, nastavte vlastnost na a nastavte vlastnost na `Shape` `None` cestu se `Icon` souborem ikony.

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

1. Otevřete soubor .dgml v textovém editoru nebo editoru XML.

2. Vyhledejte `<Link/>` element , který obsahuje jak názvy elementu zdrojového kódu, tak cílový element kódu.

3. V `<Link/>` elementu přidejte některý z následujících atributů pro přizpůsobení jeho stylu:

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

##### <a name="to-apply-custom-styles-to-a-group-of-code-elements-or-links"></a>Použití vlastních stylů na skupinu elementů kódu nebo odkazů

1. Otevřete soubor .dgml v textovém editoru nebo editoru XML.

2. Pokud `<Styles></Styles>` prvek neexistuje, přidejte ho pod `<DirectedGraph></DirectedGraph>` element za element `<Links></Links>` .

3. V `<Styles></Styles>` elementu pod `<Style/>` elementem zadejte následující atributy:

   - `TargetType="Node` &#124; `Link | Graph"`

   - `GroupLabel="`*NameInLegendBox*`"`

   - `ValueLabel="`*NameInStylePickerBox*`"`

     Pro použití vlastního stylu na všechny cílové typy nepoužívejte podmínku.

##### <a name="to-apply-a-conditional-style-to-groups-of-code-elements-or-links"></a>Použití podmíněného stylu na skupiny elementů kódu nebo odkazů

1. Otevřete soubor .dgml v textovém editoru nebo editoru XML.

2. V `<Style/>` elementu přidejte element, který obsahuje atribut pro určení `<Condition/>` `Expression` výrazu, který vrací logickou hodnotu.

    Příklad:

   ```xml
   <Condition Expression="MyCategory"/>
   ```

    - nebo –

   ```xml
   <Condition Expression="MyCategory > 100"/>
   ```

    - nebo –

   ```xml
   <Condition Expression="HasCategory('MyCategory')"/>
   ```

    Tento výraz používá následující syntaxi BNF (Backus-Naur Form):

    \<Expression> ::= \<BinaryExpression> &#124; \<UnaryExpression> &#124; "(" \<Expression> ")" &#124; &#124; \<MemberBindings> \<Literal> &#124; \<Number>

    \<BinaryExpression>::= \<Expression> \<Operator>\<Expression>

    \<UnaryExpression> ::= "!" \<Expression> &#124; "+" \<Expression> &#124; "-" \<Expression>

    \<Operator> ::= "<" &#124; " \<=" &#124; "=" &#124; "> =" &#124; ">" &#124; "!=" &#124; "or" &#124; "and" &#124; "+" &#124; "*" &#124; "/" &#124; "-"

    \<MemberBindings> ::= \<MemberBindings> &#124; \<MemberBinding> "." \<MemberBinding>

    \<MemberBinding> ::= \<MethodCall> &#124; \<PropertyGet>

    \<MethodCall> ::= \<Identifier> "(" \<MethodArgs> ")"

    \<PropertyGet> ::= Identifikátor

    \<MethodArgs> ::= \<Expression> &#124; \<Expression> "," \<MethodArgs> &#124; \<empty>

    \<Identifier> ::= [^. ]*

    \<Literal> ::= textový literál s jednoduchým nebo dvojitým uvozovek

    \<Number> ::= řetězec číslic s volitelnou desetinnou čárkou

    Můžete zadat více `<Condition/>` elementů, které musí být pravdivé, aby se styl upřesní.

3. Na další řádek za element přidejte jeden nebo více elementů pro určení atributu a pevného atributu nebo počítaného atributu, který se použije na mapu, elementy kódu nebo odkazy, které splňují `<Condition/>` `<Setter/>` `Property` `Value` `Expression` podmínku.

    Příklad:

   ```xml
   <Setter Property="BackGround" Value="Green"/>
   ```

   Jako jednoduchý kompletní příklad následující podmínka určuje, že element kódu se zobrazí zeleně nebo červeně podle toho, jestli je jeho kategorie `Passed` nastavená na `True` nebo `False` :

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

 Nastavte velikost písma jako funkci počtu řádků kódu, což také změní velikost elementu kódu. Tento příklad používá jeden podmíněný výraz k nastavení více vlastností a `FontSize` `FontFamily` .

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

 Nastavte barvu pozadí elementu kódu na základě `Coverage` vlastnosti . Styly se vyhodnocují v pořadí, v pořadí, ve které se zobrazují, podobně jako `if-else` příkazy .

 V tomto příkladu:

1. Pokud `Coverage` je > 80, nastavte `Background` vlastnost na zelenou.

2. Pokud je hodnota > 50, nastavte vlastnost na odstín oranžové na základě `Coverage` `Background` hodnoty `Coverage` vlastnosti.

3. Jinak `Background` nastavte vlastnost na odstín červené na základě hodnoty `Coverage` vlastnosti .

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

 Nastavte `Shape` vlastnost na , aby ikona `None` nahradila obrazec. K `Icon` určení umístění ikony použijte vlastnost .

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

## <a name="assign-properties-to-code-elements-and-links"></a><a name="AssignProperties"></a> Přiřazení vlastností elementům kódu a odkazům
 Prvky kódu a odkazy můžete uspořádat přiřazením vlastností. Můžete například vybrat elementy kódu, které mají konkrétní vlastnosti, abyste je mohli seskupit, změnit jejich styl nebo je skrýt.

#### <a name="to-assign-a-property-to-a-code-element"></a>Přiřazení vlastnosti k elementu kódu

1. Otevřete soubor .dgml v textovém editoru nebo editoru XML.

2. Vyhledejte `<Node/>` element pro tento prvek kódu. Zadejte název vlastnosti a její hodnotu. Příklad:

    ```xml
    <Nodes>
       <Node Id="MyNode" MyPropertyName="PropertyValue" />
    </Nodes>
    ```

3. Přidáním `<Property/>` elementu do `<Properties>` oddílu určíte atributy, jako je jeho viditelný název a datový typ:

    ```xml
    <Properties>
       <Property Id="MyPropertyName" Label="My Property" DataType="System.DataType"/>
    </Properties>
    ```

#### <a name="to-assign-a-property-to-a-link"></a>Přiřazení vlastnosti propojení

1. Otevřete soubor .dgml v textovém editoru nebo editoru XML.

2. Vyhledejte `<Link/>` element , který obsahuje jak názvy elementu zdrojového kódu, tak cílový element kódu.

3. V `<Node/>` elementu zadejte název vlastnosti a její hodnotu. Příklad:

    ```xml
    <Links>
       <Link Source="MyFirstNode" Target="MySecondNode" MyPropertyName="PropertyValue" />
    </Links>
    ```

4. Přidáním `<Property/>` elementu do `<Properties>` oddílu určíte atributy, jako je jeho viditelný název a datový typ:

    ```xml
    <Properties>
       <Property Id="MyPropertyName" Label="My Property Name" DataType="System.DataType"/>
    </Properties>
    ```

## <a name="assign-categories-to-code-elements-and-links"></a><a name="AssignCategories"></a> Přiřazení kategorií k prvkům kódu a odkazům
 Následující části ukazují, jak můžete uspořádat elementy kódu přiřazením kategorií k nim a jak můžete vytvořit hierarchické kategorie, které vám pomohou uspořádat prvky kódu a přidat atributy do podřízených kategorií pomocí dědičnosti.

#### <a name="to-assign-a-category-to-a-code-element"></a>Přiřazení kategorie k elementu kódu

- Otevřete soubor .dgml v textovém editoru nebo editoru XML.

- Najděte `<Node/>` element pro element kódu, který chcete.

- V `<Node/>` elementu přidejte `Category` atribut , který určuje název kategorie. Příklad:

    ```xml
    <Nodes>
       <Node Id="MyNode" Category="MyCategory" />
    </Nodes>
    ```

     Přidejte do oddílu element , abyste mohli pomocí atributu určit `<Category/>` zobrazovaný text pro tuto `<Categories>` `Label` kategorii:

    ```xml
    <Categories>
       <Category Id="MyCategory" Label="My Category" />
    </Categories>
    ```

#### <a name="to-assign-a-category-to-a-link"></a>Přiřazení kategorie propojení

1. Otevřete soubor .dgml v textovém editoru nebo editoru XML.

2. Vyhledejte `<Link/>` element , který obsahuje jak názvy elementu zdrojového kódu, tak cílový element kódu.

3. V `<Link/>` elementu přidejte `Category` atribut , který určuje název kategorie. Příklad:

    ```xml
    <Links>
       <Link Source="MyFirstNode" Target="MySecondNode" Category="MyCategory"
    </Links>
    ```

4. Přidejte do oddílu element , abyste mohli pomocí atributu určit `<Category/>` zobrazovaný text pro tuto `<Categories>` `Label` kategorii:

    ```xml
    <Categories>
       <Category Id="MyCategory" Label="My Category" />
    </Categories>
    ```

#### <a name="to-create-hierarchical-categories"></a>Vytvoření hierarchických kategorií

1. Otevřete soubor .dgml v textovém editoru nebo editoru XML.

2. Přidejte `<Category/>` element pro nadřazenou kategorii a pak přidejte `BasedOn` atribut do elementu podřízené `<Category/>` kategorie.

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

     V tomto příkladu je pozadí `MyFirstNode` zelené, protože jeho `Category` atribut dědí `Background` atribut `MyParentCategory` .

## <a name="link-documents-or-urls-to-code-elements-and-links"></a><a name="AddReferences"></a> Propojení dokumentů nebo adres URL s elementy kódu a odkazy
 Dokumenty nebo adresy URL můžete propojit s elementy kódu nebo odkazy úpravou souboru .dgml mapy a přidáním atributu do elementu elementu kódu nebo elementu pro `Reference` `<Node/>` `<Link/>` odkaz. Pak můžete otevřít a zobrazit tento obsah z elementu kódu nebo odkazu. Atribut `Reference` určuje cestu k obsahu. To může být cesta relativní k umístění souboru .dgml nebo absolutní cesta.

> [!CAUTION]
> Pokud použijete relativní cestu a soubor .dgml bude přesunut do jiného umístění, pak tuto cestu nebude možné interpretovat. Při pokusu o otevření a zobrazení propojeného obsahu, dojde k chybě oznamující, že obsah nelze zobrazit.

 Můžete například chtít propojit následující elementy kódu:

- Chcete-li popsat změny třídy, můžete propojit adresu URL elementu pracovního kódu, dokumentu nebo jiného souboru .dgml s elementem kódu pro třídu.

- Diagram závislostí můžete propojit s prvkem kódu skupiny, který představuje vrstvu v logické architektuře softwaru.

- Pokud chcete zobrazit další informace o komponentě, která zveřejňuje rozhraní, můžete propojit diagram komponent s elementem kódu pro toto rozhraní.

- Element kódu můžete propojit s Team Foundation Server pracovní položkou nebo chybou, případně s některými dalšími informacemi souvisejícími s elementem kódu.

#### <a name="to-link-a-document-or-url-to-a-code-element"></a>Propojení dokumentu nebo adresy URL s elementem kódu

1. Otevřete soubor .dgml v textovém editoru nebo editoru XML.

2. Najděte `<Node/>` element pro element kódu, který chcete.

3. Proveďte jednu z úloh z následující tabulky:

    Jeden prvek kódu

   - V `<Node/>` `<Link/>` elementu or přidejte `Reference` atribut pro určení umístění elementu kódu.

     > [!NOTE]
     > Pro každý prvek můžete `Reference` mít pouze jeden atribut.

     Příklad:

   ```xml
   <Nodes>
      <Node Id="MyNode" Reference="MyDocument.txt" />
   </Nodes>
   <Properties>
      <Property Id="Reference" Label="My Document" DataType="System.String" IsReference="True" />
   </Properties>
   ```

    Více prvků kódu

   1. V `<Node/>` elementu or `<Link/>` přidejte nový atribut pro určení umístění každého odkazu.

   2. V `<Properties>` části :

      1. Přidejte `<Property/>` element pro každý nový typ odkazu.

      2. Nastavte `Id` atribut na název nového atributu odkazu.

      3. Přidejte atribut a nastavte ho na , aby se odkaz objevil v místní nabídce přejít na odkaz v `IsReference` `True` elementu kódu. 

      4. Pomocí `Label` atributu můžete zadat zobrazovaný text v místní **nabídce** přejít na odkaz v elementu kódu.

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

    Na mapě je název elementu kódu podtržený. Když otevřete místní nabídku pro element kódu nebo odkaz, zobrazí se místní nabídka Přejít na odkaz, která obsahuje prvky propojeného kódu, které si můžete vybrat. 

4. Pomocí atributu můžete zadat společný řetězec, například adresu URL, který se používá více odkazy namísto opakování tohoto řetězce `ReferenceTemplate` v odkazu.

    Atribut `ReferenceTemplate` určuje zástupný symbol pro hodnotu odkazu. V následujícím příkladu bude zástupný symbol v atributu nahrazen hodnotami atributů a v elementu , aby se `{0}` `ReferenceTemplate` vytváře `MyFirstReference` `MySecondReference` `<Node/>` úplná cesta:

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

5. Pokud chcete zobrazit odkazovaný element kódu nebo elementy kódu z mapy, otevřete místní nabídku pro element kódu nebo odkaz. Zvolte **Přejít na odkaz** a pak element kódu.

## <a name="see-also"></a>Viz také

- [Mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md)
- [Použití map kódu k ladění aplikací](../modeling/use-code-maps-to-debug-your-applications.md)
- [Nalezení potenciálních problémů pomocí analyzátorů mapy kódu](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Procházení a změna uspořádání map kódu](../modeling/browse-and-rearrange-code-maps.md)
- [Referenční dokumentace jazyka přímého značení grafů (DGML)](../modeling/directed-graph-markup-language-dgml-reference.md)
