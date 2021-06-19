---
title: Generování textu za běhu pomocí textových šablon T4
description: Zjistěte, jak můžete generovat textové řetězce v aplikaci za běhu pomocí Visual Studio modulu runtime.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- Preprocessed Text Template project item
- TextTemplatingFilePreprocessor custom tool
- text templates, TransformText() method
- text templates, generating files at run time
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 96d37bc586f9e8d6134377244c3181a52ec11a84
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387551"
---
# <a name="run-time-text-generation-with-t4-text-templates"></a>Generování textu za běhu pomocí textových šablon T4

Textové řetězce můžete v aplikaci vygenerovat za běhu pomocí Visual Studio modulu runtime. Počítač, ve kterém se aplikace spouští, nemusí mít Visual Studio. Šablony modulu runtime se někdy nazývají "předzpracované textové šablony", protože v době kompilace generuje šablona kód, který se spustí za běhu.

Každá šablona je kombinace textu, protože se zobrazí ve vygenerovaných řetězcích a fragmentech kódu programu. Fragmenty programu dodávají hodnoty pro proměnné části řetězce a také řídí podmíněné a opakované části.

V aplikaci, která vytváří sestavu HTML, může být například použita následující šablona.

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

Všimněte si, že šablona je stránka HTML, ve které byly části proměnné nahrazeny kódem programu. Návrh takové stránky můžete zahájit napsání statického prototypu stránky HTML. Tabulku a další části proměnné pak můžete nahradit kódem programu, který generuje obsah, který se v jednotlivých případech liší.

Použití šablony v aplikaci usnadňuje zobrazení konečné podoby výstupu, ve které jste například mohli použít dlouhou řadu příkazů pro zápis. Provádění změn ve formě výstupu je jednodušší a spolehlivější.

## <a name="creating-a-run-time-text-template-in-any-application"></a>Vytvoření Run-Time šablony v libovolné aplikaci

### <a name="to-create-a-run-time-text-template"></a>Vytvoření textové šablony za běhu

1. V Průzkumník řešení místní nabídce projektu zvolte **Přidat**  >  **novou položku.**

2. V dialogovém **okně Přidat novou** položku vyberte **Textová šablona modulu runtime.** (V Visual Basic v části **Běžné položky.**  >  **Obecné**.)

3. Zadejte název souboru šablony.

    > [!NOTE]
    > Název souboru šablony se použije jako název třídy ve vygenerovaném kódu. Proto by neměla mít mezery ani interpunkci.

4. Zvolte **Přidat.**

    Vytvoří se nový soubor s **příponou .tt**. Vlastnost **vlastního** nástroje je nastavená na **TextTemplatingFilePreprocessor.** Obsahuje následující řádky:

    ```
    <#@ template language="C#" #>
    <#@ assembly name="System.Core" #>
    <#@ import namespace="System.Linq" #>
    <#@ import namespace="System.Text" #>
    <#@ import namespace="System.Collections.Generic" #>
    ```

## <a name="converting-an-existing-file-to-a-run-time-template"></a>Převod existujícího souboru na Run-Time šablony

Dobrým způsobem, jak vytvořit šablonu, je převést existující příklad výstupu. Pokud například vaše aplikace vygeneruje soubory HTML, můžete začít vytvořením prostého souboru HTML. Ujistěte se, že funguje správně a že jeho vzhled je správný. Potom ho zahrjte do Visual Studio projektu a převeďte ho na šablonu.

### <a name="to-convert-an-existing-text-file-to-a-run-time-template"></a>Převod existujícího textového souboru na šablonu za běhu

1. Zahrnte soubor do Visual Studio projektu. V Průzkumník řešení místní nabídce projektu zvolte **Přidat**  >  **existující položku**.

2. Vlastnost Custom Tools souboru **nastavte** na **TextTemplatingFilePreprocessor.** V Průzkumník řešení místní nabídce souboru zvolte **Vlastnosti**.

    > [!NOTE]
    > Pokud je vlastnost už nastavená, ujistěte se, že se jedná **o TextTemplatingFilePreprocessor,** a ne **TextTemplatingFileGenerator**. K tomu může dojít v případě, že zahrníte soubor, který už má **příponu .tt.**

3. Změňte příponu názvu souboru **na .tt.** I když je tento krok volitelný, pomůže vám vyhnout se otevření souboru v nesprávném editoru.

4. Odeberte všechny mezery nebo interpunkční znaky z hlavní části názvu souboru. Například "Můj webový Page.tt" by byl nesprávný, ale "MyWebPage.tt" je správná. Název souboru se použije jako název třídy ve vygenerovaném kódu.

5. Na začátek souboru vložte následující řádek. Pokud pracujete v projektu Visual Basic, nahraďte "C#" textem "VB".

    `<#@ template language="C#" #>`

## <a name="the-content-of-the-run-time-template"></a>Obsah šablony Run-Time šablony

### <a name="template-directive"></a>Direktiva Template

První řádek šablony nechte tak, jak byl při vytváření souboru:

`<#@ template language="C#" #>`

Parametr jazyka bude záviset na jazyce projektu.

### <a name="plain-content"></a>Prostý obsah

Upravte soubor **.tt** tak, aby obsahoval text, který má vaše aplikace vygenerovat. Příklad:

```html
<html><body>
<h1>Sales for January</h2>
<!-- table to be inserted here -->
This report is Company Confidential.
</body></html>
```

### <a name="embedded-program-code"></a>Vložený kód programu

Kód programu můžete vložit mezi a `<#` `#>` . Příklad:

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

Všimněte si, že mezi příkazy a `<# ... #>` jsou vloženy výrazy mezi `<#= ... #>` . Další informace najdete v tématu [Zápis textové šablony T4.](../modeling/writing-a-t4-text-template.md)

## <a name="using-the-template"></a>Použití šablony

### <a name="the-code-built-from-the-template"></a>Kód sestavený ze šablony

Když soubor **.tt uložíte,** vygeneruje se **soubor .cs** nebo **.vb** pobočky. Pokud chcete tento soubor zobrazit **Průzkumník řešení**, rozbalte **uzel souboru .tt.** V Visual Basic projektu nejprve zvolte **Zobrazit všechny soubory** na panelu **Průzkumník řešení** panelu nástrojů.

Všimněte si, že soubor pobočky obsahuje částečnou třídu, která obsahuje metodu s názvem `TransformText()` . Tuto metodu můžete volat z aplikace.

### <a name="generating-text-at-run-time"></a>Generování textu za běhu

V kódu aplikace můžete obsah šablony vygenerovat pomocí volání, jako je toto:

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

Pokud chcete vygenerované třídy umístit do konkrétního oboru názvů, nastavte vlastnost **Obor** názvů vlastního nástroje textového souboru šablony.

### <a name="debugging-runtime-text-templates"></a>Ladění textových šablon modulu runtime

Ladit a testovat textové šablony modulu runtime stejným způsobem jako běžný kód.

Zarážku můžete nastavit v textové šabloně. Pokud spustíte aplikaci v režimu ladění z Visual Studio, můžete kód krokovat a vyhodnotit výrazy watch obvyklým způsobem.

### <a name="passing-parameters-in-the-constructor"></a>Předávání parametrů v konstruktoru

Šablona obvykle musí importovat nějaká data z jiných částí aplikace. Aby to bylo snadné, je kód sestavený šablonou částečnou třídou. V jiném souboru v projektu můžete vytvořit další část stejné třídy. Tento soubor může obsahovat konstruktor s parametry, vlastnostmi a funkcemi, ke kterým má přístup kód vložený do šablony i zbytek aplikace.

Můžete například vytvořit samostatný soubor **MyWebPageCode.cs**:

```csharp
partial class MyWebPage
{
    private MyData m_data;
    public MyWebPage(MyData data) { this.m_data = data; }}
```

V souboru šablony **MyWebPage.tt**, můžete napsat:

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

Použití této šablony v aplikaci:

```csharp
MyData data = ...;
MyWebPage page = new MyWebPage(data);
String pageContent = page.TransformText();
System.IO.File.WriteAllText("outputPage.html", pageContent);
```

#### <a name="constructor-parameters-in-visual-basic"></a>Parametry konstruktoru v Visual Basic

V Visual Basic samostatný soubor **MyWebPageCode.vb** obsahuje:

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

Šablona může být vyvolána předáním parametru v konstruktoru :

```vb
Dim data = New My.Templates.MyData
    ' Add data values here ....
Dim page = New My.Templates.MyWebPage(data)
Dim pageContent = page.TransformText()
System.IO.File.WriteAllText("outputPage.html", pageContent)
```

#### <a name="passing-data-in-template-properties"></a>Předávání dat ve vlastnostech šablony

Alternativním způsobem předání dat do šablony je přidání veřejných vlastností do třídy šablony v částečné definici třídy. Aplikace může nastavit vlastnosti před vyvoláním `TransformText()` .

Do třídy šablony můžete také přidat pole v částečné definici. To vám umožní předávat data mezi po sobě jdoucími spuštěními šablony.

### <a name="use-partial-classes-for-code"></a>Použití částečných tříd pro kód

Mnoho vývojářů se v šablonách raději vyhnulo psaní velkých textů kódu. Místo toho můžete definovat metody v částečné třídě, která má stejný název jako soubor šablony. Tyto metody volejte ze šablony. Šablona tak jasněji ukazuje, jak bude cílový výstupní řetězec vypadat. Diskuze o vzhledu výsledku lze oddělit od logiky vytváření dat, která zobrazuje.

### <a name="assemblies-and-references"></a>Sestavení a odkazy

Pokud chcete, aby kód šablony odkazovat na .NET nebo jiné sestavení, například  **System.Xml.dll**, přidejte ho obvyklým způsobem do odkazů projektu.

Pokud chcete importovat obor názvů stejným způsobem jako příkaz , můžete `using` to provést pomocí `import` direktivy :

```
<#@ import namespace="System.Xml" #>
```

Tyto direktivy musí být umístěny na začátek souboru ihned za `<#@template` direktivou .

### <a name="shared-content"></a>Sdílený obsah

Pokud máte text, který je sdílen mezi několika šablonami, můžete ho umístit do samostatného souboru a zahrnout ho do každého souboru, ve kterém by se měl zobrazit:

```
<#@include file="CommonHeader.txt" #>
```

Zahrnutý obsah může obsahovat libovolnou kombinaci kódu programu a prostého textu a může obsahovat další direktivy include a další direktivy.

Direktivu include lze použít kdekoli v textu souboru šablony nebo zahrnutých souborů.

### <a name="inheritance-between-run-time-text-templates"></a>Dědičnost mezi Run-Time textových šablon

Obsah mezi šablonami za běhu můžete sdílet tak, že napíšete šablonu základní třídy, která může být abstraktní. Pomocí `inherits` parametru `<@#template#>` direktivy můžete odkazovat na jinou třídu šablony modulu runtime.

#### <a name="inheritance-pattern-fragments-in-base-methods"></a>Vzor dědičnosti: Fragmenty v základních metodách

Ve vzoru použitém v následujícím příkladu si všimněte následujících bodů:

- Základní třída definuje `SharedFragments` metody v rámci bloků vlastností třídy `<#+ ... #>` .

- Základní třída neobsahuje žádný volný text. Místo toho se všechny jeho textové bloky vyskytují uvnitř metod funkce třídy.

- Odvozená třída vyvolá metody definované v `SharedFragments` .

- Aplikace volá `TextTransform()` metodu odvozené třídy, ale ne transformuje základní třídu `SharedFragments` .

- Základní i odvozené třídy jsou textové šablony modulu runtime. To znamená, že **vlastnost Vlastní nástroj** je nastavená na **TextTemplatingFilePreprocessor.**

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

#### <a name="inheritance-pattern-text-in-base-body"></a>Vzor dědičnosti: Text v základním těle

V tomto alternativním přístupu k použití dědičnosti šablon je většina textu definována v základní šabloně. Odvozené šablony poskytují fragmenty dat a textu, které se vejdou do základního obsahu.

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

Šablony v době návrhu: Pokud chcete pomocí šablony vygenerovat kód, který se stane součástí vaší aplikace, podívejte se na část Návrhová generování kódu pomocí textových šablon [T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

Šablony za běhu lze použít v libovolné aplikaci, ve které jsou šablony a jejich obsah určeny v době kompilace. Pokud ale chcete napsat rozšíření Visual Studio, které generuje text ze šablon, které se mění za běhu, podívejte se na volání transformace textu v rozšíření [VS.](../modeling/invoking-text-transformation-in-a-vs-extension.md)

## <a name="see-also"></a>Viz také

- [Vytvoření kódu a textové šablony T4](../modeling/code-generation-and-t4-text-templates.md)
- [Tvorba textové šablony T4](../modeling/writing-a-t4-text-template.md)
- [Panel nástrojů T4](http://olegsych.com/T4Toolbox/)
