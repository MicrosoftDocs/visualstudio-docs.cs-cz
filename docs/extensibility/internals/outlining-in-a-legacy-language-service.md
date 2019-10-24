---
title: Sbalení ve službě starší verze jazyka | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- outlining
- language services [managed package framework], outlining
- outlining, supporting in language services [managed package framework]
ms.assetid: 7b5578b4-a20a-4b94-ad4c-98687ac133b9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6b2ba55a2e77a1f7261812a181ad780c2ef2b71
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726179"
---
# <a name="outlining-in-a-legacy-language-service"></a>Osnova ve službě starší verze jazyka
Díky osnově je možné sbalit složitý program na přehled nebo osnovu. Například C# všechny metody mohou být sbaleny do jednoho řádku, který zobrazuje pouze signaturu metody. Kromě toho mohou být struktury a třídy sbaleny, aby zobrazovaly pouze názvy struktur a tříd. V rámci jediné metody může být komplexní logika sbalena k zobrazení celkového toku zobrazením pouze prvního řádku příkazů, jako jsou `foreach`, `if` a `while`.

 Starší jazykové služby jsou implementovány jako součást sady VSPackage, ale novější způsob, jak implementovat funkce jazykové služby, je použít rozšíření MEF. Další informace najdete v tématu [Návod: sbalení](../../extensibility/walkthrough-outlining.md).

> [!NOTE]
> Doporučujeme začít používat nové rozhraní API editoru co nejrychleji. Tím se vylepšit výkon vaší jazykové služby a umožní vám využít nové funkce editoru.

## <a name="enabling-support-for-outlining"></a>Povolení podpory pro sbalení
 Pokud chcete povolit automatické sbalení, je položka registru `AutoOutlining` nastavena na hodnotu 1. Automatické sbalení nastaví analýzu celého zdroje při načtení nebo změně souboru za účelem identifikace skrytých oblastí a zobrazení glyfů osnovy. Sbalení lze také kontrolovat ručně uživatelem.

 Hodnotu položky registru `AutoOutlining` lze získat prostřednictvím vlastnosti <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> třídy <xref:Microsoft.VisualStudio.Package.LanguagePreferences>. Položku registru `AutoOutlining` lze inicializovat pomocí pojmenovaného parametru pro atribut <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> (podrobnosti naleznete v tématu [Registrace služby starší verze jazyka](../../extensibility/internals/registering-a-legacy-language-service1.md) ).

## <a name="the-hidden-region"></a>Skrytá oblast
 Aby se zajistilo sbalení, musí vaše jazyková služba podporovat skryté oblasti. Jedná se o rozsah textu, který lze rozbalit nebo sbalit. Skryté oblasti můžou být oddělené standardními jazykovými symboly, jako jsou složené závorky nebo vlastní symboly. Například C# má `#region` / `#endregion` dvojici, která odděluje skrytou oblast.

 Skryté oblasti se spravují pomocí skrytého správce oblastí, který je vystavený jako rozhraní <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>.

 Sbalení používá skryté oblasti rozhraní <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion> a obsahuje rozpětí skryté oblasti, aktuálního viditelného stavu a banner, který se zobrazí při sbalení rozpětí.

 Analyzátor služby jazyka používá metodu <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> k přidání nové skryté oblasti s výchozím chováním pro skryté oblasti, zatímco metoda <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> umožňuje přizpůsobit vzhled a chování obrysu. Jakmile budou skryté oblasti předány relaci skryté oblasti, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] spravuje skryté oblasti pro službu jazyka.

 Pokud potřebujete určit, kdy má být relace skryté oblasti zničena, dojde ke změně skryté oblasti nebo je nutné zajistit, aby byla viditelná konkrétní skrytá oblast. je nutné odvodit třídu z třídy <xref:Microsoft.VisualStudio.Package.Source> a přepsat příslušné metody, <xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A>, <xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A> a <xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A>, v uvedeném pořadí.

### <a name="example"></a>Příklad
 Tady je zjednodušený příklad vytváření skrytých oblastí pro všechny páry složených závorek. Předpokládá se, že jazyk poskytuje párování složených závorek a že složené závorky obsahují aspoň složené závorky ({a}). Tento přístup slouží pouze pro ilustrativní účely. Úplná implementace by měla kompletní zpracování případů v <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>. Tento příklad také ukazuje, jak nastavit předvolbu <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> pro dočasné `true`. Alternativou je zadat `AutoOutlining` pojmenovaný parametr v atributu `ProvideLanguageServiceAttribute` ve vašem jazykovém balíčku.

 Tento příklad předpokládá C# pravidla pro komentáře, řetězce a literály.

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

## <a name="see-also"></a>Viz také:
- [Funkce služby starší verze jazyka](../../extensibility/internals/legacy-language-service-features1.md)
- [Registrace služby starší verze jazyka](../../extensibility/internals/registering-a-legacy-language-service1.md)