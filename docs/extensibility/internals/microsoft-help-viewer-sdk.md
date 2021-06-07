---
title: Sada Microsoft Help Viewer SDK | Microsoft Docs
description: Přečtěte si informace o úlohách aplikace Visual Studio Help Viewer, jako je vytvoření článku, vytvoření balíčku obsahu brandingu pro aplikaci Help Viewer a nasazení sady článků.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 620d7dcd-d462-475e-a449-fbfa06ff12c5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8bc2ed473e25dc75d0155bc864aa02c157e3482f
ms.sourcegitcommit: f430d014f912aa7874e1db65026dc72688b973e4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2021
ms.locfileid: "111448321"
---
# <a name="microsoft-help-viewer-sdk"></a>Microsoft Help Viewer SDK

Tento článek obsahuje následující úlohy pro integrátory aplikace Visual Studio Help Viewer:

- Vytvoření tématu (podpora F1)

- Vytvoření balíčku s obsahem brandingu v prohlížeči nápovědy

- Nasazení sady článků

- Přidání pomocníka do prostředí sady Visual Studio (integrovaný nebo izolovaný režim)

- Další materiály

## <a name="create-a-topic-f1-support"></a>Vytvoření tématu (podpora F1)

V této části najdete Přehled součástí prezentovaného tématu, požadavky na téma, krátký popis postupu vytvoření tématu (včetně požadavků na podporu F1) a nakonec příklad tématu s jeho vykresleným výsledkem.

**Přehled témat v programu Help Viewer**

Když je pro vykreslování k dispozici téma, aplikace Help Viewer získá prvky balíčku, které jsou spojeny s tématem v době instalace nebo Poslední aktualizace, společně s tématem XHTML a zkombinuje dvě k výsledku v zobrazení prezentovaného obsahu (branding data + data tématu).  Brandingový balíček obsahuje loga, podporu pro chování obsahu a text brandingu (Copyright atd.).  Další informace o prvcích balíčku brandingu najdete níže v části "vytvoření balíčku branding" níže.  V případě, že se k tématu nevztahují žádné balíčky brandingu, aplikace Help Viewer použije záložní balíček brandingu umístěný v kořenovém adresáři aplikace Help Viewer (Branding_en-US. mshc).

**Požadavky na téma v prohlížeči nápovědy**

Aby se obsah obsahu nezpracovaných témat správně vykreslil v aplikaci Help Viewer, musí být W3C Basic 1,1 XHTML.

Téma obvykle obsahuje dvě části:

- Metadata (viz Referenční dokumentace metadat obsahu): data o tématu, například téma jedinečné ID, hodnota klíčového slova, ID obsahu tématu, ID nadřazeného uzlu atd.

- Obsah těla: kompatibilní se standardem W3C Basic 1,1 XHTML, který zahrnuje chování podporovaného obsahu (sbalitelná oblast, fragment kódu atd.) Zobrazí se úplný seznam.

Ovládací prvky podporované balíčkem sady Visual Studio:

- Odkazy

- CodeSnippet

- CollapsibleArea

- Zděděný člen

- LanguageSpecificText

Podporované řetězce jazyka (bez rozlišení velkých a malých písmen):

- javascript

- CSharp nebo c #

- cplusplus nebo VisualC + + nebo c++

- skript

- VisualBasic nebo VB

- f # nebo FSharp nebo FS

- jiný – řetězec, který představuje název jazyka

**Vytvoření tématu v programu Help Viewer**

Vytvořte nový dokument XHTML s názvem ContosoTopic4.htm a přidejte značku title (níže).

```html
<html>
<head>
<title>Contoso Topic 4</title>
</head>

<body>

</body>
</html>

```

Dále přidejte data a definujte, jak se má téma prezentovat (vlastní značka nebo ne), jak odkazovat na toto téma pro F1, kde toto téma existuje v rámci obsahu, jeho ID (odkazování podle jiných témat) atd. Úplný seznam podporovaných metadat naleznete v tabulce metadata obsahu.

- V tomto případě použijeme náš vlastní balíček brandingu, což je varianta balíčku nápovědy k aplikaci Visual Studio Help Viewer.

- Přidejte hodnoty meta Name a value pro F1 ("Microsoft. help. F1" content = "ContosoTopic4"), které budou odpovídat zadané hodnotě F1 v kontejneru vlastností IDE. (Další informace najdete v části podpory F1.) Toto je hodnota, která se shoduje s voláním F1 z rozhraní IDE pro zobrazení tohoto tématu v případě, že je v integrovaném vývojovém prostředí zvolena klávesa F1.

- Přidejte ID tématu. Toto je řetězec, který se používá v jiných tématech pro propojení s tímto tématem. Je to ID programu Help Viewer pro toto téma.

- Pro obsah přidejte nadřazený uzel tohoto tématu a definujte, kde se bude tento uzel obsahu tématu zobrazovat.

- V části obsah přidejte pořadí uzlů tohoto tématu. Pokud má nadřazený uzel `n` počet podřízených uzlů, definujte v pořadí podřízených uzlů umístění tohoto tématu. Toto téma má například počet 4 podřízených témat.

Příklad oddílu metadata:

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

Tělo (bez záhlaví a zápatí) tématu bude obsahovat odkazy na stránky, oddíl poznámky, sbalitelnou oblast, fragment kódu a oddíl textu pro konkrétní jazyk.  Informace o oblastech prezentovaného tématu najdete v části branding.

1. Přidat značku nadpisu tématu:  `<div class="title">Contoso Topic 4</div>`

2. Přidat oddíl Poznámky: `<div class="alert"> add your table tag and text </div>`

3. Přidat sbalitelnou oblast:  `<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> add text  </CollapsibleArea>`

4. Přidat fragment kódu:  `<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > a block of code </CodeSnippet>`

5. Přidat text specifický pro jazyk kódu:  `<LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />` Všimněte si, že `devLangnu=` je možné zadat jiné jazyky. Například `devLangnu="Fortran"` zobrazí FORTRAN, když fragment kódu DisplayLanguage = FORTRAN

6. Přidat odkazy na stránky: `<a href="ms-xhelp:///?Id=ContosoTopic1">Main Topic</a>`

> [!NOTE]
> Poznámka: pro nepodporovaný nový "jazyk zobrazení" (příklad, verze F #, COBOL, FORTRAN) ve fragmentu kódu bude monochromatický.

**Příklad tématu Help Viewer** Kód ukazuje, jak definovat metadata, fragment kódu, sbalitelnou oblast a text specifický pro jazyk.

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

V sadě Visual Studio vygeneruje klávesa F1 hodnoty dodávané z umístění kurzoru v rámci rozhraní IDE a naplní "kontejner objektů a dat" zadanými hodnotami (na základě umístění kurzoru). Když je ukazatel nad funkcí x, je funkce x aktivní/v zaostření a naplní kontejner objektů a hodnot.  Když je vybrána klávesa F1, naplní se kontejner objektů a Visual Studio F1 a zjistí, zda je výchozí zdroj Nápověda místní nebo online (výchozí hodnota je online), pak vytvoří odpovídající řetězec na základě nastavení uživatele (výchozí nastavení je online) – spuštění prostředí (Další informace najdete v příručce pro správce nápovědy k parametrům spuštění exe) s parametry pro místní nápovědu a klíčová slova z kontejneru objektů a dat, pokud je místní Nápověda výchozí. nebo adresu URL MSDN s klíčovým slovem v seznamu parametrů.

Pokud jsou vraceny tři řetězce pro F1, označované jako řetězec s více hodnotami, vezměte první výraz, vyhledejte nalezený a pokud se najde, jsme hotovi. Pokud ne, přejděte k dalšímu řetězci.  Otázky objednávky. Prezentace klíčových slov s více hodnotami by měla být nejdelší řetězec na nejkratší řetězec.  Pokud to chcete ověřit v případě klíčových slov s více hodnotami, podívejte se na řetězec adresy URL online F1, který bude obsahovat zvolené klíčové slovo.

V aplikaci Visual Studio 2012 jsme záměrně provedli silnější dělení mezi online a offline, takže pokud bylo nastavení uživatele pro online, pak jsme jednoduše předali požadavek F1 přímo na naši online dotazovací službu na webu MSDN namísto směrování prostřednictvím agenta knihovny pro nápovědu, který jsme měli v aplikaci Visual Studio 2010. Pak se pak spoléhá na stav "nainstalovaného obsahu dodavatele = true" a určí, jestli se v daném kontextu něco liší. Pokud je hodnota true, pak tuto logiku analýzy a směrování provádíme v závislosti na tom, co chcete pro vaše zákazníky podpořit. Pokud je hodnota false, stačí přejít na web MSDN. Pokud je nastavení uživatele místní, pak všechna volání přejdou do místního modulu nápovědy.

Vývojový diagram F1:

![Průběh F1](../../extensibility/internals/media/f1flow.png "F1flow")

Když je zdroj obsahu výchozí nápovědy aplikace Help Viewer nastaven na hodnotu online (spustit v prohlížeči):

- Funkce programu Visual Studio partner (VSP) emitují hodnotu do kontejneru vlastností F1 (předpona kontejneru objektů a adresy URL online pro předponu, která se nachází v registru): F1 pošle do prohlížeče parametry adresu URL VSP.

- Funkce sady Visual Studio (Editor jazyka, položky nabídky specifické pro Visual Studio atd.): F1 pošle do prohlížeče adresu URL sady Visual Studio.

Když je zdroj obsahu výchozí nápovědy aplikace Help Viewer nastavený na místní (spustit v aplikaci Help Viewer):

- Funkce VSP, kde se shoduje klíčové slovo mezi kontejnerem vlastností F1 a indexem místního úložiště (tj. předpona kontejneru vlastností. klíčové slovo = hodnota nalezená v místním indexu úložiště): F1 vykreslí téma v programu Help Viewer.

- Funkce sady Visual Studio (žádná možnost pro rozhraní VSP nemůže přepsat kontejner objektů a dat vysílaný z funkcí sady Visual Studio): F1 vykreslí téma sady Visual Studio v aplikaci Help Viewer.

Nastavte následující hodnoty registru, aby se pro obsah Nápověda dodavatele povolila možnost F1 Fallback. Příkaz F1 Fallback znamená, že aplikace Help Viewer je nastavená tak, aby hledala obsah nápovědy pro F1 online, a obsah dodavatele se instaluje místně na pevný disk uživatele. V programu Help Viewer by se měla zobrazovat informace o místní nápovědě k obsahu, i když je výchozí nastavení pro online nápovědu.

1. V klíči registru Help 2,3 nastavte hodnotu **VendorContent** :

   - Pro 32 operační systémy:

        HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Catalogs\VisualStudio15

        "VendorContent" = DWORD: 00000001

   - Pro 64 operační systémy:

        HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15

        "VendorContent" = DWORD: 00000001

2. Zaregistrujte obor názvů partnera v klíči registru Help 2,3:

   - Pro 32 operační systémy:

      <em> \\ Obor názvů \> HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Partner<</em>

      "umístění" = "offline"

   - Pro 64 operační systémy:

      <em> \\ Obor názvů \> HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Partner<</em>

      "umístění" = "offline"

**Základní analýza oboru názvů Native**

Chcete-li zapnout analýzu základního nativního oboru názvů, přidejte v registru novou hodnotu DWORD s názvem: BaseNativeNamespaces a nastavte její hodnotu na 1 (v rámci klíče katalogu, který chtějí podporovat).  Například pokud chcete použít katalog sady Visual Studio, můžete přidat klíč do cesty:

HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15

Při výskytu klíčového slova F1 ve formátu HEADER/METHOD bude analyzován znak '/', výsledkem bude následující konstrukce:

- Hlavička: bude obor názvů, který se dá použít k registraci v registru.

- Metoda: to se stane klíčovým slovem, které se předává.

Například vzhledem k tomu, že vlastní knihovna s názvem CustomLibrary a metoda s názvem MyTestMethod, bude v případě, že žádost F1 do ní přijde, naformátovaná jako `CustomLibrary/MyTestMethod` .

Uživatel pak může zaregistrovat CustomLibrary jako obor názvů v podregistru partneři a zadat libovolný klíč místa, který chce, a klíčové slovo předané do dotazu bude MyTestMethod.

**Povolit nástroj pro ladění helpu v integrovaném vývojovém prostředí**

Přidejte následující klíč registru a hodnotu:

::: moniker range="vs-2017"

**HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Dynamic Help**

::: moniker-end

::: moniker range=">=vs-2019"

**HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\16.0\Dynamic Help**

::: moniker-end

Hodnota: zobrazit výstup ladění v maloobchodních datech: Ano

V integrovaném vývojovém prostředí (IDE) v položce nabídky Help vyberte **ladit kontext kontextové nápovědě**.

**Metadata obsahu**

V následující tabulce je libovolný řetězec, který se zobrazí mezi závorkami, zástupný symbol, který musí být nahrazen rozpoznanou hodnotou. Například v \<meta name="Microsoft.Help.Locale" content="[language code]" /> příkazu "[kód jazyka]" musí být nahrazen hodnotou, například "en-US".

| – Vlastnost (reprezentace HTML) | Description |
| - | - |
| \< meta name="Microsoft.Help.Locale" content="[language-code]" /> | Nastaví národní prostředí pro toto téma. Pokud je tato značka použita v tématu, musí být použita pouze jednou a musí být vložena nad jakoukoliv jinou značku nápovědy společnosti Microsoft. Pokud se tato značka nepoužívá, je hlavní text tématu indexován pomocí dělení slov, které je přidruženo k národnímu prostředí produktu, pokud je zadáno. v opačném případě se použije dělení slov en-US. Tato značka odpovídá ISOC RFC 4646. Chcete-li zajistit správnou funkci aplikace Microsoft Help, použijte tuto vlastnost namísto obecného atributu Language. |
| \< meta name="Microsoft.Help.TopicLocale" content="[language-code]" /> | Nastaví národní prostředí pro toto téma, pokud se používají také jiné národní prostředí. Pokud je tato značka použita v tématu, musí být použita pouze jednou. Tuto značku použijte, pokud katalog obsahuje obsah ve více než jednom jazyce. Více témat v katalogu může mít stejné ID, ale každý musí určovat jedinečný TopicLocale. Téma, které určuje TopicLocale, které odpovídá národnímu prostředí katalogu, je téma, které se zobrazí v obsahu. Ve výsledcích hledání se ale zobrazí všechny jazykové verze tématu. |
| \< title>Hlava\</title> | Určuje název tohoto tématu. Tato značka je povinná a v tématu se musí použít jenom jednou. Pokud hlavní část tématu neobsahuje nadpis \<div> , tento název se zobrazí v tématu a v obsahu. |
| \< meta name=" Microsoft.Help.Keywords" content="[aKeywordPhrase]"/> | Určuje text odkazu, který se zobrazí v podokně index aplikace Help Viewer. Po kliknutí na odkaz se zobrazí téma. Můžete zadat více klíčových slov indexu pro téma nebo tuto značku můžete vynechat, pokud nechcete, aby se odkazy na toto téma zobrazovaly v indexu. Klíčová slova "k" z dřívějších verzí aplikace Help lze převést na tuto vlastnost. |
| \< meta name="Microsoft.Help.Id" content="[TopicID]"/> | Nastaví identifikátor pro toto téma. Tato značka je povinná a v tématu se musí použít jenom jednou. ID musí být jedinečné mezi tématy v katalogu, která mají stejné nastavení národního prostředí. V jiném tématu můžete vytvořit odkaz na toto téma pomocí tohoto ID. |
| \< meta name="Microsoft.Help.F1" content="[System.Windows.Controls.Primitives.IRecyclingItemContainerGenerator]"/> | Určuje klíčové slovo F1 pro toto téma. Můžete zadat více klíčových slov F1 pro téma nebo tuto značku můžete vynechat, pokud nechcete, aby toto téma bylo zobrazeno, když uživatel aplikace stiskne klávesu F1. Pro téma je obvykle zadáno pouze jedno klíčové slovo F1. Klíčová slova "F" z dřívějších verzí aplikace Help lze převést na tuto vlastnost. |
| \< meta name="Description" content="[topic description]" /> | Poskytuje stručný souhrn obsahu v tomto tématu. Pokud je tato značka použita v tématu, musí být použita pouze jednou. Tato vlastnost je k této vlastnosti přistupovaná přímo knihovnou dotazů. není uložen v souboru indexu. |
| meta název = "Microsoft. help. TocParent" content = "[parent_Id]"/> | Určuje nadřazené téma tohoto tématu v obsahu. Tato značka je povinná a v tématu se musí použít jenom jednou. Hodnota je Microsoft.Help.Id nadřazeného objektu. Téma může obsahovat pouze jedno umístění v obsahu. "-1" se považuje za ID tématu pro kořen obsahu. V [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] nástroji je tato stránka domovskou stránkou prohlížeče nápovědy. To je stejný důvod, že konkrétně do některých témat přidáte TocParent =-1, abyste zajistili, že se zobrazí na nejvyšší úrovni. Domovská stránka aplikace Help Viewer je systémová stránka, takže ji nelze nahradit. Pokud se VSP pokusí přidat stránku s IDENTIFIKÁTORem-1, může být přidána do sady obsahu, ale prohlížeč nápovědy bude vždy používat domovskou stránku System-Help Viewer. |
| \< meta name="Microsoft.Help.TocOrder" content="[positive integer]"/> | Určuje, kde v obsahu v tomto tématu se zobrazí Příbuzná témata. Tato značka je povinná a v tématu se musí použít jenom jednou. Hodnota je celé číslo. Téma, které určuje celé číslo nižší hodnoty, se zobrazí nad tématem, které určuje celé číslo s vyšší hodnotou. |
| \< meta name="Microsoft.Help.Product" content="[product code]"/> | Určuje produkt, který popisuje toto téma. Pokud je tato značka použita v tématu, musí být použita pouze jednou. Tyto informace se dají zadat taky jako parametr, který se předává indexeru pro usnadnění. |
| \< meta name="Microsoft.Help.ProductVersion" content="[version number]"/> | Určuje verzi produktu, kterou popisuje toto téma. Pokud je tato značka použita v tématu, musí být použita pouze jednou. Tyto informace se dají zadat taky jako parametr, který se předává indexeru pro usnadnění. |
| \< meta name="Microsoft.Help.Category" content="[string]"/> | Používá produkty k identifikaci pododdílů obsahu. Můžete identifikovat několik dílčích sekcí tématu, nebo můžete tuto značku vynechat, pokud nechcete, aby odkazy identifikovaly jakékoli dílčí oddíly. Tato značka se používá k uložení atributů pro TargetOS a TargetFrameworkMoniker, když se téma převede z dřívější verze nápovědy. Formát obsahu je AttributeName: vlastnost AttributeValue. |
| \< meta name="Microsoft.Help.TopicVersion content="[topic version number]"/> | Určuje tuto verzi tématu, pokud v katalogu existuje více verzí. Vzhledem k tomu, že Microsoft.Help.Id není zaručená jedinečnost, tato značka se vyžaduje v případě, že v katalogu existuje více než jedna verze tématu, například když katalog obsahuje téma pro .NET Framework 3,5 a téma pro .NET Framework 4 a obě mají stejný Microsoft.Help.Id. |
| \< meta name="SelfBranded" content="[TRUE or FALSE]"/> | Určuje, jestli Toto téma používá balíček s úvodními informacemi od správce knihovny nápovědy, nebo balíček brandingu, který je specifický pro téma. Tato značka musí být buď TRUE, nebo FALSE. Pokud je hodnota TRUE, pak balíček branding pro příslušné téma přepíše balíček brandingu, který je nastaven při spuštění Správce knihovny nápovědy, aby bylo téma vykresleno tak, jak je určeno, i když se liší od vykreslování jiného obsahu. Pokud je hodnota FALSE, aktuální téma se vykreslí podle balíčku brandingu, který je nastaven při spuštění Správce knihovny nápovědy. Ve výchozím nastavení předpokládá správce knihovny podpory vlastní branding na hodnotu false, pokud není proměnná SelfBranded deklarována jako TRUE. Proto není nutné deklarovat \<meta name="SelfBranded" content="FALSE"/> . |

## <a name="create-a-branding-package"></a>Vytvoření balíčku branding

Verze Visual studia zahrnuje řadu různých produktů sady Visual Studio, včetně izolovaných a integrovaných prostředí pro partnery sady Visual Studio.  Každý z těchto produktů vyžaduje určitý stupeň podpory brandingu obsahu nápovědy založeného na tématu, který je pro produkt jedinečný.  Například témata sady Visual Studio musí mít konzistentní prezentaci značek, zatímco SQL Studio, které balí prostředí ISO Shell, vyžaduje vlastní jedinečný branding obsahu nápovědy pro každé téma.  Integrovaný partner prostředí může chtít, aby jejich témata nápovědy byla v rámci nadřazeného obsahu nápovědy produktu sady Visual Studio a zároveň zachovala vlastní branding tématu.

Balíčky brandingu jsou nainstalované produktem, který obsahuje prohlížeč nápovědy.  Pro produkty sady Visual Studio:

- Záložní balíček branding (Branding_ \<locale> . mshc) je nainstalován v kořenovém adresáři aplikace Help viewer 2,3 (příklad: C:\Program Files (x86) \Microsoft Help Viewer\v2.3) v rámci jazykové sady Help Viewer.  Tato možnost se používá pro případy, kdy balíček branding produktu není nainstalovaný (není nainstalovaný žádný obsah) nebo kde je nainstalovaný balíček brandingu poškozený.  Prvky aplikace Visual Studio (logo a zpětná vazba) se ignorují, když se použije balíček pro záložní použití výrobce aplikace.

- Když je obsah sady Visual Studio nainstalován ze služby balíčků obsahu, nainstaluje se také balíček branding (při prvním scénáři instalace obsahu při instalaci).  Pokud je k dispozici aktualizace brandingového balíčku, aktualizace se nainstaluje, když dojde k další aktualizaci obsahu nebo k instalaci dalšího balíčku.

Microsoft Help Viewer podporuje branding témat v závislosti na metadatech tématu.

- Kde metadata tématu definují vlastní značku = true, vykreslí téma tak, jak je, neprovádějte žádnou akci (pokud jde o branding).

- Kde metadata tématu definují vlastní značku = false, použijte balíček branding přidružený k hodnotě metadat TopicVendor.

- Kde metadata tématu definují název = "Microsoft. help. TopicVendor" Content = \< branding package name in vendor MSHA> , použijte balíček branding definovaný v hodnotě obsahu.

- V katalogu sady Visual Studio je k dispozici prioritní použití balíčků s brandingem.  Použije se první vlastní branding sady Visual Studio a potom se v případě, že je definovaný v metadatech tématu a podporuje s přidruženým balíčkem brandingu (jak je definováno v instalačním msha), použije dodavatel, který definoval branding, jako přepsání.

Prvky značky typicky spadají do tří hlavních kategorií:

- Prvky záhlaví (příklady zahrnují odkaz na zpětnou vazbu, text podmíněného omezení, logo)

- Chování obsahu (příklady zahrnují elementy rozbalení/sbalení ovládacího prvku textu a elementy fragmentu kódu)

- Elementy zápatí (příklad autorských práv)

Mezi položky považované za prvky s brandedem patří (podrobně uvedené v této specifikací):

- Logo katalogu nebo produktu (například Visual Studio)

- Odkaz na zpětnou vazbu a prvky e-mailu

- Text právní omezení

- Text o autorských právech

Mezi podpůrné soubory v balíčku Visual Studio help viewer patří:

- Grafika (loga, ikony atd.)

- Branding.js – soubory skriptů podporující chování obsahu

- Branding.xml – řetězce, které se konzistentně používají napříč obsahem katalogu.  Poznámka: Visual Studio elementy textu lokalizace v branding.xml, _locID=" \<unique value> "

- Branding.css – definice stylu pro konzistenci prezentace

- Printing.css – definice stylů pro konzistentní tiskovou prezentaci

Jak je uvedeno výše, k tématu jsou přidruženy balíčky brandingu:

- Když je v metadatech definovaný SelfBranded = false, zdědí téma balíček brandingu katalogu.

- Nebo když SelfBranded = false a v MSHA je definovaný jedinečný balíček brandingu, který je k dispozici při instalaci obsahu.

U VSP implementující vlastní balíčky brandingu (obsah VSP, SelfBranded=True) je možné pokračovat tak, že začnete s balíčkem pro záložní branding (nainstalovaným s prohlížečem nápovědy) a podle potřeby změníte název souboru.  Soubor Branding_ .mszip je soubor zip s příponou změněnou na .ms digest, takže jednoduše změňte příponu z .mszip na .zip \<locale> a rozbalte obsah.  Níže najdete prvky balíčku brandingu a podle potřeby je upravte (například změňte logo na logo VSP a odkaz na logo v souboru Branding.xml, aktualizujte Branding.xml podle specifik VSP atd.).

Po provedení všech úprav vytvořte soubor ZIP obsahující požadované prvky brandingu a změňte příponu na .ms na .

Pokud chcete přidružit balíček vlastního brandingu, vytvořte MSHA, který obsahuje odkaz na soubor ms string brandingu společně s obsahem ms string (obsahujícím témata).  Postup vytvoření základního MSHA najdete níže v části MSHA.

Soubor Branding.xml obsahuje seznam elementů používaných pro konzistentní vykreslování konkrétních položek v tématu, pokud téma obsahuje \<meta name="Microsoft.Help.SelfBranded" content="false"/> .  Níže Visual Studio seznam elementů v Branding.xml souboru.  Tento seznam je určený k použití jako šablona pro uživatele ISO Shellu, kde tyto prvky (například logo, zpětná vazba a autorská práva) upraví tak, aby splňovaly jejich vlastní potřeby značek produktů.

Poznámka: Proměnné, které si poznamenat {n}, mají závislosti kódu – odebrání nebo změna těchto hodnot způsobí chyby a případně i selhání aplikace. Identifikátory lokalizace (_locID="codesnippet.n") jsou součástí balíčku Visual Studio brandingu.

**Branding.xml**

| Element | Popis |
| - | - |
| Funkce: | **Sbalitelnáoblast** |
| Použít: | Při rozbalení se sbalí text ovládacího prvku obsahu. |
| **Prvek** | **Hodnota** |
| RozbalitText | Rozbalit |
| Sbalit text | Sbalit |
| Funkce: | **CodeSnippet** |
| Použít: | Text ovládacího prvku fragmentu kódu.  Poznámka: Obsah fragmentu kódu s prostorem "Non-Breaking" se změní na mezeru. |
| **Prvek** | **Hodnota** |
| CopyToClipboard (Kopírovat na panel) | Kopírování do schránky |
| ViewColorizedText | Zobrazení s barevnými barvami |
| CombinedVBTabDisplayLanguage | Visual Basic (ukázka) |
| VBDeclaration | Deklarace |
| VBUsage | Využití |
| Funkce: | **Zpětná vazba, zápatí a logo** |
| Použít: | Poskytněte zákazníkovi ovládací prvek pro zpětnou vazbu, aby prostřednictvím e-mailu poskytl zpětnou vazbu k aktuálnímu tématu.  Text autorských práv k obsahu.  Definice loga. |
| **Prvek** | **Hodnota (Tyto řetězce je možné upravit tak, aby splňovaly požadavky na přijetí obsahu.)** |
| Copyright | © 2013 Microsoft Corporation. All rights reserved. |
| SendFeedback | \<a href="{0}" {1}>Pošlete \</a> Námět k tomuto tématu společnosti Microsoft. |
| Odkaz na zpětnou vazbu | |
| LogoTitle | [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] |
| Název souboru loga | vs_logo_bk.gif |
| Název_souboru_loga NEPOSOUDÍ | vs_logo_wh.gif |
| Funkce: | **Právní omezení** |
| Použít: | Sada zřeknutí se konkrétních případů pro strojově přeložený obsah |
| **Prvek** | **Hodnota** |
| MT_Editable | Tento článek byl přeložený strojově. Pokud máte připojení k internetu, vyberte Zobrazit toto téma online a zobrazte tuto stránku v režimu úprav s původním anglickým obsahem současně. |
| MT_NonEditable | Tento článek byl přeložený strojově. Pokud máte připojení k internetu, vyberte Zobrazit toto téma online a zobrazte tuto stránku v režimu úprav s původním anglickým obsahem současně. |
| MT_QualityEditable | Tento článek byl přeložen ručně. Pokud máte připojení k internetu, vyberte Zobrazit toto téma online a zobrazte tuto stránku v režimu úprav s původním anglickým obsahem současně. |
| MT_QualityNonEditable | Tento článek byl přeložen ručně. Pokud máte připojení k internetu, vyberte Zobrazit toto téma online a zobrazte tuto stránku v režimu úprav s původním anglickým obsahem současně. |
| MT_BetaContents | Tento článek byl strojově přeložen pro předběžnou verzi. Pokud máte připojení k internetu, vyberte Zobrazit toto téma online a zobrazte tuto stránku v režimu úprav s původním anglickým obsahem současně. |
| MT_BetaRecycledContents | Tento článek byl ručně přeložen pro předběžnou verzi. Pokud máte připojení k internetu, vyberte Zobrazit toto téma online a zobrazte tuto stránku v režimu úprav s původním anglickým obsahem současně. |
| Funkce: | **Tabulka LinkTable** |
| Použít: | Podpora pro online odkazy na témata |
| **Prvek** | **Hodnota** |
| LinkTableTitle | Propojit tabulku |
| Text TopicEnuLinkText | Prohlédněte si \</a> anglickou verzi tohoto tématu, která je k dispozici na vašem počítači. |
| TopicOnlineLinkText | Zobrazit toto téma \<a href="{0}" {1}> online\</a> |
| OnlineText | Online |
| Funkce: | **Ovládací prvek Zvuk videa** |
| Použít: | Zobrazení elementů a textu pro obsah videa |
| **Prvek** | **Hodnota** |
| MultiMediaNotSupported | pro Internet Explorer obsahu musí být nainstalovaná verze 9 nebo {0} vyšší. |
| VideoText | zobrazení videa |
| AudioText | streamování zvuku |
| OnlineVideoLinkText | \<p>Pokud chcete zobrazit video přidružené k tomuto tématu, klikněte {0} \<a href="{1}"> {2} \</a> sem.\</p> |
| OnlineAudioLinkText | \<p>Pokud chcete naslouchat zvuku přidruženému k tomuto tématu, klikněte {0} \<a href="{1}"> {2} \</a> sem.\</p> |
| Funkce: | **Ovládací prvek Obsah nenainstalovaný** |
| Použít: | Textové prvky (řetězce) používané pro vykreslení contentnotinstalled.htm |
| **Prvek** | **Hodnota** |
| ContentNotInstalledTitle | Ve vašem počítači se nenašel žádný obsah. |
| ContentNotInstalledDownloadContentText | \<p>Pokud chcete stáhnout obsah do počítače, \<a href="{0}" {1}> klikněte na kartu \</a> Spravovat.\</p> |
| ContentNotInstalledText | \<p>Na vašem počítači se neinstaluje žádný obsah. Informace o instalaci obsahu místní nápovědy najdete u správce.\</p> |
| Funkce: | **Ovládací prvek Téma se nenašlo** |
| Použít: | Textové prvky (řetězce) používané pro vykreslení topicnotfound.htm |
| **Prvek** | **Hodnota** |
| TopicNotFoundTitle | V počítači nelze najít požadované téma. |
| TopicNotFoundViewOnlineText | \<p>Téma, o které jste požádali, se ve vašem počítači nenašlo, ale můžete \<a href="{0}" {1}> ho zobrazit \</a> online.\</p> |
| TopicNotFoundDownloadContentText | \<p>V navigačním podokně najdete odkazy na podobná témata nebo kliknutím \<a href="{0}" {1}> na kartu Spravovat \</a> stáhněte obsah do počítače.\</p> |
| Text TopicNotFoundText | \<p>Požadované téma se ve vašem počítači nenašlo.\</p> |
| Funkce: | **Poškozený ovládací prvek tématu** |
| Použít: | Textové prvky (řetězce) používané pro vykreslení topiccorrupted.htm |
| **Prvek** | **Hodnota** |
| TémaCorruptedTitle | Požadované téma se nepodařilo zobrazit. |
| TopicCorruptedViewOnlineText | \<p>Prohlížeč nápovědy nemůže zobrazit požadované téma. V obsahu tématu nebo v podkladové systémové závislosti může dojít k chybě.\</p> |
| Funkce: | **Ovládací prvek Domovská stránka** |
| Použít: | Text podporující zobrazení obsahu uzlu nejvyšší úrovně v Help Vieweru. |
| **Prvek** | **Hodnota** |
| HomePageTitle | Domovská stránka help vieweru |
| HomePageIntroduction | \<p>Vítá vás Microsoft Help Viewer, který je základním zdrojem informací pro každého, kdo používá nástroje, produkty, technologie a služby Microsoftu. Prohlížeč nápovědy poskytuje přístup k návodům a referenčním informacím, ukázkovému kódu, technickým článkům a další informace. Pokud chcete najít obsah, který potřebujete, projděte si obsah, použijte fulltextové vyhledávání nebo procházejte obsah pomocí indexu klíčových slov.\</p> |
| HomePageContentInstallText | \<p>\<br />Na \<a href="{0}" {1}> kartě Spravovat \</a> obsah můžete provést následující akce: Přidání \<ul> \<li> obsahu do počítače. \</li> \<li> Zkontrolujte aktualizace místního obsahu. \</li> \<li> Odeberte obsah z počítače.\</li>\</ul>\</p> |
| HomePageInstalledBooks | Nainstalované knihy |
| HomePageNoBooksInstalled | Ve vašem počítači se nenašel žádný obsah. |
| HomePageHelpSettings | Nastavení obsahu nápovědy |
| HomePageHelpSettingsText | \<p>Aktuální nastavení je místní nápověda. Prohlížeč nápovědy zobrazuje obsah, který jste nainstalovali do počítače. \<br /> Pokud chcete změnit zdroj obsahu nápovědy, v řádku nabídek Visual Studio Nápověda, \<span style="{0}"> Nastavte předvolby \</span> nápovědy.\<br />\</p> |
| Mb | MB |

**branding.js**

Soubor branding.js obsahuje JavaScript používaný prvky brandingu Visual Studio Help Viewer.  Níže je seznam prvků brandingu a podpůrné funkce JavaScriptu.  Všechny řetězce, které se mají lokalizovat pro tento soubor, jsou definované v části Lokalizovatelné řetězce v horní části tohoto souboru.  Soubor ICL byl vytvořen pro lokalovací řetězce v branding.js souboru.

|**Funkce brandingu**|**Funkce JavaScriptu**|**Popis**|
|-|-|-|
|Var...||Definování proměnných|
|Získání jazyka uživatelského kódu|setUserPreferenceLang|mapuje index # na jazyk kódu|
|Nastavení a získání hodnot souborů cookie|GetCookie, setCookie||
|Zděděný člen|changeMembersLabel|Rozbalit/sbalit zděděný člen|
|When SelfBranded = false|onLoad|Přečtěte si řetězec dotazu a ověřte, zda se jedná o žádost o tisk.  Nastavte všechny codesnippets tak, aby se zaměřily na kartu upřednostňovanou uživatelem.  Pokud se jedná o žádost o tisk, nastavte isPrinterFriendly na hodnotu true. Kontroluje režim vysokého kontrastu.|
|Fragment kódu|addSpecificTextLanguageTagSet||
||getIndexFromDevLang||
||ChangeTab||
||setCodesnippetLang||
||setCurrentLang||
||CopyToClipboard||
|CollapsibleArea|addToCollapsibleControlSet|zapisovat všechny objekty sbalitelného ovládacího prvku do seznamu.|
||CA_Click|na základě stavu sbalitelné oblasti definuje, který obrázek a text má být k dispozici.|
|Podpora kontrastu pro logo|isBlackBackground()|Volá se, aby se určilo, jestli je pozadí černé.  Pouze v režimu s vysokým kontrastem.|
||isHighContrast()|pro detekci režimu vysokého kontrastu použijte barevný rozsah|
||onHighContrast (černá)|Volá se při zjištění vysokého kontrastu.|
|Funkce LST|||
||addToLanSpecTextIdSet (ID)||
||updateLST(currentLang)||
||getDevLangFromCodeSnippet (lang)||
|Funkce multimédií|Caption (začátek, konec, text, styl)||
||findAllMediaControls(normalizedId)||
||getActivePlayer(normalizedId)||
||captionsOnOff (ID)||
||toSeconds (t)||
||getAllComments (uzel)||
||styleRectify (Style; styleValue)||
||showCC (ID)||
||Podnadpis (ID)||

**SOUBORY HTM**

Balíček branding obsahuje sadu souborů HTM, které podporují scénáře pro komunikaci s klíčovými informacemi, například domovskou stránku obsahující část popisující, které sady obsahu jsou nainstalovány a stránky sdělují uživateli, když témata nelze najít v místní sadě témat. Tyto soubory HTM lze upravovat pro jednotlivé produkty.  Dodavatelé prostředí ISO Shell mohou pořizovat výchozí balíček brandingu a změnit chování a obsah těchto stránek na Suite, které potřebují.  Tyto soubory odkazují na příslušný balíček brandingu, aby značky brandingu získaly odpovídající obsah z branding.xml souboru.

|**Soubor**|**Použití**|**Zobrazený zdroj obsahu**|
|-|-|-|
|homepage.htm|Toto je stránka, která zobrazuje aktuálně nainstalovaný obsah a všechny další zprávy, které jsou vhodné k tomu, aby uživatel mohl o svém obsahu prezentovat.  Tento soubor obsahuje další atribut meta data "Microsoft.Help.Id" content = "-1", který tento obsah umístí na začátek místního obsahu obsahu.||
||<META_HOME_PAGE_TITLE_ADD/>|Branding.xml, značka \<HomePageTitle>|
||<HOME_PAGE_INTRODUCTION_SECTION_ADD/>|Branding.xml, značka \<HomePageIntroduction>|
||<HOME_PAGE_CONTENT_INSTALL_SECTION_ADD/>|Branding.xml, značka \<HomePageContentInstallText>|
||<HOME_PAGE_BOOKS_INSTALLED_SECTION_ADD/>|Sekce nadpisu Branding.xml značku \<HomePageInstalledBooks> , data generovaná z aplikace,  \<HomePageNoBooksInstalled> když nejsou nainstalovány žádné knihy.|
||<HOME_PAGE_SETTINGS_SECTION_ADD/>|Sekce nadpisu Branding.xml značka \<HomePageHelpSettings> , text oddílu \<HomePageHelpSettingsText> .|
|topiccorrupted.htm|V případě, že v místní sadě existuje téma, ale z nějakého důvodu nelze zobrazit (poškozený obsah).||
||<META_TOPIC_CORRUPTED_TITLE_ADD/>|Branding.xml, značka \<TopicCorruptedTitle>|
||<TOPIC_CORRUPTED_SECTION_ADD/>|Branding.xml, značka \<TopicCorruptedViewOnlineText>|
|topicnotfound.htm|Pokud se téma nenajde v místní sadě obsahu, ani dostupné online||
||<META_TOPIC_NOT_FOUND_TITLE_ADD/>|Branding.xml, značka \<TopicNotFoundTitle>|
||<META_TOPIC_NOT_FOUND_ID_ADD/>|Branding.xml, značka \<TopicNotFoundViewOnlineText> + \<TopicNotFoundDownloadContentText>|
||<TOPIC_NOT_FOUND_SECTION_ADD/>|Branding.xml, značka \<TopicNotFoundText>|
|contentnotinstalled.htm|Pokud není nainstalován žádný místní obsah pro produkt.||
||<META_CONTENT_NOT_INSTALLED_TITLE_ADD/>|Branding.xml, značka \<ContentNotInstalledTitle>|
||<META_CONTENT_NOT_INSTALLED_ID_ADD/>|Branding.xml, značka \<ContentNotInstalledDownloadContentText>|
||<CONTENT_NOT_INSTALLED_SECTION_ADD/>|Branding.xml, značka \<ContentNotInstalledText>|

**Soubory CSS**

Balíček nápovědy sady Visual Studio help obsahuje dva soubory CSS pro podporu konzistentní prezentace obsahu nápovědy sady Visual Studio:

- Branding. CSS – obsahuje prvky CSS pro vykreslování, kde SelfBranded = false

- Printer. CSS – obsahuje prvky CSS pro vykreslování, kde SelfBranded = false

Brandingování souborů. CSS zahrnuje definice pro prezentaci tématu sady Visual Studio (upozornění znamená, že branding. CSS obsažený v Branding_ \<locale> . mshc ze služby balíčku se může změnit).

**Grafické soubory**

Visual Studio obsah zobrazí logo Visual Studio i další grafiku.  Úplný seznam grafických souborů v balíčku pro branding Visual Studio Help Viewer je zobrazený níže.

|**Soubor**|**Použití**|**Příklady**|
|-|-|-|
|clear.gif|Slouží k vykreslení sbalitelné oblasti.||
|footer_slice.gif|Prezentace zápatí||
|info_icon.gif|Používá se při zobrazování informací.|Disclaimer|
|online_icon.gif|Tato ikona má být přidružená k online odkazům.||
|tabLeftBD.gif|Slouží k vykreslení kontejneru fragmentu kódu.||
|tabRightBD.gif|Slouží k vykreslení kontejneru fragmentu kódu.||
|vs_logo_bk.gif|Používá se pro odkazy na loga s normálním kontrastem, jak jsou definovány Branding.xml značce \<LogoFileName> .  U Visual Studio produktů je název loga vs_logo_bk.gif.||
|vs_logo_wh.gif|Používá se pro odkazy na loga s vysokým kontrastem, jak jsou definovány Branding.xml značce \<LogoFileNameHC> .  U Visual Studio produktů je název loga vs_logo_wh.gif.||
|ccOff.png|Grafika titulků||
|ccOn.png|Grafika titulků||
|ImageSprite.png|Slouží k vykreslení sbalitelné oblasti.|rozbalená nebo sbalená grafika|

## <a name="deploy-a-set-of-topics"></a>Nasazení sady témat

Toto je jednoduchý a rychlý kurz pro vytvoření sady nasazení obsahu prohlížeče nápovědy, která se skládá ze souboru MSHA a sady souborů CAB nebo MSHC obsahujících témata. MSHA je soubor XML, který popisuje sadu souborů CAB nebo MS BULLETIN. Prohlížeč nápovědy může přečíst MSHA a získat seznam obsahu (.CAB nebo . soubory MS BEZS) k dispozici pro místní instalaci.

Toto je jenom základní popis schématu XML pro pomocníka MSHA.  Pod tímto stručným přehledem a ukázkou souboru HelpContentSetup.msha je ukázková implementace.

Název MSHA je pro účely tohoto základního souboru HelpContentSetup.msha (název souboru může být cokoli, s příponou . MSHA). Soubor HelpContentSetup.msha (příklad níže) by měl obsahovat seznam dostupných souborů CAB nebo MSHC.  Typ souboru musí být konzistentní v rámci MSHA (nepodporuje kombinaci typů souborů MSHA a CAB). Pro každý soubor CAB nebo MS BULLETIN by měl být \<div class="package"> ... \</div> (viz příklad níže).

Poznámka: V následujícím příkladu implementace jsme zahrneme balíček brandingu. To je důležité zahrnout, aby bylo možné získat potřebné Visual Studio vykreslování obsahu a chování obsahu.

Ukázkový soubor HelpContentSetup.msha: (Nahraďte "content set name 1" a "content set name 2" atd. názvy souborů.)

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

1. Vytvořte místní složku, například C:\SampleContent.

2. V tomto příkladu budeme témata obsahovat pomocí souborů MS BULLETIN.  MS BEZE je soubor ZIP s příponou souboru změněnou z .zip na . MS PŘIMT.

3. Vytvořte následující soubor HelpContentSetup.msha jako textový soubor (k vytvoření souboru se použil Poznámkový blok) a uložte ho do výše uvedené složky (viz krok 1).

Třída Branding existuje a je jedinečná. Branding mstc je součástí tohoto základního souboru, takže nainstalovaný obsah bude mít branding a chování obsahu obsažené v MSHC bude mít odpovídající podpůrné prvky obsažené v balíčku brandingu. Bez toho dojde k chybám, když systém hledá položky podpory, které nejsou součástí instalovaných (nainstalovaných) obsahu.

Pokud chcete získat balíček Visual Studio brandingu, zkopírujte do své pracovní složky soubor Branding_en-US.msuser ve složce C:\Program Files (x86)\Microsoft Help Viewer\v2.3\.

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

Použitím a rozšířením výše uvedených kroků umožníte ům, aby můžou můžou nasazovat sady obsahu pro Visual Studio nápovědy.

### <a name="add-help-to-the-visual-studio-shell-integrated-and-isolated"></a>Přidání nápovědy do prostředí Visual Studio Shell (integrované a izolované)

**Úvod**

Tento názorný postup ukazuje, jak začlenit obsah nápovědy do aplikace Visual Studio Shell a pak ho nasadit.

**Požadavky**

1. [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]

2. [Visual Studio 2013 redist izolovaného prostředí](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)

**Přehled**

Prostředí [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] je verze integrovaného vývojového prostředí, [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] na které můžete založit aplikaci. Tyto aplikace obsahují izolované prostředí společně s rozšířeními, která vytvoříte. K sestavení rozšíření použijte šablony projektů izolovaného prostředí, které jsou součástí [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] sady SDK.

Základní kroky pro vytvoření aplikace izolovaného prostředí a její nápovědy:

1. Získejte [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] distribuovatelné součásti ISO Shell (stažení od Microsoftu).

2. V Visual Studio vytvořte rozšíření nápovědy, které je založené na izolovaném prostředí, například rozšíření Nápovědy společnosti Contoso, které je popsáno dále v tomto návodu.

3. Zabalte rozšíření a distribuovatelné součásti ISO Shell do MSI nasazení (nastavení aplikace). Tento názorný postup nezahrnuje krok nastavení.

Vytvořte Visual Studio obsahu. Ve scénáři Integrovaného prostředí změňte Visual Studio12 na název katalogu produktů následujícím způsobem:

- Vytvořte složku C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15.

- Vytvořte soubor s názvem CatalogType.xml a přidejte ho do složky . Soubor by měl obsahovat následující řádky kódu:

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <catalogType>UserManaged</catalogType>
    ```

Definujte úložiště obsahu v registru. Pro Integrované prostředí změňte VisualStudio15 na název katalogu produktů:

- HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15

   Klíč: Hodnota řetězce locationPath: C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15\

- HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15\en-US

   Klíč: Hodnota řetězce CatalogName: [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Dokumentace

**Vytvoření projektu**

Vytvoření rozšíření izolovaného prostředí:

1. V Visual Studio části **Soubor** zvolte Nový **projekt,** v části Jiné **typy** projektů zvolte **Rozšiřitelnost** a pak zvolte Visual Studio prostředí **v izolovaném prostředí.** Pojmete projekt `ContosoHelpShell` ) pro vytvoření projektu rozšiřitelnosti založeného na Visual Studio izolovaného prostředí.

2. V Průzkumník řešení projektu ContosoHelpShellUI ve složce Soubory prostředků otevřete soubor ApplicationCommands.vsct. Ujistěte se, že je tento řádek zakomentovaný (vyhledejte "No_Help"): `<!-- <define name="No_HelpMenuCommands"/> -->`

3. Pomocí klávesy F5 zkompilujte a spusťte **ladění.** V experimentální instanci integrovaného vývojového prostředí izolovaného prostředí zvolte **nabídku** Nápověda. Ujistěte se, že se **zobrazují** **příkazy** Zobrazit nápovědu , Přidat a odebrat obsah nápovědy a Nastavit **předvolby** nápovědy.

4. V Průzkumník řešení projektu ContosHelpShell ve složce Vlastní nastavení prostředí otevřete soubor ContosoHelpShell.pkgdef. Pokud chcete definovat katalog nápovědy společnosti Contoso, přidejte následující řádky:

    ```
     [$RootKey$\Help]
    "Product"="Contoso"
    "Catalog"="Contoso"
    "Version"="100"
    "BrandingPackage"="ContosoBrandingPackage.mshc"
    ```

5. V Průzkumník řešení projektu ContosHelpShell ve složce Vlastní nastavení prostředí otevřete ContosoHelpShell.Application.pkgdef. Pokud chcete povolit nápovědu F1, přidejte následující řádky:

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

6. V Průzkumník řešení místní nabídce řešení ContosoHelpShell zvolte **položku nabídky** Vlastnosti. V **části Vlastnosti** konfigurace vyberte **Správce konfigurace**. Ve **sloupci Konfigurace** změňte každou hodnotu Debug (Ladění) na Release (Vydaná verze).

7. Sestavte řešení. Tím se vytvoří sada souborů ve složce verze, která se použije v další části.

Pokud chcete tento test otestovat, jako by byl nasazený:

1. Na počítač, na který nasazujete Contoso, nainstalujte stažený (z výše uvedeného) prostředí ISO.

2. Vytvořte složku v \\ adresáři \Program Files (x86) a \\ pojmnte ji `Contoso` .

3. Zkopírujte obsah ze složky contosohelpshellové verze do složky \\ \Program Files (x86)\Contoso\.

4. Spusťte Editor registru tak, že v  **nabídce** **Start** zvolíte Spustit a zadáte `Regedit` . V editoru registru zvolte **Soubor a** pak **Importovat.** Přejděte do složky projektu ContosoHelpShell. V podsložce ContosoHelpShell zvolte ContosoHelpShell.reg.

5. Vytvoření úložiště obsahu:

    Prostředí ISO – vytvoření úložiště obsahu Contoso C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\ContosoDev12

    Pro [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Integrované prostředí vytvořte složku C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15.

6. Vytvořte CatalogType.xml a přidejte ho do úložiště obsahu (předchozí krok), které obsahuje:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <catalogType>UserManaged</catalogType>
   ```

7. Přidejte následující klíče registru:

    HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15Key: LocationPath String value:

    Prostředí ISO:

    C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15

    [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Integrované prostředí:

    C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15en-US

    Klíč: CatalogName String value: [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Dokumentace. V případě prostředí ISO je to název vašeho katalogu.

8. Zkopírujte svůj obsah (cabs nebo MSKOPÍRUJe a MSHA) do místní složky.

9. Příklad příkazového řádku Integrovaného prostředí pro testování úložiště obsahu V případě prostředí ISO změňte hodnoty catalog a launchingApp tak, aby odpovídaly produktu.

     "C:\Program Files (x86)\Microsoft Help Viewer\v2.3\HlpViewer.exe" /catalogName VisualStudio15 /helpQuery method="page&id=ContosoTopic0" /launchingApp Microsoft,VisualStudio,12.0

10. Spusťte aplikaci Contoso (z kořenového adresáře aplikace Contoso). V prostředí ISO zvolte položku **nabídky Nápověda** a změňte Nastavení **předvolby nápovědy** na **Použít místní nápovědu.**

11. V prostředí zvolte položku nabídky **Nápověda** a pak **Zobrazit nápovědu.** Měl by se spustit místní prohlížeč nápovědy. Zvolte kartu **Spravovat** obsah. V **části Zdroj** instalace zvolte tlačítko **možnosti** Disk. Zvolte **tlačítko ...** a přejděte do místní složky obsahující obsah společnosti Contoso (zkopírované do místní složky v kroku výše). Zvolte Soubor HelpContentSetup.msha. Společnost Contoso by se teď měla ve výběru knihy zobrazit jako kniha. Zvolte **Přidat** a pak zvolte **tlačítko Aktualizovat** (v pravém dolním rohu).

12. V integrovaném vývojovém prostředí Společnosti Contoso zvolte klávesu F1 a otestujte funkčnost F1.

## <a name="additional-resources"></a>Další zdroje informací

Informace o rozhraní RUNTIME API najdete v tématu [Rozhraní API nápovědy systému Windows.](/previous-versions/windows/desktop/helpapi/helpapi-portal)

Další informace o tom, jak využít rozhraní API nápovědy, najdete v tématu [Příklady kódu Help Viewer.](https://marketplace.visualstudio.com/items?itemName=RobChandlerHelpMVP.HelpViewer20CodeExamples)

Návrhy funkcí můžete odeslat na [Developer Community](https://aka.ms/feedback/suggest?space=8).
