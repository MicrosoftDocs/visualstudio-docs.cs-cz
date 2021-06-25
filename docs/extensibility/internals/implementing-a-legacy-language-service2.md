---
title: Implementace služby starší verze jazyka2 | Microsoft Docs
description: Naučte se implementovat službu starší verze jazyka, která podporuje funkce rozšířených jazykových služeb, pomocí rozhraní spravovaného balíčku (MPF). 2. část z 2.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- language services [managed package framework], implementing
ms.assetid: 5bcafdc5-f922-48f6-a12e-6c8507a79a05
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fca2548ddb0c8281241b14de0ec470cfe22db1a1
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900119"
---
# <a name="implementing-a-legacy-language-service-2"></a>Implementace služby starší verze jazyka 2
Chcete-li implementovat službu jazyka pomocí rozhraní spravovaného balíčku (MPF), musíte odvodit třídu z třídy a implementovat následující abstraktní metody a <xref:Microsoft.VisualStudio.Package.LanguageService> vlastnosti:

- Metoda <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>

- Metoda <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>

- Metoda <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>

- Vlastnost <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A>

  Podrobnosti o implementaci těchto metod a vlastností najdete v příslušných částech níže.

  Aby služba jazyka podporovala další funkce, bude možná muset odvodit třídu z jedné z tříd služby jazyka MPF. Například pro podporu dalších příkazů nabídky je nutné odvodit třídu z třídy a přepsat několik metod zpracování příkazů <xref:Microsoft.VisualStudio.Package.ViewFilter> (podrobnosti <xref:Microsoft.VisualStudio.Package.ViewFilter> najdete). Třída poskytuje řadu metod, které jsou volány k vytvoření nových instancí různých tříd a přepíšete příslušnou metodu vytváření pro poskytnutí <xref:Microsoft.VisualStudio.Package.LanguageService> instance třídy. Například je třeba přepsat metodu <xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A> ve třídě , aby se vrátila instance vlastní <xref:Microsoft.VisualStudio.Package.LanguageService> <xref:Microsoft.VisualStudio.Package.ViewFilter> třídy. Další podrobnosti najdete v části Vytváření instancí vlastních tříd.

  Služba jazyka může také zadat vlastní ikony, které se používají na mnoha místech. Když se například zobrazí seznam pro doplňování IntelliSense, může mít každá položka v seznamu přidruženou ikonu, která označuje položku jako metodu, třídu, obor názvů, vlastnost nebo cokoli, co je pro váš jazyk nezbytné. Tyto ikony se používají ve všech seznamech IntelliSense, v navigačním **panelu** a **v** Seznam chyb okně úlohy. Podrobnosti najdete níže v části Image jazykových služeb.

## <a name="getlanguagepreferences-method"></a>GetLanguagePreferences – metoda
 Metoda <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> vždy vrátí stejnou instanci <xref:Microsoft.VisualStudio.Package.LanguagePreferences> třídy. Základní třídu můžete <xref:Microsoft.VisualStudio.Package.LanguagePreferences> použít, pokud nepotřebujete žádné další předvolby pro službu jazyka. Třídy služeb jazyka MPF předpokládají přítomnost alespoň základní <xref:Microsoft.VisualStudio.Package.LanguagePreferences> třídy.

### <a name="example"></a>Příklad
 Tento příklad ukazuje typickou implementaci <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> metody . Tento příklad používá základní <xref:Microsoft.VisualStudio.Package.LanguagePreferences> třídu.

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
 Tato metoda vrátí instanci objektu, která implementuje line-oriented parser nebo skener používaný k získání tokenů a jejich <xref:Microsoft.VisualStudio.Package.IScanner> typů a triggerů. Tento skener se používá ve třídě pro zabarvení, i když skener lze použít také pro získání typů tokenů a triggerů jako předchůdy pro složitější operaci <xref:Microsoft.VisualStudio.Package.Colorizer> analýzy. Je nutné zadat třídu, která implementuje rozhraní a je <xref:Microsoft.VisualStudio.Package.IScanner> nutné implementovat všechny metody v <xref:Microsoft.VisualStudio.Package.IScanner> rozhraní.

### <a name="example"></a>Příklad
 Tento příklad ukazuje typickou implementaci <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> metody . Třída `TestScanner` implementuje rozhraní <xref:Microsoft.VisualStudio.Package.IScanner> (není zobrazeno).

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
 Analyzuje zdrojový soubor na základě několika různých důvodů. Této metodě je <xref:Microsoft.VisualStudio.Package.ParseRequest> dán objekt , který popisuje, co se od konkrétní operace analýzy očekává. Metoda vyvolá složitější analyzátor, který určuje <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> funkčnost a rozsah tokenu. Metoda <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> se používá v podpoře operací IntelliSense a také párování závorek. I když takové pokročilé operace nepodporujete, stále musíte vrátit platný objekt, který vyžaduje vytvoření třídy, která implementuje rozhraní a implementuje všechny metody v <xref:Microsoft.VisualStudio.Package.AuthoringScope> <xref:Microsoft.VisualStudio.Package.AuthoringScope> tomto rozhraní. Hodnoty null můžete vrátit ze všech metod, ale <xref:Microsoft.VisualStudio.Package.AuthoringScope> samotný objekt nesmí být hodnotou null.

### <a name="example"></a>Příklad
 Tento příklad ukazuje minimální implementaci metody a třídy, která je dostatečná k tomu, aby služba jazyka mohla zkompilovat a fungovat, aniž by ve skutečnosti podporovala jakoukoli <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> <xref:Microsoft.VisualStudio.Package.AuthoringScope> pokročilejší funkci.

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
 Tato vlastnost vrátí název služby jazyka. Musí to být stejný název, který jste dostali při registraci služby jazyka. Tento název se používá na řadě míst, z nichž nejvýznamnější je třída, ve které se název používá pro přístup <xref:Microsoft.VisualStudio.Package.LanguagePreferences> k registru. Název vrácený touto vlastností nesmí být lokalizovaný, protože se používá v registru pro položky registru a názvy klíčů.

### <a name="example"></a>Příklad
 Tento příklad ukazuje jednu možnou implementaci <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> vlastnosti . Všimněte si, že zde je název na pevném kódu: skutečný název by se měl získat ze souboru prostředků, aby ho bylo možné použít při registraci služby jazyka (viz Registrace služby starší verze [jazyka).](../../extensibility/internals/registering-a-legacy-language-service1.md)

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
 Následující metody v zadaných třídách lze přepsat tak, aby poskytovaly instance vlastních verzí každé třídy.

### <a name="in-the-languageservice-class"></a>Ve třídě LanguageService

|Metoda|Vrácená třída|Description|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateCodeWindowManager%2A>|<xref:Microsoft.VisualStudio.Package.CodeWindowManager>|Pro podporu vlastních přidání do textového zobrazení.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>|<xref:Microsoft.VisualStudio.Package.DocumentProperties>|Pro podporu vlastních vlastností dokumentu.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>|<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>|Pro podporu **navigačního panelu**.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionFunction>|Podpora funkcí v šablonách fragmentů kódu|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionProvider>|Pro podporu fragmentů kódu (tato metoda obvykle není přepsána).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A>|<xref:Microsoft.VisualStudio.Package.ParseRequest>|Pro podporu přizpůsobení <xref:Microsoft.VisualStudio.Package.ParseRequest> struktury (tato metoda obvykle není přepsána).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A>|<xref:Microsoft.VisualStudio.Package.Source>|Podpora formátování zdrojového kódu, zadávání znaků komentáře a přizpůsobení podpisů metod|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>|<xref:Microsoft.VisualStudio.Package.ViewFilter>|Podpora dalších příkazů nabídky|
|<xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A>|<xref:Microsoft.VisualStudio.Package.Colorizer>|Pro podporu zvýrazňování syntaxe (tato metoda obvykle není přepsána).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>|<xref:Microsoft.VisualStudio.Package.LanguagePreferences>|Pro podporu přístupu k jazykových předvolbách. Tato metoda musí být implementována, ale může vrátit instanci základní třídy.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>|<xref:Microsoft.VisualStudio.Package.IScanner>|K poskytnutí analyzátoru používaného k identifikaci typů tokenů na řádku. Tato metoda musí být implementována <xref:Microsoft.VisualStudio.Package.IScanner> a musí být odvozena z .|
|<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringScope>|K poskytnutí analyzátoru, který slouží k identifikaci funkcí a rozsahu v celém zdrojovém souboru. Tato metoda musí být implementována a musí vracet instanci vaší verze <xref:Microsoft.VisualStudio.Package.AuthoringScope> třídy. Pokud chcete podporovat pouze zvýrazňování syntaxe (které vyžaduje analyzátor vrácený metodou ), můžete v této metodě dělat nic jiného než vrátit verzi třídy, jejíž metody vracejí <xref:Microsoft.VisualStudio.Package.IScanner> <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> hodnoty <xref:Microsoft.VisualStudio.Package.AuthoringScope> null.|

### <a name="in-the-source-class"></a>Ve zdrojové třídě

|Metoda|Vrácená třída|Description|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>|<xref:Microsoft.VisualStudio.Package.CompletionSet>|Pro přizpůsobení zobrazení seznamů pro doplňování IntelliSense (tato metoda se obvykle přepíše).|
|<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>|<xref:Microsoft.VisualStudio.Package.DocumentTask>|Pro podporu značek v Seznam chyb úkolů; konkrétně podpora funkcí nad rámec otevření souboru a přechodu na řádek, který chybu způsobil.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateMethodData%2A>|<xref:Microsoft.VisualStudio.Package.MethodData>|Pro přizpůsobení zobrazení popisů informací o parametrech Technologie IntelliSense.|
|<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>|<xref:Microsoft.VisualStudio.Package.CommentInfo>|Pro podporu kódu pro komentování.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateAuthoringSink%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringSink>|Pro shromažďování informací během operace parsování.|

### <a name="in-the-authoringscope-class"></a>Ve třídě AuthoringScope

|Metoda|Vrácená třída|Description|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>|<xref:Microsoft.VisualStudio.Package.Declarations>|Poskytuje seznam deklarací, jako jsou členy nebo typy. Tato metoda musí být implementována, ale může vrátit hodnotu null. Pokud tato metoda vrátí platný objekt, musí být objekt instancí vaší verze <xref:Microsoft.VisualStudio.Package.Declarations> třídy.|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A>|<xref:Microsoft.VisualStudio.Package.Methods>|Poskytuje seznam podpisů metod pro daný kontext. Tato metoda musí být implementována, ale může vrátit hodnotu null. Pokud tato metoda vrátí platný objekt, musí být objekt instancí vaší verze <xref:Microsoft.VisualStudio.Package.Methods> třídy.|

## <a name="language-service-images"></a>Image služeb jazyka
 Pokud chcete poskytnout seznam ikon, které se mají použít v rámci služby jazyka, přepište metodu ve třídě a <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> vraťte <xref:System.Windows.Forms.ImageList> objekt obsahující ikony. Základní třída <xref:Microsoft.VisualStudio.Package.LanguageService> načte výchozí sadu ikon. Vzhledem k tomu, že na těch místech, kde potřebujete ikony, zadáte přesný index obrázku, je způsob uspořádání vlastního seznamu obrázků zcela na vás.

### <a name="images-used-in-intellisense-completion-lists"></a>Obrázky používané v seznamech doplňování IntelliSense
 U seznamů pro doplňování IntelliSense je index obrázků určený pro každou položku v metodě třídy , kterou musíte přepsat, pokud chcete zadat <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> <xref:Microsoft.VisualStudio.Package.Declarations> index obrázku. Hodnota vrácená z metody je index do seznamu obrázků zadaného konstruktoru třídy a je to stejný seznam obrázků vrácený z metody ve třídě (můžete změnit seznam obrázků, který se má použít pro , pokud přepíšete metodu ve třídě pro dodání jiného seznamu <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> <xref:Microsoft.VisualStudio.Package.CompletionSet> <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> <xref:Microsoft.VisualStudio.Package.CompletionSet> <xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A> <xref:Microsoft.VisualStudio.Package.Source> obrázků).

### <a name="images-used-in-the-navigation-bar"></a>Obrázky použité v navigačním panelu
 Navigační **panel zobrazuje** seznamy typů a členů a slouží k rychlé navigaci a může zobrazovat ikony. Tyto ikony jsou <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> získány z metody ve <xref:Microsoft.VisualStudio.Package.LanguageService> třídě a nelze je přepsat speciálně pro navigační **panel**. Indexy použité pro každou položku v polích se seznamem jsou určeny, když jsou seznamy představující pole se seznamem vyplněny metodou ve třídě (viz Podpora navigačního panelu ve službě starší verze <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> [jazyka](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)). Tyto indexy obrázků se nějakým způsobem získávají z analyzátoru, obvykle prostřednictvím vaší <xref:Microsoft.VisualStudio.Package.Declarations> verze třídy. Způsob, jakým se indexy získávají, je zcela na vás.

### <a name="images-used-in-the-error-list-task-window"></a>Obrázky použité v Seznam chyb úloh
 Pokaždé, když analyzátor metod (viz Analyzátor a skener služby starší verze jazyka) narazí na chybu a předá tuto chybu metodě ve třídě , zobrazí se tato chyba v okně Seznam chyb <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> [](../../extensibility/internals/legacy-language-service-parser-and-scanner.md) <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> <xref:Microsoft.VisualStudio.Package.AuthoringSink> úlohy.  Ke každé položce, která se zobrazí v okně úlohy, může být přidružena ikona a tato ikona pochází ze stejného seznamu obrázků vráceného metodou <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> ve <xref:Microsoft.VisualStudio.Package.LanguageService> třídě . Výchozím chováním tříd MPF je nez zobrazení obrázku s chybovou zprávou. Toto chování však můžete přepsat odvozením třídy z třídy a <xref:Microsoft.VisualStudio.Package.Source> přepsáním <xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A> metody . V této metodě vytvoříte nový <xref:Microsoft.VisualStudio.Package.DocumentTask> objekt. Před vrácením tohoto objektu můžete použít vlastnost objektu k nastavení <xref:Microsoft.VisualStudio.Shell.Task.ImageIndex%2A> <xref:Microsoft.VisualStudio.Package.DocumentTask> indexu obrázku. To by vypadalo podobně jako v následujícím příkladu. Všimněte `TestIconImageIndex` si, že je výčet, který vypíše všechny ikony a je specifický pro tento příklad. Můžete mít jiný způsob identifikace ikon ve službě jazyka.

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
 Výchozí seznam obrázků dodávaný se základními třídami služby jazyka MPF obsahuje několik ikon přidružených k běžným prvkům jazyka. Většina těchto ikon je uspořádaná do sad šesti variant, které odpovídají konceptům přístupu veřejných, interních, přátel, chráněných, privátních a klávesových zkratek. Můžete mít například pro metodu různé ikony v závislosti na tom, jestli je veřejná, chráněná nebo soukromá.

 Následující výčet určuje typické názvy pro každou sadu ikon a určuje přidružený index. Například na základě výčtu můžete zadat index obrázku pro chráněnou metodu jako `(int)IconImageIndex.Method + (int)IconImageIndex.AccessProtected` . Názvy v tomto výčtu můžete podle potřeby změnit.

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
