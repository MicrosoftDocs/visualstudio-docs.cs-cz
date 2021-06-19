---
title: Přizpůsobení vytvoření a přesunutí elementu
description: Naučte se, jak můžete dovolit přetáhnout element na jiný, a to buď ze sady nástrojů, nebo v operaci vložení nebo přesunutí.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.dsldesigner.elementmergedirective
helpviewer_keywords:
- Domain-Specific Language, element merge directives
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 42339c532db3442d5fb5c5da3b51d94801a0907d
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389394"
---
# <a name="customizing-element-creation-and-movement"></a>Přizpůsobení vytvoření a přesunutí elementu

Můžete určit, že se má element přetáhnout na jiný, a to buď z panelu nástrojů, nebo v operaci vložení nebo přesunutí. Přesunuté prvky lze spojit s cílovými prvky pomocí zadaných relací.

Direktiva sloučení elementů (EMD) určuje, co se stane, když se jeden prvek modelu *sloučí* do jiného elementu modelu. Kdy k tomu dochází:

- Uživatel je přetažen z panelu nástrojů na diagram nebo tvar.

- Uživatel vytvoří prvek pomocí nabídky Přidat v Průzkumníku nebo v obrazci oddílu.

- Uživatel přesune položku z jedné dráhy do druhé.

- Uživatel vloží element.

- Kód programu volá direktivu sloučení elementů.

I když se může stát, že se operace vytvoření liší od operací kopírování, ve skutečnosti fungují stejným způsobem. Při přidání prvku, například ze sady nástrojů, je jeho prototyp replikován. Prototyp je sloučen do modelu stejným způsobem jako prvky, které byly zkopírovány z jiné části modelu.

Zodpovědnost za EMD je rozhodování o tom, jakým způsobem by měl být objekt nebo skupina objektů sloučen do konkrétního umístění v modelu. Konkrétně rozhoduje o tom, jaké relace by se měly vytvořit tak, aby sloučily skupinu do modelu. Můžete ho také přizpůsobit pro nastavení vlastností a vytváření dalších objektů.

![Diagram znázorňující před a po zobrazení stromové struktury prvků a jejich referenčních vztahů, pokud E M D Určuje, jak je přidán nový prvek.](../modeling/media/dsl-emd_merge.png)

EMD se generuje automaticky při definování vztahu vložení. Tato výchozí EMD vytvoří instanci vztahu, když uživatelé přidají k nadřazenému objektu nové podřízené instance. Můžete upravit tyto výchozí EMDs, například přidáním vlastního kódu.

Do definice DSL můžete také přidat vlastní EMDs, aby uživatelé mohli přetahovat nebo vkládat různé kombinace sloučených a přijímacích tříd.

## <a name="defining-an-element-merge-directive"></a>Definování direktivy sloučení elementů

Do doménových tříd, doménových vztahů, obrazců, konektorů a diagramů můžete přidat direktivy sloučení elementů. Můžete je přidat nebo najít v Průzkumníkovi DSL pod přijímající doménovou třídou. Přijímací třída je doménová třída elementu, který je již v modelu, a na který bude nový nebo zkopírovaný prvek sloučen.

![Snímek obrazovky s Průzkumníkem DSL ukazující možnost přidání E-M s ExampleElement vybranými jako indexovací třídu a zaškrtnuté políčko platí pro podtřídy.](../modeling/media/dsl-emd_details.png)

**Třída indexování** je doménová třída prvků, kterou lze sloučit do členů přijímací třídy. Instance podtříd třídy indexování budou také sloučeny tímto EMD, pokud není nastavena hodnota **použít na podtřídy** na false.

Existují dva druhy direktiv sloučení:

- Direktiva **sloučení procesu** určuje vztahy, podle kterých by měl být nový prvek propojen do stromu.

- Direktiva **pro přesměrování sloučení** přesměruje nový element na jiný přijímací element, obvykle nadřazený.

Do direktiv sloučení můžete přidat vlastní kód:

- Sada **používá vlastní přijetí** pro přidání vlastního kódu k určení, zda má být konkrétní instance elementu index sloučena do cílového prvku. Když uživatel přetáhne ze sady nástrojů, ukazatel "neplatný" zobrazí, pokud kód nepovoluje sloučení.

   Sloučení můžete například povoluje pouze v případě, že přijímající element je v určitém stavu.

- Sada **používá vlastní sloučení** k přidání vlastního kódu k definování změn, které jsou provedeny v modelu při provedení sloučení.

   Můžete například nastavit vlastnosti ve sloučeném elementu pomocí dat z jeho nového umístění v modelu.

> [!NOTE]
> Pokud píšete vlastní kód sloučení, bude mít vliv pouze na sloučení, která jsou provedena pomocí tohoto EMD. Pokud existují další EMDs, které sloučí stejný typ objektu nebo pokud existuje jiný vlastní kód, který vytváří tyto objekty bez použití EMD, pak nebudou ovlivněny vlastním slučovacím kódem.
>
> Chcete-li zajistit, aby byl nový prvek nebo nový vztah vždy zpracován vlastním kódem, zvažte definování `AddRule` vztahu vkládání a `DeleteRule` třídy domény elementu. Další informace najdete v tématu [pravidla šířící změny v modelu](../modeling/rules-propagate-changes-within-the-model.md).

## <a name="example-defining-an-emd-without-custom-code"></a>Příklad: definování EMD bez vlastního kódu

Následující příklad umožňuje uživatelům vytvořit prvek a spojnici současně přetažením z panelu nástrojů na existující obrazec. V příkladu se přidá EMD do definice DSL. Před touto úpravou mohou uživatelé přetahovat nástroje do diagramu, ale ne do stávajících tvarů.

Uživatelé mohou také vkládat prvky do jiných prvků.

### <a name="to-let-users-create-an-element-and-a-connector-at-the-same-time"></a>Chcete-li umožnit uživatelům vytvořit prvek a konektor ve stejnou dobu

1. Vytvořte novou DSL pomocí šablony **minimálního jazyka** řešení.

    Když tuto DSL spustíte, umožní vám to vytvořit obrazce a spojnice mezi těmito obrazci. Nelze přetáhnout nový tvar **ExampleElement** ze sady nástrojů na existující obrazec.

2. Chcete-li uživatelům umožnit sloučení prvků do `ExampleElement` tvarů, vytvořte novou EMD ve `ExampleElement` třídě doména:

   1. V **Průzkumníku DSL** rozbalte položku **doménové třídy**. Klikněte pravým tlačítkem `ExampleElement` a potom klikněte na **Přidat novou direktivu sloučení elementů**.

   2. Ujistěte se, že je otevřené okno **Podrobnosti DSL** , takže uvidíte podrobnosti o novém EMD. (Nabídka: **zobrazení**, **ostatní okna**, **Podrobnosti DSL**.)

3. Nastavte **třídu indexování** v okně Podrobnosti DSL k definování třídy prvků, které lze sloučit do `ExampleElement` objektů.

    V tomto příkladu vyberte `ExampleElements` , aby uživatel mohl přetáhnout nové prvky na existující prvky.

    Všimněte si, že třída indexování se v Průzkumníku DSL stane názvem EMD.

4. V části **sloučení procesu vytvořením odkazů** přidejte dvě cesty:

   - Jedna cesta propojuje nový element s nadřazeným modelem. Výraz cesty, který je třeba zadat, přejde od existujícího elementu až po vložení vztahu k nadřazenému modelu. Nakonec určuje roli v novém odkazu, ke kterému bude nový prvek přiřazen. Cesta je následující:

      `ExampleModelHasElements.ExampleModel/!ExampleModel/.Elements`

   - Druhá cesta propojuje nový prvek s existujícím prvkem. Výraz Path určuje vztah odkazu a roli, do které bude nový prvek přiřazen. Tato cesta je následující:

      `ExampleElementReferencesTargets.Sources`

      Pomocí nástroje pro navigaci cest můžete vytvořit každou cestu:

      1. V části **proces sloučení vytvořením odkazů na cestách** klikněte na **\<add path>** .

      2. Klikněte na šipku rozevíracího seznamu napravo od položky seznamu. Zobrazí se stromové zobrazení.

      3. Rozbalením uzlů ve stromu můžete vytvořit cestu, kterou chcete zadat.

5. Otestujte DSL:

   1. Stisknutím klávesy **F5** znovu sestavte a spusťte řešení.

        Opakované sestavení bude trvat déle než obvykle, protože vygenerovaný kód bude aktualizován z textových šablon, aby odpovídal nové definici DSL.

   2. Po spuštění experimentální instance sady Visual Studio otevřete soubor modelu vaší DSL. Vytvoření některých ukázkových prvků.

   3. Přetáhněte z **ukázkového prvku elementu** na existující tvar.

        Zobrazí se nový tvar, který je propojený s existujícím obrazcem s konektorem.

   4. Kopírovat existující tvar. Vyberte jiný tvar a vložte ho.

        Vytvoří se kopie prvního obrazce.  Má nový název, který je propojený s druhým obrazcem pomocí konektoru.

Z tohoto postupu si všimněte následujících bodů:

- Vytvořením direktiv sloučení elementů můžete všem třídám elementu přijmout jiné. EMD se vytvoří ve třídě přijímací doména a v poli **třída indexu** se zadává přijatá doménová třída.

- Definováním cest můžete určit, jaké odkazy by se měly použít k propojení nového prvku s existujícím modelem.

     Odkazy, které zadáte, by měly zahrnovat jednu relaci vložení.

- EMD ovlivňuje vytváření ze sady nástrojů a také operace vložení.

     Pokud píšete vlastní kód, který vytváří nové prvky, můžete explicitně vyvolat EMD pomocí `ElementOperations.Merge` metody. Tím se zajistí, že váš kód propojuje nové prvky s modelem stejným způsobem jako jiné operace. Další informace najdete v tématu [přizpůsobení chování kopírování](../modeling/customizing-copy-behavior.md).

## <a name="example-adding-custom-accept-code-to-an-emd"></a>Příklad: Přidání vlastního kódu přijetí do EMD

Přidáním vlastního kódu do EMD můžete definovat složitější chování při slučování. Tento jednoduchý příklad brání uživateli v přidávání více než pevného počtu prvků do diagramu. V příkladu se upraví výchozí EMD, který doprovází vztah vložení.

### <a name="to-write-custom-accept-code-to-restrict-what-the-user-can-add"></a>Zápis vlastního kódu přijetí k omezení toho, co uživatel může přidat

1. Vytvořte DSL pomocí šablony **minimálního jazyka** řešení. Otevřete diagram definice DSL.

2. V Průzkumníku DSL rozbalte položku **třídy domény**, `ExampleModel` a **direktivy sloučení elementů**. Vyberte direktivu sloučení elementů s názvem `ExampleElement` .

     Tento EMD řídí, jak může uživatel vytvořit nové `ExampleElement` objekty v modelu, například přetažením ze sady nástrojů.

3. V okně **Podrobnosti DSL** vyberte použít **vlastní přijmout**.

4. Znovu sestavte řešení. Tato akce bude trvat déle než obvykle, protože vygenerovaný kód bude aktualizován z modelu.

     Bude nahlášena chyba sestavení, podobně jako: Company. ElementMergeSample. ExampleElement neobsahuje definici pro CanMergeExampleElement...

     Je nutné implementovat metodu `CanMergeExampleElement` .

5. Vytvořte nový soubor kódu v projektu **DSL** . Nahraďte jeho obsah následujícím kódem a změňte obor názvů na obor názvů vašeho projektu.

    ```csharp
    using Microsoft.VisualStudio.Modeling;

    namespace Company.ElementMergeSample // EDIT.
    {
      partial class ExampleModel
      {
        /// <summary>
        /// Called whenever an ExampleElement is to be merged into this ExampleModel.
        /// This happens when the user pastes an ExampleElement
        /// or drags from the toolbox.
        /// Determines whether the merge is allowed.
        /// </summary>
        /// <param name="rootElement">The root element in the merging EGP.</param>
        /// <param name="elementGroupPrototype">The EGP that the user wants to merge.</param>
        /// <returns>True if the merge is allowed</returns>
        private bool CanMergeExampleElement(ProtoElementBase rootElement, ElementGroupPrototype elementGroupPrototype)
        {
          // Allow no more than 4 elements to be added:
          return this.Elements.Count < 4;
        }
      }
    }
    ```

    Tento jednoduchý příklad omezuje počet prvků, které mohou být sloučeny do nadřazeného modelu. Pro zajímavé podmínky může metoda zkontrolovat kteroukoli z vlastností a propojení přijímajícího objektu. Může také zkontrolovat vlastnosti sloučených prvků, které jsou převedené v <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> . Další informace o najdete `ElementGroupPrototypes` v tématu [přizpůsobení chování kopírování](../modeling/customizing-copy-behavior.md). Další informace o tom, jak napsat kód, který čte model, naleznete v tématu [navigace a aktualizace modelu v kódu programu](../modeling/navigating-and-updating-a-model-in-program-code.md).

6. Otestujte DSL:

    1. Stisknutím klávesy **F5** znovu sestavte řešení. Po otevření experimentální instance sady Visual Studio otevřete instanci vaší DSL.

    2. Vytvořte nové prvky několika způsoby:

        - Přetáhněte z **ukázkového prvku** do diagramu.

        - V **Průzkumníku modelů** klikněte pravým tlačítkem na kořenový uzel a pak klikněte na **Přidat nový vzorový element**.

        - Zkopírujte a vložte prvek do diagramu.

    3. Ověřte, že nemůžete použít žádný z těchto způsobů pro přidání více než čtyř prvků do modelu. To je proto, že všechny používají direktivy sloučení elementů.

## <a name="example-adding-custom-merge-code-to-an-emd"></a>Příklad: Přidání vlastního kódu sloučení do EMD

V kódu vlastního sloučení můžete definovat, co se stane, když uživatel přetáhne nástroj nebo vloží do prvku. Existují dva způsoby, jak definovat vlastní sloučení:

1. Sada **používá vlastní sloučení** a poskytuje požadovaný kód. Váš kód nahradí generovaný kód sloučení. Tuto možnost použijte, pokud chcete zcela předefinovat, co dělá sloučení.

2. Přepsat `MergeRelate` metodu a volitelně `MergeDisconnect` metodu. Chcete-li to provést, musíte nastavit vlastnost **Generovat dvojitou hodnotu odvozenou** pro doménovou třídu. Váš kód může volat generovaný slučovací kód v základní třídě. Tuto možnost použijte, pokud chcete po provedení sloučení provést další operace.

   Tyto přístupy mají vliv pouze na sloučení, která jsou prováděna pomocí tohoto EMD. Chcete-li ovlivnit všechny způsoby, jak lze vytvořit sloučený prvek, alternativou je definování `AddRule` v relaci vložení a `DeleteRule` ve sloučené doméně třídy. Další informace najdete v tématu [pravidla šířící změny v modelu](../modeling/rules-propagate-changes-within-the-model.md).

### <a name="to-override-mergerelate"></a>Přepsání MergeRelate

1. V definici DSL se ujistěte, že jste definovali EMD, do kterého chcete přidat kód. Pokud chcete, můžete přidat cesty a definovat vlastní kód pro přijetí, jak je popsáno v předchozích částech.

2. V diagramu DslDefinition vyberte přijímací třídu sloučení. Typicky se jedná o třídu na zdrojovém konci vztahu vložení.

     Například v DSL vygenerovaném z minimálního jazykového řešení vyberte `ExampleModel` .

3. V okně **vlastnosti** je nastavena vlastnost **Generovat Double odvozenou** na **hodnotu true**.

4. Znovu sestavte řešení.

5. Zkontrolujte obsah **Dsl\Generated Files\DomainClasses.cs**. Vyhledejte metody pojmenované `MergeRelate` a prověřte jejich obsah. To vám pomůže psát vlastní verze.

6. V novém souboru kódu napište částečnou třídu pro přijímací třídu a přepište `MergeRelate` metodu. Nezapomeňte zavolat základní metodu. Příklad:

    ```csharp
    partial class ExampleModel
    {
      /// <summary>
      /// Called when the user drags or pastes an ExampleElement onto the diagram.
      /// Sets the time of day as the name.
      /// </summary>
      /// <param name="sourceElement">Element to be added</param>
      /// <param name="elementGroup">Elements to be merged</param>
      protected override void MergeRelate(ModelElement sourceElement, ElementGroup elementGroup)
      {
        // Connect the element according to the EMD:
        base.MergeRelate(sourceElement, elementGroup);

        // Custom actions:
        ExampleElement mergingElement = sourceElement as ExampleElement;
        if (mergingElement != null)
        {
          mergingElement.Name = DateTime.Now.ToLongTimeString();
        }
      }
    }
    ```

### <a name="to-write-custom-merge-code"></a>Zápis vlastního kódu sloučení

1. V **Dsl\Generated Code\DomainClasses.cs** si Prozkoumejte metody s názvem `MergeRelate` . Tyto metody vytvoří propojení mezi novým prvkem a existujícím modelem.

    Prozkoumejte také metody s názvem `MergeDisconnect` . Tyto metody odpojí prvek z modelu, když má být odstraněn.

2. V **Průzkumníku DSL** vyberte nebo vytvořte direktivu sloučení elementů, kterou chcete přizpůsobit. V okně **Podrobnosti DSL** nastavte **používat vlastní sloučení**.

    Když nastavíte tuto možnost, možnosti **sloučení** a **přeposílání** procesů se ignorují. Místo toho se použije váš kód.

3. Znovu sestavte řešení. Bude trvat déle než obvykle, protože generované soubory kódu budou aktualizovány z modelu.

    Zobrazí se chybové zprávy. Dvojitým kliknutím na chybové zprávy zobrazíte pokyny ve vygenerovaném kódu. Tyto pokyny vás požádají o zadání dvou metod, `MergeRelate` *YourDomainClass* a `MergeDisconnect` *YourDomainClass*

4. Zapište metody v definici částečné třídy v samostatném souboru kódu. Předchozí příklady, které jste si prohlédli dříve, by měly navrhnout, co potřebujete.

   Vlastní kód sloučení nebude mít vliv na kód, který vytváří objekty a vztahy přímo, a nebude mít vliv na jiné EMDs. Chcete-li zajistit, aby byly další změny implementovány bez ohledu na to, jak je prvek vytvořen, zvažte zápis `AddRule` a `DeleteRule` místo. Další informace najdete v tématu [pravidla šířící změny v modelu](../modeling/rules-propagate-changes-within-the-model.md).

## <a name="redirecting-a-merge-operation"></a>Přesměrování operace sloučení

Direktiva pro přesměrování sloučení přesměruje cíl operace sloučení. Nový cíl je obvykle vkládání nadřazeného objektu počáteční cíl.

Například v případě DSL, který byl vytvořen pomocí šablony diagramu komponent, jsou porty vloženy do komponent. Porty se zobrazují jako malé obrazce na okraji obrazce součásti. Uživatel vytvoří porty přetažením nástroje port na obrazec součásti. Někdy ale uživatel omylem přetáhne nástroj port na stávající port, nikoli na součást a operace se nezdařila. Jedná se o jednoduchou chybu, když existuje několik stávajících portů. Aby bylo možné tomuto uživateli zabránit v této nepříjemnosti, můžete porty přetáhnout na stávající port, ale akci přesměrovat na nadřazenou komponentu. Operace funguje, jako by cílový element byl součástí.

V řešení modelu komponenty můžete vytvořit direktivu pro přeposílání. Pokud zkompilujete a spustíte původní řešení, měli byste vidět, že uživatelé mohou přetahovat libovolný počet **vstupních portů** nebo **výstupních prvků portů** ze **sady nástrojů** do prvku **součásti** . Nemůžou ale přetahovat port na existující port. Nedostupný ukazatel upozorní na to, že toto přesunutí není povoleno. Můžete však vytvořit direktivu pro přeposílání, aby byl port, který je neúmyslně vyřazen na stávajícím **vstupním portem** , předán prvku **součásti** .

### <a name="to-create-a-forward-merge-directive"></a>Vytvoření direktivy pro přesměrovávání sloučení

1. Vytvořte [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] řešení pomocí šablony modelu komponent.

2. Otevřete **Průzkumníka DSL** otevřením DslDefinition. DSL.

3. V **Průzkumníku DSL** rozbalte položku **doménové třídy**.

4. Abstraktní doménová třída **ComponentPort** je základní třídou pro **inportování** i pro **přenos**. Klikněte pravým tlačítkem na **ComponentPort** a pak klikněte na **Přidat novou direktivu sloučení elementů**.

    Pod uzlem **direktivy sloučení elementů** se zobrazí nový uzel **direktivy sloučení elementů** .

5. Vyberte uzel **direktiva sloučení elementů** a otevřete okno **Podrobnosti DSL** .

6. V seznamu třída indexování vyberte možnost **ComponentPort**.

7. Vyberte **předávané sloučení do jiné doménové třídy**.

8. V seznamu výběr cesty rozbalte **ComponentPort**, rozbalte **ComponentHasPorts** a pak vyberte **součást**.

    Nová cesta by měla vypadat přibližně takto:

    **Komponenta ComponentHasPorts. Component/!**

9. Uložte řešení a pak šablony Transformujte kliknutím na tlačítko vpravo na panelu nástrojů **Průzkumník řešení** .

10. Sestavte a spusťte řešení. Zobrazí se nová instance Visual Studio.

11. V **Průzkumník řešení** otevřete soubor Sample.mydsl. Zobrazí se diagram a **sada nástrojů ComponentLanguage.**

12. Přetáhněte **vstupní port z** panelu **nástrojů** na jiný **vstupní port.** Potom přetáhněte **OutputPort** na **InputPort** a pak na jiný **OutputPort**.

     Ukazatel Nedostupný by se neměl zobrazit a nový vstupní **port** byste měli být schopni vypustit u existujícího. Vyberte nový vstupní **port a** přetáhněte ho do jiného bodu na **komponentě**.

## <a name="see-also"></a>Viz také

- [Navigace v modelu a aktualizace modelu v kódu programu](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Přizpůsobení nástrojů a panelu nástrojů](../modeling/customizing-tools-and-the-toolbox.md)
- [Ukázka DSL v schématech okruhu](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)
