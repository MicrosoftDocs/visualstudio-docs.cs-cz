---
title: Přeformátování kódu ve službě jazyk starší | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- reformatting code, supporting in language services [managed package framework]
- language services [managed package framework], reformatting code
ms.assetid: 08bb3375-8fef-4f4e-9efa-0d7333bab0eb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 392afbafc2ce15dbf7ee347efdf24ce1f7fe2301
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133186"
---
# <a name="reformatting-code-in-a-legacy-language-service"></a>Přeformátování kódu ve službě jazyk starší verze

V [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zdrojového kódu můžete naformátována pomocí normalizace použití odsazení a prázdný znak. To může zahrnovat vložení nebo odebrání mezery nebo karty na začátku každého řádku, přidání nové řádky mezi řádky nebo výměna prostory s tabulátory nebo karty s prostory.  
  
>**Poznámka:** vložení nebo odstranění znaky nového řádku může ovlivnit značek například zarážky a záložky, ale přidání nebo odebrání mezery nebo karty neovlivňuje značek.  
  
Uživatelé mohou spustit reformatting operaci výběrem **výběr formátu** nebo **formátovat dokument** z **Upřesnit** nabídce **upravit**nabídky. Reformatting operace se dá taky spustit při vložení fragmentu kódu nebo konkrétní znak. Například když zadáte pravé složené závorce v jazyce C#, všechno mezi odpovídajících složených závorek otevřít a zavřít závorek je automaticky zobrazují odsazené na správnou úroveň.
  
Při [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] odešle **výběr formátu** nebo **formátovat dokument** příkaz služba jazyka <xref:Microsoft.VisualStudio.Package.ViewFilter> třídy volání <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> metoda v <xref:Microsoft.VisualStudio.Package.Source> – třída. Pro podporu formátování, je nutné přepsat <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> metodu a zadejte vlastní formátování kódu.  
  
## <a name="enabling-support-for-reformatting"></a>Povolení podpory pro přeformátování  

Pro podporu formátování, `EnableFormatSelection` parametr <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> musí být nastavena na `true` při registraci vaší VSPackage. Tím se nastaví <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A> vlastnost `true`. <xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A> Vrátí metoda hodnotu této vlastnosti. Pokud vrátí hodnotu true, <xref:Microsoft.VisualStudio.Package.ViewFilter> třídy volání <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>.  
  
## <a name="implementing-reformatting"></a>Implementace přeformátování

K implementaci přeformátování, musí odvození třídy z <xref:Microsoft.VisualStudio.Package.Source> třídy a přepsat <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> metoda. <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> Objekt popisuje rozpětí k formátování a <xref:Microsoft.VisualStudio.Package.EditArray> objektu obsahuje úpravy provedené na rozpětí. Všimněte si, že tomuto rozpětí může být celý dokument. Ale vzhledem k tomu, že je pravděpodobně více změny provedené v rozpětí, všechny změny by měl být reverzibilního v rámci jedné akce. K tomuto účelu zabalení všechny změny v <xref:Microsoft.VisualStudio.Package.CompoundAction> objektu (viz část "Použití třídy CompoundAction" v tomto tématu).

### <a name="example"></a>Příklad  

Následující příklad zajistí, že existuje a jedna mezera po každé čárkami ve výběru, pokud je následován na kartě čárkou nebo je na konci řádku. Po odstranění se poslední čárkami na řádku koncové mezery. Najdete v části "Použití CompoundAction třídy" v tomto tématu najdete v části Jak tato metoda je volána z <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> metoda.  

```csharp 
using Microsoft.VisualStudio.Package;  
using Microsoft VisualStudio.TextManager.Interop;  
  
namespace MyLanguagePackage  
{  
    class MySource : Source  
    {  
        private void DoFormatting(EditArray mgr, TextSpan span)  
        {  
            // Make sure there is one space after every comma unless followed  
            // by a tab or comma is at end of line.  
            IVsTextLines pBuffer = GetTextLines();  
            if (pBuffer != null)  
            {  
                int    startIndex = span.iStartIndex;  
                int    endIndex   = 0;  
                string line       = "";  
                // Loop over all lines in span  
                for (int i = span.iStartLine; i <= span.iEndLine; i++)  
                {  
                    if (i < span.iEndLine)  
                    {  
                        pBuffer.GetLengthOfLine(i, out endIndex);  
                    }  
                    else  
                    {  
                        endIndex = span.iEndIndex;  
                    }  
                    pBuffer.GetLineText(i, startIndex, i, endIndex, out line);  
  
                    if (line.Length > 0)  
                    {  
                        int index = 0;  
                        // Loop over all commas in line  
                        while ((index = line.IndexOf(',', index)) != -1)  
                        {  
                            int spaceIndex = index + 1;  
                            // Determine how many spaces after comma  
                            while (spaceIndex < line.Length && line[spaceIndex] == ' ')  
                            {  
                                ++spaceIndex;  
                            }  
  
                            int      spaceCount      = spaceIndex - (index + 1);  
                            string   replacementText = " ";  
                            bool     fDoEdit         = true;  
                            TextSpan editTextSpan    = new TextSpan();  
  
                            editTextSpan.iStartLine  = i;  
                            editTextSpan.iEndLine    = i;  
                            editTextSpan.iStartIndex = index + 1;  
  
                            if (spaceIndex == line.Length)  
                            {  
                                if (spaceCount > 0)  
                                {  
                                    // Delete spaces after a comma at end of line  
                                    editTextSpan.iEndIndex = spaceIndex;  
                                    replacementText = "";  
                                }  
                                else  
                                {  
                                    // Otherwise, do not add spaces if comma is  
                                    // at end of line.  
                                    fDoEdit = false;  
                                }  
                            }  
                            else if (spaceCount == 0)  
                            {  
                                if (spaceIndex < line.Length && line[spaceIndex] == '\t')  
                                {  
                                    // Do not insert space if a tab follows  
                                    // a comma.  
                                    fDoEdit = false;  
                                }  
                                else  
                                {  
                                    // No space after comma so add a space.  
                                    editTextSpan.iEndIndex = index + 1;  
                                }  
                            }  
                            else if (spaceCount > 1)  
                            {  
                                // More than one space after comma, replace  
                                // with a single space.  
                                editTextSpan.iEndIndex = spaceIndex;  
                            }  
                            else  
                            {  
                                // Single space after a comma and not at end  
                                // of the line, leave it alone.  
                                fDoEdit = false;  
                            }  
                            if (fDoEdit)  
                            {  
                                // Add edit operation  
                                mgr.Add(new EditSpan(editTextSpan, replacementText));  
                            }  
                            index = spaceIndex;  
                        }  
                    }  
                    startIndex = 0; // All subsequent lines start at 0  
                }  
                // Apply all edits  
                mgr.ApplyEdits();  
            }  
        }  
    }  
}  
```  
  
## <a name="using-the-compoundaction-class"></a>Používání třídy CompoundAction  
 
Všechny přeformátování udělat na části kódu, musí být reverzibilního v rámci jedné akce. Můžete to provést pomocí <xref:Microsoft.VisualStudio.Package.CompoundAction> třídy. Tato třída zabalí sadu operací upravit na textová vyrovnávací paměť do jednoho upravit operace.  
  
### <a name="example"></a>Příklad

Tady je příklad použití <xref:Microsoft.VisualStudio.Package.CompoundAction> třídy. Podívejte se na příklad v části "Implementace podporu pro formátování" v tomto tématu příklad `DoFormatting` metoda.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft VisualStudio.TextManager.Interop;  
  
namespace MyLanguagePackage  
{  
    class MySource : Source  
    {  
        public override void ReformatSpan(EditArray mgr, TextSpan span)  
        {  
            string description = "Reformat code";  
            CompoundAction ca = new CompoundAction(this, description);  
            using (ca)  
            {  
                ca.FlushEditActions();      // Flush any pending edits  
                DoFormatting(mgr, span);    // Format the span  
            }  
        }  
    }  
}  
```  

## <a name="see-also"></a>Viz také

[Funkce služby starší verze jazyka](legacy-language-service-features1.md)