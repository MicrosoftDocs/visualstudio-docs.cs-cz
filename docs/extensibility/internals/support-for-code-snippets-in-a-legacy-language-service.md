---
title: Podpora fragmentů kódu ve službě starší verze jazyka | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- snippets, supporting in language services
- code snippets, supporting in language services [managed package framework]
- language services [managed package framework], supporting code snippets
ms.assetid: 7490325b-acee-4c2d-ac56-1cd5db1a1083
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d771db166baa66426c7a6d03b344c4bc7b74b27
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723111"
---
# <a name="support-for-code-snippets-in-a-legacy-language-service"></a>Podpora pro fragmenty kódu ve službě starší verze jazyka
Fragment kódu je část kódu, která je vložena do zdrojového souboru. Samotný fragment kódu je šablona založená na jazyce XML se sadou polí. Tato pole jsou zvýrazněna po vložení fragmentu kódu a mohou mít různé hodnoty v závislosti na kontextu, ve kterém je vložený fragment. Ihned po vložení fragmentu kódu může služba jazyka tento fragment kódu naformátovat.

 Fragment kódu je vložen ve speciálním režimu úprav, který umožňuje navigaci polí fragmentu pomocí klávesy TAB. Pole mohou podporovat rozevírací nabídky ve stylu technologie IntelliSense. Uživatel potvrdí fragment do zdrojového souboru zadáním klávesy ENTER nebo ESC. Chcete-li získat další informace o fragmentech kódu, přečtěte si [fragmenty kódu](../../ide/code-snippets.md).

 Starší jazykové služby jsou implementovány jako součást sady VSPackage, ale novější způsob, jak implementovat funkce jazykové služby, je použít rozšíření MEF. Další informace naleznete v tématu [Návod: implementace fragmentů kódu](../../extensibility/walkthrough-implementing-code-snippets.md).

> [!NOTE]
> Doporučujeme začít používat nové rozhraní API editoru co nejrychleji. Tím se vylepšit výkon vaší jazykové služby a umožní vám využít nové funkce editoru.

## <a name="managed-package-framework-support-for-code-snippets"></a>Podpora rozhraní Managed Package Framework pro fragmenty kódu
 Rozhraní Managed Package Framework (MPF) podporuje většinu funkcí fragmentů kódu, od čtení šablony po vložení fragmentu kódu a povolení speciálního režimu úprav. Podpora je spravována prostřednictvím třídy <xref:Microsoft.VisualStudio.Package.ExpansionProvider>.

 Při vytvoření instance <xref:Microsoft.VisualStudio.Package.Source> třídy je volána metoda <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A> ve třídě <xref:Microsoft.VisualStudio.Package.LanguageService> pro získání objektu <xref:Microsoft.VisualStudio.Package.ExpansionProvider> (Všimněte si, že základní <xref:Microsoft.VisualStudio.Package.LanguageService> Třída vždy vrátí nový objekt <xref:Microsoft.VisualStudio.Package.ExpansionProvider> pro každý objekt <xref:Microsoft.VisualStudio.Package.Source>).

 MPF nepodporuje funkce rozšíření. Funkce rozšíření je pojmenovaná funkce, která je vložena do šablony fragmentu a vrací jednu nebo více hodnot, které mají být umístěny do pole. Hodnoty jsou vráceny prostřednictvím služby jazyka samotné prostřednictvím objektu <xref:Microsoft.VisualStudio.Package.ExpansionFunction>. Objekt <xref:Microsoft.VisualStudio.Package.ExpansionFunction> musí být implementován službou jazyka pro podporu funkcí rozšíření.

## <a name="providing-support-for-code-snippets"></a>Poskytnutí podpory pro fragmenty kódu
 Chcete-li povolit podporu fragmentů kódu, je nutné zadat nebo nainstalovat fragmenty a je nutné zadat způsob, jakým uživatel bude vkládat tyto fragmenty. Existují tři kroky pro povolení podpory fragmentů kódu:

1. Instalace souborů fragmentů.

2. Povolují se fragmenty kódu pro vaši jazykovou službu.

3. Vyvolává se objekt <xref:Microsoft.VisualStudio.Package.ExpansionProvider>.

### <a name="installing-the-snippet-files"></a>Instalace souborů fragmentů
 Všechny fragmenty kódu pro jazyk jsou uloženy jako šablony v souborech XML, obvykle v jedné šabloně fragmentu na soubor. Podrobnosti o schématu XML používaném pro šablony fragmentů kódu naleznete v tématu [reference ke schématu fragmentů kódu](../../ide/code-snippets-schema-reference.md). Každá šablona fragmentů kódu je identifikována s ID jazyka. Toto ID jazyka je zadáno v registru a je vloženo do atributu `Language` \<Code značka > v šabloně.

 K dispozici jsou obvykle dvě umístění, kde jsou uloženy soubory šablon fragmentu: 1), kde byl váš jazyk nainstalován a 2) do složky uživatele. Tato umístění jsou přidána do registru tak, aby **Správce fragmentů kódu** Visual Studio mohl tyto fragmenty najít. Ve složce uživatele jsou uloženy fragmenty kódu vytvořené uživatelem.

 Typické rozložení složek pro nainstalované soubory šablon fragmentů kódu vypadá takto: *[InstallRoot]* \\ *[TestLanguage]* \Snippets \\ *[LCID]* \Snippets.

 *[InstallRoot]* je složka, ve které je váš jazyk nainstalován.

 *[TestLanguage]* je název vašeho jazyka jako název složky.

 *[LCID]* je ID národního prostředí. Toto je způsob, jakým jsou uloženy lokalizované verze fragmentů. Například ID národního prostředí pro angličtinu je 1033, takže *[LCID]* je nahrazeno 1033.

 Je nutné zadat jeden další soubor, který je indexový soubor, obvykle označovaný jako SnippetsIndex. XML nebo ExpansionsIndex. XML (můžete použít libovolný platný název souboru končící na. XML). Tento soubor je obvykle uložen ve složce *[InstallRoot]* \\ *[TestLanguage]* a určuje přesné umístění složky fragmenty a také ID jazyka a identifikátor GUID jazykové služby, která používá fragmenty. Přesná cesta k souboru indexu je uvedena v registru, jak je popsáno dále v části "instalace položek registru". Zde je příklad souboru SnippetsIndex. XML:

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

 Značka \<Language > Určuje ID jazyka (atribut `Lang`) a identifikátor GUID jazykové služby.

 V tomto příkladu se předpokládá, že jste nainstalovali službu Language Service v instalační složce sady Visual Studio. Identifikátor% LCID% je nahrazen aktuálním ID národního prostředí uživatele. Lze přidat více značek \<SnippetDir >, jeden pro každý jiný adresář a národní prostředí. Kromě toho složka fragmentů může obsahovat podsložky, z nichž každá je identifikována v souboru indexu pomocí značky \<SnippetSubDir >, která je vložena do značky > \<SnippetDir.

 Uživatelé také mohou vytvořit vlastní fragmenty kódu pro váš jazyk. Ty jsou obvykle uloženy ve složce nastavení uživatele, například *[TestDocs]* \Code fragmenty kódu \\ *[TestLanguage]* \test fragmenty kódu, kde *[TestDocs]* je umístění složky nastavení uživatele pro sadu Visual Studio.

 Následující substituční prvky lze umístit do cesty uložené v \<DirPath značka > v souboru indexu.

|Prvek|Popis|
|-------------|-----------------|
|IDENTIFIKÁTORY|ID národního prostředí|
|InstallRoot|Kořenová instalační složka pro Visual Studio, například C:\Program Files\Microsoft Visual Studio 8.|
|%ProjDir%|Složka obsahující aktuální projekt.|
|%ProjItem%|Složka obsahující aktuální položku projektu|
|%TestDocs%|Složka ve složce nastavení uživatele, například C:\Documents and Settings \\ *[UserName]* \My Documents\Visual Studio\8.|

### <a name="enabling-code-snippets-for-your-language-service"></a>Povolení fragmentů kódu pro službu jazyka
 Fragmenty kódu pro službu jazyka můžete povolit přidáním atributu <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> do balíčku VSPackage (podrobnosti najdete v tématu [Registrace služby starší verze jazyka](../../extensibility/internals/registering-a-legacy-language-service1.md) ). Parametry <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.ShowRoots%2A> a <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.SearchPaths%2A> jsou volitelné, ale měli byste zahrnout `SearchPaths` pojmenovaný parametr, aby bylo možné informovat **Správce fragmentů kódu** pro umístění vašich fragmentů.

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

### <a name="calling-the-expansion-provider"></a>Volání poskytovatele rozšíření
 Služba jazyka řídí vložení jakéhokoli fragmentu kódu a také způsob, jakým je vyvoláno vkládání.

## <a name="calling-the-expansion-provider-for-code-snippets"></a>Volání poskytovatele rozšíření pro fragmenty kódu
 Existují dva způsoby, jak vyvolat poskytovatele rozšíření: pomocí příkazu nabídky nebo pomocí zástupce ze seznamu pro doplňování.

### <a name="inserting-a-code-snippet-by-using-a-menu-command"></a>Vložení fragmentu kódu pomocí příkazu nabídky
 Chcete-li použít příkaz nabídky k zobrazení prohlížeče fragmentů kódu, přidejte příkaz nabídky a poté zavolejte metodu <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> v rozhraní <xref:Microsoft.VisualStudio.Package.ExpansionProvider> v reakci na příkaz nabídky.

1. Přidejte příkaz a tlačítko do souboru. vsct. Pokyny k tomu, jak to udělat, najdete v [tématu Vytvoření rozšíření pomocí příkazu nabídky](../../extensibility/creating-an-extension-with-a-menu-command.md).

2. Odvodit třídu z třídy <xref:Microsoft.VisualStudio.Package.ViewFilter> a přepsat metodu <xref:Microsoft.VisualStudio.Package.ViewFilter.QueryCommandStatus%2A>, aby označovala podporu pro nový příkaz nabídky. Tento příklad vždy povoluje příkaz nabídky.

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

3. Přepište metodu <xref:Microsoft.VisualStudio.Package.ViewFilter.HandlePreExec%2A> ve třídě <xref:Microsoft.VisualStudio.Package.ViewFilter> pro získání objektu <xref:Microsoft.VisualStudio.Package.ExpansionProvider> a volání metody <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> pro daný objekt.

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

     Následující metody ve třídě <xref:Microsoft.VisualStudio.Package.ExpansionProvider> jsou volány v aplikaci Visual Studio v daném pořadí během procesu vložení fragmentu kódu:

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnItemChosen%2A>

5. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

6. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

7. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

8. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

     Po zavolání metody <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A> se fragment kódu vloží a objekt <xref:Microsoft.VisualStudio.Package.ExpansionProvider> je ve speciálním režimu úprav, který se používá pro úpravu fragmentu, který byl právě vložen.

### <a name="inserting-a-code-snippet-by-using-a-shortcut"></a>Vložení fragmentu kódu pomocí zástupce
 Implementace zástupce ze seznamu pro doplňování je mnohem větší než implementace příkazu nabídky. Nejdříve je nutné přidat zástupce fragmentů do seznamu dokončování slov technologie IntelliSense. Pak je nutné zjistit, kdy byl název zástupce fragmentu kódu vložen jako výsledek dokončení. Nakonec musíte získat název fragmentu a cestu pomocí názvu zástupce a předat tyto informace metodě <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> v metodě <xref:Microsoft.VisualStudio.Package.ExpansionProvider>.

 Chcete-li přidat zástupce fragmentů do seznamu dokončování slov, přidejte je do objektu <xref:Microsoft.VisualStudio.Package.Declarations> ve vaší třídě <xref:Microsoft.VisualStudio.Package.AuthoringScope>. Je nutné se ujistit, že zástupce můžete identifikovat jako název fragmentu. Příklad naleznete v tématu [Návod: získání seznamu nainstalovaných fragmentů kódu (starší implementace)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).

 Vložení zástupce fragmentu kódu můžete zjistit v metodě <xref:Microsoft.VisualStudio.Package.Declarations.OnAutoComplete%2A> <xref:Microsoft.VisualStudio.Package.Declarations> třídy. Vzhledem k tomu, že byl název fragmentu již vložen do zdrojového souboru, je nutné jej odebrat, když je rozšíření vloženo. Metoda <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> přebírá rozsah, který popisuje bod vložení pro fragment kódu; Pokud rozpětí zahrnuje celý název fragmentu ve zdrojovém souboru, bude tento název nahrazen fragmentem.

 Zde je verze <xref:Microsoft.VisualStudio.Package.Declarations> třídy, která zpracovává vložení fragmentu názvu zástupce. Jiné metody ve třídě <xref:Microsoft.VisualStudio.Package.Declarations> byly vynechány pro přehlednost. Všimněte si, že konstruktor této třídy přebírá objekt <xref:Microsoft.VisualStudio.Package.LanguageService>. To může být předáno z vaší verze objektu <xref:Microsoft.VisualStudio.Package.AuthoringScope> (například vaše implementace <xref:Microsoft.VisualStudio.Package.AuthoringScope> třídy může převzít objekt <xref:Microsoft.VisualStudio.Package.LanguageService> ve svém konstruktoru a předat tento objekt konstruktoru třídy `TestDeclarations`).

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

 Když služba jazyka Získá název zástupce, zavolá metodu <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FindExpansionByShortcut%2A>, aby získala název souboru a název fragmentu kódu. Služba jazyka potom zavolá metodu <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> ve třídě <xref:Microsoft.VisualStudio.Package.ExpansionProvider> pro vložení fragmentu kódu. Následující metody jsou volány v aplikaci Visual Studio v daném pořadí ve třídě <xref:Microsoft.VisualStudio.Package.ExpansionProvider> během procesu vložení fragmentu kódu:

1. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

2. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

3. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

   Další informace o získání seznamu nainstalovaných fragmentů kódu pro službu jazyka najdete v tématu [Návod: získání seznamu nainstalovaných fragmentů kódu (starší implementace)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).

## <a name="implementing-the-expansionfunction-class"></a>Implementace třídy ExpansionFunction
 Funkce rozšíření je pojmenovaná funkce, která je vložena do šablony fragmentu a vrací jednu nebo více hodnot, které mají být umístěny do pole. Aby bylo možné podporovat rozšiřující funkce ve vaší jazykové službě, je nutné odvodit třídu z třídy <xref:Microsoft.VisualStudio.Package.ExpansionFunction> a implementovat metodu <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetCurrentValue%2A>. Pak je nutné přepsat metodu <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A> ve třídě <xref:Microsoft.VisualStudio.Package.LanguageService> a vrátit novou instanci vaší verze třídy <xref:Microsoft.VisualStudio.Package.ExpansionFunction> pro každou rozšiřující funkci, kterou podporujete. Pokud podporujete seznam možných hodnot z rozšiřující funkce, musíte také přepsat metodu <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetIntellisenseList%2A> ve třídě <xref:Microsoft.VisualStudio.Package.ExpansionFunction> a vrátit tak seznam těchto hodnot.

 Funkce rozšíření, která přebírá argumenty nebo musí mít přístup k jiným polím, by neměla být přidružena k upravitelnému poli, protože poskytovatel rozšíření nemusí být plně inicializován při volání funkce rozšíření. V důsledku toho funkce rozšíření nemůže získat hodnotu svých argumentů nebo žádného jiného pole.

### <a name="example"></a>Příklad
 Tady je příklad, jak může být implementována jednoduchá rozšiřující funkce nazvaná `GetName`. Tato rozšiřující funkce připojí číslo k názvu základní třídy pokaždé, když je vytvořena instance funkce rozšíření (která odpovídá pokaždé, když je vložen přidružený fragment kódu).

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

## <a name="see-also"></a>Viz také:
- [Funkce služby starší verze jazyka](../../extensibility/internals/legacy-language-service-features1.md)
- [Registrace služby starší verze jazyka](../../extensibility/internals/registering-a-legacy-language-service1.md)
- [Fragmenty kódu](../../ide/code-snippets.md)
- [Návod: Získání seznamu nainstalovaných fragmentů kódu (implementace starší verze)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)