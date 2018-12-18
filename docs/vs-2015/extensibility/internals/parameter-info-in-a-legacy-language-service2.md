---
title: Informace o parametrech ve starší verze jazyka2 | Dokumentace Microsoftu
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
- IntelliSense, Parameter Info tool tip
- language services [managed package framework], IntelliSense Parameter Info
- Parameter Info (IntelliSense), supporting in language services [managed package framework]
ms.assetid: a117365d-320d-4bb5-b61d-3e6457b8f6bc
caps.latest.revision: 24
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a540a2e5b282e1242109edd67a5dfbc95067e183
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781319"
---
# <a name="parameter-info-in-a-legacy-language-service"></a>Informace o parametrech ve službě starší verze jazyka
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Informace o parametru technologie IntelliSense je popisek, který zobrazuje podpis metody, když uživatel zadá seznamu parametrů počáteční znak (obvykle otevřena závorka) pro seznam parametrů metody. Každý parametr je zadána a je zadán parametr oddělovač (obvykle čárku), popisek se aktualizuje a zobrazí další parametr tučným písmem.  
  
 Třídy spravované balíček framework (MPF) poskytují podporu pro správu popis tlačítka informace o parametru. Analyzátor musí odhalit, parametr start parametr v dalším kroku, a parametr koncové znaky a je nutné zadat seznam podpisy metod a jejich přidružené parametry.  
  
 Služby starší verze jazyka jsou implementovány jako součást sady VSPackage, ale novější způsob implementace funkce služba jazyka je pro použití rozšíření MEF. Další informace najdete v tématu [rozšíření pro Editor a jazykových služeb](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Doporučujeme vám, že začnete používat nový editor API co nejdříve. Tím vylepšíme výkonu vaší služby jazyka a umožňují využívat nové funkce editoru.  
  
## <a name="implementation"></a>Implementace  
 Analyzátor měli nastavit hodnotu aktivační událost <xref:Microsoft.VisualStudio.Package.TokenTriggers> nastavena při nalezení znak start seznamu parametrů (často otevřena závorka). Měli nastavit <xref:Microsoft.VisualStudio.Package.TokenTriggers> aktivovat po nalezení znaku oddělovače parametr (často čárkami). To způsobí, že informace o parametru popisku aktualizovat a zobrazit další parametr tučným písmem. Analyzátor měli nastavit hodnotu aktivační událost <xref:Microsoft.VisualStudio.Package.TokenTriggers> při Pokud najde parametr seznamu koncový znak (často pravá závorka).  
  
 <xref:Microsoft.VisualStudio.Package.TokenTriggers> Hodnota triggeru zahájí volání <xref:Microsoft.VisualStudio.Package.Source.MethodTip%2A> metodu, která volá <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metoda analyzátoru s analýzy důvod <xref:Microsoft.VisualStudio.Package.ParseReason>. Pokud analyzátor shledá, že je před seznam parametrů počáteční znak identifikátoru rozpoznaný název metody, vrátí seznam spárování metod podpisů v <xref:Microsoft.VisualStudio.Package.AuthoringScope> objektu. Pokud nebyly nalezeny žádné podpisy metod, zobrazí se popis tlačítka informace o parametru podpisem první v seznamu. Tento popis je pak aktualizovat, protože je zadán více podpisu. Zadávaný koncový znak seznamu parametr popisu tlačítka informace o parametru se odebere ze zobrazení.  
  
> [!NOTE]
>  Chcete-li zajistit, aby popis tlačítka informace o parametru je ve správném formátu, je nutné přepsat vlastnosti na <xref:Microsoft.VisualStudio.Package.Methods> třída slouží k poskytování příslušných znaků. Základní <xref:Microsoft.VisualStudio.Package.Methods> předpokládá třídy C# – styl podpis metody. Zobrazit <xref:Microsoft.VisualStudio.Package.Methods> třídy podrobnosti o tom, jak to lze provést.  
  
## <a name="enabling-support-for-the-parameter-info"></a>Povolení podpory pro informace o parametru  
 Pro podporu parametru informacích, je nutné nastavit `ShowCompletion` s názvem parametru <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> k `true`. Služba jazyka přečte hodnotu této položky registru z <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> vlastnost.  
  
 Kromě toho <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ParameterInformation%2A> musí být vlastnost nastavena na `true` pro informace o parametru Popis zobrazený.  
  
### <a name="example"></a>Příklad  
 Tady je zjednodušený příklad detekovat znaky seznamu parametrů a nastavení odpovídající aktivační události. V tomto příkladu je pouze pro ilustraci. Předpokládá, že skener obsahuje metodu `GetNextToken` , který identifikuje a vrátí tokeny z řádku textu. Pokaždé, když se zobrazí správný typ znaku, ukázkový kód jednoduše nastaví aktivačních událostí.  
  
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
  
## <a name="supporting-the-parameter-info-tooltip-in-the-parser"></a>Podpora popis tlačítka informace o parametru v analyzátor  
 <xref:Microsoft.VisualStudio.Package.Source> Třídy do určité míry vyhodnotit o obsah <xref:Microsoft.VisualStudio.Package.AuthoringScope> a <xref:Microsoft.VisualStudio.Package.AuthoringSink> třídy při popisu tlačítka informace o parametru se zobrazí a aktualizuje.  
  
- Daný analyzátor <xref:Microsoft.VisualStudio.Package.ParseReason> po zadání znaku start seznamu parametrů.  
  
- Umístění podle <xref:Microsoft.VisualStudio.Package.ParseRequest> je objekt okamžitě po seznamu parametrů počáteční znak. Analyzátor musí shromáždit podpisy k dispozici na všech deklarace metody, které umístění a uložit je do seznamu ve vaší verzi <xref:Microsoft.VisualStudio.Package.AuthoringScope> objektu. Tento seznam obsahuje název metody, metoda typu (nebo návratového typu) a seznam parametrů, je to možné. Tento seznam se později hledá podpis metody nebo signatury zobrazíte v popisu tlačítka informace o parametru.  
  
  Analyzátor musí pak analyzovat řádek určené <xref:Microsoft.VisualStudio.Package.ParseRequest> objekt k získání názvu metody zadávání a také jak daleko podél uživatel je v zadávání parametrů. Toho dosahuje tím, že předáte název metody, která <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> metodu na <xref:Microsoft.VisualStudio.Package.AuthoringSink> objektu a následným voláním <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> analyzovat metodu po seznamu parametrů počáteční znak volání <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> metoda při seznam parametrů Následující znak je analyzována a nakonec volání <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> metoda při analyzovat parametr seznamu koncový znak. Výsledky volání těchto metod jsou používány <xref:Microsoft.VisualStudio.Package.Source> třídy správně aktualizovat popis tlačítka informace o parametru.  
  
### <a name="example"></a>Příklad  
 Tady je řádek textu, který může uživatel zadat. Čísla pod řádkem označují, který krok je obsazen analyzátor na této pozici řádku (za předpokladu, že analýzy přesune zleva doprava). Tady předpokladem je, že všechno, co před řádkem má být již pro podpisy metod, včetně podpis metody "testfunc".  
  
```  
testfunc("a string",3);  
     ^^          ^ ^  
     12          3 4  
```  
  
 Níže jsou uvedené kroky, které analyzátor přebírá:  
  
1.  Volání analyzátor <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> s textem "testfunc".  
  
2.  Volání analyzátor <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A>.  
  
3.  Volání analyzátor <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A>.  
  
4.  Volání analyzátor <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A>.

