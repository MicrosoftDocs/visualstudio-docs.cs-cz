---
title: 'Návod: Vytvoření kódu pomocí textových šablon | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- walkthroughs [text templates], generating application code
- walkthroughs [text templates]
ms.assetid: 24602ade-baca-425e-a6ce-be09a2c7f7e1
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: bd360e07ca555bb7cb2c482970ab9a202f7bb630
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49932547"
---
# <a name="walkthrough-generating-code-by-using-text-templates"></a>Návod: Vytvoření kódu pomocí textových šablon
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Generování kódu umožňuje vytvářet programový kód, který je silně typované a ještě můžete snadno změnit při změně modelu zdroje. Tento rozdíl oproti alternativní postup psaní naprosto obecné program, který přijímá konfigurační soubor, který je flexibilnější, ale výsledky v kódu, který není ani tak snadno přečíst a změnit, ani tyto dobrého výkonu. Tento návod ukazuje tuto výhodu.  
  
## <a name="typed-code-for-reading-xml"></a>Zadaný kód XML pro čtení  
 Obor názvů System.Xml poskytuje k dispozici komplexní nástroje pro načítání dokumentu XML a pak ho volně přejdete v paměti. Bohužel na všech uzlech mají stejného typu XmlNode. Proto je velmi snadné vytvořit programovací chyby, jako je nesprávného typu podřízený uzel nebo nesprávné atributů byl očekáván.  
  
 V tomto příkladu projektu šablona načte ukázkový soubor XML a vygeneruje třídy, které odpovídají každého typu uzlu. V kódu ručně psanou můžete použít tyto třídy pro navigaci souboru XML. Aplikace můžete použít také u jiných souborů, které používají stejné typy uzlů. Účelem ukázkový soubor XML je poskytnout příklady, všechny typy uzlů, které chcete, aby se vaše aplikace.  
  
> [!NOTE]
>  Aplikace [xsd.exe](http://go.microsoft.com/fwlink/?LinkId=178765), který je součástí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], můžete ze souborů XML vygenerovat třídy silného typu. Jako příklad je k dispozici šablona je vidět tady.  
  
 Tady je ukázkový soubor:  
  
```  
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
  
 V projektu, že tento návod vytvoří, můžete napsat následující kód a technologie IntelliSense vyzve správné názvy atributů a podřízených při psaní:  
  
```  
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
  
 Oproti to netypového kódu, který můžete například napsat bez šablony:  
  
```  
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
  
 Ve verzi silného typu způsobí změnu schématu XML změny třídám. Kompilátor bude zvýraznění částí kódu aplikace, které se musí změnit. Ve verzi netypový kód, který používá obecný kód XML neexistuje žádná taková podpora.  
  
 V tomto projektu jeden soubor šablony slouží ke generování třídy, které umožní zadané verze.  
  
## <a name="setting-up-the-project"></a>Nastavení projektu  
  
### <a name="create-or-open-a-c-project"></a>Vytvoření nebo otevření projektu v jazyce C#  
 Tento postup můžete použít jakéhokoli kódu projektu. Tento návod používá projektu v jazyce C# a pro účely testování použijeme konzolovou aplikaci.  
  
##### <a name="to-create-the-project"></a>Vytvoření projektu  
  
1.  Na **souboru** klikněte na nabídku **nový** a potom klikněte na tlačítko **projektu**.  
  
2.  Klikněte na tlačítko **Visual C#** uzel a potom v **šablony** podokně klikněte na tlačítko **konzolové aplikace.**  
  
### <a name="add-a-prototype-xml-file-to-the-project"></a>Přidání souboru XML prototyp do projektu  
 Účelem tohoto souboru je poskytnout ukázky typy uzlů XML, které chcete, aby vaše aplikace bude moct číst. To může být soubor, který se použije pro testování vašich aplikací. Šablona vytvoří třída jazyka C# pro každý typ uzlu v tomto souboru.  
  
 Soubor by měl být součástí projektu tak, aby ho mohou číst šablonu, ale nebude součástí kompilované aplikace.  
  
##### <a name="to-add-an-xml-file"></a>Přidání souboru XML  
  
1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt, klikněte na tlačítko **přidat** a potom klikněte na tlačítko **nová položka**.  
  
2. V **přidat novou položku** dialogu **soubor XML** z **šablony** podokně.  
  
3. Přidejte ukázkový obsah do souboru.  
  
4. V tomto návodu, pojmenujte soubor `exampleXml.xml`. Nastavení obsahu souboru má být XML je znázorněno v předchozí části.  
  
   .  
  
### <a name="add-a-test-code-file"></a>Přidat soubor kódu testu  
 Přidejte do projektu soubor jazyka C# a zápis do něj ukázku, kterou chcete být schopni napsat kód. Příklad:  
  
```  
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
  
 V této fázi se nepodaří tento kód zkompilovat. Při psaní šablony, vygeneruje třídy, které umožňují ji proběhla úspěšně.  
  
 Výstup této funkce test známé obsahu ukázkový soubor XML může prohlédnout komplexnější test. Ale v tomto návodu budeme spokojeni při kompilaci testovací metody.  
  
### <a name="add-a-text-template-file"></a>Přidat soubor textové šablony  
 Přidejte soubor textové šablony a nastavte výstup rozšíření "cs".  
  
##### <a name="to-add-a-text-template-file-to-your-project"></a>Chcete-li přidat do projektu soubor textové šablony  
  
1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt, klikněte na tlačítko **přidat**a potom klikněte na tlačítko **nová položka**.  
  
2. V **přidat novou položku** dialogové okno Vyberte **textové šablony** z **šablony** podokně.  
  
   > [!NOTE]
   >  Ujistěte se, že přidáte textové šablony a ne Předzpracované textové šablony.  
  
3. V souboru v direktivě šablony změnit `hostspecific` atribut `true`.  
  
    Tato změna vám umožní kód šablony pro získání přístupu k [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] služby.  
  
4. V direktivě output změňte atribut rozšíření "cs" tak, aby tato šablona vygeneruje soubor jazyka C#. V projektu jazyka Visual Basic by ho změňte na "VB".  
  
5. Uložte soubor. V této fázi soubor textové šablony by měl obsahovat tyto řádky:  
  
   ```  
   <#@ template debug="false" hostspecific="true" language="C#" #>  
   <#@ output extension=".cs" #>  
   ```  
  
   .  
  
   Všimněte si, že soubor cs zobrazí v Průzkumníku řešení jako pobočka souboru šablony. Můžete ho zobrazit kliknutím na [+] vedle názvu souboru šablony. Tento soubor je vygenerován ze souboru šablony při každém uložení nebo přesunutí výběru směrem od souboru šablony. Vygenerovaný soubor se zkompiluje jako součást vašeho projektu.  
  
   Pro usnadnění práce při vývoji soubor šablony, uspořádat okna soubor šablony a vygenerovaný soubor tak, aby si ji můžete zobrazit vedle sebe. Díky tomu můžete zobrazit okamžitě výstup šablony. Můžete si všimnout, že pokud generuje šablona neplatný kód jazyka C#, chyby se zobrazí v okně chybové zprávy.  
  
   Veškeré úpravy, které můžete provést přímo v generovaném souboru budou ztraceny, při každém uložení souboru šablony. Si proto Vyhněte se úpravám vygenerovaný soubor, nebo upravit pouze pro krátké experimentů. Někdy je užitečné si vyzkoušet krátký fragment kódu v generovaném souboru, kde je technologie IntelliSense v operaci, a zkopírujte ho do souboru šablony.  
  
## <a name="developing-the-text-template"></a>Vývoj textové šablony  
 Následující doporučené pokyny agilního vývoje bude vyvíjíme šablony do menších krůčcích vymazání některé chyby na každý přírůstek, dokud testovací kód správně zkompiluje a spustí.  
  
### <a name="prototype-the-code-to-be-generated"></a>Prototyp chcete vygenerovat kód  
 Testovací kód vyžaduje třídu pro každý uzel v souboru. Proto se některé chyby kompilace přestane být zobrazována Pokud připojit tyto řádky do šablony a pak ho uložte:  
  
```  
class Catalog {}   
class Artist {}  
class Song {}  
```  
  
 Díky tomu můžete zjistit, co je potřeba, ale deklarace by měl být vygenerován z typy uzlů v ukázkovém souboru XML. Odstraňte tyto experimentální řádky ze šablony.  
  
### <a name="generate-application-code-from-the-model-xml-file"></a>Generovat kód aplikace ze souboru XML modelu  
 Ke čtení souboru XML a generovat deklarace třídy, nahraďte obsah následujícím kódem šablony šablony:  
  
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
  
 Cesta k souboru nahraďte správnou cestu k projektu.  
  
 Všimněte si, že oddělovače bloku kódu `<#...#>`. Tyto oddělovače párování fragment kódu programu, která generuje text. Oddělovače blok výrazu `<#=...#>` párování výraz, který lze vyhodnotit na řetězec.  
  
 Když vytváříte šablonu, která generuje zdrojový kód pro vaši aplikaci, pracujete se sekvenčním dva texty a samostatné programu. Program uvnitř bloku oddělovače kód se spustí pokaždé, když uložíte šablonu nebo přesunutí výběru na další okno. Text, který generuje, který se zobrazí vně oddělovače, se zkopíruje do generovaného souboru a stane součástí kódu aplikace.  
  
 `<#@assembly#>` – Direktiva se chová jako odkaz, zpřístupnění sestavení kód šablony. Seznam sestavení viděli šablonou je oddělené od seznamu odkazů v projektu aplikace.  
  
 `<#@import#>` – Direktiva funguje stejně jako `using` příkaz, abyste mohli používat krátké názvy tříd v importované oboru názvů.  
  
 Bohužel, i když se tato šablona vygeneruje kód, vytvoří deklaraci třídy pro každý uzel v ukázkový soubor XML, tak, že pokud existuje několik instancí `<song>` uzel, zobrazí se několik deklarací skladby třídy.  
  
### <a name="read-the-model-file-then-generate-the-code"></a>Čtení souboru modelu a generování kódu  
 Mnoho textové šablony se řídí vzorem ve kterém první část šablony, přečte zdrojový soubor a druhá část vygeneruje šablonu. Musíme přečíst všechny ukázkový soubor v slouží ke shrnutí typy uzlů, které obsahuje a potom generovat deklarace tříd. Jiné `<#@import#>` je potřeba, takže můžeme použít `Dictionary<>:`  
  
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
 Řídicí blok funkcí třídy je blok, ve kterém můžete definovat pomocné metody. Blok je ohraničen `<#+...#>` a musí být uvedena jako poslední blok v souboru.  
  
 Pokud dáváte přednost názvy tříd začínat velkým písmenem, můžete nahradit následující kód šablony poslední část šablony:  
  
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
  
 V této fázi .cs vygenerovaný soubor obsahuje následující deklarace:  
  
```  
public partial class Catalog {}  
public partial class Artist {}  
public partial class Song {}  
```  
  
 Další podrobnosti, jako je například vlastnosti podřízené uzly, atributy a vnitřní text můžete přidat pomocí stejným způsobem.  
  
### <a name="accessing-the-visual-studio-api"></a>Přístup k rozhraní API sady Visual Studio  
 Nastavení `hostspecific` atribut `<#@template#>` – direktiva umožňuje získat přístup k šabloně [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozhraní API. Šablona může být využit k získání umístění souborů projektu, abyste se vyhnuli použití absolutní cestu k souboru v kódu šablony.  
  
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
  
## <a name="completing-the-text-template"></a>Dokončení textové šablony  
 Následující obsah šablony generuje kód, který umožňuje testovací kód kompilace a spuštění.  
  
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
  
### <a name="running-the-test-program"></a>Spuštění programu testu  
 Ve funkci main konzolové aplikace bude spuštěno následující řádky testovací metody. Stisknutím klávesy F5 spusťte program v režimu ladění:  
  
```  
using System;  
namespace MyProject  
{ class Program  
  { static void Main(string[] args)  
    { new CodeGeneratorTest().TestMethod();  
      // Allow user to see the output:  
      Console.ReadLine();  
} } }  
```  
  
### <a name="writing-and-updating-the-application"></a>Psaní a aktualizace aplikace  
 Aplikace je teď možné psát v styl silného typu pomocí vygenerovaných tříd, namísto použití obecný kód XML.  
  
 Při změně schématu XML, lze snadno generovat nové třídy. Kompilátor vám sdělí vývojář, ve kterém se musí aktualizovat kód aplikace.  
  
 Pokud chcete znovu vygenerovat třídy při změně ukázkový soubor XML, klikněte na tlačítko **Transformovat všechny šablony** v panelu nástrojů Průzkumníka řešení.  
  
## <a name="conclusion"></a>Závěr  
 Tento názorný postup ukazuje několik technik a výhody generování kódu:  
  
- *Generování kódu* je vytvoření část zdrojového kódu aplikace *modelu*. Model obsahuje informace ve formě vhodné k doméně aplikace a může změnit během životního cyklu aplikace.  
  
- Silné typování je jednou z výhod generování kódu. Zatímco model představuje informace ve formě vhodnější pro uživatele, umožňuje generovaného kódu ostatních částech aplikace se informace o použití sadu typů.  
  
- Technologie IntelliSense a kompilátor vám pomůžou vytvořit kód, který používá schéma modelu, pokud píšete nový kód pro i když dojde k aktualizaci schématu.  
  
- Přidávání souboru jednou šablonou znamená přístupnější aplikaci do projektu může poskytovat i tyto výhody.  
  
- Textové šablony můžete vyvinuli a testovat rychle a postupně.  
  
  V tomto podrobném návodu kód programu skutečně nevygeneruje instance modelu, reprezentativní vzorek souborů XML, které budou zpracovávat aplikace. V rámci formálnější přístupu schématu XML by vstup do šablony ve formě souboru XSD nebo definice jazyka specifického pro doménu. Tento přístup usnadníme pro šablonu, kterou chcete určit vlastnosti například násobnosti relace.  
  
## <a name="troubleshooting-the-text-template"></a>Řešení potíží s textové šablony  
 Pokud jste viděli šablona transformace nebo kompilace chyby **seznam chyb**, nebo pokud nevygeneroval výstupního souboru, je možné řešit textové šablony pomocí technik popsaných v [generování Soubory pomocí nástroje TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření kódu v době návrhu pomocí textových šablon T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)   
 [Zápis textové šablony T4](../modeling/writing-a-t4-text-template.md)



