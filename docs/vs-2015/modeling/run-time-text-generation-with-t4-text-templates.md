---
title: Generování textu za běhu pomocí textových šablon T4 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Preprocessed Text Template project item
- TextTemplatingFilePreprocessor custom tool
- text templates, TransformText() method
- text templates, generating files at run time
ms.assetid: 79b4b3c6-a9a7-4446-b6fd-e2388fc6b05f
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 75da17b32d3997121777f398a6663932c7d7143d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49920128"
---
# <a name="run-time-text-generation-with-t4-text-templates"></a>Generování textu za běhu pomocí textových šablon T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete generovat textové řetězce ve vaší aplikaci za běhu pomocí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] textové šablony běhu. Není nutné mít v počítači, kde se aplikace spustí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Modul runtime šablony jsou někdy označovány jako "předzpracovaných textových šablon" vzhledem k tomu, že v době kompilace, tato šablona vygeneruje kód, který je proveden za běhu.  
  
 Každá šablona je kombinaci textu, jak se bude zobrazovat v vygenerovaný řetězec a fragmenty kódu programu. Fragmenty programu zadejte hodnoty pro proměnné části řetězce a také řídí podmíněné a opakované části.  
  
 Například následující šablony může v aplikaci, která vytvoří zprávu ve formátu HTML.  
  
```  
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
  
 Všimněte si, že je šablona stránku HTML, ve kterém se nahrazuje proměnné částí kódu programu. Návrh taková ještě stránka může začít napsáním prototyp statické stránky HTML. Můžete pak nahradit tabulku a jiné proměnné části programový kód, který generuje obsah, který se liší od jednou na další.  
  
 Pomocí šablony ve vaší aplikaci využívá je jednodušší než v například dlouhé řadě příkazů zápisu, naleznete v tématu formuláři konečného výstupu. Provádění změn do formuláře výstup je jednodušší a spolehlivější.  
  
## <a name="creating-a-run-time-text-template-in-any-application"></a>Vytvoření šablony textu za běhu v libovolné aplikace  
  
#### <a name="to-create-a-run-time-text-template"></a>Vytvoření šablony textu za běhu  
  
1.  V Průzkumníku řešení v místní nabídce projektu zvolte **přidat**, **nová položka**.  
  
2.  V **přidat novou položku** dialogu **textové šabloně běhu**. (V [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] podívejte se do části **běžné Items\General**.)  
  
3.  Zadejte název souboru šablony.  
  
    > [!NOTE]
    >  Název souboru šablony se použije jako název třídy v generovaném kódu. Proto by neměl mít mezery ani interpunkci.  
  
4.  Zvolte **přidat**.  
  
     Je vytvořen nový soubor, který má příponu **.tt**. Jeho **Custom Tool** je nastavena na **TextTemplatingFilePreprocessor**. Obsahuje následující řádky:  
  
    ```  
    <#@ template language="C#" #>  
    <#@ assembly name="System.Core" #>  
    <#@ import namespace="System.Linq" #>  
    <#@ import namespace="System.Text" #>  
    <#@ import namespace="System.Collections.Generic" #>  
    ```  
  
## <a name="converting-an-existing-file-to-a-run-time-template"></a>Převod existující soubor do šablony za běhu  
 Je dobrým způsobem, jak vytvořit šablonu k převodu existujících příklad výstupu. Například pokud vaše aplikace budou generovat soubory HTML, spustíte tak, že vytvoříte prostý soubor HTML. Ujistěte se, že správně funguje a správnost její vzhled. Pak uvést ji do vašeho [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektu a převést ji do šablony.  
  
#### <a name="to-convert-an-existing-text-file-to-a-run-time-template"></a>Pro převod existujícího textového souboru do šablony za běhu  
  
1.  Zahrnutí souboru do vaší [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektu. V Průzkumníku řešení v místní nabídce projektu zvolte **přidat**, **existující položku**.  
  
2.  Souboru sady **vlastní nástroje** vlastnost **TextTemplatingFilePreprocessor**. V Průzkumníku řešení zvolte v místní nabídce souboru **vlastnosti**.  
  
    > [!NOTE]
    >  Pokud už je vlastnost nastavena, ujistěte se, že je **TextTemplatingFilePreprocessor** a ne **TextTemplatingFileGenerator**. K tomu může dojít, pokud zahrnete soubor, který už má rozšíření **.tt**.  
  
3.  Změnit příponu názvu souboru na **.tt**. I když tento krok je volitelný, pomůže vám vyhnout se v editoru nesprávné otevření souboru.  
  
4.  Odeberte všechny mezery ani interpunkci z hlavní část názvu souboru. Například by nesprávné "Můj Web Page.tt", ale "MyWebPage.tt" je správná. Název souboru se použije jako název třídy v generovaném kódu.  
  
5.  Vložte následující řádek na začátku souboru. Pokud pracujete v projektu jazyka Visual Basic, nahraďte "C#" a "VB".  
  
     `<#@ template language="C#" #>`  
  
## <a name="the-content-of-the-run-time-template"></a>Obsah šablony za běhu  
  
### <a name="template-directive"></a>– Direktiva šablony  
 Nechte první řádek šablony, protože byl při vytvoření souboru:  
  
 `<#@ template language="C#" #>`  
  
 Parametr jazyka závisí na jazyce projektu.  
  
### <a name="plain-content"></a>Prostý obsahu  
 Upravit **.tt** soubor bude obsahovat text, který chcete, aby vaši aplikaci a vygenerujte. Příklad:  
  
```  
<html><body>  
<h1>Sales for January</h2>  
<!-- table to be inserted here -->  
This report is Company Confidential.  
</body></html>  
```  
  
### <a name="embedded-program-code"></a>Vložený programovém kódu  
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
  
 Všimněte si, že se příkazy vložen mezi `<# ... #>` a výrazy jsou vloženy mezi `<#= ... #>`. Další informace najdete v tématu [vytvoření textové šablony T4](../modeling/writing-a-t4-text-template.md).  
  
## <a name="using-the-template"></a>Pomocí šablony  
  
### <a name="the-code-built-from-the-template"></a>Kód vytvořený ze šablony  
 Vždy, když uložíte **.tt** souboru, pobočka **.cs** nebo **.vb** vygeneruje soubor. Pokud chcete zobrazit tento soubor v Průzkumníku řešení rozbalte **.tt** uzel souboru. V projektu jazyka Visual Basic, bude možné rozbalte uzel, po kliknutí na **zobrazit všechny soubory** v panelu nástrojů Průzkumníka řešení.  
  
 Všimněte si, že tento pomocný soubor obsahuje částečné třídy, která obsahuje metodu nazvanou `TransformText()`. Tuto metodu lze volat z vaší aplikace.  
  
### <a name="generating-text-at-run-time"></a>Generování textu za běhu  
 V kódu aplikace můžete vygenerovat obsah šablony pomocí volání takto:  
  
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
  
 Chcete-li umístit na konkrétní obor názvů generované třídy, nastavte **Custom Tool Namespace** vlastnost souboru textové šablony.  
  
### <a name="debugging-runtime-text-templates"></a>Ladění Runtime textových šablon  
 Ladění a testování textové šablony běhu stejným způsobem jako běžné kód.  
  
 Můžete nastavit zarážku v textové šabloně. Pokud spustíte aplikaci v režimu ladění ze sady Visual Studio, můžete krokovat kód a vyhodnocujte výrazy watch obvyklým způsobem.  
  
### <a name="passing-parameters-in-the-constructor"></a>Předávání parametrů v konstruktoru  
 Obvykle šablony musí importovat data z jiných částí aplikace. Usnadnění, je kód vytvořený pomocí šablony částečné třídy. Můžete vytvořit jiné části stejné třídy do jiného souboru ve vašem projektu. Tento soubor může obsahovat konstruktor s parametry, vlastností a funkcí, které lze přistupovat pomocí kódu, který je vložený v šabloně i ve zbývajících částí aplikace.  
  
 Například můžete vytvořit samostatný soubor **MyWebPageCode.cs**:  
  
```csharp  
partial class MyWebPage  
{  
    private MyData m_data;  
    public MyWebPage(MyData data) { this.m_data = data; }}  
```  
  
 V souboru šablony **MyWebPage.tt**, můžete napsat:  
  
```csharp  
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
  
 Tuto šablonu použít v aplikaci:  
  
```csharp  
MyData data = ...;  
MyWebPage page = new MyWebPage(data);  
String pageContent = page.TransformText();  
System.IO.File.WriteAllText("outputPage.html", pageContent);  
```  
  
#### <a name="constructor-parameters-in-visual-basic"></a>Parametry konstruktoru v jazyce Visual Basic  
 V [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], samostatný soubor **MyWebPageCode.vb** obsahuje:  
  
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
  
```vb  
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
  
 A šablony by být vyvolána předáním parametr v konstruktoru:  
  
```vb  
Dim data = New My.Templates.MyData  
    ' Add data values here ....  
Dim page = New My.Templates.MyWebPage(data)  
Dim pageContent = page.TransformText()  
System.IO.File.WriteAllText("outputPage.html", pageContent)  
  
```  
  
#### <a name="passing-data-in-template-properties"></a>Předání dat ve vlastnostech šablony  
 Alternativní metodu pro předávání dat do šablony je přidání veřejné vlastnosti třídy šablony v definici částečné třídy. Aplikace můžete nastavit vlastnosti před vyvoláním `TransformText()`.  
  
 Můžete také přidat pole do vaší třídy šablony v částečné deklaraci. To by povolit předávání dat mezi po sobě jdoucích spuštěních šablony.  
  
### <a name="use-partial-classes-for-code"></a>Používají částečné třídy pro kód  
 Celá řada vývojářů se chcete vyhnout, psaní velké části kódu v šablonách. Místo toho definujte metody v dílčí třídě, která má stejný název jako soubor šablony. Tyto metody volejte z šablony. Tímto způsobem šablony se dozvíte, jasněji jaké cílové výstupní řetězec bude vypadat. Diskuse o vzhled výsledku je možné oddělit od logiky vytváření data, která se zobrazí.  
  
### <a name="assemblies-and-references"></a>Sestavení a odkazy  
 Pokud chcete, aby kód šablony tak, aby odkazovaly .NET nebo jiných sestavení, jako **System.Xml.dll**, měli byste ho přidat do projektu **odkazy** obvyklým způsobem.  
  
 Pokud chcete importovat obor názvů stejným způsobem jako `using` prohlášení, můžou to provedete `import` – direktiva:  
  
```  
<#@ import namespace="System.Xml" #>  
```  
  
 Tyto direktivy musí být umístěny na začátku souboru, ihned po `<#@template` směrnice.  
  
### <a name="shared-content"></a>Sdílený obsah  
 Pokud máte text, který je sdílen mezi několik šablon, můžete umístit do samostatného souboru a zahrnout do každého souboru, ve kterém se má zobrazit:  
  
```  
<#@include file="CommonHeader.txt" #>  
```  
  
 Vložený obsah může obsahovat libovolné směsi programového kódu a ve formátu prostého textu a mohou obsahovat jiné direktivy include nebo jiné direktivy.  
  
 Direktivy include lze použít kdekoli v rámci textu souboru šablony nebo vkládaném souboru.  
  
### <a name="inheritance-between-run-time-text-templates"></a>Dědičnost mezi návrhových textových šablon  
 Můžete sdílet obsah mezi šablonami běhu napsáním základní třídy šablony, která můžou být abstraktní. Použití `inherits` parametr `<@#template#>` směrnice odkazovat na jiné šablony třídy modulu runtime.  
  
#### <a name="inheritance-pattern-fragments-in-base-methods"></a>Model dědičnosti: fragmenty v základní metody  
 Ve vzoru použít v následujícím příkladu Všimněte si, že následující body:  
  
- Základní třída `SharedFragments` metod v rámci bloky s funkcí třídy definuje `<#+ ... #>`.  
  
- Základní třída obsahuje žádné volné. Místo toho všechny textové bloky dojít uvnitř funkce metody třídy.  
  
- Vyvolá metody definované v odvozené třídě `SharedFragments`.  
  
- Volání aplikace `TextTransform()` metoda odvozené třídy, ale neprovádí transformaci základní třídy `SharedFragments`.  
  
- Textové šablony běhu jsou základní a odvozené třídy: to znamená, **Custom Tool** je nastavena na **TextTemplatingFilePreprocessor**.  
  
  **SharedFragments.tt:**  
  
```csharp  
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
  
```csharp  
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
  
#### <a name="inheritance-pattern-text-in-base-body"></a>Model dědičnosti: Základní textu  
 V tomto alternativním přístupem k použití šablony dědičnosti je definován hromadné text do základní šablony. Odvozené šablony poskytují data a fragmenty textu, který se vejde do základního obsahu.  
  
 **AbstractBaseTemplate1.tt:**  
  
```csharp  
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
  
```csharp  
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
 Šablony doby návrhu: Pokud chcete použít šablonu pro generování kódu, který se stane součástí aplikace, najdete v článku [vytvoření kódu v době návrhu pomocí textových šablon T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).  
  
 Modul runtime šablony lze použít v jakékoli aplikaci kde určit tyto šablony a jejich obsah v době kompilace. Ale v případě, že chcete napsat [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozšíření, která generuje text z šablon, které změnit za běhu, naleznete v tématu [volání transformací textu v rozšíření VS](../modeling/invoking-text-transformation-in-a-vs-extension.md).  
  
## <a name="see-also"></a>Viz také  
 [Generování kódu a textové šablony T4](../modeling/code-generation-and-t4-text-templates.md)   
 [Vytvoření textové šablony T4](../modeling/writing-a-t4-text-template.md)   
 [T4 principy: Předzpracované textové šablony podle Oleg Sych](http://www.olegsych.com/2009/09/t4-preprocessed-text-templates/)



