---
title: Analyzátor a skener služby starší verze jazyka | Microsoft Docs
description: Seznamte se s analyzátorem a skenerem služby starší verze jazyka, který vybírá informace o zobrazeném kódu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- parsers, language services [managed package framework]
- language services [managed package framework], Parsers
ms.assetid: 1ac3de27-a23b-438d-9593-389e45839cfa
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9c57bd9f8b71f861fd5be4176211af6907b27e74
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090834"
---
# <a name="legacy-language-service-parser-and-scanner"></a>Analyzátor a skener služby starší verze jazyka
Analyzátor je srdcem jazykové služby. Třídy jazyka Managed Package Framework (MPF) vyžadují analyzátor jazyka pro výběr informací o zobrazeném kódu. Analyzátor odděluje text na lexikální tokeny a pak tyto tokeny identifikuje podle typu a funkce.

## <a name="discussion"></a>Diskuse
 Následuje metoda jazyka C#.

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
|=|operátor|
|{ } ( ) ;|Oddělovač|
|MyNamespace, MyClass, MyFunction, arg1, var1|identifikátor|
|MyNamespace|namespace|
|MyClass|class|
|Funkci|method|
|arg1|parameter|
|var1|lokální proměnná|

 Role analyzátoru slouží k identifikaci tokenů. Některé tokeny mohou mít více než jeden typ. Poté, co analyzátor identifikuje tokeny, může služba jazyka využít tyto informace k poskytnutí užitečných funkcí, jako je například zvýrazňování syntaxe, spárování složených závorek a operace IntelliSense.

## <a name="types-of-parsers"></a>Typy analyzátorů
 Analyzátor jazykové služby není stejný jako analyzátor používaný jako součást kompilátoru. Tento druh analyzátoru však musí použít skener i analyzátor, a to stejným způsobem jako analyzátor kompilátoru.

- K identifikaci typů tokenů se používá skener. Tyto informace slouží k zvýrazňování syntaxe a k rychlé identifikaci typů tokenů, které mohou aktivovat jiné operace, například spárování složených závorek. Tento skener je reprezentován <xref:Microsoft.VisualStudio.Package.IScanner> rozhraním.

- K popisu funkcí a rozsahu tokenů se používá analyzátor. Tyto informace se používají v operacích IntelliSense k identifikaci prvků jazyka, jako jsou metody, proměnné, parametry a deklarace, a k poskytnutí seznamů členů a signatur metod na základě kontextu. Tento analyzátor slouží také k vyhledání odpovídajícího páru prvků jazyka, jako jsou složené závorky a závorky. Tento analyzátor je k dispozici prostřednictvím <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metody ve <xref:Microsoft.VisualStudio.Package.LanguageService> třídě.

  Způsob implementace skeneru a analyzátoru pro službu jazyka je až na vás. K dispozici je několik prostředků, které popisují, jak analyzátory fungují a jak psát vlastní analyzátor. K dispozici je také několik bezplatných a komerčních produktů, které vám pomůžou při vytváření analyzátoru.

### <a name="the-parsesource-parser"></a>Analyzátor ParseSource
 Na rozdíl od analyzátoru, který se používá jako součást kompilátoru (kde jsou tokeny převedeny na určitou formu spustitelného kódu), může být analyzátor služby jazyka volán z mnoha různých důvodů a v mnoha různých kontextech. Způsob implementace tohoto přístupu v <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodě <xref:Microsoft.VisualStudio.Package.LanguageService> třídy je až na sebe. Je důležité mít na paměti, že <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metoda může být volána ve vlákně na pozadí.

> [!CAUTION]
> <xref:Microsoft.VisualStudio.Package.ParseRequest>Struktura obsahuje odkaz na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objekt. Tento <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objekt nelze použít ve vlákně na pozadí. Ve skutečnosti nelze mnoho základních tříd MPF použít ve vlákně na pozadí. Patří mezi ně třídy <xref:Microsoft.VisualStudio.Package.Source> , <xref:Microsoft.VisualStudio.Package.ViewFilter> , <xref:Microsoft.VisualStudio.Package.CodeWindowManager> a další třídy, které přímo nebo nepřímo komunikují se zobrazením.

 Tento analyzátor obvykle analyzuje celý zdrojový soubor při prvním volání nebo v případě, že hodnota důvod analýzy <xref:Microsoft.VisualStudio.Package.ParseReason> je uvedena. Následná volání <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metody zpracovávají malou část analyzovaného kódu a lze provést mnohem rychleji pomocí výsledků předchozí operace analýzy. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>Metoda komunikuje výsledky operace analýzy prostřednictvím <xref:Microsoft.VisualStudio.Package.AuthoringSink> <xref:Microsoft.VisualStudio.Package.AuthoringScope> objektů a. <xref:Microsoft.VisualStudio.Package.AuthoringSink>Objekt se používá ke shromažďování informací pro konkrétní důvod analýzy, například informace o zarovnávání odpovídající závorky nebo signatury metod, které mají seznamy parametrů. <xref:Microsoft.VisualStudio.Package.AuthoringScope>Poskytuje kolekce deklarací a signatur metod a také podporu pro možnost přejít na pokročilou úpravu (Přejít na **definici**, **Přejít k deklaraci**, **Přejít na odkaz**).

### <a name="the-iscanner-scanner"></a>IScanner skener
 Musíte taky implementovat skener, který implementuje <xref:Microsoft.VisualStudio.Package.IScanner> . Vzhledem k tomu, že tento skener pracuje na řádku po jednotlivých řádcích prostřednictvím <xref:Microsoft.VisualStudio.Package.Colorizer> třídy, je obvykle jednodušší implementovat. Na začátku každého řádku poskytne <xref:Microsoft.VisualStudio.Package.Colorizer> hodnota MPF hodnotu třídy, kterou chcete použít jako stavovou proměnnou, která je předána skeneru. Na konci každého řádku skener vrátí aktualizovanou stavovou proměnnou. Soubor MPF ukládá tyto informace o stavu pro každý řádek, aby mohl skener začít analyzovat z libovolného řádku, aniž by bylo nutné začít na začátku zdrojového souboru. Tato rychlá kontrola jediného řádku umožňuje editoru poskytnout uživateli rychlou zpětnou vazbu.

## <a name="parsing-for-matching-braces"></a>Analýza pro párové závorky
 Tento příklad ukazuje tok ovládacího prvku pro porovnání uzavírací závorky, kterou zadal uživatel. V tomto procesu se k určení typu tokenu použije také skener, který se používá k obarvení, a to, jestli token může aktivovat operaci shody se závorkami. Pokud je nalezen Trigger, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> je volána metoda pro nalezení odpovídajícího složené závorky. Nakonec se zvýrazní dvě složené závorky.

 I když se v názvech triggerů a důvodů analýzy používají složené závorky, tento proces není omezený na skutečné složené závorky. Podporuje se všechny dvojice znaků, které jsou určené jako párové dvojice. Mezi příklady patří (a), \< and > , a [a].

 Předpokládat, že jazyková služba podporuje odpovídající závorky.

1. Uživatel zadá pravou složenou závorku (}).

2. Složená závorka je vložena na kurzor ve zdrojovém souboru a kurzor je rozšířen o jednu.

3. <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>Metoda ve <xref:Microsoft.VisualStudio.Package.Source> třídě je volána pomocí typové uzavírací závorky.

4. <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>Metoda volá <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> metodu ve <xref:Microsoft.VisualStudio.Package.Source> třídě, aby získala token na pozici těsně před aktuální pozicí kurzoru. Tento token odpovídá typované pravé závorce.

    1. <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A>Metoda volá <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> metodu <xref:Microsoft.VisualStudio.Package.Colorizer> objektu pro získání všech tokenů na aktuálním řádku.

    2. <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A>Metoda volá <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> metodu <xref:Microsoft.VisualStudio.Package.IScanner> objektu s textem aktuálního řádku.

    3. <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A>Metoda opakovaně volá <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> metodu <xref:Microsoft.VisualStudio.Package.IScanner> objektu pro shromáždění všech tokenů z aktuálního řádku.

    4. <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A>Metoda volá soukromou metodu ve třídě, <xref:Microsoft.VisualStudio.Package.Source> aby získala token, který obsahuje požadovanou pozici, a předá v seznamu tokenů získaných z <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> metody.

5. <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>Metoda hledá příznak triggeru tokenu <xref:Microsoft.VisualStudio.Package.TokenTriggers> na tokenu, který je vrácen z <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> metody; to znamená token, který představuje pravou složenou závorku.

6. Pokud je nalezen příznak triggeru <xref:Microsoft.VisualStudio.Package.TokenTriggers> , je <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> volána metoda ve <xref:Microsoft.VisualStudio.Package.Source> třídě.

7. <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A>Metoda spustí operaci analýzy s hodnotou důvodu rozboru <xref:Microsoft.VisualStudio.Package.ParseReason> . Tato operace nakonec volá <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodu pro <xref:Microsoft.VisualStudio.Package.LanguageService> třídu. Pokud je povoleno asynchronní analýze, k tomuto volání <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metody dojde ve vlákně na pozadí.

8. Po dokončení operace analýzy `HandleMatchBracesResponse` je ve třídě volána interní obslužná rutina pro dokončení (označovaná také jako metoda zpětného volání) s názvem <xref:Microsoft.VisualStudio.Package.Source> . Toto volání je provedeno automaticky <xref:Microsoft.VisualStudio.Package.LanguageService> základní třídou, nikoli analyzátorem.

9. `HandleMatchBracesResponse`Metoda získá seznam rozsahů z <xref:Microsoft.VisualStudio.Package.AuthoringSink> objektu, který je uložen v <xref:Microsoft.VisualStudio.Package.ParseRequest> objektu. (Rozpětí je <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> struktura, která určuje rozsah řádků a znaků ve zdrojovém souboru.) Tento seznam rozsahů obsahuje obvykle dvě rozpětí, jednu pro levou a pravou závorku.

10. `HandleBracesResponse`Metoda volá <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> metodu na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objekt, který je uložen v <xref:Microsoft.VisualStudio.Package.ParseRequest> objektu. Tím se zvýrazní dané rozsahy.

11. Pokud <xref:Microsoft.VisualStudio.Package.LanguagePreferences> je vlastnost <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> povolena, `HandleBracesResponse` Metoda získá text, který je zahrnut v odpovídajícím rozsahu, a zobrazí první 80 znaků tohoto rozsahu ve stavovém řádku. To funguje nejlépe v případě, že <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Metoda obsahuje prvek jazyka, který doprovází odpovídající dvojici. Další informace najdete v tématu <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> vlastnost.

12. Hotovo.

### <a name="summary"></a>Souhrn
 Operace párování složených závorek je obvykle omezena na jednoduché páry jazykových prvků. Složitější prvky, jako jsou například párové tři (" `if(...)` ", " `{` " a " `}` " nebo " `else` ", "" `{` a " `}` "), mohou být zvýrazněny jako součást operace dokončování slov. Například když je slovo "else" dokončeno, je `if` možné zvýraznit příkaz "". Pokud existovala řada `if` / `else if` příkazů, může být vše zvýrazněno pomocí stejného mechanismu jako u shod složených závorek. <xref:Microsoft.VisualStudio.Package.Source>Tato základní třída již podporuje následujícím způsobem: skener musí vracet hodnotu triggeru tokenu v <xref:Microsoft.VisualStudio.Package.TokenTriggers> kombinaci s hodnotou triggeru <xref:Microsoft.VisualStudio.Package.TokenTriggers> pro token, který je před pozicí kurzoru.

 Další informace najdete v tématu [spárování složených závorek ve službě starší verze jazyka](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).

## <a name="parsing-for-colorization"></a>Analýza barev
 Zdrojový kód Colorizing je jednoduchý, stačí identifikovat typ tokenu a vrátit informace o barvách tohoto typu. <xref:Microsoft.VisualStudio.Package.Colorizer>Třída funguje jako prostředník mezi editorem a skenerem, aby poskytovala informace o barvách pro každý token. <xref:Microsoft.VisualStudio.Package.Colorizer>Třída používá <xref:Microsoft.VisualStudio.Package.IScanner> objekt k usnadnění Colorizing řádku a také k získání informací o stavu pro všechny řádky ve zdrojovém souboru. Ve třídách služeb jazyka MPF <xref:Microsoft.VisualStudio.Package.Colorizer> není nutné přepsat třídu, protože komunikuje se skenerem pouze prostřednictvím <xref:Microsoft.VisualStudio.Package.IScanner> rozhraní. Objekt, který implementuje rozhraní, zadáte <xref:Microsoft.VisualStudio.Package.IScanner> přepsáním <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> metody <xref:Microsoft.VisualStudio.Package.LanguageService> třídy.

 <xref:Microsoft.VisualStudio.Package.IScanner>Skener má prostřednictvím metody přiřazený řádek zdrojového kódu <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> . Volání <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> metody jsou opakována za účelem získání dalšího tokenu na řádku, dokud není vyčerpána čára z tokenů. V případě barevného nabarvení MPF zpracuje veškerý zdrojový kód jako sekvenci řádků. Proto musí být skener schopný odolat tomu, že se zdroj připravuje jako řádky. Kromě toho může být jakýkoli řádek kdykoli předán skeneru a jedinou zárukou je, že skener přijme proměnnou stavu z řádku před vyhledáním řádku.

 <xref:Microsoft.VisualStudio.Package.Colorizer>Třída se používá také k identifikaci triggerů tokenů. Tyto triggery říká hodnotu MPF, že konkrétní token může iniciovat složitější operaci, jako je například dokončování slov nebo párové závorky. Vzhledem k tomu, že identifikace takových triggerů musí být rychlá a musí se nacházet v jakémkoli umístění, je pro tento úkol nejvhodnější skener.

 Další informace najdete v tématu [syntaxe Colorizing ve službě starší verze jazyka](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).

## <a name="parsing-for-functionality-and-scope"></a>Analýza funkcí a rozsahu
 Analýza funkcí a rozsahu vyžaduje větší úsilí, než stačí určit typy tokenů, ke kterým došlo. Analyzátor musí identifikovat nejen typ tokenu, ale také funkčnost, pro kterou je token použit. Například identifikátor je pouze název, ale ve vašem jazyce, identifikátor může být název třídy, oboru názvů, metody nebo proměnné v závislosti na kontextu. Obecný typ tokenu může být identifikátor, ale identifikátor může mít také jiné významy v závislosti na tom, co je a kde je definován. Tato identifikace vyžaduje, aby analyzátor měl více rozsáhlých znalostí o jazyku, který se analyzuje. Zde je místo, kde se <xref:Microsoft.VisualStudio.Package.AuthoringSink> Třída nachází. <xref:Microsoft.VisualStudio.Package.AuthoringSink>Třída shromažďuje informace o identifikátorech, metodách, odpovídající dvojici jazyků (jako jsou složené závorky a kulaté závorky) a jazykové Trojnásobky (podobně jako dvojice jazyků, s výjimkou toho, že existují tři části, například " `foreach()` " " `{` a" `}` "). Kromě toho můžete <xref:Microsoft.VisualStudio.Package.AuthoringSink> třídu přepsat tak, aby podporovala identifikaci kódu, která se používá při brzkém ověřování zarážek, aby se ladicí program nemusel načíst, a okno **Automatické** ladění, které zobrazuje místní proměnné a parametry automaticky při ladění programu a vyžaduje analyzátor k identifikaci příslušných místních proměnných a parametrů, kromě těch, které ladicí program prezentuje.

 <xref:Microsoft.VisualStudio.Package.AuthoringSink>Objekt je předán analyzátoru jako součást <xref:Microsoft.VisualStudio.Package.ParseRequest> objektu a <xref:Microsoft.VisualStudio.Package.AuthoringSink> je vytvořen nový objekt pokaždé, když <xref:Microsoft.VisualStudio.Package.ParseRequest> je vytvořen nový objekt. Kromě toho <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> musí metoda vracet <xref:Microsoft.VisualStudio.Package.AuthoringScope> objekt, který se používá pro zpracování různých operací IntelliSense. <xref:Microsoft.VisualStudio.Package.AuthoringScope>Objekt udržuje seznam pro deklarace a seznam pro metody, z nichž každá je vyplněna v závislosti na důvodu analýzy. <xref:Microsoft.VisualStudio.Package.AuthoringScope>Třída musí být implementovaná.

## <a name="see-also"></a>Viz také
- [Implementace služby starší verze jazyka](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Přehled služby starší verze jazyka](../../extensibility/internals/legacy-language-service-overview.md)
- [Barevné zvýrazňování syntaxe ve službě starší verze jazyka](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
- [Související závorky ve službě starší verze jazyka](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)
