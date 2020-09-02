---
title: Přeformátování kódu ve službě starší verze jazyka | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- reformatting code, supporting in language services [managed package framework]
- language services [managed package framework], reformatting code
ms.assetid: 08bb3375-8fef-4f4e-9efa-0d7333bab0eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dd3e83c7299298b16a6fb3178b189479a80e1728
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80705914"
---
# <a name="reformatting-code-in-a-legacy-language-service"></a>Přeformátování kódu ve službě starší verze jazyka

Ve [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zdrojovém kódu lze přeformátovat normalizací použití odrážek a prázdných znaků. To může zahrnovat vložení nebo odebrání mezer nebo karet na začátku každého řádku, přidání nových řádků mezi řádky nebo nahrazení mezer tabulátory nebo tabulátory mezerami.

> [!NOTE]
> Vložení nebo odstranění znaků nového řádku může ovlivnit značky, jako jsou zarážky a záložky, ale přidávání nebo odebírání mezer nebo karet nemá vliv na značky.

Uživatelé mohou operaci přeformátování spustit výběrem možnosti **Formátovat výběr** nebo **formátovat dokument** z nabídky **Upřesnit** v nabídce **Upravit** . Operaci přeformátování lze také aktivovat při vložení fragmentu kódu nebo konkrétního znaku. Například když zadáte pravou závorku v jazyce C#, vše mezi odpovídající levou složenou závorkou a pravou složenou závorkou se automaticky odsadí na správnou úroveň.

Při [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] odeslání příkazu **formátu výběru** nebo **formátu dokumentu** jazykové službě <xref:Microsoft.VisualStudio.Package.ViewFilter> volá třída <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> metodu ve <xref:Microsoft.VisualStudio.Package.Source> třídě. Pro podporu formátování musíte přepsat <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> metodu a dodat vlastní kód formátování.

## <a name="enabling-support-for-reformatting"></a>Povolení podpory pro přeformátování

Aby bylo možné podporovat formátování, `EnableFormatSelection` parametr <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> musí být nastaven na hodnotu `true` při registraci VSPackage. Tím se <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A> vlastnost nastaví na `true` . <xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A>Metoda vrátí hodnotu této vlastnosti. Pokud vrátí hodnotu true, <xref:Microsoft.VisualStudio.Package.ViewFilter> třída volá <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> .

## <a name="implementing-reformatting"></a>Implementace přeformátování

Chcete-li implementovat přeformátování, je nutné odvodit třídu z <xref:Microsoft.VisualStudio.Package.Source> třídy a přepsat <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> metodu. <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan>Objekt popisuje rozsah pro formátování a <xref:Microsoft.VisualStudio.Package.EditArray> objekt obsahuje úpravy provedené na rozsahu. Všimněte si, že tento rozsah může být celý dokument. Vzhledem k tomu, že v rozpětí jsou pravděpodobně provedeny různé změny, všechny změny by měly být v jedné akci vratné. Chcete-li to provést, zabalte všechny změny v <xref:Microsoft.VisualStudio.Package.CompoundAction> objektu (viz část "použití třídy CompoundAction" v tomto tématu).

### <a name="example"></a>Příklad

Následující příklad zajišťuje jedno místo za každou čárkou ve výběru, pokud čárka není následována tabulátorem nebo na konci řádku. Koncové mezery za poslední čárkou na řádku se odstraní. Informace o tom, jak je tato metoda volána z metody, naleznete v části "použití třídy CompoundAction" v tomto tématu <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> .

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

## <a name="using-the-compoundaction-class"></a>Použití třídy CompoundAction

Všechna přeformátování provedené u oddílu kódu by měla být v rámci jedné akce vratná. To lze provést pomocí <xref:Microsoft.VisualStudio.Package.CompoundAction> třídy. Tato třída zalomí sadu operací úprav pro textovou vyrovnávací paměť do jediné operace Edit.

### <a name="example"></a>Příklad

Zde je příklad použití <xref:Microsoft.VisualStudio.Package.CompoundAction> třídy. Příklad metody najdete v části "implementace podpory pro formátování" v tomto tématu `DoFormatting` .

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

- [Funkce služby starší verze jazyka](legacy-language-service-features1.md)
