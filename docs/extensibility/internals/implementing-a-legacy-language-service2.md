---
title: Implementace služby staršího jazyka2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], implementing
ms.assetid: 5bcafdc5-f922-48f6-a12e-6c8507a79a05
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e435af68a893c923eafef744762c9da8505c3fb7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707677"
---
# <a name="implementing-a-legacy-language-service"></a>Implementace služby starší verze jazyka
Chcete-li implementovat službu jazyka pomocí architektury spravovaného balíčku <xref:Microsoft.VisualStudio.Package.LanguageService> (MPF), musíte odvodit třídu z třídy a implementovat následující abstraktní metody a vlastnosti:

- Metoda <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>

- Metoda <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>

- Metoda <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>

- Vlastnost <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A>

  Podrobnosti o implementaci těchto metod a vlastností naleznete v příslušných částech níže.

  Pro podporu dalších funkcí může být možné, že vaše jazyková služba bude muset odvodit třídu z jedné z tříd jazykových služeb MPF. Například pro podporu dalších příkazů nabídky je nutné <xref:Microsoft.VisualStudio.Package.ViewFilter> odvodit třídu z třídy a přepsat několik metod zpracování příkazů (podrobnosti viz). <xref:Microsoft.VisualStudio.Package.ViewFilter> Třída <xref:Microsoft.VisualStudio.Package.LanguageService> poskytuje řadu metod, které jsou volány k vytvoření nové instance různých tříd a přepsat příslušnou metodu vytvoření poskytnout instanci vaší třídy. Například je třeba přepsat <xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A> metodu <xref:Microsoft.VisualStudio.Package.LanguageService> ve třídě vrátit instanci vlastní <xref:Microsoft.VisualStudio.Package.ViewFilter> třídy. Další podrobnosti najdete v části Vytváření vytváření vlastních tříd.

  Vaše jazyková služba může také poskytovat vlastní ikony, které se používají na mnoha místech. Pokud je například zobrazen seznam dokončení technologie IntelliSense, může být ke každé položce v seznamu přidružena ikona, která položku označuje jako metodu, třídu, obor názvů, vlastnost nebo vše, co je pro váš jazyk nezbytné. Tyto ikony se používají ve všech seznamech Technologie IntelliSense, navigačním **panelu**a v okně **úlohY Seznam chyb.** Podrobnosti naleznete v části "Obrázky jazykových služeb" níže.

## <a name="getlanguagepreferences-method"></a>Metoda GetLanguagePreferences
 Metoda <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> vždy vrátí stejnou instanci <xref:Microsoft.VisualStudio.Package.LanguagePreferences> třídy. Základní <xref:Microsoft.VisualStudio.Package.LanguagePreferences> třídu můžete použít, pokud nepotřebujete žádné další předvolby pro jazykovou službu. Třídy jazykových služeb MPF předpokládají přítomnost <xref:Microsoft.VisualStudio.Package.LanguagePreferences> alespoň základní třídy.

### <a name="example"></a>Příklad
 Tento příklad ukazuje typické <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> implementace metody. Tento příklad používá <xref:Microsoft.VisualStudio.Package.LanguagePreferences> základní třídu.

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

## <a name="getscanner-method"></a>Metoda GetScanner
 Tato metoda vrátí instanci objektu, <xref:Microsoft.VisualStudio.Package.IScanner> který implementuje analyzátor orientovaný na řádek nebo skener používaný pro získání tokenů a jejich typů a aktivačních událostí. Tento skener se <xref:Microsoft.VisualStudio.Package.Colorizer> používá ve třídě pro vybarvení, i když skener lze také použít pro získání typů tokenů a aktivačních událostí jako předehra k složitější operaci analýzy. Je nutné zadat třídu, <xref:Microsoft.VisualStudio.Package.IScanner> která implementuje rozhraní a <xref:Microsoft.VisualStudio.Package.IScanner> je nutné implementovat všechny metody v rozhraní.

### <a name="example"></a>Příklad
 Tento příklad ukazuje typické <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> implementace metody. Třída `TestScanner` implementuje <xref:Microsoft.VisualStudio.Package.IScanner> rozhraní (není zobrazeno).

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

## <a name="parsesource-method"></a>Metoda ParseSource
 Analyzuje zdrojový soubor na základě několika různých důvodů. Tato metoda je <xref:Microsoft.VisualStudio.Package.ParseRequest> uveden objekt, který popisuje, co se očekává od konkrétní operace analýzy. Metoda <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> vyvolá složitější analyzátor, který určuje funkčnost tokenu a obor. Metoda <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> se používá v podpoře operací IntelliSense, stejně jako srovnávač odpovídající. I v případě, že nepodporujete takové rozšířené <xref:Microsoft.VisualStudio.Package.AuthoringScope> operace, stále je nutné vrátit platný <xref:Microsoft.VisualStudio.Package.AuthoringScope> objekt a který vyžaduje vytvoření třídy, která implementuje rozhraní a implementovat všechny metody v tomto rozhraní. Můžete vrátit hodnoty null ze <xref:Microsoft.VisualStudio.Package.AuthoringScope> všech metod, ale samotný objekt nesmí být nulovou hodnotou.

### <a name="example"></a>Příklad
 Tento příklad ukazuje minimální <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> implementaci metody <xref:Microsoft.VisualStudio.Package.AuthoringScope> a třídy, která je dostatečná k tomu, aby umožnila službě jazyka kompilovat a fungovat bez skutečné podpory některé z pokročilejších funkcí.

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

## <a name="name-property"></a>Vlastnost názvu
 Tato vlastnost vrátí název služby jazyka. To musí být stejný název, který byl uveden při registraci služby jazyka. Tento název se používá na mnoha místech, z <xref:Microsoft.VisualStudio.Package.LanguagePreferences> nichž nejvýznamnější je třída, kde se název používá pro přístup k registru. Název vrácený touto vlastností nesmí být lokalizován, protože se používá v registru pro položku registru a názvy klíčů.

### <a name="example"></a>Příklad
 Tento příklad ukazuje jednu <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> možnou implementaci vlastnosti. Všimněte si, že název je zde pevně zakódován: skutečný název by měl být získán ze souboru prostředků, aby jej bylo možné použít při registraci jazykové služby (viz [Registrace služby staršího jazyka](../../extensibility/internals/registering-a-legacy-language-service1.md)).

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

## <a name="instantiating-custom-classes"></a>Vytváření vytváření instancí vlastních tříd
 Následující metody v určených třídách mohou být přepsány, aby poskytovaly instance vlastních verzí každé třídy.

### <a name="in-the-languageservice-class"></a>Ve třídě LanguageService

|Metoda|Vrácená třída|Popis|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateCodeWindowManager%2A>|<xref:Microsoft.VisualStudio.Package.CodeWindowManager>|Podpora vlastních dodatků k zobrazení textu.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>|<xref:Microsoft.VisualStudio.Package.DocumentProperties>|Podpora vlastních vlastností dokumentu.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>|<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>|Pro podporu **navigačního panelu**.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionFunction>|Pro podporu funkcí v šablonách fragmentu kódu.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionProvider>|Pro podporu fragmentů kódu (tato metoda obvykle není přepsána).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A>|<xref:Microsoft.VisualStudio.Package.ParseRequest>|Pro podporu přizpůsobení <xref:Microsoft.VisualStudio.Package.ParseRequest> struktury (tato metoda obvykle není přepsána).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A>|<xref:Microsoft.VisualStudio.Package.Source>|Podpora formátování zdrojového kódu, zadání znaků komentáře a přizpůsobení podpisů metod.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>|<xref:Microsoft.VisualStudio.Package.ViewFilter>|Chcete-li podporovat další příkazy nabídky.|
|<xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A>|<xref:Microsoft.VisualStudio.Package.Colorizer>|Pro podporu zvýraznění syntaxe (tato metoda obvykle není přepsána).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>|<xref:Microsoft.VisualStudio.Package.LanguagePreferences>|Podpora přístupu k jazykovým předvolbám. Tato metoda musí být implementována, ale může vrátit instanci základní třídy.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>|<xref:Microsoft.VisualStudio.Package.IScanner>|Chcete-li poskytnout analyzátor používaný pro identifikaci typů tokenů na řádku. Tato metoda musí <xref:Microsoft.VisualStudio.Package.IScanner> být implementována a musí být odvozena od.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringScope>|Chcete-li poskytnout analyzátor používaný pro identifikaci funkcí a oboru v celém zdrojovém souboru. Tato metoda musí být implementována a musí <xref:Microsoft.VisualStudio.Package.AuthoringScope> vrátit instanci vaší verze třídy. Pokud vše, co chcete podporovat, je <xref:Microsoft.VisualStudio.Package.IScanner> zvýraznění syntaxe <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> (což vyžaduje analyzátor vrácený z metody), <xref:Microsoft.VisualStudio.Package.AuthoringScope> můžete v této metodě nedělat nic jiného než vrátit verzi třídy, jejíž metody všechny vrátí hodnoty null.|

### <a name="in-the-source-class"></a>Ve zdrojové třídě

|Metoda|Vrácená třída|Popis|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>|<xref:Microsoft.VisualStudio.Package.CompletionSet>|Pro přizpůsobení zobrazení seznamů dokončení Technologie IntelliSense (tato metoda obvykle není přepsána).|
|<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>|<xref:Microsoft.VisualStudio.Package.DocumentTask>|Pro podporu značek v seznamu úkolů seznamu chyb. konkrétně podpora funkcí mimo otevření souboru a přechod na řádek, který způsobil chybu.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateMethodData%2A>|<xref:Microsoft.VisualStudio.Package.MethodData>|Pro přizpůsobení zobrazení informačních tipů pro parametry Technologie IntelliSense.|
|<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>|<xref:Microsoft.VisualStudio.Package.CommentInfo>|Pro podporu komentování kódu.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateAuthoringSink%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringSink>|Pro shromažďování informací během operace analýzy.|

### <a name="in-the-authoringscope-class"></a>Ve třídě AuthoringScope

|Metoda|Vrácená třída|Popis|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>|<xref:Microsoft.VisualStudio.Package.Declarations>|Obsahuje seznam deklarací, jako jsou členy nebo typy. Tato metoda musí být implementována, ale může vrátit hodnotu null. Pokud tato metoda vrátí platný objekt, musí být objekt <xref:Microsoft.VisualStudio.Package.Declarations> instancí vaší verze třídy.|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A>|<xref:Microsoft.VisualStudio.Package.Methods>|Obsahuje seznam podpisů metod pro daný kontext. Tato metoda musí být implementována, ale může vrátit hodnotu null. Pokud tato metoda vrátí platný objekt, musí být objekt <xref:Microsoft.VisualStudio.Package.Methods> instancí vaší verze třídy.|

## <a name="language-service-images"></a>Obrázky jazykových služeb
 Chcete-li poskytnout seznam ikon, které mají být <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> použity <xref:Microsoft.VisualStudio.Package.LanguageService> v rámci <xref:System.Windows.Forms.ImageList> služby jazyka, přepsat metodu ve třídě a vrátit obsahující ikony. Základní <xref:Microsoft.VisualStudio.Package.LanguageService> třída načte výchozí sadu ikon. Vzhledem k tomu, že na místech, kde potřebujete ikony, zadáte přesný index obrázků, je zcela na vás.

### <a name="images-used-in-intellisense-completion-lists"></a>Obrázky použité v seznamech dokončení technologie IntelliSense
 Pro seznamy dokončení Technologie IntelliSense je index <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> obrázku <xref:Microsoft.VisualStudio.Package.Declarations> určen pro každou položku v metodě třídy, kterou je nutné přepsat, pokud chcete zadat index obrázku. Hodnota vrácená <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> z metody je index do seznamu <xref:Microsoft.VisualStudio.Package.CompletionSet> obrázků dodaného konstruktoru třídy <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> a to <xref:Microsoft.VisualStudio.Package.LanguageService> je stejný seznam obrázků vrácený <xref:Microsoft.VisualStudio.Package.CompletionSet> z metody ve <xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A> třídě <xref:Microsoft.VisualStudio.Package.Source> (můžete změnit, který seznam obrázků se má použít, pokud přepíšete metodu ve třídě a zadáte jiný seznam obrázků).

### <a name="images-used-in-the-navigation-bar"></a>Obrázky použité na navigačním panelu
 **Navigační panel** zobrazuje seznamy typů a členů a slouží k rychlé navigaci, která může zobrazovat ikony. Tyto ikony jsou <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> získány <xref:Microsoft.VisualStudio.Package.LanguageService> z metody ve třídě a nelze přepsat speciálně pro **navigační panel**. Indexy použité pro každou položku v polích se seznamem jsou určeny, když <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> jsou seznamy představující pole se seznamem vyplněny metodou ve <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> třídě (viz Podpora [navigačního panelu ve službě staršího jazyka).](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md) Tyto indexy obrázků jsou získány nějak z analyzátoru, <xref:Microsoft.VisualStudio.Package.Declarations> obvykle prostřednictvím verze třídy. Jak se indexy získávají, je zcela na vás.

### <a name="images-used-in-the-error-list-task-window"></a>Obrázky použité v okně úlohy seznamu chyb
 Kdykoli <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> analyzátor metody (viz [Analyzátor starších jazykových služeb a skener)](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)narazí <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> na <xref:Microsoft.VisualStudio.Package.AuthoringSink> chybu a předá tuto chybu metodě ve třídě, je chyba uvedena v okně **úlohy Seznam chyb.** K každé položce, která se zobrazí v okně úkolu, lze přidružit iontovou ikonu a tato ikona pochází ze stejného seznamu obrázků vráceného z <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> metody ve <xref:Microsoft.VisualStudio.Package.LanguageService> třídě. Výchozí chování tříd MPF je nezobrazovat obrázek s chybovou zprávou. Toto chování však můžete přepsat odvozením třídy z <xref:Microsoft.VisualStudio.Package.Source> třídy a přepsáním <xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A> metody. V této metodě vytvoříte nový <xref:Microsoft.VisualStudio.Package.DocumentTask> objekt. Před vrácením tohoto objektu <xref:Microsoft.VisualStudio.Shell.Task.ImageIndex%2A> můžete použít <xref:Microsoft.VisualStudio.Package.DocumentTask> vlastnost objektu k nastavení indexu obrazu. To by vypadalo něco jako následující příklad. Všimněte `TestIconImageIndex` si, že je výčet, který obsahuje seznam všech ikon a je specifické pro tento příklad. Ve službě jazyka můžete identifikovat ikony jinak.

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

## <a name="the-default-image-list-for-a-language-service"></a>Výchozí seznam obrázků pro jazykovou službu
 Výchozí seznam obrázků dodaný se základními třídami jazykových služeb MPF obsahuje řadu ikon přidružených k běžnějším prvkům jazyka. Převážná část těchto ikon je uspořádána do sad šesti variant, které odpovídají konceptům přístupu veřejné, interní, přátelské, chráněné, soukromé a zkratky. Můžete mít například různé ikony pro metodu v závislosti na tom, zda je veřejná, chráněná nebo soukromá.

 Následující výčet určuje typické názvy pro každou sadu ikon a určuje přidružený index. Například na základě výčtu můžete zadat index obrazu pro `(int)IconImageIndex.Method + (int)IconImageIndex.AccessProtected`chráněnou metodu jako . Můžete změnit názvy v tomto výčtu podle potřeby.

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
- [Implementace služby starší verze jazyka](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Přehled služby starší verze jazyka](../../extensibility/internals/legacy-language-service-overview.md)
- [Registrace služby starší verze jazyka](../../extensibility/internals/registering-a-legacy-language-service1.md)
- [Analyzátor a skener služby starší verze jazyka](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
