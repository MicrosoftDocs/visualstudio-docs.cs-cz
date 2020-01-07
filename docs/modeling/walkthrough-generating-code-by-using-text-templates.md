---
title: 'Návod: Vytvoření kódu pomocí textových šablon'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- walkthroughs [text templates], generating application code
- walkthroughs [text templates]
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ff583874778a2f1affd589ef260c6b9eac6b5d06
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593506"
---
# <a name="walkthrough-generate-code-by-using-text-templates"></a>Návod: Vytvoření kódu pomocí textových šablon

Generování kódu umožňuje vytvářet kód programu, který je silného typu a který lze snadno změnit při změně zdrojového modelu. Na rozdíl od tohoto alternativní techniky psaní zcela obecného programu, který přijímá konfigurační soubor, který je flexibilnější, ale má za následek, že není snadné ho číst a měnit, ani takový dobrý výkon. Tento názorný postup ukazuje tuto výhodu.

## <a name="typed-code-for-reading-xml"></a>Typový kód pro čtení XML

Obor názvů System. XML poskytuje komplexní nástroje pro načtení dokumentu XML a jeho navigaci v paměti. Všechny uzly však mají stejný typ, XmlNode. Je proto velmi snadné dělat chyby programování, například očekávat špatný typ podřízeného uzlu nebo nesprávné atributy.

V tomto příkladu projektu šablona čte ukázkový soubor XML a generuje třídy, které odpovídají každému typu uzlu. V kódu psané rukou můžete použít tyto třídy pro navigaci v souboru XML. Můžete také spustit aplikaci na všech ostatních souborech, které používají stejné typy uzlů. Účelem ukázkového souboru XML je poskytnout příklady všech typů uzlů, se kterými se má aplikace zabývat.

> [!NOTE]
> Aplikace [XSD. exe](/dotnet/standard/serialization/xml-schema-definition-tool-xsd-exe), která je součástí sady Visual Studio, může generovat třídy silného typu ze souborů XML. Zde uvedená šablona je uvedena jako příklad.

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

V projektu, který tento návod sestaví, můžete napsat kód jako následující a IntelliSense zobrazí výzvu se správným atributem a podřízenými názvy při psaní:

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

Naproti tomu Netypový kód, který můžete napsat bez šablony:

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

Ve verzi silného typu, Změna schématu XML má za následek změny tříd. Kompilátor zvýrazní části kódu aplikace, které je třeba změnit. V netypové verzi, která používá obecný kód XML, neexistuje žádná taková podpora.

V tomto projektu se k vygenerování tříd, které vytvářejí typovou verzi, používá jeden soubor šablony.

## <a name="set-up-the-project"></a>Nastavení projektu

### <a name="create-or-open-a-c-project"></a>Vytvoření nebo otevření C# projektu

Tuto techniku můžete použít pro libovolný projekt kódu. Tento návod používá C# projekt a pro účely testování používáme konzolovou aplikaci.

1. V nabídce **soubor** klikněte na příkaz **Nový** a potom klikněte na **projekt**.

2. Klikněte na **uzel C# vizuálů** a potom v podokně **šablony** klikněte na **Konzolová aplikace.**

### <a name="add-a-prototype-xml-file-to-the-project"></a>Přidat do projektu prototypový soubor XML

Účelem tohoto souboru je poskytnout vzorky typů uzlů XML, které mají být schopné číst aplikace. Může se jednat o soubor, který se bude používat k testování vaší aplikace. Šablona vytvoří C# třídu pro každý typ uzlu v tomto souboru.

Soubor by měl být součástí projektu, aby jej šablona mohla číst, ale nebude integrován do kompilované aplikace.

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt, klikněte na tlačítko **Přidat** a poté klikněte na položku **Nová položka**.

2. V dialogovém okně **Přidat novou položku** vyberte v podokně **šablony** možnost **soubor XML** .

3. Přidejte do souboru ukázkový obsah.

4. V tomto návodu pojmenujte soubor `exampleXml.xml`. Nastavte obsah souboru tak, aby byl XML zobrazený v předchozí části.

### <a name="add-a-test-code-file"></a>Přidat soubor testovacího kódu

Přidejte do C# projektu soubor a zapište do něj ukázku kódu, který chcete zapisovat. Příklad:

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

V této fázi se tento kód nedaří zkompilovat. Při psaní šablony vygenerujete třídy, které jim umožní úspěch.

Komplexnější test může zkontrolovat výstup této testovací funkce proti známému obsahu ukázkového souboru XML. V tomto návodu ale budeme při kompilaci testovací metody spokojeni.

### <a name="add-a-text-template-file"></a>Přidat textový soubor šablony

Přidejte textový soubor šablony a nastavte rozšíření Output na *. cs*.

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt, klikněte na tlačítko **Přidat**a poté klikněte na položku **Nová položka**.

2. V dialogovém okně **Přidat novou položku** vyberte v podokně **šablony** **text šablona** .

    > [!NOTE]
    > Ujistěte se, že jste přidali textovou šablonu, nikoli předzpracovaná textovou šablonu.

3. V souboru v direktivě šablony změňte atribut `hostspecific` na `true`.

     Tato změna umožní kódu šablony získat přístup ke službám sady Visual Studio.

4. V direktivě Output změňte atribut Extension na ". cs", aby šablona vygenerovala C# soubor. V Visual Basic projektu byste ho změnili na ". vb".

5. Uložte soubor. V této fázi by soubor textové šablony měl obsahovat tyto řádky:

    ```
    <#@ template debug="false" hostspecific="true" language="C#" #>
    <#@ output extension=".cs" #>
    ```

Všimněte si, že soubor. cs se zobrazí v Průzkumník řešení jako dceřiná položka souboru šablony. Můžete ji zobrazit kliknutím na [+] vedle názvu souboru šablony. Tento soubor je vygenerován ze souboru šablony vždy, když uložíte nebo přesunete fokus mimo soubor šablony. Vygenerovaný soubor se zkompiluje jako součást projektu.

Pro usnadnění práce při vývoji souboru šablony uspořádejte okna souboru šablony a vygenerovaný soubor, abyste je viděli vedle sebe. To vám umožní hned zobrazit výstup šablony. Všimněte si také, že pokud Šablona generuje neplatný C# kód, zobrazí se v okně chybová zpráva chyby.

Všechny úpravy, které provedete přímo ve vygenerovaném souboru, budou ztraceny při každém uložení souboru šablony. Proto byste se buď vyhnuli úpravám vygenerovaného souboru, nebo je jenom upravovat jenom pro krátké experimenty. Někdy je vhodné vyzkoušet krátký fragment kódu ve vygenerovaném souboru, kde je technologie IntelliSense v provozu, a pak ji zkopírovat do souboru šablony.

## <a name="develop-the-text-template"></a>Vývoj textové šablony

Po dosažení osvědčených rad pro agilní vývoj budeme vyvíjet šablonu v malých krocích, takže se v každém přírůstku vymaže některé chyby, dokud testovací kód nebude zkompilován a správně spuštěn.

### <a name="prototype-the-code-to-be-generated"></a>Vytvoření prototypu kódu, který se má vygenerovat

Testovací kód vyžaduje třídu pro každý uzel v souboru. Proto některé chyby kompilace zmizí, pokud tyto řádky připojíte k šabloně a uložíte je:

```csharp
class Catalog {}
class Artist {}
class Song {}
```

To vám pomůže zjistit, co je potřeba, ale deklarace by se měly vygenerovat z typů uzlů v ukázkovém souboru XML. Odstraňte tyto experimentální řádky ze šablony.

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

Nahraďte cestu k souboru správnou cestou k vašemu projektu.

Všimněte si oddělovačů bloků kódu `<#...#>`. Tyto oddělovače jsou v závorkách fragment kódu programu, který generuje text. Oddělovače bloku výrazu `<#=...#>` hranaté závorky výraz, který lze vyhodnotit na řetězec.

Když píšete šablonu, která generuje zdrojový kód pro vaši aplikaci, pracujete se dvěma samostatnými texty programu. Program uvnitř oddělovačů bloků kódu se spouští při každém uložení šablony nebo přesunutí fokusu do jiného okna. Text, který generuje, který se zobrazí mimo oddělovače, je zkopírován do generovaného souboru a bude se jednat o část kódu vaší aplikace.

Direktiva `<#@assembly#>` se chová jako odkaz, takže sestavení je k dispozici pro kód šablony. Seznam sestavení, která jsou vidět šablonou, je oddělený od seznamu odkazů v projektu aplikace.

Direktiva `<#@import#>` funguje jako příkaz `using` a umožňuje v importovaném oboru názvů používat krátké názvy tříd.

I když tato šablona generuje kód, vytvoří deklaraci třídy pro každý uzel v ukázkovém souboru XML, aby v případě, že existuje několik instancí `<song>` uzlu, se zobrazí několik deklarací skladby třídy.

### <a name="read-the-model-file-then-generate-the-code"></a>Přečtěte si soubor modelu a potom kód vygenerujte.

Mnoho textových šablon se řídí vzorem, ve kterém první část šablony čte zdrojový soubor a druhá část šablonu vygeneruje. Musíme načíst celý vzorový soubor pro shrnutí typů uzlů, které obsahuje, a pak vygenerovat deklarace třídy. Je potřeba další `<#@import#>`, abyste mohli používat `Dictionary<>:`

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

### <a name="add-an-auxiliary-method"></a>Přidat pomocnou metodu

Řídicí blok funkce třídy je blok, ve kterém můžete definovat pomocné metody. Blok je oddělený `<#+...#>` a musí se nacházet jako poslední blok v souboru.

Pokud upřednostňujete názvy tříd, které začínají velkým písmenem, můžete poslední část šablony nahradit následujícím kódem šablony:

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

V této fázi obsahuje generovaný soubor *. cs* následující deklarace:

```csharp
public partial class Catalog {}
public partial class Artist {}
public partial class Song {}
```

Další podrobnosti, jako jsou vlastnosti podřízených uzlů, atributů a vnitřního textu, lze přidat pomocí stejného přístupu.

### <a name="access-the-visual-studio-api"></a>Přístup k rozhraní API sady Visual Studio

Nastavení atributu `hostspecific` direktivy `<#@template#>` umožňuje šabloně získat přístup k rozhraní API sady Visual Studio. Šablona může použít k získání umístění souborů projektu, aby nedocházelo k použití absolutní cesty k souboru v kódu šablony.

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

## <a name="see-also"></a>Viz také:

- [Vytvoření kódu v době návrhu pomocí textových šablon T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)
- [Zápis textové šablony T4](../modeling/writing-a-t4-text-template.md)
