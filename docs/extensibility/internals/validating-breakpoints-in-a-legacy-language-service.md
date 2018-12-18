---
title: Ověřování zarážky ve službě jazyk starší | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoint validation
- language services [managed package framework], breakpoint validation
ms.assetid: a7e873cd-dfe1-474f-bda5-fd7532774b15
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 03bf1534789ba24e1bbf597874ea427057073b61
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31139367"
---
# <a name="validating-breakpoints-in-a-legacy-language-service"></a>Ověřování zarážky ve službě jazyk starší verze
Zarážku označuje, že spuštění programu by se měla zastavit na určitém místě, když je spuštěn v ladicí program. Uživatele můžete umístit zarážku na kterýkoli řádek v zdrojový soubor, protože editoru nemá žádné informace o co se považuje za platné umístění pro zarážky. Při spuštění ladicího programu všechny označený zarážky (označovaný jako čekající na vyřízení zarážky) je vázána na požadované místo v běžící aplikaci. Ve stejnou dobu, kdy se ověřují zarážky zajistit, aby se označit platný kód umístění. Například zarážky na komentář není platný, protože neexistuje žádný kód v tomto umístění ve zdrojovém kódu. Ladicí program zakáže neplatný zarážky.  
  
 Vzhledem k tomu, že služba jazyka ví o zdrojovém kódu, který se zobrazuje, může ověřit zarážky před spuštění ladicího programu. Je možné přepsat <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> metoda vrátí rozpětí určující platné umístění pro zarážky. Umístění zarážek stále ověření při spuštění ladicího programu, ale uživatel obdrží oznámení o neplatný zarážky bez čekání na načtení ladicího programu.  
  
## <a name="implementing-support-for-validating-breakpoints"></a>Implementace podporu pro ověřování zarážky  
  
-   <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> Metoda je uvedena pozici zarážku. Implementace musíte se rozhodnout, zda je platná umístění a znamenat, že to vrácením rozpětí textu, který identifikuje kód spojené s pozice řádku zarážce.  
  
-   Vrátí <xref:Microsoft.VisualStudio.VSConstants.S_OK> Pokud je platný, umístění nebo <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> Pokud není platný.  
  
-   Pokud platný zarážkou rozpětí textu zvýrazní společně s zarážku.  
  
-   Pokud zarážce je neplatný, zobrazí se chybová zpráva ve stavovém řádku.  
  
### <a name="example"></a>Příklad  
 Tento příklad ukazuje implementaci <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> metoda, která volá analyzátor získat rozpětí kódu (pokud existuje) do zadaného umístění.  
  
 Tento příklad předpokládá, že jste přidali `GetCodeSpan` metodu <xref:Microsoft.VisualStudio.Package.AuthoringSink> třídu, která ověřuje text rozpětí a vrátí `true` v případě platný zarážek umístění.  
  
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