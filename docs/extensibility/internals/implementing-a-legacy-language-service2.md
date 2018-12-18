---
title: Implementace starší verze jazyka2 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], implementing
ms.assetid: 5bcafdc5-f922-48f6-a12e-6c8507a79a05
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dccbac140aefb952eed97006cbcae6a61f94ac92
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49855414"
---
# <a name="implementing-a-legacy-language-service"></a>Implementace služby starší verze jazyka
Pro implementaci jazyka služby pomocí rozhraní spravovaného balíčku (MPF), musí být odvozen ze třídy <xref:Microsoft.VisualStudio.Package.LanguageService> třídy a implementovat následující abstraktní metody a vlastnosti:  
  
- <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> – Metoda  
  
- <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> – Metoda  
  
- <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> – Metoda  
  
- <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> Vlastnost  
  
  Najdete v příslušné části níže podrobnosti o implementaci těchto metod a vlastností.  
  
  Aby podporoval další funkce, vaše služba jazyka pravděpodobně nutné odvodit třídu z jedné ze tříd služby jazyka MPF; například musí podporovat další příkazy, odvoďte třídu z <xref:Microsoft.VisualStudio.Package.ViewFilter> třídy a přepsat několik metod zpracování příkazu (viz <xref:Microsoft.VisualStudio.Package.ViewFilter> podrobnosti). <xref:Microsoft.VisualStudio.Package.LanguageService> Třída poskytuje několik metod, které jsou volány k vytvoření nové instance různé třídy a přepsat metodu odpovídající vytvoření k dispozici instance třídy. Například je nutné přepsat <xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A> metoda ve <xref:Microsoft.VisualStudio.Package.LanguageService> třídy vrátit instanci vlastní <xref:Microsoft.VisualStudio.Package.ViewFilter> třídy. Další podrobnosti v části "Vytvoření instance třídy vlastní".  
  
  Vaše služba jazyka lze také zadat vlastní ikony, které se používají na mnoha místech. Když se zobrazí seznamu doplňování technologie IntelliSense, každou položku v seznamu může mít ikonu přidruženo, označí položku jako metody, třídy, oboru názvů, vlastností, nebo cokoli, co je nezbytné pro váš jazyk. Tyto ikony se používají ve všech seznamech technologie IntelliSense, **navigační panel**a v **seznam chyb** okno úkolu. V části "Služba jazyka bitové kopie" níže podrobnosti.  
  
## <a name="getlanguagepreferences-method"></a>GetLanguagePreferences – metoda  
 <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> Metoda vždy vrátí stejnou instanci <xref:Microsoft.VisualStudio.Package.LanguagePreferences> třídy. Můžete použít základní <xref:Microsoft.VisualStudio.Package.LanguagePreferences> třídy, pokud není nutné žádné další předvolby pro vaši službu jazyka. Třídy služeb jazyka MPF předpokládá existenci alespoň základní <xref:Microsoft.VisualStudio.Package.LanguagePreferences> třídy.  
  
### <a name="example"></a>Příklad  
 Tento příklad ukazuje obvyklá implementace metody <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> metody. Tento příklad používá základní <xref:Microsoft.VisualStudio.Package.LanguagePreferences> třídy.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        private LanguagePreferences m_preferences;  
  
        public override LanguagePreferences GetLanguagePreferences()  
        {  
            if (m_preferences == null)  
            {  
                m_preferences = new LanguagePreferences(this.Site,  
                                                        typeof(TestLanguageService).GUID,  
                                                        this.Name );  
                m_preferences.Init();  
            }  
            return m_preferences;  
        }  
    }  
}  
```  
  
## <a name="getscanner-method"></a>GetScanner – metoda  
 Tato metoda vrátí instanci <xref:Microsoft.VisualStudio.Package.IScanner> objekt, který implementuje řádkový analyzátoru nebo skeneru použitého pro získávání tokenů a jejich typy a aktivačních událostí. Je používán tento skener <xref:Microsoft.VisualStudio.Package.Colorizer> třídy pro barevné zvýraznění, i když skenerem lze také pro získání typy tokenů a aktivačních událostí jako prelude pro složitější operace analýzy. Je nutné zadat třídu, která implementuje <xref:Microsoft.VisualStudio.Package.IScanner> a interface musí implementovat všechny metody na <xref:Microsoft.VisualStudio.Package.IScanner> rozhraní.  
  
### <a name="example"></a>Příklad  
 Tento příklad ukazuje obvyklá implementace metody <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> metody. `TestScanner` Implementuje třída <xref:Microsoft.VisualStudio.Package.IScanner> rozhraní (nezobrazení).  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        private TestScanner m_scanner;  
  
        public override IScanner GetScanner(IVsTextLines buffer)  
        {  
            if (m_scanner == null)  
            {  
                m_scanner = new TestScanner(buffer);  
            }  
            return m_scanner;  
        }  
    }  
}  
    internal class TestScanner : IScanner  
    {  
        private IVsTextBuffer m_buffer;  
        string m_source;  
  
        public TestScanner(IVsTextBuffer buffer)  
        {  
            m_buffer = buffer;  
        }  
  
        bool IScanner.ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo, ref int state)  
        {  
            tokenInfo.Type = TokenType.Unknown;  
            tokenInfo.Color = TokenColor.Text;  
            return true;  
        }  
  
        void IScanner.SetSource(string source, int offset)  
        {  
            m_source = source.Substring(offset);  
        }  
    }  
  
```  
  
## <a name="parsesource-method"></a>ParseSource – metoda  
 Analyzuje zdrojový soubor založený na několika různých důvodů, proč. Tato metoda je uvedena <xref:Microsoft.VisualStudio.Package.ParseRequest> objekt, který popisuje, co se očekává z konkrétní operace analýzy. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Metoda vyvolá složitější analyzátor, který určuje token funkce a oboru. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Metoda se používá v podpoře pro operace IntelliSense, jakož i párování složených závorek. I v případě, že tyto pokročilé operace nepodporují, můžete stále musí vrátit platný <xref:Microsoft.VisualStudio.Package.AuthoringScope> objekt a že je potřeba vytvořit třídu, která implementuje <xref:Microsoft.VisualStudio.Package.AuthoringScope> rozhraní a implementovat všechny metody tohoto rozhraní. Můžete vracet hodnoty null ze všech metod ale <xref:Microsoft.VisualStudio.Package.AuthoringScope> samotného objektu nesmí mít hodnotu null.  
  
### <a name="example"></a>Příklad  
 Tento příklad ukazuje minimální provádění <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metoda a <xref:Microsoft.VisualStudio.Package.AuthoringScope> třídu dostatečná povolení služba jazyka ke kompilaci a funkce bez skutečně podporuje některé pokročilejší funkce.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        public override AuthoringScope ParseSource(ParseRequest req)  
        {  
            return new TestAuthoringScope();  
        }  
    }  
  
    internal class TestAuthoringScope : AuthoringScope  
    {  
        public override string GetDataTipText(int line, int col, out TextSpan span)  
        {  
            span = new TextSpan();  
            return null;  
        }  
  
        public override Declarations GetDeclarations(IVsTextView view,  
                                                     int line,  
                                                     int col,  
                                                     TokenInfo info,  
                                                     ParseReason reason)  
        {  
            return null;  
        }  
  
        public override string Goto(VSConstants.VSStd97CmdID cmd, IVsTextView textView, int line, int col, out TextSpan span)  
        {  
            span = new TextSpan();  
            return null;  
        }  
  
        public override Methods GetMethods(int line, int col, string name)  
        {  
            return null;  
        }  
}  
```  
  
## <a name="name-property"></a>Název vlastnosti  
 Tato vlastnost vrátí název služby jazyka. Musí se jednat o stejný název zadaný při služba jazyka byl zaregistrován. Tento název se používá v řadě míst, z nichž nejvýraznější je <xref:Microsoft.VisualStudio.Package.LanguagePreferences> třídy, kde název se používá pro přístup k registru. Tato vlastnost vrátí název nesmí být lokalizována, protože se používá v registru pro položku registru a názvy klíčů.  
  
### <a name="example"></a>Příklad  
 Tento příklad ukazuje jednu možnou implementaci <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> vlastnost. Všimněte si, že zadaný název je pevně zakódované: skutečný název by měl získat ze souboru prostředků, takže ho můžete použít při registraci služba jazyka (viz [registrace služby starší verze jazyka](../../extensibility/internals/registering-a-legacy-language-service1.md)).  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        public override string Name  
        {  
            get { return "Test Language"; }  
        }  
    }  
}  
```  
  
## <a name="instantiating-custom-classes"></a>Vytvoření vlastní třídy  
 Následující metody u zadané třídy může být potlačena za účelem poskytují instance vlastní verze každé třídy.  
  
### <a name="in-the-languageservice-class"></a>Ve třídě LanguageService  
  
|Metoda|Třída vrácena|Popis|  
|------------|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateCodeWindowManager%2A>|<xref:Microsoft.VisualStudio.Package.CodeWindowManager>|Podpora vlastních dodatky k zobrazení textu.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>|<xref:Microsoft.VisualStudio.Package.DocumentProperties>|Podpora vlastní vlastnosti dokumentu.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>|<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>|Pro podporu **navigační panel**.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionFunction>|Pro podporu funkcí v šablony fragmentu kódu.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionProvider>|Podpora fragmentů kódu (tuto metodu není obvykle přepsat).|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A>|<xref:Microsoft.VisualStudio.Package.ParseRequest>|Pro podporu přizpůsobení <xref:Microsoft.VisualStudio.Package.ParseRequest> struktury (tuto metodu není obvykle přepsat).|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A>|<xref:Microsoft.VisualStudio.Package.Source>|Pro podporu formátování zdrojový kód, zadáním znaky komentáře a přizpůsobení podpisy metod.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>|<xref:Microsoft.VisualStudio.Package.ViewFilter>|Pro podporu dalších příkazů.|  
|<xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A>|<xref:Microsoft.VisualStudio.Package.Colorizer>|Pro podporu, zvýrazňování syntaxe (tuto metodu není obvykle přepsat).|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>|<xref:Microsoft.VisualStudio.Package.LanguagePreferences>|Pro podporu přístupu k jazykové předvolby. Tato metoda musí být implementované ale možné vrátit instanci třídy base.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>|<xref:Microsoft.VisualStudio.Package.IScanner>|K zajištění analyzátor používá k identifikaci typy tokenů na řádek. Tato metoda musí být implementována a <xref:Microsoft.VisualStudio.Package.IScanner> musí být odvozen od.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringScope>|K zajištění analyzátor používá k identifikaci funkce a oboru v celém celému zdrojovému souboru. Tato metoda je potřeba implementovat a musí vracet instanci vaší verzi <xref:Microsoft.VisualStudio.Package.AuthoringScope> třídy. Pokud všechny, které chcete podporovat je zvýraznění syntaxe (což vyžaduje <xref:Microsoft.VisualStudio.Package.IScanner> analyzátor vrátil z <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> metoda), můžete neprovedete žádnou akci v této metodě než vrácení verze <xref:Microsoft.VisualStudio.Package.AuthoringScope> třídy, jejíž všechny metody vracet hodnoty null.|  
  
### <a name="in-the-source-class"></a>Ve třídě zdroje  
  
|Metoda|Třída vrácena|Popis|  
|------------|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>|<xref:Microsoft.VisualStudio.Package.CompletionSet>|Pro přizpůsobení zobrazení seznamů doplňování technologie IntelliSense (tuto metodu není obvykle přepsat).|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>|<xref:Microsoft.VisualStudio.Package.DocumentTask>|Podpora značek v seznamu úkolů seznam chyb Konkrétně podpora pro funkce nad rámec otevření souboru a přechod na řádek, který způsobil chybu.|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateMethodData%2A>|<xref:Microsoft.VisualStudio.Package.MethodData>|Přizpůsobení zobrazení popisy parametrů informace technologie IntelliSense.|  
|<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>|<xref:Microsoft.VisualStudio.Package.CommentInfo>|Pro podporu kód komentářů.|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateAuthoringSink%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringSink>|Pro shromažďování informací během operace analýzy.|  
  
### <a name="in-the-authoringscope-class"></a>Ve třídě AuthoringScope  
  
|Metoda|Třída vrácena|Popis|  
|------------|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>|<xref:Microsoft.VisualStudio.Package.Declarations>|Obsahuje seznam deklarace, jako například členy a typy. Tato metoda musí být implementována, ale může vrátit hodnotu null. Pokud tato metoda vrátí platný objekt, objekt musí být instance vaší verzi <xref:Microsoft.VisualStudio.Package.Declarations> třídy.|  
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A>|<xref:Microsoft.VisualStudio.Package.Methods>|Obsahuje seznam podpisy metod pro daný kontext. Tato metoda musí být implementována, ale může vrátit hodnotu null. Pokud tato metoda vrátí platný objekt, objekt musí být instance vaší verzi <xref:Microsoft.VisualStudio.Package.Methods> třídy.|  
  
## <a name="language-service-images"></a>Jazykové služby Image  
 Zajištění seznamu ikon, který se má použít v celé službě jazyka přepsat <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> metoda ve <xref:Microsoft.VisualStudio.Package.LanguageService> třídy a vrátit <xref:System.Windows.Forms.ImageList> obsahující ikony. Základní <xref:Microsoft.VisualStudio.Package.LanguageService> třídy načte výchozí sadu ikon. Vzhledem k tomu, že zadáte index přesné bitové kopie na těchto místech, které je třeba ikony, uspořádání seznamu obrázků je zcela na vás.  
  
### <a name="images-used-in-intellisense-completion-lists"></a>Obrázky používané v seznamech doplňování technologie IntelliSense  
 Pro seznamy doplňování technologie IntelliSense, je pro každou položku v zadané index bitové kopie <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> metodu <xref:Microsoft.VisualStudio.Package.Declarations> třídu, která je nutné přepsat, pokud chcete zadat index bitové kopie. Hodnota vrácená z <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> metoda je index do seznamu obrázků předány <xref:Microsoft.VisualStudio.Package.CompletionSet> konstruktoru třídy, který je stejný seznam obrázků vrácená z <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> metoda ve <xref:Microsoft.VisualStudio.Package.LanguageService> třídy (můžete změnit které seznamu obrázků použijte pro <xref:Microsoft.VisualStudio.Package.CompletionSet> Pokud přepíšete <xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A> metoda ve <xref:Microsoft.VisualStudio.Package.Source> třídy zadat jinou image seznamu).  
  
### <a name="images-used-in-the-navigation-bar"></a>Image použité v navigačním panelu  
 **Navigační panel** zobrazí seznam typů a členů a slouží pro rychlou navigaci můžete zobrazit ikony. Tyto ikony jsou získávány z <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> metodu <xref:Microsoft.VisualStudio.Package.LanguageService> třídy a nedají se přepsat speciálně pro **navigační panel**. Indexy použité pro každou položku v polích se seznamem se určí při jsou vyplněna seznamy představující polích se seznamem <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metoda ve <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> třídy (naleznete v tématu [podpora navigačního panelu ve službě starší verze jazyka](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)). Tyto image indexy jsou nějakým způsobem získaných analyzátor, obvykle prostřednictvím vaší verzi <xref:Microsoft.VisualStudio.Package.Declarations> třídy. Jak získat indexy je zcela na vás.  
  
### <a name="images-used-in-the-error-list-task-window"></a>Obrázky používané v okně chyb seznamu úkolů  
 Pokaždé, když <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> analyzátor – metoda (naleznete v tématu [starší verze jazyka analyzátor a skener služby](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)) dojde k chybě a předá tuto chybu do <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> metoda ve <xref:Microsoft.VisualStudio.Package.AuthoringSink> třídy, chybě v  **Seznam chyb** okno úkolu. Ikona můžou být spojené s každou položku, která se zobrazí v okně úlohy a této ikony pochází ze stejného seznamu obrázků vrácených <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> metoda ve <xref:Microsoft.VisualStudio.Package.LanguageService> třídy. Výchozí chování třídy MPF je nezobrazovat image s chybovou zprávou. Toto chování však můžete přepsat odvozením třídy od <xref:Microsoft.VisualStudio.Package.Source> třídy a přepsáním <xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A> metody. V této metodě, vytvořte nový <xref:Microsoft.VisualStudio.Package.DocumentTask> objektu. Před vrácením tohoto objektu, můžete použít <xref:Microsoft.VisualStudio.Shell.Task.ImageIndex%2A> vlastnost <xref:Microsoft.VisualStudio.Package.DocumentTask> objektu, který chcete nastavit index bitové kopie. To by vypadat přibližně jako v následujícím příkladu. Všimněte si, že `TestIconImageIndex` je výčet, který obsahuje seznam všech ikon a je specifická pro tento příklad. Může mít jiný způsob identifikace ikony ve vaší službě jazyka.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.Shell;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    class TestSource : Source  
    {  
        public override DocumentTask CreateErrorTaskItem(  
            TextSpan          span,  
            string            filename,  
            string            message,  
            TaskPriority      priority,  
            TaskCategory      category,  
            MARKERTYPE        markerType,  
            TaskErrorCategory errorCategory)  
        {  
            DocumentTask taskItem = base.CreateErrorTaskItem(  
                                           span,  
                                           filename,  
                                           message,  
                                           priority,  
                                           category,  
                                           markerType,  
                                           errorCategory);  
            if (errorCategory == TaskErrorCategory.Error)  
            {  
                taskItem.ImageIndex = TestIconImageIndex.Error;  
            }  
            return taskItem;  
        }  
    }  
}  
```  
  
## <a name="the-default-image-list-for-a-language-service"></a>Výchozí seznam obrázků pro služby jazyka  
 Výchozí image seznam součástí základní třídy služeb jazyka MPF obsahuje počet ikon přidružených více společné prvky jazyka. Hromadné tyto ikony jsou uspořádány do šesti variace odpovídající konceptech správy přístupů veřejné, interní, friend, protected, private, a místní sady. Například můžete mít jiné ikony pro metodu v závislosti na tom, jestli je veřejné, chráněné nebo soukromé.  
  
 Následující výčet určuje typické názvy pro každou sadu ikonu a Určuje přidružený index. Například založené na výčtu, můžete zadat index obrázku pro chráněnou metodu jako `(int)IconImageIndex.Method + (int)IconImageIndex.AccessProtected`. Můžete změnit názvy v tento výčet podle potřeby.  
  
```csharp  
public enum IconImageIndex  
        {  
            // access types  
            AccessPublic = 0,  
            AccessInternal = 1,  
            AccessFriend = 2,  
            AccessProtected = 3,  
            AccessPrivate = 4,  
            AccessShortcut = 5,  
  
            Base = 6,  
            // Each of the following icon type has 6 versions,  
            //corresponding to the access types  
            Class = Base + 0,  
            Constant = Base + 1,  
            Delegate = Base + 2,  
            Enumeration = Base + 3,  
            EnumMember = Base + 4,  
            Event = Base + 5,  
            Exception = Base + 6,  
            Field = Base + 7,  
            Interface = Base + 8,  
            Macro = Base + 9,  
            Map = Base + 10,  
            MapItem = Base + 11,  
            Method = Base + 12,  
            OverloadedMethod = Base + 13,  
            Module = Base + 14,  
            Namespace = Base + 15,  
            Operator = Base + 16,  
            Property = Base + 17,  
            Struct = Base + 18,  
            Template = Base + 19,  
            Typedef = Base + 20,  
            Type = Base + 21,  
            Union = Base + 22,  
            Variable = Base + 23,  
            ValueType = Base + 24,  
            Intrinsic = Base + 25,  
            JavaMethod = Base + 26,  
            JavaField = Base + 27,  
            JavaClass = Base + 28,  
            JavaNamespace = Base + 29,  
            JavaInterface = Base + 30,  
            // Miscellaneous icons with one icon for each type.  
            Error = 187,  
            GreyedClass = 188,  
            GreyedPrivateMethod = 189,  
            GreyedProtectedMethod = 190,  
            GreyedPublicMethod = 191,  
            BrowseResourceFile = 192,  
            Reference = 193,  
            Library = 194,  
            VBProject = 195,  
            VBWebProject = 196,  
            CSProject = 197,  
            CSWebProject = 198,  
            VB6Project = 199,  
            CPlusProject = 200,  
            Form = 201,  
            OpenFolder = 202,  
            ClosedFolder = 203,  
            Arrow = 204,  
            CSClass = 205,  
            Snippet = 206,  
            Keyword = 207,  
            Info = 208,  
            CallBrowserCall = 209,  
            CallBrowserCallRecursive = 210,  
            XMLEditor = 211,  
            VJProject = 212,  
            VJClass = 213,  
            ForwardedType = 214,  
            CallsTo = 215,  
            CallsFrom = 216,  
            Warning = 217,  
        }  
```  
  
## <a name="see-also"></a>Viz také  
 [Implementace služby starší verze jazyka](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Přehled služby starší verze jazyka](../../extensibility/internals/legacy-language-service-overview.md)   
 [Registrace služby starší verze jazyka](../../extensibility/internals/registering-a-legacy-language-service1.md)   
 [Analyzátor a skener služby starší verze jazyka](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)