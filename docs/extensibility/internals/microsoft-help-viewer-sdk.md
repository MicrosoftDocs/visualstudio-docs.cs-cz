---
title: Microsoft Help Viewer SDK | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 620d7dcd-d462-475e-a449-fbfa06ff12c5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 721623edabcaf3b395a143dd193cae3fd71d93d6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707157"
---
# <a name="microsoft-help-viewer-sdk"></a>Microsoft Help Viewer SDK

Tento článek obsahuje následující úkoly pro integrátory prohlížeče nápovědy sady Visual Studio:

- Vytvoření tématu (podpora F1)

- Vytvoření balíčku pro branding obsahu prohlížeče nápovědy

- Nasazení sady článků

- Přidání nápovědy do prostředí sady Visual Studio (integrované nebo izolované)

- Další zdroje

## <a name="create-a-topic-f1-support"></a>Vytvoření tématu (podpora F1)

Tato část obsahuje přehled součástí prezentovaného tématu, požadavky na téma, stručný popis, jak vytvořit téma (včetně požadavků na podporu F1) a nakonec ukázkové téma s vykresleným výsledkem.

**Přehled tématu prohlížeče nápovědy**

Pokud je téma voláno k vykreslování, prohlížeč nápovědy získá prvky balíčku značky, které jsou přidruženy k tématu v době instalace nebo poslední aktualizace, spolu s tématem XHTML a kombinuje tyto dva, aby výsledkem bylo zobrazení prezentovaného obsahu (data o značce + data tématu).  Balíček značky obsahuje loga, podporu chování obsahu a text značky (autorská práva atd.).  Další informace o prvcích balíčku značky naleznete níže v části "Vytvoření balíčku značky".  V případě, že k tématu není přidružen žádný balíček značky, prohlížeč nápovědy použije záložní balíček značky umístěný v kořenovém adresáři aplikace Prohlížeče nápovědy (Branding_en-US.mshc).

**Požadavky na témata prohlížeče nápovědy**

Chcete-li být vykreslensprávně v prohlížeči nápovědy, musí být nezpracovaný obsah tématu W3C Basic 1.1 XHTML.

Téma obvykle obsahuje dvě části:

- Metadata (viz Odkaz na metadata obsahu): údaje o tématu, například jedinečné ID tématu, hodnota klíčového slova, id obsahu, ID nadřazeného uzlu atd.

- Obsah těla: kompatibilní s W3C Basic 1.1 XHTML, který zahrnuje podporované chování obsahu (sbalitelná oblast, fragment kódu atd. Úplný seznam je uveden níže).

Podporované ovládací prvky sady Visual Studio Branding Package:

- Odkazy

- CodeSnippet

- Sbalitelná oblast

- Zděděný člen

- LanguageSpecificText

Podporované jazykové řetězce (neřešení velkých a malých písmen):

- javascript

- csharp nebo c #

- cplusplus nebo visualc++ nebo c++

- Jscript

- visualbasic nebo vb

- f# nebo fsharp nebo fs

- other - řetězec, který představuje název jazyka

**Vytvoření tématu Prohlížeče nápovědy**

Vytvořte nový dokument XHTML s názvem ContosoTopic4.htm a zadejte značku nadpisu (níže).

```html
<html>
<head>
<title>Contoso Topic 4</title>
</head>

<body>

</body>
</html>

```

Dále přidejte data, která definují, jak má být téma prezentováno (samoznačené nebo ne), jak odkazovat na toto téma pro F1, kde toto téma existuje v rámci TOC, jeho ID (pro odkaz odkaz na jiná témata) atd. Úplný seznam podporovaných metadat naleznete v tabulce Metadata obsahu níže.

- V takovém případě použijeme vlastní balíček značky, což je varianta balíčku brandingu prohlížeče nápovědy sady Visual Studio.

- Přidejte meta název a hodnotu F1 ("Microsoft.Help.F1" content=" ContosoTopic4"), která bude odpovídat zadané hodnotě F1 v vaku vlastností IDE. (Další informace naleznete v části Podpora F1.) Toto je hodnota, která je spárována s Volání F1 z v rámci ide zobrazit toto téma při f1 je vybrán v ide.

- Přidejte ID tématu. Toto je řetězec, který se používá v jiných tématech odkaz na toto téma. Je to ID prohlížeče nápovědy pro toto téma.

- Pro toc přidejte nadřazený uzel tohoto tématu a definujte, kde se tento uzel toč nezobrazí.

- Pro toc přidejte pořadí uzlů tohoto tématu. Pokud nadřazený uzel má `n` počet podřízených uzlů, definujte v pořadí podřízených uzlů umístění tohoto tématu. Například toto téma je číslo 4 ze 4 podřízených témat.

Příklad části metadat:

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

**Tělo tématu**

Text (bez záhlaví a zápatí) tématu bude obsahovat odkazy na stránky, oddíl poznámek, sbalitelnou oblast, fragment kódu a část textu specifického pro jazyk.  Informace o těchto oblastech prezentovaného tématu naleznete v části značky.

1. Přidání značky názvu tématu:`<div class="title">Contoso Topic 4</div>`

2. Přidejte oddíl s poznámkami:`<div class="alert"> add your table tag and text </div>`

3. Přidejte sbalitelnou oblast:`<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> add text  </CollapsibleArea>`

4. Přidání fragmentu kódu:`<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > a block of code </CodeSnippet>`

5. Přidejte text specifický `<LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />` pro `devLangnu=` jazyk kódu: Poznámka, která umožňuje zadat další jazyky. Například `devLangnu="Fortran"` zobrazí Fortran, když fragment kódu DisplayLanguage = Fortran

6. Přidat odkazy na stránky:`<a href="ms-xhelp:///?Id=ContosoTopic1">Main Topic</a>`

> [!NOTE]
> Poznámka: pro nepodporované nové "Display Language" (například F #, Cobol, Fortran) zbarvení kódu ve fragmentu kódu bude monochromatické.

**Příklad tématu prohlížeče nápovědy** Kód ukazuje, jak definovat metadata, fragment kódu, sbalititelné oblasti a text specifický pro jazyk.

```html
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
<li class="tocline1"><a href="#seealso" target="_self">See Also</a></li>
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
        <a href="ms-xhelp:///?Id=ContosoTopic1">Main Topic</a>
    </div>
 </div>
</div>
</div>
</body>
</html>
```

**Podpora F1**

V sadě Visual Studio vyberete F1 generuje hodnoty zadané z umístění kurzoru v rámci ide a naplní "vlastnost tašku" s zadanými hodnotami (na základě umístění kurzoru. Když je kurzor nad funkcí x, funkce x je aktivní/aktivní a naplní tašku vlastností hodnotami.  Když je vybrána hodnota F1, je vak vlastností naplněn a kód Visual Studio F1 hledá, zda je výchozí zdroj nápovědy zákazníků místní nebo online (online je výchozí), pak vytvoří příslušný řetězec založený na nastavení uživatelů (online je výchozí) - spuštění prostředí (viz Průvodce správcem nápovědy pro parametry spuštění exe) s parametry pro místní prohlížeč nápovědy + klíčové slovo (klíčová slova) z vaku vlastností, pokud je výchozí místní nápověda nebo adresa URL msdn s klíčovým slovem v seznamu parametrů.

Pokud jsou vráceny tři řetězce pro F1, označované jako řetězec s více hodnotami, vezměte první termín, vyhledejte přístupový server a pokud je nalezen, jsme hotovi; Pokud ne, přejděte na další řetězec.  Na pořádku záleží. Prezentace klíčových slov s více hodnotami by měla být nejdelší řetězec nejkratší řetězec.  Chcete-li to ověřit v případě klíčových slov s více hodnotami, podívejte se na řetězec url online F1, který bude obsahovat zvolené klíčové slovo.

V sadě Visual Studio 2012 jsme záměrně vytvořili větší propast mezi online a offline, takže pokud bylo nastavení uživatele pro online, jednoduše jsme předali požadavek F1 přímo naší online dotazovací službě na MSDN, nikoli směrování přes agenta knihovny nápovědy, který jsme měli v sadě Visual Studio 2010. Pak se spoléháme na stav "obsah dodavatele nainstalován = true" k určení, zda chcete udělat něco jiného v tomto kontextu. Pokud true, pak provádíme tuto logiku analýzy a směrování v závislosti na tom, co chcete podporovat pro své zákazníky. Pokud false, pak jsme prostě jít do MSDN. Pokud je nastavení uživatele místní, pak všechna volání přejít na místní modul nápovědy.

Vývojový diagram F1:

![Tok F1](../../extensibility/internals/media/f1flow.png "F1flow")

Pokud je výchozí zdroj obsahu nápovědy nastaven na online (Spuštění v prohlížeči):

- Funkce Visual Studio Partner (VSP) vysílají hodnotu do vaku vlastností F1 (vlastnost taška prefix.keyword.keyword a online URL pro předponu nalezenou v registru): F1 odešle parametry VSP URL+ do prohlížeče.

- Funkce sady Visual Studio (editor jazyka, položky nabídky specifické pro Visual Studio atd.): F1 odešle do prohlížeče adresu URL sady Visual Studio.

Pokud je výchozí zdroj obsahu nápovědy pro prohlížeč nápovědy nastaven na místní nápovědu (Spustit v prohlížeči nápovědy):

- Funkce VSP, kde shoda klíčových slov mezi f1 tašku vlastností a místní index úložiště (to znamená, že vlastnost taška prefix.keyword .

- Funkce sady Visual Studio (žádná možnost pro VSP přepsat vlastnost tašku vyzařované z funkcí sady Visual Studio): F1 vykreslí téma sady Visual Studio v prohlížeči nápovědy.

Nastavte následující hodnoty registru, chcete-li povolit f1 záložní obsah nápovědy dodavatele. F1 Záložní znamená, že prohlížeč nápovědy je nastaven tak, aby hledal obsah nápovědy F1 online a obsah dodavatele je nainstalován místně na pevný disk uživatele. Prohlížeč nápovědy by měl vyhledat místní nápovědu k obsahu, i když výchozí nastavení je pro nápovědu online.

1. Nastavte hodnotu **VendorContent** pod klíčem registru Nápověda 2.3:

   - Pro 32bitové operační systémy:

        HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Katalogy\VisualStudio15

        "VendorContent"=dword:00000001

   - Pro 64bitové operační systémy:

        HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Katalogy\VisualStudio15

        "VendorContent"=dword:00000001

2. Zaregistrujte obor názvů partnera pod klíčem registru nápovědy 2.3:

   - Pro 32bitové operační systémy:

      HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Obor<em> \\ názvů<partnera\></em>

      "umístění"="offline"

   - Pro 64bitové operační systémy:

      HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Obor<em> \\ názvů<partnera\></em>

      "umístění"="offline"

**Analýza základního nativního oboru názvů**

Chcete-li zapnout analýzu základního nativního oboru názvů, přidejte v registru nový DWORD pod názvem: BaseNativeNamespaces a nastavte jeho hodnotu na hodnotu 1 (pod klíčem katalogu, který chtějí podporovat).  Chcete-li například použít katalog sady Visual Studio, můžete do cesty přidat klíč:

HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Katalogy\VisualStudio15

Při výskytu klíčového slova F1 ve formátu HEADER/METHOD bude analyzován znak '/', což vede k následujícímu konstruktu:

- HEADER: bude obor názvů, který lze použít k registraci v registru

- METODA: to se stane klíčovým slovem, které projde.

Například dané vlastní knihovny s názvem CustomLibrary a metoda s názvem MyTestMethod, když `CustomLibrary/MyTestMethod`F1 požadavek přijde v něm bude formátován jako .

Uživatel pak můžete zaregistrovat CustomLibrary jako obor názvů pod podregistr partneři a poskytnout libovolné umístění klíč, který si přejí a klíčové slovo předané do dotazu bude MyTestMethod.

**Povolení nástroje pro ladění nápovědy v ide**

Přidejte následující klíč a hodnotu registru:

::: moniker range="vs-2017"

**HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Dynamická nápověda**

::: moniker-end

::: moniker range=">=vs-2019"

**HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\16.0\Dynamická nápověda**

::: moniker-end

Hodnota: Zobrazení ladicího výstupu v maloobchodních datech: ANO

V prostředí IDE vyberte v položce nabídky Nápověda **ladit kontext nápovědy**.

**Metadata obsahu**

V následující tabulce je libovolný řetězec, který se zobrazí mezi závorkami, zástupným symbolem, který musí být nahrazen rozpoznanou hodnotou. Například v \<meta name="Microsoft.Help.Locale" content="[kód jazyka]" />, "[kód jazyka]" musí být nahrazen hodnotou jako "en-us".

| Vlastnost (reprezentace HTML) | Popis |
| - | - |
| \<meta name="Microsoft.Help.Locale" content="[language-code]" /> | Nastaví národní prostředí pro toto téma. Pokud je tato značka použita v tématu, musí být použita pouze jednou a musí být vložena nad všechny ostatní značky nápovědy společnosti Microsoft. Pokud tato značka není použita, základní text tématu je indexován pomocí modulu dělení na slova, který je spojen s národním prostředím produktu, pokud je zadán; jinak en-us dělení na slova se používá. Tato značka odpovídá isoc RFC 4646. Chcete-li zajistit, aby nápověda microsoft funguje správně, použijte tuto vlastnost namísto obecného atributu Language. |
| \<meta name="Microsoft.Help.TopicLocale" content="[language-code]" /> | Nastaví národní prostředí pro toto téma, pokud jsou použity i jiné národní prostředí. Pokud je tato značka použita v tématu, musí být použita pouze jednou. Tuto značku použijte, pokud katalog obsahuje obsah ve více než jednom jazyce. Více témat v katalogu může mít stejné ID, ale každý musí zadat jedinečný TopicLocale. Téma, které určuje TopicLocale, který odpovídá národní prostředí katalogu je téma, které je zobrazeno v obsahu. Všechny jazykové verze tématu jsou však zobrazeny ve výsledcích hledání. |
| \<název>[Název]\</title> | Určuje název tohoto tématu. Tato značka je povinná a musí být použita pouze jednou v tématu. Pokud tělo tématu neobsahuje název \<div> části, zobrazí se tento nadpis v tématu a v obsahu. |
| \<meta name=" Microsoft.Help.Keywords" content="[aKeywordPhrase]"/> | Určuje text odkazu, který je zobrazen v podokně rejstříku prohlížeče nápovědy. Po kliknutí na odkaz se zobrazí téma. Můžete zadat více klíčových slov indexu pro téma, nebo můžete tuto značku vynechat, pokud nechcete, aby se v indexu zobrazovaly odkazy na toto téma. Klíčová slova "K" z dřívějších verzí nápovědy lze převést na tuto vlastnost. |
| \<meta name="Microsoft.Help.Id" content="[TopicID]"/> | Nastaví identifikátor pro toto téma. Tato značka je povinná a musí být použita pouze jednou v tématu. ID musí být jedinečné mezi tématy v katalogu, které mají stejné nastavení národního prostředí. V jiném tématu můžete vytvořit odkaz na toto téma pomocí tohoto ID. |
| \<meta name="Microsoft.Help.F1" content="[System.Windows.Controls.Primitives.IRecyclingItemContainerGenerator]"/> | Určuje klíčové slovo F1 pro toto téma. Můžete zadat více klíčových slov F1 pro téma, nebo můžete tuto značku vynechat, pokud nechcete, aby se toto téma zobrazilo, když uživatel aplikace stiskl klávesu F1. Pro dané téma je obvykle zadáno pouze jedno klíčové slovo F1. Klíčová slova "F" z dřívějších verzí nápovědy lze převést na tuto vlastnost. |
| \<meta name="Description" content="[popis tématu]" /> | Obsahuje krátký souhrn obsahu v tomto tématu. Pokud je tato značka použita v tématu, musí být použita pouze jednou. K této vlastnosti přistupuje přímo knihovna dotazů; není uložen v souboru indexu. |
| meta name="Microsoft.Help.TocParent" content="[parent_Id]"/> | Určuje nadřazené téma tohoto tématu v obsahu. Tato značka je povinná a musí být použita pouze jednou v tématu. Hodnota je Microsoft.Help.Id nadřazeného objektu. Téma může mít pouze jedno umístění v obsahu. "-1" je považován za ID tématu pro kořen toc. V [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]programu je tato stránka domovskou stránkou prohlížeče nápovědy. To je stejný důvod, proč jsme konkrétně přidat TocParent = -1 na některá témata, aby zajistily, že se zobrazí na nejvyšší úrovni. Domovská stránka Prohlížeče nápovědy je systémová stránka, která není tedy nahraditelná. Pokud se vsp pokusí přidat stránku s ID -1, může být přidána do sady obsahu, ale Prohlížeč nápovědy bude vždy používat systémovou stránku - Domovní stránka prohlížeče nápovědy |
| \<meta name="Microsoft.Help.TocOrder" content="[pozitivní celé číslo]"/> | Určuje, kde se v obsahu toto téma zobrazí vzhledem k tématům jeho vrstevníků. Tato značka je povinná a musí být použita pouze jednou v tématu. Hodnota je celé číslo. Téma, které určuje celé číslo s nižší hodnotou, se zobrazí nad tématem, které určuje celé číslo s vyšší hodnotou. |
| \<meta name="Microsoft.Help.Product" content="[kód produktu]"/> | Určuje produkt, který toto téma popisuje. Pokud je tato značka použita v tématu, musí být použita pouze jednou. Tyto informace mohou být také poskytnuty jako parametr, který je předán do indexeru nápovědy. |
| \<meta name="Microsoft.Help.ProductVersion" content="[číslo verze]"/> | Určuje verzi produktu, kterou toto téma popisuje. Pokud je tato značka použita v tématu, musí být použita pouze jednou. Tyto informace mohou být také poskytnuty jako parametr, který je předán do indexeru nápovědy. |
| \<meta name="Microsoft.Help.Category" content="[string]"/> | Používá se produkty k identifikaci pododdílů obsahu. Můžete identifikovat více pododdílů pro téma, nebo můžete tuto značku vynechat, pokud nechcete, aby odkazy identifikovaly žádné podsekce. Tato značka se používá k uložení atributů pro TargetOS a TargetFrameworkMoniker při převodu tématu z dřívější verze nápovědy. Formát obsahu je AttributeName:AttributeValue. |
| \<meta name="Microsoft.Help.TopicVersion content="[číslo verze tématu]"/> | Určuje tuto verzi tématu, pokud v katalogu existuje více verzí. Vzhledem k tomu, že Microsoft.Help.Id není zaručeno, že je jedinečný, tato značka je vyžadována, pokud v katalogu existuje více než jedna verze tématu, například pokud katalog obsahuje téma pro rozhraní .NET Framework 3.5 a téma pro rozhraní .NET Framework 4 a obě mají stejné Microsoft.Help.Id. |
| \<meta name="SelfBranded" content="[TRUE nebo FALSE]"/> | Určuje, zda toto téma používá balíček start-up branding správce knihovny nápovědy nebo balíček značky, který je specifický pro dané téma. Tato značka musí být PRAVDA nebo NEPRAVDA. Pokud je TRUE, pak branding balíček pro přidružené téma přepíše branding balíček, který je nastaven při spuštění Správce knihovny nápovědy tak, aby téma je vykreslen tak, jak bylo zamýšleno i v případě, že se liší od vykreslování jiného obsahu. Pokud je false, aktuální téma je vykreslen podle branding balíček, který je nastaven při spuštění Správce knihovny nápovědy. Ve výchozím nastavení správce knihovny nápovědy předpokládá, že vlastní branding je nepravdivý, pokud není proměnná SelfBranded deklarována jako PRAVDA; proto není třeba deklarovat \<meta name="SelfBranded" content="FALSE"/>. |

## <a name="create-a-branding-package"></a>Vytvoření balíčku značky

Verze sady Visual Studio zahrnuje řadu různých produktů sady Visual Studio, včetně izolovaných a integrovaných prostředí pro partnery sady Visual Studio.  Každý z těchto produktů vyžaduje určitý stupeň podpory obsahu nápovědy založené na tématech, která je pro produkt jedinečná.  Například visual studio témata musí mít konzistentní prezentaci značky, vzhledem k tomu, SQL Studio, který zabalí ISO Shell, vyžaduje vlastní jedinečný obsah nápovědy značky pro každé téma.  Integrovaný partner prostředí může chtít, aby jejich témata nápovědy byla v rámci obsahu nápovědy k nadřazenému produktu Visual Studio při zachování vlastní značky tématu.

Balíčky značek jsou nainstalovány produktem obsahujícím prohlížeč nápovědy.  Pro produkty sady Visual Studio:

- Záložní balíček značky\<(Branding_ národní prostředí>.mshc) je nainstalován v kořenovém adresáři aplikace Prohlížeč nápovědy 2.3 (například C:\Program Files (x86)\Microsoft Help Viewer\v2.3) pomocí jazykové sady Prohlížeč nápovědy.  Používá se v případech, kdy není nainstalován balíček značky produktu (nebyl nainstalován žádný obsah) nebo kde je poškozen nainstalovaný balíček značky.  Prvky sady Visual Studio (logo a zpětná vazba) jsou ignorovány při použití balíčku root root značky.

- Při instalaci obsahu sady Visual Studio ze služby balíčku obsahu je nainstalován také balíček značky (pro první scénář instalace obsahu).  Pokud dojde k aktualizaci balíčku značky, aktualizace se nainstaluje při další aktualizaci obsahu nebo další akci instalace balíčku.

Prohlížeč nápovědy společnosti Microsoft podporuje branding témat na základě metadat tématu.

- Kde metadata tématu definují vlastní značkové = true, vykreslujte téma tak, jak je, nedělat nic (pokud jde o branding).

- Kde metadata tématu definuje vlastní značkové = false, použijte balíček značky přidružený k hodnotě metadat TopicVendor.

- Kde metadata tématu definují název="Microsoft.Help.TopicVendor" content=\< název balíčku značky v> dodavatele MSHA, použijte balíček značky definovaný v hodnotě obsahu.

- V rámci katalogu Sady Visual Studio je prioritní aplikace branding balíčky.  Nejprve visual studio výchozí značky je použita a pak, pokud je definována v metadatech tématu a podporuje s přidruženým branding balíček (jak je definováno v instalaci msha), dodavatelem definované značky se použije jako přepsání.

Prvky značky obvykle spadají do tří hlavních kategorií:

- Prvky záhlaví (například odkaz na zpětnou vazbu, text podmíněného vyloučení odpovědnosti, logo)

- Chování obsahu (příklady zahrnují rozbalení/sbalit prvky textu ovládacího prvku a prvky fragmentu kódu)

- Zápatí prvky (příklad Copyright)

Položky považované za značkové prvky zahrnují (podrobně popsané v této specifikaci):

- Logo katalogu/produktu (příklad Visual Studio)

- Odkaz na zpětnou vazbu a prvky e-mailu

- Text zřeknutí se odpovědnosti

- Text autorských práv

Mezi podpůrné soubory v balíčku brandingu prohlížeče nápovědy sady Visual Studio patří:

- Grafika (loga, ikony atd.)

- Branding.js - skriptové soubory podporující chování obsahu

- Branding.xml - řetězce, které se konzistentně používají v celém obsahu katalogu.  Poznámka: pro textové prvky lokalizace sady Visual Studio\<v souboru branding.xml zahrňte _locID=" jedinečnou hodnotu>"

- Branding.css - definice stylů pro konzistenci prezentace

- Printing.css - definice stylů pro konzistentní tiskovou prezentaci

Jak bylo uvedeno výše, Branding balíčky jsou spojeny s tématem:

- Když selfBranded = false je definovánv metadatech, téma zdědí katalog značky balíček

- Nebo když SelfBranded = false a tam je jedinečný branding balíček definovaný v MSHA a k dispozici při instalaci obsahu

Pro virtuální ip adresy implementující vlastní balíčky značky (obsah VSP, SelfBranded=True) je jedním ze způsobů, jak pokračovat, začít s balíčkem záložní značky (nainstalovaným v prohlížeči nápovědy) a podle potřeby změnit název souboru.  Národní\<prostředí Branding_>.mshc soubor je soubor zip s příponou souboru změněn na .mshc, takže jednoduše změnit příponu z .mshc na .zip a extrahovat obsah.  Viz níže pro prvky balení značky a upravit podle potřeby (například změnit logo na logo VSP a odkaz na logo v souboru Branding.xml, aktualizovat Branding.xml na specifika VSP atd.).

Po dokončení všech úprav vytvořte soubor zip obsahující požadované prvky značky a změňte příponu na .mshc.

Chcete-li přidružit vlastní balíček značky, vytvořte msha, který obsahuje odkaz na soubor mshc značky spolu s obsahem mshc (obsahující témata).  Jak vytvořit základní msha, najdete níže v části "MSHA".

Soubor Branding.xml obsahuje seznam prvků používaných k onzistentně \<vykreslování určitých položek v tématu, pokud téma obsahuje meta name="Microsoft.Help.SelfBranded" content="false"/>.  Seznam prvků v souboru Branding.xml sady Visual Studio je uveden níže.  Tento seznam je určen k použití jako šablona pro uživatele ISO Shell, kde upravují tyto prvky (například logo, zpětnou vazbu a autorská práva) tak, aby vyhovovaly jejich vlastním potřebám značky produktu.

Poznámka: proměnné označené {n} mají závislosti kódu - odebrání nebo změna těchto hodnot způsobí chyby a případně selhání aplikace. Identifikátory lokalizace (příklad _locID="codesnippet.n") jsou zahrnuty v balíčku značky Visual Studio.

**Branding.xml**

| | |
| - | - |
| Funkce: | **Sbalitelná oblast** |
| Použít: | Rozbalení sbalí text ovládacího prvku obsahu |
| **Element** | **Hodnotu** |
| Rozbalittext | Rozbalit |
| Sbalit text | Sbalit |
| Funkce: | **CodeSnippet** |
| Použít: | Kód ový prvek textu.  Poznámka: Obsah fragmentu kódu s mezerou "Non-Breaking" bude změněn na místo. |
| **Element** | **Hodnotu** |
| CopyToClipboard | Kopírovat do schránky |
| ViewColorizedText | Zobrazení kolorované |
| CombinedVBTabDisplayLanguage | Visual Basic (ukázka) |
| VBDeklarace | Deklarace |
| Použití VB | Využití |
| Funkce: | **Zpětná vazba, zápatí a logo** |
| Použít: | Poskytněte zákazníkům zpětnou vazbu k aktuálnímu tématu prostřednictvím e-mailu.  Text autorských práv pro obsah.  Definice loga. |
| **Element** | **Hodnota (Tyto řetězce lze upravit tak, aby vyhovovaly potřebám uživatele obsahu.)** |
| Copyright | © 2013 Microsoft Corporation. Všechna práva vyhrazena. |
| SendFeedback | \<a{0}href=" {1} "\<>Odeslat zpětnou vazbu /a> na toto téma společnosti Microsoft. |
| Odkaz feedback | |
| LogoTitle | [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] |
| Název souboru Loga | vs_logo_bk.gif |
| LogoFileNameHC | vs_logo_wh.gif |
| Funkce: | **Disclaimer** |
| Použít: | Sada zřeknutí se odpovědnosti pro strojově přeložený obsah. |
| **Element** | **Hodnotu** |
| MT_Editable | Tento článek byl strojově přeložen. Pokud máte připojení k Internetu, vyberte možnost "Zobrazit toto téma online", chcete-li zobrazit tuto stránku v upravitelném režimu s původním anglickým obsahem současně. |
| MT_NonEditable | Tento článek byl strojově přeložen. Pokud máte připojení k Internetu, vyberte možnost "Zobrazit toto téma online", chcete-li zobrazit tuto stránku v upravitelném režimu s původním anglickým obsahem současně. |
| MT_QualityEditable | Tento článek byl přeložen ručně. Pokud máte připojení k Internetu, vyberte možnost "Zobrazit toto téma online", chcete-li zobrazit tuto stránku v upravitelném režimu s původním anglickým obsahem současně. |
| MT_QualityNonEditable | Tento článek byl přeložen ručně. Pokud máte připojení k Internetu, vyberte možnost "Zobrazit toto téma online", chcete-li zobrazit tuto stránku v upravitelném režimu s původním anglickým obsahem současně. |
| MT_BetaContents | Tento článek byl strojově přeložen pro předběžnou verzi. Pokud máte připojení k Internetu, vyberte možnost "Zobrazit toto téma online", chcete-li zobrazit tuto stránku v upravitelném režimu s původním anglickým obsahem současně. |
| MT_BetaRecycledContents | Tento článek byl ručně přeložen pro předběžnou verzi. Pokud máte připojení k Internetu, vyberte možnost "Zobrazit toto téma online", chcete-li zobrazit tuto stránku v upravitelném režimu s původním anglickým obsahem současně. |
| Funkce: | **Propojitt tabulku** |
| Použít: | Podpora online odkazů na témata |
| **Element** | **Hodnotu** |
| LinkTableTitle | Propojit tabulku |
| TopicEnuLinkText | Zobrazit anglickou\<verzi /a> tohoto tématu, které je k dispozici v počítači. |
| TémaOnlineLinkText | Zobrazit \<toto téma{0}a {1} href=" ">online\</a> |
| Onlinetext | Online |
| Funkce: | **Ovládání video zvuku** |
| Použít: | Zobrazení prvků a textu pro videoobsah |
| **Element** | **Hodnotu** |
| MultiMediaNotSupported | Pro podporu {0} obsahu musí být nainstalována aplikace Internet Explorer 9 nebo vyšší. |
| Videotext | zobrazení videa |
| AudioText | streamování zvuku |
| OnlineVideoLinkText | \<p>Chcete-li zobrazit video {0} \<spojené s{1}tímto {2}\<tématem, klikněte na href=" ">zde /a>. \</p> |
| OnlineAudioLinkText | \<p>Chcete-li poslouchat zvuk spojený {0} \<s tímto tématem, klikněte na href="{1}">{2}zde\</a>. \</p> |
| Funkce: | **Ovládací prvek Obsah není nainstalován** |
| Použít: | Textové prvky (řetězce) používané pro vykreslování souboru contentnotinstalled.htm |
| **Element** | **Hodnotu** |
| ContentNotInstalledTitle | V počítači nebyl nalezen žádný obsah. |
| ContentNotInstalledDownloadContentText Content | \<p>Chcete-li stáhnout \<obsah do{0} {1} počítače,>\<href na kartu Manage /a>. \</p> |
| ContentNotInstalledText | \<p>V počítači není nainstalován žádný obsah. Instalace obsahu místní nápovědy u svého správce. \</p> |
| Funkce: | **Ovládací prvek Téma nebylo nalezeno.** |
| Použít: | Textové prvky (řetězce) používané pro vykreslování souboru topicnotfound.htm |
| **Element** | **Hodnotu** |
| TopicNotFoundtitle | V počítači nelze najít požadované téma. |
| TopicNotFoundViewOnlineText | \<p>Požadované téma nebylo v počítači nalezeno, ale \<můžete si vytvořit href="{0}" {1}>zobrazit téma online\</a>. \</p> |
| TopicnotFoundDownloadContentText | \<p>Pro odkazy na podobná témata \<naleznete v{0} {1} navigačním podokně\<nebo na href=">kliknutím na kartu Manage /a> a stáhněte obsah do počítače. \</p> |
| TopicNotFoundText | \<p>Požadované téma nebylo v počítači nalezeno. \</p> |
| Funkce: | **Poškozený ovládací prvek tématu** |
| Použít: | Textové prvky (řetězce) používané pro vykreslování topiccorrupted.htm |
| **Element** | **Hodnotu** |
| TopicCorruptedTitle | Požadované téma nelze zobrazit. |
| TopicCorruptedViewOnlineText | \<p>Prohlížeč nápovědy nemůže zobrazit požadované téma. Může být chyba v obsahu tématu nebo základní závislost systému. \</p> |
| Funkce: | **Ovládací prvek Domovské stránky** |
| Použít: | Text podporující zobrazení obsahu uzlu nejvyšší úrovně prohlížeče nápovědy. |
| **Element** | **Hodnotu** |
| Domovská stránkaNadpis | Domovská stránka prohlížeče nápovědy |
| ÚvodÚvod | \<p>Vítejte v prohlížeči nápovědy společnosti Microsoft, který je základním zdrojem informací pro každého, kdo používá nástroje, produkty, technologie a služby společnosti Microsoft. Prohlížeč nápovědy umožňuje přístup k informacím o postupech a referencích, ukázkovému kódu, technickým článkům a dalším. Chcete-li najít potřebný obsah, procházejte obsah, použijte fulltextové vyhledávání nebo procházejte obsah pomocí indexu klíčových slov. \</p> |
| Domovská stránkaContentInstallText | \<p \<>br />\<Použijte{0}href=" " {1}>Spravovat obsah\</a kartu> k provedení následujícího:\<ul>\<li>Přidejte obsah do počítače. \</li \<>li>Zkontrolujte aktualizace místního obsahu. \</li \<>li>Odebrat obsah z počítače. \</li \<>/ul>\</p> |
| HomePageInstalledKnihy | Nainstalované knihy |
| Domovská stránkaNoknihynainstalován | V počítači nebyl nalezen žádný obsah. |
| Nastavení nápovědy domovské stránky | Nastavení obsahu nápovědy |
| HomePageHelpSettingsText | \<p>Aktuální nastavení je místní nápověda. Prohlížeč nápovědy zobrazuje obsah, který jste nainstalovali v počítači. \<br />Chcete-li změnit zdroj obsahu nápovědy, \<zvolte na{0}panelu nabídek sady\<Visual Studio styl span=" "nápověda >, nastavit předvolbu nápovědy /span>. \<br />\</p> |
| Mb | MB |

**branding.js**

Soubor branding.js obsahuje JavaScript používaný prvky značky Visual Studio Help Viewer.  Níže je uveden seznam prvků značky a podpůrná funkce JavaScriptu.  Všechny řetězce, které mají být lokalizovány pro tento soubor, jsou definovány v části "Lokalizovatelné řetězce" v horní části tohoto souboru.  Soubor ICL byl vytvořen pro loc řetězce v rámci souboru branding.js.

||||
|-|-|-|
|**Funkce brandingu**|**Funkce JavaScriptu**|**Popis**|
|Var...||Definování proměnných|
|Získání jazyka uživatelského kódu|setUserPreferenceLang|mapuje index # na kódový jazyk|
|Nastavit a získat hodnoty souborů cookie|getCookie, setCookie||
|Zděděný člen|changeMembersLabel|Rozbalit/sbalit zděděný člen|
|Když selfbranded=False|Onload|Přečtěte si řetězec dotazu a zkontrolujte, zda se jedná o požadavek na tisk.  Nastavte všechny kódy, aby se zaměřily na kartu upřednostňovanou uživatele.  Pokud je požadavek na tisk, nastavte isPrinterFriendly na true. Zkontrolujte režim vysokého kontrastu.|
|Fragment kódu|addSpecificTextLanguageTagSet||
||getIndexFromDevLang||
||ChangeTab||
||setCodesnippetLang||
||setCurrentLang||
||CopyToClipboard||
|Sbalitelná oblast|addToCollapsibleControlSet|zapsat všechny sbalitelný objekt ovládacího prvku do seznamu.|
||CA_Click|na základě stavu sbalitelné oblasti, definuje, který obraz a text se má prezentovat|
|Podpora kontrastu pro logo|isBlackBackground()|Volána k určení, zda je pozadí černé.  Přesné pouze v režimu vysokého kontrastu.|
||isHighContrast()|použití barevného rozpětí pro detekci režimu vysokého kontrastu|
||onHighContrast (černá)|Nazývá se při detekci vysokého kontrastu|
|Funkce LST|||
||addToLanSpecTextIdSet(id)||
||updateLST(currentLang)||
||getDevLangFromCodeSnippet(lang)||
|Funkce MultiMedia|titulek (začátek, konec, text, styl)||
||findAllMediaControls(normalizedId)||
||getActivePlayer(normalizedId)||
||captionsOnOff(id)||
||toSeconds(t)||
||getAllComments(uzel)||
||styleRectify(styleName, styleValue)||
||showCC(id)||
||titulky (id)||

**HTM SOUBORY**

Balíček značky obsahuje sadu souborů HTM, které podporují scénáře pro sdělování klíčových informací uživatelům obsahu nápovědy, například domovskou stránku, která obsahuje oddíl popisující, které sady obsahu jsou nainstalovány, a stránky, které uživateli říkají, že témata nelze nalézt v místní sadě témat. Tyto HTM soubory lze upravit na produkt.  Dodavatelé ISO Shell jsou schopni přijmout výchozí balíček značky a změnit chování a obsah těchto stránek tak, aby vyhovovaly jejich potřebám.  Tyto soubory odkazují na jejich příslušné značky balíček, aby značky značky získat odpovídající obsah ze souboru branding.xml.

||||
|-|-|-|
|**Soubor**|**Použití**|**Zobrazený zdroj obsahu**|
|domovská stránka.htm|Toto je stránka, která zobrazuje aktuálně nainstalovaný obsah a všechny ostatní zprávy vhodné k prezentaci uživateli o jejich obsahu.  Tento soubor má další meta datový atribut "Microsoft.Help.Id" content="-1", který umístí tento obsah na začátek místního obsahu OBSAHU.||
||<META_HOME_PAGE_TITLE_ADD />|Branding.xml, \<značka HomePageTitle>|
||<HOME_PAGE_INTRODUCTION_SECTION_ADD />|Branding.xml, \<značka HomePageÚvod>|
||<HOME_PAGE_CONTENT_INSTALL_SECTION_ADD />|Branding.xml, \<značka HomePageContentInstallText>|
||<HOME_PAGE_BOOKS_INSTALLED_SECTION_ADD />|Nadpis značky Branding.xml tag\<HomePageInstalledBooks>, \<data generovaná z aplikace, HomePageNoBooksInstalled>, když nejsou nainstalovány žádné knihy.|
||<HOME_PAGE_SETTINGS_SECTION_ADD />|Nadpis Značky Branding.xml tag \<HomePageHelpSettings>, text \<oddílu HomePageHelpSettingsText>.|
|topiccorrupted.htm|Pokud téma existuje v místní sadě, ale z nějakého důvodu nelze zobrazit (poškozený obsah).||
||<META_TOPIC_CORRUPTED_TITLE_ADD />|Branding.xml, \<tag TopicCorruptedTitle>|
||<TOPIC_CORRUPTED_SECTION_ADD />|Branding.xml, \<tag TopicCorruptedViewOnlineText>|
|topicnotfound.htm|Pokud není téma nalezeno v místní sadě obsahu, ani není k dispozici online||
||<META_TOPIC_NOT_FOUND_TITLE_ADD />|Branding.xml, \<tag TopicNotFoundTitle>|
||<META_TOPIC_NOT_FOUND_ID_ADD />|Branding.xml, \<tag TopicNotFoundViewOnlineText \<> + TopicNotFoundDownloadContentText>|
||<TOPIC_NOT_FOUND_SECTION_ADD />|Branding.xml, \<tag TopicNotFoundText>|
|contentnotinstalled.htm|Pokud pro produkt není nainstalován žádný místní obsah.||
||<META_CONTENT_NOT_INSTALLED_TITLE_ADD />|Branding.xml, \<značka ContentNotInstalledTitle>|
||<META_CONTENT_NOT_INSTALLED_ID_ADD />|Branding.xml, \<označit ContentNotInstalledDownloadContentText>|
||<CONTENT_NOT_INSTALLED_SECTION_ADD />|Branding.xml, \<tag ContentNotInstalledText>|

**Soubory CSS**

Balíček brandingu prohlížeče nápovědy sady Visual Studio obsahuje dva soubory css, které podporují konzistentní prezentaci obsahu nápovědy sady Visual Studio:

- Branding.css - obsahuje css prvky pro vykreslování, kde SelfBranded = false

- Printer.css - obsahuje css prvky pro vykreslování, kde SelfBranded=false

Branding.css soubory obsahují definice pro prezentaci tématu sady Visual Studio (upozornění\<je, že branding.css obsažené v Branding_ národní prostředí>.mshc ze služby balíčku může změnit).

**Grafické soubory**

Obsah sady Visual Studio zobrazuje logo sady Visual Studio a další grafiku.  Úplný seznam grafických souborů v balíčku značky Visual Studio Help Viewer je uveden níže.

||||
|-|-|-|
|**Soubor**|**Použití**|**Příklady**|
|clear.gif|Slouží k vykreslení sbalitelné oblasti||
|footer_slice.gif|Prezentace zápatí||
|info_icon.gif|Používá se při zobrazování informací|Disclaimer|
|online_icon.gif|Tato ikona má být spojena s online odkazy||
|tabLeftBD.gif|Slouží k vykreslení kontejneru fragmentu kódu.||
|tabRightBD.gif|Slouží k vykreslení kontejneru fragmentu kódu.||
|vs_logo_bk.gif|Používá se pro běžné odkazy na logo \<kontrastu, jak je definováno ve značce Branding.xml logoFileName>.  U produktů sady Visual Studio je název loga vs_logo_bk.gif.||
|vs_logo_wh.gif|Používá se pro normální vysoké odkazy na \<logo, jak je definováno ve značce Branding.xml LogoFileNameHC>.  U produktů sady Visual Studio je název loga vs_logo_wh.gif.||
|ccOff.png|Grafika titulků||
|ccOn.png|Grafika titulků||
|ImageSprite.png|Slouží k vykreslení sbalitelné oblasti|rozbalená nebo sbalit grafika|

## <a name="deploy-a-set-of-topics"></a>Nasazení sady témat

Toto je jednoduchý a rychlý kurz pro vytvoření sady nasazení obsahu prohlížeče nápovědy skládající se ze souboru MSHA a sady cabs nebo MSHCs obsahující témata. MSHA je soubor XML, který popisuje sadu cabs nebo MSHC soubory. Prohlížeč nápovědy může číst msha získat seznam obsahu (. CAB nebo . MSHC) k dispozici pro místní instalaci.

Toto je pouze základní nátěr popisující velmi základní schéma XML pro prohlížeč nápovědy MSHA.  Pod tímto stručným přehledem a ukázkou souboru HelpContentSetup.msha je příklad implementace.

Název MSHA, pro účely tohoto základního nátěru, je HelpContentSetup.msha (název souboru může být cokoliv, s příponou . MSHA). HelpContentSetup.msha (příklad níže) by měl obsahovat seznam cabs nebo MSHC k dispozici.  Typ souboru musí být konzistentní v rámci MSHA (nepodporuje kombinaci MSHA a CAB typy souborů). Pro každý CAB nebo MSHC \<by měl být div class ="package">... \</div> (viz příklad níže).

Poznámka: V příkladu implementace níže jsme zahrnuli balíček značky. To je důležité zahrnout, aby bylo možné získat potřebné prvky vykreslování obsahu sady Visual Studio a chování obsahu.

Ukázkový soubor HelpContentSetup.msha: (Nahraďte názvy souborů "název sady obsahu 1" a "název sady obsahu 2" atd.)

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
</div>.
```

1. Vytvořit místní složku, něco jako "C:\SampleContent"

2. V tomto příkladu použijeme soubory MSHC, které obsahují témata.  MSHC je zip s příponou souboru změněn z .zip na . MSHC.

3. Vytvořte níže uvedenou nápověduSetup.msha jako textový soubor (poznámkový blok byl použit k vytvoření souboru) a uložte jej do výše uvedené složky (viz krok 1).

Třída "Branding" existuje a je jedinečná. Branding mshc je součástí tohoto základního nátěru tak, aby nainstalovaný obsah bude mít značky a chování obsahu, které jsou obsaženy v MSHCs bude mít příslušné prvky podpory obsažené v balíčku značky. Bez toho dojde k chybám, když systém vyhledá položky podpory, které nejsou součástí zkopírovaného (nainstalovaného) obsahu.

Chcete-li získat balíček značky sady Visual Studio, zkopírujte soubor Branding_en-US.mshc na adrese C:\Program Files (x86)\Microsoft Help Viewer\v2.3\ do pracovní složky.

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

**Souhrn**

Použití a rozšíření výše uvedených kroků umožní vsp nasadit své sady obsahu pro prohlížeč nápovědy sady Visual Studio.

### <a name="add-help-to-the-visual-studio-shell-integrated-and-isolated"></a>Přidání nápovědy k prostředí Visual Studio (integrované a izolované)

**Úvod**

Tento návod ukazuje, jak začlenit obsah nápovědy do aplikace prostředí Visual Studio a potom jej nasadit.

**Požadavky**

1. [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]

2. [Visual Studio 2013 Izolované Shell Redist](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)

**Přehled**

Prostředí [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] je verze ide, [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] na kterém můžete založit aplikaci. Tyto aplikace obsahují izolované prostředí spolu s rozšířeními, které vytvoříte. Pomocí šablon projektu izolované prostředí, které [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] jsou zahrnuty v sadě SDK, k sestavení rozšíření.

Základní kroky pro vytvoření aplikace založené na izolované prostředí a její nápověda:

1. Získejte [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] redistribuovatelné prostředí ISO Shell (stažení společnosti Microsoft).

2. V sadě Visual Studio vytvořte rozšíření nápovědy, které je založeno na izolovaném prostředí, například rozšíření nápovědy Contoso, které je popsáno dále v tomto návodu.

3. Zabalit rozšíření a ISO Shell redistributable do nasazení MSI (nastavení aplikace). Tento návod neobsahuje krok nastavení.

Vytvořte úložiště obsahu sady Visual Studio. Pro scénář integrované prostředí změňte Visual Studio12 na název katalogu produktů takto:

- Vytvořte složku C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15.

- Vytvořte soubor s názvem CatalogType.xml a přidejte jej do složky. Soubor by měl obsahovat následující řádky kódu:

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <catalogType>UserManaged</catalogType>
    ```

Definujte úložiště obsahu v registru. Pro integrované prostředí změňte VisualStudio15 na název katalogu produktů:

- HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Katalogy\VisualStudio15

   Klíč: Hodnota řetězce Lokace: C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15\

- HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Katalogy\VisualStudio15\en-US

   Klíč: Hodnota Řetězce [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] CatalogName: Dokumentace

**Vytvoření projektu**

Vytvoření rozšíření izolovaného prostředí:

1. V sadě Visual Studio v části **Soubor**vyberte **Nový projekt**, v části Jiné **typy projektů** zvolte **Rozšiřitelnost**a pak zvolte **Visual Studio Shell Isolated**. Název projektu `ContosoHelpShell`) chcete-li vytvořit projekt rozšiřitelnosti na základě šablony izolovanéprostředí sady Visual Studio.

2. V Průzkumníku řešení v projektu ContosoHelpShellUI otevřete ve složce Soubory prostředků soubor ApplicationCommands.vsct. Ujistěte se, že tento řádek je komentoval (hledat "No_Help"):`<!-- <define name="No_HelpMenuCommands"/> -->`

3. Zvolte klíč F5 pro kompilaci a spuštění **ladění**. V experimentální instanci ide izolovaného prostředí zvolte nabídku **Nápověda.** Zkontrolujte, zda se zobrazí příkazy **Zobrazit nápovědu**, **Přidat a odebrat obsah nápovědy**a **Nastavit předvolbu nápovědy.**

4. V Průzkumníku řešení v projektu ContosHelpShell otevřete ve složce Přizpůsobení prostředí soubor ContosoHelpShell.pkgdef. Chcete-li definovat katalog nápovědy společnosti Contoso, přidejte následující řádky:

    ```
     [$RootKey$\Help]
    "Product"="Contoso"
    "Catalog"="Contoso"
    "Version"="100"
    "BrandingPackage"="ContosoBrandingPackage.mshc"
    ```

5. V Průzkumníku řešení v projektu ContosHelpShell otevřete ve složce Přizpůsobení prostředí contosoHelpShell.Application.pkgdef. Chcete-li povolit nápovědu F1, přidejte následující řádky:

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

6. V Průzkumníku řešení v kontextové nabídce řešení ContosoHelpShell zvolte položku nabídky **Vlastnosti.** V části **Vlastnosti konfigurace**vyberte **Nástroj pro konfiguraci**. Ve **sloupci Konfigurace** změňte každou hodnotu "Ladění" na "Release".

7. Sestavte řešení. Tím se vytvoří sada souborů ve složce vydání, která bude použita v další části.

Chcete-li to otestovat, jako by byl nasazen:

1. V počítači, do kterýho nasazujete contoso, nainstalujte stažený (shora) ISO Shell.

2. Vytvořte složku \\v \Program Files\\(x86) a pojmenujte ji `Contoso`.

3. Zkopírujte obsah ze složky vydání contosoHelpShell do \\složky \Program Files (x86)\Contoso\.

4. Spusťte Editor registru **Start** tak, že `Regedit`v nabídce Start **zvolíte Spustit** a zadáte položku . V editoru registru zvolte **Soubor**a potom **Importujte**. Přejděte do složky projektu ContosoHelpShell. V podsložce ContosoHelpShell zvolte ContosoHelpShell.reg.

5. Vytvoření úložiště obsahu:

    Pro prostředí ISO - vytvoření úložiště obsahu společnosti Contoso C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\ContosoDev12

    V [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] případě integrovaného prostředí vytvořte složku C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15

6. Vytvořit CatalogType.xml a přidat do úložiště obsahu (předchozí krok) obsahující:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <catalogType>UserManaged</catalogType>
   ```

7. Přidejte následující klíče registru:

    HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15Key: Hodnota řetězce LocationPath:

    Pro ISO Shell:

    C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15

    [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]Integrovaný shell:

    C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15en-US

    Klíč: Hodnota Řetězce [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] CatalogName: Dokumentace. Pro prostředí ISO Shell se jedná o název katalogu.

8. Zkopírujte svůj obsah (kabiny nebo MSHC a MSHA) do místní složky.

9. Příklad příkazového řádku integrovaného prostředí pro testování úložiště obsahu. Pro ISO Shell změňte katalog a spouštěníHodnoty aplikace podle potřeby tak, aby odpovídaly produktu.

     "C:\Program Files (x86)\Microsoft Help Viewer\v2.3\HlpViewer.exe" /catalogName VisualStudio15 /helpQuery method="page&id=ContosoTopic0" /launchingApp Microsoft,VisualStudio,12.0

10. Spusťte aplikaci Contoso (z kořenového adresáře aplikace Contoso). V prostředí ISO zvolte položku nabídky **Nápověda** a změňte **předvolbu nastavení nápovědy** pro **použití místní nápovědy**.

11. V rámci prostředí zvolte položku nabídky **Nápověda** a **potom zobrazit nápovědu**. Měl by být spuštěn místní prohlížeč nápovědy. Zvolte kartu **Spravovat obsah.** V části **Zdroj instalace**zvolte přepínač **Disk.** Zvolte **tlačítko ...** a přejděte do místní složky obsahující obsah Contoso (zkopírovaný do místní složky ve výše uvedeném kroku). Zvolte soubor HelpContentSetup.msha. Contoso by se nyní měl ukázat jako kniha ve výběru knih. Zvolte **Přidat**a pak zvolte tlačítko **Aktualizovat** (v pravém dolním rohu).

12. V rámci contoso IDE zvolte klávesu F1 pro testování funkcí F1.

## <a name="additional-resources"></a>Další zdroje

Rozhraní RUNTIME API naleznete v tématu [Rozhraní nápovědy systému Windows](/previous-versions/windows/desktop/helpapi/helpapi-portal).

Další informace o využití rozhraní API nápovědy naleznete v [příkladech kódu prohlížeče nápovědy](https://marketplace.visualstudio.com/items?itemName=RobChandlerHelpMVP.HelpViewer20CodeExamples).

Návrhy funkcí můžete odeslat v [komunitě vývojářů](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).
