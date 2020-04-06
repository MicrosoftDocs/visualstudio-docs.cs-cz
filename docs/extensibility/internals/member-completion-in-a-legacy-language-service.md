---
title: Dokončení členství ve službě staršího jazyka | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Member Completion tool tip
- Member Completion, supporting in language services [managed package framework]
- language services [managed package framework], IntelliSense Member Completion
ms.assetid: 500f718d-9028-49a4-8615-ba95cf47fc52
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b6445aec4954590e4d361189f053592eebe7767e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707197"
---
# <a name="member-completion-in-a-legacy-language-service"></a>Dokončování členů ve službě starší verze jazyka

Dokončení člena Technologie IntelliSense je tip nástroje, který zobrazuje seznam možných členů určitého oboru, například třídy, struktury, výčtu nebo oboru názvů. Například v C#, pokud uživatel zadá "toto" následované tečkou, seznam všech členů třídy nebo struktury v aktuálním oboru je uveden v seznamu, ze kterého může uživatel vybrat.

Rámec spravovaného balíčku (MPF) poskytuje podporu pro tip nástroje a správu seznamu v tipu nástroje; vše, co je potřeba, je spolupráce analyzátoru na poskytnutí údajů, které jsou uvedeny v seznamu.

Starší jazykové služby jsou implementovány jako součást VSPackage, ale novější způsob implementace funkcí služby jazyka je použití rozšíření MEF. Další informace naleznete v [tématu Rozšíření editoru a jazykových služeb](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Doporučujeme, abyste co nejdříve začali používat nové rozhraní API editoru. Tím se zlepší výkon služby jazyka a umožní vám využít nové funkce editoru.

## <a name="how-it-works"></a>Jak to funguje

Následují dva způsoby, kterými je seznam členů zobrazen pomocí tříd MPF:

- Umístění stříšky na identifikátor nebo po znaku dokončení člena a **výběru seznamu členů** z nabídky **IntelliSense.**

- Skener <xref:Microsoft.VisualStudio.Package.IScanner> detekuje znak dokončení člena a nastaví aktivační událost tokenu [TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) pro tento znak.

Znak dokončení člena označuje, že člen třídy, struktury nebo výčtu je následovat. Například v jazyce C# nebo Visual `.`Basic je znak dokončení člena , `.` zatímco `->`v jazyce C++ je znak buď a nebo a . Hodnota aktivační události je nastavena při skenování znaku výběru člena.

### <a name="the-intellisense-member-list-command"></a>Příkaz Seznamu členů Technologie IntelliSense

Příkaz <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> inicializuje volání <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> metody <xref:Microsoft.VisualStudio.Package.Source> na class <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> a metoda, podle <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> pořadí, volá analyzátor metody s parse důvod [parse.DisplayMemberList](<xref:Microsoft.VisualStudio.Package.ParseReason.DisplayMemberList>).

Analyzátor určuje kontext aktuální pozice, stejně jako token pod nebo bezprostředně před aktuální pozici. Na základě tohoto tokenu je uveden seznam deklarací. Například v C#, pokud umístíte stříšku na člena třídy a vyberete **Seznam členů**, získáte seznam všech členů třídy. Pokud umístíte stříšku po období, které následuje za proměnnou objektu, získáte seznam všech členů třídy, která objekt představuje. Všimněte si, že pokud je stříška umístěna na členu při zobrazení seznamu členů, výběr člena ze seznamu nahradí člen, na který se stříška nachází, členem v seznamu.

### <a name="the-token-trigger"></a>Aktivační událost tokenu

Aktivační událost [TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) inicializuje <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> volání <xref:Microsoft.VisualStudio.Package.Source> metody <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> ve třídě a metoda zase volá analyzátor s důvodem analýzy [ParseReason.MemberSelect](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelect>). Pokud aktivační událost tokenu také obsahovalpříznak [TokenTriggers.MatchBraces,](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MatchBraces>) důvodem analýzy je [ParseReason.MemberSelectAndHighlightBraces](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelectAndHighlightBraces>), který kombinuje výběr členů a zvýraznění složených závorek.

Analyzátor určuje kontext aktuální pozice, stejně jako co bylo zadáno před znakem výběru člena. Z těchto informací analyzátor vytvoří seznam všech členů požadovaného oboru. Tento seznam deklarací je <xref:Microsoft.VisualStudio.Package.AuthoringScope> uložen v objektu, který je vrácen z <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metody. Pokud jsou vráceny nějaké deklarace, zobrazí se tip nástroje pro dokončení člena. Tip nástroje je spravován instancí třídy. <xref:Microsoft.VisualStudio.Package.CompletionSet>

## <a name="enable-support-for-member-completion"></a>Povolit podporu pro dokončení členů

Chcete-li `CodeSense` podporovat všechny operace Technologie IntelliSense, musíte mít položku registru nastavenou na 1. Tuto položku registru lze nastavit s <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> pojmenovaným parametrem předaným atributu uživatele přidruženému k jazykovému balíčku. Třídy jazykových služeb číst hodnotu <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> této položky registru z vlastnosti na třídu. <xref:Microsoft.VisualStudio.Package.LanguagePreferences>

Pokud skener vrátí aktivační událost tokenu [TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>)a analyzátor vrátí seznam deklarací, zobrazí se seznam dokončení členů.

## <a name="support-member-completion-in-the-scanner"></a>Dokončení člena podpory ve skeneru

Skener musí být schopen rozpoznat znak dokončení člena a nastavit aktivační událost tokenu [TokenTriggers.MemberSelect,](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) když je tento znak analyzován.

### <a name="scanner-example"></a>Příklad skeneru

Zde je zjednodušený příklad zjištění znaku dokončení <xref:Microsoft.VisualStudio.Package.TokenTriggers> člena a nastavení příslušného příznaku. Tento příklad je pouze pro ilustrační účely. Předpokládá, že skener obsahuje `GetNextToken` metodu, která identifikuje a vrací tokeny z řádku textu. Ukázkový kód jednoduše nastaví aktivační událost vždy, když vidí správný druh znaku.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestScanner : IScanner
    {
        private Lexer lex;
        private const char memberSelectChar = '.';

        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,
                                                   ref int state)
        {
            bool foundToken = false
            string token = lex.GetNextToken();
            if (token != null)
            {
                foundToken = true;
                char c = token[0];
                if (c == memberSelectChar)
                {
                        tokenInfo.Trigger |= TokenTriggers.MemberSelect;
                }
            }
            return foundToken;
        }
    }
}
```

## <a name="support-member-completion-in-the-parser"></a>Dokončení členů podpory v analyzátoru

Pro dokončení člena <xref:Microsoft.VisualStudio.Package.Source> třída <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> volá metodu. Je nutné implementovat seznam ve třídě, <xref:Microsoft.VisualStudio.Package.Declarations> která je odvozena z třídy. Podrobnosti <xref:Microsoft.VisualStudio.Package.Declarations> o metodách, které je nutné implementovat, naleznete ve třídě.

Analyzátor je volána s [ParseReason.MemberSelect](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelect>) nebo [ParseReason.MemberSelectAndHighlightBraces](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelectAndHighlightBraces>) při zadání znaku výběru člena. Umístění uvedené v <xref:Microsoft.VisualStudio.Package.ParseRequest> objektu je bezprostředně po znaku výběru člena. Analyzátor musí shromažďovat jména všech členů, které se mohou zobrazit v seznamu členů v daném bodě ve zdrojovém kódu. Potom analyzátor musí analyzovat aktuální řádek k určení oboru, který chce uživatel přidružit k znaku výběru člena.

Tento obor je založen na typu identifikátoru před znakem výběru člena. Například v jazyce C#, `languageService` vzhledem k `LanguageService`tomu, že členská proměnná má typ , psaní **languageService.** vytvoří seznam všech členů třídy. `LanguageService` Také v C#, zadáním **tohoto.** vytvoří seznam všech členů třídy v aktuálním oboru.

### <a name="parser-example"></a>Příklad analyzátoru

Následující příklad ukazuje jeden způsob, jak naplnit <xref:Microsoft.VisualStudio.Package.Declarations> seznam. Tento kód předpokládá, že analyzátor vytvoří deklaraci a přidá ji `AddDeclaration` do `TestAuthoringScope` seznamu voláním metody ve třídě.

```csharp
using System.Collections;
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    internal class TestDeclaration
    {
        public string Name;            // Name of declaration
        public int     TypeImageIndex; // Glyph index
        public string Description;     // Description of declaration

        public TestDeclaration(string name, int typeImageIndex, string description)
        {
            this.Name = name;
            this.TypeImageIndex = typeImageIndex;
            this.Description = description;
        }
    }

    //===================================================
    internal class TestDeclarations : Declarations
    {
        private ArrayList declarations;

        public TestDeclarations()
            : base()
        {
            declarations = new ArrayList();
        }

        public void AddDeclaration(TestDeclaration declaration)
        {
            declarations.Add(declaration);
        }

        //////////////////////////////////////////////////////////////////////
        // Declarations of class methods that must be implemented.
        public override int GetCount()
        {
            // Return the number of declarations to show.
            return declarations.Count;
        }

        public override string GetDescription(int index)
        {
            // Return the description of the specified item.
            string description = "";
            if (index >= 0 && index < declarations.Count)
            {
                description = ((TestDeclaration)declarations[index]).Description;
            }
            return description;
        }

        public override string GetDisplayText(int index)
        {
            // Determine what is displayed in the tool tip list.
            string text = null;
            if (index >= 0 && index < declarations.Count)
            {
                text = ((TestDeclaration)declarations[index]).Name;
            }
            return text;
        }

        public override int GetGlyph(int index)
        {
            // Return index of image to display next to the display text.
            int imageIndex = -1;
            if (index >= 0 && index < declarations.Count)
            {
                imageIndex = ((TestDeclaration)declarations[index]).TypeImageIndex;
            }
            return imageIndex;
        }

        public override string GetName(int index)
        {
            string name = null;
            if (index >= 0 && index < declarations.Count)
            {
                name = ((TestDeclaration)declarations[index]).Name;
            }
            return name;
        }
    }

    //===================================================
    public class TestAuthoringScope : AuthoringScope
    {
        private TestDeclarations declarationsList;

        public void AddDeclaration(TestDeclaration declaration)
        {
            if (declaration != null)
            {
                if (declarationsList == null)
                {
                    declarationsList = new TestDeclarations();
                }
                declarationsList.AddDeclaration(declaration);
            }
        }

        public override Declarations GetDeclarations(IVsTextView view,
                                                     int line,
                                                     int col,
                                                     TokenInfo info,
                                                     ParseReason reason)
        {
            return declarationsList;
        }

        /////////////////////////////////////////////////
        // Remainder of AuthoringScope methods not shown.
        /////////////////////////////////////////////////
    }

    //===================================================
    class TestLanguageService : LanguageService
    {
        public override AuthoringScope ParseSource(ParseRequest req)
        {
            TestAuthoringScope scope = new TestAuthoringScope();
            if (req.Reason == ParseReason.MemberSelect ||
                req.Reason == ParseReason.MemberSelectAndHighlightBraces)
            {
                // Gather list of declarations based on what the user
                // has typed so far. In this example, this list is an array of
                // MemberDeclaration objects (a helper class you might implement
                // to hold member declarations).
                // How this list is gathered is dependent on the parser
                // and is not shown here.
                MemberDeclarations memberDeclarations;
                memberDeclarations = GetDeclarationsForScope();

                // Now populate the Declarations list in the authoring scope.
                // GetImageIndexBasedOnType() is a helper method you
                // might implement to convert a member type to an index into
                // the image list returned from the language service.
                foreach (MemberDeclaration dec in memberDeclarations)
                {
                    scope.AddDeclaration(new TestDeclaration(
                                             dec.Name,
                                             GetImageIndexBasedOnType(dec.Type),
                                             dec.Description));
                }
            }
            return scope;
        }
    }
}
```
