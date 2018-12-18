---
title: Přizpůsobení map kódu úpravou souborů DGML | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: e370e805df8e3a6ee253e3560738e882a247d2de
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817456"
---
# <a name="customize-code-maps-by-editing-the-dgml-files"></a>Přizpůsobení map kódu úpravou souborů DGML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Přizpůsobení map kódu, můžete upravit soubor Directed Graph Markup Language (.dgml) mapě. Můžete třeba upravit prvků, které mají určit vlastní styly, přiřadit vlastnosti a kategorie prvky kódu a odkazy, nebo propojit dokumenty nebo adresy URL pro prvky kódu a odkazy. Další informace o prvcích dgml lze NALÉZT v tématu [orientovaného grafu jazyka přímého značení (DGML) odkaz](../modeling/directed-graph-markup-language-dgml-reference.md).  
  
 Úpravou souboru .dgml mapy kódu v textovém editoru nebo editoru XML. Pokud mapování je součástí řešení sady Visual Studio, vyberte ho v **Průzkumníka řešení**, otevřete místní nabídku a zvolte **otevřít v programu**, **Editor (textový) XML**.  
  
> [!NOTE]
>  K vytvoření kódových map, musíte mít Visual Studio Enterprise. Při úpravě mapy kódu v sadě Visual Studio se vyčistí všechny nepoužívané prvky a atributy DGML odstraněním při uložení souboru .dgml. Vytvoří také prvky kódu automaticky při ručním přidání nových propojení. Při ukládání souboru .dgml mohou být všechny atributy, které byly přidány do prvku, uspořádány podle abecedy.  
  
##  <a name="OrganizeNodes"></a> Seskupit elementy kódu  
 Můžete přidat nové skupiny nebo převést existující uzly do skupiny.  
  
1. V textovém editoru nebo editoru XML otevřete soubor .dgml.  
  
2. Chcete-li převést prvek kódu do skupiny, vyhledejte `<Node/>` – element pro daný element kódu.  
  
    \- nebo –  
  
    Chcete-li přidat novou skupinu, vyhledejte `<Nodes>` oddílu. Přidat nový `<Node/>` elementu.  
  
3. V `<Node/>` elementu, přidejte `Group` atribut k určení, zda daná skupina zobrazovat rozbalená nebo sbalená. Příklad:  
  
   ```xml  
   <Nodes>  
      <Node Id="MyFirstGroup" Group="Expanded" />  
      <Node Id="MySecondGroup" Group="Collapsed" />  
   </Nodes>  
   ```  
  
4. V `<Links>` části, ujistěte se, že `<Link/>` element, který má následující atributy existují pro každý vztah mezi prvek skupiny kódu a jeho podřízené prvky kódu:  
  
   - A `Source` atribut, který určuje prvek skupiny kódu  
  
   - A `Target` atribut, který určuje podřízený element kódu  
  
   - A `Category` atribut, který určuje `Contains` vztah mezi prvek skupiny kódu a jeho podřízený element kódu  
  
     Příklad:  
  
   ```xml  
   <Links>  
      <Link Category="Contains" Source="MyFirstNewGroup" Target="FirstGroupChildOne" />  
      <Link Category ="Contains" Source="MyFirstNewGroup" Target="FirstGroupChildTwo" />  
      <Link Category ="Contains" Source="MySecondNewGroup" Target="SecondGroupChildOne" />  
      <Link Category="Contains" Source="MySecondNewGroup" Target="SecondGroupChildTwo" />  
   </Links>  
   ```  
  
    Další informace o `Category` atributu naleznete v tématu [přiřadit kategorie pro prvky kódu a odkazy](#AssignCategories).  
  
##  <a name="ChangeGraphStyle"></a> Změnit styl mapy  
 Úpravou souboru .dgml na mapě můžete změnit barvu pozadí a barvy ohraničení mapy. Chcete-li změnit styl prvky kódu a odkazy, [změnit styl prvky kódu a odkazy](#Highlight).  
  
1.  V textovém editoru nebo editoru XML otevřete soubor .dgml.  
  
2.  V `<DirectedGraph>` prvku, přidejte některou z následujících atributů pro změnu stylu:  
  
     Barvu pozadí  
  
    ```xml  
    Background="ColorNameOrHexadecimalValue"  
    ```  
  
     Barvu ohraničení  
  
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
  
##  <a name="Highlight"></a> Změna stylu prvků kódu a odkazy  
  
###  <a name="CreateCustomStyles"></a>   
 Použití vlastních stylů na následujících prvků kódu:  
  
-   Prvky jednoho kódu a odkazy  
  
-   Skupiny prvky kódu a odkazy  
  
-   Skupiny prvky kódu a odkazy na základě určitých podmínek  
  
> [!TIP]
>  Pokud máte opakující se styly napříč mnoha prvků kódu nebo odkazy, můžete zvážit tyto prvky kódu nebo propojení použit kategorii a pak na tuto kategorii použít styl. Další informace najdete v tématu [přiřadit kategorie pro prvky kódu a odkazy](#AssignCategories) a [přiřazení vlastností prvky kódu a odkazy](#AssignProperties).  
  
##### <a name="to-apply-a-custom-style-to-a-single-code-element"></a>Použití vlastního stylu na jediného prvku kódu  
  
1.  V textovém editoru nebo editoru XML otevřete soubor .dgml.  
  
2.  Najít element kódu `<Node/>` elementu. Přidejte některou z těchto atributů pro přizpůsobení stylu:  
  
     Barvu pozadí  
  
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
  
     Typ textu  
  
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
  
     - nebo –  
  
    ```xml  
    Style="Plain"  
    ```  
  
     Obrazec  
  
     Pro nahrazení obrazce ikonou, nastavte `Shape` vlastnost `None` a nastavit `Icon` na cestu umístění souboru s ikonou.  
  
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
  
1.  V textovém editoru nebo editoru XML otevřete soubor .dgml.  
  
2.  Najít `<Link/>` element, který obsahuje názvy prvek kódu zdrojový a cílový element kódu.  
  
3.  V `<Link/>` prvku, přidejte některou z následujících atributů pro přizpůsobení stylu:  
  
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
  
##### <a name="to-apply-custom-styles-to-a-group-of-code-elements-or-links"></a>Použití vlastních stylů na skupinu prvky kódu nebo odkazy  
  
1. V textovém editoru nebo editoru XML otevřete soubor .dgml.  
  
2. Pokud `<Styles></Styles>` element neexistuje, přidejte jej pod `<DirectedGraph></DirectedGraph>` elementu po `<Links></Links>` elementu.  
  
3. V `<Styles></Styles>` element v části `<Style/>` elementu a zadat následující atributy:  
  
   - `TargetType="Node` &#124; `Link | Graph"`  
  
   - `GroupLabel="` *NameInLegendBox* `"`  
  
   - `ValueLabel="` *NameInStylePickerBox* `"`  
  
     Pro použití vlastního stylu na všechny cílové typy nepoužívejte podmínku.  
  
##### <a name="to-apply-a-conditional-style-to-groups-of-code-elements-or-links"></a>Pro použití podmíněného stylu na skupiny kódu elementy nebo propojení  
  
1. V textovém editoru nebo editoru XML otevřete soubor .dgml.  
  
2. V `<Style/>` elementu, přidejte `<Condition/>` element, který obsahuje `Expression` atribut zadat výraz, který vrací logickou hodnotu.  
  
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
  
    <Expression> ::= <BinaryExpression> &#124; <UnaryExpression> &#124; "("<Expression>")" &#124; <MemberBindings> &#124; <Literal> &#124; <Number>  
  
    <BinaryExpression> ::= <Expression> <Operator> <Expression>  
  
    <UnaryExpression> ::= "!" <Expression> &#124; "+" <Expression> &#124; "-" <Expression>  
  
    <Operator> :: = "<" &#124; "\<=" &#124; "=" &#124; "> =" &#124; ">" &#124; "! =" &#124; "nebo" &#124; "a" &#124; "+" &#124; "*" &#124; "/" &#124; "-"  
  
    <MemberBindings> ::= <MemberBindings> &#124; <MemberBinding> "." <MemberBinding>  
  
    <MemberBinding> ::= <MethodCall> &#124; <PropertyGet>  
  
    <MethodCall> ::= <Identifier> "(" <MethodArgs> ")"  
  
    <PropertyGet> :: = Identifikátor  
  
    <MethodArgs> ::= <Expression> &#124; <Expression> "," <MethodArgs> &#124; <empty>  
  
    <Identifier> ::= [^. ]*  
  
    <Literal> :: = jedné nebo dvojitými uvozovkami řetězcový literál  
  
    <Number> :: = řetězec číslic s volitelnou desetinnou čárkou  
  
    Lze zadat více `<Condition/>` elementy, které musí být pravda, pokud chcete použít styl.  
  
3. Na dalším řádku za `<Condition/>` element, přidejte jeden nebo více `<Setter/>` prvky k určení `Property` atribut a pevnou `Value` atribut nebo počítaný `Expression` atributu použít pro mapy, prvky kódu nebo odkazy, které splňují Podmínka.  
  
    Příklad:  
  
   ```xml  
   <Setter Property="BackGround" Value="Green"/>  
   ```  
  
   Jako jednoduchý Úplný příklad, následující podmínka určuje to, že prvek kódu zobrazí zeleně nebo červeně podle toho, jestli jeho `Passed` kategorie je nastavena na `True` nebo `False`:  
  
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
  
 Nastavení velikosti písma jako funkce počtu řádků kódu, která rovněž změní velikost prvku kódu. Tento příklad používá jeden podmíněný výraz k nastavení více vlastností, `FontSize` a `FontFamily`.  
  
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
  
 Nastavit barvu pozadí prvku kódu na základě `Coverage` vlastnost. Styly jsou vyhodnocovány v pořadí, ve kterém se zobrazí, podobně jako `if-else` příkazy.  
  
 V tomto příkladu:  
  
1.  Pokud `Coverage` hodnotu > 80, pak nastavte `Background` nastavena na zelenou.  
  
2.  Else if `Coverage` > 50, pak nastavte `Background` na odstín oranžové nastavenou na hodnotu `Coverage` vlastnost.  
  
3.  Jinak nastavte `Background` na odstín červené nastavenou na hodnotu `Coverage` vlastnost.  
  
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
  
 Nastavte `Shape` vlastnost `None` tak, aby ikona nahradila obrazec. Použití `Icon` vlastnosti k určení umístění ikony.  
  
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
  
##  <a name="AssignProperties"></a> Přiřazení vlastností pro prvky kódu a odkazy  
 Prvky kódu a odkazy můžete uspořádat přiřazením vlastností. Například můžete vybrat prvky kódu, které mají specifické vlastnosti, takže můžete seskupit, změnit jejich styl nebo je skrýt.  
  
#### <a name="to-assign-a-property-to-a-code-element"></a>Přiřazení vlastnosti pro prvek kódu  
  
1.  V textovém editoru nebo editoru XML otevřete soubor .dgml.  
  
2.  Najít `<Node/>` – element pro daný element kódu. Zadejte název vlastnosti a její hodnotu. Příklad:  
  
    ```xml  
    <Nodes>  
       <Node Id="MyNode" MyPropertyName="PropertyValue" />  
    </Nodes>  
    ```  
  
3.  Přidat `<Property/>` elementu `<Properties>` pro zadání atributů, jako je například viditelný název a datový typ:  
  
    ```xml  
    <Properties>  
       <Property Id="MyPropertyName" Label="My Property" DataType="System.DataType"/>  
    </Properties>  
    ```  
  
#### <a name="to-assign-a-property-to-a-link"></a>Přiřazení vlastnosti propojení  
  
1.  V textovém editoru nebo editoru XML otevřete soubor .dgml.  
  
2.  Najít `<Link/>` element, který obsahuje názvy prvek kódu zdrojový a cílový element kódu.  
  
3.  V `<Node/>` elementu, zadejte název vlastnosti a její hodnotu. Příklad:  
  
    ```xml  
    <Links>  
       <Link Source="MyFirstNode" Target="MySecondNode" MyPropertyName="PropertyValue" />  
    </Links>  
    ```  
  
4.  Přidat `<Property/>` elementu `<Properties>` pro zadání atributů, jako je například viditelný název a datový typ:  
  
    ```xml  
    <Properties>  
       <Property Id="MyPropertyName" Label="My Property Name" DataType="System.DataType"/>  
    </Properties>  
    ```  
  
##  <a name="AssignCategories"></a> Přiřadit kategorie pro prvky kódu a odkazy  
 Následující části ukazují, jak můžete uspořádat prvky kódu pomocí přiřazení kategorií a jak můžete vytvořit hierarchické kategorie, které vám pomohou organizovat prvky kódu a přidání atributů do podřízených kategorií pomocí dědičnosti.  
  
#### <a name="to-assign-a-category-to-a-code-element"></a>Chcete přiřadit kategorii k prvek kódu  
  
-   V textovém editoru nebo editoru XML otevřete soubor .dgml.  
  
-   Najít `<Node/>` – element pro element kódu, který chcete.  
  
-   V `<Node/>` elementu, přidejte `Category` atribut k určení názvu kategorie. Příklad:  
  
    ```xml  
    <Nodes>  
       <Node Id="MyNode" Category="MyCategory" />  
    </Nodes>  
    ```  
  
     Přidat `<Category/>` elementu `<Categories>` tak, aby vám `Label` atributu pro určení zobrazovaného textu dané kategorie:  
  
    ```xml  
    <Categories>  
       <Category Id="MyCategory" Label="My Category" />  
    </Categories>  
    ```  
  
#### <a name="to-assign-a-category-to-a-link"></a>Přiřazení kategorie propojení  
  
1.  V textovém editoru nebo editoru XML otevřete soubor .dgml.  
  
2.  Najít `<Link/>` element, který obsahuje názvy prvek kódu zdrojový a cílový element kódu.  
  
3.  V `<Link/>` elementu, přidejte `Category` atribut k určení názvu kategorie. Příklad:  
  
    ```xml  
    <Links>  
       <Link Source="MyFirstNode" Target="MySecondNode" Category="MyCategory"  
    </Links>  
    ```  
  
4.  Přidat `<Category/>` elementu `<Categories>` tak, aby vám `Label` atributu pro určení zobrazovaného textu dané kategorie:  
  
    ```xml  
    <Categories>  
       <Category Id="MyCategory" Label="My Category" />  
    </Categories>  
    ```  
  
#### <a name="to-create-hierarchical-categories"></a>Vytvoření hierarchických kategorií  
  
1.  V textovém editoru nebo editoru XML otevřete soubor .dgml.  
  
2.  Přidat `<Category/>` – element pro nadřazenou kategorii a přidejte `BasedOn` atribut podřízené kategorie `<Category/>` elementu.  
  
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
  
     V tomto příkladu pozadí `MyFirstNode` zelený protože jeho `Category` dědí atribut `Background` atribut `MyParentCategory`.  
  
##  <a name="AddReferences"></a> Propojit dokumenty nebo adresy URL pro prvky kódu a odkazy  
 Můžete propojit dokumenty nebo adresy URL pro prvky kódu nebo k propojení úpravou souboru .dgml na mapě a přidání `Reference` atribut `<Node/>` – element pro element kódu nebo `<Link/>` – element pro odkaz. Pak můžete otevřít a zobrazit tento obsah z elementu kódu nebo odkaz. `Reference` Atribut určuje cestu k obsahu. To může být cesta relativní k umístění souboru .dgml nebo absolutní cesta.  
  
> [!CAUTION]
>  Pokud použijete relativní cestu a soubor .dgml bude přesunut do jiného umístění, pak tuto cestu nebude možné interpretovat. Při pokusu o otevření a zobrazení propojeného obsahu, dojde k chybě oznamující, že obsah nelze zobrazit.  
  
 Můžete například chtít propojit následujících prvků kódu:  
  
-   Chcete-li popsat změny třídy, měli byste připojit URL prvek kódu práce, dokumentu nebo jiného souboru .dgml na prvek kódu pro třídu.  
  
-   Měli byste připojit diagram vrstvy do skupinového elementu kódu, který reprezentuje vrstvu v logické architektuře softwaru.  
  
-   Chcete-li zobrazit další informace o komponentě, která zpřístupňuje rozhraní, může připojit diagram součásti na prvek kódu pro rozhraní.  
  
-   Prvek kódu propojte pracovní položky serveru Team Foundation Server nebo chyb nebo jiných informací, které se vztahuje na prvek kódu.  
  
#### <a name="to-link-a-document-or-url-to-a-code-element"></a>Odkaz na prvek kódu dokumentu nebo adresy URL  
  
1. V textovém editoru nebo editoru XML otevřete soubor .dgml.  
  
2. Najít `<Node/>` – element pro element kódu, který chcete.  
  
3. Proveďte jednu z úloh z následující tabulky:  
  
    Jediného prvku kódu  
  
   - V `<Node/>` nebo `<Link/>` elementu, přidejte `Reference` atribut k určení umístění prvku kódu.  
  
     > [!NOTE]
     >  Může mít pouze jeden `Reference` atribut na prvek.  
  
     Příklad:  
  
   ```xml  
   <Nodes>  
      <Node Id="MyNode" Reference="MyDocument.txt" />  
   </Nodes>  
   <Properties>  
      <Property Id="Reference" Label="My Document" DataType="System.String" IsReference="True" />  
   </Properties>  
   ```  
  
    Několik prvků kódu  
  
   1. V `<Node/>` nebo `<Link/>` elementu, přidáte nový atribut k určení umístění každého odkazu.  
  
   2. V `<Properties>` části:  
  
      1.  Přidat `<Property/>` – element pro každý nový typ odkazu.  
  
      2.  Nastavte `Id` atribut pro název nového atributu odkazu.  
  
      3.  Přidat `IsReference` atribut a nastavte ho na `True` odkazovat na prvek kódu zobrazí **přejděte na odkaz** nabídku.  
  
      4.  Použití `Label` atributu pro určení zobrazovaného textu na prvek kódu **přejděte na odkaz** nabídku.  
  
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
  
    Na mapě zobrazí podtržený název prvku kódu. Když otevřete místní nabídku pro prvek kódu nebo odkaz, zobrazí se **přejděte na odkaz** místní nabídka, která obsahuje elementy propojeného kódu můžete zvolit.  
  
4. Použití `ReferenceTemplate` atributu pro zadání běžného řetězce, jako je například adresu URL, která je použita více odkazy místo tohoto řetězce v referenci.  
  
    `ReferenceTemplate` Atribut určuje zástupný symbol pro hodnotu odkazu. V následujícím příkladu `{0}` zástupný symbol v `ReferenceTemplate` atribut se nahradí hodnoty `MyFirstReference` a `MySecondReference` atributy v `<Node/>` element vznikne úplná cesta:  
  
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
  
5. Chcete-li zobrazit prvku odkazovaného kódu nebo prvky kódu z mapy, otevřete místní nabídku pro prvek kódu nebo odkaz. Zvolte **přejděte na odkaz** a pak na prvek kódu.  
  
## <a name="see-also"></a>Viz také  
 [Mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md)   
 [Použití map kódu k ladění aplikací](../modeling/use-code-maps-to-debug-your-applications.md)   
 [Nalezení potenciálních problémů pomocí analyzátorů mapy kódu](../modeling/find-potential-problems-using-code-map-analyzers.md)   
 [Procházení a změna uspořádání map kódu](../modeling/browse-and-rearrange-code-maps.md)   
 [Referenční dokumentace jazyka přímého značení grafů (DGML)](../modeling/directed-graph-markup-language-dgml-reference.md)