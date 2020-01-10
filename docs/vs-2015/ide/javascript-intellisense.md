---
title: JavaScript IntelliSense | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense [JavaScript]
- <reference> JavaScript XML tag
- JavaScript Code Editor
- XML code comments, JavaScript IntelliSense
- reference JavaScript XML tag
- JavaScript, IntelliSense
- code comments, JavaScript IntelliSense
- JavaScript, reference groups
- JavaScript Editor
- reference directives [JavaScript]
- JavaScript, XML documentation comments
- reference groups [JavaScript]
- JavaScript, reference directives
- IntelliSense [JavaScript], about
- IntelliSense extensibility [JavaScript]
- XML documentation comments [JavaScript]
ms.assetid: af1a3171-c9d8-45a3-9c96-a763e3b163ef
caps.latest.revision: 67
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 962c724e231275c9fa716d6c823b7451292392cf
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75848388"
---
# <a name="javascript-intellisense"></a>JavaScript IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Technologie IntelliSense umožňuje napsat kód rychleji a s menším množstvím chyb poskytnutím informací při kódování. Při práci s klientským skriptem v editoru jazyka JavaScript technologie IntelliSense zobrazí seznam objektů, funkcí, vlastností a parametrů, které jsou k dispozici podle aktuálního kontextu. Ze seznamu místní nabídky technologie IntelliSense můžete vybrat možnost kódování a kód dokončit.

 Technologie IntelliSense usnadňuje provádění následujících úkonů:

- Vyhledání informací o členech

- Vložení prvků jazyka přímo do kódu

- Údržba kódu bez odejití z editoru kódu

- Podpora vlastní technologie IntelliSense s dokumentačními komentáři XML a rozšířením technologie IntelliSense jazyka JavaScript

  Toto téma obsahuje následující oddíly:

- [Určení kontextu IntelliSense](#DeterminingIntelliSenseContext)

- [Zpracování informací technologie IntelliSense](#ProcessingIntelliSenseInformation)

- [JavaScript – funkce technologie IntelliSense](#Features)

- [Rozšiřitelnost technologie IntelliSense pro JavaScript](#Extensibility)

- [Ověřování JavaScriptu](#Validation)

  Další informace o funkcích technologie IntelliSense [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]naleznete v tématu [Using IntelliSense](../ide/using-intellisense.md).

## <a name="DeterminingIntelliSenseContext"></a>Určení kontextu IntelliSense
 Technologie IntelliSense jazyka JavaScript poskytuje možnosti kódování na základě veškerého skriptu, který je relevantní pro váš aktuální skriptovací kontext. To zahrnuje skriptovací prvky v aktuálním souboru. Patří sem také jakýkoli kód, na který váš skript odkazuje přímo nebo nepřímo, například odkazy na soubor skriptu, odkazy na skript sestavení, odkazy na služby a odkazy související se stránkami.

 Aktuální kontext skriptu je vytvořen na základě následujících položek:

- Funkce, které jsou definovány ve všech blocích skriptu v aktivním dokumentu. Vložené bloky kódu skriptu jsou podporovány v souborech, které mají přípony názvu souboru .aspx., .ascx, .master, .html a .htm.

- `script` prvky s atributy `src`, které odkazují na jiný soubor skriptu. Cílový soubor skriptu musí mít příponu názvu souboru .js.

- JavaScriptové soubory, které odkazují na jiné soubory JavaScriptu pomocí direktivy `reference`.

- Referenční skupiny pro globální objekty, rozšíření technologie IntelliSense nebo soubory skriptů pro načtení zpoždění.

- Odkazy na webové služby XML

- Ovládací prvky <xref:System.Web.UI.ScriptManager> a <xref:System.Web.UI.ScriptManagerProxy>, pokud webová aplikace je ASP.NET aplikace s podporou jazyka AJAX.

- [!INCLUDE[atlaslib_current_ext](../includes/atlaslib-current-ext-md.md)], pokud pracujete v ASP.NET webové aplikaci s podporou AJAX.

    > [!NOTE]
    > Technologie IntelliSense není podporována pro skript, který je v atributech obslužných rutin událostí v prvcích HTML nebo který je definován v `href` atributy.

## <a name="ProcessingIntelliSenseInformation"></a>Zpracování informací technologie IntelliSense
 Aby služba jazyka JavaScript mohla poskytovat technologii IntelliSense, provádí následující operace:

- Vytvoří seznam závislých souborů jazyka JavaScript, které jsou založené na odkazech v aktivním dokumentu a na opakovaném zkoumání odkazů skriptu v odkazovaných souborech.

- Projde seznam a z každého souboru shromáždí informace o typu a další relevantní data.

- Agreguje data a předá je službě jazyka JavaScript, která informace o typu a data zpřístupňuje technologii IntelliSense.

- Sleduje změny v souborech, které by mohly ovlivnit seznam technologie IntelliSense, a podle potřeby seznam aktualizuje. Skripty na vzdálených úložištích (například skripty odkazované pomocí HTTP) monitorovány nejsou.

## <a name="Features"></a>JavaScript – funkce technologie IntelliSense
 Technologie IntelliSense jazyka JavaScript podporuje následující objekty:

- [Prvky model DOM (Document Object Model) (DOM)](#HTMLDom)

- [Vnitřní objekty](#IntrinsicObjects)

- [Uživatelem definované proměnné, funkce a objekty](#UserDefined)

- Objekty definované v externích souborech pomocí odkazů, jako jsou [odkazy skriptu](#Script), [direktivy odkazů](#ReferenceDirectives)a [referenční skupiny](#ReferenceGroups).

- Objekty definované ve vzdálených souborech stažených pomocí sady Visual Studio.

- Objekty zadané v [dokumentačních komentářích XML](#XMLDocComments), jako jsou parametry a pole.

- Objekty, které jsou popsány pomocí standardních značek komentářů jazyka JavaScript (/ /). Další informace najdete v tématu [rozšíření JavaScriptu IntelliSense](../ide/extending-javascript-intellisense.md).

- Objekty podporované pomocí mechanismu [rozšiřitelnosti JavaScriptu technologie IntelliSense](#Extensibility) . Další informace najdete v tématu [rozšíření JavaScriptu IntelliSense](../ide/extending-javascript-intellisense.md).

- [ASP.NET AJAX objekty](#ASPNet)

  Pokud technologie IntelliSense nedokáže určit typ objektu, poskytuje možnosti pro doplňování výrazů pomocí identifikátorů v aktivním dokumentu. Další informace najdete v tématu [dokončování příkazů pro identifikátory](../ide/statement-completion-for-identifiers.md).

### <a name="HTMLDom"></a>HTML elementy DOM
 Technologie IntelliSense jazyka JavaScript poskytuje programovací odkazy pro elementy dynamického HTML (DHTML) modelu DOM, například `body`, `form`a `div`. Technologie IntelliSense zobrazuje pouze prvky, které jsou obsaženy v aktuálním dokumentu a na hlavní stránce. JavaScript IntelliSense také podporuje objekty `window` a `document` a jejich členy.

### <a name="IntrinsicObjects"></a>Vnitřní objekty
 Technologie IntelliSense jazyka JavaScript poskytuje programovací odkazy pro vnitřní objekty, jako jsou `Array`, `String`, `Math`, `Date`a `Number`. Další informace o vnitřních objektech naleznete v tématu [standardní předdefinované objekty](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects).

### <a name="UserDefined"></a>Uživatelem definované proměnné, funkce a objekty
 Když změníte soubor JavaScriptu, [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] prověřování otevřených a odkazovaných dokumentů k určení všech dostupných prostředků kódu. To zahrnuje proměnné, funkce a objekty, které jste vytvořili. Tyto prostředky jsou pak k dispozici technologii IntelliSense jazyka JavaScript.

 Další informace o uživatelem definovaných proměnných, funkcích a objektech naleznete v tématu [vytváření vlastních objektů](https://msdn.microsoft.com/library/202863ha.aspx) na webu MSDN.

### <a name="External"></a>Odkazy na externí soubory
 Můžete zahrnout různé typy odkazů na externí soubory, které má technologie IntelliSense ve vašem kódu podporovat. Odkazy na externí soubory mohou být odkazy skriptu, direktivy odkazů nebo mohou být určeny pomocí referenčních skupin.

#### <a name="Script"></a>Odkazy na skripty
 Místo psaní celého klientského skriptu na stránce můžete odkazovat na externí soubory, které obsahují kód skriptu. To usnadňuje opětovné použití kódu mezi stránkami a umožňuje ukládání klientského skriptu do mezipaměti prohlížeče.

 Pokud nepracujete s webovou stránkou s podporou AJAX ASP.NET, můžete odkazovat na externí soubor skriptu pomocí atributu `src` v otevírací značce `script` elementu. Atribut `src` Určuje adresu URL externího souboru, který obsahuje zdrojový kód nebo data.

 Následující příklad ukazuje značky, které používají atribut `src` v <`script`značky > pro odkazování na soubor skriptu.

```html
<script type="text/javascript" src="~/Scripts/JavaScript.js">

</script>
```

 Pokud pracujete s webovou stránkou s podporou AJAX ASP.NET, můžete odkazovat soubory skriptu pomocí objektu <xref:System.Web.UI.ScriptReference> ovládacího prvku <xref:System.Web.UI.ScriptManager>.

 Následující příklad ukazuje značky, které používají objekt <xref:System.Web.UI.ScriptReference> v ovládacím prvku <xref:System.Web.UI.ScriptManager> pro odkazování na soubor skriptu.

```html
<asp:ScriptManager ID="ScriptManager1" runat="server">
  <Scripts>
    <asp:ScriptReference Path="~/Scripts/JavaScript.js" />
  </Scripts>
</asp:ScriptManager>
```

 Technologie IntelliSense také podporuje soubory skriptu, které jsou vloženy jako prostředky v sestavení ve webových aplikacích technologie ASP.NET AJAX. Další informace o prostředcích vloženého skriptu naleznete v tématu [Návod: vložení souboru JavaScriptu jako prostředku v sestavení](https://msdn.microsoft.com/library/d8cb78cd-95a9-4dc6-92df-391866817e89).

#### <a name="ReferenceDirectives"></a>Direktivy Reference
 Direktiva `reference` umožňuje [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] vytvořit relaci mezi právě upravovaným skriptem a jinými skripty. Direktiva `reference` umožňuje zahrnout soubor skriptu do kontextu skriptování aktuálního souboru skriptu. Technologie IntelliSense tak může při kódování odkazovat na externě definované funkce, typy a pole.

 Direktivu `reference` vytvoříte ve formě komentáře XML. Direktiva musí být deklarována v souboru dříve než jakýkoli skript. Direktiva `reference` může zahrnovat odkaz na skript na základě disku, odkaz na skript na základě sestavení, odkaz na skript na základě služby nebo odkaz na skript na základě stránky.

 Následující příklad ukazuje příklady použití direktiv odkazu na skript na základě disku. V prvním příkladu služba jazyka vyhledá soubor ve stejné složce, která obsahuje soubor projektu (například .jsproj).

 `/// <reference path="ScriptFile1.js" />`

 `/// <reference path="Scripts/ScriptFile2.js" />`

 `/// <reference path="../ScriptFile3.js" />`

 `/// <reference path="~/Scripts/ScriptFile4.js" />`

 Následující příklad ukazuje způsob vytvoření odkazu na skript na základě sestavení.

 `/// <reference name "Ajax.js" assembly="System.Web.Extensions, ..." />`

 Následující příklad ukazuje způsob vytvoření odkazu na skript na základě služby:

 `/// <reference path="MyService.asmx" />`

 `/// <reference path="Services/MyService.asmx" />`

 `/// <reference path="../MyService.asmx" />`

 `/// <reference path="~/Services/MyService.asmx" />`

> [!NOTE]
> Technologie IntelliSense jazyka JavaScript není podporována pro skript, který je obsažen v souborech webové služby (.asmx) v projektech webových aplikací (WAP).

 Následující příklad ukazuje způsob vytvoření odkazu na skript na základě stránky.

 `/// <reference path="Default.aspx" />`

 `/// <reference path="Admin/Default.aspx" />`

 `/// <reference path="../Default.aspx" />`

 `/// <reference path="~/Admin/Default.aspx" />`

 Následující pravidla se vztahují na direktivu `reference`.

- Komentář XML `reference` musí být deklarovaný před jakýmkoli skriptem.

- Je nutné použít syntaxi komentářů XML se třemi lomítky. Odkazy vytvořené pomocí syntaxe standardních komentářů (dvě lomítka) jsou ignorovány.

- Na jednu direktivu lze určit pouze jeden soubor nebo prostředek.

- Více odkazů na skripty na základě stránky není povoleno.

- Pokud je zadán odkaz na stránku, není povolen žádný jiný typ direktiv odkazu.

- Názvy souborů používají relativní cesty. K vytvoření relativních cest aplikace můžete použít operátor tilda (`~`).

- Absolutní cesty jsou ignorovány.

- Direktivy odkazu na odkazovaných stránkách nebudou zpracovány; direktivy odkazu nejsou pro stránky řešeny rekurzivně. Je zahrnut pouze jeden skript, na který stránka odkazuje přímo.

#### <a name="ReferenceGroups"></a>Referenční skupiny
 Pomocí předdefinovaných referenčních skupin můžete určit, že konkrétní soubory .js technologie IntelliSense jsou v oboru pro různé projekty jazyka JavaScript. K dispozici jsou následující typy referenčních skupin:

- Implicitní (Windows) pro [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikace pomocí JavaScriptu. Soubory zahrnuté v této skupině jsou v oboru pro každý soubor .js otevřený v editoru kódu pro projekt určeného typu.

- Implicitní (web) pro projekty HTML5. Soubory zahrnuté v této skupině jsou v oboru pro každý soubor .js otevřený v editoru kódu pro tyto typy projektů.

- Referenční skupiny vyhrazeného pracovníka, pro HTML5 Web Workers. Soubory zahrnuté v této skupině jsou v oboru pro každý soubor .js, který má explicitní odkaz na referenční skupinu vyhrazeného pracovníka.

- Obecné, pro ostatní typy projektů jazyka JavaScript.

  Ve většině případů není nutné referenční skupiny měnit. Pokud však chcete provést změny, můžete použít možnosti konfigurace pro editor kódu jazyka JavaScript a určit soubory, které budou do referenčních skupin zahrnuty. Pokyny k použití této funkce najdete v tématu [Možnosti, textový editor, JavaScript, IntelliSense](../ide/reference/options-text-editor-javascript-intellisense.md).

> [!TIP]
> Odkazy technologie IntelliSense se obvykle používají k poskytování podpory technologie IntelliSense pro globální objekty a pro [rozšíření](#Extensibility)technologie IntelliSense. Tuto funkci můžete použít také pro skripty, které musí být v době běhu načteny pomocí modulu pro zavádění skriptu.

### <a name="remote-file-references"></a>Odkazy na vzdálené soubory
 Můžete nastavit, aby aplikace Visual Studio stáhla vzdálené soubory jazyka JavaScript, které jsou odkazovány v souboru jazyka JavaScript, s cílem poskytnout podporu technologie IntelliSense pro vzdálený soubor nebo knihovny. Při použití této funkce se soubory stáhnou, pokud je vložíte jako referenci do souboru s kódem JavaScript.

> [!NOTE]
> Tuto funkci lze použít pouze pro soubory jazyka JavaScript, které jsou otevřeny mimo kontext projektu, s výjimkou webových projektů. Pro webové projekty jsou ve výchozím nastavení vzdálené soubory, na které váš projekt odkazuje, staženy automaticky.

 Pokyny k použití této funkce najdete v tématu [Možnosti, textový editor, JavaScript, IntelliSense](../ide/reference/options-text-editor-javascript-intellisense.md).

> [!WARNING]
> Pokud tuto funkci povolíte a zaznamenáte snížení výkonu editoru kódu, doporučujeme ji zakázat.

### <a name="XMLDocComments"></a>Dokumentační komentáře XML
 Dokumentační komentáře XML jsou textové popisy prvků kódu, které můžete přidat do skriptu. Tyto textové popisy jsou zobrazovány v technologii IntelliSense při odkazu na skript s komentářem. Můžete například poskytnout informace o parametrech funkce a návratové hodnotě. Dokumentační komentáře XML jsou k dispozici pouze z odkazovaných souborů, sestavení a služeb. Další informace najdete v [dokumentačních komentářích XML](../ide/xml-documentation-comments-javascript.md) a v [dokumentaci k dokumentaci XML](../ide/create-xml-documentation-comments-for-javascript-intellisense.md).

 Technologie IntelliSense může dokumentační komentáře XML zobrazit v následujících situacích:

- Soubor .js, který odkazuje na jiný soubor .js.

- Soubor .js, který odkazuje na soubor .aspx.

- Soubor .aspx, který odkazuje na soubor .js.

  Technologie IntelliSense není dostupná, když jeden soubor .aspx odkazuje na jiný soubor .aspx.

### <a name="ASPNet"></a>ASP.NET AJAX objekty
 Technologie ASP.NET AJAX podporuje také technologii IntelliSense jazyka JavaScript. Technologie ASP.NET AJAX obsahuje rozhraní klienta, které rozšiřuje standardní typy dostupné v jazyce ECMAScript (JavaScript). Chcete-li povolit technologii JavaScript IntelliSense, aby poskytovala podrobné informace o ASP.NET objektech AJAX, byly přidány dokumentační komentáře XML v rámci [!INCLUDE[atlaslib_current_ext](../includes/atlaslib-current-ext-md.md)]. Tyto dokumentační komentáře XML se zobrazí při použití typů a členů, které jsou obsaženy v knihovně technologie ASP.NET AJAX.

> [!NOTE]
> Soukromé členy nejsou pomocí technologie IntelliSense jazyka JavaScript zobrazeny. Soukromé členy jsou v technologii ASP.NET AJAX označeny jako členy, které začínají podtržítkem (_).

## <a name="Extensibility"></a>Rozšiřitelnost technologie IntelliSense pro JavaScript
 Služba jazyka JavaScript poskytuje objekty a funkce, které vám umožní změnit prostředí technologie IntelliSense pro vývojáře, kteří používají knihovny třetích stran. Tyto funkce jsou zvláště užitečné v případě, že výchozí služba jazyka není schopna poskytnout všechny informace, které chcete poskytnout zákazníkům. Další informace najdete v tématu [rozšíření JavaScriptu IntelliSense](../ide/extending-javascript-intellisense.md).

## <a name="Validation"></a>Ověřování JavaScriptu
 Ověření skriptování v jazyce JavaScript probíhá neustále na pozadí. Pokud [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] detekuje chyby syntaxe v kódu JavaScriptu, je poskytnuta zpětná vazba následujícími způsoby:

- Podtržením prvků v editoru. Chyby jsou podtrženy červenou vlnovkou. Když nad chybou podržíte ukazatel myši, zobrazí se popis chyby.

- **Seznam chyb** okno V okně **Seznam chyb** se zobrazí popis chyby, soubor, ve kterém došlo k chybě, číslo řádku a sloupce a projekt. Chcete-li zobrazit okno **Seznam chyb** , v nabídce **zobrazení** klikněte na položku **Seznam chyb**.

- Okno Výstup zobrazí odkazy, které nebyly načteny.

## <a name="see-also"></a>Viz také
- [Používání atributu IntelliSense](../ide/using-intellisense.md)
- [Vytváření komentářů k dokumentaci XML](../ide/create-xml-documentation-comments-for-javascript-intellisense.md)
- [Rozšíření JavaScript IntelliSense](../ide/extending-javascript-intellisense.md)
- [Doplňování výrazů pro identifikátory](../ide/statement-completion-for-identifiers.md)
- [Dokumentační komentáře XML](../ide/xml-documentation-comments-javascript.md)
- [O modelu objektu DHTML](https://msdn2.microsoft.com/library/ms533022.aspx)
- [Seznam členů](https://msdn.microsoft.com/1b9cc469-9cd4-4d42-9999-1f9479635ff8)
- [SRC – &#124; vlastnost src atributu](https://msdn2.microsoft.com/library/ms534642.aspx)
