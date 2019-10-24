---
title: Implementace starší verze jazyka Jazyka2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], implementing
ms.assetid: 5bcafdc5-f922-48f6-a12e-6c8507a79a05
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 053ca367776c811dd1192814c5f928bb294eefb4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727242"
---
# <a name="implementing-a-legacy-language-service"></a>Implementace služby starší verze jazyka
Chcete-li implementovat jazykovou službu pomocí spravovaného balíčku Package Framework (MPF), musíte odvodit třídu z třídy <xref:Microsoft.VisualStudio.Package.LanguageService> a implementovat následující abstraktní metody a vlastnosti:

- Metoda <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>

- Metoda <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>

- Metoda <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>

- Vlastnost <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A>

  Podrobnosti o implementaci těchto metod a vlastností naleznete v příslušných částech níže.

  Aby bylo možné podporovat další funkce, může být nutné, aby služba jazyka mohla odvodit třídu z jedné z tříd služby jazyka MPF. například pro podporu dalších příkazů nabídky musíte odvodit třídu z třídy <xref:Microsoft.VisualStudio.Package.ViewFilter> a přepsat několik metod manipulace s příkazy (podrobnosti najdete v <xref:Microsoft.VisualStudio.Package.ViewFilter>). Třída <xref:Microsoft.VisualStudio.Package.LanguageService> poskytuje řadu metod, které jsou volány pro vytvoření nových instancí různých tříd a přepsání vhodné metody vytvoření pro poskytnutí instance vaší třídy. Například je třeba přepsat metodu <xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A> ve třídě <xref:Microsoft.VisualStudio.Package.LanguageService> a vrátit instanci vlastní třídy <xref:Microsoft.VisualStudio.Package.ViewFilter>. Další podrobnosti najdete v části vytváření instancí vlastních tříd.

  Vaše jazyková služba může také poskytovat vlastní ikony, které se používají na mnoha místech. Například když se zobrazí seznam dokončení IntelliSense, může mít každá položka v seznamu přiřazenou ikonu a označit položku jako metodu, třídu, obor názvů, vlastnost nebo cokoli, co je potřeba pro váš jazyk. Tyto ikony se používají ve všech seznamech IntelliSense, v **navigačním panelu**a v okně **Seznam chyb** úlohy. Podrobnosti najdete níže v části image služby jazyka.

## <a name="getlanguagepreferences-method"></a>Metoda GetLanguagePreferences
 Metoda <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> vždy vrací stejnou instanci <xref:Microsoft.VisualStudio.Package.LanguagePreferences> třídy. Základní třídu <xref:Microsoft.VisualStudio.Package.LanguagePreferences> můžete použít, pokud nepotřebujete žádné další předvolby pro jazykovou službu. Třídy služby jazyka MPF předpokládají přítomnost alespoň základní třídy <xref:Microsoft.VisualStudio.Package.LanguagePreferences>.

### <a name="example"></a>Příklad
 Tento příklad ukazuje typickou implementaci metody <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>. Tento příklad používá základní třídu <xref:Microsoft.VisualStudio.Package.LanguagePreferences>.

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
 Tato metoda vrací instanci objektu <xref:Microsoft.VisualStudio.Package.IScanner>, který implementuje analyzátor orientovaný na řádek nebo skener používaný pro získání tokenů a jejich typů a triggerů. Tento skener se používá ve třídě <xref:Microsoft.VisualStudio.Package.Colorizer> pro vybarvení, i když se dá skener použít také k získání typů tokenů a triggerů jako předehru pro složitější operaci analýzy. Je nutné dodat třídu, která implementuje rozhraní <xref:Microsoft.VisualStudio.Package.IScanner> a je nutné implementovat všechny metody rozhraní <xref:Microsoft.VisualStudio.Package.IScanner>.

### <a name="example"></a>Příklad
 Tento příklad ukazuje typickou implementaci metody <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>. Třída `TestScanner` implementuje rozhraní <xref:Microsoft.VisualStudio.Package.IScanner> (není zobrazeno).

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
 Analyzuje zdrojový soubor na základě mnoha různých důvodů. Tato metoda má přiřazený objekt <xref:Microsoft.VisualStudio.Package.ParseRequest>, který popisuje, co se očekává od konkrétní operace analýzy. Metoda <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> vyvolá složitější analyzátor, který určuje funkce a rozsah tokenu. Metoda <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> se používá v podpoře pro operace IntelliSense a také pro spárování složených závorek. I v případě, že tyto rozšířené operace nepodporujete, je stále nutné vrátit platný objekt <xref:Microsoft.VisualStudio.Package.AuthoringScope> a vyžaduje, abyste vytvořili třídu, která implementuje rozhraní <xref:Microsoft.VisualStudio.Package.AuthoringScope> a implementovat všechny metody v tomto rozhraní. Hodnoty null můžete vracet ze všech metod, ale samotný objekt <xref:Microsoft.VisualStudio.Package.AuthoringScope> nesmí mít hodnotu null.

### <a name="example"></a>Příklad
 Tento příklad ukazuje minimální implementaci <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metody a <xref:Microsoft.VisualStudio.Package.AuthoringScope> třídy, stačí, když chcete, aby služba jazyka mohla kompilovat a fungovat, aniž by ve skutečnosti podporovala pokročilejší funkce.

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

## <a name="name-property"></a>Vlastnost Name
 Tato vlastnost vrátí název jazykové služby. Tento název musí být zadaný při registraci jazykové služby. Tento název se používá v několika místech, což je nejdůležitější z <xref:Microsoft.VisualStudio.Package.LanguagePreferences> třídy, kde se název používá pro přístup k registru. Název vrácený touto vlastností nesmí být lokalizovaný, protože se používá v registru pro položky registru a názvy klíčů.

### <a name="example"></a>Příklad
 Tento příklad ukazuje jednu možnou implementaci vlastnosti <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A>. Všimněte si, že název je pevně kódovaný: skutečný název by měl být získán ze souboru prostředků, aby jej bylo možné použít při registraci jazykové služby (viz [Registrace služby starší verze jazyka](../../extensibility/internals/registering-a-legacy-language-service1.md)).

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

## <a name="instantiating-custom-classes"></a>Vytváření instancí vlastních tříd
 Následující metody v zadaných třídách mohou být přepsány, aby poskytovaly instance vašich vlastních verzí každé třídy.

### <a name="in-the-languageservice-class"></a>Ve třídě LanguageService

|Metoda|Vrácená třída|Popis|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateCodeWindowManager%2A>|<xref:Microsoft.VisualStudio.Package.CodeWindowManager>|Pro podporu vlastních přidání do textového zobrazení.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>|<xref:Microsoft.VisualStudio.Package.DocumentProperties>|Pro podporu vlastních vlastností dokumentu.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>|<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>|Pro podporu **navigačního panelu**.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionFunction>|Pro podporu funkcí v šablonách fragmentů kódu.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionProvider>|Pro podporu fragmentů kódu (Tato metoda obvykle není přepsána).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A>|<xref:Microsoft.VisualStudio.Package.ParseRequest>|Pro podporu přizpůsobení <xref:Microsoft.VisualStudio.Package.ParseRequest> struktury (Tato metoda obvykle není přepsána).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A>|<xref:Microsoft.VisualStudio.Package.Source>|Pro podporu formátování zdrojového kódu, zadání znaků komentáře a přizpůsobení podpisů metody.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>|<xref:Microsoft.VisualStudio.Package.ViewFilter>|Pro podporu dalších příkazů nabídky.|
|<xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A>|<xref:Microsoft.VisualStudio.Package.Colorizer>|Pro podporu zvýrazňování syntaxe (Tato metoda obvykle není přepsána).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>|<xref:Microsoft.VisualStudio.Package.LanguagePreferences>|Pro podporu přístupu k jazykovým preferencím. Tato metoda musí být implementována, ale může vracet instanci základní třídy.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>|<xref:Microsoft.VisualStudio.Package.IScanner>|K poskytnutí analyzátoru používaného k identifikaci typů tokenů na řádku. Tato metoda musí být implementována a <xref:Microsoft.VisualStudio.Package.IScanner> musí být odvozena z.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringScope>|K poskytnutí analyzátoru používaného k identifikaci funkcí a rozsahu celého zdrojového souboru. Tato metoda musí být implementována a musí vracet instanci vaší verze <xref:Microsoft.VisualStudio.Package.AuthoringScope> třídy. Pokud chcete podporovat zvýrazňování syntaxe (což vyžaduje analyzátor <xref:Microsoft.VisualStudio.Package.IScanner> vrácený z metody <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>), nemůžete v této metodě dělat žádnou jinou metodu než vrátit verzi třídy <xref:Microsoft.VisualStudio.Package.AuthoringScope>, jejíž metody vrací hodnoty null.|

### <a name="in-the-source-class"></a>Ve zdrojové třídě

|Metoda|Vrácená třída|Popis|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>|<xref:Microsoft.VisualStudio.Package.CompletionSet>|Pro přizpůsobení zobrazení seznamů dokončení technologie IntelliSense (Tato metoda obvykle není přepsána).|
|<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>|<xref:Microsoft.VisualStudio.Package.DocumentTask>|Pro podpůrné značky v seznamu úkolů Seznam chyb; konkrétně Podpora funkcí mimo otevření souboru a přechod na řádek, který způsobil chybu.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateMethodData%2A>|<xref:Microsoft.VisualStudio.Package.MethodData>|Pro přizpůsobení zobrazení popisů informací o parametrech IntelliSense.|
|<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>|<xref:Microsoft.VisualStudio.Package.CommentInfo>|Pro podporu kódu komentářů.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateAuthoringSink%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringSink>|Pro shromažďování informací během operace analýzy.|

### <a name="in-the-authoringscope-class"></a>Ve třídě AuthoringScope

|Metoda|Vrácená třída|Popis|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>|<xref:Microsoft.VisualStudio.Package.Declarations>|Poskytuje seznam deklarací, jako jsou členy nebo typy. Tato metoda musí být implementována, ale může vracet hodnotu null. Pokud tato metoda vrátí platný objekt, musí být objekt instancí vaší verze třídy <xref:Microsoft.VisualStudio.Package.Declarations>.|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A>|<xref:Microsoft.VisualStudio.Package.Methods>|Poskytuje seznam signatur metod pro daný kontext. Tato metoda musí být implementována, ale může vracet hodnotu null. Pokud tato metoda vrátí platný objekt, musí být objekt instancí vaší verze třídy <xref:Microsoft.VisualStudio.Package.Methods>.|

## <a name="language-service-images"></a>Image služby jazyka
 Chcete-li poskytnout seznam ikon, které mají být použity v celé jazykové službě, přepište metodu <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> ve třídě <xref:Microsoft.VisualStudio.Package.LanguageService> a vraťte <xref:System.Windows.Forms.ImageList> obsahující ikony. Základní třída <xref:Microsoft.VisualStudio.Package.LanguageService> načte výchozí sadu ikon. Vzhledem k tomu, že jste zadali přesný index obrázku v těch místech, které potřebují ikony, způsob uspořádání vlastního seznamu obrázků je zcela na vás.

### <a name="images-used-in-intellisense-completion-lists"></a>Obrázky používané v seznamech dokončování IntelliSense
 U seznamů dokončení technologie IntelliSense je index bitové kopie určen pro každou položku v metodě <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> <xref:Microsoft.VisualStudio.Package.Declarations> třídy, kterou je nutné přepsat, pokud chcete zadat index obrázku. Hodnota vrácená z <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> metoda je index do seznamu obrázků zadaného konstruktoru <xref:Microsoft.VisualStudio.Package.CompletionSet> třídy a to je stejný seznam obrázků vrácených z metody <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> ve třídě <xref:Microsoft.VisualStudio.Package.LanguageService> (můžete změnit, který seznam obrázků se má použít pro @no__ t_4, pokud přepíšete metodu <xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A> ve třídě <xref:Microsoft.VisualStudio.Package.Source> tak, aby poskytovala jiný seznam obrázků).

### <a name="images-used-in-the-navigation-bar"></a>Obrázky použité v navigačním panelu
 **Navigační panel** zobrazuje seznam typů a členů a slouží k rychlé navigaci, které mohou zobrazovat ikony. Tyto ikony jsou získány z metody <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> ve třídě <xref:Microsoft.VisualStudio.Package.LanguageService> a nelze je přepsat specificky pro **navigační panel**. Indexy použité pro každou položku v polích se seznamem jsou zadány, když jsou v seznamech reprezentujících pole se seznamem vyplněny <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metoda ve třídě <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> (viz [Podpora pro navigační panel ve službě starší verze jazyka](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)). Tyto indexy obrázků jsou získány z analyzátoru, obvykle prostřednictvím vaší verze <xref:Microsoft.VisualStudio.Package.Declarations> třídy. Způsob získávání indexů je zcela na vás.

### <a name="images-used-in-the-error-list-task-window"></a>Obrázky používané v okně Seznam chyb úlohy
 Pokaždé, když analyzátor metody <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> (viz [analyzátor a skener služby starší verze jazyka](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)), zaznamená chybu a předá tuto chybu metodě <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> ve třídě <xref:Microsoft.VisualStudio.Package.AuthoringSink>, zobrazí se chyba v okně **Seznam chyb** úlohy. K jednotlivým položkám, které se zobrazují v okně úloh, se dá přiřadit ikona, která se zobrazí ze stejného seznamu obrázků vráceného z metody <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> ve třídě <xref:Microsoft.VisualStudio.Package.LanguageService>. Výchozím chováním tříd MPF není zobrazit obrázek s chybovou zprávou. Toto chování však můžete přepsat odvozením třídy z třídy <xref:Microsoft.VisualStudio.Package.Source> a přepsáním <xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A> metody. V této metodě vytvoříte nový objekt <xref:Microsoft.VisualStudio.Package.DocumentTask>. Před vrácením tohoto objektu můžete použít vlastnost <xref:Microsoft.VisualStudio.Shell.Task.ImageIndex%2A> v objektu <xref:Microsoft.VisualStudio.Package.DocumentTask> pro nastavení indexu obrázku. To by vypadalo podobně jako v následujícím příkladu. Všimněte si, že `TestIconImageIndex` je výčet, který obsahuje všechny ikony a je specifický pro tento příklad. Můžete mít jiný způsob identifikace ikon ve službě jazyka.

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

## <a name="the-default-image-list-for-a-language-service"></a>Výchozí seznam obrázků pro službu jazyka
 Výchozí seznam obrázků dodávaný se základními třídami služby jazyka MPF obsahuje několik ikon spojených s více společnými jazykovými prvky. Hromadné tyto ikony jsou uspořádány do množiny šesti variant, které odpovídají konceptům přístupu veřejného, interního, Friend, Protected, Private a Shortcut. Například můžete mít různé ikony pro metodu v závislosti na tom, zda je veřejný, chráněný nebo soukromý.

 Následující výčet Určuje typické názvy pro každou sadu ikon a Určuje přidružený index. Například na základě výčtu můžete určit index obrázku pro chráněnou metodu jako `(int)IconImageIndex.Method + (int)IconImageIndex.AccessProtected`. Názvy v tomto výčtu můžete změnit podle potřeby.

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

## <a name="see-also"></a>Viz také:
- [Implementace služby starší verze jazyka](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Přehled služby starší verze jazyka](../../extensibility/internals/legacy-language-service-overview.md)
- [Registrace služby starší verze jazyka](../../extensibility/internals/registering-a-legacy-language-service1.md)
- [Analyzátor a skener služby starší verze jazyka](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)