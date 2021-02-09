---
title: Sada Microsoft Help Viewer SDK | Microsoft Docs
description: Přečtěte si informace o úlohách aplikace Visual Studio Help Viewer, jako je vytvoření článku, vytvoření balíčku obsahu brandingu pro aplikaci Help Viewer a nasazení sady článků.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 620d7dcd-d462-475e-a449-fbfa06ff12c5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2e7b2c8d5f194287f0b654184ddd8716f248ca36
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895749"
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

- Chování obsahu (příklady zahrnují rozbalení/sbalení ovládacích prvků textu a prvky fragmentu kódu)

- Prvky zápatí (příklad autorského práva)

K položkám, které se považují za značky, patří (podrobné v této specifikaci):

- Logo pro katalog/produkt (například Visual Studio)

- Odkaz na zpětnou vazbu a e-mailové prvky

- Text právního omezení

- Text copyrightu

Podpůrné soubory v aplikaci Visual Studio Help Viewer – balíček obsahuje:

- Grafika (loga, ikony atd.)

- Soubory skriptu Branding.js podporující chování obsahu

- Branding.xml – řetězce, které se konzistentně používají v rámci obsahu katalogu.  Poznámka: pro prvky lokalizace textu v rámci sady Visual Studio v branding.xml přidejte _locID = " \<unique value> ".

- Branding. CSS – definice stylů pro konzistenci prezentace

- Tisk. CSS – definice stylů pro konzistentní tištěnou prezentaci

Jak je uvedeno výše, balíčky branding jsou spojené s tématem:

- Pokud jsou v metadatech definované SelfBranded = false, téma zdědí balíček brandingu katalogu.

- Nebo pokud je SelfBranded = false a v MSHA je definovaný jedinečný balíček brandingu a dostupný při instalaci obsahu

Pro VSPs implementující vlastní balíčky brandingu (obsah VSP, SelfBranded = true) je možné pokračovat, pokud chcete začít s záložním balíčkem branding (nainstalovaným v aplikaci Help Viewer) a podle potřeby změnit název souboru.  Soubor Branding_ \<locale> . mshc je soubor zip s příponou souboru, který se změnil na. mshc, takže jednoduše změňte příponu z. mshc na. zip a extrahujte obsah.  Níže najdete informace o brandingu prvků balíčku a podle potřeby je upravte (například můžete změnit logo na logo VSP a odkaz na logo v souboru Branding.xml, aktualizovat Branding.xml na základě standardu VSP atd.).

Po dokončení všech úprav vytvořte soubor ZIP obsahující požadované prvky brandingu a změňte rozšíření na. mshc.

K přidružení vlastního balíčku brandingu vytvořte MSHA, který obsahuje odkaz na soubor mshc brandingu spolu s obsahem mshc (obsahujícím témata).  Postup vytvoření základní MSHA najdete pod textem "MSHA".

Branding.xml soubor obsahuje seznam prvků, které se používají pro konzistentní vykreslování konkrétních položek v tématu, když téma obsahuje \<meta name="Microsoft.Help.SelfBranded" content="false"/> .  Seznam prvků sady Visual Studio v souboru Branding.xml je uveden níže.  Tento seznam je určený k použití jako šablona pro přijímání prostředí ISO Shell, kde tyto prvky (například logo, zpětná vazba a copyright) upraví tak, aby splňovaly vlastní požadavky na značku produktu.

Poznámka: proměnné zaznamenané "{n}" mají závislosti kódu – odebrání nebo změna těchto hodnot způsobí chyby a možnou chybu aplikace. Identifikátory lokalizace (například _locID = "codesnippet. n") jsou součástí balíčku branding sady Visual Studio.

**Branding.xml**

| Element | Popis |
| - | - |
| Zapnut | **CollapsibleArea** |
| Použije | Rozbalit sbalí text ovládacího prvku obsahu. |
| **Prvek** | **Hodnota** |
| ExpandText | Rozbalit |
| CollapseText | Sbalit |
| Zapnut | **CodeSnippet** |
| Použije | Text ovládacího prvku fragmentu kódu  Poznámka: obsah fragmentu kódu s "neprůlomovým" místem bude změněn na mezeru. |
| **Prvek** | **Hodnota** |
| CopyToClipboard | Kopírovat do schránky |
| ViewColorizedText | Zobrazit barevné barvy |
| CombinedVBTabDisplayLanguage | Visual Basic (ukázka) |
| VBDeclaration | Deklarace |
| VBUsage | Využití |
| Zapnut | **Zpětná vazba, zápatí a logo** |
| Použije | Poskytněte řízení zpětné vazby zákazníkovi, aby vám poskytl zpětnou vazbu k aktuálnímu tématu prostřednictvím e-mailu.  Text copyrightu pro obsah  Definice loga. |
| **Prvek** | **Hodnota (tyto řetězce lze upravit tak, aby splňovala požadavky na přijetí obsahu.)** |
| Úprava | © 2013 Microsoft Corporation. All rights reserved. |
| SendFeedback | \<a href="{0}" {1}>Pošlete nám svůj názor \</a> na toto téma společnosti Microsoft. |
| FeedbackLink | |
| LogoTitle | [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] |
| LogoFileName | vs_logo_bk.gif |
| LogoFileNameHC | vs_logo_wh.gif |
| Zapnut | **Právní omezení** |
| Použije | Sada omezení specifických pro velká a malá písmena pro Strojově přeložený obsah. |
| **Prvek** | **Hodnota** |
| MT_Editable | Tento článek byl Strojově přeložený. Pokud máte připojení k Internetu, zvolte "zobrazit toto téma online" pro zobrazení této stránky v upravitelném režimu spolu s původním anglickým obsahem. |
| MT_NonEditable | Tento článek byl Strojově přeložený. Pokud máte připojení k Internetu, zvolte "zobrazit toto téma online" pro zobrazení této stránky v upravitelném režimu spolu s původním anglickým obsahem. |
| MT_QualityEditable | Tento článek byl přeložen ručně. Pokud máte připojení k Internetu, zvolte "zobrazit toto téma online" pro zobrazení této stránky v upravitelném režimu spolu s původním anglickým obsahem. |
| MT_QualityNonEditable | Tento článek byl přeložen ručně. Pokud máte připojení k Internetu, zvolte "zobrazit toto téma online" pro zobrazení této stránky v upravitelném režimu spolu s původním anglickým obsahem. |
| MT_BetaContents | Tento článek byl STROJOVĚ PŘELOŽEN pro předběžnou verzi. Pokud máte připojení k Internetu, zvolte "zobrazit toto téma online" pro zobrazení této stránky v upravitelném režimu spolu s původním anglickým obsahem. |
| MT_BetaRecycledContents | Tento článek byl ručně přeložen pro předběžnou verzi. Pokud máte připojení k Internetu, zvolte "zobrazit toto téma online" pro zobrazení této stránky v upravitelném režimu spolu s původním anglickým obsahem. |
| Zapnut | **Propojování** |
| Použije | Podpora pro online odkazy na témata |
| **Prvek** | **Hodnota** |
| LinkTableTitle | Propojit tabulku |
| TopicEnuLinkText | Zobrazit anglickou verzi \</a> tohoto tématu, která je k dispozici ve vašem počítači. |
| TopicOnlineLinkText | Zobrazit toto téma \<a href="{0}" {1}> online\</a> |
| OnlineText | Online |
| Zapnut | **Ovládací prvek zvuk videa** |
| Použije | Zobrazit elementy a text pro obsah videa |
| **Prvek** | **Hodnota** |
| MultiMediaNotSupported | Pro podporu obsahu je třeba nainstalovat aplikaci Internet Explorer 9 nebo vyšší {0} . |
| VideoText | zobrazení videa |
| AudioText | streamování zvuku |
| OnlineVideoLinkText | \<p>Pokud chcete zobrazit video spojené s tímto tématem, klikněte {0} \<a href="{1}"> {2} sem \</a> .\</p> |
| OnlineAudioLinkText | \<p>Pokud chcete naslouchat zvukovému programu přidruženému k tomuto tématu, klikněte {0} \<a href="{1}"> {2} sem \</a> .\</p> |
| Zapnut | **Ovládací prvek nenainstalovaného obsahu** |
| Použije | Textové prvky (řetězce) používané pro vykreslování contentnotinstalled.htm |
| **Prvek** | **Hodnota** |
| ContentNotInstalledTitle | V počítači nebyl nalezen žádný obsah. |
| ContentNotInstalledDownloadContentText | \<p>Chcete-li stáhnout obsah do vašeho počítače, \<a href="{0}" {1}> klikněte na kartu spravovat \</a> .\</p> |
| ContentNotInstalledText | \<p>V počítači není nainstalován žádný obsah. Prohlédněte si správce pro místní instalaci obsahu aplikace.\</p> |
| Zapnut | **Nebylo nalezeno řízení tématu.** |
| Použije | Textové prvky (řetězce) používané pro vykreslování topicnotfound.htm |
| **Prvek** | **Hodnota** |
| TopicNotFoundTitle | V počítači nelze najít požadované téma. |
| TopicNotFoundViewOnlineText | \<p>Téma, které jste požadovali, nebylo v počítači nalezeno, ale můžete \<a href="{0}" {1}> Zobrazit téma online \</a> .\</p> |
| TopicNotFoundDownloadContentText | \<p>V navigačním podokně najdete odkazy na podobná témata nebo \<a href="{0}" {1}> klikněte na kartu spravovat a \</a> Stáhněte obsah do svého počítače.\</p> |
| TopicNotFoundText | \<p>Téma, které jste požadovali, nebylo v počítači nalezeno.\</p> |
| Zapnut | **Téma má poškozený ovládací prvek.** |
| Použije | Textové prvky (řetězce) používané pro vykreslování topiccorrupted.htm |
| **Prvek** | **Hodnota** |
| TopicCorruptedTitle | Nelze zobrazit požadované téma. |
| TopicCorruptedViewOnlineText | \<p>Nástroj Help Viewer nemůže zobrazit požadované téma. Může se jednat o chybu v obsahu tématu nebo o základní systémové závislosti.\</p> |
| Zapnut | **Ovládací prvek domovské stránky** |
| Použije | Text, který podporuje zobrazení obsahu uzlu nejvyšší úrovně aplikace Help Viewer. |
| **Prvek** | **Hodnota** |
| HomePageTitle | Domovská stránka prohlížeče nápovědy |
| HomePageIntroduction | \<p>Vítá vás Microsoft Help Viewer, což je důležitý zdroj informací pro všechny uživatele, kteří používají nástroje, produkty, technologie a služby společnosti Microsoft. V aplikaci Help Viewer získáte přístup k odkazům na postupy a referenční informace, vzorový kód, technické články a další. Pokud chcete najít potřebný obsah, Projděte si obsah, používejte fulltextové vyhledávání, nebo procházejte obsahem pomocí klíčového slova index.\</p> |
| HomePageContentInstallText | \<p>\<br />Pomocí \<a href="{0}" {1}> karty spravovat obsah \</a> můžete provést následující akce: \<ul> \<li> Přidat obsah do počítače. \</li> \<li> Vyhledejte aktualizace místního obsahu. \</li> \<li> Odeberte obsah z počítače.\</li>\</ul>\</p> |
| HomePageInstalledBooks | Nainstalované knihy |
| HomePageNoBooksInstalled | V počítači nebyl nalezen žádný obsah. |
| HomePageHelpSettings | Nastavení obsahu Help |
| HomePageHelpSettingsText | \<p>Aktuálním nastavením je místní nápovědě. V aplikaci Help Viewer je zobrazen obsah, který jste nainstalovali v počítači. \<br /> Chcete-li změnit zdroj obsahu aplikace, klikněte na panelu nabídek aplikace Visual Studio na tlačítko \<span style="{0}"> help (nastavit předvolby) \</span> .\<br />\</p> |
| Megabajt | MB |

**branding.js**

branding.js soubor obsahuje jazyk JavaScript, který používají prvky nápovědy aplikace Visual Studio pro branding.  Níže je uveden seznam prvků brandingu a podpůrná funkce JavaScriptu.  Všechny řetězce, které mají být lokalizovány pro tento soubor, jsou definovány v části "lokalizovatelné řetězce" v horní části tohoto souboru.  V souboru branding.js byl vytvořen soubor ICL pro řetězce Loc.

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

Obsah sady Visual Studio zobrazuje logo Visual studia i další grafiku.  Úplný seznam grafických souborů v balíčku nápovědy aplikace Visual Studio Help Viewer je uveden níže.

|**Soubor**|**Použití**|**Příklady**|
|-|-|-|
|clear.gif|Slouží k vykreslení sbalitelné oblasti.||
|footer_slice.gif|Prezentace zápatí||
|info_icon.gif|Používá se při zobrazování informací.|Disclaimer|
|online_icon.gif|Tato ikona má být přidružena k online odkazům.||
|tabLeftBD.gif|Slouží k vykreslení kontejneru fragmentů kódu||
|tabRightBD.gif|Slouží k vykreslení kontejneru fragmentů kódu||
|vs_logo_bk.gif|Používá se k odkazům na symbol normálního kontrastu, jak jsou definovány v Branding.xml značce \<LogoFileName> .  Pro Visual Studio Products se vs_logo_bk.gif název loga.||
|vs_logo_wh.gif|Používá se pro normální odkazy na loga, jak jsou definované ve značce Branding.xml \<LogoFileNameHC> .  Pro Visual Studio Products se vs_logo_wh.gif název loga.||
|ccOff.png|Grafika titulků||
|ccOn.png|Grafika titulků||
|ImageSprite.png|Slouží k vykreslení sbalitelné oblasti.|Rozbalení nebo sbalení grafiky|

## <a name="deploy-a-set-of-topics"></a>Nasazení sady témat

Toto je jednoduchý a rychlý kurz pro vytvoření sady pro nasazení obsahu aplikace Help Viewer sestávající ze souboru MSHA a sady kabin nebo MSHCs obsahující témata. MSHA je soubor XML, který popisuje sadu souborů CAB nebo MSHC. Aplikace Help Viewer může přečíst MSHA a získat tak seznam obsahu (. CAB nebo. Soubory MSHC) k dispozici pro místní instalaci.

Toto je pouze Úvod popisující základní schéma XML pro MSHA Help Viewer.  Níže najdete příklad implementace pod tímto stručným přehledem a ukázkou Sample HelpContentSetup. msha.

Název MSHA pro účely tohoto úvodu je HelpContentSetup. msha (název souboru může být cokoli s příponou. MSHA). HelpContentSetup. msha (příklad níže) by měl obsahovat seznam souborů CAB a MSHCs, které jsou k dispozici.  Typ souboru musí být konzistentní v rámci MSHA (nepodporuje kombinaci typů souborů MSHA a CAB). Pro každý soubor CAB nebo mshc by měl být \<div class="package"> ... \</div> (viz příklad níže).

Poznámka: v následujícím příkladu implementace jsme zahrnuli balíček brandingu. To je důležité zahrnout, aby bylo možné získat potřebné prvky pro vykreslování obsahu sady Visual Studio a chování obsahu.

Ukázkový soubor HelpContentSetup. msha: (nahraďte "název sady obsahu 1" a "název sady obsahu 2" atd. s názvy souborů.)

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

1. Vytvořte místní složku, například "C:\SampleContent".

2. V tomto příkladu použijeme soubory MSHC k tomu, aby obsahovaly témata.  MSHC je zip s příponou souboru, která se změnila z. zip na. MSHC.

3. Vytvořte následující HelpContentSetup. msha jako textový soubor (pomocí programu Poznámkový blok byl použit k vytvoření souboru) a uložte ho do výše uvedené složky (viz krok 1).

Třída "Brandinging" existuje a je jedinečná. Značka mshc je součástí tohoto úvodního nástroje, aby měl nainstalovaný obsah branding, a chování obsahu, které jsou obsaženy v MSHCs, bude obsahovat příslušné podpůrné prvky obsažené v balíčku branding. Bez tohoto výsledku dojde k chybám, když systém vyhledá položky podpory, které nejsou součástí zkopírovaného (instalovaného) obsahu.

Chcete-li získat balíček branding sady Visual Studio, zkopírujte soubor Branding_en-US. mshc ve složce C:\Program Files (x86) \Microsoft Help Viewer\v2.3\ do vaší pracovní složky.

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

Použití a rozšíření výše uvedených kroků umožní VSPs nasazení svých sad obsahu pro aplikaci Visual Studio Help Viewer.

### <a name="add-help-to-the-visual-studio-shell-integrated-and-isolated"></a>Přidat Help do prostředí sady Visual Studio (integrovaný a izolovaný režim)

**Úvod**

Tento návod ukazuje, jak začlenit obsah v nápovědě do aplikace prostředí sady Visual Studio a jak ho nasadit.

**Požadavky**

1. [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]

2. [Visual Studio 2013 Redist izolovaného prostředí](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)

**Přehled**

[!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]Prostředí je verze [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] integrovaného vývojového prostředí (IDE), na které můžete aplikaci založit. Takové aplikace obsahují izolované prostředí spolu s rozšířeními, která vytvoříte. Pro sestavení rozšíření použijte šablony projektů izolovaného prostředí, které jsou součástí [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] sady SDK.

Základní kroky pro vytvoření aplikace založené na izolovaném prostředí a její nápovědě:

1. Získejte [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Distribuovatelný modul ISO Shell (stažení od Microsoftu).

2. V aplikaci Visual Studio vytvořte rozšíření pro nápovědu, které je založené na izolovaném prostředí, například rozšíření Help společnosti Contoso popsané dále v tomto návodu.

3. Zabalte rozšíření a distribuovatelné prostředí ISO do balíčku MSI nasazení (instalace aplikace). Tento návod nezahrnuje krok nastavení.

Vytvořte si úložiště obsahu v aplikaci Visual Studio. V případě integrovaného scénáře prostředí změňte Visual Studio12 na název katalogu produktů následujícím způsobem:

- Vytvořit složku C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15.

- Vytvořte soubor s názvem CatalogType.xml a přidejte ho do složky. Soubor by měl obsahovat následující řádky kódu:

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <catalogType>UserManaged</catalogType>
    ```

Definujte úložiště obsahu v registru. V případě integrovaného prostředí změňte VisualStudio15 na název katalogu produktů:

- HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15

   Klíč: hodnota řetězce LocationPath: C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15\

- HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15\en-US

   Key: hodnota řetězce v katalogu: [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] dokumentace

**Vytvoření projektu**

Vytvoření rozšíření izolovaného prostředí:

1. V aplikaci Visual Studio v **části soubor** zvolte možnost **Nový projekt**, v části **ostatní typy projektů** zvolte možnost **rozšiřitelnost** a pak zvolte možnost  **prostředí Visual Studio izolované**. Pojmenujte projekt `ContosoHelpShell` ), chcete-li vytvořit projekt rozšiřitelnosti na základě šablony izolovaného prostředí sady Visual Studio.

2. V Průzkumník řešení v projektu ContosoHelpShellUI ve složce soubory prostředků otevřete ApplicationCommands. vsct. Ujistěte se, že je tento řádek zakomentováný (vyhledejte "No_Help"): `<!-- <define name="No_HelpMenuCommands"/> -->`

3. Pro zkompilování a spuštění **ladění** použijte klávesu F5. V experimentální instanci rozhraní IDE izolovaného prostředí klikněte na nabídku **help** . Zajistěte, aby se zobrazily příkazy pro **zobrazení**, **Přidání a odebrání obsahu** a **Nastavení** v nápovědě.

4. V Průzkumník řešení v projektu ContosHelpShell ve složce pro přizpůsobení prostředí otevřete ContosoHelpShell. pkgdef. Chcete-li definovat katalog nápovědě společnosti Contoso, přidejte následující řádky:

    ```
     [$RootKey$\Help]
    "Product"="Contoso"
    "Catalog"="Contoso"
    "Version"="100"
    "BrandingPackage"="ContosoBrandingPackage.mshc"
    ```

5. V Průzkumník řešení v projektu ContosHelpShell otevřete ve složce pro přizpůsobení prostředí položku ContosoHelpShell. Application. pkgdef. Chcete-li povolit nápovědu pro klávesu F1, přidejte následující řádky:

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

6. V Průzkumník řešení v kontextové nabídce řešení ContosoHelpShell vyberte položku nabídky **vlastnosti** . V části **Vlastnosti konfigurace** vyberte **Configuration Manager**. Ve sloupci **Konfigurace** změňte všechny hodnoty "ladit" na "Release".

7. Sestavte řešení. Tím se vytvoří sada souborů ve složce verze, která se použije v další části.

Chcete-li tento test otestovat, jako kdyby byl nasazen:

1. Na počítači, do kterého nasazujete contoso, nainstalujte stažený (z výše uvedeného) prostředí ISO Shell.

2. Vytvořte složku ve složce \\ \Program Files (x86) \\ a pojmenujte ji `Contoso` .

3. Zkopírujte obsah ze složky verze ContosoHelpShell do \\ složky \Program Files (x86) \Contoso\.

4. Spusťte Editor registru výběrem možnosti  **Spustit** v nabídce **Start** a zadáním příkazu `Regedit` . V editoru registru zvolte možnost **soubor** a pak položku **importovat**. Přejděte do složky projektu ContosoHelpShell. V podsložce ContosoHelpShell vyberte ContosoHelpShell. reg.

5. Vytvořit úložiště obsahu:

    Pro prostředí ISO Shell – vytvoření C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\ContosoDev12 úložiště obsahu společnosti Contoso

    V případě [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] integrovaného prostředí vytvořte složku C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15.

6. Vytvořte CatalogType.xml a přidejte je do úložiště obsahu (předchozí krok) obsahující:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <catalogType>UserManaged</catalogType>
   ```

7. Přidejte následující klíče registru:

    HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15Key: hodnota řetězce LocationPath:

    Pro prostředí ISO Shell:

    C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15

    [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Integrované prostředí:

    C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15en-US

    Key: hodnota řetězce v katalogu: [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] dokumentace Pro prostředí ISO Shell se jedná o název vašeho katalogu.

8. Zkopírujte obsah (kabiny nebo MSHC a MSHA) do místní složky.

9. Příklad integrovaného příkazového řádku prostředí pro testování úložiště obsahu. Pro prostředí ISO změňte podle potřeby hodnoty Catalog a launchingApp, aby odpovídaly produktu.

     "C:\Program Files (x86) \Microsoft Help Viewer\v2.3\HlpViewer.exe"/catalogName VisualStudio15/helpQuery Method = "Page&ID = ContosoTopic0"/launchingApp Microsoft, VisualStudio, 12.0

10. Spusťte aplikaci Contoso (z kořenového adresáře aplikace Contoso). V prostředí ISO Shell vyberte položku nabídky **help** a změňte **Předvolby Ponápovědě** pro **použití místní** aplikace.

11. V prostředí zvolte položku nabídky **help** a pak **Zobrazte Help**. Měl by se spustit místní prohlížeč nápovědy. Klikněte na kartu **Spravovat obsah** . V části **zdroj instalace** klikněte na tlačítko možnosti **disku** . Klikněte na tlačítko **...** a přejděte do místní složky obsahující obsah společnosti Contoso (zkopírované do místní složky ve výše uvedeném kroku). Vyberte HelpContentSetup. msha. Contoso by se teď měl zobrazit jako kniha v výběrech knihy. Zvolte **Přidat** a pak klikněte na tlačítko **aktualizovat** (pravý dolní roh).

12. V integrovaném vývojovém prostředí společnosti Contoso vyberte klávesu F1 pro otestování funkcí F1.

## <a name="additional-resources"></a>Další zdroje informací

Rozhraní API pro modul runtime najdete v tématu [rozhraní API pro Windows Help](/previous-versions/windows/desktop/helpapi/helpapi-portal).

Další informace o tom, jak využít rozhraní API pro nápovědu, najdete v tématu [Příklady kódu pro Help Viewer](https://marketplace.visualstudio.com/items?itemName=RobChandlerHelpMVP.HelpViewer20CodeExamples).

Návrhy funkcí můžete odeslat [komunitě vývojářů](https://aka.ms/feedback/suggest?space=8).
