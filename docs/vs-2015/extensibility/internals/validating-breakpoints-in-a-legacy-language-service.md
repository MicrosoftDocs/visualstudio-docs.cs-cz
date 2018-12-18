---
title: Ověřování zarážek ve službě starší verze jazyka | Dokumentace Microsoftu
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
- breakpoint validation
- language services [managed package framework], breakpoint validation
ms.assetid: a7e873cd-dfe1-474f-bda5-fd7532774b15
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0868e516720fd32a445f60f05f345936d24d6d7a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51734971"
---
# <a name="validating-breakpoints-in-a-legacy-language-service"></a>Ověřování zarážek ve službě starší verze jazyka
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zarážky označuje, že spuštění programu by se měla zastavit v určitém místě, když je spuštěn v ladicí program. Uživatele můžete umístit zarážky na kterýkoli řádek v ve zdrojovém souboru, protože nemá žádné informace o tom, co platné umístění zarážky editoru. Když ladicí program se spustí, všechny označené zarážky (označované jako čekajících zarážek) jsou vázány na příslušné umístění v běžící aplikaci. Ve stejnou dobu, kterou zarážek se ověří a zkontrolujte, že se označení umístění platný kód. Například zarážky na komentář není platný, protože není na tomto místě ve zdrojovém kódu žádný kód. Ladicí program se zakáže neplatný zarážky.  
  
 Protože služba jazyka ví o zdrojovém kódu se zobrazí, předtím, než se spustí ladicí program může ověřit zarážky. Je možné přepsat <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> metoda vrátí rozpětí určující platné umístění zarážky. Umístění zarážky stále ověření při spuštění ladicího programu, ale uživatel je informován o neplatný zarážky bez čekání na ladicí program načíst.  
  
## <a name="implementing-support-for-validating-breakpoints"></a>Implementace podporu pro ověřování zarážek  
  
-   <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> Metoda je uvedena umístění zarážky. Implementace musíte rozhodnout, zda je platná umístění a označující, že to tak, že vrací rozpětí textu, který identifikuje kód přidružený k řádku pozici zarážku.  
  
-   Vrátí <xref:Microsoft.VisualStudio.VSConstants.S_OK> Pokud je toto umístění platné, nebo <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> Pokud není platná.  
  
-   Pokud zarážka je platný rozsah textu je zvýrazněn spolu s zarážku.  
  
-   Pokud zarážka není platná, zobrazí se chybová zpráva ve stavovém řádku.  
  
### <a name="example"></a>Příklad  
 Tento příklad ukazuje implementaci <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> metodu, která volá analyzátor, který má získat délka kódu (pokud existuje) v zadaném umístění.  
  
 Tento příklad předpokládá, že jste přidali `GetCodeSpan` metodu <xref:Microsoft.VisualStudio.Package.AuthoringSink> třídu, která ověřuje text rozpětí a vrátí `true` Pokud se jedná o platný zarážku umístění.  
  
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
 [Funkce služby starší verze jazyka](../../extensibility/internals/legacy-language-service-features1.md)

