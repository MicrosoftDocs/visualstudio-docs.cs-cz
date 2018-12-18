---
title: Barevné zvýrazňování syntaxe ve službě starší verze jazyka | Dokumentace Microsoftu
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
- language services [managed package framework], syntax highlighting
- colorization, supporting in language services [managed package framework]
- syntax highlighting, supporting in language services [managed package framework]
- language services [managed package framework], colorization
ms.assetid: 1ca1736a-f554-42e4-a9c7-fe8c3c1717df
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 20655534439fa187488087e1ae819a7ffca4c27a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51730283"
---
# <a name="syntax-colorizing-in-a-legacy-language-service"></a>Barevné zvýrazňování syntaxe ve službě starší verze jazyka
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Barevné zvýrazňování syntaxe je funkce, která způsobí, že různé prvky programovací jazyk, který se má zobrazit ve zdrojovém souboru v různé barvy a styly. Chcete-li tuto funkci podporují, budete muset zadat analyzátor a skener, který může identifikovat typy Lexikální prvky nebo tokenů v souboru. Řadu jiných jazyků rozlišit klíčová slova, oddělovače (jako je například kulatých závorek nebo složených závorek) a komentáře podle jejich barevné zvýrazňování různými způsoby.  
  
 Služby starší verze jazyka jsou implementovány jako součást sady VSPackage, ale novější způsob implementace funkce služba jazyka je pro použití rozšíření MEF. Další informace najdete v tématu [rozšíření pro Editor a jazykových služeb](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Doporučujeme vám, že začnete používat nový editor API co nejdříve. Tím vylepšíme výkonu vaší služby jazyka a umožňují využívat nové funkce editoru.  
  
## <a name="implementation"></a>Implementace  
 Pro podporu zabarvení, zahrnuje rozhraní spravovaného balíčku (MPF) <xref:Microsoft.VisualStudio.Package.Colorizer> třídy, která implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> rozhraní. Tato třída komunikuje <xref:Microsoft.VisualStudio.Package.IScanner> k určení tokenu a barvy. Další informace o skenery, naleznete v tématu [starší verze jazyka analyzátor a skener služby](../../extensibility/internals/legacy-language-service-parser-and-scanner.md). <xref:Microsoft.VisualStudio.Package.Colorizer> Třídy pak označí každý znak token s informace o barvě a vrátí tyto informace do editoru zobrazení zdrojového souboru.  
  
 Informace o barvě vrátit do editoru je index do seznamu, které lze zabarvit položek. Které lze zabarvit položky určuje hodnotu barvy a sadu atributů písma, jako například tučné písmo nebo přeškrtnutí. V editoru poskytuje sadu výchozích které lze zabarvit položek, které můžou používat vaše služba jazyka. Všechno, co je potřeba je zadat index odpovídající barev pro každý typ tokenu. Můžete však poskytnout sadu vlastní, které lze zabarvit položky a indexy, které zadáte pro tokeny a odkazují na vlastní seznam položek, které lze zabarvit namísto výchozího seznamu. Musíte taky nastavit `RequestStockColors` záznam v registru na hodnotu 0 (nebo nezadávejte `RequestStockColors` položky ve všech) pro podporu vlastních barev. Můžete nastavit tuto položku registru s pojmenovaným parametrem k <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> uživatelský atribut. Další informace o registraci služby jazyka a jeho možnosti nastavení najdete v tématu [registrace služby starší verze jazyka](../../extensibility/internals/registering-a-legacy-language-service1.md).  
  
## <a name="custom-colorable-items"></a>Vlastní položky, které lze zabarvit  
 Chcete-li zadat vlastní které lze zabarvit položek, je nutné přepsat <xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A> a <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A> metodu na <xref:Microsoft.VisualStudio.Package.LanguageService> třídy. První metoda vrátí počet vlastních které lze zabarvit položek, které podporuje služba jazyka a druhá získá vlastní které lze zabarvit položky podle indexu. Vytvoříte výchozí seznam položek, které lze zabarvit vlastní. V konstruktoru služby jazyka vše, co je potřeba je zadat každou které lze zabarvit položku s názvem. Visual Studio automaticky zpracovává případ, které si uživatel vybere jinou sadu položek, které lze zabarvit. Tento název se zobrazí v **písma a barvy** stránku vlastností na **možnosti** dialogové okno (k dispozici v sadě Visual Studio **nástroje** nabídky) a tento název určuje, které Barva uživatele přepsal. Možnosti uživatele jsou uloženy v mezipaměti v registru a přistupuje název barvy. **Písma a barvy** stránku vlastností jsou uvedeny všechny názvy barev v abecedním pořadí, tak můžete seskupit vlastních barev před každý název barvy s vaším jménem jazyk; například "**TestLanguage - Comment**"a"**TestLanguage – klíčové slovo**". Nebo můžete seskupit podle typu, které lze zabarvit položky "**komentář (TestLanguage)**"a"**– klíčové slovo (TestLanguage)**". Seskupení podle názvu jazyka je upřednostňována.  
  
> [!CAUTION]
>  Důrazně doporučujeme zahrnout název jazyka název které lze zabarvit položky pro zabránění kolizím s existující názvy, které lze zabarvit položky.  
  
> [!NOTE]
>  Pokud změníte název jedné z vašich barvy během vývoje, je nutné obnovit mezipaměti, která sadě Visual Studio vytvoří při prvním, které používaly barev. Můžete tak učinit spuštěním **resetovat experimentální Hive** z nabídky aplikace Visual Studio SDK.  
  
 Všimněte si, že první položka v seznamu položek, které lze zabarvit nikdy odkazován. Visual Studio vždy poskytuje výchozí barvy textu a atributy pro danou položku. Nejjednodušší způsob řešení problémů s tím je zadat položku které lze zabarvit zástupný text jako první položku.  
  
### <a name="high-color-colorable-items"></a>High Color, které lze zabarvit položky  
 Které lze zabarvit položek může také podporovat 24-bit nebo vysokou barevných prostřednictvím <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> rozhraní. MPF <xref:Microsoft.VisualStudio.Package.ColorableItem> třídy podporuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> rozhraní a barvy 24-bit jsou uvedeny v konstruktoru, společně s normální barvy. Zobrazit <xref:Microsoft.VisualStudio.Package.ColorableItem> třídy pro další podrobnosti. Následující příklad ukazuje, jak nastavit 24-bit barvy pro klíčová slova a komentáře. Barvy 24-bit se používají při 24-bit barva se podporuje na ploše uživatele; v opačném případě se používají normální text barvy.  
  
 Nezapomeňte, že jde o výchozí barvy pro váš jazyk; Uživatel může změnit tyto barvy na cokoli, co chtějí.  
  
### <a name="example"></a>Příklad  
 Tento příklad ukazuje jeden způsob, jak deklarovat a naplnit pole vlastní které lze zabarvit položek pomocí <xref:Microsoft.VisualStudio.Package.ColorableItem> třídy. V tomto příkladu nastaví barvy – klíčové slovo a komentáře pomocí 24 bitů barev.  
  
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
                new ColorableItem("TestLanguage – Text",  
                                  "Text",  
                                  COLORINDEX.CI_SYSPLAINTEXT_FG,  
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,  
                                  System.Drawing.Color.Empty,  
                                  System.Drawing.Color.Empty,  
                                  FONTFLAGS.FF_DEFAULT),  
                new ColorableItem("TestLanguage – Keyword",  
                                  "Keyword",  
                                  COLORINDEX.CI_MAROON,  
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,  
                                  System.Drawing.Color.FromArgb(192,32,32),  
                                  System.Drawing.Color.Empty,  
                                  FONTFLAGS.FF_BOLD),  
                new ColorableItem("TestLanguage – Comment",  
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
 Základní <xref:Microsoft.VisualStudio.Package.LanguageService> třída nemá <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A> metoda této instantiantes <xref:Microsoft.VisualStudio.Package.Colorizer> třídy. Skener, která je vrácena z <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> metoda předána <xref:Microsoft.VisualStudio.Package.Colorizer> konstruktoru třídy.  
  
 Je nutné implementovat <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> metodu ve vaší vlastní verzi <xref:Microsoft.VisualStudio.Package.LanguageService> třídy. <xref:Microsoft.VisualStudio.Package.Colorizer> Třídy pomocí čtečky získat všechny informace o tokenu barvě.  
  
 Skener potřebuje k vyplnění <xref:Microsoft.VisualStudio.Package.TokenInfo> strukturu pro každý token ho najde. Tato struktura obsahuje informace, jako například zabírá rozsah tokenu, index barev, které chcete použít, jaký typ je tokenu a tokenu aktivační události (viz <xref:Microsoft.VisualStudio.Package.TokenTriggers>). Zabarvení podle, jsou potřeba pouze index rozpětí a barvu <xref:Microsoft.VisualStudio.Package.Colorizer> třídy.  
  
 Index barev uložené v <xref:Microsoft.VisualStudio.Package.TokenInfo> struktura je obvykle hodnotu z <xref:Microsoft.VisualStudio.Package.TokenColor> výčet, který nabízí celou řadu pojmenovaných indexy, které odpovídají různé prvky jazyka, jako jsou klíčová slova a operátory. Pokud vaše vlastní které lze zabarvit položky seznamu shody položky uvedené v <xref:Microsoft.VisualStudio.Package.TokenColor> výčet a pak můžete pouze použijte výčet jako barvu pro každý token. Pokud máte další které lze zabarvit položky nebo nechcete použít stávající hodnoty v tomto pořadí, je uspořádat vlastní které lze zabarvit položek seznamu podle svých potřeb a vrátí odpovídající index do tohoto seznamu. Jenom nezapomeňte přetypování index <xref:Microsoft.VisualStudio.Package.TokenColor> při ukládání v <xref:Microsoft.VisualStudio.Package.TokenInfo> struktury; [!INCLUDE[vs_current_short](../../includes/vs-current-short-md.md)] vidí pouze index.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak skener může identifikovat tři typy tokenů: identifikátory (cokoli, co se nejedná o číslo ani interpunkční znaménka), interpunkce a čísla. V tomto příkladu je pouze pro ilustraci a nepředstavuje komplexní implementace analyzátor a skener. Předpokládá, že je `Lexer` třídy s `GetNextToken()` metodu, která vrátí hodnotu typu string.  
  
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
 [Starší verze jazyka analyzátor a skener služby](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)   
 [Registrace služby starší verze jazyka](../../extensibility/internals/registering-a-legacy-language-service1.md)

