---
title: Přizpůsobení nástrojů a panelu nástrojů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.selectiondialog
- vs.dsltools.dsldesigner.selecticondialog
- vs.dsltools.dsldesigner.selectcursordialog
helpviewer_keywords:
- Domain-Specific Language, toolbox
ms.assetid: 2a0d03d7-ebc6-4458-b9f4-d2cb8418a62d
caps.latest.revision: 28
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 757297123bff107c28ced53a14dcdbb94ae56a87
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654917"
---
# <a name="customizing-tools-and-the-toolbox"></a>Přizpůsobení nástrojů a panelu nástrojů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Je nutné definovat položky sady nástrojů pro prvky, které chcete umožnit uživatelům přidávat do jejich modelů. Existují dva druhy nástrojů: nástroje pro prvky a nástroje pro připojení. Ve vygenerovaném návrháři může uživatel vybrat nástroj prvku pro přetahování tvarů do diagramu a může vybrat nástroj pro připojení k vykreslování propojení mezi obrazci. Obecně platí, že nástroje pro prvky umožňují uživatelům přidávat do svých modelů instance doménových tříd a nástroje pro připojení umožňují přidávat instance doménových vztahů.

 V tomto tématu:

- [Jak je definována sada nástrojů](#ToolboxDef)

- [Přizpůsobení nástrojů elementu](#customizing)

- [Vytváření skupin elementů z nástroje](#groups)

- [Přizpůsobení nástrojů pro připojení](#connections)

## <a name="ToolboxDef"></a>Jak je definována sada nástrojů
 V Průzkumníku DSL rozbalte uzel Editor a uzly pod ním. Obvykle se zobrazí hierarchie podobná této:

```

Editor
     Toobox Tabs
        MyDsl          //a tab
           Tools
               ExampleElement      // an element tool
               ExampleRelationship // a connection tool

```

 V této části Průzkumníka DSL můžete:

- Vytvořte nové karty. Karty definují záhlaví oddílů v sadě nástrojů.

- Vytvořte nové nástroje.

- Nástroje pro kopírování a vkládání.

- Přesunutí nástrojů v seznamu nahoru nebo dolů.

- Odstraní karty a nástroje.

> [!IMPORTANT]
> Chcete-li přidat nebo vložit položky v Průzkumníku DSL, klikněte pravým tlačítkem myši na prarodič nového uzlu. Chcete-li například přidat nástroj, klikněte pravým tlačítkem myši na kartu a nikoli na uzel **nástroje** . Chcete-li přidat kartu, klikněte pravým tlačítkem myši na uzel **editoru** .

 Vlastnost **ikony panelu nástrojů** každého nástroje odkazuje na soubor s obrázkem 16x16. Tyto soubory jsou obvykle uchovávány ve složce **Dsl\Resources** .

 Vlastnost **Class** nástroje elementu odkazuje na konkrétní doménovou třídu. Ve výchozím nastavení nástroj vytvoří instance této třídy. Můžete však napsat kód, který má nástroj vytvořit skupiny prvků, nebo prvky různých typů.

 Vlastnost **Tvůrce připojení** nástroje pro připojení odkazuje na Tvůrce připojení, který definuje typy prvků, které může nástroj připojit, a vztahy mezi nimi vytvořenými. Tvůrci připojení jsou v Průzkumníkovi DSL definováni jako uzly. Tvůrci připojení se vytvoří automaticky při definování doménových vztahů, ale můžete napsat kód, který je přizpůsobí.

#### <a name="to-add-a-tool-to-the-toolbox"></a>Přidání nástroje do sady nástrojů

1. Obvykle vytvoříte nástroj element po vytvoření třídy Shape a namapujete ji na doménovou třídu.

     Nástroj spojnice obvykle vytvoříte poté, co vytvoříte třídu konektoru a namapujete ji na referenční relaci.

2. V Průzkumníku DSL rozbalte uzel **Editor** a uzel **karty panelu nástrojů** .

     Klikněte pravým tlačítkem myši na uzel karta panelu nástrojů a potom klikněte na tlačítko **Přidat nový nástroj prvku** nebo **Přidat nový nástroj připojení**.

3. Nastavte vlastnost **Icon panelu nástrojů** tak, aby odkazovala na obrázek 16x16.

     Pokud chcete definovat novou ikonu, vytvořte v Průzkumník řešení ve složce **Dsl\Resources** rastrový soubor. Soubor by měl obsahovat následující hodnoty vlastností: **Akce sestavení**  = **obsah**; **Kopírovat do výstupního adresáře**  = **Nekopírovat**.

4. **Pro nástroj elementu:** Nastavte vlastnost **Class** nástroje tak, aby odkazovala na konkrétní doménovou třídu, která je namapována na tvar.

     **Pro nástroj konektoru:** Nastavte vlastnost **Tvůrce připojení** nástroje na jednu z položek, které jsou nabízeny v rozevíracím seznamu. Tvůrci připojení se automaticky vytvoří při mapování spojnice na doménový vztah. Pokud jste v poslední době vytvořili konektor, obvykle byste vybrali přidruženého Tvůrce připojení.

5. Chcete-li otestovat DSL, stiskněte klávesu F5 nebo CTRL + F5 a v experimentální instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] otevřete vzorový soubor modelu. Nový nástroj by se měl zobrazit v sadě nástrojů. Přetáhněte ho do diagramu, abyste ověřili, že vytvoří nový prvek.

     Pokud se nástroj nezobrazí, zastavte experimentální [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. V nabídce **Start** systému Windows spusťte **resetování experimentální instance Microsoft Visual Studio 2010**. V nabídce**sestavení** [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] klikněte na **znovu sestavit řešení**. Pak zkuste DSL znovu otestovat.

## <a name="customizing"></a>Přizpůsobení nástrojů elementů
 Ve výchozím nastavení nástroj vytvoří jednu instanci zadané třídy, ale můžete se změnit dvěma způsoby:

- Definovat direktivy sloučení elementů na jiných třídách, povolit jim přijímat nové instance této třídy a povolit jim vytváření dalších odkazů při vytvoření nového prvku. Můžete například uživateli dovolit, aby vynechal komentář k jinému prvku, a vytvoří odkaz propojení mezi těmito dvěma.

     Tato přizpůsobení mají vliv také na to, co se stane, když uživatel vloží nebo přetáhne a uvolní prvek.

     Další informace naleznete v tématu [přizpůsobení vytváření a přesunu prvku](../modeling/customizing-element-creation-and-movement.md).

- Napište kód pro přizpůsobení nástroje tak, aby mohl vytvořit skupiny prvků. Nástroj je inicializován metodami v ToolboxHelper.cs, které lze přepsat. Další informace naleznete v tématu [vytváření skupin prvků z nástroje](#groups).

## <a name="groups"></a>Vytváření skupin elementů z nástroje
 Každý nástroj elementu obsahuje prototyp prvků, které by měl vytvořit. Ve výchozím nastavení každý nástroj elementu vytvoří jeden prvek, ale je také možné vytvořit skupinu souvisejících objektů s jedním nástrojem. K tomu je třeba nástroj inicializovat pomocí <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype>, který obsahuje související položky.

 Následující příklad je proveden z DSL, v němž je typu Transistor. Každý Transistor má tři pojmenované terminály. Nástroj elementu pro Transistors ukládá prototyp obsahující čtyři prvky modelu a tři odkazy na relace. Když uživatel přetáhne nástroj do diagramu, vytvoří se prototyp instance a propojí se s kořenem modelu.

 Tento kód přepisuje metodu, která je definována v **Dsl\GeneratedCode\ToolboxHelper.cs**.

 Další informace o přizpůsobení modelu pomocí kódu programu naleznete v tématu [navigace a aktualizace modelu v kódu programu](../modeling/navigating-and-updating-a-model-in-program-code.md).

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

## <a name="connections"></a>Přizpůsobení nástrojů pro připojení
 Obvykle vytvoříte nástroj prvku při vytváření nové třídy konektoru. Alternativně můžete přetížit jeden nástroj tím, že umožníte typům obou konců určit typ relace. Můžete například definovat jeden nástroj pro připojení, který by mohl vytvořit vztahy mezi osobami a pracovní město.

 Nástroje pro připojení vyvolávají tvůrci připojení. Pomocí tvůrců připojení určete, jak mohou uživatelé propojit prvky ve vygenerovaném návrháři. Tvůrci připojení určují prvky, které mohou být propojeny, a druh propojení, které je mezi nimi vytvořeno.

 Při vytváření referenčního vztahu mezi doménovými třídami se automaticky vytvoří Tvůrce připojení. Pomocí tohoto Tvůrce připojení můžete namapovat nástroj připojení. Další informace o tom, jak vytvořit nástroje pro připojení, najdete v tématu [Konfigurace sady nástrojů](../modeling/customizing-tools-and-the-toolbox.md).

 Výchozí Tvůrce připojení můžete upravit tak, aby mohl pracovat s různými rozsahy zdrojového a cílového typu, a vytvořit různé typy vztahů.

 Můžete také napsat vlastní kód pro tvůrci připojení pro určení zdrojové a cílové třídy pro připojení, definovat typ připojení, který má být vytvořen, a provést další akce spojené s vytvořením připojení.

### <a name="the-structure-of-connection-builders"></a>Struktura tvůrců připojení
 Tvůrci připojení obsahují jednu nebo více direktiv propojení odkazů, které určují vztah domény a zdrojové a cílové prvky. Například v šabloně řešení toku úloh můžete zobrazit **CommentReferencesSubjectsBuilder** v **Průzkumníku DSL**. Tento Tvůrce připojení obsahuje jednu direktivu připojení propojení s názvem **CommentReferencesSubjects**, která je namapovaná na **CommentReferencesSubjects**doménového vztahu. Tato direktiva propojení odkazů obsahuje direktivu zdrojové role, která odkazuje na doménovou třídu `Comment` a cílovou direktivu role odkazující na `FlowElement` doménovou třídu.

### <a name="using-connection-builders-to-restrict-source-and-target-roles"></a>Použití tvůrců připojení k omezení zdrojových a cílových rolí
 Tvůrci připojení můžete použít k omezení výskytu určitých tříd buď ve zdrojové roli, nebo v cílové roli daného doménového vztahu. Například můžete mít třídu základní domény, která má doménový vztah k jiné doménové třídě, ale nechcete, aby všechny odvozené třídy základní třídy měly stejné role v daném vztahu. V řešení flow je k dispozici čtyři konkrétní třídy domény (**StartPoint**, **Endpoint**, **MergeBranch**a **Synchronization**), které dědí přímo z abstraktní třídy domény **FlowElement**a dvě konkrétní. doménové třídy (**Task** a **ObjectInState**), které jsou z ní nepřímo děděny. Existuje také vztah odkazu na **tok** , který převezme **FlowElement** doménové třídy v jeho zdrojové roli a cílové roli. Instance třídy domény **koncového bodu** by však neměla být zdrojem instance vztahu **toku** , ani by instance třídy **StartPoint** měla být cílem instance vztahu **toku** . Tvůrce připojení **FlowBuilder** má direktivu Connect Link s názvem **Flow** , která určuje, které třídy domény mohou hrát zdrojovou roli (**Task**, **MergeBranch**, **StartPoint**a **Synchronization**) a které může hrát cílovou roli (**MergeBranch**, **Endpoint**a **Synchronization**).

### <a name="connection-builders-with-multiple-link-connect-directives"></a>Tvůrci připojení s více direktivami spojení odkazů
 Do Tvůrce připojení můžete přidat více než jednu direktivu připojení propojení. To vám může pomáhat s skrytím některých složitosti doménového modelu od uživatelů a zabránit tomu, aby se **Sada nástrojů** dostala příliš zbytečně. Do jednoho Tvůrce připojení můžete přidat direktivy propojení odkazů pro několik různých doménových vztahů. Při provádění přibližně stejné funkce byste ale měli kombinovat relace domény.

 V řešení toku úloh se nástroj pro připojení **Flow** používá k nakreslení instancí vztahů mezi **ObjectFlow** a doménami. Tvůrce připojení **FlowBuilder** kromě výše popsané směrnice pro propojení **toků** , která je popsaná výše, obsahuje dvě direktivy Connect Link s názvem **ObjectFlow**. Tyto direktivy určují, že instance vztahu **ObjectFlow** může být vykreslená mezi instancemi doménové třídy **ObjectInState** nebo z instance **ObjectInState** do instance **úlohy**, ale ne mezi dvěma. instance **úkolu**nebo z instance **úkolu** do instance **ObjectInState**. Nicméně instance vztahu **toku** může být vykreslena mezi dvěma instancemi **úkolu**. Pokud zkompilujete a spustíte řešení toku úkolů, vidíte, že vykreslení **toku** z instance **ObjectInState** do instance **úlohy** vytvoří instanci **ObjectFlow**, ale vykreslí **tok** mezi dvěma instancemi. **úlohy** vytvoří instanci **toku**.

### <a name="custom-code-for-connection-builders"></a>Vlastní kód pro sestavování připojení
 V uživatelském rozhraní jsou čtyři zaškrtávací políčka, která definují různé typy přizpůsobení tvůrců připojení:

- zaškrtávací políčko **vlastní přijetí** u zdrojové nebo cílové direktivy role

- zaškrtávací políčko **vlastní připojení** pro direktivu zdrojové nebo cílové role

- zaškrtávací políčko **používá vlastní připojení** u direktivy Connect

- vlastnost **je vlastní** Tvůrce připojení.

  K provedení těchto úprav musíte zadat nějaký kód programu. Chcete-li zjistit, jaký kód je třeba dodat, zaškrtněte jedno z těchto políček, klikněte na možnost transformovat všechny šablony a poté Sestavte řešení. Výsledkem bude zpráva o chybě. Dvojitým kliknutím na zprávu o chybách se zobrazí komentář s vysvětlením, jaký kód byste měli přidat.

> [!NOTE]
> Chcete-li přidat vlastní kód, vytvořte definici částečné třídy v souboru kódu odděleně od souborů kódu ve složkách GeneratedCode. Aby nedošlo ke ztrátě vaší práce, neměli byste upravovat vygenerované soubory kódu. Další informace naleznete v tématu [přepsání a rozšíření vygenerovaných tříd](../modeling/overriding-and-extending-the-generated-classes.md).

#### <a name="creating-custom-connection-code"></a>Vytváření vlastního kódu připojení
 V každé direktivě propojení odkazů je karta **direktiva zdrojové role** definována z typů, které můžete přetáhnout. Podobně karta **direktivy cílové role** definuje, které typy lze přetáhnout. Pro každý typ můžete dále určit, jestli se má připojení (pro tuto direktivu propojení) použít, nastavením příznaku **přijmout** a následným zadáním dalšího kódu.

 Můžete také přizpůsobit, co se stane při navázání spojení. Například můžete přizpůsobit pouze případ, kde dojde k přetahování na nebo z konkrétní třídy, všechny případy, kdy jedna linka propojení odkazů řídí nebo je celá FlowBuilder Tvůrce připojení. Pro každou z těchto možností můžete nastavit vlastní příznaky na příslušné úrovni. Při transformaci všech šablon a pokusu o sestavení řešení, chybové zprávy vás přesměrují na komentáře, které jsou ve vygenerovaném kódu. Tyto komentáře identifikují, co je třeba zadat.

 V ukázce diagramu komponent je Tvůrce připojení pro relaci připojení domény přizpůsobený tak, aby se omezilo připojení, která je možné mezi porty vytvořit. Následující obrázek ukazuje, že je možné vytvořit připojení pouze z prvků `OutPort` do `InPort` prvků, ale součásti lze vnořit do sebe.

 **Připojení, které přichází do externího portu, z vnořené komponenty**

 ![Tvůrce připojení](../modeling/media/connectionbuilder-3.png "ConnectionBuilder_3")

 Proto možná budete chtít určit, že připojení může pocházet z vnořené komponenty do přípravku. Chcete-li určit takové připojení, nastavte v okně **Podrobnosti DSL** jako cílová role jako cílovou roli **vlastní přijetí** jako zdrojovou roli a jako cílovou **roli typ** **portu** jako cíl, jak je znázorněno na následujících obrázcích:

 **Propojit direktivu Connect v Průzkumníkovi DSL**

 ![Obrázek Tvůrce připojení](../modeling/media/connectionbuilder-4a.png "ConnectionBuilder_4a")

 **Propojovací direktiva propojení v okně Podrobnosti DSL**

 ![](../modeling/media/connectionbuilder-4b.png "ConnectionBuilder_4b")

 Pak musíte zadat metody ve třídě tvůrci propojení:

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
    private static bool CanAcceptInPortAndInPortAsSourceAndTarget                (InPort sourceInPort, InPort targetInPort)
    {
      return sourceInPort.Component == targetInPort.Component.Parent;
    }
// And similar for OutPorts…
```

 Další informace o přizpůsobení modelu pomocí kódu programu naleznete v tématu [navigace a aktualizace modelu v kódu programu](../modeling/navigating-and-updating-a-model-in-program-code.md).

 Podobný kód můžete použít například k tomu, abyste uživatelům zabránili ve vytváření smyček s odkazy nadřízený-podřízený. Tato omezení se považují za omezení typu "pevná", protože uživatelé je nemohou kdykoli narušovat. Můžete také vytvořit kontrolní kontroly podmíněného ověřování, které mohou uživatelé dočasně obejít vytvořením neplatných konfigurací, které nelze uložit.

### <a name="good-practice-in-defining-connection-builders"></a>Dobrý postup při definování tvůrců připojení
 Je nutné definovat jednoho Tvůrce připojení, aby bylo možné vytvořit různé typy vztahů pouze v případě, že jsou v koncepční souvislosti. V ukázce toku úlohy můžete použít stejného tvůrce pro vytváření toků mezi úkoly a také mezi úkoly a objekty. Je ale matoucí použít stejný Tvůrce k vytváření vztahů mezi komentáři a úkoly.

 Pokud definujete Tvůrce připojení pro více typů vztahů, měli byste se ujistit, že se nemůže shodovat s více než jedním typem ze stejné dvojice zdrojového a cílového objektu. V opačném případě nebudou výsledky předvídatelné.

 Pomocí vlastního kódu můžete použít omezení typu "Hard", ale měli byste zvážit, zda by uživatelé měli být schopni dočasně vytvořit neplatná připojení. Pokud by měly, můžete tato omezení upravit tak, aby se neověřilo, dokud se uživatelé nepokusí Uložit změny.

## <a name="see-also"></a>Viz také
 [Přizpůsobení vytváření a přesunu prvků](../modeling/customizing-element-creation-and-movement.md) [přizpůsobení chování kopírování](../modeling/customizing-copy-behavior.md) [: Přidání obslužné rutiny přetažení myší](../modeling/how-to-add-a-drag-and-drop-handler.md) [procházení a aktualizace modelu v diagramech programového kódu](../modeling/navigating-and-updating-a-model-in-program-code.md) [Ukázka DSL](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)
