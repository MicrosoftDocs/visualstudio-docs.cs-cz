---
title: Generování textu za běhu pomocí textových šablon T4
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- Preprocessed Text Template project item
- TextTemplatingFilePreprocessor custom tool
- text templates, TransformText() method
- text templates, generating files at run time
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e1ee422ec549ced0995db22258edf9ef21540804
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660312"
---
# <a name="run-time-text-generation-with-t4-text-templates"></a>Generování textu za běhu pomocí textových šablon T4

Textové řetězce můžete v aplikaci generovat pomocí textových šablon sady Visual Studio za běhu. Počítač, ve kterém je aplikace spuštěna, nemusí mít aplikaci Visual Studio. Šablony modulu runtime jsou někdy označovány jako "předběžné zpracování textových šablon", protože v době kompilace Šablona generuje kód, který je spuštěn za běhu.

Každá šablona je kombinací textu, který se zobrazí ve vygenerovaném řetězci, a fragmenty kódu programu. Fragmenty programu zadávají hodnoty pro části proměnné řetězce a také řídí podmíněné a opakující se části.

Například následující šablonu lze použít v aplikaci, která vytvoří sestavu jazyka HTML.

```html
<#@ template language="C#" #>
<html><body>
<h1>Sales for Previous Month</h2>
<table>
    <# for (int i = 1; i <= 10; i++)
       { #>
         <tr><td>Test name <#= i #> </td>
             <td>Test value <#= i * i #> </td> </tr>
    <# } #>
 </table>
This report is Company Confidential.
</body></html>
```

Všimněte si, že šablona je stránka HTML, ve které byly proměnné částí nahrazeny kódem programu. Návrh této stránky můžete zahájit psaním statického prototypu stránky HTML. Pak byste mohli nahradit tabulku a další části proměnných kódem programu, který generuje obsah, který se od jedné příležitosti bude lišit.

Použití šablony ve vaší aplikaci usnadňuje zobrazení konečné formy výstupu, než by bylo možné v, například dlouhé řady příkazů zápisu. Provádění změn ve formě výstupu je jednodušší a spolehlivější.

## <a name="creating-a-run-time-text-template-in-any-application"></a>Vytvoření textové šablony Run-time v libovolné aplikaci

### <a name="to-create-a-run-time-text-template"></a>Vytvoření textové šablony Run-Time

1. V Průzkumník řešení v místní nabídce projektu vyberte možnost **přidat**  > **Nová položka**.

2. V dialogovém okně **Přidat novou položku** vyberte možnost **Textová šablona pro modul runtime**. (V Visual Basic najdete v části **běžné položky**  > **Obecné**.)

3. Zadejte název souboru šablony.

    > [!NOTE]
    > Název souboru šablony bude použit jako název třídy ve vygenerovaném kódu. Proto by neměl obsahovat mezery ani interpunkční znaménka.

4. Klikněte na tlačítko **Přidat**.

    Vytvoří se nový soubor s příponou **. TT**. Jeho vlastnost **vlastního nástroje** je nastavená na **TextTemplatingFilePreprocessor**. Obsahuje následující řádky:

    ```
    <#@ template language="C#" #>
    <#@ assembly name="System.Core" #>
    <#@ import namespace="System.Linq" #>
    <#@ import namespace="System.Text" #>
    <#@ import namespace="System.Collections.Generic" #>
    ```

## <a name="converting-an-existing-file-to-a-run-time-template"></a>Převod existujícího souboru na šablonu run-time

Dobrým způsobem, jak vytvořit šablonu, je převést existující příklad výstupu. Například pokud vaše aplikace bude generovat soubory HTML, můžete začít vytvořením prostého souboru HTML. Přesvědčte se, zda správně funguje a zda je jeho vzhled správný. Pak ji zahrňte do projektu sady Visual Studio a převeďte ji na šablonu.

### <a name="to-convert-an-existing-text-file-to-a-run-time-template"></a>Převod existujícího textového souboru na šablonu run-time

1. Zahrňte soubor do projektu sady Visual Studio. V Průzkumník řešení v místní nabídce projektu vyberte možnost **přidat**  > **existující položku**.

2. Nastavte vlastnost **vlastních nástrojů** souboru na **TextTemplatingFilePreprocessor**. V Průzkumník řešení v místní nabídce souboru vyberte možnost **vlastnosti**.

    > [!NOTE]
    > Pokud je vlastnost již nastavena, ujistěte se, že je **TextTemplatingFilePreprocessor** a není **hodnotu TextTemplatingFileGenerator**. K tomu může dojít, pokud zahrnete soubor, který již má příponu **. TT**.

3. Změňte příponu názvu souboru na **. TT**. I když je tento krok nepovinný, pomůže vám se vyhnout otevření souboru v nesprávném editoru.

4. Z hlavní části názvu souboru odeberte všechny mezery nebo interpunkční znaménka. Například "můj Web Page.tt" by byl nesprávný, ale "MyWebPage.tt" je správný. Název souboru bude použit jako název třídy ve vygenerovaném kódu.

5. Vložte následující řádek na začátek souboru. Pokud pracujete v Visual Basic projektu, nahraďte "C#" "pomocí" VB ".

    `<#@ template language="C#" #>`

## <a name="the-content-of-the-run-time-template"></a>Obsah šablony Run-Time

### <a name="template-directive"></a>Template – direktiva

Ponechte první řádek šablony jako při vytvoření souboru:

`<#@ template language="C#" #>`

Parametr Language bude záviset na jazyku vašeho projektu.

### <a name="plain-content"></a>Prostý obsah

Upravte soubor **. TT** tak, aby obsahoval text, který má vaše aplikace vygenerovat. Příklad:

```html
<html><body>
<h1>Sales for January</h2>
<!-- table to be inserted here -->
This report is Company Confidential.
</body></html>
```

### <a name="embedded-program-code"></a>Kód vloženého programu

Můžete vložit kód programu mezi `<#` a `#>`. Příklad:

```csharp
<table>
    <# for (int i = 1; i <= 10; i++)
       { #>
         <tr><td>Test name <#= i #> </td>
             <td>Test value <#= i * i #> </td> </tr>
    <# } #>
 </table>
```

```vb
<table>
<#
    For i As Integer = 1 To 10
#>
    <tr><td>Test name <#= i #> </td>
      <td>Test value <#= i*i #> </td></tr>
<#
    Next
#>
</table>
```

Všimněte si, že mezi `<# ... #>` se vkládají příkazy a mezi `<#= ... #>` se vkládají výrazy. Další informace najdete v tématu [zápis textové šablony T4](../modeling/writing-a-t4-text-template.md).

## <a name="using-the-template"></a>Použití šablony

### <a name="the-code-built-from-the-template"></a>Kód sestavený ze šablony

Při uložení souboru **. TT** se vygeneruje soubor dceřiné společnosti **. cs** nebo **. vb** . Pokud chcete tento soubor zobrazit v **Průzkumník řešení**, rozbalte uzel soubor **. TT** . V projektu Visual Basic nejprve vyberte možnost **Zobrazit všechny soubory** na panelu nástrojů **Průzkumník řešení** .

Všimněte si, že soubor pobočky obsahuje částečnou třídu, která obsahuje metodu s názvem `TransformText()`. Tuto metodu můžete zavolat z vaší aplikace.

### <a name="generating-text-at-run-time"></a>Generování textu v době běhu

V kódu aplikace můžete vygenerovat obsah šablony pomocí volání, jako je toto:

```csharp
MyWebPage page = new MyWebPage();
String pageContent = page.TransformText();
System.IO.File.WriteAllText("outputPage.html", pageContent);
```

```vb
Dim page = New My.Templates.MyWebPage
Dim pageContent = page.TransformText()
System.IO.File.WriteAllText("outputPage.html", pageContent)
```

Chcete-li vygenerované třídy umístit do konkrétního oboru názvů, nastavte vlastnost **Namespace vlastního nástroje** souboru textové šablony.

### <a name="debugging-runtime-text-templates"></a>Ladění šablon textu za běhu

Ladit a testovat šablony textu za běhu stejným způsobem jako běžný kód.

V textové šabloně můžete nastavit zarážku. Pokud aplikaci spustíte v režimu ladění ze sady Visual Studio, můžete krokovat kód a vyhodnotit sledované výrazy obvyklým způsobem.

### <a name="passing-parameters-in-the-constructor"></a>Předávání parametrů v konstruktoru

Šablona obvykle musí importovat některá data z jiných částí aplikace. Pro usnadnění je kód sestavený šablonou částečnou třídou. Můžete vytvořit další část stejné třídy v jiném souboru v projektu. Tento soubor může obsahovat konstruktor s parametry, vlastnostmi a funkcemi, které mohou být k dispozici v rámci kódu, který je vložen do šablony, a zbytkem aplikace.

Můžete například vytvořit samostatný soubor **MyWebPageCode.cs**:

```csharp
partial class MyWebPage
{
    private MyData m_data;
    public MyWebPage(MyData data) { this.m_data = data; }}
```

V souboru šablony **MyWebPage.TT**můžete napsat:

```html
<h2>Sales figures</h2>
<table>
<# foreach (MyDataItem item in m_data.Items)
   // m_data is declared in MyWebPageCode.cs
   { #>
      <tr><td> <#= item.Name #> </td>
          <td> <#= item.Value #> </td></tr>
<# } // end of foreach
#>
</table>
```

Chcete-li použít tuto šablonu v aplikaci:

```csharp
MyData data = ...;
MyWebPage page = new MyWebPage(data);
String pageContent = page.TransformText();
System.IO.File.WriteAllText("outputPage.html", pageContent);
```

#### <a name="constructor-parameters-in-visual-basic"></a>Parametry konstruktoru v Visual Basic

V Visual Basic samostatný soubor **MyWebPageCode. vb** obsahuje:

```vb
Namespace My.Templates
  Partial Public Class MyWebPage
    Private m_data As MyData
    Public Sub New(ByVal data As MyData)
      m_data = data
    End Sub
  End Class
End Namespace
```

Soubor šablony může obsahovat:

```html
<#@ template language="VB" #>
<html><body>
<h1>Sales for January</h2>
<table>
<#
    For Each item In m_data.Items
#>
    <tr><td>Test name <#= item.Name #> </td>
      <td>Test value <#= item.Value #> </td></tr>
<#
    Next
#>
</table>
This report is Company Confidential.
</body></html>
```

Šablonu lze vyvolat předáním parametru v konstruktoru:

```vb
Dim data = New My.Templates.MyData
    ' Add data values here ....
Dim page = New My.Templates.MyWebPage(data)
Dim pageContent = page.TransformText()
System.IO.File.WriteAllText("outputPage.html", pageContent)
```

#### <a name="passing-data-in-template-properties"></a>Předávání dat do vlastností šablony

Alternativním způsobem, jak předat data do šablony, je přidat veřejné vlastnosti do třídy Template v definici částečné třídy. Vaše aplikace může nastavit vlastnosti před vyvoláním `TransformText()`.

Do třídy šablony můžete také přidat pole v částečné definici. To vám umožní předávat data mezi po sobě jdoucí provedení šablony.

### <a name="use-partial-classes-for-code"></a>Použití dílčích tříd pro kód

Mnoho vývojářů upřednostňuje vyhnout se psaní velkých subjektů kódu v šablonách. Místo toho můžete definovat metody v částečné třídě, která má stejný název jako soubor šablony. Zavolejte tyto metody ze šablony. Tímto způsobem šablona zobrazuje zřetelnější informace o tom, jak bude mít cílový výstupní řetězec. Diskuze o vzhledu výsledku je možné oddělit od logiky vytváření zobrazených dat.

### <a name="assemblies-and-references"></a>Sestavení a odkazy

Pokud chcete, aby kód šablony odkazoval na rozhraní .NET nebo jiné sestavení, jako je **System. XML. dll**, přidejte ho obvyklým způsobem do **odkazů** projektu.

Pokud chcete importovat obor názvů stejným způsobem jako příkaz `using`, můžete to provést pomocí direktivy `import`:

```
<#@ import namespace="System.Xml" #>
```

Tyto direktivy musí být umístěny na začátku souboru ihned po `<#@template` direktivě.

### <a name="shared-content"></a>Sdílený obsah

Pokud máte text, který je sdílen mezi několika šablonami, můžete ho umístit do samostatného souboru a zahrnout ho do každého souboru, ve kterém se má zobrazit:

```
<#@include file="CommonHeader.txt" #>
```

Zahrnutý obsah může obsahovat libovolnou kombinaci programového kódu a prostého textu a může obsahovat jiné direktivy include a jiné direktivy.

Direktiva include se dá použít kdekoli v textu souboru šablony nebo zahrnutého souboru.

### <a name="inheritance-between-run-time-text-templates"></a>Dědičnost mezi textovými šablonami run-time

Můžete sdílet obsah mezi šablonami za běhu, a to tak, že zapíšete šablonu základní třídy, která může být abstraktní. Použijte parametr `inherits` direktivy `<@#template#>` pro odkazování na jinou třídu šablony modulu runtime.

#### <a name="inheritance-pattern-fragments-in-base-methods"></a>Vzor dědičnosti: fragmenty v základních metodách

Ve vzoru použitém v následujícím příkladu si všimněte následujících bodů:

- Základní třída `SharedFragments` definuje metody v rámci bloků funkcí třídy `<#+ ... #>`.

- Základní třída neobsahuje žádný bezplatný text. Místo toho se všechny jeho textové bloky vyskytují uvnitř metod funkcí třídy.

- Odvozená třída vyvolá metody definované v `SharedFragments`.

- Aplikace volá metodu `TextTransform()` odvozené třídy, ale netransformuje `SharedFragments` základní třídy.

- Základní i odvozené třídy jsou textové šablony za běhu; To znamená, že vlastnost **Custom Tool** je nastavená na **TextTemplatingFilePreprocessor**.

**SharedFragments.tt:**

```
<#@ template language="C#" #>
<#+
protected void SharedText(int n)
{
#>
   Shared Text <#= n #>
<#+
}
// Insert more methods here if required.
#>
```

**MyTextTemplate1.tt:**

```
<#@ template language="C#" inherits="SharedFragments" #>
begin 1
   <# SharedText(2); #>
end 1
```

**MyProgram.cs:**

```csharp
...
MyTextTemplate1 t1  = new MyTextTemplate1();
string result = t1.TransformText();
Console.WriteLine(result);
```

**Výsledný výstup:**

```
begin 1
    Shared Text 2
end 1
```

#### <a name="inheritance-pattern-text-in-base-body"></a>Vzor dědičnosti: text v základním textu

V tomto alternativním přístupu k použití dědičnosti šablon je hromadný text definován v základní šabloně. Odvozené šablony poskytují fragmenty dat a textu, které se vejdou do základního obsahu.

**AbstractBaseTemplate1.tt:**

```
<#@ template language="C#" #>

Here is the description for this derived template:
  <#= this.Description #>

Here is the fragment specific to this derived template:
<#
  this.PushIndent("  ");
  SpecificFragment(42);
  this.PopIndent();
#>
End of common template.
<#+
  // State set by derived class before calling TextTransform:
  protected string Description = "";
  // 'abstract' method to be defined in derived classes:
  protected virtual void SpecificFragment(int n) { }
#>
```

**DerivedTemplate1.tt:**

```
<#@ template language="C#" inherits="AbstractBaseTemplate1" #>
<#
  // Set the base template properties:
  base.Description = "Description for this derived class";

  // Run the base template:
  base.TransformText();

#>
End material for DerivedTemplate1.

<#+
// Provide a fragment specific to this derived template:

protected override void SpecificFragment(int n)
{
#>
   Specific to DerivedTemplate1 : <#= n #>
<#+
}
#>
```

**Kód aplikace:**

```csharp
...
DerivedTemplate1 t1 = new DerivedTemplate1();
string result = t1.TransformText();
Console.WriteLine(result);
```

**Výsledný výstup:**

```
Here is the description for this derived template:
  Description for this derived class

Here is the fragment specific to this derived template:
     Specific to DerivedTemplate1 : 42
End of common template.
End material for DerivedTemplate1.
```

## <a name="related-topics"></a>Související témata

Šablony návrhu: Pokud chcete použít šablonu k vygenerování kódu, který se stal součástí vaší aplikace, podívejte se na téma [generování kódu v době návrhu pomocí textových šablon T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

Šablony modulu runtime lze použít v libovolné aplikaci, kde jsou šablony a jejich obsah určeny v době kompilace. Pokud ale chcete napsat rozšíření sady Visual Studio, které generuje text ze šablon, které se mění v době běhu, přečtěte si téma [vyvolání transformace textu v rozšíření vs](../modeling/invoking-text-transformation-in-a-vs-extension.md).

## <a name="see-also"></a>Viz také:

- [Vytvoření kódu a textové šablony T4](../modeling/code-generation-and-t4-text-templates.md)
- [Zápis textové šablony T4](../modeling/writing-a-t4-text-template.md)
- [Sada nástrojů T4](http://olegsych.com/T4Toolbox/)
