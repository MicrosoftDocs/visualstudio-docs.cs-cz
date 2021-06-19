---
title: 'Návod: Vytvoření kódu pomocí textových šablon'
description: Zjistěte, že generování kódu umožňuje vytvářet programový kód se silnými typy, který lze však snadno změnit při změně zdrojového modelu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- walkthroughs [text templates], generating application code
- walkthroughs [text templates]
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 22940fb86ab0cfd7262a3ca7845521847add2dff
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388123"
---
# <a name="walkthrough-generate-code-by-using-text-templates"></a>Návod: Vytvoření kódu pomocí textových šablon

Generování kódu umožňuje vytvořit programový kód se silnými typy, který lze při změně zdrojového modelu snadno změnit. Porovnejte to s alternativní technikou psaní zcela obecného programu, který přijímá konfigurační soubor, který je flexibilnější, ale výsledkem je kód, který není tak snadný ke čtení a změně, ani nemá tak dobrý výkon. Tento názorný postup tuto výhodu předvede.

## <a name="typed-code-for-reading-xml"></a>Typový kód pro čtení XML

Obor System.Xml poskytuje komplexní nástroje pro načtení dokumentu XML a jeho volné procházení v paměti. Bohužel všechny uzly mají stejný typ, XmlNode. Proto je velmi snadné provádět programovací chyby, například očekávat nesprávný typ podřízeného uzlu nebo nesprávné atributy.

V tomto ukázkovém projektu šablona načte ukázkový soubor XML a vygeneruje třídy, které odpovídají jednotlivým typům uzlů. V ručně napsaném kódu můžete tyto třídy použít k navigaci v souboru XML. Aplikaci můžete také spustit na všech ostatních souborech, které používají stejné typy uzlů. Účelem ukázkového souboru XML je poskytnout příklady všech typů uzlů, které má vaše aplikace řešit.

> [!NOTE]
> Aplikace [xsd.exe](/dotnet/standard/serialization/xml-schema-definition-tool-xsd-exe), která je součástí Visual Studio, může generovat třídy silného typu ze souborů XML. Zde zobrazená šablona je uvedena jako příklad.

Tady je ukázkový soubor:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<catalog>
  <artist id ="Mike%20Nash" name="Mike Nash Quartet">
    <song id ="MikeNashJazzBeforeTeatime">Jazz Before Teatime</song>
    <song id ="MikeNashJazzAfterBreakfast">Jazz After Breakfast</song>
  </artist>
  <artist id ="Euan%20Garden" name="Euan Garden">
    <song id ="GardenScottishCountry">Scottish Country Garden</song>
  </artist>
</catalog>
```

V projektu, který tento názorný průvodce sestaví, můžete napsat kód, jako je následující, a IntelliSense vás při psaní vyzve ke správnému názvu atributu a podřízených názvů:

```csharp
Catalog catalog = new Catalog(xmlDocument);
foreach (Artist artist in catalog.Artist)
{
  Console.WriteLine(artist.name);
  foreach (Song song in artist.Song)
  {
    Console.WriteLine("   " + song.Text);
  }
}
```

Porovnejte tento kód s netypový kód, který můžete napsat bez šablony:

```csharp
XmlNode catalog = xmlDocument.SelectSingleNode("catalog");
foreach (XmlNode artist in catalog.SelectNodes("artist"))
{
    Console.WriteLine(artist.Attributes["name"].Value);
    foreach (XmlNode song in artist.SelectNodes("song"))
    {
         Console.WriteLine("   " + song.InnerText);
     }
}
```

Změna schématu XML ve verzi silného typu vede ke změnám tříd. Kompilátor zvýrazní části kódu aplikace, které je nutné změnit. V netypové verzi, která používá obecný kód XML, není taková podpora k dispozici.

V tomto projektu se jeden soubor šablony používá k vygenerování tříd, které umožní typovou verzi.

## <a name="set-up-the-project"></a>Nastavení projektu

### <a name="create-or-open-a-c-project"></a>Vytvoření nebo otevření projektu v jazyce C#

Tuto techniku můžete použít u libovolného projektu kódu. Tento názorný postup používá projekt jazyka C# a pro účely testování používáme konzolovou aplikaci.

1. V nabídce **File (Soubor)** **klikněte na New (Nový)** a pak na **Project (Projekt).**

2. Klikněte na **uzel Visual C#** a pak v podokně **Šablony** klikněte na **Konzolová aplikace.**

### <a name="add-a-prototype-xml-file-to-the-project"></a>Přidání prototypu souboru XML do projektu

Účelem tohoto souboru je poskytnout ukázky typů uzlů XML, které má aplikace číst. Může to být soubor, který se použije k testování vaší aplikace. Šablona vytvoří třídu jazyka C# pro každý typ uzlu v tomto souboru.

Soubor by měl být součástí projektu, aby ho šablona četla, ale nebude sestavený do zkompilované aplikace.

1. V **Průzkumník řešení** klikněte pravým tlačítkem na projekt, klikněte na **Přidat** a potom klikněte na **Nová položka.**

2. V **dialogovém okně Přidat** novou položku vyberte v podokně **Šablony** možnost Soubor **XML.**

3. Přidejte do souboru ukázkový obsah.

4. Pro tento názorný postup pojmnte soubor `exampleXml.xml` . Nastavte obsah souboru na XML zobrazený v předchozí části.

### <a name="add-a-test-code-file"></a>Přidání souboru testovacího kódu

Přidejte do projektu soubor jazyka C# a napište do něj vzorek kódu, který chcete napsat. Příklad:

```csharp
using System;
namespace MyProject
{
  class CodeGeneratorTest
  {
    public void TestMethod()
    {
      Catalog catalog = new Catalog(@"..\..\exampleXml.xml");
      foreach (Artist artist in catalog.Artist)
      {
        Console.WriteLine(artist.name);
        foreach (Song song in artist.Song)
        {
          Console.WriteLine("   " + song.Text);
} } } } }
```

V této fázi se tento kód nepodaří zkompilovat. Při psaní šablony budete generovat třídy, které umožní, aby byla úspěšná.

Komplexnější test by mohl zkontrolovat výstup této testovací funkce se známým obsahem příkladu souboru XML. V tomto názorném postupu ale budeme spokojeni, až se testovací metoda zkompiluje.

### <a name="add-a-text-template-file"></a>Přidání souboru textové šablony

Přidejte soubor textové šablony a nastavte výstupní příponu na *.cs.*

1. V **Průzkumník řešení** klikněte pravým tlačítkem na projekt, klikněte **na Přidat** a potom klikněte na Nová **položka.**

2. V dialogovém **okně Přidat novou** položku vyberte **Textová šablona** z **podokna** Šablony.

    > [!NOTE]
    > Nezapomeňte přidat textovou šablonu, a ne předzpracovanou textovou šablonu.

3. V souboru v direktivě template změňte `hostspecific` atribut na `true` .

     Tato změna umožní kódu šablony získat přístup k Visual Studio službám.

4. V direktivě output změňte atribut extension na ".cs", aby šablona vygeneruje soubor jazyka C#. V Visual Basic projektu byste ho změnili na ".vb".

5. Soubor uložte. V této fázi by měl soubor textové šablony obsahovat tyto řádky:

    ```
    <#@ template debug="false" hostspecific="true" language="C#" #>
    <#@ output extension=".cs" #>
    ```

Všimněte si, že soubor .cs se Průzkumník řešení jako pobočka souboru šablony. Zobrazí se kliknutím na [+] vedle názvu souboru šablony. Tento soubor se vygeneruje ze souboru šablony pokaždé, když uložíte nebo přesunete fokus mimo soubor šablony. Vygenerovaný soubor se zkompiluje jako součást projektu.

Pro usnadnění vývoje souboru šablony uspořádejte okna souboru šablony a vygenerovaný soubor tak, abyste je viděli vedle sebe. To vám umožní okamžitě zobrazit výstup šablony. Také si všimnete, že když vaše šablona vygeneruje neplatný kód jazyka C#, zobrazí se v okně chybové zprávy chyby.

Veškeré úpravy, které provedete přímo ve vygenerovaném souboru, budou ztraceny při každém uložení souboru šablony. Proto byste se měli buď vyhnout úpravám vygenerované souboru, nebo ho upravit pouze pro krátké experimenty. Někdy je užitečné vyzkoušet ve vygenerovaném souboru krátký fragment kódu, ve kterém je technologie IntelliSense v provozu, a pak ji zkopírovat do souboru šablony.

## <a name="develop-the-text-template"></a>Vývoj textové šablony

Na základě nejlepších rad pro agilní vývoj budeme šablonu vyvíjet v malých krocích a některé chyby v každém přírůstku vymazat, dokud se testovací kód nezkompiluje a neshodí správně.

### <a name="prototype-the-code-to-be-generated"></a>Vytvoření prototypu kódu, který se má vygenerovat

Testovací kód vyžaduje třídu pro každý uzel v souboru . Proto některé chyby kompilace zmizí, pokud tyto řádky připojíte k šabloně a pak je uložíte:

```csharp
class Catalog {}
class Artist {}
class Song {}
```

To vám pomůže zobrazit, co je potřeba, ale deklarace by měly být generovány z typů uzlů v ukázkovém souboru XML. Odstraňte tyto experimentální řádky ze šablony.

### <a name="generate-application-code-from-the-model-xml-file"></a>Generování kódu aplikace ze souboru XML modelu

Chcete-li číst soubor XML a generovat deklarace třídy, nahraďte obsah šablony následujícím kódem šablony:

```
<#@ template debug="false" hostspecific="true" language="C#" #>
<#@ output extension=".cs" #>
<#@ assembly name="System.Xml"#>
<#@ import namespace="System.Xml" #>
<#
 XmlDocument doc = new XmlDocument();
 // Replace this file path with yours:
 doc.Load(@"C:\MySolution\MyProject\exampleXml.xml");
 foreach (XmlNode node in doc.SelectNodes("//*"))
 {
#>
  public partial class <#= node.Name #> {}
<#
 }
#>
```

Nahraďte cestu k souboru správnou cestou pro váš projekt.

Všimněte si oddělovačů bloku kódu `<#...#>` . Tyto oddělovače oddělují fragment kódu programu, který generuje text. Oddělovače bloků výrazů jsou `<#=...#>` v závorkách výrazu, který lze vyhodnotit na řetězec.

Při psaní šablony, která generuje zdrojový kód pro vaši aplikaci, se zabýváte dvěma samostatnými texty programu. Program uvnitř oddělovačů bloku kódu se spustí pokaždé, když šablonu uložíte nebo přesunete fokus do jiného okna. Text, který generuje, který se zobrazí mimo oddělovače, se zkopíruje do vygenerovaného souboru a stane se součástí kódu vaší aplikace.

Direktiva `<#@assembly#>` se chová jako odkaz, takže sestavení je k dispozici pro kód šablony. Seznam sestavení, která šablona používá, je oddělený od seznamu odkazů v projektu aplikace.

Direktiva funguje jako příkaz , který umožňuje používat krátké názvy tříd v `<#@import#>` `using` importovaného oboru názvů.

I když tato šablona generuje kód, vytvoří deklaraci třídy pro každý uzel v příkladu souboru XML, takže pokud existuje několik instancí uzlu, objeví se několik deklarací skladby `<song>` třídy.

### <a name="read-the-model-file-then-generate-the-code"></a>Čtení souboru modelu a vygenerování kódu

Mnoho textových šablon dodržuje vzor, ve kterém první část šablony přečte zdrojový soubor a druhá část vygeneruje šablonu. Potřebujeme přečíst všechny příklady souborů, které shrnují typy uzlů, které obsahuje, a poté vygenerovat deklarace třídy. Další `<#@import#>` je potřeba, abychom mohli použít `Dictionary<>:`

```
<#@ template debug="false" hostspecific="true" language="C#" #>
<#@ output extension=".cs" #>
<#@ assembly name="System.Xml"#>
<#@ import namespace="System.Xml" #>
<#@ import namespace="System.Collections.Generic" #>
<#
 // Read the model file
 XmlDocument doc = new XmlDocument();
 doc.Load(@"C:\MySolution\MyProject\exampleXml.xml");
 Dictionary <string, string> nodeTypes =
        new Dictionary<string, string>();
 foreach (XmlNode node in doc.SelectNodes("//*"))
 {
   nodeTypes[node.Name] = "";
 }
 // Generate the code
 foreach (string nodeName in nodeTypes.Keys)
 {
#>
  public partial class <#= nodeName #> {}
<#
 }
#>
```

### <a name="add-an-auxiliary-method"></a>Přidání pomocné metody

Řídicí blok funkce třídy je blok, ve kterém můžete definovat pomocné metody. Blok je oddělen hodnotou a `<#+...#>` musí se zobrazit jako poslední blok v souboru.

Pokud dáváte přednost názvům tříd, aby začínat velkým písmenem, můžete poslední část šablony nahradit následujícím kódem šablony:

```
// Generate the code
 foreach (string nodeName in nodeTypes.Keys)
 {
#>
  public partial class <#= UpperInitial(nodeName) #> {}
<#
 }
#>
<#+
 private string UpperInitial(string name)
 { return name[0].ToString().ToUpperInvariant() + name.Substring(1); }
#>
```

V této fázi obsahuje vygenerovaný *soubor .cs* následující deklarace:

```csharp
public partial class Catalog {}
public partial class Artist {}
public partial class Song {}
```

Další podrobnosti, jako jsou vlastnosti podřízených uzlů, atributů a vnitřního textu, je možné přidat stejným způsobem.

### <a name="access-the-visual-studio-api"></a>Přístup k rozhraní VISUAL STUDIO API

Nastavení `hostspecific` atributu `<#@template#>` direktivy umožňuje šabloně získat přístup k rozhraní VISUAL STUDIO API. Šablona může použít k získání umístění souborů projektu, aby se zabránilo použití absolutní cesty k souboru v kódu šablony.

```
<#@ template debug="false" hostspecific="true" language="C#" #>
...
<#@ assembly name="EnvDTE" #>
...
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)
                       .GetService(typeof(EnvDTE.DTE));
// Open the prototype document.
XmlDocument doc = new XmlDocument();
doc.Load(System.IO.Path.Combine(dte.ActiveDocument.Path, "exampleXml.xml"));
```

## <a name="complete-the-text-template"></a>Dokončete textovou šablonu.

Následující obsah šablony generuje kód, který umožňuje zkompilovat a spustit testovací kód.

```
<#@ template debug="false" hostspecific="true" language="C#" #>
<#@ output extension=".cs" #>
<#@ assembly name="System.Xml" #>
<#@ assembly name="EnvDTE" #>
<#@ import namespace="System.Xml" #>
<#@ import namespace="System.Collections.Generic" #>
using System;using System.Collections.Generic;using System.Linq;using System.Xml;namespace MyProject{
<#
 // Map node name --> child name --> child node type
 Dictionary<string, Dictionary<string, XmlNodeType>> nodeTypes = new Dictionary<string, Dictionary<string, XmlNodeType>>();

 // The Visual Studio host, to get the local file path.
 EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)
                       .GetService(typeof(EnvDTE.DTE));
 // Open the prototype document.
 XmlDocument doc = new XmlDocument();
 doc.Load(System.IO.Path.Combine(dte.ActiveDocument.Path, "exampleXml.xml"));
 // Inspect all the nodes in the document.
 // The example might contain many nodes of the same type,
 // so make a dictionary of node types and their children.
 foreach (XmlNode node in doc.SelectNodes("//*"))
 {
   Dictionary<string, XmlNodeType> subs = null;
   if (!nodeTypes.TryGetValue(node.Name, out subs))
   {
     subs = new Dictionary<string, XmlNodeType>();
     nodeTypes.Add(node.Name, subs);
   }
   foreach (XmlNode child in node.ChildNodes)
   {
     subs[child.Name] = child.NodeType;
   }
   foreach (XmlNode child in node.Attributes)
   {
     subs[child.Name] = child.NodeType;
   }
 }
 // Generate a class for each node type.
 foreach (string className in nodeTypes.Keys)
 {
    // Capitalize the first character of the name.
#>
    partial class <#= UpperInitial(className) #>
    {      private XmlNode thisNode;      public <#= UpperInitial(className) #>(XmlNode node)       { thisNode = node; }

<#
    // Generate a property for each child.
    foreach (string childName in nodeTypes[className].Keys)
    {
      // Allow for different types of child.
      switch (nodeTypes[className][childName])
      {
         // Child nodes:
         case XmlNodeType.Element:
#>
      public IEnumerable<<#=UpperInitial(childName)#>><#=UpperInitial(childName) #>      {         get         {            foreach (XmlNode node in                thisNode.SelectNodes("<#=childName#>"))              yield return new <#=UpperInitial(childName)#>(node);       } }
<#
         break;
         // Child attributes:
         case XmlNodeType.Attribute:
#>
      public string <#=childName #>      { get { return thisNode.Attributes["<#=childName#>"].Value; } }
<#
         break;
         // Plain text:
         case XmlNodeType.Text:
#>
      public string Text  { get { return thisNode.InnerText; } }
<#
         break;
       } // switch
     } // foreach class child
  // End of the generated class:
#>
   }
<#
 } // foreach class

   // Add a constructor for the root class
   // that accepts an XML filename.
   string rootClassName = doc.SelectSingleNode("*").Name;
#>
   partial class <#= UpperInitial(rootClassName) #>   {      public <#= UpperInitial(rootClassName) #>(string fileName){        XmlDocument doc = new XmlDocument();        doc.Load(fileName);        thisNode = doc.SelectSingleNode("<#=rootClassName#>");}   }}
<#+
   private string UpperInitial(string name)
   {
      return name[0].ToString().ToUpperInvariant() + name.Substring(1);
   }
#>
```

### <a name="run-the-test-program"></a>Spuštění testovacího programu

V hlavní aplikaci konzoly budou na následujících řádcích spouštěny testovací metody. Stisknutím klávesy F5 spusťte program v režimu ladění:

```csharp
using System;
namespace MyProject
{
  class Program
  {
    static void Main(string[] args)
    {
      new CodeGeneratorTest().TestMethod();
      // Allow user to see the output:
      Console.ReadLine();
    }
  }
}
```

### <a name="write-and-update-the-application"></a>Zápis a aktualizace aplikace

Aplikace může být nyní napsána ve stylu silného typu pomocí vygenerovaných tříd namísto použití obecného kódu XML.

Při změně schématu XML lze snadno vygenerovat nové třídy. Kompilátor sdělí vývojářům, kde musí být aktualizován kód aplikace.

Pokud chcete třídy znovu vygenerovat, když se změní ukázkový soubor XML, klikněte na tlačítko **transformovat všechny šablony** na panelu nástrojů **Průzkumník řešení** .

## <a name="conclusion"></a>Závěr

Tento názorný postup ukazuje několik technik a výhod generování kódu:

- *Generování kódu* je vytvoření části zdrojového kódu vaší aplikace z *modelu*. Model obsahuje informace, které jsou vhodné pro doménu aplikace, a může se změnit po dobu života aplikace.

- Silné psaní je jedna z výhod generování kódu. I když model představuje informace ve formuláři lépe vhodné pro uživatele, generovaný kód umožňuje ostatním částem aplikace pracovat s informacemi pomocí sady typů.

- IntelliSense a kompilátor vám pomůžou vytvořit kód, který odpovídá schématu modelu, při psaní nového kódu a při aktualizaci schématu.

- Přidání jednoho nekomplikovaného souboru šablony do projektu může poskytnout tyto výhody.

- Textovou šablonu lze vyvíjet a testovat rychle a postupně.

V tomto návodu je programový kód skutečně vygenerován z instance modelu, což je reprezentativní příklad souborů XML, které aplikace zpracuje. V rámci příznivějšího přístupu bude schéma XML vstupem do šablony, ve formě souboru. XSD nebo definice jazyka specifického pro doménu. Tento přístup by usnadnil, aby šablona určila vlastnosti, jako je násobnost vztahu.

## <a name="troubleshoot-the-text-template"></a>Řešení potíží s textovou šablonou

Pokud jste viděli transformaci šablony nebo chyby kompilace v **Seznam chyb**, nebo pokud výstupní soubor nebyl vygenerován správně, můžete řešit problémy s textovou šablonou pomocí technik popsaných v tématu [generování souborů pomocí nástroje TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).

## <a name="see-also"></a>Viz také

- [Vytvoření kódu v době návrhu pomocí textových šablon T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)
- [Tvorba textové šablony T4](../modeling/writing-a-t4-text-template.md)
