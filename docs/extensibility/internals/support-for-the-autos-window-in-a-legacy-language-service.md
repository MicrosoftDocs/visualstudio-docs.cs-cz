---
title: Podpora okna Automatické hodnoty ve službě starší verze jazyka
description: Naučte se implementovat podporu pro okno Automatické hodnoty, ve kterém se zobrazí výrazy, které jsou v oboru, když je program laděný, pozastaven.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: c97ab4db9b71c91689abe0afb85230e5b0242962
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876503"
---
# <a name="support-for-the-autos-window-in-a-legacy-language-service"></a>Podpora pro okno Automatické hodnoty ve službě starší verze jazyka

Okno **Automatické** hodnoty zobrazuje výrazy, jako jsou proměnné a parametry, které jsou v oboru, pokud je program laděný (buď kvůli zarážce, nebo výjimku). Výrazy mohou zahrnovat proměnné, místní nebo globální a parametry, které byly změněny v místním oboru. Okno **Automatické** hodnoty může také zahrnovat vytváření instancí třídy, struktury nebo jiného typu. Cokoli, co může vyhodnocovací filtr výrazů vyhodnotit, může být potenciálně možné zobrazit v okně **Automatické** hodnoty.

 Sada Managed Package Framework (MPF) neposkytuje přímou podporu pro okno **Automatické** hodnoty. Nicméně pokud přepíšete <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> metodu, můžete vrátit seznam výrazů, které mají být zobrazeny v okně **Automatické** hodnoty.

## <a name="implementing-support-for-the-autos-window"></a>Implementace podpory pro okno Automatické hodnoty

 Vše, co potřebujete k podpoře okna **Automatické** hodnoty, je implementace <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> metody ve <xref:Microsoft.VisualStudio.Package.LanguageService> třídě. Vaše implementace se musí rozhodnout pro umístění ve zdrojovém souboru, které výrazy by se měly zobrazit v okně **Automatické** hodnoty. Metoda vrátí seznam řetězců, ve kterých každý řetězec představuje jeden výraz. Návratová hodnota <xref:Microsoft.VisualStudio.VSConstants.S_OK> označuje, že seznam obsahuje výrazy, zatímco se zobrazí <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> žádné výrazy k zobrazení.

 Skutečné vrácené výrazy jsou názvy proměnných nebo parametrů, které se zobrazí v daném umístění v kódu. Tyto názvy jsou předány do vyhodnocovacího filtru výrazů, aby získaly hodnoty a typy, které jsou následně zobrazeny v okně **Automatické** hodnoty.

### <a name="example"></a>Příklad
 Následující příklad ukazuje implementaci <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> metody, která získá seznam výrazů z <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metody pomocí důvodu analýzy <xref:Microsoft.VisualStudio.Package.ParseReason> . Každý výraz je zabalen jako `TestVsEnumBSTR` , který implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR> rozhraní.

 Všimněte si, `GetAutoExpressionsCount` že `GetAutoExpression` metody a jsou vlastní metody `TestAuthoringSink` objektu a byly přidány pro podporu v tomto příkladu. Představují jeden způsob, jakým jsou výrazy přidané do `TestAuthoringSink` objektu analyzátorem (voláním <xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A> metody) k dispozici mimo analyzátor.

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
