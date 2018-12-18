---
title: Osnova ve službě starší verze jazyka | Dokumentace Microsoftu
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
- outlining
- language services [managed package framework], outlining
- outlining, supporting in language services [managed package framework]
ms.assetid: 7b5578b4-a20a-4b94-ad4c-98687ac133b9
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 356b3d49fa8eb74ef2352e6ba36597d1c39fecf4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51751533"
---
# <a name="outlining-in-a-legacy-language-service"></a>Osnova ve službě starší verze jazyka
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Sbalování umožňuje sbalit složitý program do přehled nebo osnovy. Například v jazyce C# všechny metody lze sbalit do jednoho řádku zobrazující pouze podpis metody. Kromě toho třídy a struktury mohou být sbalena zobrazit pouze názvy třídy a struktury. Uvnitř jedinou metodu, mohou být sbalena komplexní logiku tak celkový tok zobrazením pouze první řádek příkazy `foreach`, `if`, a `while`.  
  
 Služby starší verze jazyka jsou implementovány jako součást sady VSPackage, ale novější způsob implementace funkce služba jazyka je pro použití rozšíření MEF. Další informace najdete v tématu [návod: sbalení](../../extensibility/walkthrough-outlining.md).  
  
> [!NOTE]
>  Doporučujeme vám, že začnete používat nový editor API co nejdříve. Tím vylepšíme výkonu vaší služby jazyka a umožňují využívat nové funkce editoru.  
  
## <a name="enabling-support-for-outlining"></a>Povolení podpory pro sbalení  
 `AutoOutlining` Položky registru je nastavená na 1, chcete-li povolit automatické sbalování. Automatické sbalování nastaví analýzy celého zdroje při načtení nebo změnit, aby bylo možné identifikovat skryté regiony a zobrazit sbalování glyfy souboru. Sbalení je možné řídit také ručně uživatelem.  
  
 Hodnota `AutoOutlining` záznam v registru můžete získat prostřednictvím <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> vlastnost <xref:Microsoft.VisualStudio.Package.LanguagePreferences> třídy. `AutoOutlining` Záznam v registru mohou být inicializovány pomocí pojmenovaný parametr <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> atribut (naleznete v tématu [registrace služby starší verze jazyka](../../extensibility/internals/registering-a-legacy-language-service1.md) podrobnosti).  
  
## <a name="the-hidden-region"></a>Skrytých oblastí:  
 Pokud chcete poskytnout, osnovy, musí podporovat vaše služba jazyka skryté regiony. Jedná se o rozpětí textu, který lze rozbalit nebo sbalit. Skryté regiony můžete být oddělené jazyka podle standardu symboly, jako je například složených závorek, nebo vlastní symboly. Například C# má `#region` / `#endregion` pár, který odděluje citaci skryté oblasti.  
  
 Skryté regiony spravuje počet skrytých oblastí: manažera, která je vystavena jako <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> rozhraní.  
  
 Sbalování používá skryté regiony <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion> rozhraní a obsahovat rozpětí skrytých oblastí, aktuální stav viditelnosti a banner, který má být zobrazen, pokud je značka span sbalený.  
  
 Používá službu analyzátoru jazyka <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> způsob, jak přidat novou oblast skryté pomocí výchozího nastavení pro skryté regiony, zatímco <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> metoda umožňuje přizpůsobit vzhled a chování obrysu. Jakmile skryté regiony disponují relace počet skrytých oblastí: [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] spravuje skrytých oblastí pro službu jazyka.  
  
 Pokud je potřeba určit, kdy počet skrytých oblastí: relace je zničen, změně skrytý oblasti nebo potřebujete zajistit, aby že konkrétní skryté oblasti je viditelný; musí být odvozen ze třídy <xref:Microsoft.VisualStudio.Package.Source> třídy a přepsat odpovídající metody <xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A>, <xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A>, a <xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A>v uvedeném pořadí.  
  
### <a name="example"></a>Příklad  
 Tady je zjednodušený příklad vytvoření skryté regiony pro všechny páry složených závorek. Předpokládá se, že jazyk poskytuje párování závorek a složené závorky lze porovnat zahrnovat aspoň složených závorek ({a}). Tento přístup je pouze pro ilustraci. Úplnou implementaci by měla úplné zpracování případů v <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>. Tento příklad také ukazuje, jak nastavit <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> přednost `true` dočasně. Další možností je zadat `AutoOutlining` s názvem parametru v `ProvideLanguageServiceAttribute` atribut v jazyce balíčku.  
  
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
 [Registrace služby starší verze jazyka](../../extensibility/internals/registering-a-legacy-language-service1.md)

