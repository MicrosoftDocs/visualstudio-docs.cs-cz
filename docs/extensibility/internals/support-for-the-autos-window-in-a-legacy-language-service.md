---
title: Podpora pro automobily okna ve službě jazyk starší | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], Autos window
- Autos window, supporting in language services [managed package framework]
ms.assetid: 47d40aae-7a3c-41e1-a949-34989924aefb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a1a2627bd36e6047db00afaada231dc49cde2cc3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135819"
---
# <a name="support-for-the-autos-window-in-a-legacy-language-service"></a>Podpora pro automobily okna ve službě jazyk starší verze
**Automobily** zobrazuje výrazy, například proměnné a parametry, které jsou v oboru, když program laděné je pozastaveno (buď z důvodu zarážku nebo výjimku). Výrazy může obsahovat proměnné, místní nebo globální a parametry, které se změnily v místní oboru. **Automobily** okno může také obsahovat instancí třídy, struktury nebo jiný typ. Potenciálně všechno, co můžete vyhodnotit vyhodnocení výrazu lze zobrazit v **automobily** okno.  
  
 Rozhraní framework spravované balíčku (MPF) neposkytuje přímé podpory pro **automobily** okno. Ale pokud přepíšete <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> metodu, můžete se vrátit seznam výrazů ve **automobily** okno.  
  
## <a name="implementing-support-for-the-autos-window"></a>Implementace podpora automatické hodnoty – okno  
 Všechny je potřeba pro podporu **automobily** okno je k implementaci <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> metoda v <xref:Microsoft.VisualStudio.Package.LanguageService> třídy. Implementace, musíte se rozhodnout zadané umístění, do zdrojového souboru, který výrazy by se měla objevit v **automobily** okno. Metoda vrátí seznam řetězců, ve kterých každý řetězec představuje jeden výraz. Vrácená hodnota <xref:Microsoft.VisualStudio.VSConstants.S_OK> označuje, jestli seznam obsahuje výrazy, zatímco <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> označuje, že neexistují žádné výrazy k zobrazení.  
  
 Skutečné výrazů vrátila jsou názvy proměnných nebo parametry, které se zobrazují v tomto umístění v kódu. Tyto názvy se předávají vyhodnocovací filtr výrazů k získání hodnot a typy, které se zobrazí v **automobily** okno.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje implementaci <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> metoda, která načte seznam výrazů z <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodu pomocí z důvodu analýzy <xref:Microsoft.VisualStudio.Package.ParseReason>. Každý z výrazů je je uzavřen jako `TestVsEnumBSTR` , která implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR> rozhraní.  
  
 Všimněte si, že `GetAutoExpressionsCount` a `GetAutoExpression` metody jsou vlastních metod na `TestAuthoringSink` objektu a byly přidány k podpoře v tomto příkladu. Představují jeden ze způsobů ve výrazech, které přidá do `TestAuthoringSink` objekt analyzátorem (voláním <xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A> metoda) můžete přistupovat mimo analyzátor.  
  
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