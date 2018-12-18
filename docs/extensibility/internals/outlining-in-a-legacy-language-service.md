---
title: Osnova ve službě jazyk starší | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- outlining
- language services [managed package framework], outlining
- outlining, supporting in language services [managed package framework]
ms.assetid: 7b5578b4-a20a-4b94-ad4c-98687ac133b9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b899f53ba6b2a0b58997cc51a83a0d9ca8480e63
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135648"
---
# <a name="outlining-in-a-legacy-language-service"></a>Osnova ve službě jazyk starší verze
Osnova umožňuje sbalit komplexní program do přehled nebo outline. Například v jazyce C# všechny metody lze sbalit na jeden řádek, zobrazuje pouze podpis metody. Kromě toho struktury a třídy lze sbalit zobrazit pouze názvy třídy a struktury. V jedné metody, lze sbalit komplexní logiku k zobrazení celkového toku zobrazením pouze první řádek příkazy `foreach`, `if`, a `while`.  
  
 Starší verze jazyka služby jsou implementovány jako součást VSPackage, ale novější způsob implementace funkce služby jazyk je použití MEF rozšíření. Další informace naleznete v tématu [návod: vytvoření přehledu](../../extensibility/walkthrough-outlining.md).  
  
> [!NOTE]
>  Doporučujeme vám, že začnete používat co nejdříve editoru nové rozhraní API. Tím zvýšit výkon služby jazyk a umožňují využívat výhod nových funkcí editoru.  
  
## <a name="enabling-support-for-outlining"></a>Povolení podpory pro osnovy  
 `AutoOutlining` Položky registru povolit automatické sbalení nastavena na hodnotu 1. Analýzy celého zdroje automatické sbalení nastaví, když je načten nebo změnit, aby bylo možné identifikovat oblasti skrytá a zobrazit popisující glyfy soubor. Osnova lze také řídit ručně uživatelem.  
  
 Hodnota `AutoOutlining` záznam v registru můžete získat prostřednictvím <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> vlastnost na <xref:Microsoft.VisualStudio.Package.LanguagePreferences> třídy. `AutoOutlining` Záznam v registru můžete inicializovat pomocí pojmenovaného parametr, který se <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> atribut (v tématu [registrace služby jazyk starší](../../extensibility/internals/registering-a-legacy-language-service1.md) podrobnosti).  
  
## <a name="the-hidden-region"></a>Skrytá oblast  
 Zajistit osnovy vaše služba jazyka musí podporovat skrytá oblasti. Jedná se o rozpětí textu, které můžete rozbalit nebo sbalit. Skrytá oblasti můžete oddělený standardní jazyk symboly, například složené závorky, nebo vlastní symboly. Například C# má `#region` / `#endregion` pár oddělující Skrytá oblast.  
  
 Skrytá oblasti spravuje manažera Skrytá oblast, která je k dispozici jako <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> rozhraní.  
  
 Osnova používá skrytá oblasti <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion> rozhraní a obsahovat rozpětí oblasti skryté, aktuální stav viditelné a Banner informující o která se má zobrazit při sbalené rozpětí.  
  
 Používá služba analyzátor jazyka <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> metodu za účelem přidání nové skryté oblasti s výchozí chování pro skrytý oblasti při <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> metoda umožňuje přizpůsobit vzhled a chování obrysu. Jakmile skrytá oblasti jsou uvedeny k relaci Skrytá oblast, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] spravuje skrytá oblasti pro službu jazyka.  
  
 Pokud potřebujete k určení, kdy zničena relace Skrytá oblast, skrytý oblast mění, nebo je potřeba Ujistěte se, že konkrétní Skrytá oblast je viditelná; musí být odvozen od třídy <xref:Microsoft.VisualStudio.Package.Source> třídy a přepsat příslušné metody <xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A>, <xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A>, a <xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A>, v uvedeném pořadí.  
  
### <a name="example"></a>Příklad  
 Zde je příklad zjednodušené vytváření skrytá oblasti pro všechny páry složené závorky. Předpokládá se, že jazyk poskytuje závorky a složené závorky lze porovnat zahrnovat aspoň složené závorky ({a}). Tento přístup je pouze pro ilustraci. Úplnou implementaci by měla mít dokončení zpracování případů v <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>. Tento příklad také ukazuje, jak nastavit <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> preference `true` dočasně. Další možností je zadat `AutoOutlining` s názvem v parametru `ProvideLanguageServiceAttribute` atribut v jazykovou sadu.  
  
 Tento příklad předpokládá pravidla C# pro komentáře, řetězce a literály.  
  
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
 [Funkce služby starší verze jazyka](../../extensibility/internals/legacy-language-service-features1.md)   
 [Registrace služby jazyk starší verze](../../extensibility/internals/registering-a-legacy-language-service1.md)