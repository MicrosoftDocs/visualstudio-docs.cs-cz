---
title: Analyzátor a skener služby starší verze jazyka | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- parsers, language services [managed package framework]
- language services [managed package framework], Parsers
ms.assetid: 1ac3de27-a23b-438d-9593-389e45839cfa
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11b172fee8f6f5cf1c80d306a8a8b154f7316bf8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726728"
---
# <a name="legacy-language-service-parser-and-scanner"></a>Analyzátor a skener služby starší verze jazyka
Analyzátor je srdcem jazykové služby. Třídy jazyka Managed Package Framework (MPF) vyžadují analyzátor jazyka pro výběr informací o zobrazeném kódu. Analyzátor odděluje text na lexikální tokeny a pak tyto tokeny identifikuje podle typu a funkce.

## <a name="discussion"></a>Účely
 Následuje C# metoda.

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
|obor názvů, třída, veřejný, void, int|klíčové slovo|
|=|– operátor|
|{ } ( ) ;|Oddělovač|
|MyNamespace, MyClass, MyFunction, arg1, var1|identifikátor|
|MyNamespace|– obor názvů|
|MyClass|třída|
|Funkci|– metoda|
|arg1|parametr|
|var1|Lokální proměnná|

 Role analyzátoru slouží k identifikaci tokenů. Některé tokeny mohou mít více než jeden typ. Poté, co analyzátor identifikuje tokeny, může služba jazyka využít tyto informace k poskytnutí užitečných funkcí, jako je například zvýrazňování syntaxe, spárování složených závorek a operace IntelliSense.

## <a name="types-of-parsers"></a>Typy analyzátorů
 Analyzátor jazykové služby není stejný jako analyzátor používaný jako součást kompilátoru. Tento druh analyzátoru však musí použít skener i analyzátor, a to stejným způsobem jako analyzátor kompilátoru.

- K identifikaci typů tokenů se používá skener. Tyto informace slouží k zvýrazňování syntaxe a k rychlé identifikaci typů tokenů, které mohou aktivovat jiné operace, například spárování složených závorek. Tento skener je reprezentován rozhraním <xref:Microsoft.VisualStudio.Package.IScanner>.

- K popisu funkcí a rozsahu tokenů se používá analyzátor. Tyto informace se používají v operacích IntelliSense k identifikaci prvků jazyka, jako jsou metody, proměnné, parametry a deklarace, a k poskytnutí seznamů členů a signatur metod na základě kontextu. Tento analyzátor slouží také k vyhledání odpovídajícího páru prvků jazyka, jako jsou složené závorky a závorky. Tento analyzátor je k dispozici prostřednictvím metody <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> ve třídě <xref:Microsoft.VisualStudio.Package.LanguageService>.

  Způsob implementace skeneru a analyzátoru pro službu jazyka je až na vás. K dispozici je několik prostředků, které popisují, jak analyzátory fungují a jak psát vlastní analyzátor. K dispozici je také několik bezplatných a komerčních produktů, které vám pomůžou při vytváření analyzátoru.

### <a name="the-parsesource-parser"></a>Analyzátor ParseSource
 Na rozdíl od analyzátoru, který se používá jako součást kompilátoru (kde jsou tokeny převedeny na určitou formu spustitelného kódu), může být analyzátor služby jazyka volán z mnoha různých důvodů a v mnoha různých kontextech. Způsob implementace tohoto přístupu v metodě <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> třídy <xref:Microsoft.VisualStudio.Package.LanguageService> je až vám. Je důležité mít na paměti, že <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metoda může být volána ve vlákně na pozadí.

> [!CAUTION]
> Struktura <xref:Microsoft.VisualStudio.Package.ParseRequest> obsahuje odkaz na objekt <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>. Tento objekt <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> nelze použít ve vlákně na pozadí. Ve skutečnosti nelze mnoho základních tříd MPF použít ve vlákně na pozadí. Patří mezi ně <xref:Microsoft.VisualStudio.Package.Source>, <xref:Microsoft.VisualStudio.Package.ViewFilter>, <xref:Microsoft.VisualStudio.Package.CodeWindowManager> třídy a jakákoliv jiná třída, kterou přímo nebo nepřímo komunikuje se zobrazením.

 Tento analyzátor obvykle analyzuje celý zdrojový soubor při prvním volání nebo v případě, že je zadána hodnota důvod analýzy <xref:Microsoft.VisualStudio.Package.ParseReason>. Následná volání metody <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> zpracovávají malou část analyzovaného kódu a mohou být provedeny mnohem rychleji pomocí výsledků předchozí operace analýzy. Metoda <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> komunikuje výsledky operace analýzy prostřednictvím objektů <xref:Microsoft.VisualStudio.Package.AuthoringSink> a <xref:Microsoft.VisualStudio.Package.AuthoringScope>. Objekt <xref:Microsoft.VisualStudio.Package.AuthoringSink> se používá ke shromažďování informací pro konkrétní důvod analýzy, například informace o rozložené závorkách nebo podpisech metod, které mají seznamy parametrů. @No__t_0 poskytuje kolekce deklarací a signatur metod a také podporuje možnost přejít na pokročilou úpravu (**Přejít k definici**, **Přejít na deklaraci**, **Přejít na odkaz**).

### <a name="the-iscanner-scanner"></a>IScanner skener
 Musíte taky implementovat skener, který implementuje <xref:Microsoft.VisualStudio.Package.IScanner>. Vzhledem k tomu, že tento skener pracuje na řádku po jednotlivých řádcích prostřednictvím <xref:Microsoft.VisualStudio.Package.Colorizer> třídy, je obvykle jednodušší implementovat. Na začátku každého řádku poskytne hodnota MPF hodnotu <xref:Microsoft.VisualStudio.Package.Colorizer> třídu a, která se má použít jako stavová proměnná, která je předána skeneru. Na konci každého řádku skener vrátí aktualizovanou stavovou proměnnou. Soubor MPF ukládá tyto informace o stavu pro každý řádek, aby mohl skener začít analyzovat z libovolného řádku, aniž by bylo nutné začít na začátku zdrojového souboru. Tato rychlá kontrola jediného řádku umožňuje editoru poskytnout uživateli rychlou zpětnou vazbu.

## <a name="parsing-for-matching-braces"></a>Analýza pro párové závorky
 Tento příklad ukazuje tok ovládacího prvku pro porovnání uzavírací závorky, kterou zadal uživatel. V tomto procesu se k určení typu tokenu použije také skener, který se používá k obarvení, a to, jestli token může aktivovat operaci shody se závorkami. Pokud je nalezen Trigger, je volána metoda <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> k nalezení odpovídajícího složené závorky. Nakonec se zvýrazní dvě složené závorky.

 I když se v názvech triggerů a důvodů analýzy používají složené závorky, tento proces není omezený na skutečné složené závorky. Podporuje se všechny dvojice znaků, které jsou určené jako párové dvojice. Mezi příklady patří (a), \< a > a [a].

 Předpokládat, že jazyková služba podporuje odpovídající závorky.

1. Uživatel zadá pravou složenou závorku (}).

2. Složená závorka je vložena na kurzor ve zdrojovém souboru a kurzor je rozšířen o jednu.

3. Metoda <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> ve třídě <xref:Microsoft.VisualStudio.Package.Source> je volána pomocí typové uzavírací závorky.

4. Metoda <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> volá metodu <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> ve třídě <xref:Microsoft.VisualStudio.Package.Source>, aby získala token na pozici těsně před aktuální pozicí kurzoru. Tento token odpovídá typované pravé závorce.

    1. Metoda <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> volá metodu <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> na objektu <xref:Microsoft.VisualStudio.Package.Colorizer>, aby získala všechny tokeny na aktuálním řádku.

    2. Metoda <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> volá metodu <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> na objektu <xref:Microsoft.VisualStudio.Package.IScanner> s textem aktuálního řádku.

    3. Metoda <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> opakovaně volá metodu <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> na objektu <xref:Microsoft.VisualStudio.Package.IScanner> pro shromáždění všech tokenů z aktuálního řádku.

    4. Metoda <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> volá soukromou metodu ve třídě <xref:Microsoft.VisualStudio.Package.Source>, aby získala token, který obsahuje požadovanou pozici a předá je v seznamu tokenů získaných z metody <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A>.

5. Metoda <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> vyhledá příznak triggeru tokenu <xref:Microsoft.VisualStudio.Package.TokenTriggers> na tokenu, který je vrácen z metody <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A>; To znamená token, který představuje pravou složenou závorku.

6. Pokud je nalezen příznak triggeru <xref:Microsoft.VisualStudio.Package.TokenTriggers>, je volána metoda <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> ve třídě <xref:Microsoft.VisualStudio.Package.Source>.

7. Metoda <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> spustí operaci analýzy s hodnotou důvodu rozboru <xref:Microsoft.VisualStudio.Package.ParseReason>. Tato operace nakonec zavolá metodu <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> třídy <xref:Microsoft.VisualStudio.Package.LanguageService>. Pokud je povoleno asynchronní analýze, dojde k tomuto volání metody <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> ve vlákně na pozadí.

8. Po dokončení operace analýzy je ve třídě <xref:Microsoft.VisualStudio.Package.Source> volána interní obslužná rutina dokončení (označovaná také jako metoda zpětného volání) s názvem `HandleMatchBracesResponse`. Toto volání je provedeno automaticky <xref:Microsoft.VisualStudio.Package.LanguageService> základní třídou, nikoli analyzátorem.

9. Metoda `HandleMatchBracesResponse` získá seznam rozsahů z objektu <xref:Microsoft.VisualStudio.Package.AuthoringSink>, který je uložen v objektu <xref:Microsoft.VisualStudio.Package.ParseRequest>. (Rozpětí je <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> struktura, která určuje rozsah řádků a znaků ve zdrojovém souboru.) Tento seznam rozsahů obsahuje obvykle dvě rozpětí, jednu pro levou a pravou závorku.

10. Metoda `HandleBracesResponse` volá metodu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> na objektu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>, který je uložen v objektu <xref:Microsoft.VisualStudio.Package.ParseRequest>. Tím se zvýrazní dané rozsahy.

11. Pokud je povolena vlastnost <xref:Microsoft.VisualStudio.Package.LanguagePreferences> <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>, metoda `HandleBracesResponse` získá text, který je zahrnut v odpovídajícím rozsahu, a zobrazí první 80 znaků tohoto rozsahu ve stavovém řádku. To funguje nejlépe v případě, že metoda <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> obsahuje prvek jazyka, který doprovází odpovídající dvojici. Další informace najdete v tématu vlastnost <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>.

12. Hotovo.

### <a name="summary"></a>Souhrn
 Operace párování složených závorek je obvykle omezena na jednoduché páry jazykových prvků. Složitější prvky, jako jsou například párové tři ("`if(...)`", "`{`" a "`}`" nebo "`else`", "`{`" a "`}`"), mohou být zvýrazněny jako součást operace dokončování slov. Například když je slovo "else" dokončeno, je možné zvýraznit shodný příkaz "`if`". Pokud existovala řada `if` / `else if` příkazy, všechny mohou být zvýrazněny pomocí stejného mechanismu jako u shod složených závorek. @No__t_0 základní třídu již podporuje následujícím způsobem: skener musí vrátit hodnotu triggeru tokenu <xref:Microsoft.VisualStudio.Package.TokenTriggers> kombinaci s hodnotou triggeru <xref:Microsoft.VisualStudio.Package.TokenTriggers> pro token, který je před pozicí kurzoru.

 Další informace najdete v tématu [spárování složených závorek ve službě starší verze jazyka](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).

## <a name="parsing-for-colorization"></a>Analýza barev
 Zdrojový kód Colorizing je jednoduchý, stačí identifikovat typ tokenu a vrátit informace o barvách tohoto typu. Třída <xref:Microsoft.VisualStudio.Package.Colorizer> funguje jako prostředník mezi editorem a skenerem, který poskytuje informace o barvách pro každý token. Třída <xref:Microsoft.VisualStudio.Package.Colorizer> používá objekt <xref:Microsoft.VisualStudio.Package.IScanner> k usnadnění colorizingí řádku a také k získání informací o stavu pro všechny řádky ve zdrojovém souboru. Ve třídách služeb jazyka MPF není nutné přepsat třídu <xref:Microsoft.VisualStudio.Package.Colorizer>, protože komunikuje se skenerem pouze prostřednictvím rozhraní <xref:Microsoft.VisualStudio.Package.IScanner>. Objekt, který implementuje rozhraní <xref:Microsoft.VisualStudio.Package.IScanner>, zadáte přepsáním metody <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> třídy <xref:Microsoft.VisualStudio.Package.LanguageService>.

 @No__t_0 skeneru je prostřednictvím metody <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> přiřazen řádek zdrojového kódu. Volání metody <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> se opakují za účelem získání dalšího tokenu na řádku, dokud není vyčerpána čára z tokenů. V případě barevného nabarvení MPF zpracuje veškerý zdrojový kód jako sekvenci řádků. Proto musí být skener schopný odolat tomu, že se zdroj připravuje jako řádky. Kromě toho může být jakýkoli řádek kdykoli předán skeneru a jedinou zárukou je, že skener přijme proměnnou stavu z řádku před vyhledáním řádku.

 Třída <xref:Microsoft.VisualStudio.Package.Colorizer> slouží také k identifikaci triggerů tokenů. Tyto triggery říká hodnotu MPF, že konkrétní token může iniciovat složitější operaci, jako je například dokončování slov nebo párové závorky. Vzhledem k tomu, že identifikace takových triggerů musí být rychlá a musí se nacházet v jakémkoli umístění, je pro tento úkol nejvhodnější skener.

 Další informace najdete v tématu [syntaxe Colorizing ve službě starší verze jazyka](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).

## <a name="parsing-for-functionality-and-scope"></a>Analýza funkcí a rozsahu
 Analýza funkcí a rozsahu vyžaduje větší úsilí, než stačí určit typy tokenů, ke kterým došlo. Analyzátor musí identifikovat nejen typ tokenu, ale také funkčnost, pro kterou je token použit. Například identifikátor je pouze název, ale ve vašem jazyce, identifikátor může být název třídy, oboru názvů, metody nebo proměnné v závislosti na kontextu. Obecný typ tokenu může být identifikátor, ale identifikátor může mít také jiné významy v závislosti na tom, co je a kde je definován. Tato identifikace vyžaduje, aby analyzátor měl více rozsáhlých znalostí o jazyku, který se analyzuje. Zde je místo, kde se <xref:Microsoft.VisualStudio.Package.AuthoringSink> Třída nachází. Třída <xref:Microsoft.VisualStudio.Package.AuthoringSink> shromažďuje informace o identifikátorech, metodách, odpovídající dvojici jazyků (jako jsou složené závorky a závorky) a jazykové Trojnásobky (podobně jako dvojice jazyků s tím rozdílem, že existují tři části, například "`foreach()`" `{` "a" `}` ") . Kromě toho můžete přepsat třídu <xref:Microsoft.VisualStudio.Package.AuthoringSink> pro podporu Identifikace kódu, která se používá při počátečním ověřování zarážek, aby se ladicí program nemusel načíst a okno **Automatické** ladění, které zobrazuje místní proměnné a parametry. automaticky při ladění programu a vyžaduje, aby analyzátor identifikoval vhodné lokální proměnné a parametry kromě těch, které ladicí program prezentuje.

 Objekt <xref:Microsoft.VisualStudio.Package.AuthoringSink> je předán analyzátoru jako součást objektu <xref:Microsoft.VisualStudio.Package.ParseRequest> a při každém vytvoření nového objektu <xref:Microsoft.VisualStudio.Package.ParseRequest> je vytvořen nový objekt <xref:Microsoft.VisualStudio.Package.AuthoringSink>. Kromě toho musí metoda <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> vracet objekt <xref:Microsoft.VisualStudio.Package.AuthoringScope>, který se používá pro zpracování různých operací IntelliSense. Objekt <xref:Microsoft.VisualStudio.Package.AuthoringScope> udržuje seznam pro deklarace a seznam pro metody, z nichž každá je vyplněna v závislosti na důvodu analýzy. Třída <xref:Microsoft.VisualStudio.Package.AuthoringScope> musí být implementovaná.

## <a name="see-also"></a>Viz také:
- [Implementace služby starší verze jazyka](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Přehled služby starší verze jazyka](../../extensibility/internals/legacy-language-service-overview.md)
- [Barevné zvýrazňování syntaxe ve službě starší verze jazyka](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
- [Související závorky ve službě starší verze jazyka](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)