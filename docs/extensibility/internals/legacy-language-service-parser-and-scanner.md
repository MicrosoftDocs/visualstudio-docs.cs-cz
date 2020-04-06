---
title: Analyzátor starších jazykových služeb a skener | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- parsers, language services [managed package framework]
- language services [managed package framework], Parsers
ms.assetid: 1ac3de27-a23b-438d-9593-389e45839cfa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c87f447a4b8bca804d27aae4967f4adaf389c627
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707316"
---
# <a name="legacy-language-service-parser-and-scanner"></a>Analyzátor a skener služby starší verze jazyka
Analyzátor je srdcem jazykové služby. Jazykové třídy Rozhraní spravovaného balíčku (MPF) vyžadují analyzátor jazyka k výběru informací o zobrazeném kódu. Analyzátor odděluje text do lexikálnítokeny a pak identifikuje tyto tokeny podle typu a funkčnosti.

## <a name="discussion"></a>Diskuse
 Následuje metoda Jazyka C#.

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

 V tomto příkladu tokeny jsou slova a interpunkční znaménka. Druhy žetonů jsou následující.

|Název tokenu|Typ tokenu|
|----------------|----------------|
|obor názvů, třída, veřejné, neplatné, int|klíčové slovo|
|=| – operátor|
|{ } ( ) ;|delimiter|
|MyNamespace, MyClass, MyFunction, arg1, var1|identifikátor|
|Mynamespace|namespace|
|Myclass|třída|
|Funkce My|method|
|arg1|parametr|
|var1|lokální proměnná|

 Role analyzátoru je identifikovat tokeny. Některé tokeny mohou mít více než jeden typ. Poté, co analyzátor identifikoval tokeny, může jazyková služba použít informace k poskytování užitečných funkcí, jako je zvýraznění syntaxe, porovnávání složených závorek a operace Technologie IntelliSense.

## <a name="types-of-parsers"></a>Typy analyzátorů
 Analyzátor služby jazyka není stejný jako analyzátor používaný jako součást kompilátoru. Tento druh analyzátoru však musí používat skener i analyzátor stejným způsobem jako analyzátor kompilátoru.

- Skener se používá k identifikaci typů tokenů. Tyto informace se používají pro zvýraznění syntaxe a pro rychlou identifikaci typů tokenů, které mohou aktivovat další operace, například porovnávání složených závorek. Tento skener je <xref:Microsoft.VisualStudio.Package.IScanner> reprezentován rozhraním.

- Analyzátor se používá k popisu funkce a rozsah tokeny. Tyto informace se používají v operacích Technologie IntelliSense k identifikaci prvků jazyka, jako jsou metody, proměnné, parametry a deklarace, a k poskytnutí seznamů členů a podpisů metod na základě kontextu. Tento analyzátor se také používá k vyhledání odpovídajících párů elementů jazyka, jako jsou závorky a závorky. Tento analyzátor je přístupný <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> prostřednictvím <xref:Microsoft.VisualStudio.Package.LanguageService> metody ve třídě.

  Jak implementovat skener a analyzátor pro vaši jazykovou službu je jen na vás. K dispozici je několik zdrojů, které popisují, jak analyzátory fungují a jak psát vlastní analyzátor. K dispozici je také několik bezplatných a komerčních produktů, které pomáhají při vytváření analyzátoru.

### <a name="the-parsesource-parser"></a>Analyzátor parsesource
 Na rozdíl od analyzátoru, který se používá jako součást kompilátoru (kde tokeny jsou převedeny na nějakou formu spustitelného kódu), analyzátor služby jazyka lze volat z mnoha různých důvodů a v mnoha různých kontextech. Jak implementovat tento <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> přístup v <xref:Microsoft.VisualStudio.Package.LanguageService> metodě ve třídě je na vás. Je důležité mít na paměti, že <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metoda může být volána na podprocesu na pozadí.

> [!CAUTION]
> Struktura <xref:Microsoft.VisualStudio.Package.ParseRequest> obsahuje odkaz na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objekt. Tento <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objekt nelze použít ve vlákně na pozadí. Ve skutečnosti mnoho základních tříd MPF nelze použít ve vlákně na pozadí. Patří mezi <xref:Microsoft.VisualStudio.Package.Source> <xref:Microsoft.VisualStudio.Package.ViewFilter>ně <xref:Microsoft.VisualStudio.Package.CodeWindowManager> , , třídy a všechny ostatní třídy, které přímo nebo nepřímo komunikuje s zobrazením.

 Tento analyzátor obvykle analyzuje celý zdrojový soubor při prvním volání nebo při přiřazení <xref:Microsoft.VisualStudio.Package.ParseReason> hodnoty důvodu analýzy. Následná volání <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metody zpracovat malou část analyzovaného kódu a lze provést mnohem rychleji pomocí výsledků předchozí operace úplné analýzy. Metoda <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> sděluje výsledky operace analýzy <xref:Microsoft.VisualStudio.Package.AuthoringSink> prostřednictvím <xref:Microsoft.VisualStudio.Package.AuthoringScope> a objekty. Objekt <xref:Microsoft.VisualStudio.Package.AuthoringSink> se používá ke shromažďování informací pro konkrétní důvod analýzy, například informace o rozpětí odpovídající závorky nebo podpisy metody, které mají seznamy parametrů. Poskytuje <xref:Microsoft.VisualStudio.Package.AuthoringScope> kolekce deklarací a podpisů metod a také podporu pro možnost Přejít na rozšířené úpravy (**Přejít na definici**, **Přejít na deklaraci**, **Přejít na odkaz**).

### <a name="the-iscanner-scanner"></a>Skener IScanner
 Je také nutné implementovat <xref:Microsoft.VisualStudio.Package.IScanner>skener, který implementuje . Však vzhledem k tomu, že tento skener <xref:Microsoft.VisualStudio.Package.Colorizer> pracuje na základě řádku prostřednictvím třídy, je obvykle jednodušší implementovat. Na začátku každého řádku MPF <xref:Microsoft.VisualStudio.Package.Colorizer> dává třídy hodnotu použít jako proměnnou stavu, která je předána skeneru. Na konci každého řádku skener vrátí aktualizovanou proměnnou stavu. MPF ukládá tyto informace o stavu pro každý řádek tak, aby skener můžete spustit analýzu z libovolného řádku bez nutnosti spustit na začátku zdrojového souboru. Toto rychlé skenování jednoho řádku umožňuje editoru poskytovat rychlou zpětnou vazbu pro uživatele.

## <a name="parsing-for-matching-braces"></a>Analýza odpovídajících závorek
 Tento příklad ukazuje tok ovládacího prvku pro odpovídající uzavírací složená závorka, kterou uživatel zadal. V tomto procesu skener, který se používá pro vybarvení se také používá k určení typu tokenu a zda token může aktivovat operaci složená závorka. Pokud je nalezenaktivační <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> událost, je volána metoda najít odpovídající složená závorka. Nakonec jsou zvýrazněny dvě závorky.

 I když závorky se používají v názvech aktivačních událostí a analyzovat důvody, tento proces není omezen na skutečné závorky. Je podporována jakákoli dvojice znaků, která je určena jako odpovídající dvojice. Příklady zahrnují ( \< a ) a > a [ a ] a .

 Předpokládejme, že služba jazyka podporuje odpovídající závorky.

1. Uživatel zadá uzavírací složenou závorku (}).

2. Složená závorka je vložena do kurzoru ve zdrojovém souboru a kurzor je posunut o jeden.

3. Metoda <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> ve <xref:Microsoft.VisualStudio.Package.Source> třídě je volána s zadaným uzavírací morálkou.

4. Metoda <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> volá <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> metodu <xref:Microsoft.VisualStudio.Package.Source> ve třídě získat token na pozici těsně před aktuální pozici kurzoru. Tento token odpovídá zadané uzavírací závorky).

    1. Metoda <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> volá <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> metodu <xref:Microsoft.VisualStudio.Package.Colorizer> na objekt získat všechny tokeny na aktuálním řádku.

    2. Metoda <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> volá <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> metodu <xref:Microsoft.VisualStudio.Package.IScanner> na objektu s textem aktuálního řádku.

    3. Metoda <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> opakovaně volá <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> metodu <xref:Microsoft.VisualStudio.Package.IScanner> na objekt shromáždit všechny tokeny z aktuálního řádku.

    4. Metoda <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> volá soukromou metodu <xref:Microsoft.VisualStudio.Package.Source> ve třídě k získání tokenu, který obsahuje požadovanou pozici, a předá v seznamu tokenů získaných z <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> metody.

5. Metoda <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> hledá příznak aktivační událost <xref:Microsoft.VisualStudio.Package.TokenTriggers> tokenu na tokenu, který je vrácen z <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> metody; to znamená token, který představuje uzavírací složenou závorku).

6. Pokud <xref:Microsoft.VisualStudio.Package.TokenTriggers> je nalezen aktivační příznak, <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> je <xref:Microsoft.VisualStudio.Package.Source> volána metoda ve třídě.

7. Metoda <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> spustí operaci analýzy s hodnotou důvodu <xref:Microsoft.VisualStudio.Package.ParseReason>analýzy . Tato operace nakonec <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> volá metodu na třídu. <xref:Microsoft.VisualStudio.Package.LanguageService> Pokud je povolena asynchronní analýza, toto volání <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metody probíhá ve vlákně na pozadí.

8. Po dokončení operace analýzy je ve třídě volána obslužná `HandleMatchBracesResponse` rutina interního dokončování (označovaná také jako metoda zpětného <xref:Microsoft.VisualStudio.Package.Source> volání). Toto volání je <xref:Microsoft.VisualStudio.Package.LanguageService> automaticky provedeno základní třídou, nikoli analyzátorem.

9. Metoda `HandleMatchBracesResponse` získá seznam rozsahů z objektu, <xref:Microsoft.VisualStudio.Package.AuthoringSink> který je <xref:Microsoft.VisualStudio.Package.ParseRequest> uložen v objektu. (Rozsah je <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> struktura, která určuje rozsah řádků a znaků ve zdrojovém souboru.) Tento seznam rozsahů obvykle obsahuje dva rozsahy, jeden pro otevírací a uzavírací závorky.

10. Metoda `HandleBracesResponse` volá <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> metodu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> na objekt, který <xref:Microsoft.VisualStudio.Package.ParseRequest> je uložen v objektu. To zvýrazní dané rozpětí.

11. Pokud <xref:Microsoft.VisualStudio.Package.LanguagePreferences> je <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> vlastnost povolena, `HandleBracesResponse` metoda získá text, který je zahrnut odpovídající rozpětí a zobrazí prvních 80 znaků tohoto rozsahu ve stavovém řádku. To funguje nejlépe, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> pokud metoda obsahuje element jazyka, který doprovází odpovídající pár. Další informace naleznete <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> v ubytovacím zařízení.

12. Hotovo.

### <a name="summary"></a>Souhrn
 Odpovídající závorky operace je obvykle omezena na jednoduché dvojice prvků jazyka. Složitější prvky, například odpovídající`if(...)`trojité`{`prvky`}`("`else`",`{`" a`}`" " nebo " ", " a " ", mohou být zvýrazněny jako součást operace dokončení slova. Například po dokončení slova "else" lze zvýraznit odpovídající příkaz "`if`". Pokud existuje řada `if` / `else if` příkazů, všechny z nich by mohly být zvýrazněny pomocí stejného mechanismu jako odpovídající závorky. Základní <xref:Microsoft.VisualStudio.Package.Source> třída již podporuje, takto: Skener musí vrátit <xref:Microsoft.VisualStudio.Package.TokenTriggers> aktivační hodnotu tokenu v kombinaci s aktivační hodnotou <xref:Microsoft.VisualStudio.Package.TokenTriggers> pro token, který je před pozici kurzoru.

 Další informace naleznete [v tématu Rovnátka odpovídající ve službě starší jazyk](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).

## <a name="parsing-for-colorization"></a>Analýza pro vybarvení
 Vybarvení zdrojového kódu je jednoduché, stačí identifikovat typ tokenu a vrátit informace o barvě tohoto typu. Třída <xref:Microsoft.VisualStudio.Package.Colorizer> funguje jako prostředník mezi editorem a skenerem poskytnout informace o barvu o každém tokenu. Třída <xref:Microsoft.VisualStudio.Package.Colorizer> používá <xref:Microsoft.VisualStudio.Package.IScanner> objekt k pomoci při barvení čáry a také shromažďovat informace o stavu pro všechny řádky ve zdrojovém souboru. Ve třídách služby jazyka <xref:Microsoft.VisualStudio.Package.Colorizer> MPF není nutné třídu přepsat, protože komunikuje <xref:Microsoft.VisualStudio.Package.IScanner> se skenerem pouze prostřednictvím rozhraní. Zadáte objekt, který implementuje <xref:Microsoft.VisualStudio.Package.IScanner> rozhraní <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> přepsáním metody ve <xref:Microsoft.VisualStudio.Package.LanguageService> třídě.

 Skener <xref:Microsoft.VisualStudio.Package.IScanner> je uveden řádek zdrojového <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> kódu prostřednictvím metody. Volání <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> metody se opakují získat další token v řádku, dokud řádek je vyčerpán tokeny. Pro vybarvení MPF zachází se všemi zdrojovým kódem jako sekvenci řádků. Proto musí být skener schopen vyrovnat se se zdrojem, který na něj přichází jako linky. Kromě toho může být každá linka předána skeneru kdykoli a jedinou zárukou je, že skener obdrží proměnnou stavu z řádku před tím, než má být řádek skenován.

 Třída <xref:Microsoft.VisualStudio.Package.Colorizer> se také používá k identifikaci aktivační události tokenu. Tyto aktivační události sdělují MPF, že konkrétní token může zahájit složitější operaci, jako je například dokončení slova nebo odpovídající závorky. Vzhledem k tomu, že identifikace těchto aktivačních událostí musí být rychlá a musí k ní dojít v libovolném umístění, je skener pro tento úkol nejvhodnější.

 Další informace naleznete [v tématu Syntax colorizing in a Legacy Language Service](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).

## <a name="parsing-for-functionality-and-scope"></a>Analýza funkčnosti a oboru
 Analýza funkčnosti a oboru vyžaduje více úsilí než pouze identifikaci typů tokenů, které jsou zjištěny. Analyzátor musí identifikovat nejen typ tokenu, ale také funkce, pro které se používá token. Identifikátor je například pouze název, ale ve vašem jazyce může být identifikátor název třídy, oboru názvů, metody nebo proměnné v závislosti na kontextu. Obecný typ tokenu může být identifikátor, ale identifikátor může mít také jiné významy, v závislosti na tom, co je a kde je definován. Tato identifikace vyžaduje analyzátor mít rozsáhlejší znalosti o jazyku, který je analyzován. Tady přijde <xref:Microsoft.VisualStudio.Package.AuthoringSink> na řadě třída. Třída <xref:Microsoft.VisualStudio.Package.AuthoringSink> shromažďuje informace o identifikátorech, metodách, odpovídajících jazykových párech (například závorkách a závorkách) a jazykových`foreach()`trojicích`{`(podobně`}`jako páry jazyků s tím rozdílem, že existují tři části, například " " " a " "). Kromě toho můžete přepsat <xref:Microsoft.VisualStudio.Package.AuthoringSink> třídu pro podporu identifikace kódu, který se používá v časném ověření zarážek tak, aby ladicí program nemusí být načtena a **autos** ladění okno, které zobrazuje místní proměnné a parametry automaticky při ladění programu a vyžaduje analyzátor k identifikaci příslušné místní proměnné a parametry kromě těch, které představuje ladicí program.

 Objekt <xref:Microsoft.VisualStudio.Package.AuthoringSink> je předán analyzátoru jako součást <xref:Microsoft.VisualStudio.Package.ParseRequest> objektu a <xref:Microsoft.VisualStudio.Package.AuthoringSink> nový objekt je vytvořen <xref:Microsoft.VisualStudio.Package.ParseRequest> při každém vytvoření nového objektu. Kromě toho <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> musí metoda <xref:Microsoft.VisualStudio.Package.AuthoringScope> vrátit objekt, který se používá ke zpracování různých operací Technologie IntelliSense. Objekt <xref:Microsoft.VisualStudio.Package.AuthoringScope> udržuje seznam pro deklarace a seznam pro metody, z nichž buď je naplněna, v závislosti na důvodu analýzy. Třída <xref:Microsoft.VisualStudio.Package.AuthoringScope> musí být implementována.

## <a name="see-also"></a>Viz také
- [Implementace služby starší verze jazyka](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Přehled služby starší verze jazyka](../../extensibility/internals/legacy-language-service-overview.md)
- [Barevné zvýrazňování syntaxe ve službě starší verze jazyka](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
- [Související závorky ve službě starší verze jazyka](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)
