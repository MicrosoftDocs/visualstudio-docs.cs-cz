---
title: Ověřování zarážek ve službě staršího jazyka | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoint validation
- language services [managed package framework], breakpoint validation
ms.assetid: a7e873cd-dfe1-474f-bda5-fd7532774b15
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af09e4f8f2156100bea9267c92ffebeb64ce1aa3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704095"
---
# <a name="validating-breakpoints-in-a-legacy-language-service"></a>Ověřování zarážek ve službě starší verze jazyka
Zarážka označuje, že spuštění programu by se mělo zastavit v určitém bodě, zatímco je spuštěnv ladicím programu. Uživatel může umístit zarážku na libovolný řádek ve zdrojovém souboru, protože editor nemá žádné znalosti o tom, co představuje platné umístění pro zarážku. Při spuštění ladicího programu jsou všechny označené zarážky (nazývané čekající zarážky) vázány na příslušné umístění v běžícím programu. Současně jsou ověřovány zarážky, aby bylo zajištěno, že označují platná umístění kódu. Například zarážka na komentář není platný, protože není žádný kód v tomto umístění ve zdrojovém kódu. Ladicí program zakáže neplatné zarážky.

 Vzhledem k tomu, že služba jazyka ví o zobrazeném zdrojovém kódu, může ověřit zarážky před spuštěním ladicího programu. Můžete přepsat metodu <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> vrátit rozpětí určující platné umístění pro zarážku. Umístění zarážky je stále ověřena při spuštění ladicího programu, ale uživatel je upozorněn na neplatné zarážky bez čekání na ladicí program načíst.

## <a name="implementing-support-for-validating-breakpoints"></a>Implementace podpory pro ověřování zarážek

- Metoda <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> je dána pozice zarážky. Implementace musí rozhodnout, zda umístění je platný a označí to vrácením textu span, který identifikuje kód přidružený k řádku pozici zarážky.

- Vraťte, <xref:Microsoft.VisualStudio.VSConstants.S_OK> pokud je <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> umístění platné nebo pokud není platné.

- Pokud je zarážka platná, bude rozsah textu zvýrazněn spolu s zarážkou.

- Pokud je zarážka neplatná, zobrazí se na stavovém řádku chybová zpráva.

### <a name="example"></a>Příklad
 Tento příklad ukazuje implementaci <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> metody, která volá analyzátor získat rozsah kódu (pokud existuje) v zadaném umístění.

 Tento příklad předpokládá, že `GetCodeSpan` jste přidali metodu do <xref:Microsoft.VisualStudio.Package.AuthoringSink> třídy, `true` která ověřuje rozsah textu a vrátí, pokud se jedná o platné umístění zarážky.

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
