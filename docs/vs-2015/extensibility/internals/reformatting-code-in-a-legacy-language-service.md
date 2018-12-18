---
title: Přeformátování kódu ve službě starší verze jazyka | Dokumentace Microsoftu
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
- reformatting code, supporting in language services [managed package framework]
- language services [managed package framework], reformatting code
ms.assetid: 08bb3375-8fef-4f4e-9efa-0d7333bab0eb
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 95b878448904c194bd758d266e67599369502fe6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51779265"
---
# <a name="reformatting-code-in-a-legacy-language-service"></a>Přeformátování kódu ve službě starší verze jazyka
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

V [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zdrojový kód můžete naformátována pomocí normalizace použití odsazení a mezery. To může zahrnovat vkládání nebo odebrání mezerami či tabulátory na začátku každého řádku, přidat nové řádky mezi řádky nebo nahrazení mezery tabulátory nebo tabulátory mezerami.  
  
> [!NOTE]
>  **Poznámka:** vložení nebo odstranění znaky nového řádku může ovlivnit značky, jako je například zarážky a záložky, ale přidáním nebo odebráním mezerami či tabulátory nemá vliv na značky.  
  
 Uživatelé mohou spustit operaci reformatting tak, že vyberete **výběr formátu** nebo **formátovat dokument** z **Upřesnit** nabídce **upravit**nabídky. Reformatting operace se dá taky spustit při vložení fragmentu kódu nebo konkrétní znak. Například při psaní pravou složenou závorku v jazyce C# všechno mezi odpovídající levou složenou závorku a Zavřít složenou závorkou je automaticky odsazený správnou úroveň.  
  
 Při [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] odešle **výběr formátu** nebo **formátovat dokument** příkaz ke službě jazykového <xref:Microsoft.VisualStudio.Package.ViewFilter> třídy volání <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> metodu <xref:Microsoft.VisualStudio.Package.Source> třídy. Pro podporu formátování, je nutné přepsat <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> metodu a zadejte vlastní formátování kódu.  
  
## <a name="enabling-support-for-reformatting"></a>Povolení podpory přeformátovat  
 Pro podporu formátování, `EnableFormatSelection` parametr <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> musí být nastaveno na `true` při registraci vašeho balíčku VSPackage. Tím se nastaví <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A> vlastnost `true`. <xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A> Vrátí metoda hodnotu této vlastnosti. Pokud vrátí hodnotu PRAVDA, <xref:Microsoft.VisualStudio.Package.ViewFilter> třídy volání <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>.  
  
## <a name="implementing-reformatting"></a>Implementace přeformátování  
 K implementaci přeformátování, musíte odvodit třídu z <xref:Microsoft.VisualStudio.Package.Source> třídy a přepsat <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> metody. <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> Objektu popisuje rozpětí pro formátování a <xref:Microsoft.VisualStudio.Package.EditArray> obsahuje úpravy provedené v rozpětí. Všimněte si, že tomuto rozpětí může být celý dokument. Ale protože je pravděpodobně více změn provedených v rozsahu, všechny změny by měl být reverzibilního v rámci jedné akce. K tomuto účelu zabalení všechny změny v <xref:Microsoft.VisualStudio.Package.CompoundAction> objektu (viz oddíl "Horizontálních oddílů pomocí třídy CompoundAction" v tomto tématu).  
  
### <a name="example"></a>Příklad  
 Následující příklad zajistí, že jedna mezera za každou čárku ve výběru, pokud není čárka je následována na kartě nebo na konci řádku. Po odstranění se poslední čárka v řádku koncové mezery. V části "Použití CompoundAction třídy" v tomto tématu, jak tato metoda je volána z <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> metody.  
  
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
 Všechny přeformátování hotové práce na části kódu by měla být v rámci jedné akce vrátit zpět. Můžete to udělat pomocí <xref:Microsoft.VisualStudio.Package.CompoundAction> třídy. Tato třída zabalí sadu operací úpravy na textovou vyrovnávací paměť do úprav jednu operaci.  
  
### <a name="example"></a>Příklad  
 Tady je příklad, jak používat <xref:Microsoft.VisualStudio.Package.CompoundAction> třídy. Podívejte se na příklad v části "Implementace podpory pro formátování" v tomto tématu příklad `DoFormatting` metody.  
  
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
 [Funkce služby starší verze jazyka](../../extensibility/internals/legacy-language-service-features1.md)

