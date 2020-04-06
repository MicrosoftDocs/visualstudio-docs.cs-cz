---
title: Porovnávání složených závorek ve službě staršího jazyka | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- brace matching
- language services [managed package framework], brace matching
ms.assetid: 4e3d0a70-f22f-49dd-92d8-edf48ab62b52
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0081be3e3ab5a53f7d85f77475d4288aa5c87092
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709807"
---
# <a name="brace-matching-in-a-legacy-language-service"></a>Porovnávání složených závorek ve starší jazykové službě
Porovnávání závorek pomáhá vývojáři sledovat prvky jazyka, které je třeba provést společně, jako jsou závorky a složené závorky. Když vývojář zadá uzavírací složenou závorku, zvýrazní se úvodní závorka.

 Můžete porovnat dva nebo tři kovyskytující se prvky, nazývané páry a trojité prvky. Trojité jsou sady tří kovyskytujících prvků. Například v C#, `foreach` příkaz tvoří `foreach()`triple: `{` `}`, , a . Všechny tři prvky jsou zvýrazněny při zadání uzavírací složená závorka.

 Starší jazykové služby jsou implementovány jako součást VSPackage, ale novější způsob implementace funkcí služby jazyka je použití rozšíření MEF. Další informace o novém způsobu implementace párování složených závorek naleznete v [tématu Návod: Zobrazení odpovídajících závorek](../../extensibility/walkthrough-displaying-matching-braces.md).

> [!NOTE]
> Doporučujeme, abyste co nejdříve začali používat nové rozhraní API editoru. Tím se zlepší výkon služby jazyka a umožní vám využít nové funkce editoru.

 Třída <xref:Microsoft.VisualStudio.Package.AuthoringSink> podporuje dvojice a triples <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchPair%2A> s <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchTriple%2A> metodami a.

## <a name="implementation"></a>Implementace
 Služba jazyka musí identifikovat všechny odpovídající prvky v jazyce a potom vyhledat všechny odpovídající dvojice. To se obvykle provádí implementací <xref:Microsoft.VisualStudio.Package.IScanner> pro detekci odpovídajícího <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> jazyka a potom pomocí metody tak, aby odpovídaly prvky.

 Metoda <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> volá skener tokenizovat linku a vrátit token těsně před stříška. Skener označuje, že dvojice elementů jazyka byla nalezena <xref:Microsoft.VisualStudio.Package.TokenTriggers> nastavením aktivační hodnoty tokenu na aktuálním tokenu. Metoda <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> volá <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> metodu, která <xref:Microsoft.VisualStudio.Package.LanguageService.BeginParse%2A> zase volá metodu s <xref:Microsoft.VisualStudio.Package.ParseReason> hodnotou důvod analýzy vyhledejte odpovídající prvek jazyka. Při nalezení odpovídající prvek jazyka jsou zvýrazněny oba prvky.

 Úplný popis toho, jak zadání závorky aktivuje zvýraznění složených závorek, naleznete v části *Příklad operace analýzy* v článku [Analyzátor služby starší jazyk a skener](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).

## <a name="enable-support-for-brace-matching"></a>Povolit podporu pro porovnávání složených závorek
 Atribut <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> můžete nastavit **MatchBraces**, **MatchBracesAtCaret**a **ShowMatchingBrace** položky registru, které nastavují odpovídající vlastnosti <xref:Microsoft.VisualStudio.Package.LanguagePreferences> třídy. Vlastnosti jazykových předvoleb může také nastavit uživatel.

|Položka registru|Vlastnost|Popis|
|--------------------|--------------|-----------------|
|MatchBraces|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBraces%2A>|Povolí shodu složených závorek.|
|MatchBracesAtCaret|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBracesAtCaret%2A>|Povolí shodu složených složených složených svorek při pohybu stříšky.|
|Zobrazitodpovídajícírovná|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>|Zvýrazní odpovídající složenou závorku.|

## <a name="match-conditional-statements"></a>Shoda podmíněných příkazů
 `if`Podmíněné příkazy, například `else if`, `else`a `#if` `#elif`, `#else` `#endif`, , můžete spárovat stejným způsobem jako odpovídající oddělovače. Můžete podtřídy <xref:Microsoft.VisualStudio.Package.AuthoringSink> třídy a poskytnout metodu, která můžete přidat rozsahy textu, stejně jako oddělovače do vnitřní pole odpovídající prvky.

## <a name="set-the-trigger"></a>Nastavení aktivační události
 Následující příklad ukazuje, jak zjistit odpovídající závorky, složené závorky a čtvercové závorky a nastavení aktivační události pro něj ve skeneru. Metoda <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> na <xref:Microsoft.VisualStudio.Package.Source> třídy zjistí aktivační událost a volá analyzátor najít odpovídající pár (viz *hledání shody* části v tomto článku). Tento příklad je pouze pro ilustrační účely. Předpokládá, že skener obsahuje `GetNextToken` metodu, která identifikuje a vrací tokeny z řádku textu.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestScanner : IScanner
    {
        private const string braces = "()[]{}";
        private Lexer lex;

        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,
                                                   ref int state)
        {
            bool foundToken = false;
            string token = lex.GetNextToken();
            if (token != null)
            {
                foundToken = true;
                char firstChar = token[0];
                if (Char.IsPunctuation(firstChar) && token.Length > 0)
                {
                    if (braces.IndexOf(firstChar) != -1)
                    {
                        tokenInfo.Trigger = TokenTriggers.MatchBraces;
                    }
                }
            }
            return foundToken;
        }
```

## <a name="match-the-braces"></a>Porovnejte závorky
 Zde je zjednodušený příklad pro `{ }` `( )`porovnávání `[ ]`prvků jazyka , a <xref:Microsoft.VisualStudio.Package.AuthoringSink> , a přidání jejich rozpětí k objektu. Tento přístup není doporučený mašlový přístup k analýzě zdrojového kódu; je pouze pro ilustrační účely.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class Parser
    {
         private IList<TextSpan[]> m_braces;
         public IList<TextSpan[]> Braces
         {
             get { return m_braces; }
         }
         private void AddMatchingBraces(TextSpan braceSpan1, TextSpan braceSpan2)
         {
             if IsMatch(braceSpan1, braceSpan2)
                 m_braces.Add(new TextSpan[] { braceSpan1, braceSpan2 });
         }

         private bool IsMatch(TextSpan braceSpan1, TextSpan braceSpan2)
         {
             //definition for matching here
          }
    }

    public class TestLanguageService : LanguageService
    {
         Parser parser = new Parser();
         Source source = (Source) this.GetSource(req.FileName);

         private AuthoringScope ParseSource(ParseRequest req)
         {
             if (req.Sink.BraceMatching)
             {
                 if (req.Reason==ParseReason.MatchBraces)
                 {
                     foreach (TextSpan[] brace in parser.Braces)
                     {
                         req.Sink.MatchPair(brace[0], brace[1], 1);
                     }
                 }
             }
             return new TestAuthoringScope();
         }
    }
}
```

## <a name="see-also"></a>Viz také
- [Funkce služby starších jazyků](../../extensibility/internals/legacy-language-service-features1.md)
- [Analyzátor starších jazykových služeb a skener](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
