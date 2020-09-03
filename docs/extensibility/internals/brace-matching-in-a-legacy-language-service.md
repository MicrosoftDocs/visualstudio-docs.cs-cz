---
title: Spárování složených závorek ve službě starší verze jazyka | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709807"
---
# <a name="brace-matching-in-a-legacy-language-service"></a>Spárování složených závorek ve službě starší verze jazyka
Spárování složených závorek pomáhá vývojářům sledovat prvky jazyka, které musí probíhat společně, například kulaté závorky a složené závorky. Když vývojář zadá pravou složenou závorku, zvýrazní se levá složená závorka.

 Můžete porovnat dva nebo tři opakující se prvky, nazývané páry a tři. Tři jsou množiny tří prvků, které se společně vyskytují. Například v jazyce C# `foreach` příkaz tvoří Troji: `foreach()` , `{` , a `}` . Po zadání pravé složené závorky se zvýrazní všechny tři prvky.

 Starší jazykové služby jsou implementovány jako součást sady VSPackage, ale novější způsob, jak implementovat funkce jazykové služby, je použít rozšíření MEF. Další informace o novém způsobu implementace spárování složených závorek naleznete v tématu [Návod: zobrazení vyhovujících závorek](../../extensibility/walkthrough-displaying-matching-braces.md).

> [!NOTE]
> Doporučujeme začít používat nové rozhraní API editoru co nejrychleji. Tím se vylepšit výkon vaší jazykové služby a umožní vám využít nové funkce editoru.

 <xref:Microsoft.VisualStudio.Package.AuthoringSink>Třída podporuje dvojice i Trojnásobky s <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchPair%2A> <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchTriple%2A> metodami a.

## <a name="implementation"></a>Implementace
 Služba jazyka potřebuje identifikovat všechny odpovídající prvky v jazyce a potom najít všechny odpovídající páry. To se obvykle provádí implementací <xref:Microsoft.VisualStudio.Package.IScanner> k detekci odpovídajícího jazyka a následným použitím <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metody pro porovnání prvků.

 <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>Metoda volá skener, aby tokenizovat čáru a vrátila token těsně před blikajícím kurzorem. Skener indikuje, že byl nalezen pár jazykových prvků nastavením hodnoty triggeru tokenu <xref:Microsoft.VisualStudio.Package.TokenTriggers> u aktuálního tokenu. <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>Metoda volá <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> metodu, která zase volá <xref:Microsoft.VisualStudio.Package.LanguageService.BeginParse%2A> metodu s hodnotou důvodu analýzy <xref:Microsoft.VisualStudio.Package.ParseReason> pro nalezení odpovídajícího prvku jazyka. Při nalezení odpovídajícího prvku jazyka se zvýrazní oba elementy.

 Úplný popis způsobu, jakým se při zadávání složené závorky aktivují zvýrazňování složených závorek, najdete v části *příklad operace analýzy* v článku [analyzátor a skener služby starší verze jazyka](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).

## <a name="enable-support-for-brace-matching"></a>Povolit podporu pro spárování složených závorek
 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>Atribut může nastavit položky registru **MatchBraces**, **MatchBracesAtCaret**a **ShowMatchingBrace** , které nastaví odpovídající vlastnosti <xref:Microsoft.VisualStudio.Package.LanguagePreferences> třídy. Vlastnosti jazykové předvolby může nastavit i uživatel.

|Položka registru|Vlastnost|Popis|
|--------------------|--------------|-----------------|
|MatchBraces|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBraces%2A>|Povoluje spárování složených závorek.|
|MatchBracesAtCaret|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBracesAtCaret%2A>|Povoluje spárování složených závorek s přesunutím blikajícího kurzoru.|
|ShowMatchingBrace|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>|Zvýrazní spárovánou závorku.|

## <a name="match-conditional-statements"></a>Shoda s podmíněnými příkazy
 Můžete se shodovat s podmíněnými příkazy, jako `if` jsou, `else if` , a `else` , nebo,,, `#if` `#elif` `#else` `#endif` a stejným způsobem jako odpovídající oddělovače. Třídu můžete podtřídit <xref:Microsoft.VisualStudio.Package.AuthoringSink> a poskytnout metodu, která může přidat text a také oddělovače do interního pole odpovídající prvky.

## <a name="set-the-trigger"></a>Nastavení triggeru
 Následující příklad ukazuje, jak detekovat párové závorky, složené závorky a hranaté závorky a nastavit pro ni aktivační událost ve skeneru. <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>Metoda ve <xref:Microsoft.VisualStudio.Package.Source> třídě detekuje Trigger a volá analyzátor, aby nalezl odpovídající dvojici (viz část *hledání shody* v tomto článku). Tento příklad je určen pouze pro ilustrativní účely. Předpokládá, že váš skener obsahuje metodu `GetNextToken` , která identifikuje a vrací tokeny z řádku textu.

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

## <a name="match-the-braces"></a>Porovnat složené závorky
 Zde je zjednodušený příklad pro porovnání prvků jazyka `{ }` , `( )` , a `[ ]` a přidání jejich rozsahů do <xref:Microsoft.VisualStudio.Package.AuthoringSink> objektu. Tento přístup není doporučeným přístupem k analýze zdrojového kódu; je určen pouze pro ilustrativní účely.

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
- [Funkce služby starší verze jazyka](../../extensibility/internals/legacy-language-service-features1.md)
- [Analyzátor a skener služby starší verze jazyka](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
