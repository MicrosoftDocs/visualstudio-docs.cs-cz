---
title: Přeformátování kódu ve službě staršího jazyka | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705914"
---
# <a name="reformatting-code-in-a-legacy-language-service"></a>Přeformátování kódu ve službě starší verze jazyka

Ve [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zdrojovém kódu lze přeformátovat normalizací použití odsazení a mezery. To může zahrnovat vložení nebo odebrání mezer nebo tabulátorů na začátek každého řádku, přidání nových čar mezi řádky nebo nahrazení mezer pomocí tabulátorů nebo tabulátorů mezerami.

> [!NOTE]
> Vkládání nebo odstraňování znaků nového řádku může ovlivnit značky, jako jsou zarážky a záložky, ale přidání nebo odebrání mezer nebo tabulátorů nemá vliv na značky.

Uživatelé mohou zahájit operaci přeformátování výběrem **nebo** **Formát dokumentu** z nabídky Upřesnit v nabídce **Úpravy.** **Edit** Přeformátování operace může být také aktivována při vložení fragmentu kódu nebo konkrétní znak. Například při zadání uzavírací složená závorka v C#, vše mezi odpovídající otevřenou složenou závorku a zavřít složená závorka je automaticky odsazen na správnou úroveň.

Když [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] odešle příkaz **Formát výběru** nebo **Formát dokumentu** do jazykové služby, <xref:Microsoft.VisualStudio.Package.ViewFilter> třída volá metodu <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> ve <xref:Microsoft.VisualStudio.Package.Source> třídě. Chcete-li podpořit formátování, <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> musíte přepsat metodu a zadat vlastní kód formátování.

## <a name="enabling-support-for-reformatting"></a>Povolení podpory pro přeformátování

Pro podporu formátování, `EnableFormatSelection` parametr <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> musí být nastavena na `true` při registraci VSPackage. Tím <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A> nastavíte `true`vlastnost na . Metoda <xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A> vrátí hodnotu této vlastnosti. Pokud vrátí hodnotu <xref:Microsoft.VisualStudio.Package.ViewFilter> true, <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>třída volá .

## <a name="implementing-reformatting"></a>Provádění přeformátování

Chcete-li implementovat přeformátování, musíte <xref:Microsoft.VisualStudio.Package.Source> odvodit <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> třídu z třídy a přepsat metodu. Objekt <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> popisuje rozsah formátování a <xref:Microsoft.VisualStudio.Package.EditArray> objekt obsahuje úpravy provedené v rozsahu. Všimněte si, že toto rozpětí může být celý dokument. Vzhledem k tomu, že je však pravděpodobné, že bude provedeno více změn v rozsahu, všechny změny by měly být reverzibilní v jedné akci. Chcete-li to provést, <xref:Microsoft.VisualStudio.Package.CompoundAction> zalomit všechny změny v objektu (viz "Použití CompoundAction Class" části v tomto tématu).

### <a name="example"></a>Příklad

Následující příklad zajišťuje, že je jedna mezera za každou čárkou ve výběru, pokud čárka následuje kartu nebo je na konci řádku. Koncové mezery za poslední čárkou v řádku budou odstraněny. Naleznete v části "Použití třídy CompoundAction" v tomto tématu <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> zobrazíte, jak je tato metoda volána z metody.

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

Všechny přeformátování provedené na části kódu by měly být reverzibilní v jedné akci. To lze provést pomocí <xref:Microsoft.VisualStudio.Package.CompoundAction> třídy. Tato třída zalomí sadu operací úprav na vyrovnávací paměti textu do jedné operace úprav.

### <a name="example"></a>Příklad

Zde je příklad použití třídy. <xref:Microsoft.VisualStudio.Package.CompoundAction> Příklad metody naleznete v příkladu v části Implementující podpora formátování v `DoFormatting` tomto tématu.

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
