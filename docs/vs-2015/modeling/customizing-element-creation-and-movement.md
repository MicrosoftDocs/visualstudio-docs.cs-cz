---
title: Přizpůsobení vytvoření a přesunutí elementu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.elementmergedirective
helpviewer_keywords:
- Domain-Specific Language, element merge directives
ms.assetid: cbd28f15-dfd7-46bd-ab79-5430e3ed83c8
caps.latest.revision: 38
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 470ff89dfd864443206c1d9131fb126d58280859
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49853828"
---
# <a name="customizing-element-creation-and-movement"></a>Přizpůsobení vytvoření a přesunutí elementu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete povolit element, který má přetahovat do jiného, z panelu nástrojů nebo v vložením nebo operace přesunutí. Můžete mít přesunutých prvků propojené s cílových elementů pomocí vztahy, které zadáte.  
  
 Direktiva sloučení elementů (EMD) určuje, co se stane, když jeden prvek modelu *sloučené* na jiný prvek modelu. To se stane, když:  
  
- Uživatel přetáhne z panelu nástrojů do diagramu nebo obrazce.  
  
- Uživatel vytvoří element s použitím přidat nabídku v Průzkumníku nebo obrazce oddílu.  
  
- Uživatel přesune na jiné položky z jednoho plavecké dráhy.  
  
- Uživatel vloží prvek.  
  
- Váš program kód volá direktiva sloučení elementů.  
  
  I když operace vytváření se může zdát, že se liší od operace kopírování, skutečně fungují stejně. Když se přidá prvek, například z panelu nástrojů prototyp ho se replikuje. Prototyp se sloučí do modelu stejným způsobem jako prvky, které byly zkopírovány z jiné části modelu.  
  
  Odpovědnost EMD se rozhodnout, jak objekt nebo skupinu objektů by měly být sloučeny do konkrétních místech v modelu. Konkrétně se rozhodne, jaký relace by měl vytvořit instanci propojení skupině sloučené do modelu. Můžete také upravit, můžete nastavit vlastnosti a vytvořit další objekty.  
  
  ![DSL&#45;EMD&#95;Merge](../modeling/media/dsl-emd-merge.png "DSL-EMD_Merge")  
  Role direktiva sloučení elementů  
  
  Při definování vztah obsažení, vygenerovaný automaticky EMD. Toto výchozí nastavení EMD vytvoří instanci relace, když uživatelé přidají nové podřízené instance pro nadřazenou. Tyto výchozí EMDs, můžete upravit třeba tak, že přidáte vlastní kód.  
  
  Můžete také přidat vlastní EMDs v definici DSL a umožnit přetáhněte nebo vložte různé kombinace sloučené a přijímající třídy.  
  
## <a name="defining-an-element-merge-directive"></a>Definování direktivě sloučení elementů  
 Direktivy sloučení elementů můžete přidat doménové třídy, vztahy domén, tvary, konektory a diagramy. Můžete přidat nebo je vyhledat v Průzkumník DSL pod přijímající doménové třídy. Přijímací třída je doménová třída elementu, který je už v modelu a do které se sloučí element nové nebo zkopírovaný.  
  
 ![DSL&#45;EMD&#95;podrobnosti](../modeling/media/dsl-emd-details.png "DSL EMD_Details")  
  
 **Indexování třídy** je doménová třída prvky, které mohou být sloučeny do členy přijímající třídy. Instance podtřídy třídy indexování bude také sloučeno uživatelem EMD, pokud nenastavíte **atí pro podtřídy** na hodnotu False.  
  
 Existují dva druhy slučovací direktiva:  
  
- A **proces sloučení** direktiva určuje vztahy, které by měly být propojeny nový prvek do stromové struktury.  
  
- A **vpřed sloučit** – direktiva přesměruje nový prvek na jiný přijímací element, obvykle nadřazenou položku.  
  
  Můžete přidat vlastní kód direktivy sloučení:  
  
- Nastavte **používá vlastní přijetí** přidání vlastního kódu k určení, zda by měly být konkrétní instanci prvku indexování sloučeny do cílového elementu. Když uživatel přetáhne z panelu nástrojů, "neplatný" ukazatel ukazuje, pokud váš kód zakazuje sloučení.  
  
   Například můžete umožnit sloučení pouze v případě přijímací element je v určitém stavu.  
  
- Nastavte **používá vlastní sloučení** přidat poskytnout vlastní kód, který definuje změny provedené na model, při provádění sloučení.  
  
   Například můžete nastavit vlastnosti v elementu sloučené s použitím dat z nové místo v modelu.  
  
> [!NOTE]
>  Pokud píšete kód vlastní sloučení, ovlivní pouze sloučení, které se provádí pomocí této EMD. Pokud existují další EMDs, které sloučení stejného typu objektu, nebo pokud je jiný vlastní kód, který vytvoří tyto objekty bez použití EMD, nebude vliv kódem vlastní sloučení.  
>   
>  Pokud chcete, aby se zajistilo, že nový prvek nebo nová relace je vždy zpracovány váš vlastní kód, zvažte možnost definice `AddRule` na vztah obsažení a `DeleteRule` v elementu doménovou třídu. Další informace najdete v tématu [pravidla šíření změn v rámci the Model](../modeling/rules-propagate-changes-within-the-model.md).  
  
## <a name="example-defining-an-emd-without-custom-code"></a>Příklad: Definování EMD bez vlastního kódu  
 Následující příklad umožňuje uživatelům vytvářet elementu a konektor ve stejnou dobu přetažením z panelu nástrojů do existujícího tvaru. V příkladu přidá EMD definici DSL. Před provedením této změny můžete uživatelům přetáhnout nástrojů do diagramu, ale ne na existující obrazce.  
  
 Uživatelům také můžete vložit prvky do dalších prvků.  
  
#### <a name="to-let-users-create-an-element-and-a-connector-at-the-same-time"></a>Umožňuje uživatelům vytvořit prvek a konektor ve stejnou dobu  
  
1. Vytvořit nový DSL pomocí **minimální jazykový** šablonu řešení.  
  
    Když spustíte tento DSL, umožňuje vám vytvořit obrazců a konektorů mezi tvary. Nelze přetáhnout nový **ExampleElement** tvaru z panelu nástrojů do existujícího tvaru.  
  
2. Umožňuje uživatelům sloučit elementy do `ExampleElement` tvary, vytvořte nový EMD v `ExampleElement` doménové třídy:  
  
   1.  V **Průzkumník DSL**, rozbalte **doménovými třídami**. Klikněte pravým tlačítkem na `ExampleElement` a potom klikněte na tlačítko **přidat nové direktiva sloučení elementů**.  
  
   2.  Ujistěte se, že **podrobnosti DSL** tak, aby si můžete zobrazit podrobnosti nové EMD je otevřeno, okno. (Nabídka: **zobrazení**, **jiných Windows**, **podrobnosti DSL**.)  
  
3. Nastavte **indexování třídy** v okně podrobností DSL, chcete-li definovat, jaké třídy prvků může být sloučeny do `ExampleElement` objekty.  
  
    V tomto příkladu vyberte `ExampleElements`tak, aby uživatel nové prvky můžete přetáhnout do existující prvky.  
  
    Všimněte si, že třída indexování bude název EMD v Průzkumník DSL.  
  
4. V části **pracovat sloučení vytvořením odkazů**, přidejte dvě cesty:  
  
   1. Jedna cesta odkazuje na model nadřazené nového elementu. Výraz cesty, které budete muset zadat prochází z existující prvek nahoru vztah obsažení nadřízeného modelu. Také definuje roli v nový odkaz, ke kterému se přiřadí nový prvek. Cesta je následujícím způsobem:  
  
       `ExampleModelHasElements.ExampleModel/!ExampleModel/.Elements`  
  
   2. Jiné cesty propojí nový prvek do existujícího prvku. Výraz cesty určuje referenční vztah a role, ke kterému se přiřadí nový prvek. Tato cesta je následujícím způsobem:  
  
       `ExampleElementReferencesTargets.Sources`  
  
      Nástroj navigace cestu slouží k vytvoření jednotlivé cesty:  
  
   3. V části **pracovat sloučení vytvořením odkazů na cestách**, klikněte na tlačítko  **\<přidat cestu >**.  
  
   4. Klikněte na rozevírací šipku napravo od položky seznamu. Zobrazení stromu se zobrazí.  
  
   5. Rozbalte uzly ve stromu na formulář, který chcete zadat cestu.  
  
5. Otestujte DSL:  
  
   1.  Stisknutím klávesy F5 znovu sestavte a spusťte řešení.  
  
        Opětovné sestavení bude trvat déle než obvykle, protože generovaný kód se budou aktualizovat z textové šablony tak, aby odpovídal na novou definici DSL.  
  
   2.  Když experimentální instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] má začít, otevřete soubor modelu tohoto kódu DSL. Vytvořte některé prvky příklad.  
  
   3.  Přetáhněte z **příklad elementu** nástroj na existující obrazec.  
  
        Zobrazí se nový tvar a je propojený s existující obrazec s konektorem.  
  
   4.  Zkopírujte existující tvar. Vyberte jiný tvar a vložit.  
  
        Je vytvořena kopie okraje prvního tvaru.  Má nový název a je propojený obrazec s konektorem.  
  
   Všimněte si následujících z tohoto postupu:  
  
-   Vytvořením direktivy sloučení elementů, můžete povolit všechny třídy element tak, aby přijímal jakýkoli jiný. EMD se vytvoří v přijímající třídy domény a přijaté doménová třída je uveden v **Index – třída** pole.  
  
-   Definování cest, můžete určit, jaké odkazy by měly sloužit k připojení nový prvek do existujícího modelu.  
  
     Jeden vztah obsažení by měla obsahovat odkazy, které zadáte.  
  
-   EMD ovlivňuje vytvoření panelu nástrojů a také operace vložení.  
  
     Můžete psát vlastní kód, který vytvoří nové prvky, můžete explicitně vyvolat EMD pomocí `ElementOperations.Merge` metody. Tím zajistíte, že váš kód odkazuje nové prvky do modelu stejným způsobem jako jiné operace. Další informace najdete v tématu [přizpůsobení chování kopírování](../modeling/customizing-copy-behavior.md).  
  
## <a name="example-adding-custom-accept-code-to-an-emd"></a>Příklad: Přidání vlastní přijetí kódu do EMD  
 Do EMD přidáte vlastní kód, můžete definovat složitější chování sloučení. Tento jednoduchý příklad zabrání uživateli v přidávání více než pevný počet elementů do diagramu. V příkladu změní výchozí EMD, který doprovází vztah obsažení.  
  
#### <a name="to-write-custom-accept-code-to-restrict-what-the-user-can-add"></a>Vytvoření vlastní přijetí kódu pro omezení toho, co můžete přidat uživatele  
  
1.  Vytvoření DSL pomocí **minimální jazykový** šablonu řešení. Otevřete diagram definici DSL.  
  
2.  V okně Průzkumník DSL, rozbalte **doménovými třídami**, `ExampleModel`, **direktivy sloučení elementů**. Vyberte direktivě sloučení elementů s názvem `ExampleElement`.  
  
     Tato EMD řídí, jak uživatel může vytvořit nové `ExampleElement` objekty v modelu, například přetažením z panelu nástrojů.  
  
3.  V **podrobnosti DSL** okně **používá vlastní přijetí**.  
  
4.  Znovu sestavte řešení. Bude to trvat déle než obvykle, protože generovaný kód se budou aktualizovat z modelu.  
  
     Chyba sestavení bude ohlášené, podobně jako: "Company.ElementMergeSample.ExampleElement neobsahuje definici pro CanMergeExampleElement..."  
  
     Je nutné implementovat metodu `CanMergeExampleElement`.  
  
5.  Vytvoření nového souboru v kódu **Dsl** projektu. Nahraďte jeho obsah následujícím kódem a změna oboru názvů do oboru názvů vašeho projektu.  
  
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
  
     Tento jednoduchý příklad omezuje počet prvků, které mohou být sloučeny do nadřazeného modelu. Zajímavější podmínky můžete si prohlédnout metodu, všechny vlastnosti a odkazy přijímající objektu. Můžete také zkontrolovat vlastnosti sloučení elementů, které se přenášejí v <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype>. Další informace o `ElementGroupPrototypes`, naleznete v tématu [přizpůsobení chování kopírování](../modeling/customizing-copy-behavior.md). Další informace o tom, jak psát kód, který čte model, najdete v části [navigace a aktualizace modelu v programovém kódu](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
6.  Otestujte DSL:  
  
    1.  Znovu sestavte řešení stisknutím klávesy F5. Když experimentální instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] se otevře, spusťte instanci tohoto kódu DSL.  
  
    2.  Vytvořte nové prvky několika způsoby:  
  
        1.  Přetáhněte z **příklad elementu** nástrojů do diagramu.  
  
        2.  V **Průzkumníka modelů příklad**, klikněte pravým tlačítkem na kořenový uzel a potom klikněte na tlačítko **přidejte nový prvek příklad**.  
  
        3.  Zkopírujte a vložte elementu v diagramu.  
  
    3.  Ověřte, že nemůžete použít žádnou z těchto způsobů, jak přidat více než čtyři prvky modelu. Je to proto, že všechny používají u direktivy sloučení elementů.  
  
## <a name="example-adding-custom-merge-code-to-an-emd"></a>Příklad: Přidání vlastní sloučení kódu do EMD  
 Ve vlastní sloučení kódu můžete definovat, co se stane, když uživatel přetáhne nástroj nebo vloží do elementu. Existují dva způsoby, jak definovat vlastní sloučení:  
  
1. Nastavte **používá vlastní sloučit** a zadejte požadovaný kód. Kód nahradí kód vygenerovaný sloučení. Tuto možnost použijte, pokud chcete úplně předefinovat význam sloučení.  
  
2. Přepsat `MergeRelate` metoda a volitelně také `MergeDisconnect` metoda. Chcete-li to provést, je nutné nastavit **Generates Double Derived** vlastnost doménové třídy. Váš kód může volat kód vygenerovaný sloučení v základní třídě. Tuto možnost použijte, pokud chcete provádět další operace po provedení sloučení.  
  
   Tyto přístupy ovlivní pouze sloučení, která se provádí na základě této EMD. Pokud chcete mít vliv na všechny způsoby, ve kterých můžete vytvořit sloučené element, alternativou je definování `AddRule` na vztah obsažení a `DeleteRule` na sloučené doménové třídy. Další informace najdete v tématu [pravidla šíření změn v rámci the Model](../modeling/rules-propagate-changes-within-the-model.md).  
  
#### <a name="to-override-mergerelate"></a>Chcete-li přepsat MergeRelate  
  
1.  Ujistěte se, kterou jste definovali EMD, ke kterému chcete přidat kód v definici DSL. Pokud chcete, můžete přidat cesty a definovat vlastní přijetí kódu, jak je popsáno v předchozích částech.  
  
2.  V diagramu DslDefinition vyberte přijímající třídy sloučení. Obvykle je třída na konci zdroje vztah obsažení.  
  
     Například v DSL vygenerovaná minimální jazykový řešení, vyberte `ExampleModel`.  
  
3.  V **vlastnosti** okno, nastavte **Generates Double Derived** k **true**.  
  
4.  Znovu sestavte řešení.  
  
5.  Zkontrolovat obsah **Dsl\Generated Files\DomainClasses.cs**. Hledat metody s názvem `MergeRelate` a zkontrolovat jejich obsah. To vám pomůže psát vlastní verze.  
  
6.  V novém souboru kódu, zápis částečné třídy pro přijímající třídy a přepsat `MergeRelate` metody. Nezapomeňte volat základní metodu. Příklad:  
  
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
  
#### <a name="to-write-custom-merge-code"></a>Vytvoření vlastní sloučení kódu  
  
1. V **Dsl\Generated Code\DomainClasses.cs**, zkontrolujte metody s názvem `MergeRelate`. Tyto metody vytvoří propojení mezi nového elementu a existující model.  
  
    Také zkontrolovat metody s názvem `MergeDisconnect`. Tyto metody odpojit z modelu prvek po odstranění.  
  
2. V **Průzkumník DSL**vyberte nebo vytvořte direktivě sloučení elementů, které chcete přizpůsobit. V **podrobnosti DSL** okno, nastavte **používá vlastní sloučit**.  
  
    Když tuto možnost nastavíte **proces sloučení** a **vpřed sloučit** možnosti jsou ignorovány. Svůj kód se místo toho použít.  
  
3. Znovu sestavte řešení. Bude trvat déle než obvykle, protože generovaný kód soubory se budou aktualizovat z modelu.  
  
    Zobrazí se chybové zprávy. Klikněte dvakrát na chybové zprávy, zobrazí se pokyny v generovaném kódu. Tyto pokyny vás vyzve k zadání dvě metody, `MergeRelate` *YourDomainClass* a `MergeDisconnect` *YourDomainClass*  
  
4. Metody zapsat definicí částečné třídy v samostatném souboru kódu. Příklady, které ho zkontrolovat dříve by měla navrhovat, co potřebujete.  
  
   Vlastní slučovat kód nebude mít vliv na kód, který vytvoří objekty a vztahy přímo, a to nebude mít vliv na ostatní EMDs. Chcete-li mít jistotu, že další změny jsou implementovány bez ohledu na to, jak vytvořit prvek, zvažte zápis `AddRule` a `DeleteRule` místo. Další informace najdete v tématu [pravidla šíření změn v rámci the Model](../modeling/rules-propagate-changes-within-the-model.md).  
  
## <a name="redirecting-a-merge-operation"></a>Přesměrování operaci sloučení  
 Dopředné slučovací direktiva přesměruje cíl operace sloučení. Nový cíl je obvykle vkládání nadřazené počáteční cíle.  
  
 V DSL, který byl vytvořen pomocí šablony diagramu součástí, například porty jsou vloženy do komponenty. Porty se zobrazují jako malé obrazce na okraji tvar součásti. Uživatel vytvoří porty přetažením nástroj Port na tvar součásti. Ale v některých případech omylem přetažena nástroj Port existující port, namísto komponenty, a operace se nezdaří. To je snadno chybu, pokud existuje několik existujících portů. Abychom uživatelům vyhnout se této nepříjemný, můžete povolit porty přetahovat do existující port, ale mají akce přesměrován na nadřazenou komponentu. Operace funguje jakoby byly komponenta cílového prvku.  
  
 Dopředné slučovací direktiva můžete vytvořit v modelu řešení. Pokud kompilace a spuštění v původním řešení, měli byste vidět, že uživatelé můžete přetáhnout libovolný počet **vstupní Port** nebo **výstupní Port** elementy ze **nástrojů** k **Komponenty** elementu. Nelze však přetažení portu pro existující port. Ukazatel není k dispozici je upozorní, tento krok není povoleno. Však můžete vytvořit přesměrování slučovací direktiva tak, aby port, který je neúmyslně na existující **vstupní Port** předá **komponenty** elementu.  
  
#### <a name="to-create-a-forward-merge-directive"></a>Chcete-li vytvořit přesměrování slučovací direktiva  
  
1.  Vytvoření [!INCLUDE[dsl](../includes/dsl-md.md)] řešení s použitím šablony modelu.  
  
2.  Zobrazení **Průzkumník DSL** otevřením DslDefinition.dsl.  
  
3.  V **Průzkumník DSL**, rozbalte **doménovými třídami**.  
  
4.  **ComponentPort** abstraktní doménová třída je základní třídou obou **InPort** a **OutPort**. Klikněte pravým tlačítkem na **ComponentPort** a potom klikněte na tlačítko **přidat nové direktiva sloučení elementů**.  
  
     Nový **direktiva sloučení elementů** uzel se zobrazí v části **direktivy sloučení elementů** uzlu.  
  
5.  Vyberte **direktiva sloučení elementů** uzlu a otevřít **podrobnosti DSL** okna.  
  
6.  Vyberte v seznamu tříd indexování **ComponentPort**.  
  
7.  Vyberte **sloučit přesměrováním do jiné doménové třídy**.  
  
8.  V seznamu cest pro výběr, rozbalte **ComponentPort**, rozbalte **ComponentHasPorts**a pak vyberte **komponenty**.  
  
     Nová cesta by se mělo podobat následujícímu:  
  
     **ComponentHasPorts.Component/!Component**  
  
9. Uložte řešení a potom klikněte na tlačítko vpravo na transformaci šablon **Průzkumníka řešení** nástrojů.  
  
10. Sestavte a spusťte řešení. Novou instanci třídy [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] se zobrazí.  
  
11. V **Průzkumníka řešení**, otevřete Sample.mydsl. Diagram a **ComponentLanguage nástrojů** zobrazí.  
  
12. Přetáhněte **vstupní Port** z **nástrojů** do jiného **vstupní Port.** V dalším kroku přetáhněte **OutputPort** do **InputPort** a pak do jiného **OutputPort**.  
  
     Neměli vidět ukazatel není k dispozici a je třeba vyřadit nové **vstupní Port** na existující. Vyberte novou **vstupní Port** a přetáhněte jej do jiného bodu **komponenty**.  
  
## <a name="see-also"></a>Viz také  
 [Procházení a aktualizace modelu v programovém kódu](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Přizpůsobení nástrojů a panelu nástrojů](../modeling/customizing-tools-and-the-toolbox.md)   
 [Ukázka diagramy okruh DSL](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)



