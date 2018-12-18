---
title: Související závorky ve službě starší verze jazyka | Dokumentace Microsoftu
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
- brace matching
- language services [managed package framework], brace matching
ms.assetid: 4e3d0a70-f22f-49dd-92d8-edf48ab62b52
caps.latest.revision: 28
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 70ad3062a4cbbce8ef46c3afe8851382949fe3f3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51753216"
---
# <a name="brace-matching-in-a-legacy-language-service"></a>Související závorky ve službě starší verze jazyka
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Párování závorek pomáhá vývojářům sledovat prvky jazyka, které se musí se provést současně, jako je například závorky a složené závorky. Když vývojář přejde do pravé složené závorky, je zvýrazněn levou složenou závorku.  
  
 Můžete porovnat dvě nebo tři společně se vyskytující prvky nazývané páry a trojic. Trojic jsou sady společně se vyskytující tři prvky. Například v jazyce C# `foreach` příkaz forms s trojitými: "`foreach()`","`{`", a "`}`". Po zadání pravé složené závorce, jsou zvýrazněny všechny tři prvky.  
  
 Služby starší verze jazyka jsou implementovány jako součást sady VSPackage, ale novější způsob implementace funkce služba jazyka je pro použití rozšíření MEF. Další informace o nový způsob implementace párování závorek, najdete v tématu [návod: zobrazení párových složených závorek](../../extensibility/walkthrough-displaying-matching-braces.md).  
  
> [!NOTE]
>  Doporučujeme vám, že začnete používat nový editor API co nejdříve. Tím vylepšíme výkonu vaší služby jazyka a umožňují využívat nové funkce editoru.  
  
 <xref:Microsoft.VisualStudio.Package.AuthoringSink> Třída podporuje obě páry a triples s <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchPair%2A> a <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchTriple%2A> metody.  
  
## <a name="implementation"></a>Implementace  
 Služba jazyka je potřeba identifikovat všechny odpovídající elementy v jazyce a vyhledejte všechny odpovídající dvojice. To je obvykle provedeno pomocí implementace <xref:Microsoft.VisualStudio.Package.IScanner> ke zjištění odpovídající jazyk a poté použijete <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodu tak, aby odpovídaly prvky.  
  
 <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Metoda volá skener tokenizovat řádku a vrátíte se token těsně před blikajícím kurzorem. Skener označuje, že byla nalezena dvojice elementů jazyk tak, že nastavíte hodnotu tokenu aktivační událost <xref:Microsoft.VisualStudio.Package.TokenTriggers> na aktuální token. <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Volání metod <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> metodu, která volá <xref:Microsoft.VisualStudio.Package.LanguageService.BeginParse%2A> metody s hodnotou z důvodu analýzy <xref:Microsoft.VisualStudio.Package.ParseReason> najít odpovídající prvek jazyka. Když je nalezena odpovídající prvek jazyka, jsou zvýrazněny oba prvky.  
  
 Úplný popis jak psát složenou závorku aktivuje zvýraznění závorek, najdete v části "Příklad analyzovat operace" v tématu [starší verze jazyka analyzátor a skener služby](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).  
  
## <a name="enabling-support-for-brace-matching"></a>Povolení podpory pro párování závorek  
 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> Atribut lze nastavit `MatchBraces`, `MatchBracesAtCaret`, a `ShowMatchingBrace` pojmenované parametry, které nastavte odpovídající vlastnosti <xref:Microsoft.VisualStudio.Package.LanguagePreferences> třídy. Jazykové předvolby vlastnosti můžete také nastavit uživatelem.  
  
|Položky registru|Vlastnost|Popis|  
|--------------------|--------------|-----------------|  
|`MatchBraces`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBraces%2A>|Povolí párování závorek|  
|`MatchBracesAtCaret`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBracesAtCaret%2A>|Povolí párování složených závorek jako blikající kurzor přesouvá.|  
|`ShowMatchingBrace`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>|Zvýrazní odpovídající závorce.|  
  
## <a name="matching-conditional-statements"></a>Odpovídající podmíněné příkazy  
 Můžete porovnat podmíněné příkazy, jako například `if`, `else if`, a `else`, nebo `#if`, `#elif`, `#else`, `#endif`, stejně jako odpovídající oddělovače. Je možné podtřídy <xref:Microsoft.VisualStudio.Package.AuthoringSink> třídy a zadejte metodu, která můžete přidat text a zahrnuje i oddělovačů vnitřní pole odpovídajících prvků.  
  
## <a name="setting-the-trigger"></a>Nastavení aktivační události  
 Následující příklad ukazuje, jak detekovat odpovídající závorky, složených závorek a hranatých závorkách a nastavení aktivační události pro něj v skeneru. <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Metodu <xref:Microsoft.VisualStudio.Package.Source> třídy detekuje aktivační událost a volá analyzátor najít odpovídající dvojici (viz oddíl "Hledání shodu" v tomto tématu). V tomto příkladu je pouze pro ilustraci. Předpokládá, že skener obsahuje metodu `GetNextToken` , který identifikuje a vrátí tokeny z řádku textu.  
  
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
  
## <a name="matching-the-braces"></a>Odpovídající složené závorky  
 Tady je zjednodušený příklad pro závorek {} prvky jazyka, () a [] č. a jejich rozpětí k přidání <xref:Microsoft.VisualStudio.Package.AuthoringSink> objektu. Tento přístup není doporučený postup pro analýzu zdrojového kódu; je pouze pro ilustraci.  
  
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
 [Funkce služby starší verze jazyka](../../extensibility/internals/legacy-language-service-features1.md)   
 [Analyzátor a skener služby starší verze jazyka](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

