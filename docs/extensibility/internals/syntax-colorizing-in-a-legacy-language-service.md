---
title: Syntaktické vybarvení ve službě staršího jazyka | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], syntax highlighting
- colorization, supporting in language services [managed package framework]
- syntax highlighting, supporting in language services [managed package framework]
- language services [managed package framework], colorization
ms.assetid: 1ca1736a-f554-42e4-a9c7-fe8c3c1717df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 02723a09254255b98291cb921ae5ec091d8b9859
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704698"
---
# <a name="syntax-colorizing-in-a-legacy-language-service"></a>Barevné zvýrazňování syntaxe ve službě starší verze jazyka
Syntaktické zbarvení je funkce, která způsobuje, že se ve zdrojovém souboru v různých barvách a stylech zobrazují různé prvky programovacího jazyka. Pro podporu této funkce je třeba zadat analyzátor nebo skener, který může identifikovat typy lexikálních prvků nebo tokenů v souboru. Mnoho jazyků rozlišuje klíčová slova, oddělovače (například závorky nebo závorky) a komentáře jejich vybarvením různými způsoby.

 Starší jazykové služby jsou implementovány jako součást VSPackage, ale novější způsob implementace funkcí služby jazyka je použití rozšíření MEF. Další informace naleznete v [tématu Rozšíření editoru a jazykových služeb](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Doporučujeme, abyste co nejdříve začali používat nové rozhraní API editoru. Tím se zlepší výkon služby jazyka a umožní vám využít nové funkce editoru.

## <a name="implementation"></a>Implementace
 Pro podporu vybarvení, spravované ho balíček <xref:Microsoft.VisualStudio.Package.Colorizer> framework (MPF) zahrnuje třídu, která implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> rozhraní. Tato třída spolupracuje <xref:Microsoft.VisualStudio.Package.IScanner> s k určení tokenu a barvy. Další informace o skenerech naleznete v [tématu Analyzátor starších jazykových služeb a skener](../../extensibility/internals/legacy-language-service-parser-and-scanner.md). Třída <xref:Microsoft.VisualStudio.Package.Colorizer> pak označí každý znak tokenu s informacemi o barvě a vrátí tyto informace do editoru zobrazující zdrojový soubor.

 Informace o barvě vrácené do editoru je index do seznamu barevných položek. Každá barevná položka určuje hodnotu barvy a sadu atributů písma, například tučné nebo přeškrtnuté. Editor poskytuje sadu výchozích barevných položek, které může služba jazyka používat. Vše, co musíte udělat, je zadat příslušný index barev pro každý typ tokenu. Můžete však zadat sadu vlastních barevných položek a indexů, které zadáte pro tokeny, a odkazovat na vlastní seznam barevných položek namísto výchozího seznamu. Musíte také nastavit `RequestStockColors` položku registru na hodnotu `RequestStockColors` 0 (nebo položku vůbec nezadávejte) pro podporu vlastních barev. Tuto položku registru s pojmenovaným <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> parametrem můžete nastavit na uživatelem definovaný atribut. Další informace o registraci jazykové služby a nastavení jejích možností naleznete v [tématu Registrace služby staršího jazyka](../../extensibility/internals/registering-a-legacy-language-service1.md).

## <a name="custom-colorable-items"></a>Vlastní položky, které lze zabarvit
 Chcete-li zadat vlastní barevné položky, <xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A> musíte <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A> přepsat <xref:Microsoft.VisualStudio.Package.LanguageService> metodu a ve třídě. První metoda vrátí počet vlastních barevných položek, které podporuje vaše jazyková služba a druhá získá vlastní barevnou položku podle indexu. Vytvoříte výchozí seznam vlastních barevných položek. V konstruktoru služby jazyka, vše, co musíte udělat, je zadat každou barevnou položku s názvem. Visual Studio automaticky zpracovává případ, kde uživatel vybere jinou sadu barevných položek. Tento název se zobrazí na stránce **vlastnosti Písma a barvy** v dialogovém okně **Možnosti** (k dispozici v nabídce **Nástroje** sady Visual Studio) a tento název určuje, jakou barvu uživatel přepsal. Volby uživatele jsou uloženy v mezipaměti v registru a přístupné podle názvu barvy. Na stránce **Vlastnosti Písma a barvy** jsou uvedeny všechny názvy barev v abecedním pořadí, takže vlastní barvy můžete seskupit podle předchozího názvu barvy s názvem jazyka; například "**TestLanguage-Comment**" a "**TestLanguage- Klíčové slovo**". Nebo můžete seskupit své barevné položky podle typu , "**Komentář (TestLanguage)**" a "**Klíčové slovo (TestLanguage)**". Je upřednostňováno seskupení podle názvu jazyka.

> [!CAUTION]
> Důrazně doporučujeme zahrnout název jazyka do názvu barevné položky, aby se zabránilo kolizím s existujícími colorable názvy položek.

> [!NOTE]
> Pokud změníte název jedné z barev během vývoje, je nutné obnovit mezipaměť, kterou visual studio vytvořilpři prvním přístupu k vašim barvám. Můžete tak učinit spuštěním příkazu **Obnovit experimentální podregistr** z nabídky programu Sady Visual Studio SDK.

 Všimněte si, že první položka v seznamu barevných položek se nikdy odkazuje. Visual Studio vždy poskytuje výchozí barvy textu a atributy pro tuto položku. Nejjednodušší způsob, jak se s tím vypořádat, je zadat zástupnou barevnou položku jako první položku.

### <a name="high-color-colorable-items"></a>Vysoké barevné barevné barevné položky
 Barevné položky mohou také podporovat 24bitové <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> nebo vysoké barevné hodnoty prostřednictvím rozhraní. Třída MPF <xref:Microsoft.VisualStudio.Package.ColorableItem> podporuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> rozhraní a 24bitové barvy jsou určeny v konstruktoru spolu s normálními barvami. Další <xref:Microsoft.VisualStudio.Package.ColorableItem> podrobnosti najdete ve třídě. Následující příklad ukazuje, jak nastavit 24bitové barvy pro klíčová slova a komentáře. 24bitové barvy se používají, když je na ploše uživatele podporována 24bitová barva; v opačném případě se použijí normální barvy textu.

 Nezapomeňte, že se jedná o výchozí barvy pro váš jazyk; uživatel může změnit tyto barvy na cokoliv chtějí.

### <a name="example"></a>Příklad
 Tento příklad ukazuje jeden způsob, jak deklarovat <xref:Microsoft.VisualStudio.Package.ColorableItem> a naplnit pole vlastní chodelných položek pomocí třídy. Tento příklad nastaví barvy klíčových slov a komentářů pomocí 24bitových barev.

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

## <a name="the-colorizer-class-and-the-scanner"></a>Třída Colorizer a skener
 Základní <xref:Microsoft.VisualStudio.Package.LanguageService> třída má <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A> metodu, která <xref:Microsoft.VisualStudio.Package.Colorizer> instance třídy. Skener, který je <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> vrácen z metody <xref:Microsoft.VisualStudio.Package.Colorizer> je předán konstruktoru třídy.

 Je nutné <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> implementovat metodu ve <xref:Microsoft.VisualStudio.Package.LanguageService> vlastní verzi třídy. Třída <xref:Microsoft.VisualStudio.Package.Colorizer> používá skener získat všechny informace o barvě tokenu.

 Skener potřebuje naplnit <xref:Microsoft.VisualStudio.Package.TokenInfo> strukturu pro každý token, který najde. Tato struktura obsahuje informace, jako je například rozsah, který token zabírá, index barev, který <xref:Microsoft.VisualStudio.Package.TokenTriggers>chcete použít, jaký typ je token a aktivační události tokenu (viz). Pro vybarvení třídou <xref:Microsoft.VisualStudio.Package.Colorizer> jsou potřeba pouze index y rozpětí a barvy.

 Index barev uložený <xref:Microsoft.VisualStudio.Package.TokenInfo> ve struktuře je <xref:Microsoft.VisualStudio.Package.TokenColor> obvykle hodnota z výčtu, která poskytuje počet pojmenovaných indexů odpovídajících různým jazykovým prvkům, jako jsou klíčová slova a operátory. Pokud váš vlastní barevný seznam položek odpovídá <xref:Microsoft.VisualStudio.Package.TokenColor> položkám prezentovaným ve výčtu, můžete výčet použít jako barvu pro každý token. Pokud však máte další barevné položky nebo nechcete použít existující hodnoty v tomto pořadí, můžete uspořádat vlastní seznam barevných položek tak, aby vyhovoval vašim potřebám, a vrátit příslušný index do tohoto seznamu. Jen se ujistěte, že <xref:Microsoft.VisualStudio.Package.TokenColor> obsazení indexu při <xref:Microsoft.VisualStudio.Package.TokenInfo> ukládání do struktury; [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] vidí pouze index.

### <a name="example"></a>Příklad
 Následující příklad ukazuje, jak skener může identifikovat tři typy tokenů: čísla, interpunkce a identifikátory (vše, co není číslo nebo interpunkce). Tento příklad je pouze pro ilustrační účely a nepředstavuje komplexní analyzátor a implementaci skeneru. Předpokládá, že je `Lexer` třída s `GetNextToken()` metodou, která vrací řetězec.

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

## <a name="see-also"></a>Viz také
- [Funkce služby starší verze jazyka](../../extensibility/internals/legacy-language-service-features1.md)
- [Analyzátor a skener služby starší verze jazyka](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
- [Registrace služby starší verze jazyka](../../extensibility/internals/registering-a-legacy-language-service1.md)
