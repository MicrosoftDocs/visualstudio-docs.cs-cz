---
title: Colorizing syntaxe ve službě starší verze jazyka | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], syntax highlighting
- colorization, supporting in language services [managed package framework]
- syntax highlighting, supporting in language services [managed package framework]
- language services [managed package framework], colorization
ms.assetid: 1ca1736a-f554-42e4-a9c7-fe8c3c1717df
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 19561363affada05154e15142bd32a30a5d051d0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722835"
---
# <a name="syntax-colorizing-in-a-legacy-language-service"></a>Barevné zvýrazňování syntaxe ve službě starší verze jazyka
Barevné zvýrazňování syntaxe je funkce, která způsobí zobrazení různých prvků programovacího jazyka ve zdrojovém souboru v různých barvách a stylech. Pro podporu této funkce je nutné zadat analyzátor nebo skener, který může identifikovat typy lexikálních prvků nebo tokenů v souboru. Mnoho jazyků rozlišuje klíčová slova, oddělovače (například kulaté závorky nebo složené závorky) a komentáře jejich Colorizing různými způsoby.

 Starší jazykové služby jsou implementovány jako součást sady VSPackage, ale novější způsob, jak implementovat funkce jazykové služby, je použít rozšíření MEF. Další informace najdete v tématu [rozšíření editoru a jazykových služeb](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Doporučujeme začít používat nové rozhraní API editoru co nejrychleji. Tím se vylepšit výkon vaší jazykové služby a umožní vám využít nové funkce editoru.

## <a name="implementation"></a>Implementace
 Pro podporu barevného zabarvení, rozhraní Managed Package Framework (MPF) obsahuje třídu <xref:Microsoft.VisualStudio.Package.Colorizer>, která implementuje rozhraní <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>. Tato třída komunikuje s <xref:Microsoft.VisualStudio.Package.IScanner> pro určení tokenu a barev. Další informace o skenerech najdete v tématu [analyzátor a skener služby starší verze jazyka](../../extensibility/internals/legacy-language-service-parser-and-scanner.md). Třída <xref:Microsoft.VisualStudio.Package.Colorizer> pak označí každý znak tokenu informacemi o barvách a vrátí tyto informace do editoru, který zobrazuje zdrojový soubor.

 Informace o barvách vracené do editoru jsou indexem seznamu položek barev. Každá barevná položka určuje hodnotu barvy a sadu atributů písma, jako je tučné písmo nebo přeškrtnutí. Editor poskytuje sadu výchozích barev, které mohou používat vaše služba jazyka. Stačí zadat odpovídající index barvy pro každý typ tokenu. Můžete však poskytnout sadu vlastních barev a indexů, které zadáte pro tokeny, a odkazovat na vlastní seznam položek, které jsou k dispozici, a nikoli na výchozí seznam. Musíte také nastavit položku registru `RequestStockColors` na hodnotu 0 (nebo vůbec nespecifikovat položku `RequestStockColors`), aby podporovala vlastní barvy. Tuto položku registru můžete nastavit s pojmenovaným parametrem na <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> uživatelsky definovaný atribut. Další informace o registraci jazykové služby a nastavení jejích možností najdete v tématu [Registrace služby starší verze jazyka](../../extensibility/internals/registering-a-legacy-language-service1.md).

## <a name="custom-colorable-items"></a>Vlastní položky, které lze zabarvit
 Chcete-li dodat vlastní barevné položky, je nutné přepsat <xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A> a metodu <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A> na třídě <xref:Microsoft.VisualStudio.Package.LanguageService>. První metoda vrátí počet vlastních barevně vybarvenéch položek, které podporuje vaše jazyková služba, a druhá získá vlastní barevnou položku podle indexu. Vytvoříte výchozí seznam vlastních barevně vydaných položek. V konstruktoru vaší jazykové služby je vše, co potřebujete, poskytovat každou barevnou položku s názvem. Sada Visual Studio automaticky zpracuje případ, kde uživatel vybere jinou sadu barev, která je k disdílnému výběru položek. Tento název se zobrazí na stránce vlastností **písma a barvy** v dialogovém okně **Možnosti** (k dispozici v nabídce **nástroje** sady Visual Studio) a tento název určuje, která barva se uživateli přepsala. Volby uživatele jsou uloženy v mezipaměti v registru a jsou k němu přistupované pomocí názvu barvy. Stránka vlastností **písma a barvy** obsahuje seznam všech názvů barev v abecedním pořadí, takže můžete seskupit vlastní barvy předchozími názvy barev s názvem jazyka; například "**TestLanguage-Comment**" a "**TestLanguage-klíčové slovo**". Můžete také seskupit položky barev podle typu, "**Comment (TestLanguage)** " a "**klíčové slovo (TestLanguage)** ". Seskupení podle názvu jazyka je preferované.

> [!CAUTION]
> Důrazně doporučujeme, abyste do názvu barevné položky zahrnuli název jazyka, abyste se vyhnuli kolizím s existujícími názvy položek barev.

> [!NOTE]
> Pokud změníte název jedné z barev během vývoje, je nutné resetovat mezipaměť, kterou aplikace Visual Studio vytvořila při prvním použití barvy. Můžete to udělat tak, že spustíte příkaz **resetovat experimentální podregistr** z nabídky programu Visual Studio SDK.

 Všimněte si, že na první položku v seznamu položek, na které máte barvy, se nikdy neodkazuje. Visual Studio vždy poskytuje výchozí barvy textu a atributy pro tuto položku. Nejjednodušší způsob, jak to řešit, je dodat jako první položku zástupnou položku barvy.

### <a name="high-color-colorable-items"></a>Vysoce barevné barevné položky
 Barevné položky mohou také podporovat 24bitové nebo vysoké hodnoty barev prostřednictvím rozhraní <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>. Třída MPF <xref:Microsoft.VisualStudio.Package.ColorableItem> podporuje rozhraní <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> a 24bitové barvy jsou zadány v konstruktoru společně s normálními barvami. Další podrobnosti najdete ve třídě <xref:Microsoft.VisualStudio.Package.ColorableItem>. Následující příklad ukazuje, jak nastavit 24bitové barvy pro klíčová slova a komentáře. 24bitové barvy se používají, když je na ploše uživatele podporovaná 24bitové barva. v opačném případě se použijí normální barvy textu.

 Pamatujte na to, že jsou to výchozí barvy pro váš jazyk. uživatel může tyto barvy změnit bez ohledu na to, co chtějí.

### <a name="example"></a>Příklad
 Tento příklad ukazuje jeden ze způsobů, jak deklarovat a naplnit pole vlastních barevně vydaných položek pomocí třídy <xref:Microsoft.VisualStudio.Package.ColorableItem>. Tento příklad nastavuje klíčová slova a barvy komentářů pomocí 24bitové barvy.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        private ColorableItem[] m_colorableItems;

        TestLanguageService() : base()
        {
            m_colorableItems = new ColorableItem[] {
                new ColorableItem("TestLanguage - Text",
                                  "Text",
                                  COLORINDEX.CI_SYSPLAINTEXT_FG,
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,
                                  System.Drawing.Color.Empty,
                                  System.Drawing.Color.Empty,
                                  FONTFLAGS.FF_DEFAULT),
                new ColorableItem("TestLanguage - Keyword",
                                  "Keyword",
                                  COLORINDEX.CI_MAROON,
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,
                                  System.Drawing.Color.FromArgb(192,32,32),
                                  System.Drawing.Color.Empty,
                                  FONTFLAGS.FF_BOLD),
                new ColorableItem("TestLanguage - Comment",
                                  "Comment",
                                  COLORINDEX.CI_DARKGREEN,
                                  COLORINDEX.CI_LIGHTGRAY,
                                  System.Drawing.Color.FromArgb(32,128,32),
                                  System.Drawing.Color.Empty,
                                  FONTFLAGS.FF_DEFAULT)
                // ...
                // Add as many colorable items as you want to support.
            };
        }
    }
}
```

## <a name="the-colorizer-class-and-the-scanner"></a>Třída colorizer a skener
 Třída Base <xref:Microsoft.VisualStudio.Package.LanguageService> má <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A> metodu, která instantiantes třídu <xref:Microsoft.VisualStudio.Package.Colorizer>. Skener, který je vrácen z <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> metoda, je předán konstruktoru třídy <xref:Microsoft.VisualStudio.Package.Colorizer>.

 Je nutné implementovat metodu <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> ve vaší vlastní verzi třídy <xref:Microsoft.VisualStudio.Package.LanguageService>. Třída <xref:Microsoft.VisualStudio.Package.Colorizer> používá skener k získání všech barevných informací o tokenech.

 Skener musí naplnit strukturu <xref:Microsoft.VisualStudio.Package.TokenInfo> pro každý nalezený token. Tato struktura obsahuje informace, jako je například rozsah, který token zabírá, použitý index barvy, typ tokenu a triggery tokenů (viz <xref:Microsoft.VisualStudio.Package.TokenTriggers>). Pro barevné vyřazení třídou <xref:Microsoft.VisualStudio.Package.Colorizer> je potřeba pouze index rozsahu a barvy.

 Barevný index uložený ve struktuře <xref:Microsoft.VisualStudio.Package.TokenInfo> je obvykle hodnota z výčtu <xref:Microsoft.VisualStudio.Package.TokenColor>, která poskytuje řadu pojmenovaných indexů odpovídajících různým prvkům jazyka, jako jsou klíčová slova a operátory. Pokud vlastní seznam položek barev odpovídá položkám uvedeným ve výčtu <xref:Microsoft.VisualStudio.Package.TokenColor>, můžete pouze použít výčet jako barvu pro každý token. Pokud ale máte další barevné položky nebo pokud nechcete použít existující hodnoty v tomto pořadí, můžete si přizpůsobit vlastní seznam položek, které odpovídají vašim potřebám, a vrátit příslušný index do tohoto seznamu. Stačí, abyste při ukládání do struktury <xref:Microsoft.VisualStudio.Package.TokenInfo> přetypování index na <xref:Microsoft.VisualStudio.Package.TokenColor>.  [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] uvidí jenom index.

### <a name="example"></a>Příklad
 Následující příklad ukazuje, jak může skener identifikovat tři typy tokenů: čísla, interpunkční znaménka a identifikátory (cokoli, co není číslo nebo interpunkční znaménko). Tento příklad je určen pouze pro ilustrativní účely a nepředstavuje komplexní analyzátor a implementaci skeneru. Předpokládá, že existuje třída `Lexer` s metodou `GetNextToken()`, která vrací řetězec.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    private Lexer lex;

    public class TestScanner : IScanner
    {
        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,
                                                   ref int state)
        {
            bool foundToken = false;
            string token = lex.GetNextToken();
            if (token != null)
            {
                char firstChar = token[0];
                if (Char.IsPunctuation(firstChar))
                {
                    tokenInfo.Type = TokenType.Operator;
                    tokenInfo.Color = TokenColor.Keyword;
                }
                else if (Char.IsNumber(firstChar))
                {
                    tokenInfo.Type = TokenType.Literal;
                    tokenInfo.Color = TokenColor.Number;
                }
                else
                {
                    tokenInfo.Type = TokenType.Identifier;
                    tokenInfo.Color = TokenColor.Identifier;
                }
            }
            return foundToken;
        }
```

## <a name="see-also"></a>Viz také:
- [Funkce služby starší verze jazyka](../../extensibility/internals/legacy-language-service-features1.md)
- [Analyzátor a skener služby starší verze jazyka](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
- [Registrace služby starší verze jazyka](../../extensibility/internals/registering-a-legacy-language-service1.md)