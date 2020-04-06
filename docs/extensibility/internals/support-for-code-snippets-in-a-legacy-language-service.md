---
title: Podpora fragmentů kódu ve starší jazykové službě | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- snippets, supporting in language services
- code snippets, supporting in language services [managed package framework]
- language services [managed package framework], supporting code snippets
ms.assetid: 7490325b-acee-4c2d-ac56-1cd5db1a1083
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ad871eb73341f6ab87229687e2a6df898ffda32d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704915"
---
# <a name="support-for-code-snippets-in-a-legacy-language-service"></a>Podpora pro fragmenty kódu ve službě starší verze jazyka
Fragment kódu je část kódu, která je vložena do zdrojového souboru. Samotný úryvek je šablona založená na XML se sadou polí. Tato pole jsou zvýrazněna po vložení fragmentu a mohou mít různé hodnoty v závislosti na kontextu, ve kterém je fragment vložen. Ihned po vložení fragmentu může jazyková služba fragment formátovat.

 Úryvek je vložen ve speciálním režimu úprav, který umožňuje navigaci polí fragmentu pomocí klávesy TAB. Pole mohou podporovat rozevírací nabídky ve stylu Technologie IntelliSense. Uživatel potvrdí výstřižek do zdrojového souboru zadáním klávesy ENTER nebo ESC. Další informace o úryvcích naleznete v [tématu Fragmenty kódu](../../ide/code-snippets.md).

 Starší jazykové služby jsou implementovány jako součást VSPackage, ale novější způsob implementace funkcí služby jazyka je použití rozšíření MEF. Další informace naleznete [v tématu Návod: Implementace fragmentů kódu](../../extensibility/walkthrough-implementing-code-snippets.md).

> [!NOTE]
> Doporučujeme, abyste co nejdříve začali používat nové rozhraní API editoru. Tím se zlepší výkon služby jazyka a umožní vám využít nové funkce editoru.

## <a name="managed-package-framework-support-for-code-snippets"></a>Podpora rámce spravovaného balíčku pro fragmenty kódu
 Architektura spravovaného balíčku (MPF) podporuje většinu funkcí fragmentu, od čtení šablony až po vložení fragmentu a povolení speciálního režimu úprav. Podpora je spravována prostřednictvím třídy. <xref:Microsoft.VisualStudio.Package.ExpansionProvider>

 Když <xref:Microsoft.VisualStudio.Package.Source> je instance třídy, <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A> metoda ve <xref:Microsoft.VisualStudio.Package.LanguageService> třídě je volána k <xref:Microsoft.VisualStudio.Package.ExpansionProvider> získání <xref:Microsoft.VisualStudio.Package.LanguageService> objektu (všimněte si, že základní třída vždy vrátí nový <xref:Microsoft.VisualStudio.Package.ExpansionProvider> objekt pro každý <xref:Microsoft.VisualStudio.Package.Source> objekt).

 MPF nepodporuje rozšiřující funkce. Rozšiřující funkce je pojmenovaná funkce, která je vložena do šablony úryvku a vrací jednu nebo více hodnot, které mají být umístěny do pole. Hodnoty jsou vráceny samotnou jazykovou službou prostřednictvím objektu. <xref:Microsoft.VisualStudio.Package.ExpansionFunction> Objekt <xref:Microsoft.VisualStudio.Package.ExpansionFunction> musí být implementován službou jazyka pro podporu rozšiřujících funkcí.

## <a name="providing-support-for-code-snippets"></a>Poskytování podpory pro fragmenty kódu
 Chcete-li povolit podporu pro fragmenty kódu, je nutné zadat nebo nainstalovat výstřižky a je nutné poskytnout prostředky pro uživatele vložit tyto výstřižky. Existují tři kroky k povolení podpory pro fragmenty kódu:

1. Instalace souborů úryvků.

2. Povolení fragmentů kódu pro jazykovou službu.

3. Vyvolání objektu. <xref:Microsoft.VisualStudio.Package.ExpansionProvider>

### <a name="installing-the-snippet-files"></a>Instalace souborů úryvků
 Všechny úryvky pro jazyk jsou uloženy jako šablony v souborech XML, obvykle jedna šablona výstřižku na soubor. Podrobnosti o schématu XML použitém pro šablony fragmentů kódu naleznete v [tématu Odkaz na schéma fragmentů kódu](../../ide/code-snippets-schema-reference.md). Každá šablona úryvku je označena ID jazyka. Toto ID jazyka je zadáno v `Language` registru \<a je vloženo do atributu značka Code> v šabloně.

 Obvykle existují dvě umístění, kde jsou uloženy soubory šablon výstřižků: 1) kde byl nainstalován jazyk a 2) ve složce uživatele. Tato umístění jsou přidána do registru, aby **správce výstřižků kódu** sady Visual Studio mohl výstřižky najít. Složka uživatele je místo, kde jsou uloženy úryvky vytvořené uživatelem.

 Typické rozložení složky pro nainstalované soubory šablon úryvku vypadá takto: *[InstallRoot]*\\ *[TestLanguage]* \Snippets\\ *[LCID]* \Snippets.

 *[InstallRoot]* je složka, ve které je jazyk nainstalován.

 *[TestLanguage]* je název vašeho jazyka jako názvu složky.

 *[LCID]* je ID národního prostředí. Takto jsou uloženy lokalizované verze výstřižků. Například ID národního prostředí pro angličtinu je 1033, takže *[LCID]* je nahrazen 1033.

 Musí být zadán jeden další soubor, který je indexový soubor, obvykle nazývaný SnippetsIndex.xml nebo ExpansionsIndex.xml (můžete použít libovolný platný název souboru končící na .xml). Tento soubor je obvykle uložen ve složce *[InstallRoot]*\\ *[TestLanguage]* a určuje přesné umístění složky výstřižky, stejně jako ID jazyka a GUID jazykové služby, která používá výstřižky. Přesná cesta souboru indexu je vložena do registru, jak je popsáno dále v části "Instalace položek registru". Zde je příklad souboru SnippetsIndex.xml:

```
<?xml version="1.0" encoding="utf-8" ?>
<SnippetCollection>
    <Language Lang="Testlanguage" Guid="{b614a40a-80d9-4fac-a6ad-fc2868fff7cd}">
        <SnippetDir>
            <OnOff>On</OnOff>
            <Installed>true</Installed>
            <Locale>1033</Locale>
            <DirPath>%InstallRoot%\TestLanguage\Snippets\%LCID%\Snippets\</DirPath>
            <LocalizedName>Snippets</LocalizedName>
        </SnippetDir>
    </Language>
</SnippetCollection>
```

 Značka \<Language> určuje ID jazyka `Lang` (atribut) a identifikátor GUID jazykové služby.

 Tento příklad předpokládá, že jste nainstalovali jazykovou službu do instalační složky sady Visual Studio. %LCID% je nahrazeno id aktuálního národního prostředí uživatele. Lze \<přidat více značek> SnippetDir, jednu pro každý jiný adresář a národní prostředí. Složka složky úryvek může navíc obsahovat podsložky, z nichž \<každá je v souboru indexu identifikována \<> značkou SnippetSubDir, která je vložena do> značky SnippetDir.

 Uživatelé mohou také vytvářet vlastní úryvky pro váš jazyk. Ty jsou obvykle uloženy ve složce nastavení uživatele, například *[TestDocs]* \Fragmenty\\kódu *[TestLanguage]* \Test Code Snippets, kde *[TestDocs]* je umístění složky nastavení uživatele pro Visual Studio.

 Následující substituční prvky lze \<umístit do cesty uložené v> značce DirPath v souboru indexu.

|Element|Popis|
|-------------|-----------------|
|%LCID %|ID národního prostředí.|
|%InstallRoot%|Kořenová instalační složka sady Visual Studio, například C:\Program Files\Microsoft Visual Studio 8.|
|%ProjDir%|Složka obsahující aktuální projekt.|
|%ProjItem%|Složka obsahující aktuální položku projektu.|
|%TestDocs%|Složka ve složce nastavení uživatele, například C:\Documents and Settings\\ *[uživatelské jméno]* \Dokumenty\Visual Studio\8.|

### <a name="enabling-code-snippets-for-your-language-service"></a>Povolení fragmentů kódu pro vaši jazykovou službu
 Fragmenty kódu pro jazykovou službu můžete <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> povolit přidáním atributu do balíčku VSPackage (podrobnosti najdete v [tématu Registrace služby staršího jazyka).](../../extensibility/internals/registering-a-legacy-language-service1.md) <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.ShowRoots%2A> Parametry <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.SearchPaths%2A> a jsou volitelné, ale `SearchPaths` měli byste zahrnout pojmenovaný parametr, abyste informovali **správce fragmentů kódu** o umístění fragmentů.

 Následuje příklad použití tohoto atributu:

```
[ProvideLanguageCodeExpansion(
         typeof(TestSnippetLanguageService),
         "Test Snippet Language",          // Name of language used as registry key
         0,                               // Resource ID of localized name of language service
         "Test Snippet Language",        // Name of Language attribute in snippet template
         @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\SnippetsIndex.xml",  // Path to snippets index
         SearchPaths = @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\")]    // Path to snippets
```

### <a name="calling-the-expansion-provider"></a>Volání zprostředkovatele rozšíření
 Služba jazyka řídí vkládání libovolného fragmentu kódu a také způsob vyvolání vložení.

## <a name="calling-the-expansion-provider-for-code-snippets"></a>Volání zprostředkovatele rozšíření pro fragmenty kódu
 Zprostředkovatele rozšíření lze vyvolat dvěma způsoby: pomocí příkazu nabídky nebo pomocí zástupce ze seznamu dokončení.

### <a name="inserting-a-code-snippet-by-using-a-menu-command"></a>Vložení fragmentu kódu pomocí příkazu nabídky
 Chcete-li použít příkaz nabídky k zobrazení prohlížeče výstřižků, <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> přidejte <xref:Microsoft.VisualStudio.Package.ExpansionProvider> příkaz nabídky a potom v reakci na tento příkaz nabídky zavoláte metodu v rozhraní.

1. Přidejte příkaz a tlačítko do souboru .vsct. Pokyny k tomu najdete v [příkazu Vytvoření rozšíření pomocí příkazu nabídky](../../extensibility/creating-an-extension-with-a-menu-command.md).

2. Odvodit <xref:Microsoft.VisualStudio.Package.ViewFilter> třídu z <xref:Microsoft.VisualStudio.Package.ViewFilter.QueryCommandStatus%2A> třídy a přepsat metodu k označení podpory pro nový příkaz nabídky. Tento příklad vždy povolí příkaz nabídky.

    ```csharp
    using Microsoft.VisualStudio.Package;

    namespace TestLanguagePackage
    {
        class TestViewFilter : ViewFilter
        {
            public TestViewFilter(CodeWindowManager mgr, IVsTextView view)
                : base(mgr, view)
            {
            }

            protected override int QueryCommandStatus(ref Guid guidCmdGroup,
                                                      uint nCmdId)
            {
                int hr = base.QueryCommandStatus(ref guidCmdGroup, nCmdId);
                // If the base class did not recognize the command then
                // see if we can handle the command.
                if (hr == (int)Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP)
                {
                    if (guidCmdGroup == GuidList.guidTestLanguagePackageCmdSet)
                    {
                        if (nCmdId == PkgCmdIDList.InvokeCodeSnippetsBrowser)
                        {
                            hr = (int)(OLECMDF.OLECMDF_SUPPORTED | OLECMDF.OLECMDF_ENABLED);
                        }
                    }
                }
                return hr;
            }
        }
    }
    ```

3. <xref:Microsoft.VisualStudio.Package.ViewFilter.HandlePreExec%2A> Přepsat metodu ve <xref:Microsoft.VisualStudio.Package.ViewFilter> třídě získat <xref:Microsoft.VisualStudio.Package.ExpansionProvider> objekt a <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> volání metody na tento objekt.

    ```csharp
    using Microsoft.VisualStudio.Package;

    namespace TestLanguagePackage
    {
        class TestViewFilter : ViewFilter
        {
            public override bool HandlePreExec(ref Guid guidCmdGroup,
                                               uint nCmdId,
                                               uint nCmdexecopt,
                                               IntPtr pvaIn,
                                               IntPtr pvaOut)
            {
                if (base.HandlePreExec(ref guidCmdGroup,
                                       nCmdId,
                                       nCmdexecopt,
                                       pvaIn,
                                       pvaOut))
                {
                    // Base class handled the command.  Do nothing more here.
                    return true;
                }

                if (guidCmdGroup == GuidList.guidTestLanguagePackageCmdSet)
                {
                    if (nCmdId == PkgCmdIDList.InvokeCodeSnippetsBrowser)
                    {
                        ExpansionProvider ep = this.GetExpansionProvider();
                        if (this.TextView != null && ep != null)
                        {
                            bool bDisplayed = ep.DisplayExpansionBrowser(
                                this.TextView,
                                "TestLanguagePackage Snippet:",
                                null,
                                false,
                                null,
                                false);
                        }
                        return true;   // Handled the command.
                    }
                }
                return false;   // Did not handle the command.
            }
        }
    }

    ```

     Následující metody ve <xref:Microsoft.VisualStudio.Package.ExpansionProvider> třídě jsou volány Visual Studio v daném pořadí během procesu vkládání výstřižku:

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnItemChosen%2A>

5. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

6. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

7. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

8. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

     Po <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A> volání metody byl vložen výstřižek a <xref:Microsoft.VisualStudio.Package.ExpansionProvider> objekt je ve speciálním režimu úprav, který se používá k úpravě fragmentu, který byl právě vložen.

### <a name="inserting-a-code-snippet-by-using-a-shortcut"></a>Vložení fragmentu kódu pomocí zástupce
 Implementace zástupce ze seznamu dokončení je mnohem více než implementace příkazu nabídky. Do seznamu dokončení slov Technologie IntelliSense je nutné nejprve přidat zástupce výstřižků. Potom je nutné zjistit, kdy byl vložen název zástupce fragmentu jako výsledek dokončení. Nakonec je nutné získat název fragmentu a cestu pomocí názvu zástupce <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> a předat <xref:Microsoft.VisualStudio.Package.ExpansionProvider> tyto informace metodě metody.

 Chcete-li přidat zástupce výstřižků do seznamu <xref:Microsoft.VisualStudio.Package.Declarations> dokončení slov, přidejte je do objektu ve třídě. <xref:Microsoft.VisualStudio.Package.AuthoringScope> Musíte se ujistit, že můžete identifikovat zástupce jako název výstřižku. Příklad najdete [v tématu Návod: Získání seznamu nainstalovaných fragmentů kódu (starší implementace)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).

 Můžete zjistit vložení zástupce fragmentu kódu v metodě <xref:Microsoft.VisualStudio.Package.Declarations.OnAutoComplete%2A> třídy. <xref:Microsoft.VisualStudio.Package.Declarations> Vzhledem k tomu, že název fragmentu byl již vložen do zdrojového souboru, musí být odebrán při vložení rozšíření. Metoda <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> trvá rozpětí, které popisuje bod vložení pro úryvek; pokud rozpětí obsahuje celý název fragmentu ve zdrojovém souboru, bude tento název nahrazen fragmentem.

 Zde je verze <xref:Microsoft.VisualStudio.Package.Declarations> třídy, která zpracovává vložení fragmentu zadaný název zástupce. Jiné metody <xref:Microsoft.VisualStudio.Package.Declarations> ve třídě byly vynechány pro přehlednost. Všimněte si, že konstruktor <xref:Microsoft.VisualStudio.Package.LanguageService> této třídy trvá objekt. To může být předánz verze <xref:Microsoft.VisualStudio.Package.AuthoringScope> objektu (například implementace <xref:Microsoft.VisualStudio.Package.AuthoringScope> třídy <xref:Microsoft.VisualStudio.Package.LanguageService> může mít objekt v jeho konstruktoru a předat tento objekt na konstruktoru `TestDeclarations` třídy).

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    internal class TestDeclarations : Declarations
    {
        private ArrayList       declarations;
        private LanguageService languageService;
        private TextSpan        commitSpan;

        public TestDeclarations(LanguageService langService)
            : base()
        {
            languageService = langService;
            declarations = new ArrayList();
        }

        // This method is used to add declarations to the internal list.
        public void AddDeclaration(TestDeclaration declaration)
        {
            declarations.Add(declaration);
        }

        // This method is called to get the string to commit to the source buffer.
        // Note that the initial extent is only what the user has typed so far.
        public override string OnCommit(IVsTextView textView,
                                        string textSoFar,
                                        char commitCharacter,
                                        int index,
                                        ref TextSpan initialExtent)
        {
            // We intercept this call only to get the initial extent
            // of what was committed to the source buffer.
            commitSpan = initialExtent;

            return base.OnCommit(textView,
                                 textSoFar,
                                 commitCharacter,
                                 index,
                                 ref initialExtent);
        }

        // This method is called after the string has been committed to the source buffer.
        public override char OnAutoComplete(IVsTextView textView,
                                            string committedText,
                                            char commitCharacter,
                                            int index)
        {
            TestDeclaration item = declarations[index] as TestDeclaration;
            if (item != null)
            {
                // In this example, TestDeclaration identifies types with a string.
                // You can choose a different approach.
                if (item.Type == "snippet")
                {
                    Source src = languageService.GetSource(textView);
                    if (src != null)
                    {
                        ExpansionProvider ep = src.GetExpansionProvider();
                        if (ep != null)
                        {
                            string title;
                            string path;
                            int commitLength = commitSpan.iEndIndex - commitSpan.iStartIndex;
                            if (commitLength < committedText.Length)
                            {
                                // Replace everything that was inserted
                                // so calculate the span of the full
                                // insertion, taking into account what
                                // was inserted when the commitSpan
                                // was obtained in the first place.
                                commitSpan.iEndIndex += (committedText.Length - commitLength);
                            }

                            if (ep.FindExpansionByShortcut(textView,
                                                           committedText,
                                                           commitSpan,
                                                           true,
                                                           out title,
                                                           out path))
                            {
                                ep.InsertNamedExpansion(textView,
                                                        title,
                                                        path,
                                                        commitSpan,
                                                        false);
                            }
                        }
                    }
                }
            }
            return '\0';
        }
    }
}
```

 Když služba jazyka získá název zástupce, <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FindExpansionByShortcut%2A> zavolá metodu k získání názvu souboru a názvu fragmentu kódu. Služba jazyka pak <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> volá metodu ve <xref:Microsoft.VisualStudio.Package.ExpansionProvider> třídě vložit fragment kódu. Následující metody jsou volány Visual Studio v <xref:Microsoft.VisualStudio.Package.ExpansionProvider> daném pořadí ve třídě během procesu vkládání výstřižku:

1. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

2. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

3. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

   Další informace o získání seznamu nainstalovaných fragmentů kódu pro vaši jazykovou službu naleznete [v tématu Návod: Získání seznamu nainstalovaných fragmentů kódu (starší implementace).](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)

## <a name="implementing-the-expansionfunction-class"></a>Implementace třídy ExpansionFunction
 Rozšiřující funkce je pojmenovaná funkce, která je vložena do šablony úryvku a vrací jednu nebo více hodnot, které mají být umístěny do pole. Chcete-li podporovat rozšiřující funkce ve vaší jazykové službě, <xref:Microsoft.VisualStudio.Package.ExpansionFunction> musíte odvodit třídu z třídy a implementovat metodu. <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetCurrentValue%2A> Potom je nutné <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A> přepsat metodu ve <xref:Microsoft.VisualStudio.Package.LanguageService> třídě vrátit novou instanci <xref:Microsoft.VisualStudio.Package.ExpansionFunction> vaší verze třídy pro každou rozšiřující funkci, kterou podporujete. Pokud podporujete seznam možných hodnot z rozšiřující funkce, <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetIntellisenseList%2A> musíte také <xref:Microsoft.VisualStudio.Package.ExpansionFunction> přepsat metodu ve třídě, abyste vrátili seznam těchto hodnot.

 Rozšiřující funkce, která přebírá argumenty nebo potřebuje přístup k jiným polím, by neměla být přidružena k upravitelnému poli, protože zprostředkovatel rozšíření nemusí být plně inicializován v době, kdy je volána funkce rozšíření. V důsledku toho funkce rozšíření není schopen získat hodnotu jeho argumenty nebo jiné pole.

### <a name="example"></a>Příklad
 Zde je příklad, jak může `GetName` být implementována jednoduchá rozšiřující funkce volaná. Tato rozšiřující funkce připojí číslo k názvu základní třídy pokaždé, když je vytvořena instance funkce rozšíření (což odpovídá každému, kdy je vložen přidružený fragment kódu).

```csharp
using Microsoft.VisualStudio.Package;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        private int classNameCounter = 0;

        public override ExpansionFunction CreateExpansionFunction(
            ExpansionProvider provider,
            string functionName)
        {
            ExpansionFunction function = null;
            if (functionName == "GetName")
            {
                ++classNameCounter;
                function = new TestGetNameExpansionFunction(provider, classNameCounter);
            }
            return function;
        }
    }

    internal class TestGetNameExpansionFunction : ExpansionFunction
    {
        private int nameCount;

        TestGetNameExpansionFunction(ExpansionProvider provider, int counter)
            : base(provider)
        {
            nameCount = counter;
        }

        public override string GetCurrentValue()
        {
            string name = "TestClass";
            name += nameCount.ToString();
            return name;
        }
    }
}
```

## <a name="see-also"></a>Viz také
- [Funkce služby starší verze jazyka](../../extensibility/internals/legacy-language-service-features1.md)
- [Registrace služby starší verze jazyka](../../extensibility/internals/registering-a-legacy-language-service1.md)
- [Fragmenty kódu](../../ide/code-snippets.md)
- [Návod: Získání seznamu nainstalovaných fragmentů kódu (implementace starší verze)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)
