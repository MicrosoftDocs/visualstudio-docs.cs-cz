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
ms.openlocfilehash: 3d18282cf0fbd8782eb7abce05794e0b2eb1c5c1
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2020
ms.locfileid: "90035739"
---
# <a name="use-coded-ui-test-to-test-your-code"></a>Použití programového testu uživatelského rozhraní k otestování kódu

Programový test UI (CUITs) diskovou aplikaci prostřednictvím svého uživatelského rozhraní (UI). Tyto testy zahrnují funkční testování ovládacích prvků uživatelského rozhraní. Umožňují ověřit, že celá aplikace, včetně jejího uživatelského rozhraní, funguje správně. Programové testy uživatelského rozhraní jsou užitečné v případě, že je v uživatelském rozhraní k dispozici ověřování nebo jiná logika, například na webové stránce. Používají se také často k automatizaci stávajícího manuálního testu.

Vytvoření programového testu uživatelského rozhraní v aplikaci Visual Studio je snadné. Stačí provést test ručně, zatímco je program Tvůrce programového **testu uživatelského rozhraní** spuštěn na pozadí. Můžete také určit, které hodnoty se mají zobrazit v určitých polích. **Tvůrce programového testu uživatelského rozhraní** zaznamenává vaše akce a generuje z nich kód. Po vytvoření testu ho můžete upravit ve specializovaném editoru, který vám umožní upravit sekvenci akcí.

Tvůrce specializovaného programového **testu uživatelského rozhraní** a editor usnadňuje vytváření a úpravy programových testů uživatelského rozhraní, a to i v případě, že jsou hlavní dovednosti soustředěny při testování namísto kódování. Ale pokud jste vývojář a chcete rozšířit test pokročilým způsobem, je kód strukturovaný, aby bylo snadné ho zkopírovat a přizpůsobit. Můžete například zaznamenat test a koupit něco na webu a potom upravit generovaný kód a přidat smyčku, která nakupuje mnoho položek.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="requirements"></a>Požadavky

- Visual Studio Enterprise
- Komponenta programového testu uživatelského rozhraní

Další informace o tom, které platformy a konfigurace podporuje programové testy UI, najdete v tématu [podporované platformy](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md).

## <a name="install-the-coded-ui-test-component"></a>Instalace komponenty programového testu uživatelského rozhraní

Chcete-li získat přístup k nástrojům programového testu uživatelského rozhraní a šablonám, nainstalujte komponentu programový **test uživatelského rozhraní** sady Visual Studio.

1. Spusťte **instalační program pro Visual Studio** výběrem **nástrojů**  >  **získat nástroje a funkce**.

1. V **instalační program pro Visual Studio**zvolte kartu **jednotlivé komponenty** a potom přejděte dolů k části **ladění a testování** . Vyberte komponentu programového **testu uživatelského rozhraní** .

   ![Komponenta programového testu uživatelského rozhraní](media/coded-ui-test-component.png)

1. Vyberte **Upravit**.

## <a name="create-a-coded-ui-test"></a>Vytvoření programového testu uživatelského rozhraní

1. Vytvořte projekt programového testu uživatelského rozhraní.

   Programové testy uživatelského rozhraní musí být obsaženy v projektu programového testu uživatelského rozhraní. Pokud ještě nemáte projekt programového testu UI, vytvořte ho. Vyberte **soubor**  >  **Nový**  >  **projekt**. Vyhledejte a vyberte šablonu projektu **projektu programového testu uživatelského rozhraní** .

   ::: moniker range="vs-2017"

   ![Šablona projektu programový test uživatelského rozhraní v dialogovém okně Nový projekt](media/coded-ui-test-project-template.png)

   ::: moniker-end

   > [!NOTE]
   > Pokud nevidíte šablonu **projektu programový test uživatelského rozhraní** , je nutné [nainstalovat komponentu PROGRAMového testu uživatelského](../test/use-ui-automation-to-test-your-code.md#install-the-coded-ui-test-component)rozhraní.

2. Přidejte soubor programového testu uživatelského rozhraní.

     Pokud jste právě vytvořili projekt kódovaného uživatelského rozhraní, je první soubor UI přidán automaticky. Chcete-li přidat další testovací soubor, otevřete místní nabídku projektu programového testu uživatelského rozhraní v **Průzkumník řešení**a pak zvolte možnost **Přidat**programový  >  **test uživatelského rozhraní**.

     V dialogovém okně **generovat kód pro programový test uživatelského rozhraní** vyberte možnost **zaznamenat akce**  >  **Upravit mapu uživatelského rozhraní nebo přidat kontrolní výrazy**.

     ![Dialogové okno generovat kód pro programový test uživatelského rozhraní](media/generate-code-for-coded-ui-test.png)

     Zobrazí se Tvůrce programového **testu uživatelského rozhraní** .

     ![Tvůrce programového testu uživatelského rozhraní](../test/media/codedui_testbuilder.png)

3. Zaznamenejte sekvenci akcí.

     **Chcete-li spustit záznam**, vyberte ikonu **záznamu** . Proveďte akce, které chcete ve své aplikaci testovat, včetně spuštění aplikace, pokud je to nutné. Například při testování webové aplikace, můžete spustit prohlížeč, přejít na web a přihlásit se k aplikaci.

     **Chcete-li záznam pozastavit**, například pokud potřebujete pracovat s příchozí poštou, vyberte možnost **pozastavit**.

    > [!WARNING]
    > Budou zaznamenány všechny akce prováděné na ploše. Pozastaví nahrávání, pokud provádíte akce, které mohou vést k zahrnutí citlivých dat do záznamu.

     **Chcete-li odstranit akce** , které jste si poznamenali omylem, vyberte **upravit kroky**.

     **Chcete-li vygenerovat kód** , který bude replikovat vaše akce, vyberte ikonu **generovat kód** a zadejte název a popis pro metodu programového testu uživatelského rozhraní.

4. Ověřte hodnoty v polích uživatelského rozhraní, jako jsou textová pole.

     Zvolte **Přidat kontrolní výrazy** v Tvůrci programového **testu UI**a pak zvolte ovládací prvek uživatelského rozhraní v běžící aplikaci. V seznamu vlastností, které se zobrazí, vyberte vlastnost, například **text** v textovém poli. V místní nabídce vyberte možnost **Přidat kontrolní výraz**. V dialogovém okně vyberte operátor porovnání, hodnotu porovnání a chybovou zprávu.

     Zavřete okno kontrolního výrazu a klikněte na příkaz **generovat kód**.

     ![Cílový prvek programového testu uživatelského rozhraní](../test/media/codedui_1.png)

    > [!TIP]
    > Alternativní mezi akcemi záznamu a ověřováním hodnot. Vygenerujte kód na konci každé posloupnosti akcí nebo ověření. Pokud chcete, budete moct později vkládat nové akce a ověřování.

     Další podrobnosti najdete v tématu [ověření vlastností ovládacích prvků](#validate-the-properties-of-ui-controls).

5. Zobrazit generovaný testovací kód.

     Chcete-li zobrazit generovaný kód, zavřete okno Tvůrce testu uživatelského rozhraní. V kódu uvidíte názvy, které jste přiřadili jednotlivým krokům. Kód je v souboru UI, který jste vytvořili:

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

   Umístěte kurzor do vhodného bodu v testovací metodě a potom v místní nabídce zvolte možnost **generovat kód pro programový test uživatelského rozhraní**. V tomto okamžiku bude vložen nový kód.

7. Upravte podrobnosti testovacích akcí a kontrolních výrazů.

     Otevřete *UIMap. UITest*. Tento soubor se otevře v **editoru programového testu UI**, kde můžete upravit libovolnou sekvenci akcí, které jste si poznamenali, a upravit kontrolní výrazy.

     ![Editor programového testu UI](../test/media/cuit_editor_edit.png)

     Další informace naleznete v tématu [Úpravy programových testů uživatelského rozhraní pomocí editoru programového testu UI](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

8. Spusťte test.

   Použijte Průzkumníka testů nebo otevřete místní nabídku v testovací metodě a pak zvolte možnost **Spustit testy**. Další informace o tom, jak spustit testy, najdete v tématu [spuštění testů jednotek pomocí Průzkumníka testů](../test/run-unit-tests-with-test-explorer.md) a *dalších možností pro spuštění programových testů uživatelského rozhraní* v části [co dál?](#whats-next) na konci tohoto tématu.

Zbývající části tohoto tématu poskytují další podrobnosti o krocích v tomto postupu.

Podrobnější příklad naleznete v tématu [Návod: vytváření, úpravy a údržba kódovaného testu uživatelského rozhraní](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md). V tomto návodu vytvoříte jednoduchou aplikaci Windows Presentation Foundation (WPF), která ukazuje, jak vytvořit, upravit a udržovat programový test uživatelského rozhraní. Návod poskytuje řešení pro opravu testů, které byly poškozeny různými chybami časování a refaktoringem ovládacích prvků.

## <a name="start-and-stop-the-application-under-test"></a>Spuštění a zastavení testované aplikace

Pokud nechcete spouštět a zastavovat aplikaci, prohlížeč nebo databázi samostatně pro každý test, proveďte jednu z následujících akcí:

- Pokud nechcete zaznamenávat akce pro spuštění testované aplikace, musíte aplikaci spustit před výběrem ikony **záznamu** .

- Na konci testu proces, ve kterém je test spuštěn, je ukončen. Pokud jste aplikaci spustili v testu, aplikace se obvykle zavře.  Pokud nechcete, aby test zavřel aplikaci při ukončení, přidejte do svého řešení soubor *. runsettings* a použijte `KeepExecutorAliveAfterLegacyRun` možnost. Další informace najdete v tématu [konfigurace testů jednotek pomocí souboru. runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

- Přidejte metodu Initialize testu, která je označena `[TestInitialize]` atributem, který spouští kód na začátku každé testovací metody. Například můžete spustit aplikaci z metody TestInitialize.

- Přidejte metodu vyčištění testu identifikovanou `[TestCleanup]` atributem, který spustí kód na konci každé testovací metody. Například metoda zavření aplikace by mohla být volána z metody TestCleanup.

## <a name="validate-the-properties-of-ui-controls"></a>Ověřit vlastnosti ovládacích prvků uživatelského rozhraní

Tvůrce programového **testu UI** můžete použít k přidání ovládacího prvku uživatelského rozhraní (UI) do [UIMap](/previous-versions/dd580454(v=vs.140)) pro váš test nebo k vygenerování kódu pro metodu ověřování, která používá kontrolní výraz pro ovládací prvek uživatelského rozhraní.

Chcete-li generovat kontrolní výrazy pro ovládací prvky uživatelského rozhraní, vyberte nástroj **Přidat kontrolní** výraz v Tvůrci programového **testu uživatelského rozhraní** a přetáhněte jej do ovládacího prvku testované aplikace, kterou chcete ověřit, je správný. Jakmile se v poli zobrazí ovládací prvek, uvolněte tlačítko myši. Kód třídy ovládacího prvku je okamžitě vytvořen v souboru *UIMap.Designer.cs* .

![Cílový prvek programového testu uživatelského rozhraní](../test/media/codedui_1.png)

Vlastnosti tohoto ovládacího prvku jsou nyní uvedeny v dialogovém okně **Přidat kontrolní výrazy** .

Dalším způsobem navigace na konkrétní ovládací prvek je výběr šipky **(<<)** pro rozšíření zobrazení pro **mapu ovládacího prvku uživatelského rozhraní**. Chcete-li najít nadřazený ovládací prvek, na stejné úrovni nebo podřízený ovládací prvek, můžete kliknout kamkoli na mapu a pomocí kláves se šipkami se pohybovat kolem stromu.

![Vlastnosti kódovaného testu uživatelského rozhraní](../test/media/codedui_2.png)

> [!TIP]
> Pokud nevidíte žádné vlastnosti při výběru ovládacího prvku v aplikaci nebo když ovládací prvek není zobrazen v mapě ovládacího prvku uživatelského rozhraní, ověřte, zda má ovládací prvek v kódu aplikace jedinečné ID. Jedinečné ID může být atribut ID HTML nebo UId WPF.

Potom otevřete místní nabídku vlastnosti ovládacího prvku uživatelského rozhraní, který chcete ověřit, a pak přejděte na **Přidat kontrolní výraz**. V dialogovém okně **Přidat kontrolní výraz** vyberte **komparátor** pro váš kontrolní výraz, například <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A> a zadejte hodnotu pro kontrolní výraz v **hodnotě porovnání**.

![Kontrolní výrazy programového testu UI](../test/media/codedui_3.png)

Když jste přidali všechny kontrolní výrazy pro svůj test, klikněte na **tlačítko OK**.

Chcete-li vygenerovat kód pro kontrolní výrazy a přidat ovládací prvek do mapy uživatelského rozhraní, klikněte na ikonu **generovat kód** . Zadejte název metody programového testu uživatelského rozhraní a popis metody, který bude přidán jako komentář pro metodu. Vyberte možnost **Přidat a generovat**. Potom klikněte na ikonu **Zavřít** a zavřete Tvůrce programového **testu uživatelského rozhraní**. Tím se vygeneruje kód podobný následujícímu kódu. Pokud název, který jste zadali, je například `AssertForAddTwoNumbers` , kód bude vypadat jako v tomto příkladu:

- Přidá volání metody Assert AssertForAddTwoNumbers do testovací metody v souboru programového testu uživatelského rozhraní:

    ```csharp
    [TestMethod]
    public void CodedUITestMethod1()
    {
        this.UIMap.AddTwoNumbers();
        this.UIMap.AssertForAddTwoNumbers();
    }
    ```

     Úpravou tohoto souboru můžete změnit pořadí kroků a kontrolních výrazů nebo vytvořit nové testovací metody. Chcete-li přidat další kód, umístěte kurzor na testovací metodu a v místní nabídce vyberte možnost **generovat kód pro programový test uživatelského rozhraní**.

- Přidá metodu volanou `AssertForAddTwoNumbers` do vaší mapy uživatelského rozhraní (*UIMap. UITest*). Tento soubor se otevře v **editoru programového testu UI**, kde můžete upravit kontrolní výrazy.

     ![Upravit kontrolní výraz pomocí editoru programového testu UI](../test/media/cuit_editor_assert.png)

     Další informace naleznete v tématu [Úpravy programových testů uživatelského rozhraní pomocí editoru programového testu UI](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

     Můžete také zobrazit generovaný kód metody kontrolního výrazu v *UIMap.Designer.cs*. Tento soubor byste ale neměli upravovat. Chcete-li vytvořit upravenou verzi kódu, zkopírujte metody do jiného souboru, například *UIMap.cs*, přejmenujte metody a upravte je zde.

    ```csharp
    public void AssertForAddTwoNumbers()
    {
        ...
    }
    ```

### <a name="select-a-hidden-control-using-the-keyboard"></a>Výběr skrytého ovládacího prvku pomocí klávesnice

Pokud ovládací prvek, který chcete vybrat, ztratí fokus a zmizí při výběru nástroje **Přidat kontrolní** výraz z Tvůrce programového **testu uživatelského rozhraní**:

Někdy, když přidáte ovládací prvky a ověříte jejich vlastnosti, možná budete muset použít klávesnici. Například při pokusu o nahrání kódovaného testu uživatelského rozhraní, který používá ovládací prvek nabídky po kliknutí pravým tlačítkem myši, seznam položek nabídky v ovládacím prvku ztratí fokus a zmizí při pokusu o výběr nástroje **Přidat kontrolní výrazy** z Tvůrce programového **testu uživatelského rozhraní**. To je znázorněno na následujícím obrázku, kde se nabídka kliknutí pravým tlačítkem v aplikaci Internet Explorer ztratí fokus a zmizí, pokud se pokusíte o výběr pomocí nástroje **Přidat kontrolní výrazy** .

![CodedUITest&#95;SelectControlKeyboard](../test/media/codeduitest_selectcontrolkeyboard.png)

Chcete-li použít klávesnici k výběru ovládacího prvku uživatelského rozhraní, najeďte myší nad ovládací prvek myší. Pak podržte stisknutou klávesu **CTRL** a klávesu **I** . Uvolněte klíče. Ovládací prvek je zaznamenán pomocí Tvůrce programového **testu uživatelského rozhraní**.

#### <a name="manually-record-mouse-hovers"></a>Ruční záznam najetí myší

Pokud nemůžete nahrávat ukazatel myši na ovládacím prvku:

Za určitých okolností může konkrétní ovládací prvek, který se používá v programovém testu UI, vyžadovat použití klávesnice k ručnímu záznamu událostí při přechodu myší. Například při testování aplikace Windows Form nebo Windows Presentation Foundation (WPF) může existovat vlastní kód. Nebo může být definováno speciální chování pro najetí myší nad ovládací prvek, jako je například rozbalování uzlu stromu, když na něj uživatel najede myší. Chcete-li otestovat okolnosti, jako jsou tyto, je nutné ručně nastavit program Tvůrce programového **testu uživatelského rozhraní** , který přejedete nad ovládací prvek pomocí klávesových zkratek předdefinovaných klávesových zkratek.

Při provádění programového testu uživatelského rozhraní, najeďte myší na ovládací prvek. Pak stiskněte a podržte **klávesu CTRL**, zatímco stisknete a podržíte klávesy **SHIFT** a **R** na klávesnici. Uvolněte klíče. Událost najetí myší je zaznamenána pomocí **Tvůrce programového testu uživatelského rozhraní**.

![CodedUI&#95;najetí myší](../test/media/codedui_hover.png)

Po vygenerování testovací metody se kód podobný následujícímu příkladu přidá do souboru *UIMap.Designer.cs* :

```csharp
// Mouse hover '1' label at (87, 9)
Mouse.Hover(uIItem1Text, new Point(87, 9));
```

### <a name="configure-mouse-hover-keyboard-assignments"></a>Konfigurace přiřazení klávesnice při najetí myší

Pokud se přiřazení klíče pro zachytávání událostí kurzoru myši používá jinde v mém prostředí:

V případě potřeby je výchozí přiřazení klávesnice **CTRL** + **SHIFT** + **R** , které se používá k aplikování událostí myši myší v programových testech UI, možné nakonfigurovat tak, aby používala různé klíče.

> [!WARNING]
> Nemusíte měnit přiřazení klávesnice pro události ukazatele myši za běžných okolností. Při opětovném přiřazení klávesnice použijte upozornění. Vaše volba se už možná používá jinde v sadě Visual Studio nebo v testované aplikaci.

Chcete-li změnit přiřazení klávesnice, upravte následující konfigurační soubor:

*% ProgramFiles (x86)% \ Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CodedUITestBuilder.exe.config*

V konfiguračním souboru změňte hodnoty `HoverKeyModifier` klíčů a, `HoverKey` aby se změnily přiřazení klávesnice:

```xml
<!-- Begin : Background Recorder Settings -->
<!-- HoverKey to use. -->
<add key="HoverKeyModifier" value="Control, Shift"/>
<add key="HoverKey" value="R"/>
```

### <a name="set-implicit-mouse-hovers-for-the-web-browser"></a>Nastavit implicitní ukazatele myši pro webový prohlížeč

Pokud máte problémy s nahráváním ukazatele myši na webu:

Pokud na mnoha webech najedete myší na určitý ovládací prvek, rozbalí se a zobrazí se další podrobnosti. Obecně tyto vypadají jako nabídky v aplikacích klasické pracovní plochy. Vzhledem k tomu, že se jedná o společný vzor, kódované testy uživatelského rozhraní umožňují implicitní najetí myší na prohlížení webu. Pokud například záznam najedete myší v aplikaci Internet Explorer, aktivuje se událost. Tyto události mohou vést k nahranému nadbytečnému najetí myší. Z tohoto důvodu jsou implicitní najetí myší zaznamenávány s `ContinueOnError` nastavením do `true` konfiguračního souboru testu uživatelského rozhraní. To umožňuje, aby přehrávání pokračovalo i v případě neúspěchu události přechodu myší.

Chcete-li povolit záznam implicitních pojetí myší ve webovém prohlížeči, otevřete konfigurační soubor:

*% ProgramFiles (x86)% \ Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CodedUITestBuilder.exe.config*

Ověřte, že konfigurační soubor má klíč `RecordImplicitiHovers` nastavený na hodnotu `true` , jak je znázorněno v následující ukázce:

```xml
<!--Use this to enable/disable recording of implicit hovers.-->
<add key="RecordImplicitHover" value="true"/>
```

## <a name="customize-the-coded-ui-test"></a>Přizpůsobení kódovaného testu uživatelského rozhraní

Po vytvoření programového testu UI ho můžete upravit pomocí některého z následujících nástrojů v aplikaci Visual Studio:

- Pomocí **Tvůrce programového testu UI** přidejte do testů další ovládací prvky a ověřování. Viz část [Přidání ovládacích prvků a ověření jejich vlastností](#validate-the-properties-of-ui-controls) v tomto tématu.

- **Editor programového testu UI** umožňuje snadno upravit kódované testy uživatelského rozhraní. Pomocí **editoru programového testu UI**můžete vyhledat, zobrazit a upravit testovací metody. Můžete také upravit akce uživatelského rozhraní a jejich přidružené ovládací prvky v mapě ovládacího prvku uživatelského rozhraní. Další informace naleznete v tématu [Úpravy programových testů uživatelského rozhraní pomocí editoru programového testu UI](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

- **Editor kódu:**

  - Ručně přidejte kód pro ovládací prvky v testu, jak je popsáno v části programové [akce a vlastnosti ovládacího prvku uživatelského rozhraní](#coded-ui-control-actions-and-properties) v tomto tématu.

  - Po vytvoření programového testu UI ho můžete upravit tak, aby byl řízený daty. Další informace najdete v tématu [vytvoření kódovaného programového testu UI založeného na datech](../test/creating-a-data-driven-coded-ui-test.md).

  - V průběhu přehrávání programového testu uživatelského rozhraní můžete určit, že se má test čekat na výskyt určitých událostí, jako je okno, které se má zobrazit, indikátor průběhu zmizí atd. Chcete-li to provést, přidejte příslušnou metodu UITestControl. WaitForControlXXX (). Úplný seznam dostupných metod naleznete v tématu vytváření programových [testů uživatelského rozhraní čeká na konkrétní události během přehrávání](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md). Příklad kódovaného testu uživatelského rozhraní, který čeká na povolení ovládacího prvku pomocí metody metody WaitForControlEnabled, naleznete v tématu [Návod: vytváření, úpravy a údržba programového testu uživatelského rozhraní](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md).

  - Programové testy UI zahrnují podporu pro některé ovládací prvky HTML5, které jsou součástí aplikace Internet Explorer 9 a Internet Explorer 10. Další informace naleznete v tématu [použití ovládacích prvků HTML5 v programových testech UI](../test/using-html5-controls-in-coded-ui-tests.md).

  - Pokyny pro kódování programového testu uživatelského rozhraní:

    - [Anatomie kódovaného testu uživatelského rozhraní](../test/anatomy-of-a-coded-ui-test.md)

    - [Osvědčené postupy pro programové testy uživatelského rozhraní](../test/best-practices-for-coded-ui-tests.md)

    - [Testování rozsáhlé aplikace s více mapami uživatelského rozhraní](../test/testing-a-large-application-with-multiple-ui-maps.md)

    - [Podporované konfigurace a platformy pro programové testy uživatelského rozhraní a záznamy akcí](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)

### <a name="the-generated-code"></a>Generovaný kód

Když zvolíte možnost **generovat kód**, vytvoří se několik částí kódu:

- Řádek v testovací metodě.

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

     Kliknutím pravým tlačítkem na tuto metodu můžete přidat další zaznamenané akce a ověření. Můžete ji také upravit ručně a kód tak rozšíříte nebo upravíte. Například můžete uzavřít část kódu ve smyčce.

     Můžete také přidat nové testovací metody a přidat kód do nich stejným způsobem. Každá testovací metoda musí mít `[TestMethod]` atribut.

- Metoda v *UIMap. UITest*.

     Tato metoda zahrnuje podrobné informace o vámi zaznamenaných akcích nebo o hodnotě, kterou jste ověřili. Tento kód můžete upravit otevřením *UIMap. UITest*. Otevře se ve specializovaném editoru, ve kterém můžete zaznamenané akce odstranit nebo Refaktorovat.

     Vygenerovanou metodu můžete zobrazit také v *UIMap.Designer.cs*. Tato metoda provádí akce, které jste si poznamenali při spuštění testu.

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
    > Tento soubor byste neměli upravovat, protože se znovu vygeneruje při vytváření dalších testů.

     Upravené verze těchto metod můžete upravit jejich zkopírováním do *UIMap.cs*. Můžete například vytvořit parametrizovanou verzi, kterou můžete volat z testovací metody:

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

- Deklarace v *UIMap. UITest*.

    Tyto deklarace představují ovládací prvky uživatelského rozhraní aplikace, které jsou používány vaším testem. Jsou používány generovaným kódem k provozování ovládacích prvků a k přístupu ke svým vlastnostem.

    Můžete je také použít, pokud píšete vlastní kód. Například můžete mít testovací metodu zvolit hypertextový odkaz ve webové aplikaci, zadat hodnotu do textového pole nebo vytvořit větev a provést jiné testovací akce na základě hodnoty v poli.

    Pro usnadnění testování rozsáhlých aplikací můžete přidat více programových testů UI a více objektů a souborů map uživatelského rozhraní. Další informace najdete v tématu [testování velké aplikace s více mapami uživatelského rozhraní](../test/testing-a-large-application-with-multiple-ui-maps.md).

Další informace o vygenerovaném kódu naleznete v tématu [anatomie kódovaného testu uživatelského rozhraní](../test/anatomy-of-a-coded-ui-test.md).

## <a name="coded-ui-control-actions-and-properties"></a>Programové akce a vlastnosti ovládacího prvku uživatelského rozhraní

Při práci s ovládacími prvky testu uživatelského rozhraní v programových testech UI jsou rozděleny do dvou částí: akce a vlastnosti.

- První část se skládá z akcí, které lze provádět v ovládacích prvcích testu uživatelského rozhraní. Například kódované testy uživatelského rozhraní mohou simulovat kliknutí myší na ovládací prvek testu uživatelského rozhraní nebo simulovat klíče, které jsou zadány na klávesnici a ovlivnit ovládací prvek testu uživatelského rozhraní.

- Druhá část se skládá z možnosti získat a nastavit vlastnosti ovládacího prvku test uživatelského rozhraní. Například kódované testy uživatelského rozhraní mohou získat počet položek v `ListBox` , nebo nastavit `CheckBox` na vybraný stav.

**Přístup k akcím ovládacího prvku test uživatelského rozhraní**

Chcete-li provádět akce s ovládacími prvky testu uživatelského rozhraní, jako je kliknutí myší nebo akce klávesnice, použijte metody v <xref:Microsoft.VisualStudio.TestTools.UITesting.Mouse> <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard> třídách a:

- K provedení akce orientované na myš, jako je například kliknutí myší, na ovládacím prvku test uživatelského rozhraní, použijte <xref:Microsoft.VisualStudio.TestTools.UITesting.Mouse.Click%2A> .

     `Mouse.Click(buttonCancel);`

- K provedení akcí orientovaných na klávesnici, jako je například psaní do ovládacího prvku pro úpravy, použijte <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A> .

     `Keyboard.SendKeys(textBoxDestination, @"C:\Temp\Output.txt");`

**Přístup k vlastnostem ovládacího prvku test uživatelského rozhraní**

Chcete-li získat a nastavit hodnoty vlastností specifických pro ovládací prvky uživatelského rozhraní, můžete přímo získat nebo nastavit hodnoty vlastností ovládacího prvku nebo můžete použít  <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A?displayProperty=fullName> <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A?displayProperty=fullName> metody a s názvem konkrétní vlastnosti, kterou chcete získat nebo nastavit.

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A> Vrátí objekt, který lze následně přetypovat na příslušný objekt <xref:System.Type> . <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A> přijímá objekt pro hodnotu vlastnosti.

### <a name="to-get-or-set-properties-from-ui-test-controls-directly"></a>Chcete-li získat nebo nastavit vlastnosti z ovládacích prvků testu uživatelského rozhraní přímo

Pomocí ovládacích prvků, které jsou odvozeny z, jako je například <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl> [HtmlList](xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls.HtmlList) nebo [WinComboBox](xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls.WinComboBox), můžete získat nebo nastavit hodnoty vlastností přímo. Následující kód ukazuje několik příkladů:

```csharp
int i = myHtmlList.ItemCount;
myWinCheckBox.Checked = true;
```

### <a name="to-get-properties-from-ui-test-controls"></a>Získání vlastností z ovládacích prvků testu uživatelského rozhraní

- Chcete-li získat hodnotu vlastnosti z ovládacího prvku, použijte <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A> .

- Chcete-li určit vlastnost ovládacího prvku, který má být získán, použijte odpovídající řetězec z `PropertyNames` třídy v každém ovládacím prvku jako parametr na <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A> .

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A> vrátí příslušný datový typ, ale tato návratová hodnota je převedena jako <xref:System.Object> . Návratový <xref:System.Object> typ musí být poté převeden jako příslušný typ.

     Příklad:

     `int i = (int)GetProperty(myHtmlList.PropertyNames.ItemCount);`

### <a name="to-set-properties-for-ui-test-controls"></a>Nastavení vlastností ovládacích prvků testu uživatelského rozhraní

- Chcete-li nastavit vlastnost v ovládacím prvku, použijte <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A> .

- Chcete-li určit vlastnost ovládacího prvku, který má být nastaven, použijte odpovídající řetězec z  `PropertyNames` třídy jako první parametr pro <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A> s hodnotou vlastnosti jako druhý parametr.

     Příklad:

     `SetProperty(myWinCheckBox.PropertyNames.Checked, true);`

## <a name="debug"></a>Ladění

Můžete analyzovat kódované testy uživatelského rozhraní pomocí protokolů programových testů uživatelského rozhraní. Protokoly programových testů uživatelského rozhraní filtr a zaznamenávají důležité informace o běhu programového testu uživatelského rozhraní. Formát protokolů vám umožní rychle ladit problémy. Další informace naleznete v tématu [Analýza programových testů uživatelského rozhraní pomocí protokolů kódovaného testu uživatelského rozhraní](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md).

## <a name="whats-next"></a>Co dále?

::: moniker range="vs-2017"
**Další možnosti pro spuštění programových testů uživatelského rozhraní:** Programové testy uživatelského rozhraní lze spustit přímo ze sady Visual Studio, jak je popsáno dříve v tomto tématu. Kromě toho můžete spouštět automatizované testy uživatelského rozhraní z Microsoft Test Manager nebo pomocí Azure Pipelines. Když jsou programové testy uživatelského rozhraní automatizované, musí při jejich spouštění pracovat na rozdíl od jiných automatizovaných testů.
::: moniker-end
::: moniker range=">=vs-2019"
**Další možnosti pro spuštění programových testů uživatelského rozhraní:** Programové testy uživatelského rozhraní lze spustit přímo ze sady Visual Studio, jak je popsáno dříve v tomto tématu. Kromě toho můžete spouštět automatizované testy uživatelského rozhraní pomocí Azure Pipelines. Když jsou programové testy uživatelského rozhraní automatizované, musí při jejich spouštění pracovat na rozdíl od jiných automatizovaných testů.
::: moniker-end

- [Spouštění testů částí pomocí Průzkumníka testů](../test/run-unit-tests-with-test-explorer.md)

- [Spuštění testů v procesu sestavení](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts)

- [Postupy: nastavení testovacího agenta pro spouštění testů, které komunikují s plochou](/previous-versions/ee291332(v=vs.140))

**Přidání podpory pro vlastní ovládací prvky:**  Rozhraní programového testování uživatelského rozhraní nepodporuje všechny možné uživatelské rozhraní a nemusí podporovat uživatelské rozhraní, které chcete testovat. Například nelze okamžitě vytvořit programový test uživatelského rozhraní pro aplikaci Microsoft Excel. Můžete však vytvořit rozšíření programového testování uživatelského rozhraní, které podporuje vlastní ovládací prvek.

- [Povolení programového testování uživatelského rozhraní pro vaše ovládací prvky](../test/enable-coded-ui-testing-of-your-controls.md)

- [Rozšiřování programových testů uživatelského rozhraní a záznamů akcí](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)

Programové testy uživatelského rozhraní se často používají k automatizaci ručních testů. Další informace o automatizovaných testech naleznete v tématu [Test Tools v aplikaci Visual Studio](../test/improve-code-quality.md).

## <a name="see-also"></a>Viz také

- [Záznam a přehrání manuálních testů](/azure/devops/test/mtm/record-play-back-manual-tests?view=vsts)
- [Xamarin. UITest](/appcenter/test-cloud/uitest/)
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>
- [Návod: vytvoření, úprava a údržba kódovaného testu uživatelského rozhraní](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
- [Vytvoření programového testu uživatelského rozhraní pro otestování aplikace pro UWP](test-uwp-app-with-coded-ui-test.md)
- [Anatomie kódovaného testu uživatelského rozhraní](../test/anatomy-of-a-coded-ui-test.md)
- [Osvědčené postupy pro programové testy uživatelského rozhraní](../test/best-practices-for-coded-ui-tests.md)
- [Testování rozsáhlé aplikace s více mapami uživatelského rozhraní](../test/testing-a-large-application-with-multiple-ui-maps.md)