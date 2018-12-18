---
title: Podpora okna Automatické hodnoty ve službě starší verze jazyka | Dokumentace Microsoftu
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
- language services [managed package framework], Autos window
- Autos window, supporting in language services [managed package framework]
ms.assetid: 47d40aae-7a3c-41e1-a949-34989924aefb
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8e1f787b3a0f2ab1c153dfd3742c8939975e3ad1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51764478"
---
# <a name="support-for-the-autos-window-in-a-legacy-language-service"></a>Podpora okna Automatické hodnoty ve službě starší verze jazyka
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**Automatické hodnoty** okno zobrazuje výrazy, jako jsou proměnné a parametry, které jsou v oboru, když se laděný program pozastaví (buď z důvodu zarážky nebo výjimky). Výraz může obsahovat proměnné, místní nebo globální a parametry, které byly změněny v místním oboru. **Automatické hodnoty** okno může také obsahovat instance třídy, struktury nebo jiný typ. Cokoli, co můžete vyhodnotit vyhodnocovače výrazů může potenciálně zobrazený v **automatické hodnoty** okna.  
  
 Rozhraní spravovaného balíčku (MPF) neposkytuje přímou podporu **automatické hodnoty** okna. Nicméně pokud přepíšete <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> metoda může vrátit seznam výrazů, které se budou zobrazovat v **automatické hodnoty** okna.  
  
## <a name="implementing-support-for-the-autos-window"></a>Implementace podpora okna Automatické hodnoty  
 Všechno, co potřebujete udělat pro podporu **automatické hodnoty** okna je implementace <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> metodu <xref:Microsoft.VisualStudio.Package.LanguageService> třídy. Implementace, musíte se rozhodnout daném umístění ve zdrojovém souboru, který výrazů by se měla objevit v **automatické hodnoty** okna. Metoda vrátí seznam řetězců, ve kterých každý řetězec představuje jeden výraz. Vrácená hodnota <xref:Microsoft.VisualStudio.VSConstants.S_OK> označuje, zda seznam obsahuje výrazy, zatímco <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> znamená, že neexistují žádné výrazy k zobrazení.  
  
 Skutečné výrazů vrátila jsou názvy proměnných nebo parametrech, které se zobrazí na tomto místě v kódu. Tyto názvy jsou předány Chyba při vyhodnocování výrazu k získání hodnot a typy, které se zobrazí v **automatické hodnoty** okna.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje implementaci <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> metodu, která načte seznam výrazů od <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodu pomocí analýzy důvod <xref:Microsoft.VisualStudio.Package.ParseReason>. Každá z těchto výrazů je zabalena jako `TestVsEnumBSTR` , který implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR> rozhraní.  
  
 Všimněte si, že `GetAutoExpressionsCount` a `GetAutoExpression` metody jsou vlastních metod na `TestAuthoringSink` objektu a byly přidány pro podporu v tomto příkladu. Představují jeden ze způsobů ve výrazech, které přidá do `TestAuthoringSink` objekt analyzátorem (voláním <xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A> metoda) je přístupná mimo analyzátor.  
  
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

