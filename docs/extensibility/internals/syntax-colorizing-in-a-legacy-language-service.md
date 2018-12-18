---
title: Syntaxe barevné ve službě jazyk starší | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], syntax highlighting
- colorization, supporting in language services [managed package framework]
- syntax highlighting, supporting in language services [managed package framework]
- language services [managed package framework], colorization
ms.assetid: 1ca1736a-f554-42e4-a9c7-fe8c3c1717df
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1d82a85958fd979a3d9d44375656b08356ef09d9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135945"
---
# <a name="syntax-colorizing-in-a-legacy-language-service"></a>Syntaxe barevné ve službě jazyk starší verze
Zabarvení syntaxe je funkce, která způsobí, že různé prvky programovací jazyk, který se má zobrazit ve zdrojovém souboru v jiné barvy a styly. Chcete-li tuto funkci podporovat, budete muset zadat analyzátor nebo skener, který můžete identifikovat typy lexikální elementy nebo tokenů v souboru. Mnoho jazyků existenci klíčová slova, oddělovače (například závorkách nebo složené závorky) a komentáře barevné je různými způsoby.  
  
 Starší verze jazyka služby jsou implementovány jako součást VSPackage, ale novější způsob implementace funkce služby jazyk je použití MEF rozšíření. Další informace naleznete v tématu [rozšíření pro Editor a služby, jazyk](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Doporučujeme vám, že začnete používat co nejdříve editoru nové rozhraní API. Tím zvýšit výkon služby jazyk a umožňují využívat výhod nových funkcí editoru.  
  
## <a name="implementation"></a>Implementace  
 Pro podporu zabarvení, zahrnuje rozhraní spravované balíčku (MPF) <xref:Microsoft.VisualStudio.Package.Colorizer> třídy, které implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> rozhraní. Tato třída komunikuje <xref:Microsoft.VisualStudio.Package.IScanner> k určení tokenu a barvy. Další informace o skenery najdete v tématu [analyzátoru služby starší verze jazyka a skener](../../extensibility/internals/legacy-language-service-parser-and-scanner.md). <xref:Microsoft.VisualStudio.Package.Colorizer> Třída pak označí každý znak tokenu s informacemi, barvu a vrátí tyto informace do editoru zobrazení zdrojového souboru.  
  
 Vrácené do editoru informace barva je index do colorable položek seznamu. Každá položka colorable určuje hodnoty barvy a sadu atributů písma, například tučné písmo nebo přeškrtnutí. Editor poskytuje sadu výchozí colorable položky, které můžete použít jazyk služby. Všechny, které musíte udělat je, určete index odpovídající barvu pro každý typ tokenu. Můžete však poskytují sadu vlastní colorable položky a indexy, které zadáte pro tokeny a odkazovat na vlastní seznam colorable položek místo na výchozím seznamu. Je nutné také nastavit `RequestStockColors` položky registru na hodnotu 0 (nebo nezadávejte `RequestStockColors` položku na všechny) pro podporu vlastních barev. Můžete nastavit tuto položku registru s s názvem parametr, který se <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> vlastní atribut. Další informace o registraci jazykové služby a nastavení jeho možností najdete v tématu [registrace služby jazyk starší](../../extensibility/internals/registering-a-legacy-language-service1.md).  
  
## <a name="custom-colorable-items"></a>Vlastní Colorable položky  
 K poskytování vlastních položek colorable, je nutné přepsat <xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A> a <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A> metodu <xref:Microsoft.VisualStudio.Package.LanguageService> třídy. První metoda vrátí počet vlastní colorable položek, které podporuje služba jazyka a druhý získá vlastní colorable položky podle indexu. Můžete vytvořit výchozí seznam vlastní colorable položky. V konstruktoru služby jazyk všechny, které je potřeba je zadat každou colorable položku s názvem. Visual Studio automaticky zpracuje tento případ, které si uživatel vybere jinou sadu colorable položky. Tento název se zobrazí v **písma a barev** stránka vlastností na **možnosti** dialogové okno (k dispozici ze sady Visual Studio **nástroje** nabídky) a tento název určuje, které Barva uživatel má přepsat. Volby uživatele jsou uloženy v mezipaměti v registru a přístup podle názvu barvy. **Písma a barev** stránka vlastností jsou uvedeny všechny názvy barev v abecedním pořadí, můžete seskupit vlastních barev tak, že před název každé barvy nahraďte názvem jazyk; například "**TestLanguage - komentář**"a"**TestLanguage – klíčové slovo**". Nebo můžete seskupit colorable položek podle typu "**komentář (TestLanguage)**"a"**– klíčové slovo (TestLanguage)**". Seskupení podle názvu jazyk je upřednostňovaný.  
  
> [!CAUTION]
>  Důrazně doporučujeme zahrnout název jazyka do název colorable položky předejdete kolizí se stávajícími názvy colorable položky.  
  
> [!NOTE]
>  Pokud změníte název jednoho z vaší barvy během vývoje, je nutné obnovit mezipaměti vytvořený při prvním vaší barvy měla přístup k sadě Visual Studio. To lze provést tak, že spustíte **resetovat experimentální Hive** příkazu v nabídce programu Visual Studio SDK.  
  
 Všimněte si, že se první položky v seznamu položek colorable nikdy odkazuje. Visual Studio poskytuje vždy výchozí text barvy a atributy pro tuto položku. Nejjednodušším způsobem práci s to je zadat položku colorable zástupný text jako první položka.  
  
### <a name="high-color-colorable-items"></a>Vysoká barva Colorable položky  
 Colorable položek může také podporovat – hodnoty barev 24bitový nebo vysokou prostřednictvím <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> rozhraní. Sady MPF <xref:Microsoft.VisualStudio.Package.ColorableItem> třídy podporuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> rozhraní a 24bitové barvy se zadaným v konstruktoru společně s normální barvy. Najdete v článku <xref:Microsoft.VisualStudio.Package.ColorableItem> třída další podrobnosti. Následující příklad ukazuje, jak nastavit barvy 24bitový klíčová slova a komentáře. Barvy 24bitový se používají při 24bitové barvy se podporuje na ploše uživatele; barvy běžného textu, jinak se používají.  
  
 Mějte na paměti, že jedná se o výchozí barvy pro váš jazyk; uživatele můžete změnit tyto barvy na chtějí mít.  
  
### <a name="example"></a>Příklad  
 Tento příklad ukazuje jeden ze způsobů deklarace a naplnit pole vlastní colorable položky pomocí <xref:Microsoft.VisualStudio.Package.ColorableItem> třídy. Tento příklad nastaví barvy – klíčové slovo a komentář pomocí 24bitové barvy.  
  
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
  
## <a name="the-colorizer-class-and-the-scanner"></a>Třída Colorizer a skeneru  
 Základní <xref:Microsoft.VisualStudio.Package.LanguageService> třída má <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A> metoda této instantiantes <xref:Microsoft.VisualStudio.Package.Colorizer> třídy. Skener, která je vrácena z <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> metoda je předán <xref:Microsoft.VisualStudio.Package.Colorizer> konstruktoru třídy.  
  
 Musí implementovat <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> metoda ve vaší vlastní verzi <xref:Microsoft.VisualStudio.Package.LanguageService> třídy. <xref:Microsoft.VisualStudio.Package.Colorizer> Třída používá skeneru získat všechny informace o tokenu barev.  
  
 Skeneru potřebuje k naplnění <xref:Microsoft.VisualStudio.Package.TokenInfo> struktury pro každý token ho najde. Tato struktura obsahuje informace, jako například zabírá rozpětí token, index barev, které chcete použít, jaký typ je token a tokenu aktivačních událostí (viz <xref:Microsoft.VisualStudio.Package.TokenTriggers>). Pouze index rozpětí a barvu jsou potřebné pro zabarvení pomocí <xref:Microsoft.VisualStudio.Package.Colorizer> třídy.  
  
 Index barev uložené v <xref:Microsoft.VisualStudio.Package.TokenInfo> struktura je obvykle hodnotu z <xref:Microsoft.VisualStudio.Package.TokenColor> výčtu, který poskytuje řadu s názvem indexy odpovídající různé jazykové elementy, jako jsou klíčová slova a operátory. Pokud své vlastní colorable položky seznamu odpovídá položky uvedené v <xref:Microsoft.VisualStudio.Package.TokenColor> výčet a pak můžete jednoduše použít výčtu jako barvu pro každý token. Pokud máte další colorable položky nebo nechcete použít stávající hodnoty v tomto pořadí, můžete uspořádat vlastní colorable položek seznamu podle svých potřeb a vrátíte se do tohoto seznamu, odpovídající index. Jenom nezapomeňte přetypovat index <xref:Microsoft.VisualStudio.Package.TokenColor> při ukládání do <xref:Microsoft.VisualStudio.Package.TokenInfo> struktury; [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] vidí pouze index.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak může skeneru identifikovat tři typy tokenů: identifikátory (všechno, co není číslo ani interpunkce), interpunkce a čísla. V tomto příkladu je pouze pro ilustraci a nepředstavuje komplexní implementace analyzátor a skener. Předpokládá, že je `Lexer` třídy s `GetNextToken()` metodu, která vrátí řetězec.  
  
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
 [Funkce služby starší verze jazyka](../../extensibility/internals/legacy-language-service-features1.md)   
 [Analyzátor jazyka starší verze služby a skener](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)   
 [Registrace služby jazyk starší verze](../../extensibility/internals/registering-a-legacy-language-service1.md)