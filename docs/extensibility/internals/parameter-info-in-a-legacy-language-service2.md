---
title: Informace o parametrech ve starším jazyce Jazyka2 | Microsoft Docs
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
ms.openlocfilehash: dff6e871320d0727ed2fbec4188e8f7af2e5c5fe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "88237955"
---
# <a name="parameter-info-in-a-legacy-language-service-2"></a>Informace o parametrech ve službě starší verze jazyka 2
Informace o parametrech IntelliSense je popis, který zobrazí signaturu metody, když uživatel zadá spouštěcí znak seznamu parametrů (obvykle levou závorku) pro seznam parametrů metody. Při zadání každého parametru a zadání oddělovače parametrů (obvykle čárka) se popis aktualizuje a zobrazí se další parametr tučným písmem.

 Třídy spravovaného balíčku architektury (MPF) poskytují podporu pro správu popisů parametrů pro informace o parametrech. Analyzátor musí detekovat počáteční znaky parametrů, parametry Next a end a musí poskytovat seznam signatur metod a jejich přidružených parametrů.

 Starší jazykové služby jsou implementovány jako součást sady VSPackage, ale novější způsob, jak implementovat funkce jazykové služby, je použít rozšíření MEF. Další informace najdete v tématu [rozšíření editoru a jazykových služeb](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Doporučujeme začít používat nové rozhraní API editoru co nejrychleji. Tím se vylepšit výkon vaší jazykové služby a umožní vám využít nové funkce editoru.

## <a name="implementation"></a>Implementace
 Analyzátor by měl nastavit hodnotu triggeru, <xref:Microsoft.VisualStudio.Package.TokenTriggers> když najde spouštěcí znak seznamu parametrů (často levou závorku). Měla by být nastavena <xref:Microsoft.VisualStudio.Package.TokenTriggers> Trigger, když najde oddělovač parametrů (často čárka). To způsobí, že se popisek informace parametru aktualizuje a zobrazí se další parametr tučným písmem. Analyzátor by měl nastavit hodnotu triggeru, <xref:Microsoft.VisualStudio.Package.TokenTriggers> když nalezne koncový znak seznamu parametrů (často pravá závorka).

 <xref:Microsoft.VisualStudio.Package.TokenTriggers>Hodnota triggeru zahájí volání <xref:Microsoft.VisualStudio.Package.Source.MethodTip%2A> metody, která zase volá <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> analyzátor metody s důvodem analýzy <xref:Microsoft.VisualStudio.Package.ParseReason> . Pokud analyzátor určí, že identifikátor před počátečním znakem seznamu parametrů je rozpoznaným názvem metody, vrátí seznam odpovídající signatury metody v <xref:Microsoft.VisualStudio.Package.AuthoringScope> objektu. Pokud byly nalezeny jakékoli signatury metod, v seznamu se zobrazí popisek informace o parametru s prvním podpisem. Tento popis se pak aktualizuje, protože se zapíše další podpis. Při zadání koncového znaku seznamu parametrů je popisek informace o parametru odebrán ze zobrazení.

> [!NOTE]
> Chcete-li zajistit, aby byl popisek informací o parametrech správně naformátován, je nutné přepsat vlastnosti <xref:Microsoft.VisualStudio.Package.Methods> třídy, aby poskytovaly příslušné znaky. Základní <xref:Microsoft.VisualStudio.Package.Methods> Třída předpokládá podpis metody ve stylu jazyka C#. Podrobnosti o <xref:Microsoft.VisualStudio.Package.Methods> tom, jak to lze provést, naleznete v třídě.

## <a name="enabling-support-for-the-parameter-info"></a>Povolení podpory pro informace o parametru
 Chcete-li podporovat informace o parametrech, je nutné nastavit `ShowCompletion` pojmenovaný parametr <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> pro `true` . Služba jazyka načte hodnotu této položky registru z <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> Vlastnosti.

 Kromě toho <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ParameterInformation%2A> musí být vlastnost nastavena na hodnotu `true` pro zobrazení popisku informace o parametru.

### <a name="example"></a>Příklad
 Tady je zjednodušený příklad rozpoznávání znaků seznamu parametrů a nastavení příslušných triggerů. Tento příklad je určen pouze pro ilustrativní účely. Předpokládá, že váš skener obsahuje metodu `GetNextToken` , která identifikuje a vrací tokeny z řádku textu. Vzorový kód jednoduše nastaví triggery vždy, když uvidí správný druh znaku.

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

## <a name="supporting-the-parameter-info-tooltip-in-the-parser"></a>Podpora popisu parametru informace v analyzátoru
 <xref:Microsoft.VisualStudio.Package.Source>Třída provede některé předpoklady týkající se obsahu <xref:Microsoft.VisualStudio.Package.AuthoringScope> <xref:Microsoft.VisualStudio.Package.AuthoringSink> tříd a při zobrazení a aktualizaci popisu parametru informace.

- Analyzátor je uveden <xref:Microsoft.VisualStudio.Package.ParseReason> při zadání počátečního znaku seznamu parametrů.

- Umístění zadané v <xref:Microsoft.VisualStudio.Package.ParseRequest> objektu je ihned po počátečním znaku seznamu parametrů. Analyzátor musí shromažďovat podpisy všech deklarací metod dostupných na této pozici a ukládat je do seznamu ve vaší verzi <xref:Microsoft.VisualStudio.Package.AuthoringScope> objektu. Tento seznam obsahuje název metody, typ metody (nebo návratový typ) a seznam možných parametrů. V tomto seznamu se později vyhledal podpis metody nebo signatury, které se mají zobrazit v popisu parametru informace.

  Analyzátor musí potom analyzovat řádek určený <xref:Microsoft.VisualStudio.Package.ParseRequest> objektem, aby shromáždil název metody, která se zadává, a také to, jak daleko podél uživatele je zadání parametrů. To se provádí předáním názvu metody do <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> metody <xref:Microsoft.VisualStudio.Package.AuthoringSink> objektu a následným voláním <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> metody, když je analyzovaný spouštěcí znak seznamu parametrů, voláním <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> metody při analýze dalšího znaku seznamu parametrů a nakonec voláním <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> metody při analýze koncového znaku seznamu parametrů. Výsledky těchto volání metody jsou používány <xref:Microsoft.VisualStudio.Package.Source> třídou pro správné aktualizace popisku parametru informace.

### <a name="example"></a>Příklad
 Tady je řádek textu, který uživatel může zadat. Čísla pod řádkem označují, který krok se provádí analyzátorem na této pozici na řádku (za předpokladu, že se analýza přesune doleva). Předpokladem je, že vše před řádkem již bylo analyzováno pro signatury metod, včetně signatury metody "testfunc".

```
testfunc("a string",3);
     ^^          ^ ^
     12          3 4
```

 Postup analýzy je popsaný níže:

1. Analyzátor volá <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> text "testfunc".

2. Analyzátor volá <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> .

3. Analyzátor volá <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> .

4. Analyzátor volá <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> .
