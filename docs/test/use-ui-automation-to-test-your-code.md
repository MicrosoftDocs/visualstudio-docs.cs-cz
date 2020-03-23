---
title: Programové testy uživatelského rozhraní
ms.date: 12/04/2018
ms.topic: conceptual
f1_keywords:
- vs.codedUITest
- vs.codedUITest.recorder
- vs.codedUITest.testbuilder
- vs.codedUITest.addAssertions
- vs.codedUITest.createdialog
helpviewer_keywords:
- automated tests, testing UI interface
- coded UI test
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f3bd667579d9ff0645e7dd2753278257a9796709
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585636"
---
# <a name="use-coded-ui-test-to-test-your-code"></a>Testování kódu pomocí programového testu ui

Programové testy uživatelského rozhraní (CUITs) řídit vaši aplikaci prostřednictvím svého uživatelského rozhraní (UI). Tyto testy zahrnují funkční testování ovládacích prvků ui. Umožňují ověřit, že celá aplikace, včetně jejího uživatelského rozhraní, funguje správně. Programové testy uživatelského rozhraní jsou užitečné tam, kde je ověření nebo jiné logiky v uživatelském rozhraní, například na webové stránce. Často se také používají k automatizaci existujícího ručního testu.

Vytvoření testu programovaného ui v sadě Visual Studio je snadné. Jednoduše provést test ručně, zatímco **coded UI Test Builder** běží na pozadí. Můžete také určit, jaké hodnoty se mají v určitých polích zobrazovat. **Programový tvůrce testů ui** zaznamenává vaše akce a generuje z nich kód. Po vytvoření testu jej můžete upravit ve specializovaném editoru, který umožňuje upravit posloupnost akcí.

Specializovaný **programový tvůrce testů a** editor testů ui usnadňují vytváření a úpravy programovaných testů ui, i když jsou vaše hlavní dovednosti soustředěny spíše v testování než kódování. Ale pokud jste vývojář a chcete rozšířit test pokročilejším způsobem, kód je strukturován tak, aby bylo jednoduché kopírovat a přizpůsobit. Můžete například zaznamenat test, abyste něco koupili na webu, a pak upravit generovaný kód a přidat smyčku, která nakoupí mnoho položek.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="requirements"></a>Požadavky

- Visual Studio Enterprise
- Kódovaná testovací komponenta ui

Další informace o platformách a konfiguracích podporovaných testy programového rozhraní naleznete v [tématu Podporované platformy](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md).

## <a name="install-the-coded-ui-test-component"></a>Instalace testovací součásti programovaného ui

Chcete-li získat přístup k kódované nástroje a šablony uživatelského nastavení, nainstalujte **programové uživatelské ho uživatelského nastavení testovací** součást sady Visual Studio.

1. Spusťte **Instalační službu sady Visual Studio** výběrem **nástroje** > **získat nástroje a funkce**.

1. V **Instalační službě sady Visual Studio**zvolte kartu Jednotlivé **součásti** a pak přejděte dolů do části Ladění a **testování.** Vyberte testovací komponentu **kódovaného ui.**

   ![Kódovaná testovací komponenta ui](media/coded-ui-test-component.png)

1. Vyberte **Změnit**.

## <a name="create-a-coded-ui-test"></a>Vytvoření programového testu ui

1. Vytvořte projekt testu programového ui.

   Programové testy ui musí být obsaženy v projektu test programovaného rozhraní. Pokud ještě nemáte programový testovací projekt ui, vytvořte ho. Zvolte **Soubor** > **nový** > **projekt**. Vyhledejte a vyberte šablonu **projektu programového testovacího projektu uživatelského mise.**

   ::: moniker range="vs-2017"

   ![Kódovaná šablona testovacího projektu uživatelského i v novém projektu](media/coded-ui-test-project-template.png)

   ::: moniker-end

   > [!NOTE]
   > Pokud nevidíte šablonu **programového testovacího projektu uživatelského nastavení,** je třeba [nainstalovat testovací komponentu programovaného uživatelského nastavení](../test/use-ui-automation-to-test-your-code.md#install-the-coded-ui-test-component).

2. Přidejte kódovaný testovací soubor ui.

     Pokud jste právě vytvořili programový projekt ui, bude automaticky přidán první soubor CUIT. Chcete-li přidat další testovací soubor, otevřete místní nabídku v testovacím projektu programového rozhraní v **Průzkumníku řešení**a pak zvolte **Přidat** > **kódovaný test ui**.

     V dialogovém **okně Generovat kód pro kódovaný test ui** zvolte **Zaznamenat akce** > **Úprava mapy ui nebo přidejte kontrolní výrazy**.

     ![Dialogové okno Generovat kód pro kódované testovací ui.](media/generate-code-for-coded-ui-test.png)

     Zobrazí se **Tvůrce testů programového ui.**

     ![Tvůrce kódovaných testů ui](../test/media/codedui_testbuilder.png)

3. Zaznamenejte posloupnost akcí.

     **Chcete-li zahájit nahrávání**, zvolte ikonu **Záznam.** Proveďte akce, které chcete testovat v aplikaci, včetně spuštění aplikace, pokud je to požadováno. Pokud například testujete webovou aplikaci, můžete spustit prohlížeč, přejít na web a přihlásit se k aplikaci.

     **Chcete-li pozastavit nahrávání**, například pokud se musíte vypořádat s příchozí poštou, zvolte **Pozastavit**.

    > [!WARNING]
    > Všechny akce prováděné na ploše budou zaznamenány. Pokud provádíte akce, které mohou vést k zahrnutí citlivých dat do záznamu, pozastavte nahrávání.

     **Chcete-li odstranit akce,** které jste zaznamenali omylem, zvolte **Upravit kroky**.

     **Chcete-li generovat kód,** který bude replikovat vaše akce, zvolte ikonu **Generovat kód** a zadejte název a popis pro testovací metodu kódovaného uživatelského prostředí.

4. Ověřte hodnoty v polích ui, jako jsou textová pole.

     V **nástroji Coded UI Test Builder**zvolte Přidat kontrolní **výrazy** a pak zvolte ovládací prvek ui ve spuštěné aplikaci. V seznamu vlastností, které se zobrazí, vyberte vlastnost, například **Text** v textovém poli. V místní nabídce zvolte **Přidat kontrolní výraz**. V dialogovém okně vyberte operátor porovnání, hodnotu porovnání a chybovou zprávu.

     Zavřete okno kontrolního **výrazu**a zvolte Generovat kód .

     ![Kódovaný prvek cílení testu ui](../test/media/codedui_1.png)

    > [!TIP]
    > Přepínají mezi akcemi nahrávání a ověřováním hodnot. Generovat kód na konci každé sekvence akcí nebo ověření. Pokud chcete, budete moci později vložit nové akce a ověření.

     Další podrobnosti naleznete v [tématu Ověření vlastností ovládacích prvků](#validate-the-properties-of-ui-controls).

5. Zobrazení generovaného testovacího kódu.

     Chcete-li zobrazit generovaný kód, zavřete okno Tvůrce testů ui. V kódu můžete zobrazit názvy, které jste přidali každému kroku. Kód je v souboru CUIT, který jste vytvořili:

    ```csharp
    [CodedUITest]
    public class CodedUITest1
    { ...
      [TestMethod]
      public void CodedUITestMethod1()
      {
          this.UIMap.AddTwoNumbers();
          this.UIMap.VerifyResultValue();
          // To generate more code for this test, select
          // "Generate Code" from the shortcut menu.
      }
    }
    ```

6. Přidejte další akce a kontrolní výrazy.

   Umístěte kurzor na příslušný bod v testovací metodě a pak v místní nabídce zvolte **Generovat kód pro kódovaný test uj.** V tomto okamžiku bude vložen nový kód.

7. Upravte podrobnosti testovacích akcí a kontrolnívýrazy.

     Otevřete *UIMap.uitest*. Tento soubor se otevře v **Editoru testů programového rozhraní**, kde můžete upravit libovolnou posloupnost zaznamenaných akcí a také upravit kontrolní výrazy.

     ![Editor programového testu UI](../test/media/cuit_editor_edit.png)

     Další informace naleznete [v tématu Úprava programových testů ui pomocí editoru programového testu ui](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

8. Spusťte test.

   Použijte Průzkumníka testů nebo otevřete místní nabídku v testovací metodě a pak zvolte **Spustit testy**. Další informace o tom, jak spustit testy, naleznete [v tématu Spuštění testů částí s Průzkumníkem testů](../test/run-unit-tests-with-test-explorer.md) a *Další možnosti pro spuštění programových testů ui* v části [Co dál?](#whats-next)

Zbývající části v tomto tématu poskytují další podrobnosti o krocích v tomto postupu.

Podrobnější příklad najdete [v tématu Návod: Vytváření, úpravy a údržba programovaného testu ui](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md). V návodu vytvoříte jednoduchou aplikaci WPF (Windows Presentation Foundation), která předvede, jak vytvořit, upravit a udržovat test programového řízení. Návod poskytuje řešení pro opravu testů, které byly poškozeny různými chybami časování a refaktoringem ovládacích prvků.

## <a name="start-and-stop-the-application-under-test"></a>Spuštění a zastavení testovky

Pokud nechcete spustit a zastavit aplikaci, prohlížeč nebo databázi samostatně pro každý test, proveďte jeden z následujících akcí:

- Pokud nechcete zaznamenávat akce pro spuštění aplikace v testu, musíte spustit aplikaci před výběrem ikony **Záznam.**

- Na konci testu je ukončen proces, ve kterém je ukončena zkušební běhy. Pokud jste aplikaci spustili v testu, aplikace se obvykle zavře.  Pokud nechcete, aby test ukončit aplikaci při ukončení, přidejte soubor *.runsettings* do řešení a použijte `KeepExecutorAliveAfterLegacyRun` možnost. Další informace naleznete [v tématu Konfigurace testů částí pomocí souboru .runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

- Přidejte metodu inicializovat `[TestInitialize]` test, identifikovanou atributem, který spustí kód na začátku každé zkušební metody. Můžete například spustit aplikaci z metody TestInitialize.

- Přidejte metodu vyčištění testu, `[TestCleanup]` identifikovanou atributem, který spouští kód na konci každé zkušební metody. Například metoda pro ukončení aplikace může být volána z Metody TestCleanup.

## <a name="validate-the-properties-of-ui-controls"></a>Ověření vlastností ovládacích prvků ui

Pomocí tvůrce **testů programového uživatelského rozhraní** můžete přidat ovládací prvek uživatelského rozhraní (UI) do [uimap](/previous-versions/dd580454(v=vs.140)) pro test nebo ke generování kódu pro metodu ověření, která používá kontrolní výraz pro ovládací prvek uživatelského rozhraní.

Chcete-li generovat kontrolní výrazy pro ovládací prvky ui, zvolte nástroj **Přidat kontrolní výrazy** v **programovém nástroji Tvůrce testů ui** a přetáhněte jej do ovládacího prvku v testované aplikaci, který chcete ověřit, je správný. Když pole načrtne ovládací prvek, uvolněte myš. Kód třídy ovládacího prvku je okamžitě vytvořen v *souboru UIMap.Designer.cs.*

![Kódovaný prvek cílení testu ui](../test/media/codedui_1.png)

Vlastnosti tohoto ovládacího prvku jsou nyní uvedeny v dialogovém okně **Přidat kontrolní výrazy.**

Dalším způsobem navigace k určitému ovládacímu prvku je výběr šipky **(<<)** pro rozšíření zobrazení **mapy řízení ui**. Chcete-li najít nadřazený ovládací prvek, na stejné úrovni nebo podřízený ovládací prvek, můžete kliknout na libovolné místo na mapě a pomocí kláves se šipkami se pohybovat po stromu.

![Kódované vlastnosti testu ui](../test/media/codedui_2.png)

> [!TIP]
> Pokud nevidíte žádné vlastnosti při výběru ovládacího prvku v aplikaci nebo nevidíte ovládací prvek v mapě ovládacího prvku ui, ověřte, zda má ovládací prvek jedinečné ID v kódu aplikace. Jedinečné ID může být atribut ID HTML nebo WPF UId.

Dále otevřete místní nabídku ve vlastnosti ovládacího prvku ui, který chcete ověřit, a přejděte na **přidat kontrolní výraz**. V dialogovém okně **Přidat kontrolní výraz** vyberte **komparátor** pro kontrolní výraz, například <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A>, a zadejte hodnotu výrazu do srovnávací **hodnoty**.

![Kódované kontrolní výrazy testu uI](../test/media/codedui_3.png)

Po přidání všech kontrolních výrazů pro test zvolte **OK**.

Chcete-li vygenerovat kód pro vaše kontrolní výrazy a přidat ovládací prvek do mapy ui, zvolte ikonu **Generovat kód.** Zadejte název testovací metody kódovaného uživatelského zařízení a popis metody, která bude přidána jako komentáře k metodě. Zvolte **Přidat a generovat**. Dále zvolte ikonu **Zavřít** a zavřete **Tvůrce programového testování ui**. To generuje kód podobný následující kód. Pokud je `AssertForAddTwoNumbers`například zadaný název , bude kód vypadat takto:

- Přidá volání metody assert AssertForAddTwoNumbers do testovací metody v testovacím souboru programového ui:

    ```csharp
    [TestMethod]
    public void CodedUITestMethod1()
    {
        this.UIMap.AddTwoNumbers();
        this.UIMap.AssertForAddTwoNumbers();
    }
    ```

     Tento soubor můžete upravit a změnit pořadí kroků a kontrolních výrazů nebo vytvořit nové zkušební metody. Chcete-li přidat další kód, umístěte kurzor na testovací metodu a v místní nabídce zvolte **Generovat kód pro kódovaný test ui**.

- Přidá metodu `AssertForAddTwoNumbers` volanou do mapy ui (*UIMap.uitest*). Tento soubor se otevře v **Editoru testu programového rozhraní**, kde můžete kontrolní výrazy upravit.

     ![Upravit assert pomocí editoru programových testů ui](../test/media/cuit_editor_assert.png)

     Další informace naleznete [v tématu Úprava programových testů ui pomocí editoru testů programového rozhraní](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

     Můžete také zobrazit generovaný kód metody assertion v *UIMap.Designer.cs*. Tento soubor byste však neměli upravovat. Pokud chcete vytvořit přizpůsobenou verzi kódu, zkopírujte metody do jiného souboru, například *UIMap.cs*, přejmenujte metody a upravte je tam.

    ```csharp
    public void AssertForAddTwoNumbers()
    {
        ...
    }
    ```

### <a name="select-a-hidden-control-using-the-keyboard"></a>Výběr skrytého ovládacího prvku pomocí klávesnice

Pokud ovládací prvek, který chcete vybrat, ztratí fokus a zmizí, když vyberete nástroj **Přidat kontrolní výrazy** z **tvůrce programového testu ui**:

Někdy při přidání ovládacích prvků a ověření jejich vlastností může být nutné použít klávesnici. Například při pokusu o záznam test kódovaného ui, který používá ovládací prvek nabídky pravým tlačítkem myši, seznam položek nabídky v ovládacím prvku ztratí fokus a zmizí při pokusu o výběr nástroje **Přidat kontrolní výrazy** z **Coded UI Test Builder**. To je znázorněno na následujícím obrázku, kde nabídka pravým tlačítkem myši v aplikaci Internet Explorer ztratí fokus a zmizí, pokud se pokusíte vybrat pomocí nástroje **Přidat kontrolní výrazy.**

![CodedUITest&#95;SelectControlKeyboard](../test/media/codeduitest_selectcontrolkeyboard.png)

Chcete-li pomocí klávesnice vybrat ovládací prvek ui, najeďte myší na ovládací prvek. Pak podržte klávesu **Ctrl** a **i** klíč ve stejnou dobu. Uvolněte klíče. Ovládací prvek je zaznamenán **tvůrcem testovaných kódovaných ui**.

#### <a name="manually-record-mouse-hovers"></a>Ruční záznam umístění myší

Pokud nemůžete zaznamenat ukazatel myši na ovládací prvek:

Za určitých okolností může určitý ovládací prvek, který se používá v testu programového ui, vyžadovat použití klávesnice k ručnímu záznamu událostí najezení myší. Například při testování formuláře systému Windows nebo Windows Presentation Foundation (WPF) aplikace, může být vlastní kód. Nebo může být definováno zvláštní chování pro najetí nad ovládací prvek, jako je například uzel stromu rozbalení, když uživatel najede nad ním. Chcete-li otestovat okolnosti, jako jsou tyto, musíte ručně upozornit **programové ui Test Builder,** že se pohybujenad ovládacím prvkem stisknutím předdefinované klávesy.

Při provádění test umítaný kód, najeďte nad ovládacím prvkem. Pak stiskněte a podržte **klávesu Ctrl**a podržte klávesy **Shift** a **R** na klávesnici. Uvolněte klíče. Událost při jezeně je **zaznamenána tvůrcem testů programového ui**.

![CodedUI&#95;Hover](../test/media/codedui_hover.png)

Po vygenerování testovací metody bude do *UIMap.Designer.cs* souboru přidán kód podobný následujícímu příkladu:

```csharp
// Mouse hover '1' label at (87, 9)
Mouse.Hover(uIItem1Text, new Point(87, 9));
```

### <a name="configure-mouse-hover-keyboard-assignments"></a>Konfigurace přiřazení klávesnice s myší

Pokud je přiřazení klíče pro zachycení událostí jehličnat myší používán jinde v mém prostředí:

V případě potřeby lze nakonfigurovat výchozí přiřazení **klávesklávesy Ctrl**+**Shift**+**R,** které se používá k použití událostí přechodu myší v testech programovaného rozhraní, aby bylo možné používat různé klávesy.

> [!WARNING]
> Za běžných okolností byste neměli měnit přiřazení klávesnice pro události přechodu myší. Při opětovném přiřazení klávesnice buďte opatrní. Vaše volba může být již používán jinde v rámci sady Visual Studio nebo aplikace, která je testována.

Chcete-li změnit přiřazení klávesnice, upravte následující konfigurační soubor:

*%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CodedUITestBuilder.exe.config*

V konfiguračním souboru `HoverKeyModifier` `HoverKey` změňte hodnoty kláves a upravte přiřazení klávesnice:

```xml
<!-- Begin : Background Recorder Settings -->
<!-- HoverKey to use. -->
<add key="HoverKeyModifier" value="Control, Shift"/>
<add key="HoverKey" value="R"/>
```

### <a name="set-implicit-mouse-hovers-for-the-web-browser"></a>Nastavení implicitních umístění myší pro webový prohlížeč

Pokud máte problémy se záznamem myši na webu:

Na mnoha webech se při najetí na určitý ovládací prvek rozbalí a zobrazí další podrobnosti. Obecně platí, že tyto vypadají jako nabídky v desktopových aplikacích. Vzhledem k tomu, že se jedná o běžný vzor, programové testy uživatelského rozhraní umožňují implicitní změny při procházení webu. Pokud například zaznamenáte zvýšení vznášejícíse v aplikaci Internet Explorer, je aktivována událost. Tyto události mohou vést k získání redundantní hodování získávání zaznamenány. Z tohoto důvodu jsou implicitní `ContinueOnError` změny `true` zabezpečení zaznamenány s nastavenou na v konfiguračním souboru testovacího ui. To umožňuje přehrávání pokračovat, pokud se událost přijetí k přehlédnutí nezdaří.

Chcete-li povolit nahrávání implicitních vznášejících se změn ve webovém prohlížeči, otevřete konfigurační soubor:

*%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CodedUITestBuilder.exe.config*

Ověřte, zda je `RecordImplicitiHovers` v konfiguračním souboru nastaven klíč nastaven na hodnotu uvedenou `true` v následující ukázce:

```xml
<!--Use this to enable/disable recording of implicit hovers.-->
<add key="RecordImplicitHover" value="true"/>
```

## <a name="customize-the-coded-ui-test"></a>Přizpůsobení testu programového ui

Po vytvoření programového testu ui ho můžete upravit pomocí některého z následujících nástrojů v sadě Visual Studio:

- Pomocí **programového tvůrce testů ui** přidat další ovládací prvky a ověření do testů. Podívejte se do části [Přidání ovládacích prvků a ověření jejich vlastností](#validate-the-properties-of-ui-controls) v tomto tématu.

- **Programový editor testů ui** umožňuje snadno upravit testy programovaného rozhraní. Pomocí **Programového editoru testů ui**můžete vyhledávat, zobrazovat a upravovat testovací metody. Akce ui a jejich přidružené ovládací prvky můžete také upravit v mapě ovládacího prvku ui. Další informace naleznete [v tématu Úprava programových testů ui pomocí editoru testů programového rozhraní](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

- **Editor kódu:**

  - Ručně přidejte kód pro ovládací prvky v testu, jak je popsáno v [kódované akce ovládacího prvku rozhraní a vlastnosti](#coded-ui-control-actions-and-properties) části v tomto tématu.

  - Po vytvoření test umítka kódovaného, můžete upravit tak, aby se řídit daty. Další informace naleznete [v tématu Vytvoření testu kódovaného ui řízeného daty](../test/creating-a-data-driven-coded-ui-test.md).

  - V programovém přehrávání testu ui můžete dát pokyn, aby test počkal, až se objeví určité události, jako je například okno, indikátor průběhu zmizí a tak dále. Chcete-li to provést, přidejte příslušnou metodu UITestControl.WaitForControlXXX(). Úplný seznam dostupných metod naleznete v tématu [Make coded UI tests wait for specific events during back back back the back the for the](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md) Příklad testu programového rozhraní, který čeká na povolení ovládacího prvku pomocí metody WaitForControlEnabled, naleznete v [tématu Návod: Vytváření, úpravy a údržba kódovaného testu ui](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md).

  - Programové testy ui zahrnují podporu pro některé ovládací prvky HTML5, které jsou součástí aplikace Internet Explorer 9 a Internet Explorer 10. Další informace naleznete [v tématu Použití ovládacích prvků HTML5 v kódovaných testech ui](../test/using-html5-controls-in-coded-ui-tests.md).

  - Kódovací pokyny k kódování kódovaného ui:

    - [Anatomie kódovaného testu ui](../test/anatomy-of-a-coded-ui-test.md)

    - [Doporučené postupy pro kódované testy rozhraní](../test/best-practices-for-coded-ui-tests.md)

    - [Testování velké aplikace s více mapami ui](../test/testing-a-large-application-with-multiple-ui-maps.md)

    - [Podporované konfigurace a platformy pro kódované testy a záznamy akcí](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)

### <a name="the-generated-code"></a>Generovaný kód

Když zvolíte **Generovat kód**, vytvoří se několik částí kódu:

- Řádek ve zkušební metodě.

    ```csharp
    [CodedUITest]
    public class CodedUITest1
    { ...
      [TestMethod]
      public void CodedUITestMethod1()
      {
          this.UIMap.AddTwoNumbers();
          // To generate more code for this test, select
          // "Generate Code" from the shortcut menu.      }
    }
    ```

     Kliknutím pravým tlačítkem myši na tuto metodu můžete přidat další zaznamenané akce a ověření. Můžete jej také upravit ručně rozšířit nebo upravit kód. Můžete například uzavřít některé kód ve smyčce.

     Můžete také přidat nové testovací metody a přidat kód k nim stejným způsobem. Každá zkušební metoda `[TestMethod]` musí mít atribut.

- Metoda v *UIMap.uitest*.

     Tato metoda zahrnuje podrobnosti o zaznamenaných akcích nebo hodnotu, kterou jste ověřili. Tento kód můžete upravit otevřením *UIMap.uitest*. Otevře se ve specializovaném editoru, ve kterém můžete odstranit nebo refaktorovat zaznamenané akce.

     Vygenerovanou metodu můžete také zobrazit v *UIMap.Designer.cs*. Tato metoda provádí akce, které jste zaznamenali při spuštění testu.

    ```csharp
    // File: UIMap.Designer.cs
    public partial class UIMap
    {
      /// <summary>
      /// Add two numbers
      /// </summary>
      public void AddTwoNumbers()
      { ...   }
    }
    ```

    > [!WARNING]
    > Tento soubor byste neměli upravovat, protože bude znovu vygenerován při vytváření dalších testů.

     Můžete vytvořit upravené verze těchto metod jejich zkopírováním do *UIMap.cs*. Můžete například vytvořit parametrizovanou verzi, kterou můžete volat z testovací metody:

    ```csharp
    // File: UIMap.cs
    public partial class UIMap // Same partial class
    {
      /// <summary>
      /// Add two numbers - parameterized version
      /// </summary>
      public void AddTwoNumbers(int firstNumber, int secondNumber)
      { ...   // Code modified to use parameters.
      }
    }
    ```

- Deklarace v *UIMap.uitest*.

    Tyto deklarace představují ovládací prvky ui aplikace, které jsou používány test. Jsou používány generovaným kódem k ovládání ovládacích prvků a přístupu k jejich vlastnostem.

    Můžete je také použít, pokud napíšete vlastní kód. Testovací metoda může například zvolit hypertextový odkaz ve webové aplikaci, zadat hodnotu do textového pole nebo odbočit a provést různé testovací akce na základě hodnoty v poli.

    Můžete přidat více programové testy ui a více objektů a souborů mapování rozhraní pro usnadnění testování velké aplikace. Další informace naleznete [v tématu Test velké aplikace s více map ui](../test/testing-a-large-application-with-multiple-ui-maps.md).

Další informace o generovaném kódu naleznete [v tématu Anatomie programového testu uI](../test/anatomy-of-a-coded-ui-test.md).

## <a name="coded-ui-control-actions-and-properties"></a>Akce a vlastnosti kódovaného ovládacího prvku rozhraní

Při práci s ovládacími prvky testování ui v programové testy ui jsou rozděleny do dvou částí: akce a vlastnosti.

- První část se skládá z akcí, které můžete provádět na ovládacích prvcích testování ui. Například programované testy ui můžete simulovat kliknutí myší na ovládací prvek testu ui nebo simulovat klávesy zadané na klávesnici ovlivnit ovládací prvek testu ui.

- Druhá část se skládá z povolení získat a nastavit vlastnosti na ovládací prvek testu ui. Například programové testy uznaného rozhraní můžete `ListBox`získat počet `CheckBox` položek v , nebo nastavit do vybraného stavu.

**Přístup k akcím ovládacího prvku testu ui**

Chcete-li provádět akce na ovládací prvky testu ui, jako <xref:Microsoft.VisualStudio.TestTools.UITesting.Mouse> je <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard> například klepnutí myší nebo akce klávesnice, použijte metody v a třídy:

- Chcete-li provést akci orientovanou na myš, například klepnutí myší, na testovací ovládací prvek ui, použijte <xref:Microsoft.VisualStudio.TestTools.UITesting.Mouse.Click%2A>.

     `Mouse.Click(buttonCancel);`

- Chcete-li provést akci orientovanou na klávesnici, <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A>například zadání do ovládacího prvku pro úpravy, použijte .

     `Keyboard.SendKeys(textBoxDestination, @"C:\Temp\Output.txt");`

**Přístup k vlastnostem ovládacího prvku testu uI**

Chcete-li získat a nastavit hodnoty vlastností řízení uživatelského rozhraní, můžete přímo získat nebo <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A?displayProperty=fullName> <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A?displayProperty=fullName> nastavit hodnoty vlastnosti ovládacího prvku, nebo můžete použít metody a s názvem konkrétní vlastnosti, kterou chcete získat nebo nastavit.

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A>vrátí objekt, který pak může být <xref:System.Type>přetypován na příslušný . <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A>přijme objekt pro hodnotu vlastnosti.

### <a name="to-get-or-set-properties-from-ui-test-controls-directly"></a>Získání nebo nastavení vlastností z testovacích ovládacích prvků uI přímo

S ovládacími <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl>prvky, které jsou odvozeny z , například [HtmlList](xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls.HtmlList) nebo [WinComboBox](xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls.WinComboBox), můžete získat nebo nastavit jejich hodnoty vlastností přímo. Následující kód ukazuje některé příklady:

```csharp
int i = myHtmlList.ItemCount;
myWinCheckBox.Checked = true;
```

### <a name="to-get-properties-from-ui-test-controls"></a>Získání vlastností z testovacích ovládacích prvků uI

- Chcete-li získat hodnotu vlastnosti z ovládacího prvku, použijte <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A>.

- Chcete-li určit vlastnost ovládacího prvku získat, `PropertyNames` použijte příslušný řetězec z <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A>třídy v každém ovládacím prvku jako parametr .

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A>vrátí příslušný datový typ, ale tato vrácená hodnota je přetypována <xref:System.Object>jako . Vrácení <xref:System.Object> pak musí být přetypován jako příslušný typ.

     Příklad:

     `int i = (int)GetProperty(myHtmlList.PropertyNames.ItemCount);`

### <a name="to-set-properties-for-ui-test-controls"></a>Nastavení vlastností testovacích ovládacích prvků uI

- Chcete-li nastavit vlastnost v <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A>ovládacím prvku, použijte .

- Chcete-li určit vlastnost ovládacího prvku, který `PropertyNames` chcete nastavit, použijte <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A>příslušný řetězec z třídy jako první parametr do , s hodnotou vlastnosti jako druhý parametr.

     Příklad:

     `SetProperty(myWinCheckBox.PropertyNames.Checked, true);`

## <a name="debug"></a>Ladění

Můžete analyzovat programové testy ui pomocí protokolů test kódovaného rozhraní. Protokoly testovaných kódovaných ui filtrují a zaznamenávají důležité informace o spuštění testů programového ui. Formát protokolů umožňuje rychle ladit problémy. Další informace naleznete v [tématu Analýza kódovaných testů ui pomocí kódovaných protokolů testů ui](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md).

## <a name="whats-next"></a>Co dále?

**Další možnosti pro spuštění programových testů ui:** Programové testy ui můžete spustit přímo z visual studia, jak je popsáno výše v tomto tématu. Kromě toho můžete spustit automatizované testy ui z Microsoft Test Manager nebo pomocí Azure Pipelines. Pokud jsou testy programového rozhraní automatizované, musí při jejich spuštění pracovat s plochou, na rozdíl od jiných automatizovaných testů.

- [Spouštění testování částí pomocí Průzkumníka testů](../test/run-unit-tests-with-test-explorer.md)

- [Spuštění testů v procesu sestavení](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts)

- [Postup: Nastavení testovacího agenta pro spuštění testů, které interagují s plochou](https://msdn.microsoft.com/Library/3a94dd07-6d17-402c-ae8f-7947143755c9)

**Přidání podpory pro vlastní ovládací prvky:**  Coded ui testování rozhraní rozhraní nepodporuje všechny možné ui a nemusí podporovat ui, které chcete testovat. Například nelze okamžitě vytvořit test programovaného rozhraní ui pro aplikaci Microsoft Excel. Můžete však vytvořit rozšíření coded rozhraní pro testování rozhraní, které podporuje vlastní ovládací prvek.

- [Povolení programového testování ovládacích prvků v rozhraní](../test/enable-coded-ui-testing-of-your-controls.md)

- [Rozšíření kódovaných testů a záznamů akcí v oblasti usměrňovaného rozhraní](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)

Programové testy ui se často používají k automatizaci ručních testů. Další informace o ručních testech naleznete v [tématu Spuštění ručních testů pomocí správce testů společnosti Microsoft](/azure/devops/test/mtm/run-manual-tests-with-microsoft-test-manager?view=vsts). Další informace o automatizovaných testech naleznete [v tématu Test tools in Visual Studio](../test/improve-code-quality.md).

## <a name="see-also"></a>Viz také

- [Záznam a přehrávání ručních testů](/azure/devops/test/mtm/record-play-back-manual-tests?view=vsts)
- [Xamarin.UITest](/appcenter/test-cloud/uitest/)
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>
- [Návod: Vytvoření, úprava a údržba programového testu ui](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
- [Vytvoření programového testu ui pro testování aplikace UPW](test-uwp-app-with-coded-ui-test.md)
- [Anatomie programového testu ui](../test/anatomy-of-a-coded-ui-test.md)
- [Doporučené postupy pro testy programového rozhraní](../test/best-practices-for-coded-ui-tests.md)
- [Testování velké aplikace s více mapami ui](../test/testing-a-large-application-with-multiple-ui-maps.md)
