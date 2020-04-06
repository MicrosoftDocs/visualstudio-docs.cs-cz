---
title: Podpora okna Autos ve službě starší verze jazyka | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], Autos window
- Autos window, supporting in language services [managed package framework]
ms.assetid: 47d40aae-7a3c-41e1-a949-34989924aefb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 75f8c761721dde5dad4bb75b8675f71f678b06df
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704886"
---
# <a name="support-for-the-autos-window-in-a-legacy-language-service"></a>Podpora okna Automatické hodnoty ve službě starší verze jazyka
Okno **Autos** zobrazuje výrazy, jako jsou proměnné a parametry, které jsou v oboru, když je laděný program pozastaven (buď z důvodu zarážky nebo výjimky). Výrazy mohou obsahovat proměnné, místní nebo globální a parametry, které byly změněny v místním oboru. Okno **Autos** může také obsahovat instance třídy, struktury nebo jiného typu. Vše, co vyhodnocení výrazu může vyhodnotit potenciálně lze zobrazit v okně **Autos.**

 Rozhraní spravovaného balíčku (MPF) neposkytuje přímou podporu pro okno **Autos.** Pokud však přepíšete metodu, <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> můžete vrátit seznam výrazů, které mají být prezentovány v okně **Autos.**

## <a name="implementing-support-for-the-autos-window"></a>Implementace podpory okna Autos
 Vše, co musíte udělat pro podporu okna <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> **Autos** je implementovat metodu ve <xref:Microsoft.VisualStudio.Package.LanguageService> třídě. Vaše implementace musí rozhodnout, dané umístění ve zdrojovém souboru, které výrazy by se měly objevit v okně **Autos.** Metoda vrátí seznam řetězců, ve kterých každý řetězec představuje jeden výraz. Vrácená hodnota <xref:Microsoft.VisualStudio.VSConstants.S_OK> označuje, že seznam obsahuje <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> výrazy, zatímco označuje, že neexistují žádné výrazy, které by bylo možné zobrazit.

 Skutečné vrácené výrazy jsou názvy proměnných nebo parametrů, které se zobrazí v tomto umístění v kódu. Tyto názvy jsou předány vyhodnocení výrazu získat hodnoty a typy, které jsou pak zobrazeny v okně **Autos.**

### <a name="example"></a>Příklad
 Následující příklad ukazuje implementaci <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> metody, která získá seznam výrazů z <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metody <xref:Microsoft.VisualStudio.Package.ParseReason>pomocí důvodu analýzy . Každý z výrazů je zabalen `TestVsEnumBSTR` jako, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR> který implementuje rozhraní.

 Všimněte `GetAutoExpressionsCount` si, že metody `GetAutoExpression` `TestAuthoringSink` a jsou vlastní metody na objektu a byly přidány pro podporu tohoto příkladu. Představují jeden způsob, ve kterém `TestAuthoringSink` výrazy přidané k objektu <xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A> analyzátorem (voláním metody) lze přistupovat mimo analyzátor.

```csharp
using Microsoft.VisualStudio;
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        public override int GetProximityExpressions(IVsTextBuffer buffer,
                                                    int line,
                                                    int col,
                                                    int cLines,
                                                    out IVsEnumBSTR ppEnum)
        {
            int retval = VSConstants.E_NOTIMPL;
            ppEnum = null;
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
                                                              ParseReason.Autos,
                                                              null);
                        req.Scope = this.ParseSource(req);
                        TestAuthoringSink sink = req.Sink as TestAuthoringSink;

                        retval = VSConstants.S_FALSE;
                        int spanCount = sink.GetAutoExpressionsCount();
                        if (spanCount > 0) {
                            TestVsEnumBSTR bstrList = new TestVsEnumBSTR();
                            for (int i = 0; i < spanCount; i++)
                            {
                                TextSpan span;
                                sink.GetAutoExpression(i, out span);
                                string expression = src.GetText(span.iStartLine,
                                                                span.iStartIndex,
                                                                span.iEndLine,
                                                                span.iEndIndex);
                                bstrList.AddString(expression);
                            }
                            ppEnum = bstrList;
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
