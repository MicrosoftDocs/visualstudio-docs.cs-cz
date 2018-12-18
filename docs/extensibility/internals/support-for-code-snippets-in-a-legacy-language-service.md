---
title: Podpora pro fragmenty kódu ve službě starší verze jazyka | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- snippets, supporting in language services
- code snippets, supporting in language services [managed package framework]
- language services [managed package framework], supporting code snippets
ms.assetid: 7490325b-acee-4c2d-ac56-1cd5db1a1083
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a7ad314e5a160ae280b33586fb7dfe1b42ec470f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49858105"
---
# <a name="support-for-code-snippets-in-a-legacy-language-service"></a>Podpora pro fragmenty kódu ve službě starší verze jazyka
Fragment kódu je část kódu, který je vložen do zdrojového souboru. Samotný fragment kódu je šablonu založený na formátu XML s sadu polí. Tato pole jsou zvýrazněny po vložení fragmentu kódu a může mít různé hodnoty v závislosti na kontextu, ve kterém se tento fragment vloží. Okamžitě po vložení fragmentu kódu můžete naformátovat služba jazyka fragmentu kódu.  
  
 Fragment kódu je vložen do režimu úpravy zvláštní pole fragment kódu pro navigaci pomocí klávesy TAB. Pole může podporovat stylu funkce IntelliSense rozevírací nabídky. Uživatel potvrdí fragmentu kódu ke zdrojovému souboru tak, že zadáte ENTER nebo ESC klíč. Další informace o fragmenty kódu, najdete v tématu [fragmenty kódu](../../ide/code-snippets.md).  
  
 Služby starší verze jazyka jsou implementovány jako součást sady VSPackage, ale novější způsob implementace funkce služba jazyka je pro použití rozšíření MEF. Další informace najdete v tématu [návod: implementace fragmentů kódu](../../extensibility/walkthrough-implementing-code-snippets.md).  
  
> [!NOTE]
>  Doporučujeme vám, že začnete používat nový editor API co nejdříve. Tím vylepšíme výkonu vaší služby jazyka a umožňují využívat nové funkce editoru.  
  
## <a name="managed-package-framework-support-for-code-snippets"></a>Managed Package Framework podpora pro fragmenty kódu  
 Rozhraní spravovaného balíčku (MPF) podporuje většinu funkcí fragment kódu ze šablony pro vložení fragmentu kódu pro čtení a povolení speciální režim úprav. Podpora je spravována prostřednictvím <xref:Microsoft.VisualStudio.Package.ExpansionProvider> třídy.  
  
 Při <xref:Microsoft.VisualStudio.Package.Source> je vytvořena instance třídy, <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A> metoda ve <xref:Microsoft.VisualStudio.Package.LanguageService> třídy je volána k získání <xref:Microsoft.VisualStudio.Package.ExpansionProvider> objektu (Všimněte si, že základní <xref:Microsoft.VisualStudio.Package.LanguageService> třídy vždy vrátí nový <xref:Microsoft.VisualStudio.Package.ExpansionProvider> objekt pro každou <xref:Microsoft.VisualStudio.Package.Source> objekt).  
  
 MPF nepodporuje rozšíření funkce. Rozšíření funkce je pojmenované funkce, která je součástí šablony fragmentu kódu a vrátí jednu nebo více hodnot, které se mají umístit na pole. Hodnoty jsou vráceny pomocí jazyka vlastní prostřednictvím služby <xref:Microsoft.VisualStudio.Package.ExpansionFunction> objektu. <xref:Microsoft.VisualStudio.Package.ExpansionFunction> Objekt musí implementovat služba jazyka pro podporu funkcí rozšíření.  
  
## <a name="providing-support-for-code-snippets"></a>Poskytuje podporu pro fragmenty kódu  
 Povolení podpory pro fragmenty kódu, je nutné zadat nebo nainstalovat fragmenty kódu a je nutné zadat znamená, že uživatel chce vložit tyto fragmenty kódu. Existují tři kroky pro povolení podpory pro fragmenty kódu:  
  
1.  Instalují se soubory fragmentu kódu.  
  
2.  Povolení fragmenty kódu pro vaši službu jazyka.  
  
3.  Volání <xref:Microsoft.VisualStudio.Package.ExpansionProvider> objektu.  
  
### <a name="installing-the-snippet-files"></a>Instalují se soubory fragmentu kódu  
 Všechny fragmenty kódu pro jazyk se ukládají jako šablony v souboru XML, obvykle jedna šablona fragmentu na soubor. Informace o schématu XML pro šablony fragmentu kódu, naleznete v tématu [fragmenty kódu – odkaz schématu](../../ide/code-snippets-schema-reference.md). Každá šablona fragmentu kódu se určuje podle ID jazyka. Tento jazyk ID je uvedený v registru a přejde do `Language` atribut \<kód > značky v šabloně.  
  
 Jsou obvykle dvou umístěních, kde jsou uložené soubory šablony fragmentu kódu: 1) Pokud byl nainstalován jazyk a (2) ve složce daného uživatele. Tato místa jsou přidány do registru tak, která sadě Visual Studio **Správce fragmentů kódů** můžete najít fragmenty kódu. Složky uživatele je, kde jsou uložené fragmenty vytvořených uživatelem.  
  
 Typické složku rozložení pro soubory šablon nainstalovaných fragment kódu vypadá takto: *[InstallRoot]*\\ *[TestLanguage]* \Snippets\\ *[LCID]* \Snippets.  
  
 *[InstallRoot]*  je složka, je nainstalovaný jazyk.  
  
 *[TestLanguage]*  je název jazyka, jako název složky.  
  
 *[LCID]*  je ID národního prostředí. Toto je lokalizovaných verzích vaše fragmenty jsou uložené. Identifikátor národního prostředí pro angličtina je například 1033, tak *[LCID]* nahrazuje 1033.  
  
 Je nutné zadat jeden další soubor a, který je indexový soubor, obvykle nazývá SnippetsIndex.xml nebo ExpansionsIndex.xml (můžete použít libovolný platný název souboru končí na .xml). Tento soubor je obvykle uložen ve *[InstallRoot]*\\ *[TestLanguage]* složce a určuje přesné umístění složky fragmentů kódu a také ID jazyka a identifikátor GUID jazyka Služba, která používá fragmenty kódu. Jak je popsáno dále v "Instalace položky registru" přesnou cestu k souboru indexu přejde do registru. Tady je příklad souboru SnippetsIndex.xml:  
  
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
  
 \<Jazyk > značky Určuje ID jazyka ( `Lang` atribut) a služba jazyka identifikátor GUID.  
  
 Tento příklad předpokládá, že vaše služba jazyka nainstalována v instalační složce Nástroje Visual Studio. LCID % se nahradí za ID uživatele aktuální národní prostředí. Více \<SnippetDir > značky lze přidat, jeden pro každý jiný adresář a národní prostředí. Kromě toho složky fragmentů kódu může obsahovat podsložky, z nichž každý je uvedena v souboru indexu s \<SnippetSubDir > značky, které jsou součástí \<SnippetDir > značky.  
  
 Uživatelé mohou také vytvářet své vlastní fragmenty kódu pro váš jazyk. Ty jsou obvykle uložena v složce nastavení uživatele, například *[TestDocs]* \Code fragmenty\\ *[TestLanguage]* \Test fragmenty kódu, kde *[TestDocs]* je umístění uživatele nastavení složky pro sadu Visual Studio.  
  
 Následující prvky substituce mohou být umístěny v uložených v cestě \<DirPath > značky v souboru indexu.  
  
|Prvek|Popis|  
|-------------|-----------------|  
|LCID %|ID národního prostředí.|  
|InstallRoot %|Kořenová složka instalace pro Visual Studio, například C:\Program Files\Microsoft Visual Studio 8.|  
|ProjDir %|Složka obsahující aktuální projekt.|  
|ProjItem %|Složka obsahující aktuální položky projektu.|  
|TestDocs %|Složky ve složce nastavení uživatele, například C:\Documents and nastavení\\ *[username]* Documents\Visual Studio\8.|  
  
### <a name="enabling-code-snippets-for-your-language-service"></a>Povolení fragmenty kódu pro vaši službu jazyka  
 Fragmenty kódu pro vaši službu jazyka můžete povolit přidáním <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> atribut vašeho balíčku VSPackage (naleznete v tématu [registrace služby starší verze jazyka](../../extensibility/internals/registering-a-legacy-language-service1.md) podrobnosti). <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.ShowRoots%2A> a <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.SearchPaths%2A> parametry jsou volitelné, ale měli byste zahrnout `SearchPaths` s názvem parametru, aby bylo možné informovat **Správce fragmentů kódů** umístění vašeho fragmenty kódu.  
  
 Následuje příklad, jak používat tento atribut:  
  
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
 Služba jazyka řídí vkládání jakékoli fragmenty kódu, jakož i způsob, jakým je vyvolán vložení.  
  
## <a name="calling-the-expansion-provider-for-code-snippets"></a>Volání zprostředkovatele rozšíření pro fragmenty kódu  
 Existují dva způsoby, jak vyvolat poskytovatele rozšíření: pomocí příkazu nabídky nebo pomocí zástupce v seznamu dokončení.  
  
### <a name="inserting-a-code-snippet-by-using-a-menu-command"></a>Vložení fragmentu kódu s použitím příkazu nabídky  
 Pomocí příkazu nabídky zobrazit v prohlížeči fragment, přidání příkazu nabídky a pak zavolat <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> metodu <xref:Microsoft.VisualStudio.Package.ExpansionProvider> rozhraní v reakci na příkaz nabídky.  
  
1.  Přidejte do souboru .vsct příkazu a tlačítko. Proto v postupu můžete najít [vytváření rozšíření pomocí příkazu nabídky](../../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Odvodit třídu z <xref:Microsoft.VisualStudio.Package.ViewFilter> třídy a přepsat <xref:Microsoft.VisualStudio.Package.ViewFilter.QueryCommandStatus%2A> indikace podporu pro nový příkaz nabídky. Tento příklad povolí vždy příkazu nabídky.  
  
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
  
3.  Přepsat <xref:Microsoft.VisualStudio.Package.ViewFilter.HandlePreExec%2A> metoda ve <xref:Microsoft.VisualStudio.Package.ViewFilter> třídy získat <xref:Microsoft.VisualStudio.Package.ExpansionProvider> objektu a volání <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> metoda k tomuto objektu.  
  
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
  
     Následující metody u <xref:Microsoft.VisualStudio.Package.ExpansionProvider> třídy jsou volány pomocí sady Visual Studio v uvedeném pořadí během procesu vložení fragmentu kódu:  
  
4.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnItemChosen%2A>  
  
5.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>  
  
6.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>  
  
7.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>  
  
8.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>  
  
     Po <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A> metoda je volána, fragment kódu byl vložen a <xref:Microsoft.VisualStudio.Package.ExpansionProvider> objekt je ve speciální úpravy režim používaný pro úpravu fragment kódu, který právě byl vložen.  
  
### <a name="inserting-a-code-snippet-by-using-a-shortcut"></a>Vložení fragmentu kódu pomocí zástupce  
 Implementace zástupce seznamu dokončení je mnohem složitější než implementace příkazu nabídky. Zkratky fragmentu kódu je nutné nejprve přidat do seznamu doplňování technologie IntelliSense aplikace word. Potom musí rozpoznat, kdy místní název fragmentu kódu byla vložena jako výsledek dokončení. Nakonec musíte získat název fragmentu kódu a cesty pomocí názvu odkazu a předejte tyto informace <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> metodu na <xref:Microsoft.VisualStudio.Package.ExpansionProvider> metody.  
  
 Chcete-li přidat zástupce fragment kódu pro seznam pro doplňování slov, přidejte je do <xref:Microsoft.VisualStudio.Package.Declarations> objektu ve vaší <xref:Microsoft.VisualStudio.Package.AuthoringScope> třídy. Musíte zkontrolovat, že identifikujete místní jako název fragmentu kódu. Příklad najdete v tématu [návod: získání seznam z nainstalované fragmenty kódu (implementace starší verze)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).  
  
 Vložení zástupce fragmentu kódu, můžete zjistit <xref:Microsoft.VisualStudio.Package.Declarations.OnAutoComplete%2A> metodu <xref:Microsoft.VisualStudio.Package.Declarations> třídy. Protože název fragmentu kódu již byl vložen do zdrojového souboru, musí být odebrána po vložení rozšíření. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> Metoda přijímá rozsahu, který popisuje bodu vložení fragmentu; rozpětí zahrnuje název celý fragment kódu ve zdrojovém souboru, tento název se nahradí fragmentem.  
  
 Tady je verze <xref:Microsoft.VisualStudio.Package.Declarations> třídu, která zpracovává místní název vložení fragmentu kódu. Jiné metody v <xref:Microsoft.VisualStudio.Package.Declarations> třídy byly vynechány nejasnostem. Všimněte si, že má konstruktor třídy této třídy <xref:Microsoft.VisualStudio.Package.LanguageService> objektu. To můžete předávat ve vaší verzi <xref:Microsoft.VisualStudio.Package.AuthoringScope> objektu (například vaši implementaci <xref:Microsoft.VisualStudio.Package.AuthoringScope> třída může trvat, než <xref:Microsoft.VisualStudio.Package.LanguageService> 've svém konstruktoru objektu a předejte tento objekt k vaší `TestDeclarations` konstruktoru třídy).  
  
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
  
 Služba jazyka získá jméno zástupce, zavolá <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FindExpansionByShortcut%2A> způsob získání názvu souboru a Kód fragmentu kódu nadpis. Pak zavolá služba jazyka <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> metoda ve <xref:Microsoft.VisualStudio.Package.ExpansionProvider> třídu pro vložení fragmentu kódu. Následující metody jsou volány pomocí sady Visual Studio v daném pořadí <xref:Microsoft.VisualStudio.Package.ExpansionProvider> třída během procesu vložení fragmentu kódu:  
  
1. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>  
  
2. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>  
  
3. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>  
  
4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>  
  
   Další informace o získání seznamu nainstalovaných fragmentů kódu pro vaši službu jazyka najdete v tématu [návod: získání seznam z nainstalované fragmenty kódu (implementace starší verze)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).  
  
## <a name="implementing-the-expansionfunction-class"></a>Implementující třída ExpansionFunction  
 Rozšíření funkce je pojmenované funkce, která je součástí šablony fragmentu kódu a vrátí jednu nebo více hodnot, které se mají umístit na pole. Za účelem podpory funkcí rozšíření ve vaší službě jazyka, musí být odvozen ze třídy <xref:Microsoft.VisualStudio.Package.ExpansionFunction> třídy a implementovat <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetCurrentValue%2A> metody. Pak je nutné přepsat <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A> metoda ve <xref:Microsoft.VisualStudio.Package.LanguageService> třídy k vrácení nové instance vaší verzi <xref:Microsoft.VisualStudio.Package.ExpansionFunction> třídy pro každou funkci rozšíření, které podporujete. Pokud podporujete seznam možných hodnot z funkce rozšíření, musí také přepsat <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetIntellisenseList%2A> metodu <xref:Microsoft.VisualStudio.Package.ExpansionFunction> třídy se seznam těchto hodnot.  
  
 Rozšíření funkce, která přebírá argumenty nebo potřebuje přístup k jiné pole by neměl být přidružen upravitelné pole, podle poskytovatele rozšíření nemusí být plně inicializován v době, kdy je volána funkce rozšíření. V důsledku toho funkce rozšíření není schopen získat hodnotu jeho argumenty nebo jakékoli jiné pole.  
  
### <a name="example"></a>Příklad  
 Tady je příklad, jak jednoduché rozšíření funkci s názvem `GetName` může být implementována. Tato funkce rozšíření přidá číslo a název základní třídy pokaždé, když je vytvořena instance funkce rozšíření (který odpovídá pokaždé, když fragment přidružený kód je vložen).  
  
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
 [Funkce služby starší verze jazyka](../../extensibility/internals/legacy-language-service-features1.md)   
 [Registrace služby starší verze jazyka](../../extensibility/internals/registering-a-legacy-language-service1.md)   
 [Fragmenty kódu](../../ide/code-snippets.md)   
 [Návod: Získání seznamu nainstalovaných fragmentů kódu (implementace starší verze)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)