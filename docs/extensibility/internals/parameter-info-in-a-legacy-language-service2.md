---
title: Informace o parametrech ve službě staršího jazyka2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Parameter Info tool tip
- language services [managed package framework], IntelliSense Parameter Info
- Parameter Info (IntelliSense), supporting in language services [managed package framework]
ms.assetid: a117365d-320d-4bb5-b61d-3e6457b8f6bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e2c40c9ca5c038a70714545f4133db0c0dd686d5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706751"
---
# <a name="parameter-info-in-a-legacy-language-service"></a>Informace o parametrech ve službě starší verze jazyka
Informace o parametrech IntelliSense je popis, který zobrazuje podpis metody, když uživatel zadá počáteční znak seznamu parametrů (obvykle otevřenou závorku) pro seznam parametrů metody. Při zadání každého parametru a zadání oddělovače parametrů (obvykle čárky) se popisek aktualizuje tak, aby zobrazoval další parametr tučně.

 Třídy Framework spravovaného balíčku (MPF) poskytují podporu pro správu popisku Informace o parametrech. Analyzátor musí zjistit počáteční parametr, parametr next a koncové znaky parametru a musí zadat seznam podpisů metody a jejich přidružené parametry.

 Starší jazykové služby jsou implementovány jako součást VSPackage, ale novější způsob implementace funkcí služby jazyka je použití rozšíření MEF. Další informace naleznete v [tématu Rozšíření editoru a jazykových služeb](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Doporučujeme, abyste co nejdříve začali používat nové rozhraní API editoru. Tím se zlepší výkon služby jazyka a umožní vám využít nové funkce editoru.

## <a name="implementation"></a>Implementace
 Analyzátor by měl nastavit <xref:Microsoft.VisualStudio.Package.TokenTriggers> hodnotu aktivační události je nastavena, když najde počáteční znak seznamu parametrů (často otevřené závorky). Měl by <xref:Microsoft.VisualStudio.Package.TokenTriggers> nastavit aktivační událost, když najde oddělovač parametrů (často čárku). To způsobí, že popisek Informace o parametrech bude aktualizován a zobrazí se další parametr tučně. Analyzátor by měl nastavit <xref:Microsoft.VisualStudio.Package.TokenTriggers> hodnotu aktivační události, pokud najde koncový znak seznamu parametrů (často zavřít závorku).

 Hodnota <xref:Microsoft.VisualStudio.Package.TokenTriggers> aktivační události iniciuje volání <xref:Microsoft.VisualStudio.Package.Source.MethodTip%2A> metody, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> která zase volá analyzátor <xref:Microsoft.VisualStudio.Package.ParseReason>metody s důvodem analýzy . Pokud analyzátor zjistí, že identifikátor před počátečním znakem seznamu parametrů je rozpoznaný název <xref:Microsoft.VisualStudio.Package.AuthoringScope> metody, vrátí seznam odpovídajících podpisů metody v objektu. Pokud byly nalezeny nějaké podpisy metody, zobrazí se popis ekvalizér Informace o parametrech s prvním podpisem v seznamu. Tento popis je pak aktualizován jako další podpis je zadán. Při zadání znaku konce seznamu parametrů je ze zobrazení odebrán popis informace o parametrech.

> [!NOTE]
> Chcete-li zajistit, aby byl popis informací o parametru správně <xref:Microsoft.VisualStudio.Package.Methods> formátován, je nutné přepsat vlastnosti třídy a zadat příslušné znaky. Základní <xref:Microsoft.VisualStudio.Package.Methods> třída předpokládá podpis metody jazyka C#style. Podrobnosti <xref:Microsoft.VisualStudio.Package.Methods> o tom, jak toho lze provést, najdete ve třídě.

## <a name="enabling-support-for-the-parameter-info"></a>Povolení podpory pro informace o parametrech
 Chcete-li podporovat popisky informace `ShowCompletion` o parametrech, musíte nastavit pojmenovaný parametr parametru <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> na . `true` Jazyková služba přečte hodnotu této <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> položky registru z vlastnosti.

 Kromě toho <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ParameterInformation%2A> musí být vlastnost `true` nastavena na pro popis informací o parametrech, které mají být zobrazeny.

### <a name="example"></a>Příklad
 Zde je zjednodušený příklad zjištění znaků seznamu parametrů a nastavení příslušných aktivačních událostí. Tento příklad je pouze pro ilustrační účely. Předpokládá, že skener obsahuje `GetNextToken` metodu, která identifikuje a vrací tokeny z řádku textu. Ukázkový kód jednoduše nastaví aktivační události vždy, když vidí správný druh znaku.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestScanner : IScanner
    {
        private Lexer lex;
        private const char parameterListStartChar = '(';
        private const char parameterListEndChar   = ')';
        private const char parameterNextChar      = ',';

        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,
                                                   ref int state)
        {
            bool foundToken = false
            string token = lex.GetNextToken();
            if (token != null)
            {
                foundToken = true;
                char c = token[0];
                if (Char.IsPunctuation(c))
                {
                    tokenInfo.Type = TokenType.Operator;
                    tokenInfo.Color = TokenColor.Keyword;
                    tokenInfo.EndIndex = index;

                    if (c == parameterListStartChar)
                    {
                        tokenInfo.Trigger |= TokenTriggers.ParameterStart;
                    }
                    else if (c == parameterListNextChar)
                    {
                        tokenInfo.Trigger |= TokenTriggers.ParameterNext;
                    else if (c == parameterListEndChar)
                    {
                        tokenInfo.Trigger |= TokenTriggers.ParameterEnd;
                    }
                }
            return foundToken;
        }
    }
}
```

## <a name="supporting-the-parameter-info-tooltip-in-the-parser"></a>Podpora popisku informací o parametrech v analyzátoru
 Třída <xref:Microsoft.VisualStudio.Package.Source> provede některé předpoklady o <xref:Microsoft.VisualStudio.Package.AuthoringScope> obsahu <xref:Microsoft.VisualStudio.Package.AuthoringSink> a třídy při zobrazení a aktualizaci popisek Informace o parametrech.

- Analyzátor je zadán <xref:Microsoft.VisualStudio.Package.ParseReason> při zadání počátečního znaku seznamu parametrů.

- Umístění uvedené v <xref:Microsoft.VisualStudio.Package.ParseRequest> objektu je bezprostředně za počátečním znakem seznamu parametrů. Analyzátor musí shromažďovat podpisy všech deklarací metod, které jsou k dispozici na této <xref:Microsoft.VisualStudio.Package.AuthoringScope> pozici, a uložit je do seznamu ve vaší verzi objektu. Tento seznam obsahuje název metody, typ metody (nebo návratový typ) a seznam možných parametrů. Tento seznam je později vyhledán pro podpis metody nebo podpisy, které se mají zobrazit v popisku Informace o parametrech.

  Analyzátor pak musí analyzovat řádek určený <xref:Microsoft.VisualStudio.Package.ParseRequest> objektem shromáždit název zadané metody, jakož i jak daleko podél uživatele je v parametrech zadávání. Toho je dosaženo předáním názvu metody <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> na metodu <xref:Microsoft.VisualStudio.Package.AuthoringSink> na objekt <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> a potom volání metody při analýzu <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> znaku start seznamu parametrů, volání metody při <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> analyzování seznamu parametrů další znak a nakonec volání metody při analýzu znaku seznamu parametrů. Výsledky těchto volání metody jsou <xref:Microsoft.VisualStudio.Package.Source> používány třídy odpovídajícím způsobem aktualizovat popisek Informace o parametrech.

### <a name="example"></a>Příklad
 Zde je řádek textu, který může uživatel zadat. Čísla pod čárou označují, který krok je proveden analyzátorem na této pozici v řádku (za předpokladu, že analýza se přesune zleva doprava). Předpokladem je, že vše před řádek již byla analyzována pro podpisy metody, včetně "testfunc" podpis metody.

```
testfunc("a string",3);
     ^^          ^ ^
     12          3 4
```

 Kroky, které analyzátor provede, jsou uvedeny níže:

1. Analyzátor volá <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> s textem "testfunc".

2. Analyzátor volá <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A>.

3. Analyzátor volá <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A>.

4. Analyzátor volá <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A>.
