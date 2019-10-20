---
title: Vytvoření jazyka specifického pro doménu založeného na model Windows Forms | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 452318ff-8ecf-46d0-8ca0-4013d0cdafaf
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cea3b76575e1da2e846e230580c6cfa50ef9b207
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651267"
---
# <a name="creating-a-windows-forms-based-domain-specific-language"></a>Vytvoření doménově specifického jazyka založeného na Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Model Windows Forms můžete použít k zobrazení stavu modelu DSL (Domain-Specific Language) namísto použití diagramu DSL. Toto téma vás provede vazbou formuláře Windows na DSL pomocí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] vizualizace a modelování sady SDK.

 ![DSL&#45;WPF&#45;2](../modeling/media/dsl-wpf-2.png "DSL – WPF-2") Instance DSL, která zobrazuje uživatelské rozhraní formuláře Windows a Průzkumník modelů.

## <a name="creating-a-windows-forms-dsl"></a>Vytvoření model Windows Forms DSL
 Šablona DSL pro **Návrháře minimálního DataGridView** vytvoří minimální DSL, kterou můžete upravit tak, aby vyhovovala vašim požadavkům.

#### <a name="to-create-a-minimal-winforms-dsl"></a>Vytvoření minimálního počtu WinForms DSL

1. Vytvořte DSL ze šablony **minimálního návrháře DataGridView** .

    V tomto návodu se předpokládají následující názvy:

   |                       |                 |
   |-----------------------|-----------------|
   | Název řešení a DSL |     FarmApp     |
   |       Obor názvů       | Společnost. FarmApp |

2. Experimentujte s úvodním příkladem, který šablona poskytuje:

   1. Transformujte všechny šablony.

   2. Sestavte a spusťte ukázku (**CTRL + F5**).

   3. V experimentální instanci aplikace Visual Studio otevřete soubor `Sample` v ladění projektu.

        Všimněte si, že se zobrazuje v ovládacím prvku model Windows Forms.

        Můžete také zobrazit prvky modelu zobrazené v Průzkumníkovi.

        Přidejte některé prvky ve formuláři nebo v Průzkumníku a Všimněte si, že se zobrazují v jiném zobrazení.

   V hlavní instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] si všimněte následujících bodů řešení DSL:

- `DslDefinition.dsl` neobsahuje žádné prvky diagramu. Důvodem je, že nebudete používat diagramy DSL k zobrazení modelů instancí této DSL. Místo toho navážete formulář Windows na model a prvky ve formuláři zobrazí model.

- Kromě projektů `Dsl` a `DslPackage` obsahuje řešení také třetí projekt s názvem `UI.` projekt**uživatelského rozhraní** obsahuje definici model Windows Formsho ovládacího prvku. `DslPackage` závisí na `UI` a `UI` závisí na `Dsl`.

- V projektu `DslPackage` `UI\DocView.cs` obsahuje kód, který zobrazuje ovládací prvek model Windows Forms, který je definován v projektu `UI`.

- @No__t_0 projekt obsahuje pracovní ukázku ovládacího prvku formuláře vázaného na DSL. Po změně definice DSL ale nebude fungovat. @No__t_0 projekt obsahuje:

  - Model Windows Forms třídy s názvem `ModelViewControl`.

  - Soubor s názvem `DataBinding.cs`, který obsahuje další částečnou definici `ModelViewControl`. Chcete-li zobrazit jeho obsah, v **Průzkumník řešení**otevřete místní nabídku souboru a vyberte možnost **Zobrazit kód**.

### <a name="about-the-ui-project"></a>O projektu uživatelského rozhraní
 Při aktualizaci souboru definice DSL pro definování vlastní DSL budete muset aktualizovat ovládací prvek v projektu `UI`, aby se zobrazila vaše DSL. Na rozdíl od `Dsl` a `DslPackage` projekty není ukázkový `UI` projekt generován ze `DslDefinitionl.dsl`. Můžete přidat soubory. TT pro vygenerování kódu, pokud chcete, i když to není pokryto v tomto návodu.

## <a name="updating-the-dsl-definition"></a>Aktualizace definice DSL
 V tomto návodu se používá následující definice DSL.

 ![DSL&#45;WPF&#45;1](../modeling/media/dsl-wpf-1.png "DSL – WPF-1")

#### <a name="to-update-the-dsl-definition"></a>Aktualizace definice DSL

1. Otevřete DslDefinition. DSL v Návrháři DSL.

2. Odstranit **ExampleElement**

3. Přejmenujte třídu domény **ExampleModel** na `Farm`.

     Poskytněte dodatečné doménové vlastnosti s názvem `Size` typu **Int32**a `IsOrganic` typu **Boolean**.

    > [!NOTE]
    > Pokud odstraníte kořenovou třídu domény a pak vytvoříte nový kořenový adresář, budete muset resetovat vlastnost kořenové třídy editoru. V **Průzkumníku DSL**vyberte **Editor**. Pak v okno Vlastnosti nastavte **kořenovou třídu** na `Farm`.

4. Pomocí nástroje **pojmenované doménové třídy** vytvořte následující doménové třídy:

    - `Field` – poskytněte tuto vlastnost další doménu s názvem `Size`.

    - `Animal` – v okno Vlastnosti nastavte **Modifikátor dědičnosti** na **abstract**.

5. Pomocí nástroje **doménová třída** vytvořte následující třídy:

    - `Sheep`

    - `Goat`

6. Pomocí nástroje **dědičnosti** `Goat` a `Sheep` převezmou z `Animal`.

7. Pomocí nástroje pro **vkládání** vložte `Field` a `Animal` v části `Farm`.

8. Možná budete chtít diagram uklizený. Chcete-li snížit počet duplicitních prvků, použijte příkaz **přenést podstrom** v místní nabídce prvků listu.

9. **Transformuje všechny šablony** na panelu nástrojů Průzkumník řešení.

10. Sestavte projekt **DSL** .

    > [!NOTE]
    > V této fázi nebudou ostatní projekty sestaveny bez chyb. Chceme však sestavit projekt DSL, aby jeho sestavení bylo k dispozici v Průvodci zdrojem dat.

## <a name="updating-the-ui-project"></a>Aktualizuje se projekt uživatelského rozhraní.
 Nyní můžete vytvořit nový uživatelský ovládací prvek, ve kterém budou zobrazeny informace, které jsou uloženy v modelu DSL. Nejjednodušší způsob, jak připojit uživatelský ovládací prvek k modelu, je prostřednictvím datových vazeb. Typ adaptéru datové vazby s názvem **ModelingBindingSource** je speciálně navržený pro propojení DSL s non-VMSDK rozhraními.

#### <a name="to-define-your-dsl-model-as-a-data-source"></a>Definování modelu DSL jako zdroje dat

1. V nabídce **data** klikněte na možnost **Zobrazit zdroje dat**.

     Otevře se okno **zdroje dat** .

     Vyberte možnost **Přidat nový zdroj dat**. Otevře se **Průvodce konfigurací zdroje dat** .

2. Vyberte **objekt**, **Další**.

     Rozbalte **DSL**, **Company. FarmApp**a vyberte **farmu**, která je kořenovou třídou vašeho modelu. Klikněte na tlačítko **Dokončit**.

     V Průzkumník řešení projekt **uživatelského rozhraní** nyní obsahuje **Properties\DataSources\Farm.DataSource**

     Vlastnosti a vztahy třídy modelu se zobrazí v okně zdroje dat.

     ![DslWpf&#45;3](../modeling/media/dslwpf-3.png "DslWpf-3")

#### <a name="to-connect-your-model-to-a-form"></a>Připojení modelu k formuláři

1. V projektu **uživatelského rozhraní** odstraňte všechny existující soubory. cs.

2. Přidejte do projektu **uživatelského rozhraní** nový soubor **uživatelského ovládacího prvku** s názvem `FarmControl`.

3. V okně **zdroje dat** vyberte v rozevírací nabídce v části **farma**možnost **Podrobnosti**.

    Pro ostatní vlastnosti ponechte výchozí nastavení.

4. Otevřete FarmControl.cs v návrhovém zobrazení.

    Přetáhněte **farmu** z okna zdroje dat do FarmControl.

    Zobrazí se sada ovládacích prvků, jedna pro každou vlastnost. Vlastnosti vztahu negenerují ovládací prvky.

5. Odstraňte **farmBindingNavigator**. To je také automaticky vygenerováno v Návrháři `FarmControl`, ale není vhodné pro tuto aplikaci.

6. Pomocí panelu nástrojů vytvořte dvě instance **ovládacího prvku DataGridView**a pojmenujte je `AnimalGridView` a `FieldGridView`.

   > [!NOTE]
   > Alternativním krokem je přetahování položek zvířat a polí z okna zdroje dat do ovládacího prvku. Tato akce automaticky vytvoří datovou mřížku a vazby mezi zobrazením mřížky a zdrojem dat. Tato vazba však pro DSL správně nefunguje. Proto je lepší vytvořit datovou mřížku a vazby ručně.

7. Pokud sada nástrojů neobsahuje nástroj **ModelingBindingSource** , přidejte ji. V místní nabídce na kartě **data** vyberte **možnost zvolit položky**. V dialogovém okně **zvolit položky sady nástrojů** vyberte na **kartě .NET Framework**možnost **ModelingBindingSource** .

8. Pomocí panelu nástrojů vytvořte dvě instance **ModelingBindingSource**a pojmenujte je `AnimalBinding` a `FieldBinding`.

9. Nastavte vlastnost **DataSource** každého **ModelingBindingSource** na **farmBindingSource**.

     Nastavte vlastnost **DataMember** na hodnotu **zvířata** nebo **pole**.

10. Nastavte vlastnosti **DataSource** `AnimalGridView` na `AnimalBinding` a `FieldGridView` na `FieldBinding`.

11. Upravte rozložení ovládacího prvku farmy na svou chuť.

    **ModelingBindingSource** je adaptér, který provádí několik funkcí specifických pro DSL:

- Rozbalí aktualizace do transakce VMSDK Store.

   Například když uživatel odstraní řádek z mřížky zobrazení dat, regulární vazba by způsobila výjimku transakce.

- Zajistí, že když uživatel vybere řádek, okno Vlastnosti zobrazí vlastnosti odpovídajícího prvku modelu namísto řádku datové mřížky.

  ![DslWpf4](../modeling/media/dslwpf4.png "DslWpf4") Schéma propojení mezi zdroji dat a zobrazeními.

#### <a name="to-complete-the-bindings-to-the-dsl"></a>Dokončení vazby na DSL

1. Přidejte následující kód do samostatného souboru kódu v projektu **uživatelského rozhraní** :

    ```csharp
    using System.ComponentModel;
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.Design;

    namespace Company.FarmApp
    {
      partial class FarmControl
      {
        public IContainer Components { get { return components; } }

        /// <summary>Binds the WinForms data source to the DSL model.
        /// </summary>
        /// <param name="nodelRoot">The root element of the model.</param>
        public void DataBind(ModelElement modelRoot)
        {
          WinFormsDataBindingHelper.PreInitializeDataSources(this);
          this.farmBindingSource.DataSource = modelRoot;
          WinFormsDataBindingHelper.InitializeDataSources(this);
        }
      }
    }
    ```

2. V projektu **DslPackage** upravte **DslPackage\DocView.TT** tak, aby se aktualizovala následující definice proměnné:

    ```csharp
    string viewControlTypeName = "FarmControl";
    ```

## <a name="testing-the-dsl"></a>Testování DSL
 Řešení DSL teď může sestavovat a spouštět, i když možná budete chtít později přidat další vylepšení.

#### <a name="to-test-the-dsl"></a>Otestování DSL

1. Sestavte a spusťte řešení.

2. V experimentální instanci aplikace Visual Studio otevřete **vzorový** soubor.

3. V **Průzkumníku FarmApp**otevřete místní nabídku na kořenovém uzlu **farmy** a vyberte možnost **Přidat novou kozy**.

     `Goat1` se zobrazí v zobrazení **zvířata** .

    > [!WARNING]
    > Je nutné použít místní nabídku uzlu **farma** , nikoli uzel **zvířata** .

4. Vyberte kořenový uzel **farmy** a zobrazte jeho vlastnosti.

     V zobrazení formulář změňte **název** nebo **Velikost** farmy.

     Když opustíte jednotlivá pole ve formuláři, odpovídající vlastnosti se změní v okno Vlastnosti.

## <a name="enhancing-the-dsl"></a>Vylepšení DSL

#### <a name="to-make-the-properties-update-immediately"></a>Postup aktualizace vlastností hned

1. V zobrazení Návrh FarmControl.cs vyberte jednoduché pole, jako je název, velikost nebo anorganické.

2. V okno Vlastnosti rozbalte položku **DataBindings** a otevřete **(rozšířené)** .

     V dialogu **formátování a rozšířené vazby** klikněte v části **režim aktualizace zdroje dat**na možnost **přepropertychanged**.

3. Sestavte a spusťte řešení.

     Ověřte, že při změně obsahu pole se okamžitě změní odpovídající vlastnost modelu farmy.

#### <a name="to-provide-add-buttons"></a>Poskytnutí tlačítek přidat

1. V zobrazení Návrh FarmControl.cs použijte panel nástrojů k vytvoření tlačítka na formuláři.

    Upravte název a text tlačítka, například `New Sheep`.

2. Otevřete kód za tlačítkem (například poklikáním myši).

    Upravte ho následujícím způsobem:

   ```csharp
   private void NewSheepButton_Click(object sender, EventArgs e)
   {
     using (Transaction t = farm.Store.TransactionManager.BeginTransaction("Add sheep"))
     {
       elementOperations.MergeElementGroup(farm,
         new ElementGroup(new Sheep(farm.Partition)));
       t.Commit();
     }
   }

   // The following code is shared with other add buttons:
   private ElementOperations operationsCache = null;
   private ElementOperations elementOperations
   {
     get
     {
       if (operationsCache == null)
       {
         operationsCache = new ElementOperations(farm.Store, farm.Partition);
       }
       return operationsCache;
     }
   }
   private Farm farm
   {
     get { return this.farmBindingSource.DataSource as Farm; }
   }

   ```

    Budete také muset vložit následující direktivu:

   ```csharp

   using Microsoft.VisualStudio.Modeling;

   ```

3. Přidejte podobné tlačítka pro kozy a pole.

4. Sestavte a spusťte řešení.

5. Ověřte, že tlačítko Nový přidá položku. Nová položka by se měla zobrazit v Průzkumníkovi FarmApp i v příslušném zobrazení mřížky dat.

    Měli byste být schopni upravit název prvku v zobrazení tabulky dat. Můžete ho také odstranit z těchto.

   ![DSL&#45;WPF&#45;2](../modeling/media/dsl-wpf-2.png "DSL – WPF-2")

### <a name="about-the-code-to-add-an-element"></a>O kódu pro přidání elementu
 U tlačítek nového elementu je následující alternativní kód mírně jednodušší.

```csharp
private void NewSheepButton_Click(object sender, EventArgs e)
{
  using (Transaction t = farm.Store.TransactionManager.BeginTransaction("Add sheep"))
  {
    farm.Animals.Add(new Sheep(farm.Partition)); ;
    t.Commit();
  }
}

```

 Tento kód však pro novou položku nenastaví výchozí název. Nespustí žádné přizpůsobené sloučení, které jste pravděpodobně definovali v **direktivách sloučení elementů** DSL, a nespustí žádný vlastní slučovací kód, který může být definován.

 Proto doporučujeme použít <xref:Microsoft.VisualStudio.Modeling.ElementOperations> k vytváření nových elementů. Další informace naleznete v tématu [přizpůsobení vytváření a přesunu prvku](../modeling/customizing-element-creation-and-movement.md).

## <a name="see-also"></a>Viz také
 [Definování kódu specifického](../modeling/how-to-define-a-domain-specific-language.md) [pro doménu psaní kódu pro přizpůsobení jazykové](../modeling/writing-code-to-customise-a-domain-specific-language.md) [sady SDK pro specifické domény pro sadu Visual Studio – jazyky specifické pro doménu](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)
