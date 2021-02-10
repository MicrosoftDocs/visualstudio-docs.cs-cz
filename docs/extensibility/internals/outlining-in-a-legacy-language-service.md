---
title: Sbalení ve službě starší verze jazyka | Microsoft Docs
description: Naučte se, jak podporovat sbalení prostřednictvím implementace skrytých oblastí ve službě starší verze jazyka.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- outlining
- language services [managed package framework], outlining
- outlining, supporting in language services [managed package framework]
ms.assetid: 7b5578b4-a20a-4b94-ad4c-98687ac133b9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8a2f00cc4e968551983a8b943d256b49e33d7d6d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99954628"
---
# <a name="outlining-in-a-legacy-language-service"></a>Osnova ve službě starší verze jazyka
Díky osnově je možné sbalit složitý program na přehled nebo osnovu. Například v jazyce C# mohou být všechny metody sbaleny do jediného řádku, který zobrazuje pouze signaturu metody. Kromě toho mohou být struktury a třídy sbaleny, aby zobrazovaly pouze názvy struktur a tříd. V rámci jediné metody může být komplexní logika sbalena k zobrazení celkového toku zobrazením pouze prvního řádku příkazů, jako jsou `foreach` , `if` a `while` .

 Starší jazykové služby jsou implementovány jako součást sady VSPackage, ale novější způsob, jak implementovat funkce jazykové služby, je použít rozšíření MEF. Další informace najdete v tématu [Návod: sbalení](../../extensibility/walkthrough-outlining.md).

> [!NOTE]
> Doporučujeme začít používat nové rozhraní API editoru co nejrychleji. Tím se vylepšit výkon vaší jazykové služby a umožní vám využít nové funkce editoru.

## <a name="enabling-support-for-outlining"></a>Povolení podpory pro sbalení
 `AutoOutlining`Položka registru je nastavena na hodnotu 1, aby bylo možné povolit automatické sbalení. Automatické sbalení nastaví analýzu celého zdroje při načtení nebo změně souboru za účelem identifikace skrytých oblastí a zobrazení glyfů osnovy. Sbalení lze také kontrolovat ručně uživatelem.

 Hodnotu `AutoOutlining` položky registru lze získat prostřednictvím <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> vlastnosti <xref:Microsoft.VisualStudio.Package.LanguagePreferences> třídy. `AutoOutlining`Položku registru lze inicializovat pomocí pojmenovaného parametru <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> atributu (podrobnosti naleznete v tématu [Registrace služby starší verze jazyka](../../extensibility/internals/registering-a-legacy-language-service1.md) ).

## <a name="the-hidden-region"></a>Skrytá oblast
 Aby se zajistilo sbalení, musí vaše jazyková služba podporovat skryté oblasti. Jedná se o rozsah textu, který lze rozbalit nebo sbalit. Skryté oblasti můžou být oddělené standardními jazykovými symboly, jako jsou složené závorky nebo vlastní symboly. Například jazyk C# má `#region` / `#endregion` dvojici, která odděluje skrytou oblast.

 Skryté oblasti se spravují pomocí skrytého správce oblastí, který je vystavený jako <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> rozhraní.

 Osnova používá skryté oblasti <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion> rozhraní a obsahuje rozpětí skryté oblasti, aktuálního viditelného stavu a banner, který se zobrazí při sbalení rozpětí.

 Analyzátor služby jazyka používá <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> metodu k přidání nové skryté oblasti s výchozím chováním pro skryté oblasti, zatímco <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> Metoda umožňuje přizpůsobit vzhled a chování obrysu. Jakmile budou skryté oblasti předány relaci skryté oblasti, aplikace [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] spravuje skryté oblasti pro jazykovou službu.

 Pokud potřebujete určit, kdy má být relace skryté oblasti zničena, dojde ke změně skryté oblasti nebo je nutné zajistit, aby byla viditelná konkrétní skrytá oblast. musíte odvodit třídu z <xref:Microsoft.VisualStudio.Package.Source> třídy a přepsat vhodné metody, <xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A> , <xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A> a v <xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A> uvedeném pořadí.

### <a name="example"></a>Příklad
 Tady je zjednodušený příklad vytváření skrytých oblastí pro všechny páry složených závorek. Předpokládá se, že jazyk poskytuje párování složených závorek a že složené závorky obsahují aspoň složené závorky ({a}). Tento přístup slouží pouze pro ilustrativní účely. Úplná implementace by měla kompletní zpracování případů v <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> . Tento příklad také ukazuje, jak dočasně nastavit <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> Předvolby `true` . Alternativou je zadat `AutoOutlining` pojmenovaný parametr v `ProvideLanguageServiceAttribute` atributu ve vašem jazykovém balíčku.

 Tento příklad předpokládá pravidla jazyka C# pro komentáře, řetězce a literály.

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
