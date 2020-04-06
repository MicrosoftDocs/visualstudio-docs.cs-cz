---
title: Osnova ve službě staršího jazyka | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- outlining
- language services [managed package framework], outlining
- outlining, supporting in language services [managed package framework]
ms.assetid: 7b5578b4-a20a-4b94-ad4c-98687ac133b9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: be485a0e7406d49c4dcce77958c720e0b62504b6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706815"
---
# <a name="outlining-in-a-legacy-language-service"></a>Osnova ve službě starší verze jazyka
Osnova umožňuje sbalit složitý program do přehledu nebo osnovy. Například v C# všechny metody mohou být sbaleny na jeden řádek, zobrazující pouze podpis metody. Kromě toho struktury a třídy lze sbalit zobrazit pouze názvy struktur a tříd. Uvnitř jedné metody lze sbalit komplexní logiku, která zobrazí celkový tok `foreach` `if`zobrazením `while`pouze prvního řádku příkazů, například , a .

 Starší jazykové služby jsou implementovány jako součást VSPackage, ale novější způsob implementace funkcí služby jazyka je použití rozšíření MEF. Další informace naleznete v [tématu Návod: Osnova](../../extensibility/walkthrough-outlining.md).

> [!NOTE]
> Doporučujeme, abyste co nejdříve začali používat nové rozhraní API editoru. Tím se zlepší výkon služby jazyka a umožní vám využít nové funkce editoru.

## <a name="enabling-support-for-outlining"></a>Povolení podpory pro osnovu
 Položka `AutoOutlining` registru je nastavena na 1, aby bylo možné automatické osnovy. Automatické osnovy nastaví analýzu celého zdroje při načtení nebo změně souboru za účelem identifikace skrytých oblastí a zobrazení osnovních glyfů. Osnova může být také řízena ručně uživatelem.

 Hodnotu položky `AutoOutlining` registru lze získat <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> prostřednictvím <xref:Microsoft.VisualStudio.Package.LanguagePreferences> vlastnosti ve třídě. Položku `AutoOutlining` registru lze inicializovat s <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> pojmenovaným parametrem atributu (podrobnosti naleznete v [tématu Registrace služby staršího jazyka).](../../extensibility/internals/registering-a-legacy-language-service1.md)

## <a name="the-hidden-region"></a>Skrytá oblast
 Chcete-li poskytnout osnovy, musí vaše jazyková služba podporovat skryté oblasti. Jedná se o rozsahy textu, které lze rozbalit nebo sbalit. Skryté oblasti mohou být odděleny standardními jazykovými symboly, například složenými závorkami, nebo vlastními symboly. Například C# má `#region` / `#endregion` pár, který vymezuje skryté oblasti.

 Skryté oblasti jsou spravovány správcem skrytých <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> oblastí, který je vystaven jako rozhraní.

 Osnova používá skryté <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion> oblasti rozhraní a obsahují rozsah skryté oblasti, aktuální viditelný stav a banner, který se má zobrazit při sbalení rozpětí.

 Analyzátor jazykových služeb <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> používá metodu k přidání nové skryté oblasti s <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> výchozím chováním pro skryté oblasti, zatímco metoda umožňuje přizpůsobit vzhled a chování osnovy. Jakmile jsou skryté oblasti uvedeny [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] do relace skryté oblasti, spravuje skryté oblasti pro jazykovou službu.

 Pokud potřebujete určit, kdy je relace skryté oblasti zničena, změní se skrytá oblast nebo se potřebujete ujistit, že je viditelná určitá skrytá oblast; musíte odvodit <xref:Microsoft.VisualStudio.Package.Source> třídu z třídy <xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A>a <xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A>přepsat <xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A>příslušné metody , , a , v uvedeném pořadí.

### <a name="example"></a>Příklad
 Zde je zjednodušený příklad vytváření skrytých oblastí pro všechny páry složených závorek. Předpokládá se, že jazyk poskytuje odpovídající složená závorka a že složená závorka, která mají být spárována, zahrnují alespoň složené závorky ({ a }). Tento přístup je pouze pro ilustrační účely. Úplné provedení by mělo úplné řešení <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>případů v . Tento příklad také ukazuje, <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> jak `true` dočasně nastavit předvolbu. Alternativou je zadat `AutoOutlining` pojmenovaný parametr `ProvideLanguageServiceAttribute` v atributu v jazykovém balíčku.

 Tento příklad předpokládá c# pravidla pro komentáře, řetězce a literály.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace MyLanguagePackage
{

    public class MyLanguageService : LanguageService
    {
        private LanguagePreferences m_preferences;

        public override LanguagePreferences  GetLanguagePreferences()
        {
            if (m_preferences == null)
            {
                m_preferences = new LanguagePreferences(this.Site,
                                                        typeof(MyLanguageService).GUID,
                                                        Name);
                m_preferences.Init();
                // Temporarily enabled auto-outlining
                m_preferences.AutoOutlining = true;
            }
            return m_preferences;
        }

        public override AuthoringScope  ParseSource(ParseRequest req)
        {
            Source source = (Source) this.GetSource(req.FileName);
            switch (req.Reason)
            {
               case ParseReason.HighlightBraces:
               case ParseReason.MatchBraces:
               case ParseReason.MemberSelectAndHighlightBraces:
                  if (source.Braces != null)
                  {
                      foreach (TextSpan[] brace in source.Braces)
                      {
                         if (brace.Length == 2)
                         {
                             if (req.Sink.HiddenRegions == true
                                   && source.GetText(brace[0]).Equals("{")
                                   && source.GetText(brace[1]).Equals("}"))
                             {
                                //construct a TextSpan of everything between the braces
                                TextSpan hideSpan = new TextSpan();
                                hideSpan.iStartIndex = brace[0].iStartIndex;
                                hideSpan.iStartLine = brace[0].iStartLine;
                                hideSpan.iEndIndex = brace[1].iEndIndex;
                                hideSpan.iEndLine = brace[1].iEndLine;
                                req.Sink.ProcessHiddenRegions = true;
                                req.Sink.AddHiddenRegion(hideSpan);
                             }
                             req.Sink.MatchPair(brace[0], brace[1], 1);
                         }
                         else if (brace.Length >= 3)
                             req.Sink.MatchTriple(brace[0], brace[1], brace[2], 1);
                  }
        }
                   break;
               default:
                   break;
      }
            // Must always return a valid AuthoringScope object.
            return new MyAuthoringScope();
        }
    }
}
```

## <a name="see-also"></a>Viz také
- [Funkce služby starší verze jazyka](../../extensibility/internals/legacy-language-service-features1.md)
- [Registrace služby starší verze jazyka](../../extensibility/internals/registering-a-legacy-language-service1.md)
