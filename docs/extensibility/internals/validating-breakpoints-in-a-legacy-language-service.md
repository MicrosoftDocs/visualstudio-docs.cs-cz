---
title: Ověřování zarážek ve službě starší verze jazyka | Microsoft Docs
description: Přečtěte si, jak můžete přepsat metodu ValidateBreakpointLocation ve službě starší verze jazyka pro ověření zarážek před spuštěním ladicího programu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoint validation
- language services [managed package framework], breakpoint validation
ms.assetid: a7e873cd-dfe1-474f-bda5-fd7532774b15
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 593663c4906cc669c52336ffe6689e8de9fcde48
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941590"
---
# <a name="validating-breakpoints-in-a-legacy-language-service"></a>Ověřování zarážek ve službě starší verze jazyka
Zarážka označuje, že by mělo být spuštění programu zastaveno v určitém bodě, v němž je spuštěno v ladicím programu. Uživatel může umístit zarážku na libovolný řádek ve zdrojovém souboru, protože editor nemá žádné znalosti o tom, co představuje platné umístění pro zarážku. Po spuštění ladicího programu jsou všechny označené zarážky (nazývané nedokončené zarážky) vázány na příslušné umístění v běžícím programu. V současné době jsou zarážky ověřeny, aby se zajistilo, že označí platná umístění kódu. Například zarážka na komentáři není platná, protože ve zdrojovém kódu není v tomto umístění žádný kód. Ladicí program zakáže neplatné zarážky.

 Vzhledem k tomu, že služba jazyka ví o zobrazení zdrojového kódu, může ověřit zarážky před spuštěním ladicího programu. Metodu můžete přepsat <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> tak, aby vracela rozpětí určující platné umístění pro zarážku. Umístění zarážky je stále ověřováno při spuštění ladicího programu, ale uživatel je informován o neplatných zarážekch bez čekání na načtení ladicího programu.

## <a name="implementing-support-for-validating-breakpoints"></a>Implementace podpory pro ověřování zarážek

- <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>Metodě je dána pozice zarážky. Vaše implementace musí rozhodnout, zda je umístění platné, a indikovat to tak, že vrátí textový rozsah, který identifikuje kód přidružený k řádku pozice zarážky.

- Vrátí <xref:Microsoft.VisualStudio.VSConstants.S_OK> , zda je umístění platné, nebo <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> zda není platné.

- Pokud je zarážka platná, je zvýrazněný textový rozsah spolu se zarážkou.

- Pokud je zarážka neplatná, zobrazí se ve stavovém řádku chybová zpráva.

### <a name="example"></a>Příklad
 Tento příklad ukazuje implementaci <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> metody, která volá analyzátor, aby získala rozsah kódu (pokud existuje) v zadaném umístění.

 Tento příklad předpokládá, že jste přidali `GetCodeSpan` metodu do <xref:Microsoft.VisualStudio.Package.AuthoringSink> třídy, která ověřuje rozsah textu a vrátí, `true` Pokud se jedná o platné umístění zarážky.

```csharp
using Microsoft VisualStudio;
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    class TestLanguageService : LanguageService
    {
        public override int ValidateBreakpointLocation(IVsTextBuffer buffer,
                                                       int line,
                                                       int col,
                                                       TextSpan[] pCodeSpan)
        {
            int retval = VSConstants.S_FALSE;
            if (pCodeSpan != null)
            {
                // Initialize span to current line by default.
                pCodeSpan[0].iStartLine = line;
                pCodeSpan[0].iStartIndex = col;
                pCodeSpan[0].iEndLine = line;
                pCodeSpan[0].iEndIndex = col;
            }

            if (buffer != null)
            {
                IVsTextLines textLines = buffer as IVsTextLines;
                if (textLines != null)
                {
                    Source src = this.GetSource(textLines);
                    if (src != null)
                    {
                        TokenInfo tokenInfo = new TokenInfo();
                        string text = src.GetText();
                        ParseRequest req = CreateParseRequest(src,
                                                              line,
                                                              col,
                                                              tokenInfo,
                                                              text,
                                                              src.GetFilePath(),
                                                              ParseReason.CodeSpan,
                                                              null);
                        req.Scope = this.ParseSource(req);
                        TestAuthoringSink sink = req.Sink as TestAuthoringSink;

                        TextSpan span = new TextSpan();
                        if (sink.GetCodeSpan(out span))
                        {
                            pCodeSpan[0] = span;
                            retval = VSConstants.S_OK;
                        }
                    }
                }
            }
            return retval;
        }
    }
}
```

## <a name="see-also"></a>Viz také
- [Funkce služby starší verze jazyka](../../extensibility/internals/legacy-language-service-features1.md)
