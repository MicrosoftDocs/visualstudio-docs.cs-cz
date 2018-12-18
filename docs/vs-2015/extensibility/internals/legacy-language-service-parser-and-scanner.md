---
title: Starší verze jazyka analyzátor a skener služby | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parsers, language services [managed package framework]
- language services [managed package framework], Parsers
ms.assetid: 1ac3de27-a23b-438d-9593-389e45839cfa
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fd419c569a298afd37548fd7b85a23cad733e371
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51786394"
---
# <a name="legacy-language-service-parser-and-scanner"></a>Analyzátor a skener služby starší verze jazyka
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Analyzátor je srdce komunity služby jazyka. Třídy jazyka Managed Package Framework (MPF) vyžadují analyzátoru jazyka pro výběr informací o kódu se zobrazí. Analyzátor oddělí text do lexikální tokenů a pak identifikuje těchto tokenů podle typu a funkce.  
  
## <a name="discussion"></a>Diskuse  
 Následuje metoda C#.  
  
```csharp  
namespace MyNamespace  
{  
    class MyClass  
    {  
        public void MyFunction(int arg1)  
        {  
            int var1 = arg1;  
        }  
    }  
}  
```  
  
 V tomto příkladu jsou tokeny slova a interpunkční znaménka. Typy tokenů jsou následující.  
  
|Název tokenu|Typ tokenu|  
|----------------|----------------|  
|obor názvů, třídy, veřejná, void, int|klíčové slovo|  
|=|– operátor|  
|{ } ( ) ;|Oddělovač|  
|MyNamespace, MyClass, MáFunkce, arg1, var1|identifikátor|  
|MyNamespace|– obor názvů|  
|MyClass|třída|  
|MáFunkce|– metoda|  
|arg1|parametr|  
|var1|Lokální proměnná|  
  
 Role Analyzátor je identifikace tokeny. Některé tokeny může mít více než jeden typ. Po analyzátor zjistil tokeny, že služba jazyka můžete použít operace IntelliSense a informace o zajištění užitečné funkce, jako jsou zvýraznění syntaxe, párování složených závorek.  
  
## <a name="types-of-parsers"></a>Typy analyzátory  
 Služba analyzátor jazyka není stejný jako analyzátor používá jako součást kompilátoru. Tento druh analyzátor však musí používat skeneru a analyzátor, stejně jako analyzátor kompilátoru.  
  
- Skener slouží k identifikaci typy tokenů. Tyto informace slouží pro zvýraznění syntaxe a umožňuje rychle identifikovat pro typy tokenů, které můžete aktivovat další operace, například související závorky. Je reprezentován Tento skener <xref:Microsoft.VisualStudio.Package.IScanner> rozhraní.  
  
- Analyzátor se používá k popisu funkce a oboru tokenů. Tyto informace slouží v operacích IntelliSense k identifikaci prvků jazyka, jako jsou metody, proměnné, parametry a deklarace a poskytnout seznam členů a podpisy metod na základě kontextu. Tento analyzátor je také používaná k nalezení odpovídající dvojice elementu jazyka, například složené závorky a závorky. Tento analyzátor je přístupný prostřednictvím <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodu <xref:Microsoft.VisualStudio.Package.LanguageService> třídy.  
  
  Jak implementovat analyzátor a skener služby jazyka je na vás. Jsou k dispozici několik prostředků, které popisují, jak fungují analyzátory a tom, jak psát vlastní analyzátor. Kromě toho jsou k dispozici několik produktů bezplatná a komerční, které pomáhají při vytváření analyzátor.  
  
### <a name="the-parsesource-parser"></a>Analyzátor ParseSource  
 Na rozdíl od analyzátor, který se používá jako součást kompilátor (kde tokeny jsou převedeny na nějakou formu spustitelného kódu) lze volat analyzátoru služby jazyka pro mnoho různých důvodů, proč a v mnoha různých kontextech. Implementace tohoto přístupu v <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodu <xref:Microsoft.VisualStudio.Package.LanguageService> třída je jenom na vás. Je důležité mít na paměti, která <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metoda může být volána na vlákně na pozadí.  
  
> [!CAUTION]
>  <xref:Microsoft.VisualStudio.Package.ParseRequest> Struktura obsahuje odkaz na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objektu. To <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objekt nelze použít ve vlákně na pozadí. Ve skutečnosti mnoho základních tříd MPF nelze použít ve vlákně na pozadí. Patří mezi ně <xref:Microsoft.VisualStudio.Package.Source>, <xref:Microsoft.VisualStudio.Package.ViewFilter>, <xref:Microsoft.VisualStudio.Package.CodeWindowManager> třídy a další třídu, která přímo nebo nepřímo komunikuje s zobrazení.  
  
 Tento analyzátor obvykle analyzuje soubor první čas celý zdroj je volána, nebo když analýzy z důvodu hodnotu <xref:Microsoft.VisualStudio.Package.ParseReason> je uveden. Následující volání <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metoda zpracování malou část analyzovaný kód a mohou být provedeny mnohem rychleji s využitím výsledky předchozí operace úplné analýzy. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Metoda komunikuje výsledky operace analýzy prostřednictvím <xref:Microsoft.VisualStudio.Package.AuthoringSink> a <xref:Microsoft.VisualStudio.Package.AuthoringScope> objekty. <xref:Microsoft.VisualStudio.Package.AuthoringSink> Objektu se používá ke shromažďování informací z určitého důvodu analýzy, například informace o rozsahy párování závorek nebo složených podpisy metod, které mají seznamy parametrů. <xref:Microsoft.VisualStudio.Package.AuthoringScope> Poskytuje kolekce deklarace a podpisy metod a také podporu přejít na rozšířených upravit možnosti (**přejít k definici**, **přejít na deklaraci**, **přejít na Odkazovat**).  
  
### <a name="the-iscanner-scanner"></a>Skener IScanner  
 Musíte také implementovat skener, který implementuje <xref:Microsoft.VisualStudio.Package.IScanner>. Ale protože tento skener funguje na základě řádek po řádku prostřednictvím <xref:Microsoft.VisualStudio.Package.Colorizer> třídy, je obvykle jednodušší implementaci. Na začátku každého řádku, poskytuje MPF <xref:Microsoft.VisualStudio.Package.Colorizer> třídy hodnotu pro použití jako stavová proměnná, která je předána skeneru. Na konci každého řádku vrací skener proměnnou aktualizovaný stav. MPF ukládá do mezipaměti tyto informace stav pro každý řádek tak, aby skener můžete spouštět analýzy z jakéhokoli řádku bez nutnosti spouštět na začátku zdrojového souboru. Toto rychlé vyhledávání z jednoho řádku umožňuje editoru poskytnout rychlé zpětné vazby pro uživatele.  
  
## <a name="parsing-for-matching-braces"></a>Analýza kódu pro párování závorek  
 Tento příklad ukazuje tok řízení pro odpovídající uzavírací závorkou, která uživatel zadal. V tomto procesu, který se používá pro barevné zvýraznění skener slouží také určit typ tokenu a určuje, zda token, který můžete aktivovat operace shody složenou závorku. Pokud trigger nenajde, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metoda je volána k nalezení odpovídající závorce. A konečně dva složené závorky jsou zvýrazněné.  
  
 I když složené závorky se používají v názvech aktivačních událostí a analyzovat z důvodů, tento proces není omezený na skutečné složené závorky. Pár znaků, který je nastaven na odpovídající dvojice je podporována. Mezi příklady patří (a), \< a >, a [a].  
  
 Předpokládejme, že služba jazyka podporuje odpovídající složené závorky.  
  
1.  Uživatel zadá uzavírací složená závorka (}).  
  
2.  Vložení složené závorky na pozici kurzoru ve zdrojovém souboru a kurzor je rozšířená o jednu.  
  
3.  <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Metodu <xref:Microsoft.VisualStudio.Package.Source> třída se nazývá s typem pravou složenou závorku.  
  
4.  <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Volání metod <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> metoda ve <xref:Microsoft.VisualStudio.Package.Source> třídy se získat token na pozici těsně před aktuální pozici kurzoru. Tento token odpovídá typu pravou složenou závorku).  
  
    1.  <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> Volání metod <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> metodu <xref:Microsoft.VisualStudio.Package.Colorizer> objekt k získání všech tokenů na aktuálním řádku.  
  
    2.  <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> Volání metod <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> metodu <xref:Microsoft.VisualStudio.Package.IScanner> objekt s textem aktuálního řádku.  
  
    3.  <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> Opakovaně volá metodu <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> metodu <xref:Microsoft.VisualStudio.Package.IScanner> objekt ke shromažďování všech tokenů z aktuálního řádku.  
  
    4.  <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> Metoda volá privátní metodu <xref:Microsoft.VisualStudio.Package.Source> třídy k získání tokenu, který obsahuje požadované místo, a předá v seznamu tokenů získané z <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> metody.  
  
5.  Tím <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> metoda vyhledá token trigger příznak <xref:Microsoft.VisualStudio.Package.TokenTriggers> na token, který je vrácen z <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> metoda; to znamená, že token, který představuje pravou složenou závorku).  
  
6.  Pokud příznak trigger <xref:Microsoft.VisualStudio.Package.TokenTriggers> nenajde, <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> metodu <xref:Microsoft.VisualStudio.Package.Source> třída se nazývá.  
  
7.  <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> Metoda začíná operace analýzy s hodnotou z důvodu analýzy <xref:Microsoft.VisualStudio.Package.ParseReason>. Takže v konečném důsledku volá tuto operaci <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodu <xref:Microsoft.VisualStudio.Package.LanguageService> třídy. Pokud asynchronní analýza kódu je povoleno, toto volání <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> vyvolá metodu ve vlákně na pozadí.  
  
8.  Při dokončení operace analýzy, obslužné rutiny dokončení vnitřní (označované také jako metody zpětného volání) s názvem `HandleMatchBracesResponse` je volána <xref:Microsoft.VisualStudio.Package.Source> třídy. Toto volání provádí automaticky <xref:Microsoft.VisualStudio.Package.LanguageService> základní třídy, ne společnost analyzátor.  
  
9. `HandleMatchBracesResponse` Metoda získá seznam rozsahy z <xref:Microsoft.VisualStudio.Package.AuthoringSink> objekt, který je uložen v <xref:Microsoft.VisualStudio.Package.ParseRequest> objektu. (Značka span je <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> struktura, která určuje rozsah řádků a znaků ve zdrojovém souboru.) Tento seznam rozsahy obvykle obsahuje dva rozsahy, jeden pro otevírací a uzavírací závorky.  
  
10. `HandleBracesResponse` Volání metod <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> metodu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objekt, který je uložen v <xref:Microsoft.VisualStudio.Package.ParseRequest> objektu. Tím se zvýrazní dané rozpětí.  
  
11. Pokud <xref:Microsoft.VisualStudio.Package.LanguagePreferences> vlastnost <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> je povoleno, `HandleBracesResponse` metoda získá text, který je vlastněný odpovídající značky span a ve stavovém řádku zobrazí nejprve 80 znaků tohoto rozpětí. Toto funguje nejlépe, pokud <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metoda obsahuje prvek jazyka, který doprovází shodnou dvojici. Další informace najdete v tématu <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> vlastnost.  
  
12. Hotovo.  
  
### <a name="summary"></a>Souhrn  
 Odpovídající složené závorky operace je obvykle omezené na jednoduché dvojice prvků jazyka. Složitější prvky, jako je například porovnávání trojic ("`if(…)`","`{`"a"`}`", nebo "`else`","`{`"a"`}`"), může být zvýrazněný jako součást operace dokončování slov. Například slovo "else" dokončení odpovídající "`if`" může být zvýrazněný příkaz. Pokud došlo k řadě `if` / `else if` příkazy, všechny z nich může být zvýrazněný pomocí mechanismu stejné jako odpovídající složené závorky. <xref:Microsoft.VisualStudio.Package.Source> Základní třídy již podporuje, následujícím způsobem: skener musí vracet hodnotu tokenu trigger <xref:Microsoft.VisualStudio.Package.TokenTriggers> v kombinaci s hodnotou aktivační událost <xref:Microsoft.VisualStudio.Package.TokenTriggers> pro daný token, který je před pozice kurzoru.  
  
 Další informace najdete v tématu [závorky ve službě starší verze jazyka](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).  
  
## <a name="parsing-for-colorization"></a>Analýza kódu pro barevné zvýraznění  
 Barevné zvýrazňování zdrojový kód je jednoduché, stačí identifikuje typ barva tokenu a vrátí informace o typu. <xref:Microsoft.VisualStudio.Package.Colorizer> Třída slouží jako zprostředkovatel mezi editoru a skener informovat například o barvu každého tokenu. <xref:Microsoft.VisualStudio.Package.Colorizer> Třídy používá <xref:Microsoft.VisualStudio.Package.IScanner> objektu, které vám pomůžou barevné označování řádku a také ke shromažďování informací o stavu pro všechny řádky ve zdrojovém souboru. Ve třídách MPF jazykové služby <xref:Microsoft.VisualStudio.Package.Colorizer> třída nemá přepsat, protože komunikuje pomocí skeneru pouze prostřednictvím <xref:Microsoft.VisualStudio.Package.IScanner> rozhraní. Můžete zadat objekt, který implementuje <xref:Microsoft.VisualStudio.Package.IScanner> rozhraní tak, že přepíšete <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> metodu <xref:Microsoft.VisualStudio.Package.LanguageService> třídy.  
  
 <xref:Microsoft.VisualStudio.Package.IScanner> Skener dostane řádku zdrojového kódu až <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> metody. Volání <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> metoda se opakují získat další token v řádku, až do vyčerpání řádku tokenů. Pro barevné zvýraznění MPF považuje pořadí řádků s veškerým zdrojovým kódem. Skener proto musí být schopen čelit zdroj už ji jako řádky. Kromě toho libovolném řádku může být předán skener kdykoli a jediná záruka je, že skener obdrží od řádku před řádkem asi ke kontrole proměnné stavu.  
  
 <xref:Microsoft.VisualStudio.Package.Colorizer> Třída se používá také k identifikaci token aktivační události. Tyto triggery informace MPF, že konkrétní token může iniciovat operaci s mnohem složitější, jako je například dokončení slova nebo odpovídající složené závorky. Protože identifikující tyto aktivační události musí být rychlé a v libovolném umístění se musí vyskytovat skener je nejvhodnější pro tuto úlohu.  
  
 Další informace najdete v tématu [barevné zvýrazňování syntaxe ve službě starší verze jazyka](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).  
  
## <a name="parsing-for-functionality-and-scope"></a>Analýza kódu pro funkce a oboru  
 Analýza kódu pro funkce a oboru vyžaduje další úsilí než jen Rychlá kontrola typy tokenů, které se vyskytují. Analyzátor musí identifikovat nejen typ tokenu, ale také funkce, pro který se používá token. Například identifikátor je pouze název, ale ve vašem jazyce, může být identifikátor názvu třídy, oboru názvů, metody nebo proměnné, v závislosti na kontextu. Obecný typ tokenu může být identifikátor, ale identifikátor mohou mít i jiné význam, a to v závislosti na tom, co je a kde je definován. Tato identifikace vyžaduje analyzátor, který má více rozsáhlé znalosti o jazyk, ve kterém je analyzován. Tady <xref:Microsoft.VisualStudio.Package.AuthoringSink> třídy je k dispozici ve. <xref:Microsoft.VisualStudio.Package.AuthoringSink> Třídy shromažďuje informace o identifikátory, metody, odpovídající dvojice jazyka (například složené závorky a závorek) a jazyk trojic (podobně jako dvojice jazyků s tím rozdílem, že existují tři části, například "`foreach()`" "`{`"a"`}`"). Kromě toho můžete přepsat <xref:Microsoft.VisualStudio.Package.AuthoringSink> třídy pro podporu identifikační kód, který se používá v rané fázi ověřování zarážek, tak, aby ladicí program má být načten, a **automatické hodnoty** ladění okna, která zobrazuje místní proměnné a parametry automaticky při programu je právě laděna a vyžaduje analyzátor identifikovat příslušné místní proměnné a parametry než ty, které ladicí program zobrazí.  
  
 <xref:Microsoft.VisualStudio.Package.AuthoringSink> Objekt je předán do analyzátor jako součást <xref:Microsoft.VisualStudio.Package.ParseRequest> objektu a nový <xref:Microsoft.VisualStudio.Package.AuthoringSink> objektu je vytvořena pokaždé, když nové <xref:Microsoft.VisualStudio.Package.ParseRequest> je vytvořen objekt. Kromě toho <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metoda musí vracet <xref:Microsoft.VisualStudio.Package.AuthoringScope> objektu, který se používá ke zpracování různé operace IntelliSense. <xref:Microsoft.VisualStudio.Package.AuthoringScope> Objekt udržuje seznam pro deklarace a seznam metod, buď z nichž se vyplní, v závislosti na důvodu pro analýzu. <xref:Microsoft.VisualStudio.Package.AuthoringScope> Třída musí implementovat.  
  
## <a name="see-also"></a>Viz také  
 [Implementace služby starší verze jazyka](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Přehled služby starší verze jazyka](../../extensibility/internals/legacy-language-service-overview.md)   
 [Barevné zvýrazňování syntaxe ve službě starší verze jazyka](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)   
 [Související závorky ve službě starší verze jazyka](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)

