---
title: Přizpůsobení nástrojů a panelu nástrojů
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.selectiondialog
- vs.dsltools.dsldesigner.selecticondialog
- vs.dsltools.dsldesigner.selectcursordialog
helpviewer_keywords:
- Domain-Specific Language, toolbox
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 3b0acab24dbb7ff1313e62e91b17bf87190dbb99
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "50967438"
---
# <a name="customizing-tools-and-the-toolbox"></a>Přizpůsobení nástrojů a panelu nástrojů

Je nutné definovat položky panelu nástrojů pro prvky, které chcete umožnit uživatelům, přidejte do své modely. Existují dva typy nástrojů: element nástroje a nástroje pro připojení. Uživatel ve vygenerovaném návrháři, můžete vybrat nástroj elementu přetáhněte do diagramu tvary a můžete vybrat nástroj pro připojení k vykreslení odkazů mezi tvary. Obecně platí nástrojů elementu umožňují uživatelům přidat instance třídy domény jejich modelů a nástroje pro připojení umožnit jim přidat instance vztahů domény.

## <a name="ToolboxDef"></a> Jak je definované sady nástrojů
 V okně Průzkumník DSL rozbalte Editor uzlů a uzlů pod ním. Obvykle se zobrazí hierarchie, která vypadá takto:

```
Editor
     Toobox Tabs
        MyDsl          //a tab
           Tools
               ExampleElement      // an element tool
               ExampleRelationship // a connection tool
```

V této části Průzkumník DSL můžete:

-   Vytvoření nových kartách. Karty definovat nadpisy oddílů v panelu nástrojů.

-   Vytvoření nových nástrojů.

-   Zkopírujte a vložte nástroje.

-   Přesunutí nástroje směrem nahoru nebo dolů v seznamu.

-   Odstraňte karty a nástroje.

> [!IMPORTANT]
> Chcete-li přidat nebo vložit položky v Průzkumníku DSL, klikněte pravým tlačítkem na nadřazený nový uzel. Například pokud chcete přidat nástroj, klikněte pravým tlačítkem na kartu a ne **nástroje** uzlu. Chcete-li přidat na kartě, klikněte pravým tlačítkem **Editor** uzlu.

**Panelu nástrojů ikonu** vlastnost každý nástroj odkazuje na soubor rastrového obrázku velikosti 16 x 16. Tyto soubory jsou obvykle uloženy v **Dsl\Resources** složky.

**Třídy** vlastnost nástroj elementu odkazuje na konkrétní doménovou třídu. Ve výchozím nastavení nástroj vytvoří instance této třídy. Ale můžete napsat kód, aby nástroj pro vytváření skupin elementy nebo elementy různých typů.

**Tvůrce připojení** vlastnost připojení nástroje odkazuje na Tvůrce připojení, která definuje, jaké typy prvků můžete připojit nástroj a jaké vztahy vytvoří mezi nimi. Tvůrci připojení jsou definované jako uzly v Průzkumníku DSL. Tvůrci připojení se vytvoří automaticky při definování vztahů mezi doménami, ale můžete napsat kód, který si je přizpůsobit.

#### <a name="to-add-a-tool-to-the-toolbox"></a>Chcete-li přidat nástroj na panelu nástrojů

1.  Obvykle vytvoříte nástroj pro element po vytvoření obrazec třídy a mapován na doménovou třídu.

     Obvykle vytvoříte konektor nástroje po vytvoření konektoru třídy a mapován na vztah odkazu.

2.  V okně Průzkumník DSL, rozbalte **Editor** uzlu a **karty panelu nástrojů** uzlu.

     Klikněte pravým tlačítkem na uzel kartu panelu nástrojů a potom klikněte na tlačítko **přidejte nový prvek nástroj** nebo **přidat nové připojení nástroje**.

3.  Nastavte **panelu nástrojů ikonu** vlastnost k odkazování na rastrový obrázek 16 x 16.

     Pokud chcete definovat nová ikona, vytvořit soubor rastrového obrázku v Průzkumníku řešení v **Dsl\Resources** složky. Soubor by měl mít následující hodnoty vlastností: **akce sestavení** = **obsahu**; **Kopírovat do výstupního adresáře** = **nekopírovat**.

4.  **Pro element nástroj:** nastavit **třídy** vlastnost nástroje k odkazování na konkrétní doménovou třídou, která je namapovaná na obrazec.

     **Pro nástroj konektor:** nastavit **Tvůrce připojení** vlastnost nástroje pro jednu z položek, které nabízí v rozevíracím seznamu. Tvůrci připojení se automaticky vytvoří při mapování spojnici na doménový vztah. Pokud jste nedávno vytvořili konektor, obvykle vyberete Tvůrce asociované připojení.

5.  K otestování DSL, stiskněte klávesu F5 nebo CTRL + F5 a v experimentální instanci sady Visual Studio, otevřete ukázkový soubor modelu. Nový nástroj by se zobrazit na panelu nástrojů. Přetáhněte do diagramu, ověřte, že vytvoří nový prvek.

     Pokud nástroj nezobrazí, zastavte experimentální Visual Studio. V Windows **Start** nabídky, spusťte **resetování Microsoft Visual Studio 2010 experimentální instanci**. Na **sestavení** nabídky, klikněte na tlačítko **znovu sestavit řešení**. Potom znovu otestujte DSL.

## <a name="customizing"></a> Přizpůsobení nástrojů elementu
 Ve výchozím nastavení nástroj vytvoří jednu instanci dané třídy, ale to se může pohybovat dvěma způsoby:

-   Definujte direktivy sloučení elementů pro jiné třídy, což jim tak, aby přijímal nové instance této třídy a umožnit jim vytvořit další odkazy, když se vytvoří nový prvek. Může například uživateli umožní vyřadit komentář na jiný element a tím vytvořit odkaz mezi těmito dvěma.

     Tyto úpravy také vliv na co se stane, když uživatel vloží nebo přetáhne a zahodí elementu.

     Další informace najdete v tématu [přizpůsobení vytvoření a přesunutí elementu](../modeling/customizing-element-creation-and-movement.md).

-   Zápis kódu pro úpravu nástroje, takže ho můžete vytvořit skupiny prvků. Nástroj je inicializován pomocí metody v ToolboxHelper.cs, které můžete přepsat. Další informace najdete v tématu [vytváření skupin z prvků z nástroje](#groups).

## <a name="groups"></a> Vytvoření skupiny prvků z nástroje
 Nástroj pro každý prvek obsahuje prototyp prvky, které se má vytvořit. Ve výchozím nastavení nástroj pro každý element vytvoří jeden element, ale je také možné vytvořit pomocí jednoho nástroje skupiny souvisejících objektů. K tomuto účelu nástroj s inicializaci <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> , který obsahuje související položky.

 Následující příklad je převzat z DSL, ve kterém je typ tranzistorové. Každý tranzistorové má tři pojmenované terminály. Nástroj elementu pro tranzistory ukládá prototypem obsahující čtyři prvků modelu a tři vztah odkazy. Když uživatel přetáhne nástroj do diagramu, prototyp vytvořena a propojí s kořenem modelu.

 Tento kód přepíše metodu, která je definována v **Dsl\GeneratedCode\ToolboxHelper.cs**.

 Další informace o přizpůsobení modelu pomocí kódu programu najdete v tématu [navigace a aktualizace modelu v programovém kódu](../modeling/navigating-and-updating-a-model-in-program-code.md).

```
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;

  public partial class CircuitsToolboxHelper
  {
    /// <summary>
    /// Toolbox initialization, called for each element tool on the toolbox.
    /// This version deals with each Component subtype separately.
    /// </summary>
    /// <param name="store"></param>
    /// <param name="domainClassId">Identifies the domain class this tool should instantiate.</param>
    /// <returns>prototype of the object or group of objects to be created by tool</returns>
    protected override ElementGroupPrototype CreateElementToolPrototype(Store store, Guid domainClassId)
    {
        if (domainClassId == Transistor.DomainClassId)
        {
            Transistor transistor = new Transistor(store);

            transistor.Base = new ComponentTerminal(store);
            transistor.Collector = new ComponentTerminal(store);
            transistor.Emitter = new ComponentTerminal(store);

            transistor.Base.Name = "base";
            transistor.Collector.Name = "collector";
            transistor.Emitter.Name = "emitter";

            // Create an ElementGroup for the Toolbox.
            ElementGroup elementGroup = new ElementGroup(store.DefaultPartition);
            elementGroup.AddGraph(transistor, true);
            // AddGraph includes the embedded parts

            return elementGroup.CreatePrototype();
        }
        else
        {
            return base.CreateElementToolPrototype(store, domainClassId);
}  }    }
```

## <a name="connections"></a> Přizpůsobení nástrojů pro připojení
 Obvykle vytvoříte nástroj pro element když vytvoříte novou třídu konektoru. Alternativně můžete použít přetížení jeden nástroj pro tím, že typy dva elementy end určit typ vztahu. Můžete například definovat jeden nástroj pro připojení, která může vytvářet vztahy osoba na osobu a vztahy osoba města.

 Připojení nástroje vyvolat tvůrci připojení. Tvůrci připojení použijte k určení, jak uživatele můžete propojit prvky ve vygenerovaném návrháři. Tvůrci připojení zadejte prvky, které lze propojit a typu odkazu, který je vytvořen mezi nimi.

 Když vytvoříte vztah odkazu mezi doménovými třídami, se automaticky vytvoří Tvůrce připojení. Tato Tvůrce připojení můžete použít při mapování nástroj pro připojení. Další informace o tom, jak vytvořit připojení nástroje najdete v tématu [konfigurace sady nástrojů](../modeling/customizing-tools-and-the-toolbox.md).

 Výchozí Tvůrce připojení můžete upravit tak, aby ho řešit jiný rozsah zdrojovými a cílovými typy a vytvářet různé typy vztahů.

 Můžete také napsat vlastní kód pro připojení počítačů při určení zdrojové a cílové třídy pro připojení, definují typ připojení, které budou nebo provádět jiné akce přidružené k vytvoření připojení.

### <a name="the-structure-of-connection-builders"></a>Struktura tvůrci připojení
 Tvůrci připojení obsahovat jednu nebo odkaz na další připojení direktivy, které určují doménový vztah a zdrojové a cílové elementy. Například v šabloně řešení tok úloh můžete zobrazit **CommentReferencesSubjectsBuilder** v **Průzkumník DSL**. Tvůrce toto připojení obsahuje jedno propojení připojit direktivu s názvem **CommentReferencesSubjects – odkazová**, která se mapuje na doménový vztah **CommentReferencesSubjects – odkazová**. Připojte tento odkaz direktiva obsahuje direktivy zdrojové role, který odkazuje na `Comment` doménové třídy a direktivy cílové role, která odkazuje na `FlowElement` doménovou třídu.

### <a name="using-connection-builders-to-restrict-source-and-target-roles"></a>Pomocí připojení počítačů k omezení zdrojové a cílové role
 Tvůrci připojení můžete omezit výskyt určitých tříd ve zdrojové role nebo cílová role vztahu danou doménu. Například můžete mít základní doménovou třídu, která má vztah domény do jiné doménové třídy, ale možná nebudete chtít všechny odvozené třídy základní třídy, která se mají stejné role v této relaci. V řešení tok úkolů jsou čtyři konkrétní doménové třídy (**StartPoint**, **koncový bod**, **MergeBranch**, a **synchronizace**), který dědí přímo z abstraktní doménová třída **FlowElement**, a dvě konkrétní doménové třídy (**úloh** a **ObjectInState**), který nepřímo dědit z něj. K dispozici je také **tok** odkaz vztahu, který přebírá **FlowElement** doménovými třídami v její zdrojová role a cílová role. Však instance **koncový bod** doménové třídy nesmí sloužit jako zdroj pro instance **tok** vztahu, ani by měla instance **StartPoint** třída být cílové instance **tok** vztah. **FlowBuilder** Tvůrce připojení má odkaz připojení direktivu s názvem **tok** , která určuje, které třídy domény můžete přehrát zdrojové role (**úloh**,  **MergeBranch**, **StartPoint**, a **synchronizace**) a které hrají roli cílový (**MergeBranch**,  **Koncový bod**, a **synchronizace**).

### <a name="connection-builders-with-multiple-link-connect-directives"></a>Tvůrci připojení s více propojení direktivy propojení
 Můžete přidat více než jedno propojení propojovací direktiva Tvůrce připojení. To vám může pomoct skrýt některých složitějších model domény od uživatelů a zachovat **nástrojů** z nepřehledný. Můžete přidat odkaz direktivy pro několik různých doménové vztahy propojení na tvůrce jedno připojení. Ale doporučujeme, abyste zkombinovali vztahy domén při vykonávání přibližně stejnou funkci.

 V řešení tok úkolů **tok** nástroj pro připojení se používá k vykreslení instance obou **tok** a **Tok_objektů** vztahy domén. **FlowBuilder** Tvůrce připojení má, navíc k **tok** bylo popsáno dříve direktiva propojení odkazů, s názvem direktivy propojení dvou odkazů **Tok_objektů**. Tyto direktivy určit, že instance **Tok_objektů** může vykreslit vztah mezi instancemi **ObjectInState** doménovou třídu nebo z instance **ObjectInState**  do instance systému **úloh**, ale není mezi dvěma instancemi **úloh**, nebo z instance **úloh** do instance **ObjectInState**. Ale instance **tok** může vykreslit vztah mezi dvěma instancemi **úloh**. Pokud kompilace a spuštění řešení tok úkolů, zobrazí se tento kreslení **tok** z instance **ObjectInState** do instance systému **úloh** vytvoří instanci **Tok_objektů**, ale vykreslování **tok** mezi dvěma instancemi **úloh** vytvoří instanci **tok**.

### <a name="custom-code-for-connection-builders"></a>Vlastní kód pro tvůrci připojení
 Existují čtyři políček v uživatelském rozhraní, které definují různé druhy přizpůsobení tvůrci připojení:

- **vlastní přijetí** zaškrtávací políčko na direktivu zdrojová nebo cílová role

- **připojit vlastní** zaškrtávací políčko na direktivu zdrojová nebo cílová role

- **používá vlastní připojit** zaškrtávací políčko pro direktivu connect

- **je vlastní** vlastnosti Tvůrce připojení

  Je nutné zadat nějaký kód programu k provedení těchto úprav. Chcete-li zjistit, jaký kód je nutné zadat, jeden z těchto polí a transformovat všechny šablony potom sestavte řešení. Zpráva o chybě dojde. Klikněte dvakrát na zprávy o chybě zobrazíte komentář, který vysvětluje, jaký kód že je nutné přidat.

> [!NOTE]
>  Chcete-li přidat vlastní kód, vytvořte definici částečné třídy v souboru kódu odděleně od kódu souborů ve složkách GeneratedCode. Abyste se vyhnuli ztrátě práce, byste neměli upravovat soubory generovaného kódu. Další informace najdete v tématu [přepisování a rozšiřování třídy generované v](../modeling/overriding-and-extending-the-generated-classes.md).

#### <a name="creating-custom-connection-code"></a>Vytváří se připojení vlastní kód
 V každé propojení propojovací direktiva, **zdrojové direktivy rolí, které** kartě definuje, jaké typy lze přetáhnout. Podobně **cílové direktivy rolí, které** definuje kartu pro jaké typy lze přetáhnout. Pro každý typ, můžete dále určit, jestli se má povolit připojení (pro tento odkaz propojovací direktiva) tak, že nastavíte **vlastní přijetí** příznak a pak zadáním zvláštní kód.

 Můžete také přizpůsobit, co se stane, když se připojení. Například lze upravit pouze tento případ, kde dochází k přetahování do nebo z určité třídy, připojte tento jeden odkaz všechny případy směrnice upravuje, nebo celé FlowBuilder Tvůrce připojení. Pro každou z těchto možností můžete nastavit vlastní příznaky požadovanou úroveň. Když Transformovat všechny šablony a opakujte pokus o sestavení řešení, chybové zprávy nasměrujeme na to, komentáře, které jsou ve vygenerovaném kódu. Tyto poznámky určují, co je třeba zadat.

 V ukázce Diagram součásti Tvůrce připojení pro připojení doménového vztahu upravit tak, aby omezení připojení, které mohou být provedeny mezi porty. Následující obrázek znázorňuje, že můžete provést připojení pouze z `OutPort` prvků, které mají `InPort` elementů, ale můžete vnořit součásti do sebe navzájem.

 **Připojení OutPort komponentu vnořené přichází do**

 ![Tvůrce připojení](../modeling/media/connectionbuilder_3.png)

 Proto můžete chtít určit, že připojení můžou pocházet z vnořené komponenty do OutPort. K určení těchto připojení, nastavíte **používá vlastní přijetí** na **InPort** typ jako zdrojová role a **OutPort** typ jako cílová role v **podrobnosti DSL**  okna, jak je znázorněno na následujících obrázcích:

 **V Průzkumníku DSL direktiva propojení odkazů**

 ![Obrázek Tvůrce připojení](../modeling/media/connectionbuilder_4a.png)

 **V okně podrobností DSL direktiva propojení odkazů**

 ![](../modeling/media/connectionbuilder_4b.png)

 Pak je nutné zadat metody ve třídě Tvůrce propojení:

```
  public partial class ConnectionBuilder
  {
    /// <summary>
    /// OK if this component has children
    /// </summary>
    private static bool CanAcceptInPortAsSource(InPort candidate)
    {
       return candidate.Component.Children.Count > 0;
    }

    /// <summary>
    /// Only if source is on parent of target.
    /// </summary>
    private static bool CanAcceptInPortAndInPortAsSourceAndTarget                (InPort sourceInPort, InPort targetInPort)
    {
      return sourceInPort.Component == targetInPort.Component.Parent;
    }
// And similar for OutPorts...
```

 Další informace o přizpůsobení modelu pomocí kódu programu najdete v tématu [navigace a aktualizace modelu v programovém kódu](../modeling/navigating-and-updating-a-model-in-program-code.md).

 Podobný kód, můžete použít třeba zabránit uživatelům ve vytváření smyčky s odkazy nadřazenosti a podřízenosti. Tato omezení jsou považovány za "pevné" omezení, protože uživatelé nelze porušují kdykoli. Můžete také vytvořit "soft" ověřovací kontroly, které uživatelé mohou dočasně obejít tak, že vytvoříte neplatná konfigurace, které nelze uložit.

### <a name="good-practice-in-defining-connection-builders"></a>Vhodné při definování tvůrci připojení
 Byste měli definovat jeden Tvůrce připojení k vytvoření různých typů vztahů pouze v případě, že se obecně týkají. V ukázce tok úloh pomocí stejné tvůrce můžete vytvářet toky mezi úkoly a také mezi úkoly a objekty. Nicméně by bylo matoucí pro vytváření vztahů mezi komentáře a úlohy pomocí stejné Tvůrce.

 Pokud definujete Tvůrce připojení pro různé typy vztahů, měli byste zajistit, nelze odpovídají více než jeden typ ze stejného páru zdrojové a cílové objektů. V opačném případě bude výsledky nepředvídatelné.

 Použití vlastního kódu pro použití "pevné" omezení, ale měli byste zvážit, jestli uživatelé by měli být schopni dočasně provádět neplatné připojení. Pokud by měly, můžete upravit omezení tak, aby se neověřuje připojení, dokud uživatelé se pokusí uložit změny.

## <a name="see-also"></a>Viz také

- [Přizpůsobení vytvoření a přesunutí elementu](../modeling/customizing-element-creation-and-movement.md)
- [Přizpůsobení chování kopírování](../modeling/customizing-copy-behavior.md)
- [Postupy: Přidání obslužné rutiny operace přetažení myší](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Navigace v modelu a aktualizace modelu v kódu programu](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Ukázka diagramy okruh DSL](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)