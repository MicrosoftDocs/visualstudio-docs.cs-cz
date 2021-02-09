---
title: Dokončení členů ve službě starší verze jazyka | Microsoft Docs
description: Přečtěte si, jak Tip nástroje pro dokončení členů technologie IntelliSense funguje ve službě starší verze jazyka a jak je podporován rozhraním MPF (Managed Package Framework).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Member Completion tool tip
- Member Completion, supporting in language services [managed package framework]
- language services [managed package framework], IntelliSense Member Completion
ms.assetid: 500f718d-9028-49a4-8615-ba95cf47fc52
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1a72b90530358346c2a20808deeb0050e6c72b8e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99839386"
---
# <a name="member-completion-in-a-legacy-language-service"></a>Dokončování členů ve službě starší verze jazyka

Dokončování členů technologie IntelliSense je popis tlačítka, který zobrazuje seznam možných členů konkrétního oboru, jako je třída, struktura, výčet nebo obor názvů. Například v jazyce C#, pokud uživatel zadá "This" následovaný tečkou, seznam všech členů třídy nebo struktury v aktuálním oboru je prezentován v seznamu, ze kterého může uživatel vybrat.

Sada Managed Package Framework (MPF) poskytuje podporu pro popis tlačítka a správu seznamu v popisu nástroje. vše, co je potřeba, je spolupráce z analyzátoru a poskytuje data, která se zobrazí v seznamu.

Starší jazykové služby jsou implementovány jako součást sady VSPackage, ale novější způsob, jak implementovat funkce jazykové služby, je použít rozšíření MEF. Další informace najdete v tématu [rozšíření editoru a jazykových služeb](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Doporučujeme začít používat nové rozhraní API editoru co nejrychleji. Tím se vylepšit výkon vaší jazykové služby a umožní vám využít nové funkce editoru.

## <a name="how-it-works"></a>Jak to funguje

Níže jsou uvedeny dva způsoby, jak se seznam členů zobrazuje pomocí tříd MPF:

- Pozice blikajícího kurzoru na identifikátor nebo po znaku dokončení členů a výběr **členů seznamu** z nabídky **technologie IntelliSense** .

- <xref:Microsoft.VisualStudio.Package.IScanner>Skener detekuje znak dokončení členů a pro tento znak nastaví Trigger tokenu [TokenTriggers. MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) .

Znak dokončení členů označuje, že je nutné sledovat člena třídy, struktury nebo výčtu. Například v jazyce C# nebo Visual Basic znak dokončení člena je `.` , zatímco v jazyce C++ je znak buď `.` nebo `->` . Hodnota triggeru je nastavena při prohledávání znaku výběru člena.

### <a name="the-intellisense-member-list-command"></a>Příkaz pro výpis členů IntelliSense

<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>Příkaz iniciuje volání <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> metody <xref:Microsoft.VisualStudio.Package.Source> třídy na třídu a <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> Metoda zase volá <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> analyzátor metody s důvodem analýzy [ParseReason. DisplayMemberList](<xref:Microsoft.VisualStudio.Package.ParseReason.DisplayMemberList>).

Analyzátor určuje kontext aktuální pozice a také token pod nebo bezprostředně před aktuální pozicí. Na základě tohoto tokenu se zobrazí seznam deklarací. Například v jazyce C#, pokud umístíte blikající kurzor na člena třídy a vyberete **seznam členů**, získáte seznam všech členů třídy. Pokud umístíte blikající kurzor po tečkě, která následuje za proměnnou objektu, získáte seznam všech členů třídy, které objekt představuje. Všimněte si, že pokud je kurzor umístěn na členu, když je zobrazen seznam členů, výběr člena ze seznamu nahradí člena, na kterém je kurzor v seznamu.

### <a name="the-token-trigger"></a>Aktivační událost tokenu

Aktivační událost [TokenTriggers. MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) inicializuje volání <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> metody <xref:Microsoft.VisualStudio.Package.Source> třídy na třídu a <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> Metoda pak zavolá analyzátor s důvodem analýzy [ParseReason. MemberSelect](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelect>). Pokud aktivační událost tokenu zahrnovala také příznak [TokenTriggers. MatchBraces](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MatchBraces>) , je důvod analýzy [ParseReason. MemberSelectAndHighlightBraces](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelectAndHighlightBraces>), který kombinuje výběr členů a zvýrazňování složených závorek.

Analyzátor určuje kontext aktuální pozice a také to, co byl zadán před vybraným znakem člena. Z těchto informací analyzátor vytvoří seznam všech členů požadovaného oboru. Tento seznam deklarací je uložen v <xref:Microsoft.VisualStudio.Package.AuthoringScope> objektu, který je vrácen z <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metody. Pokud jsou vráceny nějaké deklarace, zobrazí se popis nástroje pro dokončení členů. Popis nástroje je spravován instancí <xref:Microsoft.VisualStudio.Package.CompletionSet> třídy.

## <a name="enable-support-for-member-completion"></a>Povolit podporu pro dokončování členů

Aby bylo možné podporovat jakoukoli operaci technologie IntelliSense, je nutné, abyste měli `CodeSense` položku registru nastavenou na hodnotu 1. Tuto položku registru lze nastavit pomocí pojmenovaného parametru předaného do <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> atributu uživatele přidruženého k jazykovému balíčku. Třídy služby jazyka čtou hodnotu této položky registru z <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> vlastnosti <xref:Microsoft.VisualStudio.Package.LanguagePreferences> třídy.

Pokud váš skener vrátí Trigger tokenu [TokenTriggers. MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>)a váš analyzátor vrátí seznam deklarací, zobrazí se seznam dokončení členů.

## <a name="support-member-completion-in-the-scanner"></a>Doplňování členů podpory ve skeneru

Aby bylo možné tento znak analyzovat, musí být skener schopný detekovat znak dokončení členů a nastavit Trigger tokenu [TokenTriggers. MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) .

### <a name="scanner-example"></a>Příklad skeneru

Tady je zjednodušený příklad zjištění znaku dokončení členů a nastavení příslušného <xref:Microsoft.VisualStudio.Package.TokenTriggers> příznaku. Tento příklad je určen pouze pro ilustrativní účely. Předpokládá, že váš skener obsahuje metodu `GetNextToken` , která identifikuje a vrací tokeny z řádku textu. Vzorový kód jednoduše nastaví Trigger vždy, když se uvidí správný druh znaku.

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

## <a name="support-member-completion-in-the-parser"></a>Doplňování členů podpory v analyzátoru

Pro dokončení členů <xref:Microsoft.VisualStudio.Package.Source> třída volá <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> metodu. Je nutné implementovat seznam ve třídě, která je odvozena od <xref:Microsoft.VisualStudio.Package.Declarations> třídy. Další informace <xref:Microsoft.VisualStudio.Package.Declarations> o metodách, které je nutné implementovat, naleznete v třídě.

Analyzátor je volán pomocí [ParseReason. MemberSelect](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelect>) nebo [ParseReason. MemberSelectAndHighlightBraces](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelectAndHighlightBraces>) při zadání znaku pro výběr člena. Umístění zadané v <xref:Microsoft.VisualStudio.Package.ParseRequest> objektu je ihned po znaku výběru člena. Analyzátor musí shromažďovat názvy všech členů, které se mohou objevit v seznamu členů daného konkrétního bodu ve zdrojovém kódu. Poté analyzátor musí analyzovat aktuální řádek a určit tak rozsah, který uživatel potřebuje k výběru znaku.

Tento rozsah je založen na typu identifikátoru před vybraným znakem člena. Například v jazyce C#, s ohledem na členskou proměnnou `languageService` , která má typ `LanguageService` , zadejte **languageService.** Vytvoří seznam všech členů `LanguageService` třídy. Také v jazyce C# zadáním **tohoto příkazu.** Vytvoří seznam všech členů třídy v aktuálním oboru.

### <a name="parser-example"></a>Příklad analyzátoru

Následující příklad ukazuje jeden ze způsobů, jak naplnit <xref:Microsoft.VisualStudio.Package.Declarations> seznam. Tento kód předpokládá, že analyzátor vytvoří deklaraci a přidá ji do seznamu voláním `AddDeclaration` metody `TestAuthoringScope` třídy.

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
