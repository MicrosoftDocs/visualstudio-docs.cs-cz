---
title: Přizpůsobení nástrojů a panelu nástrojů
description: Zjistěte, jak je nutné definovat položky sady nástrojů pro prvky, které chcete uživatelům nechat přidat do svých modelů.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.dsldesigner.selectiondialog
- vs.dsltools.dsldesigner.selecticondialog
- vs.dsltools.dsldesigner.selectcursordialog
helpviewer_keywords:
- Domain-Specific Language, toolbox
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 956955a9c2feb9982bee0101965336be2ca29ab7
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385809"
---
# <a name="customizing-tools-and-the-toolbox"></a>Přizpůsobení nástrojů a panelu nástrojů

Musíte definovat položky sady nástrojů pro prvky, které chcete uživatelům nechat přidat do svých modelů. Existují dva druhy nástrojů: nástroje elementů a nástroje pro připojení. Ve vygenerované návrháři může uživatel vybrat nástroj prvku pro přetažení tvarů do diagramu a výběrem nástroje pro připojení nakreslit propojení mezi tvary. Obecně platí, že nástroje elementů umožňují uživatelům přidávat do svých modelů instance tříd domén a nástroje pro připojení umožňují přidávat instance vztahů mezi doménami.

## <a name="how-the-toolbox-is-defined"></a><a name="ToolboxDef"></a> Jak je sada nástrojů definována
 V Průzkumníku DSL rozbalte uzel Editor a pod ním uzly. Obvykle se zobrazí hierarchie, která se podobá této:

```
Editor
     Toobox Tabs
        MyDsl          //a tab
           Tools
               ExampleElement      // an element tool
               ExampleRelationship // a connection tool
```

V této části průzkumníka DSL můžete:

- Vytvořte nové karty. Karty definují záhlaví oddílu v sadě nástrojů.

- Vytvořte nové nástroje.

- Nástroje pro kopírování a vkládání.

- Přesuňte nástroje v seznamu nahoru nebo dolů.

- Odstraňte karty a nástroje.

> [!IMPORTANT]
> Pokud chcete přidat nebo vložit položky v průzkumníku DSL, klikněte pravým tlačítkem myši na ikonu nového uzlu. Pokud například chcete přidat nástroj, klikněte pravým tlačítkem na kartu, a ne na **uzel** Nástroje. Pokud chcete přidat kartu, klikněte pravým tlačítkem na **uzel Editor.**

Vlastnost **Ikona panelu** nástrojů každého nástroje odkazuje na rastrový soubor 16x16. Tyto soubory jsou obvykle uloženy ve **složce Dsl\Resources.**

Vlastnost **Class** nástroje prvku odkazuje na konkrétní třídu domény. Ve výchozím nastavení nástroj vytvoří instance této třídy. Můžete ale napsat kód, který nástroj vytvoří skupiny prvků nebo prvky různých typů.

Vlastnost **Tvůrce připojení** nástroje pro připojení odkazuje na tvůrce připojení, který definuje, jaké typy prvků může nástroj připojit a jaké relace mezi nimi vytváří. Tvůrci připojení jsou definováni jako uzly v průzkumníku DSL. Tvůrci připojení se vytvářejí automaticky při definování vztahů mezi doménami, ale můžete napsat kód pro jejich přizpůsobení.

#### <a name="to-add-a-tool-to-the-toolbox"></a>Přidání nástroje do panelu nástrojů

1. Nástroj elementu obvykle vytvoříte po vytvoření třídy obrazce a namapování na třídu domény.

     Nástroj konektoru obvykle vytvoříte po vytvoření třídy konektoru a namapování na referenční relaci.

2. V Průzkumníku DSL rozbalte **uzel Editor** a uzel **Karty panelu** nástrojů.

     Klikněte pravým tlačítkem na uzel karty panelu nástrojů a potom klikněte na **Přidat nový nástroj elementu** nebo **Přidat nový nástroj pro připojení**.

3. Nastavte **vlastnost Ikona panelu** nástrojů tak, aby odkazovat na rastrový obrázek o 16 × 16.

     Pokud chcete definovat novou ikonu, vytvořte v souboru bitmapy Průzkumník řešení ve složce **Dsl\Resources.** Soubor by měl mít následující hodnoty vlastností: **Obsah akce**  =  **sestavení**; **Kopírování do výstupního adresáře**  =  **Nekopírujte .**

4. **Nástroj elementu:** Nastavte **vlastnost Class** nástroje tak, aby odkazoval na konkrétní třídu domény, která je namapovaná na tvar.

     **Nástroj konektoru:** Nastavte **vlastnost Tvůrce** připojení nástroje na jednu z položek, které jsou nabízeny v rozevíracím seznamu. Tvůrci připojení se automaticky vytvoří při mapování konektoru na vztah domény. Pokud jste nedávno vytvořili konektor, normálně byste vytvořili přidruženého tvůrce připojení.

5. Pokud chcete dsl otestovat, stiskněte F5 nebo CTRL+F5 a v experimentální instanci Visual Studio otevřete soubor ukázkového modelu. Nový nástroj by se měl zobrazit na panelu nástrojů. Přetáhněte ho do diagramu a ověřte, že vytvoří nový prvek.

     Pokud se nástroj nezobrazí, zastavte experimentální Visual Studio. V nabídce **Start** ve Windows spusťte **resetování experimentální instance Microsoft Visual Studio 2010.** V nabídce **Sestavení** klikněte na **Znovu sestavit řešení.** Pak znovu otestujte DSL.

## <a name="customizing-element-tools"></a><a name="customizing"></a> Přizpůsobení nástrojů elementu
 Ve výchozím nastavení nástroj vytvoří jednu instanci zadané třídy, ale můžete to změnit dvěma způsoby:

- Definujte direktivy sloučení elementů u jiných tříd, které jim umožňují přijímat nové instance této třídy a umožnit jim vytvářet další odkazy při vytvoření nového prvku. Uživateli můžete například umožnit, aby přetál komentář na jiný prvek a vytvořil odkazový odkaz mezi těmito dvěma prvky.

     Tato přizpůsobení mají také vliv na to, co se stane, když uživatel vloží nebo přetáhne prvek.

     Další informace najdete v tématu [Přizpůsobení vytváření a přesouvání elementů.](../modeling/customizing-element-creation-and-movement.md)

- Napište kód pro přizpůsobení nástroje tak, aby mohl vytvářet skupiny prvků. Nástroj je inicializován metodami v souboru ToolboxHelper.cs, který lze přepsat. Další informace najdete v tématu [Vytváření skupin elementů z nástroje](#groups).

## <a name="creating-groups-of-elements-from-a-tool"></a><a name="groups"></a> Vytváření skupin elementů z nástroje
 Každý nástroj elementu obsahuje prototyp prvků, které by měl vytvořit. Ve výchozím nastavení každý nástroj prvku vytvoří jeden prvek, ale pomocí jednoho nástroje je také možné vytvořit skupinu souvisejících objektů. Chcete-li to provést, inicializovat nástroj s <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> objektem , který obsahuje související položky.

 Následující příklad je převzat z DSL, ve kterém je typ Tranzistor. Každý tranzistor má tři pojmenované Terminály. Nástroj elementu pro tranzistory ukládá prototyp obsahující čtyři prvky modelu a tři propojení vztahů. Když uživatel nástroj přetáhne do diagramu, vytvoří se instance prototypu a vytvoří se propojení s kořenem modelu.

 Tento kód přepíše metodu definovanou v **souboru Dsl\GeneratedCode\ToolboxHelper.cs**.

 Další informace o přizpůsobení modelu pomocí programového kódu najdete v tématu Navigace a aktualizace [modelu v programovém kódu](../modeling/navigating-and-updating-a-model-in-program-code.md).

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

## <a name="customizing-connection-tools"></a><a name="connections"></a> Přizpůsobení nástrojů pro připojení
 Při vytváření nové třídy konektoru obvykle vytvoříte nástroj elementu. Alternativně můžete jeden nástroj přetížit tím, že umožníte typům obou konců určit typ relace. Můžete například definovat jeden nástroj pro připojení, který by mohl vytvořit Person-Person a Person-Town relace.

 Nástroje pro připojení vyvolané tvůrci připojení. Pomocí tvůrců připojení můžete určit, jak mohou uživatelé propojit prvky ve vygenerované návrháři. Tvůrci připojení určují prvky, které mohou být propojeny, a typ propojení, které je mezi nimi vytvořeno.

 Při vytváření referenční relace mezi třídami domény se automaticky vytvoří tvůrce připojení. Tohoto tvůrce připojení můžete použít při mapování nástroje pro připojení. Další informace o tom, jak vytvořit nástroje pro připojení, najdete v [tématu Konfigurace sady nástrojů](../modeling/customizing-tools-and-the-toolbox.md).

 Můžete upravit výchozího tvůrce připojení tak, aby mohl řešit jiný rozsah zdrojových a cílových typů a vytvářet různé typy vztahů.

 Můžete také napsat vlastní kód pro tvůrce připojení k určení zdrojových a cílových tříd pro připojení, definovat typ připojení, které se má vytvořit, a provádět další akce spojené s vytvořením připojení.

### <a name="the-structure-of-connection-builders"></a>Struktura tvůrců připojení
 Tvůrci připojení obsahují jednu nebo více direktiv připojení propojení, které určují vztah domény a zdrojové a cílové elementy. Například v šabloně řešení Tok úloh uvidíte **CommentReferencesSubjectsBuilder** v **Průzkumníku DSL.** Tento tvůrce připojení obsahuje jednu direktivu link connect s názvem **CommentReferencesSubjects**, která je namapovaná na vztah domény **CommentReferencesSubjects**. Tato direktiva propojení connect obsahuje direktivu zdrojové role, která odkazuje na třídu domény, a cílovou direktivu role, která odkazuje `Comment` na `FlowElement` třídu domény.

### <a name="using-connection-builders-to-restrict-source-and-target-roles"></a>Použití tvůrců připojení k omezení zdrojových a cílových rolí
 Pomocí tvůrců připojení můžete omezit výskyt určitých tříd ve zdrojové roli nebo cílové roli daného vztahu domény. Můžete mít například základní třídu domény, která má vztah mezi doménou a jinou doménovou třídou, ale možná nechcete, aby všechny odvozené třídy základní třídy v tomto vztahu měli stejné role. V řešení toku úloh existují čtyři konkrétní třídy domény (**StartPoint**, **EndPoint**, **MergeBranch** a **Synchronization**), které dědí přímo z abstraktní třídy domény **FlowElement** a dvě konkrétní třídy domény (**Task** a **ObjectInState**), které z něj dědí nepřímo. Existuje také odkazový **vztah toku,** který přebírá třídy domény **FlowElement** ve své zdrojové i cílové roli. Instance třídy domény **EndPoint** by však neměla být zdrojem instance relace **toku** a instance třídy **StartPoint** by neměla být cílem instance relace **toku.** Tvůrce **připojení FlowBuilder** má direktivu propojení connect s názvem **Flow,** která určuje, které třídy domény mohou hrát zdrojovou roli (**Úloha**, **MergeBranch**, **StartPoint** a **Synchronizace**) a které mohou hrát cílovou roli(**MergeBranch**, **Koncový** bod a **Synchronizace**).

### <a name="connection-builders-with-multiple-link-connect-directives"></a>Tvůrci připojení s více direktivami propojení
 Do tvůrce připojení můžete přidat více než jednu direktivu link connect. To vám pomůže skrýt některé složitosti doménového modelu před uživateli a zabránit tomu, aby sada **nástrojů** byla příliš zatřitelná. K jednomu tvůrci připojení můžete přidat direktivy propojení pro několik různých vztahů mezi doménami. Relace domény byste však měli kombinovat, pokud provádějí přibližně stejnou funkci.

 V řešení Tok úloh se nástroj pro připojení **toku** používá k kreslení instancí vztahů mezi doménami **Tok** i **Tok** objektů. Tvůrce **připojení FlowBuilder** má kromě direktivy připojení propojení **toku** popsané výše také dvě direktivy připojení propojení s názvem **ObjectFlow**. Tyto direktivy určují, že instance vztahu **ObjectFlow** může být nakreslena mezi instancemi třídy domény **ObjectInState** nebo z instance **ObjectInState** do instance úkolu **,** ale ne mezi dvěma instancemi úkolu **nebo** z instance **Task** do instance **ObjectInState**. Mezi dvěma instancemi úlohy **však lze** vykreslit instanci vztahu **toku.** Při kompilaci **a** spuštění řešení toku úloh  uvidíte, že při kreslení toku z instance **ObjectInState** do instance úlohy  se vytvoří instance  **toku** objektů , ale při kreslení toku mezi dvěma instancemi úlohy se vytvoří instance **toku**.

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

 V ukázce diagramu komponent je Tvůrce připojení pro relaci připojení domény přizpůsobený tak, aby se omezilo připojení, která je možné mezi porty vytvořit. Následující obrázek ukazuje, že je možné vytvořit připojení pouze z `OutPort` prvků k `InPort` prvkům, ale je možné vnořit komponenty do sebe navzájem.

 **Připojení, které přichází do externího portu, z vnořené komponenty**

 ![Tvůrce připojení](../modeling/media/connectionbuilder_3.png)

 Proto možná budete chtít určit, že připojení může pocházet z vnořené komponenty do přípravku. Chcete-li určit takové připojení, nastavte v okně **Podrobnosti DSL** jako cílová role jako cílovou roli **vlastní přijetí** jako zdrojovou roli a jako cílovou **roli typ** **portu** jako cíl, jak je znázorněno na následujících obrázcích:

 **Propojit direktivu Connect v Průzkumníkovi DSL**

 ![Obrázek Tvůrce připojení](../modeling/media/connectionbuilder_4a.png)

 **Propojovací direktiva propojení v okně Podrobnosti DSL**

 ![Propojovací direktiva propojení v okně Podrobnosti DSL](../modeling/media/connectionbuilder_4b.png)

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
    private static bool CanAcceptInPortAndInPortAsSourceAndTarget                (InPort sourceInPort, InPort targetInPort)
    {
      return sourceInPort.Component == targetInPort.Component.Parent;
    }
// And similar for OutPorts...
```

 Další informace o přizpůsobení modelu pomocí kódu programu naleznete v tématu [navigace a aktualizace modelu v kódu programu](../modeling/navigating-and-updating-a-model-in-program-code.md).

 Podobný kód můžete použít například k tomu, abyste uživatelům zabránili ve vytváření smyček s odkazy nadřízený-podřízený. Tato omezení se považují za omezení typu "pevná", protože uživatelé je nemohou kdykoli narušovat. Můžete také vytvořit kontrolní kontroly podmíněného ověřování, které mohou uživatelé dočasně obejít vytvořením neplatných konfigurací, které nelze uložit.

### <a name="good-practice-in-defining-connection-builders"></a>Dobrý postup při definování tvůrců připojení
 Je nutné definovat jednoho Tvůrce připojení, aby bylo možné vytvořit různé typy vztahů pouze v případě, že jsou v koncepční souvislosti. V ukázce toku úlohy můžete použít stejného tvůrce pro vytváření toků mezi úkoly a také mezi úkoly a objekty. Je ale matoucí použít stejný Tvůrce k vytváření vztahů mezi komentáři a úkoly.

 Pokud definujete Tvůrce připojení pro více typů vztahů, měli byste se ujistit, že se nemůže shodovat s více než jedním typem ze stejné dvojice zdrojového a cílového objektu. V opačném případě nebudou výsledky předvídatelné.

 Pomocí vlastního kódu můžete použít omezení typu "Hard", ale měli byste zvážit, zda by uživatelé měli být schopni dočasně vytvořit neplatná připojení. Pokud by měly, můžete tato omezení upravit tak, aby se neověřilo, dokud se uživatelé nepokusí Uložit změny.

## <a name="see-also"></a>Viz také

- [Přizpůsobení vytvoření a přesunutí elementu](../modeling/customizing-element-creation-and-movement.md)
- [Přizpůsobení chování kopírování](../modeling/customizing-copy-behavior.md)
- [Postupy: Přidání obslužné rutiny operace přetažení myší](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Navigace v modelu a aktualizace modelu v kódu programu](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Ukázka DSL diagramů okruhů](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)
