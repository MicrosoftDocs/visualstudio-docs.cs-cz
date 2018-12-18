---
title: Dokončování členů ve službě starší verze jazyka | Dokumentace Microsoftu
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
- IntelliSense, Member Completion tool tip
- Member Completion, supporting in language services [managed package framework]
- language services [managed package framework], IntelliSense Member Completion
ms.assetid: 500f718d-9028-49a4-8615-ba95cf47fc52
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b8b5940e473c639600c30e66e7dc0c732359322d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51790981"
---
# <a name="member-completion-in-a-legacy-language-service"></a>Dokončování členů ve službě starší verze jazyka
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Člen doplňování technologie IntelliSense je popisku tlačítka, která zobrazuje seznam možných členů určitého oboru jako třída, struktura, výčet nebo oboru názvů. Například v jazyce C#, pokud uživatel zadá "this" následovaných tečkou, seznam všech členů třídy nebo struktury v aktuálním oboru se zobrazí v seznamu, ze kterého může uživatel vybrat.  
  
 Rozhraní spravovaného balíčku (MPF) poskytuje podporu pro popis tlačítka a správu seznamu v popisu tlačítka; vše, co je potřeba je spolupráce z analyzátor, který má poskytnout data, která se zobrazí v seznamu.  
  
 Služby starší verze jazyka jsou implementovány jako součást sady VSPackage, ale novější způsob implementace funkce služba jazyka je pro použití rozšíření MEF. Další informace najdete v tématu [rozšíření pro Editor a jazykových služeb](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Doporučujeme vám, že začnete používat nový editor API co nejdříve. Tím vylepšíme výkonu vaší služby jazyka a umožňují využívat nové funkce editoru.  
  
## <a name="how-it-works"></a>Jak to funguje  
 Následují dva způsoby, ve kterých se zobrazí seznam členů třídy MPF pomocí:  
  
- Umístění blikající kurzor na identifikátor nebo za znakem ukončení člena a vyberete **seznam členů** z **IntelliSense** nabídky.  
  
- <xref:Microsoft.VisualStudio.Package.IScanner> Skener zjistí znak člen dokončení a nastaví token aktivační událost s <xref:Microsoft.VisualStudio.Package.TokenTriggers> pro daný znak.  
  
  Člen dokončení znak označuje, že je členem třídy, struktury nebo výčtu dodržovat. Například v jazyce C# nebo Visual Basic je znak dokončení člena `.`, zatímco v jazyce C++ je znak, který buď `.` nebo `->`. Aktivační událost hodnota, při kontrole vyberte znak člena.  
  
### <a name="the-intellisense-member-list-command"></a>Příkaz seznamu členů IntelliSense  
 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> Příkaz zahájí volání <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> metodu <xref:Microsoft.VisualStudio.Package.Source> třídy a <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> zase volání metody <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metoda analyzátoru s důvod analýzy <xref:Microsoft.VisualStudio.Package.ParseReason>.  
  
 Určuje analyzátor kontextu aktuální pozici, jakož i token pod nebo bezprostředně před aktuální pozici. Na základě tohoto tokenu, se zobrazí seznam deklarací. Například v jazyce C#, pokud pozice blikajícího kurzoru na člen třídy a vyberte **seznam členů**, získání seznamu všech členů třídy. Pokud umístíte blikající kurzor po určitou dobu, která odpovídá proměnné objektu, získání seznamu všech členů třídy, které objekt představuje. Všimněte si, že pokud je kurzor na člen když se zobrazí seznam členů, výběr člena ze seznamu nahradí členu, který je blikající kurzor na s jednou v seznamu.  
  
### <a name="the-token-trigger"></a>Token aktivační událost  
 <xref:Microsoft.VisualStudio.Package.TokenTriggers> Aktivační událost zahájí volání <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> metodu na <xref:Microsoft.VisualStudio.Package.Source> třídy a <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> metody volá analyzátor s důvod analýzy <xref:Microsoft.VisualStudio.Package.ParseReason> (pokud token aktivační události obsahuje taky <xref:Microsoft.VisualStudio.Package.TokenTriggers> příznak, z důvodu analýzy je <xref:Microsoft.VisualStudio.Package.ParseReason> zahrnující výběr členů a zvýraznění závorek).  
  
 Určuje analyzátor, kontext aktuálního umístění a také, co byla zadána před člen vyberte znak. Z těchto informací že analyzátor vytvoří seznam všech členů požadovaném oboru. Tento seznam deklarací je uložen v <xref:Microsoft.VisualStudio.Package.AuthoringScope> objekt, který je vrácen z <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metody. Pokud jsou vráceny všechny deklarace, zobrazí se popis tlačítka člen dokončení. Popis tlačítka spravuje instance <xref:Microsoft.VisualStudio.Package.CompletionSet> třídy.  
  
## <a name="enabling-support-for-member-completion"></a>Povolení podpory pro dokončování členů  
 Musíte mít `CodeSense` položka registru nastavena na hodnotu 1 pro podporu všechny operace IntelliSense. Tato položka registru můžete nastavit pomocí pojmenovaný parametr předaný <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> atribut uživatele přidružené k balíčku jazyka. Třídy služeb jazyka načetla se hodnota této položky registru z <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> vlastnost <xref:Microsoft.VisualStudio.Package.LanguagePreferences> třídy.  
  
 Pokud skener vrátí token aktivační událost s <xref:Microsoft.VisualStudio.Package.TokenTriggers>a analyzátor jazyka vrátí seznam hodnot deklarace a pak se zobrazí seznam dokončení členů.  
  
## <a name="supporting-member-completion-in-the-scanner"></a>Podpora dokončování členů ve skener  
 Skener musí být schopen rozpoznat znak dokončení člen a nastavte token aktivační událost s <xref:Microsoft.VisualStudio.Package.TokenTriggers> při analyzovat tento znak.  
  
### <a name="example"></a>Příklad  
 Tady je zjednodušený příklad detekovat znak dokončení člena a nastavení odpovídající <xref:Microsoft.VisualStudio.Package.TokenTriggers> příznak. V tomto příkladu je pouze pro ilustraci. Předpokládá, že skener obsahuje metodu `GetNextToken` , který identifikuje a vrátí tokeny z řádku textu. Pokaždé, když se zobrazí správný typ znaku, ukázkový kód jednoduše nastaví aktivační událost.  
  
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
  
## <a name="supporting-member-completion-in-the-parser"></a>Podpora dokončování členů ve analyzátor  
 Pro dokončování členů <xref:Microsoft.VisualStudio.Package.Source> třídy volání <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> metody. V seznamu musí implementovat do třídy, která je odvozena od <xref:Microsoft.VisualStudio.Package.Declarations> třídy. Zobrazit <xref:Microsoft.VisualStudio.Package.Declarations> podrobné informace o metodách musí implementovat třídu.  
  
 Analyzátor je volána s <xref:Microsoft.VisualStudio.Package.ParseReason> nebo <xref:Microsoft.VisualStudio.Package.ParseReason> po zadání znaku vyberte člena. Umístění podle <xref:Microsoft.VisualStudio.Package.ParseRequest> je objekt okamžitě po člen vyberte znak. Analyzátor musí shromáždit názvy všech členů, které se mohou objevit v seznamu členů v daný okamžik ve zdrojovém kódu. Analyzátor musí pak parsovat aktuální řádek do určit obor, který chce uživatel přidružený vyberte znak člena.  
  
 Tento obor je založená na typu identifikátor před člen vyberte znak. V jazyce C#, například členskou proměnnou `languageService` , která má typ `LanguageService`, zadáním **languageService.** Vytvoří seznam všech členů `LanguageService` třídy. Také v jazyce C# psát **to.** Vytvoří seznam všech členů třídy v aktuálním oboru.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje jeden způsob, jak naplnit <xref:Microsoft.VisualStudio.Package.Declarations> seznamu. Tento kód předpokládá, že analyzátor vytvoří deklaraci a přidá ji do seznamu voláním `AddDeclaration` metodu `TestAuthoringScope` třídy.  
  
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

