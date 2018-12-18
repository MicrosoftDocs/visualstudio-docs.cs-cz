---
title: Microsoft Help Viewer SDK | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 620d7dcd-d462-475e-a449-fbfa06ff12c5
caps.latest.revision: 34
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d56d71dd8c8e144c8a2267ed4571b661cca378c2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51794696"
---
# <a name="microsoft-help-viewer-sdk"></a>Microsoft Help Viewer SDK
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Tento článek obsahuje následující úkoly pro Visual Studio Help Viewer integrátorům:

-   Vytváří se téma (podpora F1)

-   Vytvoření balíčku aplikace Help Viewer obsah značky

-   Nasazení sady článků

-   Přidání Nápověda pro Visual Studio shell (integrované nebo izolované)

-   Další prostředky

### <a name="creating-a-topic-f1-support"></a>Vytváří se téma (podpora F1)
 Tato část obsahuje přehled komponent prezentované tématu, požadavky na téma, krátký popis vytvoření tématu (včetně požadavky na podporu F1) a nakonec tématu příklad s jeho vykreslené výsledek.

 **Přehled okna téma nápovědy**

 Pokud téma se volá pro vykreslení, Help Viewer získá značky balíčku prvky, které jsou spojeny s tématem v době instalace nebo poslední aktualizace, spolu s tématu XHTML a kombinuje dvě zobrazené zobrazení obsahu (branding dat + téma data).  Přizpůsobení prostředí značce balíček obsahuje loga, podporu obsahu chování a textu značky (o autorských právech, atd.).  Níže jsou uvedeny "Vytváření Branding balíček" Další informace o přizpůsobení prostředí značce prvky balíčku.  V případě, že neexistuje žádný značky balíček přidružené k tématu, bude aplikace Help Viewer pomocí záložní přizpůsobení prostředí značce balíčku umístěný v kořenovém adresáři aplikace Help Viewer (Branding_en US.mshc).

 **Požadavky na prohlížeč téma nápovědy**

 Vykreslený správně v aplikaci Help Viewer, obsah nezpracované tématu musí být základní XHTML 1.1 W3C.

 Téma obvykle obsahuje dvě části:

- Metadata (viz odkaz na Metadata obsahu): data k tématu, například jedinečné ID tématu, hodnota – klíčové slovo, tématu obsahu ID nadřazené ID uzlu, atd.

- Obsah textu: splňovat základní XHTML 1.1 W3C, která obsahuje podporované obsahu chování (sbalitelné oblasti, fragment kódu, atd. Úplný seznam najdete níž).

  Branding balíček pro Visual Studio nepodporuje ovládací prvky:

- Odkazy

- CodeSnippet

- CollapsibleArea

- Zděděný člen

- LanguageSpecificText

  Podporovaných řetězců jazyka (nerozlišuje velikost písmen):

- JavaScript

- CSharp nebo c#

- cplusplus nebo visualc ++ nebo c ++

- jazyk JScript

- VisualBasic nebo VB.

- f # nebo fsharp nebo služby fs

- jiné – řetězec představující název jazyka

  **Vytváří se téma aplikace Help Viewer**

  Vytvořit nový dokument XHTML s názvem ContosoTopic4.htm a obsahovat název značky (níže).

```html
<html>
<head>
<title>Contoso Topic 4</title>
</head>

<body>

</body>
</html>

```

 V dalším kroku přidejte data k definování, jak v tématu nastat ve třech (vlastní značky, nebo ne), jak odkazovat na toto téma pro F1, kde existuje v tomto tématu v obsahu, jeho ID (pro název odkazu v dalších tématech), atd.  Naleznete v tématu "Metadata obsahu" tabulce pro úplný seznam podporovaných metadat.

- V tomto případě použijeme vlastní značky balíčku hodnotu typu variant značky balíčku Visual Studio Help Viewer.

- Přidat F1 meta název a hodnotu ("Microsoft.Help.F1" content = "ContosoTopic4"), která bude odpovídat hodnotě zadané F1 v kontejneru objektů a integrované vývojové prostředí.  (Viz část podporu F1 pro další informace.)   Jedná se o hodnotu, která je nalezena shoda F1 volání z integrovaného vývojového prostředí pro zobrazení v tomto tématu při výběru klávesy F1 v integrovaném vývojovém prostředí.

- Přidat ID tématu. Jedná se o řetězec, který používá další témata pro propojení k tomuto tématu.  Je Identifikátor Prohlížeč nápovědy pro toto téma.

- Pro obsah přidejte toto téma nadřazený uzel k definování, kde se zobrazí uzel obsahu tohoto tématu.

- Pro obsah přidejte uzel pořadí v tomto tématu. Když nadřazený uzel nemá n počet podřízených uzlů, definujte v pořadí podřízené uzly umístění v tomto tématu. For example, toto téma je 4 témat podřízené číslo 4.)

  Vzorový oddíl metadat:

```html
<html>
<head>
<title>Contoso Topic 4</title>

<meta name="SelfBranded" content="false" />
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
    <meta name="Microsoft.Help.Id" content="ContosoTopic4" />
<meta name="Microsoft.Help.F1" content=" ContosoTopic4" />
    <meta name="Language" content="en-us" />
<meta name="Microsoft.Help.TocParent" content="ContosoTopic0" />
<meta name="Microsoft.Help.TocOrder" content="4" />

</head>

<body>

</body>
</html>

```

 **Text tématu**

 Text tématu (nikoli včetně záhlaví a zápatí) bude obsahovat, odkazů na stránky, Všimněte si části, sbalitelné oblasti, fragment kódu a část textu konkrétní jazyk.  V části Přizpůsobení prostředí značce pro informace o těchto oblastí prezentované tématu.

1.  Přidáte značku název tématu:  `<div class="title">Contoso Topic 4</div>`

2.  Přidáte oddíl Poznámka: `<div class="alert"> add your table tag and text </div>`

3.  Přidání sbalitelné oblasti:  `<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> add text  </CollapsibleArea>`

4.  Přidání fragmentu kódu:  `<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > a block of code </CodeSnippet>`

5.  Přidejte kód jazyka určitý text: `<LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />` Všimněte si, že devLangnu = můžete zadat jiné jazyky. Například devLangnu = "Až po Fortran" se zobrazí až po Fortran při fragment kódu DisplayLanguage = až po Fortran

6.  Přidání odkazů na stránky: `<a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a>`

> [!NOTE]
>  Poznámka: pro nepodporované nové "Jazyk" (například F#, Cobol, až po Fortran) odlišení kódu ve fragmentu kódu bude Monochromatický.

 **Příklad tématu Prohlížeč nápovědy** kód ukazuje, jak definovat metadat, fragment kódu, sbalitelné oblasti a jazyka určitý text.

```
<?xml version="1.0" encoding="utf-8"?>
<html>
<head>
<title>Contoso Topic 4</title>

    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
    <meta name="Microsoft.Help.Id" content="ContosoTopic4" />
<meta name="Microsoft.Help.F1" content=" ContosoTopic4" />
    <meta name="Language" content="en-us" />
<meta name="Microsoft.Help.TocParent" content="ContosoTopic0" />
<meta name="Microsoft.Help.TocOrder" content="4" />
<meta name="SelfBranded" content="false" />
</head>

<body>
<div class="title">Contoso Topic 4</div>

  <div id="header">
<table id="bottomTable" cellpadding="0" cellspacing="0"  width="100%">
        <tr id="headerTableRow2"><td align="left">
            <span id="nsrTitle">Contoso Topic 1</span>
          </td>
<td align="right">
</td></tr>
<tr id="headerTableRow1"><td align="left">
            <span id="runningHeaderText">Contoso Widgets & Sprockets</span>
          </td></tr>
      </table>
</div>

<h2>Table of Contents</h2>

<ul class="toc">
<li class="tocline1"><a href="#introduction" target="_self">1.0 Introduction</a></li>
<li class="tocline1"><a href="#seealso" target="_self">2.1 See Also</a></li>
</ul>

<div class="topic">

<div id="mainSection">
<div id="mainBody">

<a name="introduction"></a>
<h2>1.0 Introduction</h2>
<p>[This documentation is for sample purposes only.]</p>

<p>Contoso Topic 1 contains examples of:
<ul>
<li>Collapsible Area</li>
<li>Bookmark ("See also")</li>
<li>Code Snippets from Branding Package</li>
</ul>
 </p>
<div class="alert"><table><tr><th>
<strong>Note </strong></th></tr>
<tr><td>
<p>This is an example of a <span class="label">Note </span>section.
Call out important items for your reader in this <span class="label">Note </span>box.
</p></td></tr>
</table>
</div>
</div>

<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading">

            <a id="sectionToggle0"><!----></a>

<div>
Example of Collapsible Area
<br/>
Lorem ipsum dolor sit amet...
</div>
</CollapsibleArea>

<div id="snippetGroup" >
<CodeSnippet EnableCopyCode="true" Language="VisualBasic" ContainsMarkup="false" DisplayLanguage="Visual Basic" >
Private Sub ToolStripRenderer1_RenderGrip(sender as Object, e as ToolStripGripRenderEventArgs) _ Handles ToolStripRenderer1.RenderGrip
Dim messageBoxVB as New System.Text.StringBuilder()
    messageBoxVB.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds)
    messageBoxVB.AppendLine()
 ...
    MessageBox.Show(messageBoxVB.ToString(),"RenderGrip Event")
End Sub
</CodeSnippet>

<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" >
private void ToolStripRenderer1_RenderGrip(Object sender, ToolStripGripRenderEventArgs e)
{
System.Text.StringBuilder messageBoxCS = new System.Text.StringBuilder();
messageBoxCS.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds );
messageBoxCS.AppendLine();
...
MessageBox.Show(messageBoxCS.ToString(), "RenderGrip Event" );
}
</CodeSnippet>

<CodeSnippet EnableCopyCode="true" Language="fsharp" ContainsMarkup="false" DisplayLanguage="F#" >
some F# code
</CodeSnippet>
</div>

<h4 class="subHeading">Example of code specific text</h4>Language = <LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />

<a name="seealso"></a>
<h1 class="heading">See Also</h1>

    <div id="seeAlsoSection" class="section">
    <div class="seeAlsoStyle">
        <a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a>
    </div>
 </div>
</div>
</div>
</body>
</html>

```

 **Podpora F1**

 V sadě Visual Studio vyberete F1 generuje hodnoty poskytnuté z umístění kurzoru v rámci rozhraní IDE a naplní "kontejner objektů" se zadanými hodnotami (založená na umístění kurzoru. Když je ukazatel myši nad funkce x, funkce x je aktivní/ve fokusu a naplní kontejner objektů a dat s hodnotami.  Při výběru F1 vyplní kontejner objektů a Visual Studio F1 kód ověří zjistit, zda je výchozí zdroj nápovědy zákazníci místního nebo online (online je výchozí možnost), pak vytvoří odpovídající řetězec založená na uživatelích nastavení (online je výchozí nastavení) – spouštění prostředí (viz Nápověda Příručka pro správce je pro soubor exe spuštění parametry) s parametry pro místní nápovědy a klíčová slova z kontejneru objektů a pokud místní nápovědy je výchozí hodnota nebo adresu URL webu MSDN pomocí klíčového slova v seznamu parametrů.

 Pokud pro F1 jsou vráceny tyto tři řetězce, uvedené jako řetězec s více hodnotami, provést první výraz, hledejte pro klepnutí, a pokud najde, jsme se vším hotovi; Pokud ne, přejít na další řetězec.  Pořadí je důležité. Nejdelší řetězec nejkratší řetězec by měl být prezentace klíčových slov s více hodnotami.  Chcete-li to ověřit v případě klíčových slov s více hodnotami, podívejte se na online řetězce adresy URL F1, která bude obsahovat vybrané – klíčové slovo.

 V sadě Visual Studio 2012 záměrně provedli jsme silnější dělení mezi online a offline, aby pokud byla nastavení uživatele pro Online, potom jsme jednoduše se předávají F1 žádost přímo na naše online dotazovací služby MSDN, místo směrování přes agenta knihovnu nápovědy jestli jsme měli v sadě Visual Studio 2010. Potom spoléháme na stavu "obsah dodavatele nainstalován = true" k určení, jestli se má provést něco jiného, v tomto kontextu. Při hodnotě true se můžeme provést tuto logiku analýzy a směrování v závislosti na tom, co si přejete podporovat pro vaše zákazníky. Pokud má hodnotu false, pak nám stačí, když přejdete na web MSDN. Pokud místní nastavení uživatele, všechna volání přejděte do modulu místní nápovědy.

 F1 vývojový Diagram:

 ![Tok F1](../../extensibility/internals/media/f1flow.png "F1flow")

 Když zdroj obsahu nápovědy výchozí aplikace Help Viewer je nastaven na online (spustit v prohlížeči):

- Funkce sady Visual Studio Partner (VSP) generování hodnoty F1 kontejner objektů a dat (prefix.keyword vlastnosti kontejneru objektů a dat a předpona, která v registru byla nalezena online URL): F1 odešle URL VSP + parametry k prohlížeči.

- Funkce sady Visual Studio (jazyk editor, Visual Studio specifické položky nabídek, atd.): F1 odešle Visual Studio adresu URL do prohlížeče.

  Když zdroj obsahu nápovědy výchozí aplikace Help Viewer je nastaven na místní nápovědy (spuštění v aplikaci Help Viewer):

- VSP funkce, kde – klíčové slovo porovnává F1 kontejner objektů a dat a index místní úložiště (to znamená, že vlastnost prefix.keyword kontejner objektů a dat = hodnotu nalezenou v indexu místní úložiště): F1 vykreslí témat v Help Viewer.

- Funkce sady Visual Studio (žádná možnost pro VSP přepsání kontejner objektů a dat z funkce aplikace Visual Studio, protože ho): F1 vykreslí sady Visual Studio témat v Help Viewer.

  Nastavte následující hodnoty registru pro povolit záložní F1 pro obsah nápovědy dodavatele. Použití náhradní lokality F1 znamená, že aplikace Help Viewer je nastavena na hledání Nápověda F1 obsahu online a dodavatele obsahu je nainstalovaný místně pevném disku. Aplikace Help Viewer by měl vypadat na místní nápovědy pro obsah i v případě, že ve výchozím nastavení je pro online nápovědy.

1. Nastavte **VendorContent** Help 2.1 klíči registru:

   -   Pro 32bitové operační systémy:

        HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.1\Catalogs\VisualStudio12

        "VendorContent" = dword: 00000001

   -   Pro 64bitové operační systémy:

        HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Catalogs\VisualStudio12

        "VendorContent" = dword: 00000001

2. Obor názvů partnera v klíči registru Help 2.1 registrace:

   - Pro 32bitové operační systémy:

      HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.1\Partner<em>\\< obor názvů\></em>

      "umístění"="do režimu offline"

   - Pro 64bitové operační systémy:

      HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Partner<em>\\< obor názvů\></em>

      "umístění"="do režimu offline"

   **Základní analýza nativní Namespace**

   Chcete-li při analýze základního nativní oboru názvů, v registru přidejte novou hodnotu DWORD s názvem: BaseNativeNamespaces a nastavte jej na hodnotu 1 (pod klíčem katalogu, které chtějí podporují).  Pokud chcete použít v katalogu sady Visual Studio, můžete například přidat klíč do cesty:

   HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Catalogs\VisualStudio12

   F1 – klíčové slovo ve formátu, který záhlaví/metodu dochází, když znak '/', bude analyzována, výsledkem je následující konstruktor:

- ZÁHLAVÍ: bude obor názvů, který slouží k registraci v registru

- Metoda: to se stane klíčové slovo, podrobné.

  Mějme například vlastní knihovnu s názvem CustomLibrary a metodu nazvanou MyTestMethod, když F1 žádost pochází v něm naformátovaný jako `CustomLibrary/MyTestMethod`.

  Uživatel pak můžete zaregistrovat CustomLibrary jako obor názvů v části partneři hive a zadat jakékoli umístění klíč přejí a – klíčové slovo předán dotaz bude MyTestMethod.

  **Povolit ladění nástroje v integrovaném vývojovém prostředí nápovědy**

  Přidejte následující klíč registru a hodnoty:

  Klávesa HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\12.0\Dynamic: výstup ladění zobrazovaný v hodnotě maloobchodní: Ano

  V prostředí IDE v položce nabídky Nápověda zvolte "Ladit kontext nápovědy"

  **Metadata obsahu**

  V následující tabulce je jakýkoli řetězec, který se zobrazí mezi hranaté závorky zástupný symbol, který se musí nahradit odpovídajícími rozpoznaná hodnota. Například v \<meta name="Microsoft.Help.Locale" obsah = "[jazyk]" / >, "[jazyk]" se musí nahradit odpovídajícími hodnotu, jako "en-us".

|Vlastnosti (znázornění HTML)|Popis|
|--------------------------------------|-----------------|
|\< Meta name="Microsoft.Help.Locale" content = "[-kód jazyka]" / >|Nastaví národní prostředí pro toto téma. Pokud se tato značka se používá v tématu, musí být použit pouze jednou a musí být vložen nad všechny ostatní značky Microsoft Help. Pokud tato značka se nepoužívá, základní text tématu, které se indexuje zpětně pomocí pro dělení slov, která souvisí s národní prostředí produktu, pokud je zadán; v opačném případě en-us se používá pro dělení slov. Tato značka odpovídá ISOC RFC 4646. Pokud chcete mít jistotu, že Microsoft Help funguje správně, pomocí této vlastnosti namísto obecného atribut Language.|
|\< Meta name="Microsoft.Help.TopicLocale" content = "[-kód jazyka]" / >|Nastaví národní prostředí pro toto téma se také používají jiné národní prostředí. Pokud se tato značka se používá v tématu, musí být použit pouze jednou. Tato značka použijte, pokud katalog s obsahem ve více než jednom jazyku. Více témat v katalogu může mít stejné ID, ale každý musí určovat jedinečný TopicLocale. Téma, které určuje TopicLocale, odpovídajícímu národnímu prostředí katalogu je téma, které se zobrazí v obsahu. Všechny jazykové verze tohoto tématu se však zobrazí ve výsledcích hledání.|
|\< název > [Title] \< /title >|Určuje název tohoto tématu. Tato značka je povinné a musí být použit pouze jednou v tématu. Pokud se text tématu neobsahuje název \<div > části, tento název se zobrazí v tomto tématu a v obsahu.|
|\< Meta name = "Microsoft.Help.Keywords" content = "[aKeywordPhrase]" / >|Určuje text odkazu, který se zobrazí v podokně index aplikace Help Viewer. Po kliknutí na odkaz, zobrazí se tématu. Můžete zadat více klíčových slov index tématu nebo toto klíčové slovo můžete vynechat, pokud nechcete, aby se odkazy na toto téma se zobrazí v indexu. Klíčová slova "K" z předchozích verzí nápovědy lze převést na tuto vlastnost.|
|\< Meta name="Microsoft.Help.Id" content = "[TopicID]" / >|Nastaví identifikátor pro toto téma. Tato značka je povinné a musí být použit pouze jednou v tématu. ID musí být jedinečný mezi témata v katalogu, které mají stejné nastavení národního prostředí. V jiném tématu můžete vytvořit odkaz na toto téma pomocí tohoto ID.|
|\< Meta name="Microsoft.Help.F1" content="[System.Windows.Controls.Primitives.IRecyclingItemContainerGenerator]"/ >|Určuje klíčové slovo F1 pro toto téma. Můžete zadat více klíčových slov F1 pro téma nebo toto klíčové slovo můžete vynechat, pokud nechcete, aby se v tomto tématu a zobrazí, když uživatel aplikace stisknutí klávesy F1. Obvykle je zadán pouze jeden F1 – klíčové slovo tématu. Klíčová slova "F" z předchozích verzí nápovědy lze převést na tuto vlastnost.|
|\< Meta name = "Popis" content = "[tématu description]" / >|Poskytuje krátký popis obsahu v tomto tématu. Pokud se tato značka se používá v tématu, musí být použit pouze jednou. Tato vlastnost je k němu přistupuje přímo dotazu knihovny; není uložený v souboru indexu.|
 Meta name="Microsoft.Help.TocParent" content = "[parent_Id]" / >|Určuje nadřazené téma tohoto tématu v obsahu. Tato značka je povinné a musí být použit pouze jednou v tématu. Hodnota je Microsoft.Help.Id nadřazeného prvku. Téma může mít jen jeden umístění v tabulce obsahu. "-1" se považuje za ID tématu pro kořenový obsah. V [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)], tuto stránku je domovská stránka aplikace Help Viewer. Toto je ze stejného důvodu, že konkrétně jsme některá témata k zajištění, že se zobrazí v horní úrovni přidat TocParent =-1. Domovská stránka aplikace Help Viewer je stránka systému a proto není – nahraditelné. Pokud VSP se pokusí přidat stránku s ID -1, může získat přidali do sady obsahu, ale aplikace Help Viewer bude vždy používat stránku systému – Domovská stránka prohlížeč nápovědy|
|\< Meta name="Microsoft.Help.TocOrder" content = "[kladné celé číslo]" / >|Určuje, kde v obsahu v tomto tématu zobrazí vzhledem k jeho peer témata. Tato značka je povinné a musí být použit pouze jednou v tématu. Hodnota je celé číslo. Téma, které určuje celé číslo nižší hodnota se zobrazí nad téma, které určuje celé číslo vyšší hodnotu.|
|\< Meta name="Microsoft.Help.Product" content = "[kód produktu]" / >|Určuje produkt, který popisuje Toto téma. Pokud se tato značka se používá v tématu, musí být použit pouze jednou. Tyto informace mohou být rovněž dodán jako parametr, který je předán do indexovacího členu nápovědy.|
|\< Meta name="Microsoft.Help.ProductVersion" content = "[číslo verze]" / >|Určuje verzi produktu, který popisuje Toto téma. Pokud se tato značka se používá v tématu, musí být použit pouze jednou. Tyto informace mohou být rovněž dodán jako parametr, který je předán do indexovacího členu nápovědy.|
|\< Meta name="Microsoft.Help.Category" content = "[string]" / >|Produkty se používá k identifikaci dílčí části objektů obsahu. Můžete určit více pododdíly tématu nebo toto klíčové slovo můžete vynechat, pokud nechcete, aby se odkazy k identifikaci všech podsekcí. Tato značka se používá k ukládání atributy pro TargetOS a TargetFrameworkMoniker, když je téma převést ze starší verze nápovědy. Formát obsahu je AttributeName:AttributeValue.|
|\< Meta name="Microsoft.Help.TopicVersion obsah ="[tématu číslo verze]"/ >|Určuje tuto verzi tématu, pokud existuje více verzí v katalogu. Protože Microsoft.Help.Id nemusí být jedinečný, tato značka se vyžaduje při více než jednu verzi tématu existuje v katalogu, například když katalog obsahuje téma pro rozhraní .NET Framework 3.5 a téma pro rozhraní .NET Framework 4 a obě mají stejné Micro obnovitelně. Help.Id.|
|\< Meta name = "SelfBranded" content = "[hodnotu TRUE nebo FALSE]" / >|Určuje, zda toto téma používá balíček Správce knihovny nápovědy počáteční značky nebo vlastní balíček, který je specifický pro téma. Tato značka musí být buď TRUE nebo FALSE. Pokud je hodnota TRUE, pak balíček přizpůsobení prostředí značce pro související téma přepíše značky balíčku, který je nastaven při spuštění Správce knihovny nápovědy tak, aby tématu je vykreslen tak, jak má i v případě, že se liší od vykreslování jiný obsah. Pokud je FALSE, v aktuálním tématu je vykreslena podle značky balíčku, který je nastaven při spuštění Správce knihovny nápovědy. Ve výchozím nastavení předpokládá svým značky jako NEPRAVDA, pokud SelfBranded proměnná je deklarovaná jako TRUE; Správce knihovny nápovědy proto není nutné deklarovat \<meta name = "SelfBranded" content = "FALSE" / >.|

### <a name="creating-a-branding-package"></a>Vytváří se balíček pro přizpůsobení prostředí značce
 Verze sady Visual Studio zahrnuje celou řadou různých produktů Visual Studio, včetně izolované a integrované prostředí pro partnerů pro Visual Studio.  Každá z těchto produktů vyžaduje určitý stupeň obsahu založeného na téma nápovědy branding podporu pro produkt jedinečné.  Například témat Visual Studio musí mít konzistentní Image značky prezentace, zatímco SQL Studio, která zabalí ISO prostředí vyžaduje svou vlastní jedinečnou nápovědu obsahu branding pro každého tématu.  Integrovaná partnerská prostředí může být vhodné jejich témata nápovědy, které se v rámci nadřazené obsahu nápovědy produktu Visual Studio při zachování jejich vlastní téma značky.

 Přizpůsobení prostředí značce balíčky se nainstalují podle produktu, který obsahuje aplikace Help Viewer.  Pro produkty Visual Studio:

- Náhradní vlastní balíček (Branding_\<národní prostředí > .mshc) je nainstalována v kořenovém adresáři aplikace Help Viewer 2.1 (Příklad: C:\Program Files (x86) \Microsoft Help Viewer\v2.1) pomocí této aplikace Help Viewer jazykové sady.  Používá se pro případy, ve kterém není nainstalován produkt branding balíčku (žádný obsah nejsou nainstalované) nebo kde je nainstalovaný balíček značky poškozený.  Prvky sady Visual Studio (logo a zpětná vazba) jsou ignorovány při použití značky balíčku aplikace kořenové použití náhradní lokality.

- Při instalaci sady Visual Studio obsah z balíčku obsahu služby (pro první čas instalace obsahu scénář) je také nainstalována značky balíčku.  Pokud dojde k přizpůsobení prostředí značce balíčku aktualizace, je aktualizace nainstalována při další aktualizaci obsahu nebo akce instalace dalších balíčků se stane.

  Microsoft Help Viewer podporuje značky na základě metadat tématu témata.

- Kde tématu metadat definuje vlastní značky = true, tématu, jako je vykreslování, neprovádějte žádnou akci (až na hodnotu značky).

- Kde tématu metadat definuje vlastní značky = false, použití značky balíčku spojeného s hodnotou TopicVendor metadat.

- Kde tématu metadat definuje name="Microsoft.Help.TopicVendor" obsah =\< značky název balíčku v dodavatele MSHA >, pomocí značky balíčku definované v hodnotě obsahu.

- V katalogu sady Visual Studio je priorita aplikace Branding balíčků.  První sady Visual Studio výchozí branding se použije a poté, pokud definované v metadatech tématu a podpora s přidružené branding balíček (jak jsou definovány v msha instalace), dodavatele definované branding se použije jako přepsání.

  Přizpůsobení prostředí značce elementy obvykle spadají do tří hlavních kategorií:

- Prvky hlavičky (například odkazu na zpětnou vazbu, text zřeknutí se práv podmíněné, logo)

- Obsah chování (příklady zahrnují rozbalení/sbalení ovládacího prvku textové prvky a prvky fragment kódu)

- Zápatí prvků (např. Copyright)

  Položky, které jsou považovány za obsahovat obchodní značku prvky (podrobně popsané v této specifikace):

- Logo katalogu/produktu (např. Visual Studio)

- Prvky odkazu a e-mailu zpětné vazby

- Text zřeknutí se práv

- Text o autorských právech

  Podpůrné soubory v balíčku Visual Studio Help Viewer značky patří:

- Grafika (loga, ikony, atd.)

- Soubory skriptu Branding.js – podpůrné obsahu chování

- Branding.XML – řetězce, které jsou používány konzistentně napříč katalogu obsahu.  Poznámka: pro Visual Studio lokalizace textové prvky v branding.xml, patří _locID = "\<jedinečnou hodnotu >"

- Branding.CSS – definice stylů pro prezentaci konzistence

- Printing.CSS – definice stylů pro konzistentní tisk prezentace

  Jak bylo uvedeno výše, jsou spojeny s tématu Branding balíčky:

- Když SelfBranded = false je definované v metadatech, tématu dědí katalogu značky balíčku

- Nebo pokud SelfBranded = false a že je jedinečný Branding balíček definovány v MSHA a k dispozici při instalaci obsahu

  Pro implementaci vlastní značky balíčky VSPs (VSP obsah, SelfBranded = True), je jedním ze způsobů, aby bylo možné pokračovat začít s balíček záložní značky (instalovanou se aplikace Help Viewer) a název souboru podle potřeby změnit.  Branding_\<národní prostředí > .mshc soubor je soubor zip s příponou souboru změněn na .mshc, takže jednoduše změňte příponu na .zip z .mshc a rozbalit obsah.  Níže jsou značky balíčku elementy a upravovat podle potřeby (například změnit logo VSP logo a odkaz na logo v souboru Branding.xml, aktualizujte Branding.xml za VSP specifika atd.).

  Po dokončení všech změn, vytvořte soubor zip obsahující požadované prvky značky a změňte jeho příponu na .mshc.

  Přidružit vlastní značky balíčku, vytvořte MSHA, který obsahuje odkaz na soubor značky mshc spolu s obsahu mshc (obsahující témata).  Níže jsou uvedeny "MSHA" jak vytvořit základní MSHA.

  Soubor Branding.xml obsahuje prvky seznamů používané k vykreslování konzistentně konkrétní položky v tématu, když se téma obsahuje \<meta name="Microsoft.Help.SelfBranded" content = "false" / >.  Visual Studio seznam prvků v souboru Branding.xml je uveden níže.  Tento seznam je určena pro použití jako šablony pro přechod ISO prostředí, kde se upravovat tyto prvky (například logo, zpětnou vazbu a autorská práva) podle své vlastní značky produktu musí.

  Poznámka: proměnné, které jsou označeny "{n}" mít závislostí kódu – odebrání nebo změny těchto hodnot způsobí chyby a případně selhání aplikace. Lokalizace identifikátory (například _locID="codesnippet.n") jsou obsažené v balíčku Branding Visual Studio.

  **Branding.XML**

|||
|-|-|
|Funkce:|**CollapsibleArea**|
|Použití:|Rozbalte text sbalí obsahu ovládacího prvku|
|**Element**|**Hodnota**|
|ExpandText|Rozbalte položku|
|CollapseText|Sbalit|
|Funkce:|**CodeSnippet**|
|Použití:|Text ovládacího prvku fragmentu kódu.  Poznámka: Obsah fragment kódu s prostorem "Non-zásadní" se změní na místo.|
|**Element**|**Hodnota**|
|CopyToClipboard|Kopírovat do schránky|
|ViewColorizedText|Zobrazit Obarvený text|
|CombinedVBTabDisplayLanguage|Visual Basic (ukázka)|
|VBDeclaration|Deklarace|
|VBUsage|Použití|
|Funkce:|**Zpětná vazba, zápatí a Logo**|
|Použití:|Poskytnutí zpětné vazby ovládacího prvku pro zákazníka, které chcete poskytnout zpětnou vazbu na aktuální téma e-mailem.  O autorských právech text pro obsah.  Logo definice.|
|**Element**|**Hodnota (tyto řetězce lze upravit podle potřeby obsahu adopter.)**|
|CopyRight|© 2013 Microsoft Corporation. Všechna práva vyhrazena.|
|SendFeedback|\<href = "{0}" {1}> Odeslat názor\</a > k tomuto tématu společnosti Microsoft.|
|FeedbackLink||
|LogoTitle|[!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)]|
|LogoFileName|vs_logo_bk.GIF|
|LogoFileNameHC|vs_logo_wh.GIF|
|Funkce:|**Právní omezení**|
|Použití:|Obsah přeložený sadu právní omezení velikosti písmen specifické pro počítač.|
|**Element**|**Hodnota**|
|MT_Editable|Tento článek byl strojově přeložen. Pokud máte připojení k Internetu, vyberte možnost "Zobrazit toto téma online" pro zobrazení této stránky v upravitelném režimu spolu s původním anglickým obsahem ve stejnou dobu.|
|MT_NonEditable|Tento článek byl strojově přeložen. Pokud máte připojení k Internetu, vyberte možnost "Zobrazit toto téma online" pro zobrazení této stránky v upravitelném režimu spolu s původním anglickým obsahem ve stejnou dobu.|
|MT_QualityEditable|Tento článek byl přeložen ručně. Pokud máte připojení k Internetu, vyberte možnost "Zobrazit toto téma online" pro zobrazení této stránky v upravitelném režimu spolu s původním anglickým obsahem ve stejnou dobu.|
|MT_QualityNonEditable|Tento článek byl přeložen ručně. Pokud máte připojení k Internetu, vyberte možnost "Zobrazit toto téma online" pro zobrazení této stránky v upravitelném režimu spolu s původním anglickým obsahem ve stejnou dobu.|
|MT_BetaContents|Tento článek byl strojově přeložen pro předběžné vydání. Pokud máte připojení k Internetu, vyberte možnost "Zobrazit toto téma online" pro zobrazení této stránky v upravitelném režimu spolu s původním anglickým obsahem ve stejnou dobu.|
|MT_BetaRecycledContents|Tento článek byl přeložen ručně pro předběžné vydání. Pokud máte připojení k Internetu, vyberte možnost "Zobrazit toto téma online" pro zobrazení této stránky v upravitelném režimu spolu s původním anglickým obsahem ve stejnou dobu.|
|Funkce:|**LinkTable**|
|Použití:|Podpora pro online téma obsahuje odkazy|
|**Element**|**Hodnota**|
|LinkTableTitle|Vazební tabulka|
|TopicEnuLinkText|Zobrazit anglickou verzi\</a > tohoto tématu, který je dostupný na vašem počítači.|
|TopicOnlineLinkText|Zobrazit toto téma \<href = "{0}" {1}> online\</a >|
|OnlineText|Online|
|Funkce:|**Ovládacího prvku video zvuku**|
|Použití:|Zobrazit elementy a text v případě video obsahu|
|**Element**|**Hodnota**|
|MultiMediaNotSupported|Aplikace Internet Explorer 9 nebo vyšší musí být nainstalována, aby podporovaly {0} obsah.|
|VideoText|zobrazení videa|
|AudioText|vysílání datového proudu zvuku|
|OnlineVideoLinkText|\<p > pro zobrazení videa patřícího k tomuto tématu, klikněte na tlačítko {0} \<href = "{1}" >{2}tady\</a >.\< /p >|
|OnlineAudioLinkText|\<p > poslech Audio nahrávky patřící k tomuto tématu klikněte na tlačítko {0} \<href = "{1}" >{2}tady\</a >.\< /p >|
|Funkce:|**Ovládací prvek obsahu není nainstalován**|
|Použití:|Textové prvky (řetězce) použita pro vykreslení contentnotinstalled.htm|
|**Element**|**Hodnota**|
|ContentNotInstalledTitle|V počítači nebyl nalezen žádný obsah.|
|ContentNotInstalledDownloadContentText|\<p > pro stažení obsahu do vašeho počítače, \<href = "{0}" {1}> klikněte na kartu spravovat\</a >.\< /p >|
|ContentNotInstalledText|\<p > ve vašem počítači není nainstalován žádný obsah. Kontaktujte správce pro místní instalaci obsahu nápovědy. \</p >|
|Funkce:|**Téma nebyl nalezen ovládací prvek**|
|Použití:|Textové prvky (řetězce) použita pro vykreslení topicnotfound.htm|
|**Element**|**Hodnota**|
|TopicNotFoundTitle|Nelze najít požadované téma ve vašem počítači.|
|TopicNotFoundViewOnlineText|\<p > požadované téma nebyl nalezen v počítači, ale můžete \<href = "{0}" {1}> zobrazit téma online\</a >.\< /p >|
|TopicNotFoundDownloadContentText|\<p > v navigačním podokně se odkazy na podobná témata nebo \<href = "{0}" {1}> klikněte na kartu spravovat\</a > pro stažení obsahu do vašeho počítače.\< /p >|
|TopicNotFoundText|\<p > požadované téma nebyl nalezen v počítači. \</p >|
|Funkce:|**Téma poškozený ovládacího prvku**|
|Použití:|Textové prvky (řetězce) použita pro vykreslení topiccorrupted.htm|
|**Element**|**Hodnota**|
|TopicCorruptedTitle|Nelze zobrazit požadované téma.|
|TopicCorruptedViewOnlineText|\<p > aplikace Help Viewer nemůže zobrazit požadované téma. Pravděpodobně došlo k chybě v obsahu tématu nebo základní závislosti systému. \</p >|
|Funkce:|**Ovládací prvek domovské stránky**|
|Použití:|Text podporuje zobrazení obsahu aplikace Help Viewer uzel nejvyšší úrovně.|
|**Element**|**Hodnota**|
|HomePageTitle|Domovská stránka prohlížeč nápovědy|
|HomePageIntroduction|\<p > Vítá vás Microsoft Help Viewer, základní zdroj informací pro každého, kdo používá nástroje, produkty, technologie a služby společnosti Microsoft. Aplikace Help Viewer poskytuje přístup k postupy a referenční informace, ukázky kódu, technické články a další. Hledání obsahu, je nutné, procházet obsah, použít fulltextové vyhledávání nebo procházení obsahu pomocí indexu – klíčové slovo. \</p >|
|HomePageContentInstallText|\<p >\<br / > použití \<href = "{0}" {1}> Spravovat obsah\</a > karty můžete provádět následující:\<ul >\<li > přidávat obsah do počítače.\< /li >\<li > vyhledat aktualizace místního obsahu.\< /li >\<li > odebrat obsah z vašeho počítače.\< /li >\</ul >\</p >|
|HomePageInstalledBooks|Nainstalované knihy|
|HomePageNoBooksInstalled|V počítači nebyl nalezen žádný obsah.|
|HomePageHelpSettings|Nastavení obsahu nápovědy|
|HomePageHelpSettingsText|\<p > vaše aktuální nastavení je místní nápovědy. Aplikace Help Viewer zobrazí obsah, který jste nainstalovali ve vašem počítači. \<br / > Chcete-li změnit zdroj obsahu nápovědy na panelu nabídek sady Visual Studio zvolte \<span style = "{0}" > Nápověda, nastavení předvoleb nápovědy\</span >.\< br / >\</p >|
|MB|MB|

 **Branding.js**

 Soubor branding.js obsahuje JavaScript používá značky elementů Visual Studio Help Viewer.  Níže je seznam značky elementů a podpůrné funkce jazyka JavaScript.  Všechny řetězce lokalizované pro tento soubor jsou definovány v sekci "Lokalizovatelných řetězců" v horní části tohoto souboru.  Pro umístění řetězců v rámci branding.js soubor byl vytvořen soubor ICL.

||||
|-|-|-|
|**Přizpůsobení prostředí značce funkce**|**Funkce jazyka JavaScript**|**Popis**|
|Var...||Definujte proměnné, které|
|Získejte jazyk kódu uživatele|setUserPreferenceLang|mapuje indexu # do jazyka kódu|
|Nastavení a získání hodnoty souboru cookie|getCookie setCookie||
|Zděděný člen|changeMembersLabel|Rozbalit/sbalit zděděného členu|
|Když SelfBranded = False|Při načtení|Přečtěte si řetězec dotazu a zkontrolujte, zda se jedná o žádost o tisk.  Nastavte všechny codesnippets zaměřit kartě upřednostňované uživateli.  Pokud se jedná o žádost o tisk, nastavte vlastnost isPrinterFriendly na hodnotu true. Zkontrolujte režim s vysokým kontrastem.|
|Fragment kódu|addSpecificTextLanguageTagSet||
||getIndexFromDevLang||
||ChangeTab||
||setCodesnippetLang||
||setCurrentLang||
||CopyToClipboard||
|CollapsibleArea|addToCollapsibleControlSet|Zapište všechny objektu sbalitelného ovládacího prvku do seznamu.|
||CA_Click|na základě stavu sbalitelné oblasti, definuje, které obrázek a text, který má k dispozici|
|Podpora kontrast – Logo|isBlackBackground()|Voláno k určení, zda je černé pozadí.  Jenom přesné při režim s vysokým kontrastem.|
||isHighContrast()|barevný rozsah použijte k detekci režim s vysokým kontrastem|
||onHighContrast(black)|Volá se, když se zjistí vysoký kontrast|
|Funkce Obrázků|||
||addToLanSpecTextIdSet(id)||
||updateLST(currentLang)||
||getDevLangFromCodeSnippet(lang)||
|Multimediální funkce|Popisek (zahájení, ukončení, text, styl)||
||findAllMediaControls(normalizedId)||
||getActivePlayer(normalizedId)||
||captionsOnOff(id)||
||toSeconds(t)||
||getAllComments(node)||
||styleRectify (styleName, styleValue)||
||showCC(id)||
||subtitle(ID)||

 **SOUBORY HTM**

 Přizpůsobení prostředí značce balíček obsahuje sadu souborů HTM, které podporují scénáře pro komunikaci klíčové informace, které pomáhají uživatelům obsahu, například domovskou stránku, která obsahuje oddíl popisující, které sady obsahu jsou nainstalovány a stránky, která sděluje uživateli, když nelze témata najít v místní sadě témata. Tyto soubory HTM, lze upravit podle produktu.  Dodavatelé ISO prostředí budou moct přijmout výchozí značky balíček a změnit chování a obsah těchto stránek do sady jejich potřeby.  Tyto soubory naleznete v příslušných značky balíčku v pořadí pro přizpůsobení prostředí značce značky získat příslušný obsah ze souboru branding.xml.

||||
|-|-|-|
|**Soubor**|**Použití**|**Zobrazit zdroj obsahu**|
|domovskastranka.htm|Toto je stránka, která zobrazuje aktuálně nainstalovaný obsah a jakékoli jiné zprávy, které jsou vhodné pro konkrétního uživatele o jejich obsahu.  Tento soubor obsahuje další obsah "Microsoft.Help.Id" data atributu meta = "-1" který nahradí to obsahu v horní části místního obsahu obsahu.||
||&LT; META_HOME_PAGE_TITLE_ADD / &GT;|Branding.XML, značka \<HomePageTitle >|
||&LT; HOME_PAGE_INTRODUCTION_SECTION_ADD / &GT;|Branding.XML, značka \<HomePageIntroduction >|
||&LT; HOME_PAGE_CONTENT_INSTALL_SECTION_ADD / &GT;|Branding.XML, značka \<HomePageContentInstallText >|
||&LT; HOME_PAGE_BOOKS_INSTALLED_SECTION_ADD / &GT;|Nadpis oddílu Branding.xml značky\<HomePageInstalledBooks >, data generovaná z aplikace, \<HomePageNoBooksInstalled > při instalaci žádná knihy.|
||&LT; HOME_PAGE_SETTINGS_SECTION_ADD / &GT;|Nadpis oddílu Branding.xml značky \<HomePageHelpSettings >, části textu \<HomePageHelpSettingsText >.|
|topiccorrupted.htm|Téma v nastavení místní existuje, ale pro z nějakého důvodu nelze zobrazit (poškozený obsah).||
||&LT; META_TOPIC_CORRUPTED_TITLE_ADD / &GT;|Branding.XML, značka \<TopicCorruptedTitle >|
||&LT; TOPIC_CORRUPTED_SECTION_ADD / &GT;|Branding.XML, značka \<TopicCorruptedViewOnlineText >|
|topicnotfound.htm|Když téma nebyl nalezen v místní obsah ani nastavení není k dispozici online||
||&LT; META_TOPIC_NOT_FOUND_TITLE_ADD / &GT;|Branding.XML, značka \<TopicNotFoundTitle >|
||&LT; META_TOPIC_NOT_FOUND_ID_ADD / &GT;|Branding.XML, značka \<TopicNotFoundViewOnlineText > + \<TopicNotFoundDownloadContentText >|
||&LT; TOPIC_NOT_FOUND_SECTION_ADD / &GT;|Branding.XML, značka \<TopicNotFoundText >|
|contentnotinstalled.htm|Pokud není žádný místní obsah instalaci produktu.||
||&LT; META_CONTENT_NOT_INSTALLED_TITLE_ADD / &GT;|Branding.XML, značka \<ContentNotInstalledTitle >|
||&LT; META_CONTENT_NOT_INSTALLED_ID_ADD / &GT;|Branding.XML, značka \<ContentNotInstalledDownloadContentText >|
||&LT; CONTENT_NOT_INSTALLED_SECTION_ADD / &GT;|Branding.XML, značka \<ContentNotInstalledText >|

 **Soubory šablon stylů CSS**

 Nápověda prohlížeč Branding balíček pro Visual Studio obsahuje dva soubory šablon stylů css pro podporu obsahu konzistentní prezentace nápovědy aplikace Visual Studio:

- Branding.CSS – obsahuje prvky šablon stylů css pro vykreslení where SelfBranded = false

- Printer.CSS – obsahuje prvky šablon stylů css pro vykreslení where SelfBranded = false

  Soubory Branding.CSS obsahuje definice pro Visual Studio tématu prezentaci (výstrahou je, že branding.css součástí Branding_\<národní prostředí > .mshc z balíčku služby se může změnit).

  **Grafické soubory**

  Visual Studio obsahu zobrazuje logo sady Visual Studio, stejně jako jiné grafické.  Úplný seznam grafických souborů v balíčku značky Visual Studio Help Viewer je uveden níže.

||||
|-|-|-|
|**Soubor**|**Použití**|**Příklady**|
|Clear.GIF|Použije k vykreslení sbalitelné oblasti||
|footer_slice.GIF|Prezentace zápatí||
|info_icon.GIF|Při zobrazení informací o|Právní omezení|
|online_icon.GIF|Tato ikona se k online odkazy||
|tabLeftBD.gif|Použije k vykreslení kontejneru fragmentu kódu||
|tabRightBD.gif|Použije k vykreslení kontejneru fragmentu kódu||
|vs_logo_bk.GIF|Používá pro normální kontrast logo odkazy, jak je definováno ve značce Branding.xml \<LogoFileName >.  Pro produkty Visual Studio je název logo vs_logo_bk.gif.||
|vs_logo_wh.GIF|Používá pro normální vysokou logo odkazy definované ve značce Branding.xml \<LogoFileNameHC >.  Pro produkty Visual Studio je název logo vs_logo_wh.gif.||
|ccOff.png|Titulky grafiky||
|ccOn.png|Titulky grafiky||
|ImageSprite.png|Použije k vykreslení sbalitelné oblasti|Rozbalit nebo sbalit grafiky|

### <a name="deploying-a-set-of-topics"></a>Nasazení sady témata
 Toto je jednoduchý a rychlý kurz pro vytvoření sady obsahu nasazení aplikace Help Viewer MSHA soubor a sadu souborů CAB nebo MSHCs obsahující témata. MSHA je soubor XML, který popisuje sadu souborů CAB nebo MSHC soubory. Aplikace Help Viewer můžete přečíst MSHA získat seznam obsahu (). Soubor CAB nebo. Soubory MSHC) dostupná pro místní instalaci.

 Toto je pouze základy popisující velmi základní schéma XML pro MSHA Prohlížeč nápovědy.  Není pod tento stručný přehled a ukázka HelpContentSetup.msha příklad implementace.

 Název MSHA, pro účely tento úvod je HelpContentSetup.msha (název souboru může obsahovat cokoli, s příponou. MSHA). HelpContentSetup.msha (následující příklad) by měl obsahovat seznam souborů CAB nebo MSHCs k dispozici.  Typ souboru musí být konzistentní vzhledem k aplikacím v rámci MSHA (nepodporuje kombinace typů souborů MSHA a souboru CAB). Pro každý soubor CAB nebo MSHC, měla by existovat \<div třídy = "balíček" >...  \< /div > (viz následující příklad).

 Poznámka: v následujícím příkladu implementace jsme přidali balíček značky. To je důležité zahrnout zajistí potřebný prvky vykreslování obsahu sady Visual Studio a obsahu chování.

 Ukázkový soubor HelpContentSetup.msha: (nahradit "obsah nastaven název 1" a "obsahu, název sady 2" atd. s názvy souborů.)

```
<html>
<head />
<body class="vendor-book">
<div class="details">
<span class="vendor">Your Company</span>
<span class="locale">en-us</span>
<span class="product">Your Company Help Content</span>
<span class="name">Your Company Help Content</span>
</div>
<div class="package-list">
<div class="package">
<span class="name">Your_Company _Content_Set_1</span>
<span class="deployed">True</span>
<a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a>
</div>
<div class="package">
<span class="name">Your_Company _Content_Set_2</span>
<span class="deployed">True</span>
<a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a>
</div>.

```

1. Vytvořte místní složku, něco jako "C:\SampleContent"

2. V tomto příkladu používáme MSHC soubory tak, aby obsahovala témata.  MSHC je zip s příponou souboru změnil z .zip na. MSHC.

3. Vytvořte níže HelpContentSetup.msha jako textový soubor (Poznámkový blok se použila k vytvoření souboru) a uloží ho do výše uvedené složky (viz krok 1).

   Třída "Značky" existuje a je jedinečný. Branding mshc je součástí tento úvod tak, aby nainstalovaného obsahu budou mít brandingu a obsahu chování, které jsou součástí MSHCs bude mít vhodnou podporu elementů obsažených v balíčku přizpůsobení prostředí značce. Bez toho způsobí chyby při systému hledá podporu položky, které nejsou součástí zkopírované (nainstalovat) obsahu.

   Získat značku balíčku sady Visual Studio, zkopírujte soubor Branding_en US.mshc na C:\Program Files (x86) \Microsoft Help Viewer\v2.1\ pracovní složky.

```html
<html>
<head />
<body class="vendor-book">
<div class="details">
<span class="vendor">Your Company</span>
<span class="locale">en-us</span>
<span class="product">Your Company Help Content</span>
<span class="name">Your Company Help Content</span>
</div>
<div class="package-list">
<div class="package">
<span class="name">Your_Company _Content_Set_1</span>
<span class="deployed">True</span>
<a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a>
</div>
<div class="package">
<span class="name">Your_Company _Content_Set_2</span>
<span class="deployed">True</span>
<a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a>
</div>
<div class="package">
<span class="packageType">branding</span>
<span class="name">Branding_en-US</span>
<span class="deployed">True</span>
<a class="current-link" href="Branding_en-US.mshc">Branding_en-US.mshc</a>
</div>
</div>
</body>
</html>

```

 **Shrnutí**

 VSPs nasadit jejich obsahu sady Visual Studio Help Viewer vám umožní používání a rozšiřování výše uvedené kroky.

### <a name="adding-help-to-the-visual-studio-shell-integrated-and-isolated"></a>Přidání Nápověda pro Visual Studio Shell (integrovaný režim a izolovaný režim)
 **Úvod**

 Tento návod ukazuje, jak zahrnout obsah nápovědy do aplikace Visual Studio Shell a potom ji nasadíte.

 **Požadavky**

1. [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)]

2. [Izolované aplikace Visual Studio 2013 Shell Redist](http://www.microsoft.com/visualstudio/11/downloads#vs-shell)

   **Přehled**

   [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] Prostředí je verze [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] integrovaného vývojového prostředí, ve kterém vytváříte aplikaci. Tyto aplikace obsahují izolovaného prostředí, spolu s rozšíření, které vytvoříte. Použití projektových šablon izolovaného prostředí, které jsou součástí [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] SDK k sestavení rozšíření.

   Základní kroky pro vytvoření aplikace založené na izolovaném prostředí a jeho nápovědy:

3. Získat [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] ISO prostředí redistributable (Microsoftu ke stažení).

4. V sadě Visual Studio vytvořte příponu nápovědy, který je založen na izolovaného prostředí, například, rozšíření nápovědy společnosti Contoso, která je popsána dále v tomto názorném postupu.

5. Zabalení rozšíření a ISO prostředí redistributable do nasazení MSI (nastavení aplikace). Tento návod neobsahuje krok instalace.

   Vytvořte úložiště obsahu sady Visual Studio. Pro scénář prostředí Integrated Shell změňte Visual Studio12 název katalogu produktu takto:

- Vytvořte složku C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio12.

- Vytvořte soubor CatalogType.xml a přidejte ho do složky. Soubor by měl obsahovat následující řádky kódu:

  ```
  <?xml version="1.0" encoding="UTF-8"?>
  <catalogType>UserManaged</catalogType>
  ```

  Definování úložiště obsahu v registru. Pro prostředí Integrated Shell změňte název katalogu produktů VisualStudio12:

- HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Catalogs\VisualStudio12

   Klíč: Hodnota řetězce LocationPath: C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio12\

- HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Catalogs\VisualStudio12\en-us

   Klíč: Hodnota řetězce CatalogName: [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] dokumentace

  **Vytvoření projektu**

  Chcete-li vytvořit rozšíření izolovaného prostředí:

1. V sadě Visual Studio v části **souboru**, zvolte **nový projekt**v části **ostatní typy projektů** zvolte **rozšiřitelnost**a klikněte na tlačítko  **Izolované prostředí sady Visual Studio**. Pojmenujte projekt `ContosoHelpShell`) Chcete-li vytvořit projekt rozšiřitelnosti založený na šabloně izolované prostředí sady Visual Studio.

2. V Průzkumníku řešení otevřete v projektu ContosoHelpShellUI ve složce zdrojové soubory ApplicationCommands.vsct. Ujistěte se, že tento řádek je označené jako komentář (vyhledejte "No_Help"): `<!-- <define name=“No_HelpMenuCommands”/> -->`

3. Zvolte klávesu F5 ke kompilaci a spuštění **ladění**. V experimentální instanci izolovaného prostředí IDE, zvolte **pomáhají** nabídky. Ujistěte se, že **zobrazit nápovědu**, **přidat nebo odebrat obsah nápovědy**, a **nastavení předvoleb nápovědy** zobrazí příkazy.

4. V Průzkumníku řešení otevřete v projektu ContosHelpShell ve složce přizpůsobení prostředí ContosoHelpShell.pkgdef. K definování katalogu nápovědy společnosti Contoso, přidejte následující řádky:

   ```
    [$RootKey$\Help]
   "Product"="Contoso"
   "Catalog"="Contoso"
   “Version"="100"
   "BrandingPackage"="ContosoBrandingPackage.mshc"
   ```

5. V Průzkumníku řešení otevřete v projektu ContosHelpShell ve složce přizpůsobení prostředí ContosoHelpShell.Application.pkgdef. Pokud chcete povolit, Nápověda F1, přidejte následující řádky:

   ```
   // F1 Help Provider

   [$RootKey$\HelpProviders\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}]
   "Name"="13407"
   "Package"="{DA9FB551-C724-11d0-AE1F-00A0C90FFFC3}"
   @="Help3 Provider"
   [$RootKey$\HelpProviders]
   @="{C99BDC23-FF29-46bf-9658-ADD634CCAED8}"
   [$RootKey$\Services\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}]
   "Name"="Help3 Provider"
   @="{4A791146-19E4-11D3-B86B-00C04F79F802}"
   ```

6. V Průzkumníku řešení zvolte v místní nabídce řešení ContosoHelpShell **vlastnosti** položky nabídky. V části **vlastnosti konfigurace**vyberte **nástroje Configuration Manager**. V **konfigurace** sloupce, změňte hodnotu každé "Debug" na "Verze".

7. Sestavte řešení. Tím se vytvoří sadu souborů ve složce verzi, která se použije v další části.

   Abyste to mohli otestovat jakoby nasazení:

8. Na počítači nasazujete Contoso k instalaci na stažený ISO prostředí (uvedeného).

9. Vytvořte složku v \\\Program Files (x86)\\a pojmenujte ho `Contoso`.

10. Zkopírujte obsah ze složky vydání ContosoHelpShell \\složku \Program Files (x86) \Contoso\.

11. Spusťte Editor registru výběrem **spustit** v **Start** nabídky a zadáním `Regedit`. V okně editor registru, zvolte **souboru**a potom **Import**. Přejděte do složky projektu ContosoHelpShell. V podsložce ContosoHelpShell zvolte ContosoHelpShell.reg.

12. Vytvoření obsahu úložiště:

     Pro prostředí ISO - vytvoření obsahu úložiště Contoso C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\ContosoDev12

     Pro [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] prostředí Integrated Shell, vytvořte složku C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio12

13. Vytvořte CatalogType.xml a přidejte do obsahujícího obsahu úložiště (v předchozím kroku):

    ```
    <?xml version="1.0" encoding="UTF-8"?>
    <catalogType>UserManaged</catalogType>
    ```

14. Přidejte následující klíče registru:

     HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Catalogs\VisualStudio12Key: Hodnota řetězce LocationPath:

     Pro prostředí ISO:

     C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio12

     [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] Integrované prostředí:

     C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio12en-USA

     Klíč: Hodnota řetězce CatalogName: [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] dokumentaci. Pro prostředí ISO jde o název katalogu.

15. Zkopírujte obsah (soubory CAB nebo MSHC a MSHA) do místní složky.

16. Příklad integrované prostředí příkazového řádku pro testování úložiště obsahu. ISO prostředí změňte hodnoty katalogu a launchingApp podle potřeby tak, aby odpovídaly produktu.

      Metoda /helpQuery/catalogname VisualStudio12 "C:\Program soubory (x86) \Microsoft Help Viewer\v2.1\HlpViewer.exe" = "Stránka & id = ContosoTopic0" /launchingApp Microsoft VisualStudio, 12.0

17. Spusťte aplikaci Contoso (z kořenového adresáře aplikace Contoso). V rámci prostředí ISO, zvolte **pomáhají** položky nabídky a změnit **nastavení předvoleb nápovědy** k **místní Nápověda**.

18. V rámci prostředí, zvolte **pomáhají** položku nabídky, poté **zobrazit nápovědu**. By měl spustit místní nápovědy. Zvolte **spravovat obsah** kartu. V části **zdrojová data instalace**, zvolte **disku** přepínač. Zvolte **...**  tlačítko a přejděte do místní složky obsahující obsah společnosti Contoso (zkopírovaný do místní složky v předchozím kroku). Zvolte HelpContentSetup.msha. Contoso by měl nyní zobrazí jako knihu výběry knihy. Zvolte **přidat**a klikněte na tlačítko **aktualizace** tlačítko (pravého dolního rohu).

19. Chcete-li otestovat funkci F1 integrovaného vývojového prostředí Contoso, stiskněte klávesu F1.

### <a name="additional-resources"></a>Další prostředky

Rozhraní API modulu Runtime naleznete v tématu [rozhraní API pomáhají Windows](http://msdn.microsoft.com/library/windows/desktop/hh447318\(v=vs.85\).aspx).

Další informace o tom, jak využít rozhraní API pomáhají najdete v tématu [pomáhají příklady kódu pro prohlížeč](http://visualstudiogallery.msdn.microsoft.com/f08f296f-7076-4aec-8da3-8f0fbe04461e).

Aktualizace na nejnovější problémy, najdete [Readme Prohlížeč nápovědy](http://go.microsoft.com/fwlink/?LinkID=231397&clcid=0x409).