---
title: Automatizované testy uživatelského rozhraní
ms.date: 12/04/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ce10c81265ecfd95f43d62c73d69c902eda1a6c6
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2018
ms.locfileid: "52896637"
---
# <a name="use-ui-automation-to-test-your-code"></a>Použití automatizace uživatelského rozhraní k testování kódu

Automatizované testy, které ovládají aplikaci prostřednictvím jejího uživatelského rozhraní (UI) jsou označovány jako *programové testy UI* (CUITs) v sadě Visual Studio. Tyto testy zahrnují funkční testování ovládacích prvků uživatelského rozhraní. Umožňují ověřit, že celá aplikace včetně uživatelského rozhraní, funguje správně. Programové testy uživatelského rozhraní jsou obzvláště užitečná, pokud je ověření nebo jiná logika v uživatelském rozhraní, například na webové stránce. Používají se také často k automatizaci existujícího manuálního testu.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

Jak je znázorněno na následujícím obrázku, může být typické vývojové prostředí, kde na začátku můžete jednoduše svou aplikaci a klikněte na tlačítko prostřednictvím ovládacích prvků uživatelského rozhraní k ověření, že všechno správně funguje. Potom můžete rozhodnout vytváření automatizovaných testů, takže není nutné a pokračujte v testování aplikace ručně. V závislosti na konkrétní funkce testování ve vaší aplikaci můžete napsat kód pro funkční testování nebo pro test integrace, který může nebo nemusí obsahovat testování na úrovni uživatelského rozhraní. Pokud chcete získat přímo přístup spustí nějakou obchodní logiku, může kód testu jednotek. Ale za určitých okolností může být vhodné zahrnout testování různých ovládacích prvků uživatelského rozhraní v aplikaci. Programový test UI můžete ověřit, že změny v kódu neovlivní funkčnost aplikace.

![Testování během vývoje aplikace](../test/media/cuit_overview.png)

Vytvoření programového testu uživatelského rozhraní je jednoduché. Můžete jednoduše provést test ručně při **Tvůrce programového testu UI** běží na pozadí. Můžete také určit, jaké hodnoty by se zobrazit v konkrétních polích. **Tvůrce programového testu UI** zaznamená vaše akce a generuje kód z nich. Po vytvoření testu, můžete ho upravit v začínáte se speciálním editorem, který umožňuje upravit posloupnost akcí.

Případně pokud máte testovací případ, která byla zaznamenána v nástroji Microsoft Test Manager, může generovat kód od. Další informace najdete v tématu [záznam a přehrávání zpět manuálních testů](/azure/devops/test/mtm/record-play-back-manual-tests?view=vsts).

Specializované **Tvůrce programového testu UI** a editor snadno vytvářet a upravovat kódované UI testy, i když jsou hlavní dovednosti koncentrované testování místo psaní kódu. Ale pokud jste vývojář a chcete rozšířit test pokročilejší způsobem, kód je strukturována tak, aby se snadno kopírovat a upravit. Například může zaznamenat test koupit na webu a pak upravte generovaný kód pro přidání smyčku, která koupí mnoho položek.

**Požadavky**

- Visual Studio Enterprise
- Programový test komponenta uživatelského prostředí

Další informace o tom, které platformy a konfigurace podporují programové testy UI, naleznete v tématu [podporované platformy](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md).

## <a name="install-the-coded-ui-test-component"></a>Nainstalovat komponentu programového testu uživatelského rozhraní

Chcete-li získat přístup k programové nástroje pro testování uživatelského rozhraní a šablony, nainstalovat **programových testů uživatelského rozhraní** komponentu sady Visual Studio 2017.

1. Spuštění **instalační program sady Visual Studio** výběrem **nástroje** > **stažení nástrojů a funkcí**.

1. V **instalační program sady Visual Studio**, zvolte **jednotlivé komponenty** kartu a potom přejděte dolů k položce **ladění a testování** oddílu. Vyberte **programových testů uživatelského rozhraní** komponenty.

   ![Programový test komponenta uživatelského prostředí](media/coded-ui-test-component.png)

1. Vyberte **upravit**.

## <a name="create-a-coded-ui-test"></a>Vytvořit programový test uživatelského rozhraní

1. Vytvořte projekt programového testu UI.

   Programové testy uživatelského rozhraní musí být součástí projektu programového testu UI. Pokud ještě nemáte projekt programového testu uživatelského rozhraní, vytvořte si ho. Zvolte **souboru** > **nový** > **projektu** otevřít **nový projekt** dialogové okno. V podokně kategorie na levé straně rozbalte **nainstalováno** > **jazyka Visual Basic** *nebo* **Visual C#**  >   **Test**. Vyberte **projekt programového testu UI** šablony a klikněte na tlačítko **OK**.

   ![Programových testů UI v šabloně projektu v dialogovém okně Nový projekt](media/coded-ui-test-project-template.png)

   > [!NOTE]
   > Pokud se nezobrazí **projekt testu uživatelského rozhraní programového** šablony, budete muset [nainstalovat komponentu programového testu uživatelského rozhraní](../test/use-ui-automation-to-test-your-code.md#install-the-coded-ui-test-component).

2. Přidejte soubor do programového testu uživatelského rozhraní.

     Pokud jste právě vytvořili projekt programového uživatelského rozhraní, první soubor CUIT je automaticky přidán. Pokud chcete přidat jiný soubor testu, otevřete místní nabídku na projekt programového testu uživatelského rozhraní v **Průzkumníka řešení**a klikněte na tlačítko **přidat** > **programový Test uživatelského rozhraní**.

     V **generovat kód pro programový Test uživatelského rozhraní** dialogového okna zvolte **záznam akcí** > **upravit mapu uživatelského rozhraní nebo přidat kontrolní výrazy**.

     ![Generovat kód pro programový test dialogového okna uživatelského rozhraní](media/generate-code-for-coded-ui-test.png)

     **Tvůrce programového testu UI** se zobrazí.

     ![Tvůrce programového testu UI](../test/media/codedui_testbuilder.png)

3. Záznam posloupnost akcí.

     **Účelem zahájení zaznamenávání**, zvolte **záznam** ikonu. Provedení akce, které chcete otestovat ve vaší aplikaci, včetně spuštění aplikace, pokud je povinný. Například pokud testujete webovou aplikaci, můžete může spustit prohlížeč, přejděte na web a přihlaste se k aplikaci.

     **Pozastavit záznam**, například pokud budete muset řešit příchozí pošty, zvolte **pozastavit**.

    > [!WARNING]
    > Všechny akce provedené v klientských počítačích, bude zaznamenán. Pozastavte záznam, pokud provádíte akce, které může vést k citlivá data nebudou zahrnuty v záznamu.

     **Chcete-li odstranit některé akce** , který jste si poznamenali omylem, zvolte **upravit kroky**.

     **Ke generování kódu** , který bude replikovat vaše akce, zvolte **generovat kód** ikonu a zadejte název a popis pro kódované UI testovací metoda.

4. Ověřte hodnoty v polích uživatelského rozhraní, jako je například textová pole.

     Zvolte **přidat kontrolní výrazy** v **Tvůrce programového testu UI**a klikněte na tlačítko ovládacího prvku uživatelského rozhraní ve spuštěné aplikaci. V seznamu vlastností, které se zobrazí, vyberte vlastnosti, například **Text** v textovém poli. V místní nabídce zvolte **přidat kontrolní výraz**. V dialogovém okně vyberte operátor porovnání, hodnotu porovnání a chybová zpráva.

     Zavřete okno kontrolní výraz a zvolte **generovat kód**.

     ![Programový prvek cílení testu uživatelského rozhraní](../test/media/codedui_1.png)

    > [!TIP]
    > Střídání nahrávání akcí a ověření hodnot. Generování kódu na konci každé posloupnost akcí nebo ověření. Pokud chcete, bude možné později vložit nové akce a ověření.

     Další podrobnosti najdete v tématu [ověření vlastností ovládacích prvků](#validate-the-properties-of-ui-controls).

5. Zobrazení kódu vygenerovaného testu.

     Chcete-li zobrazit generovaného kódu, zavřete okno Tvůrce testu uživatelského rozhraní. V kódu můžete vidět názvy, které jste zadali pro každý krok. Kód je v souboru CUIT, kterou jste vytvořili:

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

6. Přidání více akcí a kontrolní výrazy.

   Umístěte kurzor na slovo v odpovídajícím bodě v testovací metodě a potom v místní nabídce zvolte **generovat kód pro programový Test uživatelského rozhraní**. V tomto okamžiku se vloží nový kód.

7. Upravte podrobnosti o testovacích akcí a kontrolní výrazy.

     Otevřít *UIMap.uitest*. Tento soubor se otevře v **editoru programového testu UI**, kde je můžete upravit libovolnou posloupností akce, které jste si poznamenali i upravit vaše kontrolní výrazy.

     ![Editor programového testu UI](../test/media/cuit_editor_edit.png)

     Další informace najdete v tématu [úprava programových testů UI pomocí editoru programových testů UI](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

8. Spusťte test.

   Pomocí nástroje Test Explorer, nebo otevřete místní nabídku v testovací metodě a klikněte na tlačítko **spustit testy**. Další informace o tom, jak spustit testy, naleznete v tématu [spouštění testů jednotek pomocí Průzkumníka testů](../test/run-unit-tests-with-test-explorer.md) a *dalších možností pro spouštění programových testů UI* v [co se chystá?](#what's-next?) části na konci tohoto tématu.

Zbývající části tohoto tématu poskytují další podrobnosti o postupu v tomto postupu.

Podrobnější příklad naleznete v tématu [návod: vytváření, úpravy a údržba programového testu UI](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md). V tomto návodu vytvoříte jednoduchou aplikaci Windows Presentation Foundation (WPF) pro demonstraci vytvoření, úpravy a správy programového testu UI. Návod poskytuje řešení pro opravu testů, které byly poškozeny různými chybami časování a refaktoringem ovládacích prvků.

## <a name="start-and-stop-the-application-under-test"></a>Spuštění a zastavení testovanou aplikaci

Pokud nechcete, aby ke spuštění a zastavení aplikace, prohlížeče nebo databáze samostatně pro každý test, proveďte jednu z následujících akcí:

- Pokud nechcete pro záznam akce, které chcete spustit aplikaci v rámci testu, je nutné spustit aplikace, než se rozhodnete **záznam** ikonu.

- Na konci testu je ukončen proces, ve kterém test běží. Pokud jste začali vaše aplikace v testu, aplikace obvykle ukončí.  Pokud nechcete, aby test, který chcete zavřít aplikaci při jejím ukončení, přidejte *s příponou .runsettings* do vašeho řešení a použít `KeepExecutorAliveAfterLegacyRun` možnost. Další informace najdete v tématu [konfigurace testů jednotek s použitím souboru .runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

- Přidejte do metody inicializace testu identifikovaný `[TestInitialize]` atribut, který spouští kód na začátku každé zkušební metody. Například by mohl spustit aplikaci z metody TestInitialize.

- Přidat čistící metoda testu, identifikovaný `[TestCleanup]` atributu, která spustí kód na konci jednotlivých zkušebních metod. Například metoda zavřít aplikaci může volat z metoda TestCleanup.

## <a name="validate-the-properties-of-ui-controls"></a>Ověření vlastností ovládacích prvků uživatelského rozhraní

Můžete použít **Tvůrce programového testu UI** přidat ovládací prvek uživatelského rozhraní (UI) pro <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> pro test nebo ke generování kódu pro metodu ověřování, používá kontrolní výraz pro ovládací prvek uživatelského rozhraní.

Chcete-li vygenerovat kontrolní výrazy pro vaše ovládací prvky uživatelského rozhraní, zvolte **přidat kontrolní výrazy** nástroj v **Tvůrce programového testu UI** a přetáhněte ji na ovládací prvek na aplikaci v rámci testu, který chcete ověřit správnost. Pokud pole obsahuje ovládací prvek, uvolněte tlačítko myši. Kód třídy ovládacího prvku se okamžitě vytvoří v *UIMap.Designer.cs* souboru.

![Programový prvek cílení testu uživatelského rozhraní](../test/media/codedui_1.png)

Vlastnosti pro tento ovládací prvek je nyní obsažena v **přidat kontrolní výrazy** dialogové okno.

Jiný způsob přechodu na určitý ovládací prvek je na šipku **(<<)** rozbalte zobrazení **mapování ovládacího prvku UI**. Najít nadřazený, na stejné úrovni nebo podřízený ovládací prvek, klikněte na libovolné místo na mapě a pohyb stromu pomocí kláves se šipkami.

![Vlastnosti programového testu uživatelského rozhraní](../test/media/codedui_2.png)

> [!TIP]
> Pokud nevidíte žádné vlastnosti, když vyberete ovládací prvek ve vaší aplikaci, nebo se ovládací prvek do mapování ovládacích prvků uživatelského rozhraní, ověřte, zda ovládací prvek má jedinečné ID v kódu aplikace. Jedinečné ID může být atributu HTML ID nebo WPF UId.

Dále otevřete místní nabídku pro vlastnost pro ovládací prvek uživatelského rozhraní, který chcete ověřit a pak přejděte na **přidat kontrolní výraz**. V **přidat kontrolní výraz** dialogové okno, vyberte **Komparátor** pro vaše kontrolního výrazu, například <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A>a zadejte hodnotu pro vaše kontrolního výrazu v **hodnotu porovnání**.

![Kontrolní výrazy s testů programového uživatelského rozhraní](../test/media/codedui_3.png)

Po přidání všech kontrolních výrazů pro test, zvolte **OK**.

Chcete-li generovat kód pro vaše kontrolní výrazy a přidejte ovládací prvek do mapy uživatelského rozhraní, zvolte **generovat kód** ikonu. Zadejte název pro metodu programového testu uživatelského rozhraní a popis pro metodu, která se přidají jako komentář pro metodu. Zvolte **přidejte a generujte**. V dalším kroku vyberte **zavřete** ikonu Zavřít **Tvůrce programového testu UI**. Tím se vygeneruje kód, podobně jako v následujícím kódu. Například, pokud zadaný název je `AssertForAddTwoNumbers`, kód bude vypadat jako v tomto příkladu:

- Volání metody assert AssertForAddTwoNumbers přidá do testovací metody v souboru programového testu uživatelského rozhraní:

    ```csharp
    [TestMethod]
    public void CodedUITestMethod1()
    {
        this.UIMap.AddTwoNumbers();
        this.UIMap.AssertForAddTwoNumbers();
    }
    ```

     Můžete upravit tento soubor, chcete-li změnit pořadí kroků a kontrolní výrazy nebo k vytvoření nové metody testu. Chcete-li přidat další kód, umístěte kurzor v testovací metodě a v místní nabídce zvolte **generovat kód pro programový Test uživatelského rozhraní**.

- Přidá metodu nazvanou `AssertForAddTwoNumbers` do mapy uživatelského rozhraní (*UIMap.uitest*). Tento soubor se otevře v **editoru programového testu UI**, kde můžete upravit kontrolní výrazy.

     ![Vyhodnocení upravit pomocí editoru programového testu uživatelského rozhraní](../test/media/cuit_editor_assert.png)

     Další informace najdete v tématu [úprava programových testů UI pomocí editoru programových testů UI](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

     Můžete také zobrazit generovaný kód výrazu metody v *UIMap.Designer.cs*. Tento soubor by neměl upravit. Pokud chcete vytvořit přizpůsobené verzi kódu, zkopírujte metody do jiného souboru, jako *UIMap.cs*, přejmenujte metody a tam je upravovat.

    ```csharp
    public void AssertForAddTwoNumbers()
    {
        ...
    }
    ```

### <a name="select-a-hidden-control-using-the-keyboard"></a>Vyberte skrytý ovládací prvek pomocí klávesnice

Pokud chcete vybrat ovládací prvek ztratí fokus a zmizí při výběru **přidat kontrolní výrazy** nástroj z **Tvůrce programového testu UI**:

V některých případech při přidání ovládacích prvků a ověřit jejich vlastnosti, budete nejspíš muset použít klávesnici. Například když zkusíte zaznamenat programový test UI používající ovládací prvek místní nabídky, seznam položek nabídky v ovládacím prvku se ztratí fokus a zmizí při pokusu o vyberte **přidat kontrolní výrazy** nástroj z **programový Test uživatelského rozhraní Tvůrce**. To je patrné na následujícím obrázku, kde místní nabídky v aplikaci Internet Explorer ztratí fokus a zmizí, pokud se pokusíte jej vybrat **přidat kontrolní výrazy** nástroj.

![CodedUITest&#95;SelectControlKeyboard](../test/media/codeduitest_selectcontrolkeyboard.png)

Použití klávesnice k výběru ovládacího prvku uživatelského rozhraní, najeďte myší ovládací prvek pomocí myši. Potom podržte klávesu **Ctrl** klíč a **můžu** klíče ve stejnou dobu. Verze klíče. Ovládací prvek je zaznamenaných **Tvůrce programového testu UI**.

#### <a name="manually-record-mouse-hovers"></a>Ručně záznam se ukazatel myši nachází

Pokud myší najedete na ovládací prvek nelze zaznamenat:

Za určitých okolností konkrétní ovládací prvek, který se používá v programového uživatelského rozhraní testu může vyžadovat použití klávesnice k události ručně zaznamenávat myši při najetí myší. Například při testování formuláře Windows nebo aplikaci Windows Presentation Foundation (WPF), může existovat vlastní kód. Nebo může být zvláštní chování definované pro najedete myší na ovládací prvek, jako je například uzel stromu, rozbalení, když uživatel najede myší ho. K otestování za těchto okolností, budete muset ručně upozornit **Tvůrce programového testu UI** , že jsou najede myší ovládací prvek stisknutím kombinace kláves předdefinované.

Když provádíte programového testu uživatelského rozhraní, najeďte myší ovládací prvek. Stiskněte a podržte **Ctrl**, zatímco stiskněte a podržte **Shift** a **R** klávesy na klávesnici. Verze klíče. Zaznamená událost najeďte myší **Tvůrce programového testu UI**.

![CodedUI&#95;při najetí myší](../test/media/codedui_hover.png)

Po vytvoření testovací metody, podobně jako v následujícím příkladu kódu se přidají do *UIMap.Designer.cs* souboru:

```csharp
// Mouse hover '1' label at (87, 9)
Mouse.Hover(uIItem1Text, new Point(87, 9));
```

### <a name="configure-mouse-hover-keyboard-assignments"></a>Konfigurace přiřazení klávesových myši při najetí myší

Pokud přiřazení klíče pro zachytávání událostí myši při najetí myší se používá jinde v Moje prostředí:

Pokud se potřeby výchozí klávesnice přiřazení **Ctrl**+**Shift**+**R** , který se používá k aplikování při najetí myší událostí myši v programových testů uživatelského rozhraní může být nakonfigurován k používání různých klíčů.

> [!WARNING]
> Není nutné změnit přiřazení klávesnice pro události myši při najetí myší za běžných okolností. Buďte opatrní při přiřazení přiřazení klávesnice. Podle vašeho výběru mohou být již používá jinde v rámci sady Visual Studio nebo aplikaci právě testováno.

Chcete-li změnit přiřazení klávesnice, upravte následující konfigurační soubor:

*%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CodedUITestBuilder.exe.config*

V konfiguračním souboru změňte hodnoty `HoverKeyModifier` a `HoverKey` pro změnu přiřazení klávesnice:

```xml
<!-- Begin : Background Recorder Settings -->
<!-- HoverKey to use. -->
<add key="HoverKeyModifier" value="Control, Shift"/>
<add key="HoverKey" value="R"/>
```

### <a name="set-implicit-mouse-hovers-for-the-web-browser"></a>Nastavte implicitní myši pohybuje pro webový prohlížeč

Pokud máte potíže s záznam se ukazatel myši nachází na webu:

V mnoha weby když najedete myší na ovládací prvek konkrétní rozšiřuje zobrazíte další podrobnosti. Obecně tyto vypadat nabídky v aplikacích klasické pracovní plochy. Protože jde o častou, programové testy uživatelského rozhraní povolit implicitní ukazatele pro procházení webu. Například pokud jste záznam se nachází v aplikaci Internet Explorer, je vyvolána událost. Tyto události může vést k redundantní pohybuje nahrávají. Z toho důvodu se zaznamenávají implicitní ukazatele s `ContinueOnError` nastavena na `true` v konfiguračním souboru testu uživatelského rozhraní. To umožňuje přehrávání pokračovat, pokud událost při najetí myší se nezdaří.

Pokud chcete povolit nahrávání implicitní ukazatele ve webovém prohlížeči, otevřete konfigurační soubor:

*%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CodedUITestBuilder.exe.config*

Ověřte, zda konfigurační soubor má klíč `RecordImplicitiHovers` nastavena na hodnotě `true` jak je znázorněno v následujícím příkladu:

```xml
<!--Use this to enable/disable recording of implicit hovers.-->
<add key="RecordImplicitHover" value="true"/>
```

## <a name="customize-the-coded-ui-test"></a>Upravit programový test uživatelského rozhraní

Po vytvoření programového testu UI, můžete ji upravit pomocí některého z následujících nástrojů v sadě Visual Studio:

- Použití **Tvůrce programového testu UI** chcete do testů přidat další ovládací prvky a ověřování. V části [přidat ovládací prvky a ověřit jejich vlastnosti](#validate-the-properties-of-ui-controls) v tomto tématu.

- **Programové Editor testu UI** umožňuje snadno upravovat programové testy uživatelského rozhraní. Pomocí **editoru programového testu UI**, můžete vyhledat, zobrazit a upravit testovací metody. Můžete také upravit akce uživatelského rozhraní a jim přidružené ovládací prvky v mapování ovládacího prvku uživatelského rozhraní. Další informace najdete v tématu [úprava programových testů UI pomocí editoru programových testů UI](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

- **Editor kódu:**

    - Ručně přidejte kód pro ovládací prvky v testu, jak je popsáno v [akce uživatelského rozhraní pro řízení a vlastnosti](#coded-ui-control-actions-and-properties) v tomto tématu.

    - Po vytvoření programového testu UI můžete upravit tak být řízený daty. Další informace najdete v tématu [vytvoření datově řízeného programového testu UI](../test/creating-a-data-driven-coded-ui-test.md).

    - Programové přehrávání testů uživatelského rozhraní webu můžete dát pokyn testů čekala určitých událostí pravděpodobnější, jako je okno se zobrazí indikátor průběhu signalizující zmizí a tak dále. K tomu přidáte odpovídající metodu UITestControl.WaitForControlXXX(). Úplný seznam dostupných metod najdete v tématu [vytvořit kódované testy uživatelského rozhraní čekání na konkrétní události při přehrávání](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md). Příklad programový test UI, který čeká na ovládací prvek pro povolit pomocí WaitForControlEnabled metodu, najdete v části [návod: vytváření, úpravy a údržba programového testu UI](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md).

    - Programové testy UI zahrnují podporu pro některé ovládací prvky jazyka HTML5, které jsou zahrnuty v aplikaci Internet Explorer 9 a Internet Explorer 10. Další informace najdete v tématu [ovládacích prvků pomocí specifikace HTML5 v programových testů UI](../test/using-html5-controls-in-coded-ui-tests.md).

    - Programový test UI kódování pokyny:

       - [Anatomie programového testu uživatelského rozhraní](../test/anatomy-of-a-coded-ui-test.md)

       - [Osvědčené postupy pro programové testy uživatelského rozhraní](../test/best-practices-for-coded-ui-tests.md)

       - [Testování rozsáhlé aplikace s více mapami uživatelského rozhraní](../test/testing-a-large-application-with-multiple-ui-maps.md)

       - [Podporované konfigurace a platformy pro programové testy uživatelského rozhraní a zaznamenávání akcí](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)

### <a name="the-generated-code"></a>Generovaný kód

Pokud zvolíte **generovat kód**, několika částí kódu jsou vytvořeny:

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

     Klikněte pravým tlačítkem v této metodě, chcete-li přidat více zaznamenané akce a ověření. Můžete také upravit ho ručně, aby se rozšířit nebo upravit kód. Může některý kód například uzavřete ve smyčce.

     Můžete také přidat nové metody testu, přidejte kód k nim stejným způsobem. Každá testovací metoda musí mít `[TestMethod]` atribut.

- Metoda v *UIMap.uitest*.

     Tato metoda zahrnuje podrobné akce, které jste si poznamenali nebo hodnotu, která jste ověřili. Tento kód můžete upravit tak, že otevřete *UIMap.uitest*. Otevře se v začínáte se speciálním editorem, ve kterém můžete odstranit nebo Refaktorujte již nahrané akce.

     Můžete také zobrazit vytvořena metoda v *UIMap.Designer.cs*. Tato metoda provádí akce, že jste si poznamenali při spuštění testu.

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
    > Tento soubor by neměl upravit, protože se znovu vygeneruje, když vytvoříte další testy.

     Dokážete přizpůsobit verze těchto metod zkopírováním do *UIMap.cs*. Například může vytvořit parametrizovanou verzi, která lze volat z testovací metody:

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

    Tyto deklarace představují ovládací prvky uživatelského rozhraní aplikace, které jsou používány vašeho testu. Používají se vygenerovaný kód pracovat ovládací prvky a přístup k jejich vlastností.

    Můžete také je můžete psát vlastní kód. Například můžete mít vaše testovací metoda vyberte hypertextový odkaz ve webové aplikaci, zadejte hodnotu v textovém poli, nebo větví a provést různé testovací akce na základě hodnoty v poli.

    Můžete přidat více programové testy uživatelského rozhraní a více objekty mapování uživatelského rozhraní a soubory, aby usnadnil testování rozsáhlé aplikace. Další informace najdete v tématu [testování rozsáhlé aplikace s více mapami uživatelského rozhraní](../test/testing-a-large-application-with-multiple-ui-maps.md).

Další informace o generovaný kód, naleznete v tématu [anatomie programového testu UI](../test/anatomy-of-a-coded-ui-test.md).

## <a name="coded-ui-control-actions-and-properties"></a>Akce správy programového uživatelského rozhraní a vlastnosti

Při práci s ovládacími prvky test uživatelského rozhraní v kódované testy uživatelského rozhraní jsou rozdělené do dvou částí: akcí a vlastností.

- V první části se skládá z akcí, které můžete provádět na ovládací prvky uživatelského rozhraní testu. Například programové testy uživatelského rozhraní můžete simulovat kliknutí myší na ovládací prvek uživatelského rozhraní testu, nebo simulovat zadané na klávesnici ovlivnit ovládacího prvku uživatelského rozhraní testu klávesy.

- Druhá část se skládá z něhož můžete získat a nastavit vlastnosti ovládacího prvku uživatelského rozhraní testu. Například programové testy uživatelského rozhraní můžete získat počet položek v `ListBox`, nebo nastavte `CheckBox` na vybraném stavu.

**Přístup k akce testu ovládacího prvku uživatelského rozhraní**

K provádění akcí v ovládacích prvcích test uživatelského rozhraní, jako je například kliknutí myší nebo akce klávesnice, použijte metody v <xref:Microsoft.VisualStudio.TestTools.UITesting.Mouse> a <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard> třídy:

- Chcete-li provést akci myši objektově orientovaný, jako například kliknutí myší na ovládací prvek uživatelského rozhraní testu použijte <xref:Microsoft.VisualStudio.TestTools.UITesting.Mouse.Click%2A>.

     `Mouse.Click(buttonCancel);`

- K provedení akce orientované klávesnice, jako je například psaní do ovládacího prvku pro úpravy, použijte <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A>.

     `Keyboard.SendKeys(textBoxDestination, @"C:\Temp\Output.txt");`

**Přístup k vlastnostem ovládacího prvku uživatelského rozhraní testu**

K získání a nastavení konkrétní hodnoty vlastností ovládacího prvku uživatelského rozhraní, můžete přímo získání nebo nastavení hodnoty vlastností ovládacího prvku, nebo můžete použít <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A?displayProperty=fullName> a <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A?displayProperty=fullName> metody s názvem konkrétní vlastnost, která má získat nebo nastavit.

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A> Vrátí objekt, který lze převést na příslušné <xref:System.Type>. <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A> přijímá objekt pro hodnoty vlastnosti.

### <a name="to-get-or-set-properties-from-ui-test-controls-directly"></a>Pro získání nebo nastavení vlastnosti přímo z ovládacích prvků uživatelského rozhraní testu

Pomocí ovládacích prvků, které jsou odvozeny z <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl>, jako například [HTML](xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls.HtmlList) nebo [WinComboBox](xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls.WinComboBox), můžete získat nebo nastavit jejich hodnoty vlastností přímo. Následující kód ukazuje několik příkladů:

 ```csharp
 int i = myHtmlList.ItemCount;
 myWinCheckBox.Checked = true;
 ```

### <a name="to-get-properties-from-ui-test-controls"></a>Chcete-li získat vlastnosti z ovládacích prvků uživatelského rozhraní testu

- K získání hodnoty vlastnosti z ovládacího prvku použijte <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A>.

- Pokud chcete nastavit vlastnost ovládacího prvku, chcete-li získat, použijte příslušným řetězcem z `PropertyNames` třídy v každém ovládacím prvku jako parametr <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A>.

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A> vrátí odpovídající typ dat, ale to vrátit hodnotu je typovaná jako <xref:System.Object>. Vrácení <xref:System.Object> musíte přetypovat jako odpovídajícího typu.

     Příklad:

     `int i = (int)GetProperty(myHtmlList.PropertyNames.ItemCount);`

### <a name="to-set-properties-for-ui-test-controls"></a>Chcete-li nastavit vlastnosti pro test uživatelského rozhraní ovládacích prvků

- Chcete-li nastavit vlastnost v ovládacím prvku, použijte <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A>.

- Chcete-li určit vlastnost ovládacího prvku, chcete-li nastavit, použijte příslušným řetězcem z `PropertyNames` třídu jako první parametr <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A>, s hodnotou vlastnosti jako druhý parametr.

     Příklad:

     `SetProperty(myWinCheckBox.PropertyNames.Checked, true);`

## <a name="debug"></a>Ladit

Programové testy uživatelského rozhraní pomocí protokolů z programových testů uživatelského rozhraní můžete analyzovat. Programového uživatelského rozhraní testu protokoly filtr a záznam, který běží důležité informace o programového testu UI. Formát protokolů umožňuje ladit problémy rychle. Další informace najdete v tématu [analyzovat kódované testy uživatelského rozhraní pomocí protokolů z programových testů uživatelského rozhraní](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md).

## <a name="whats-next"></a>Co se chystá?

**Další možností pro spouštění programových testů UI:** spustit programové testy UI přímo ze sady Visual Studio, jak je popsáno výše v tomto tématu. Kromě toho můžete spustit automatizované testy uživatelského rozhraní z nástroje Microsoft Test Manager nebo pomocí kanálů Azure. Pokud jsou automatizované programové testy UI, mají komunikovat s plochou, když spustíte, je oproti jiným automatizovaným testům.

- [Spouštění testování částí pomocí Průzkumníka testů](../test/run-unit-tests-with-test-explorer.md)

- [Spuštění testů v procesu sestavení](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts)

- [Postupy: nastavení testovacího agenta pro spouštění testů komunikujících s plochou](https://msdn.microsoft.com/Library/3a94dd07-6d17-402c-ae8f-7947143755c9)

**Přidání podpory pro vlastní ovládací prvky:** programového uživatelského rozhraní testovací rozhraní nepodporuje všechna možná uživatelská rozhraní a nemusí podporovat uživatelské rozhraní, které chcete testovat. Například nelze vytvořit okamžitě programový test UI uživatelského rozhraní pro aplikaci Microsoft Excel. Můžete však vytvořit rozšíření programového uživatelského rozhraní testování rozhraní, která bude podporovat vlastní ovládací prvek.

- [Povolení programového testování uživatelského rozhraní pro vaše ovládací prvky](../test/enable-coded-ui-testing-of-your-controls.md)

- [Rozšíření programových testů UI a záznamů akcí](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)

Programové testy uživatelského rozhraní se často používají k automatizaci ručních testů. Další informace o ruční testy, naleznete v tématu [spuštění manuálních testů pomocí nástroje Microsoft Test Manager](/azure/devops/test/mtm/run-manual-tests-with-microsoft-test-manager?view=vsts). Další informace o automatických testů, naleznete v tématu [Test tools v sadě Visual Studio](../test/improve-code-quality.md).

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>
- [Návod: Vytvoření, úpravy a správy programového testu uživatelského rozhraní](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
- [Vytvoření programového uživatelského rozhraní testu aplikace pro UPW](test-uwp-app-with-coded-ui-test.md)
- [Anatomie programového testu uživatelského rozhraní](../test/anatomy-of-a-coded-ui-test.md)
- [Osvědčené postupy pro programové testy uživatelského rozhraní](../test/best-practices-for-coded-ui-tests.md)
- [Testování rozsáhlé aplikace s více mapami uživatelského rozhraní](../test/testing-a-large-application-with-multiple-ui-maps.md)
