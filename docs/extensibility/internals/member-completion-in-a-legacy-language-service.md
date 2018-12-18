---
title: Dokončení člen ve službě jazyk starší | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Member Completion tool tip
- Member Completion, supporting in language services [managed package framework]
- language services [managed package framework], IntelliSense Member Completion
ms.assetid: 500f718d-9028-49a4-8615-ba95cf47fc52
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8f618c9500b79ec5e1ef0db8c2c6b8b130c6c75b
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37057263"
---
# <a name="member-completion-in-a-legacy-language-service"></a>Dokončování členů ve službě starší verze jazyka

Dokončování IntelliSense člen je popis, který zobrazí seznam možných členy určité oboru, například třída, struktura, výčet nebo obor názvů. Například v C#, pokud uživatel zadá "to" následovaný tečkou, seznam všech členů třídu nebo strukturu v aktuálním oboru zobrazí v seznamu, ve kterém můžete vybrat uživatele.

Rozhraní spravované balíčku (MPF) poskytuje podporu pro popis tlačítka a správu seznamu v popisu tlačítka; všechno, co je potřeba je spolupráce z analyzátor zadat data, která se zobrazí v seznamu.

Starší verze jazyka služby jsou implementovány jako součást VSPackage, ale novější způsob implementace funkce služby jazyk je použití MEF rozšíření. Další informace naleznete v tématu [rozšíření pro Editor a služby, jazyk](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Doporučujeme vám, že začnete používat co nejdříve editoru nové rozhraní API. Tím zvýšit výkon služby jazyk a umožňují využívat výhod nových funkcí editoru.

## <a name="how-it-works"></a>Jak to funguje

Toto jsou dva způsoby, ve kterých se zobrazí seznam členů při použití sady MPF třídy:

- Umístění pomocí kurzoru na identifikátor nebo po dokončení znak člen a výběrem **vypsat členy** z **IntelliSense** nabídky.

- <xref:Microsoft.VisualStudio.Package.IScanner> Skener zjistí znak dokončení člen a nastaví tokenu aktivační událost s [TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) pro tento znak.

Znak dokončení člen označuje, že členem třídy, struktury nebo výčtu je podle. Například v C# nebo Visual Basic je znak dokončení člen `.`, zatímco v jazyce C++ znak, který je buď `.` nebo `->`. Aktivační událost hodnota je nastavena, když je skenován znak vyberte člena.

### <a name="the-intellisense-member-list-command"></a>Příkaz seznamu člen IntelliSense

<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> Příkaz zahájí volání <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> metodu <xref:Microsoft.VisualStudio.Package.Source> – třída a <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> naopak volá metody <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metoda analyzátor pomocí důvodu analýzy [ParseReason.DisplayMemberList ](<xref:Microsoft.VisualStudio.Package.ParseReason.DisplayMemberList>).

Analyzátor určuje kontextu aktuální pozici, jakož i token pod nebo bezprostředně před aktuální pozici. Podle tohoto tokenu, je uveden seznam deklarace. Například v jazyce C#, pokud umístit pomocí kurzoru na člen třídy a vyberte **vypsat členy**, zobrazí se seznam všech členů třídy. Jestliže po určitou dobu, která odpovídá proměnné objektu umístíte pomocí kurzoru, můžete získat seznam všech členů třídy, které představuje objekt. Všimněte si, že pokud znak je umístěn na člena, když se zobrazí seznam členů, výběr člena ze seznamu nahradí člen, ve které pomocí kurzoru s jedním v seznamu.

### <a name="the-token-trigger"></a>Token aktivační události

[TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) aktivační událost zahájí volání <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> metodu <xref:Microsoft.VisualStudio.Package.Source> – třída a <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> metoda, pak volá analyzátor pomocí důvodu analýzy [ ParseReason.MemberSelect](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelect>). Pokud token aktivační událost také obsaženy [TokenTriggers.MatchBraces](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MatchBraces>) příznak, je z důvodu analýzy [ParseReason.MemberSelectAndHighlightBraces](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelectAndHighlightBraces>), který kombinuje výběr členů a zvýraznění závorek .

Určuje analyzátor kontextu aktuálního umístit i napsané předtím, než člen vybrat znak. Z těchto informací vytvoří seznam všech členů požadovaném oboru. Tento seznam deklarace je uložený v <xref:Microsoft.VisualStudio.Package.AuthoringScope> objekt, který je vrácen z <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metoda. Pokud jsou vráceny všechny deklarace, se zobrazí popis tlačítka dokončení člen. Popis tlačítka spravuje instanci <xref:Microsoft.VisualStudio.Package.CompletionSet> třídy.

## <a name="enable-support-for-member-completion"></a>Povolení podpory pro dokončení člena

Musíte mít `CodeSense` položka registru nastavena na hodnotu 1 pro podporu všechny operace IntelliSense. Tato položka registru můžete nastavit uvedený parametr předaný <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> atribut uživatele přidružené k balíčku jazyk. Třídy služeb jazyk načíst hodnotu této položky registru z <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> vlastnost <xref:Microsoft.VisualStudio.Package.LanguagePreferences> třídy.

Pokud skener vrátí tokenu aktivační událost [TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>)a analyzátor jazyka vrátí seznam hodnot deklarace a pak se zobrazí seznam dokončení členů.

## <a name="support-member-completion-in-the-scanner"></a>Podpora člen dokončení v skeneru

Skeneru musí být schopen zjistit znak dokončení člen a nastavte tokenu aktivační událost [TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) při analýze tento znak.

### <a name="scanner-example"></a>Příklad skener

Zde je příklad zjednodušené detekovat znak dokončení člen a nastavení odpovídající <xref:Microsoft.VisualStudio.Package.TokenTriggers> příznak. V tomto příkladu je pouze pro ilustraci. Předpokládá, že skener obsahuje metodu `GetNextToken` který identifikuje a vrátí tokeny z řádku textu. Ukázkový kód jednoduše nastaví aktivační událost vždy, když se zobrazí správný druh znak.

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

## <a name="support-member-completion-in-the-parser"></a>Podpora člen dokončení analyzátoru

Pro dokončení člena <xref:Microsoft.VisualStudio.Package.Source> třídy volání <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> metoda. V seznamu musí implementovat třídu, která je odvozená od <xref:Microsoft.VisualStudio.Package.Declarations> třídy. Najdete v článku <xref:Microsoft.VisualStudio.Package.Declarations> třída podrobné informace o metodách musí implementovat.

Analyzátor je volán s [ParseReason.MemberSelect](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelect>) nebo [ParseReason.MemberSelectAndHighlightBraces](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelectAndHighlightBraces>) Pokud je zadán znak vyberte člena. V umístění <xref:Microsoft.VisualStudio.Package.ParseRequest> objekt je ihned po člen vyberte znak. Analyzátor musí shromažďovat názvy všech členů, které se mohou objevit v seznamu členů v daném okamžiku ve zdrojovém kódu. Pak musí analyzátor analyzovat aktuálního řádku k určení oboru, která chce uživatel přidružený znak vyberte člena.

Tento obor je založený na typu identifikátoru, předtím, než člen vybrat znak. Například v jazyce C#, uděleno členské proměnné `languageService` s typem `LanguageService`, zadáním **languageService.** Vytvoří seznam všech členů `LanguageService` třídy. Také v jazyce C# zadáním **to.** Vytvoří seznam všech členů třídy v aktuálním oboru.

### <a name="parser-example"></a>Příklad analyzátor

Následující příklad ukazuje jeden ze způsobů k naplnění <xref:Microsoft.VisualStudio.Package.Declarations> seznamu. Tento kód předpokládá, že analyzátor vytvoří deklaraci a přidá do seznamu voláním `AddDeclaration` metodu `TestAuthoringScope` třídy.

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