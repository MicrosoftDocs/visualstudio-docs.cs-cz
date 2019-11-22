---
title: Použití automatizace uživatelského rozhraní k otestování kódu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
ms.assetid: ad9e3eaa-ab86-436e-95b8-dc20eb1f8b2a
caps.latest.revision: 87
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2eb0a4ee7c69ebe2bf753d4bbde63160b6e0043e
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297989"
---
# <a name="use-ui-automation-to-test-your-code"></a>Použití automatizace uživatelského rozhraní k testování kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Automatizované testy, které zařídí vaši aplikaci prostřednictvím uživatelského rozhraní (UI), se označují jako programové *testy uživatelského rozhraní* (CUITs). Tyto testy zahrnují funkční testování ovládacích prvků uživatelského rozhraní. Umožňují ověřit, že celá aplikace, včetně jejího uživatelského rozhraní, funguje správně. Programové testy uživatelského rozhraní jsou zvláště užitečné v případě, že je v uživatelském rozhraní k dispozici ověřování nebo jiná logika, například na webové stránce. Používají se také často k automatizaci stávajícího manuálního testu.

 Jak je znázorněno na následujícím obrázku, typickým vývojovým prostředím může být jedna z nich, kde zpočátku stačí sestavit aplikaci (F5) a kliknout na ovládací prvky uživatelského rozhraní a ověřit, zda fungují správně. Pak se můžete rozhodnout vytvořit kódovaný test, aby nemuseli aplikace nadále testovat ručně. V závislosti na tom, jaké funkce jsou testovány ve vaší aplikaci, můžete napsat kód pro funkční test nebo pro test integrace, který může nebo nemusí zahrnovat testování na úrovni uživatelského rozhraní. Pokud jednoduše chcete získat přímý přístup k některé obchodní Logic, můžete kód otestovat jednotkou. Za určitých okolností však může být užitečné zahrnout do aplikace testování různých ovládacích prvků uživatelského rozhraní. Programový test uživatelského rozhraní může automatizovat úvodní scénář (F5) a ověřit, že změny kódu nemají vliv na funkčnost aplikace.

 ![Testování během vývoje aplikace](../test/media/cuit-overview.png "CUIT_Overview")

 Vytvoření programového testu uživatelského rozhraní je snadné. Stačí provést test ručně, zatímco se UI test Builder spouští na pozadí. Můžete také určit, které hodnoty se mají zobrazit v určitých polích. Nástroj UI test Builder zaznamenává vaše akce a generuje z nich kód. Po vytvoření testu ho můžete upravit ve specializovaném editoru, který vám umožní upravit sekvenci akcí.

 Případně, pokud máte testovací případ, který byl zaznamenán v Microsoft Test Manager, můžete z něj vygenerovat kód. Další informace najdete v tématech [záznam a přehrání manuálních testů](/azure/devops/test/mtm/record-play-back-manual-tests).

 Specializovaný UI a editor testů usnadňuje vytváření a úpravy programových testů UI i v případě, že vaše hlavní dovednosti jsou při testování soustředěny spíše než kódování. Ale pokud jste vývojář a chcete rozšířit test pokročilým způsobem, je kód strukturovaný, aby bylo snadné ho zkopírovat a přizpůsobit. Můžete například zaznamenat test a koupit něco na webu a potom upravit generovaný kód a přidat smyčku, která nakupuje mnoho položek.

 **Požadavky**

- Visual Studio Enterprise

  Další informace o tom, které platformy a konfigurace podporuje programové testy UI, najdete v tématu [podporované konfigurace a platformy pro programové testy uživatelského rozhraní a záznamy akcí](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md).

  **V tomto tématu**

- [Vytváření programových testů uživatelského rozhraní](#VerifyingCodeUsingCUITCreate)

  - [Hlavní procedura](#VerifyingCodeUsingCUITCreate)

  - [Spuštění a zastavení aplikace](#starting)

  - [Ověřování vlastností ovládacích prvků uživatelského rozhraní](#VerifyingCodeUsingCUITGenerateAssertions)

- [Přizpůsobení kódovaného testu uživatelského rozhraní](#VerifyingCodeCUITModify)

  - [Generovaný kód](#generatedCode)

  - [Kódování akcí a vlastností ovládacích prvků uživatelského rozhraní](#actions)

  - [Ladění](#debugging)

- [Co dál](#VerifyCodeUsingCUITWhatsNext)

## <a name="VerifyingCodeUsingCUITCreate"></a>Vytváření programových testů uživatelského rozhraní

1. **Vytvořte projekt programového testu uživatelského rozhraní.**

    Programové testy uživatelského rozhraní musí být obsaženy v projektu programového testu uživatelského rozhraní. Pokud ještě nemáte projekt programového testu UI, vytvořte ho. V **Průzkumník řešení**v místní nabídce řešení zvolte možnost **Přidat**, **Nový projekt** a potom vyberte možnost **Visual Basic** nebo **vizuál C#** . Dále vyberte **test**, programový **test uživatelského rozhraní**.

   - <em>Nevidím šablony projektu programový **test uživatelského rozhraní</em>* .*

      Je možné, že používáte verzi sady Visual Studio, která nepodporuje programové testy uživatelského rozhraní. Chcete-li vytvořit programové testy uživatelského rozhraní, je nutné použít Visual Studio Enterprise.

2. **Přidejte soubor programového testu uživatelského rozhraní.**

    Pokud jste právě vytvořili projekt kódovaného uživatelského rozhraní, je první soubor UI přidán automaticky. Chcete-li přidat další testovací soubor, otevřete místní nabídku projektu programového testu uživatelského rozhraní, přejděte na položku **Přidat**a poté vyberte programový **test uživatelského rozhraní**.

    ![Vytvoření programového testu uživatelského rozhraní](../test/media/codedui-create.png "CodedUI_Create")

    V dialogovém okně **generovat kód pro programový test UI** , vyberte možnost **zaznamenat akce, upravit mapu uživatelského rozhraní nebo přidat kontrolní výrazy**.

    ![Vybrat akce záznamu](../test/media/codedui-codegendialogb.png "CodedUI_CodeGenDialogB")

    Zobrazí se Tvůrce programového testu uživatelského rozhraní a minimalizuje se Visual Studio.

    ![Tvůrce programového testu uživatelského rozhraní](../test/media/codedui-testbuilder.png "CodedUI_TestBuilder")

3. **Zaznamenejte sekvenci akcí**.

    **Chcete-li spustit záznam**, vyberte ikonu **záznamu** . Proveďte akce, které chcete ve své aplikaci testovat, včetně spuštění aplikace, pokud je to nutné.

    Například při testování webové aplikace je možné spustit prohlížeč, přejít na web a přihlásit se k aplikaci.

    **Chcete-li záznam pozastavit**, například pokud potřebujete pracovat s příchozí poštou, vyberte možnost **pozastavit**.

   > [!WARNING]
   > Budou zaznamenány všechny akce prováděné na ploše. Pozastaví nahrávání, pokud provádíte akce, které mohou vést k zahrnutí citlivých dat do záznamu.

    Pokud **chcete odstranit akce** , které jste si poznamenali omylem, klikněte na **Upravit akce**.

    **Chcete-li vygenerovat kód** , který bude replikovat vaše akce, vyberte ikonu **generovat kód** a zadejte název a popis pro metodu programového testu uživatelského rozhraní.

4. **Ověřte hodnoty v polích uživatelského rozhraní, jako jsou textová pole**.

    Zvolte **Přidat kontrolní výrazy** v Tvůrci programového testu UI a pak zvolte ovládací prvek uživatelského rozhraní v běžící aplikaci. V seznamu vlastností, které se zobrazí, vyberte vlastnost, například **text** v textovém poli. V místní nabídce vyberte možnost **Přidat kontrolní výraz**. V dialogovém okně vyberte operátor porovnání, hodnotu porovnání a chybovou zprávu.

    Zavřete okno kontrolního výrazu a klikněte na příkaz **generovat kód**.

    ![Cílový prvek programového testu uživatelského rozhraní](../test/media/codedui-1.png "CodedUI_1")

   > [!TIP]
   > Alternativní mezi akcemi záznamu a ověřováním hodnot. Vygenerujte kód na konci každé posloupnosti akcí nebo ověření. Pokud chcete, budete moct později vkládat nové akce a ověřování.

    Další podrobnosti najdete v tématu [ověřování vlastností ovládacích prvků](#VerifyingCodeUsingCUITGenerateAssertions).

5. **Zobrazit generovaný testovací kód**.

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

6. **Přidejte další akce a kontrolní výrazy**.

    Umístěte kurzor do vhodného bodu v testovací metodě a potom v místní nabídce zvolte možnost **generovat kód pro programový test uživatelského rozhraní**. V tomto okamžiku bude vložen nový kód.

7. **Upravte podrobnosti testovacích akcí a kontrolních výrazů**.

    Otevřete UIMap. UITest. Tento soubor se otevře v editoru programového testu UI, kde můžete upravit libovolnou sekvenci akcí, které jste si poznamenali, a upravit kontrolní výrazy.

    ![Editor programového testu UI](../test/media/cuit-editor-edit.png "CUIT_Editor_edit")

    Další informace naleznete v tématu [Úpravy programových testů uživatelského rozhraní pomocí editoru programových testů uživatelského rozhraní](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

8. **Spusťte test**.

    Použijte Průzkumníka testů nebo otevřete místní nabídku v testovací metodě a pak zvolte možnost **Spustit testy**. Další informace o tom, jak spustit testy, najdete v tématu [spuštění testů jednotek pomocí Průzkumníka testů](../test/run-unit-tests-with-test-explorer.md) a *dalších možností pro spuštění programových testů uživatelského rozhraní* v části [co dál?](#VerifyCodeUsingCUITWhatsNext) na konci tohoto tématu.

   Zbývající části tohoto tématu poskytují další podrobnosti o krocích v tomto postupu.

   Podrobnější příklad naleznete v tématu [Návod: vytváření, upravování a údržba programového testu uživatelského rozhraní](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md). V tomto návodu vytvoříte jednoduchou aplikaci Windows Presentation Foundation (WPF), která ukazuje, jak vytvořit, upravit a udržovat programový test uživatelského rozhraní. Návod poskytuje řešení pro opravu testů, které byly poškozeny různými chybami časování a refaktoringem ovládacích prvků.

### <a name="starting"></a>Spuštění a zastavení testované aplikace
 *Nechci spouštět a zastavovat aplikaci, prohlížeč ani databázi samostatně pro každý test. Návody se tomu vyhnout?*

- ![Prerequsite](../test/media/prereq.png "Požadavků ohlásila") Pokud nechcete zaznamenávat akce pro spuštění testované aplikace, musíte aplikaci spustit před výběrem ikony **záznamu** .

- ![Prerequsite](../test/media/prereq.png "Požadavků ohlásila") Na konci testu proces, ve kterém je test spuštěn, je ukončen. Pokud jste aplikaci spustili v testu, aplikace se obvykle zavře.  Pokud nechcete, aby test zavřel aplikaci při ukončení, musíte do svého řešení přidat soubor. runsettings a použít možnost `KeepExecutorAliveAfterLegacyRun`. Další informace najdete v tématu [konfigurace testů jednotek s použitím souboru .runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

- ![Prerequsite](../test/media/prereq.png "Požadavků ohlásila") Můžete přidat metodu Initialize testu identifikovanou atributem [TestInitialize], který spouští kód na začátku každé testovací metody. Například můžete spustit aplikaci z metody TestInitialize.

- ![Prerequsite](../test/media/prereq.png "Požadavků ohlásila") Můžete přidat metodu čištění testu identifikovanou atributem [TestCleanup], který spouští kód na konci každé testovací metody. Například metoda zavření aplikace by mohla být volána z metody TestCleanup.

### <a name="VerifyingCodeUsingCUITGenerateAssertions"></a>Ověřování vlastností ovládacích prvků uživatelského rozhraní
 Tvůrce programového **testu UI** můžete použít k přidání ovládacího prvku uživatelského rozhraní (UI) do [UIMap](/previous-versions/dd580454(v=vs.140)) pro váš test nebo k vygenerování kódu pro metodu ověřování, která používá kontrolní výraz pro ovládací prvek uživatelského rozhraní.

 Chcete-li generovat kontrolní výrazy pro ovládací prvky uživatelského rozhraní, vyberte nástroj **Přidat kontrolní** výraz v Tvůrci programového testu uživatelského rozhraní a přetáhněte jej do ovládacího prvku testované aplikace, kterou chcete ověřit, je správný. Jakmile se v poli zobrazí ovládací prvek, uvolněte tlačítko myši. Kód třídy ovládacího prvku je okamžitě vytvořen v souboru `UIMap.Designer.cs`.

 ![Cílový prvek programového testu uživatelského rozhraní](../test/media/codedui-1.png "CodedUI_1")

 Vlastnosti tohoto ovládacího prvku jsou nyní uvedeny v dialogovém okně **Přidat kontrolní výrazy** .

 Dalším způsobem navigace na konkrétní ovládací prvek je výběr šipky **(< <)** pro rozšíření zobrazení pro **mapu ovládacího prvku uživatelského rozhraní**. Chcete-li najít nadřazený ovládací prvek, na stejné úrovni nebo podřízený ovládací prvek, můžete kliknout kamkoli na mapu a pomocí kláves se šipkami se pohybovat kolem stromu.

 ![Vlastnosti kódovaného testu uživatelského rozhraní](../test/media/codedui-2.png "CodedUI_2")

- *Při výběru ovládacího prvku v aplikaci se nezobrazí žádné vlastnosti, nebo ovládací prvek není zobrazen v mapě ovládacího prvku uživatelského rozhraní.*

   V kódu aplikace musí mít ovládací prvek, který chcete ověřit, jedinečné ID, jako je atribut ID HTML nebo UId WPF. Pro přidání těchto ID může být nutné aktualizovat kód aplikace.

  Potom otevřete místní nabídku vlastnosti ovládacího prvku uživatelského rozhraní, který chcete ověřit, a pak přejděte na **Přidat kontrolní výraz**. V dialogovém okně **Přidat kontrolní výraz** vyberte **komparátor** pro kontrolní výraz, například <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A>, a do **hodnoty pro porovnání**zadejte hodnotu pro svůj kontrolní výraz.

  ![Kontrolní výrazy programového testu UI](../test/media/codedui-3.png "CodedUI_3")

  Když jste přidali všechny kontrolní výrazy pro svůj test, klikněte na **tlačítko OK**.

  Chcete-li vygenerovat kód pro kontrolní výrazy a přidat ovládací prvek do mapy uživatelského rozhraní, klikněte na ikonu **generovat kód** . Zadejte název metody programového testu uživatelského rozhraní a popis metody, který bude přidán jako komentář pro metodu. Vyberte možnost **Přidat a generovat**. Potom klikněte na ikonu **Zavřít** a zavřete Tvůrce programového **testu uživatelského rozhraní**. Tím se vygeneruje kód podobný následujícímu kódu. Například pokud je název, který jste zadali, `AssertForAddTwoNumbers`, kód bude vypadat jako v tomto příkladu:

- Přidá volání metody Assert AssertForAddTwoNumbers do testovací metody v souboru programového testu uživatelského rozhraní:

  ```
  [TestMethod]
  public void CodedUITestMethod1()
  {
      this.UIMap.AddTwoNumbers();
      this.UIMap.AssertForAddTwoNumbers();
  }
  ```

   Úpravou tohoto souboru můžete změnit pořadí kroků a kontrolních výrazů nebo vytvořit nové testovací metody. Chcete-li přidat další kód, umístěte kurzor na testovací metodu a v místní nabídce vyberte možnost **generovat kód pro programový test uživatelského rozhraní**.

- Přidá metodu nazvanou `AssertForAddTwoNumbers` do vaší mapy uživatelského rozhraní (UIMap. UITest). Tento soubor se otevře v editoru programového testu UI, kde můžete upravit kontrolní výrazy.

   ![Upravit kontrolní výraz pomocí editoru programového testu UI](../test/media/cuit-editor-assert.png "CUIT_Editor_assert")

   Další informace naleznete v tématu [Úpravy programových testů uživatelského rozhraní pomocí editoru programových testů uživatelského rozhraní](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

   Můžete také zobrazit generovaný kód metody kontrolního výrazu v UIMap.Designer.cs. Tento soubor byste ale neměli upravovat. Chcete-li vytvořit upravenou verzi kódu, zkopírujte metody do jiného souboru, například UIMap.cs, přejmenujte metody a upravte je zde.

  ```
  public void AssertForAddTwoNumbers()
  {
      ...
  }
  ```

  *Ovládací prvek, který chcete vybrat, ztratí fokus a zmizí při pokusu o výběr nástroje Přidat kontrolní výrazy z Tvůrce programového testu uživatelského rozhraní. Návody vybrat ovládací prvek?* 
  **výběru skrytého ovládacího prvku pomocí klávesnice**

  V některých případech může být při [přidávání ovládacích prvků a ověřování jejich vlastností](#VerifyingCodeUsingCUITGenerateAssertions)nutné použít klávesnici. Například při pokusu o nahrání kódovaného testu uživatelského rozhraní, který používá ovládací prvek místní nabídky, seznam položek nabídky v ovládacím prvku ztratí fokus a zmizí při pokusu o výběr nástroje Přidat kontrolní výrazy z Tvůrce programového testu uživatelského rozhraní. To je znázorněno na následujícím obrázku, kde kontextová nabídka v aplikaci Internet Explorer ztratí fokus a zmizí, pokud se pokusíte o výběr pomocí nástroje Přidat kontrolní výrazy.

  ![CodedUITest&#95;SelectControlKeyboard](../test/media/codeduitest-selectcontrolkeyboard.png "CodedUITest_SelectControlKeyboard")

  Chcete-li použít klávesnici k výběru ovládacího prvku uživatelského rozhraní, najeďte myší nad ovládací prvek myší. Pak podržte stisknutou klávesu **CTRL** a klávesu **I** . Uvolněte klíče. Ovládací prvek je zaznamenán pomocí kódovaného tvůrce testů.

> [!WARNING]
> Pokud používáte Microsoft Lync, musíte před spuštěním Tvůrce programového testu uživatelského rozhraní zavřít Lync. Microsoft Lync má vliv na klávesovou zkratku **CTRL + I** .

 *Nemohu nahrávat ukazatel myši na ovládací prvek. Existuje toto řešení?*
 **Ruční zaznamenávání ukazatele myši**

 Za určitých okolností může konkrétní ovládací prvek, který se používá v programovém testu UI, vyžadovat použití klávesnice k ručnímu záznamu událostí při přechodu myší. Například při testování aplikace Windows Form nebo Windows Presentation Foundation (WPF) může existovat vlastní kód. Nebo může být definováno speciální chování pro najetí myší nad ovládací prvek, jako je například rozbalování uzlu stromu, když na něj uživatel najede myší. Chcete-li otestovat okolnosti, jako jsou tyto, je nutné ručně nastavit program Tvůrce programového testu uživatelského rozhraní, který přejedete nad ovládací prvek pomocí klávesových zkratek předdefinovaných klávesových zkratek.

 Při provádění programového testu uživatelského rozhraní, najeďte myší na ovládací prvek. Pak stiskněte a podržte klávesu CTRL, zatímco stisknete a podržíte klávesy SHIFT a R na klávesnici. Uvolněte klíče. Událost najetí myší je zaznamenána prostřednictvím kódovaného tvůrce testů.

 ![Najeďte myší CodedUI&#95;](../test/media/codedui-hover.png "CodedUI_Hover")

 Po vygenerování testovací metody se kód podobný následujícímu příkladu přidá do souboru UIMap.Desinger.cs:

```csharp
// Mouse hover '1' label at (87, 9)
Mouse.Hover(uIItem1Text, new Point(87, 9));

```

 *Přiřazení klíče pro zachytávání událostí při přechodu myší se v mém prostředí používá jinde. Můžu změnit výchozí přiřazení kláves?*
 **Konfigurace přiřazení klávesnice při najetí myší**

 V případě potřeby se výchozí přiřazení klávesnice CTRL + SHIFT + R, které se používá k aplikování událostí najetí myší v programových testech UI, dá nakonfigurovat tak, aby používalo jiné klíče.

> [!WARNING]
> Nemusíte měnit přiřazení klávesnice pro události ukazatele myši za běžných okolností. Při opětovném přiřazení klávesnice použijte upozornění. Vaše volba se už možná používá jinde v sadě Visual Studio nebo v testované aplikaci.

 Chcete-li změnit přiřazení klávesnice, je nutné upravit následující konfigurační soubor:

 `<drive letter:>\Program Files (x86)\Microsoft Visual Studio 11.0\Common7\IDE\CodedUITestBuilder.exe.config`

 V konfiguračním souboru změňte hodnoty `HoverKeyModifier` a `HoverKey` pro změnu přiřazení klávesnice:

```
<!-- Begin : Background Recorder Settings -->
<!-- HoverKey to use. -->
<add key="HoverKeyModifier" value="Control, Shift"/>
<add key="HoverKey" value="R"/>

```

 *Mám problémy s nahráváním ukazatele myši na webu. Je zde nějaká oprava?*
 **Nastavení implicitního efektu myši pro webový prohlížeč**

 Pokud na mnoha webech najedete myší na určitý ovládací prvek, rozbalí se a zobrazí se další podrobnosti. Obecně tyto vypadají jako nabídky v aplikacích klasické pracovní plochy. Vzhledem k tomu, že se jedná o společný vzor, kódované testy uživatelského rozhraní umožňují implicitní najetí myší na prohlížení webu. Pokud například záznam najedete myší v aplikaci Internet Explorer, aktivuje se událost. Tyto události mohou vést k nahranému nadbytečnému najetí myší. Z tohoto důvodu jsou implicitní najetí myší zaznamenávány s `ContinueOnError` nastavenou na `true` v konfiguračním souboru testu uživatelského rozhraní. To umožňuje, aby přehrávání pokračovalo i v případě neúspěchu události přechodu myší.

 Chcete-li povolit záznam implicitních pojetí myší ve webovém prohlížeči, otevřete konfigurační soubor:

 `<drive letter:>\Program Files (x86)\Microsoft Visual Studio 11.0\Common7\IDE\CodedUITestBuilder.exe.config`

 Ověřte, zda má konfigurační soubor klávesu `RecordImplicitiHovers` nastaveno na hodnotu `true`, jak je znázorněno v následující ukázce:

```
<!--Use this to enable/disable recording of implicit hovers.-->
<add key="RecordImplicitHover" value="true"/>

```

## <a name="VerifyingCodeCUITModify"></a>Přizpůsobení kódovaného testu uživatelského rozhraní
 Po vytvoření programového testu UI ho můžete upravit pomocí některého z následujících nástrojů v aplikaci Visual Studio:

- **Tvůrce programového testu uživatelského rozhraní:** Pomocí Tvůrce programového testu UI přidejte další ovládací prvky a ověření k vašim testům. Přečtěte si část [Přidání ovládacích prvků a ověření jejich vlastností](#VerifyingCodeUsingCUITGenerateAssertions) v tomto tématu.

- **Editor programového testu uživatelského rozhraní:** Editor programového testu UI umožňuje snadno upravit kódované testy uživatelského rozhraní. Pomocí editoru programového testu UI můžete vyhledat, zobrazit a upravit testovací metody. Můžete také upravit akce uživatelského rozhraní a jejich přidružené ovládací prvky v mapě ovládacího prvku uživatelského rozhraní. Další informace naleznete v tématu [Úpravy programových testů uživatelského rozhraní pomocí editoru programových testů uživatelského rozhraní](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

- **Editor kódu:**

  - Ručně přidejte kód pro ovládací prvky v testu, jak je popsáno v části [kódy a vlastnosti ovládacího prvku uživatelského rozhraní](#actions) v tomto tématu.

  - Po vytvoření programového testu UI ho můžete upravit tak, aby byl řízený daty. Další informace naleznete v tématu [vytváření programového testu uživatelského rozhraní řízeného daty](../test/creating-a-data-driven-coded-ui-test.md).

  - V průběhu přehrávání programového testu uživatelského rozhraní můžete určit, že se má test čekat na výskyt určitých událostí, jako je okno, které se má zobrazit, indikátor průběhu zmizí atd. Chcete-li to provést, přidejte příslušnou metodu UITestControl. WaitForControlXXX (). Úplný seznam dostupných metod naleznete v tématu vytváření programových [testů uživatelského rozhraní, které čekají na konkrétní události během přehrávání](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md). Příklad kódovaného testu uživatelského rozhraní, který čeká na povolení ovládacího prvku pomocí metody metody WaitForControlEnabled, naleznete v tématu [Návod: vytváření, úpravy a údržba programového testu uživatelského rozhraní](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md).

  - Programové testy UI zahrnují podporu pro některé ovládací prvky HTML5, které jsou součástí aplikace Internet Explorer 9 a Internet Explorer 10. Další informace naleznete v tématu [použití ovládacích prvků HTML5 v programových testech UI](../test/using-html5-controls-in-coded-ui-tests.md).

  - **Pokyny pro kódování programového testu uživatelského rozhraní:**

    - [Anatomie programového testu UI](../test/anatomy-of-a-coded-ui-test.md)

    - [Doporučené postupy pro programové testy UI](../test/best-practices-for-coded-ui-tests.md)

    - [Testování rozsáhlé aplikace s více mapami uživatelského rozhraní](../test/testing-a-large-application-with-multiple-ui-maps.md)

    - [Podporované konfigurace a platformy pro programové testy uživatelského rozhraní a zaznamenávání akcí](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)

### <a name="generatedCode"></a>Generovaný kód
 Když zvolíte možnost **generovat kód**, vytvoří se několik částí kódu:

- **Řádek v testovací metodě.**

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

   Můžete také přidat nové testovací metody a přidat kód do nich stejným způsobem. Každá testovací metoda musí mít atribut `[TestMethod]`.

- **Metoda v UIMap. UITest**

   Tato metoda zahrnuje podrobné informace o vámi zaznamenaných akcích nebo o hodnotě, kterou jste ověřili. Tento kód můžete upravit otevřením UIMap. UITest. Otevře se ve specializovaném editoru, ve kterém můžete zaznamenané akce odstranit nebo Refaktorovat.

   Youcan také zobrazit vygenerovanou metodu v UIMap.Designer.cs. Tato metoda provádí akce, které jste si poznamenali při spuštění testu.

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

   Upravené verze těchto metod můžete upravit jejich zkopírováním do UIMap.cs. Můžete například vytvořit parametrizovanou verzi, kterou můžete volat z testovací metody:

  ```csharp
  // File: UIMap.cs
  public partial class UIMap // Same partial class
  {
    /// <summary>
    /// Add two numbers – parameterized version
    /// </summary>
    public void AddTwoNumbers(int firstNumber, int secondNumber)
    { ...   // Code modified to use parameters.
    }
  }
  ```

- **Deklarace v UIMap. UITest**

   Tyto deklarace představují ovládací prvky uživatelského rozhraní aplikace, které jsou používány vaším testem. Jsou používány generovaným kódem k provozování ovládacích prvků a k přístupu ke svým vlastnostem.

   Můžete je také použít, pokud píšete vlastní kód. Například můžete mít testovací metodu zvolit hypertextový odkaz ve webové aplikaci, zadat hodnotu do textového pole nebo vytvořit větev a provést jiné testovací akce na základě hodnoty v poli.

   Pro usnadnění testování rozsáhlých aplikací můžete přidat více programových testů UI a více objektů a souborů map uživatelského rozhraní. Další informace najdete v tématu [testování velké aplikace s více mapami uživatelského rozhraní](../test/testing-a-large-application-with-multiple-ui-maps.md).

  Další informace o vygenerovaném kódu naleznete v tématu [anatomie kódovaného testu uživatelského rozhraní](../test/anatomy-of-a-coded-ui-test.md).

### <a name="actions"></a>Kódování akcí a vlastností ovládacích prvků uživatelského rozhraní
 Při práci s ovládacími prvky testu uživatelského rozhraní v programových testech UI jsou rozděleny do dvou částí: akce a vlastnosti.

- První část se skládá z akcí, které lze provádět v ovládacích prvcích testu uživatelského rozhraní. Například kódované testy uživatelského rozhraní mohou simulovat kliknutí myší na ovládací prvek testu uživatelského rozhraní nebo simulovat klíče, které jsou zadány na klávesnici a ovlivnit ovládací prvek testu uživatelského rozhraní.

- Druhá část se skládá z možnosti získat a nastavit vlastnosti ovládacího prvku test uživatelského rozhraní. Například kódované testy uživatelského rozhraní mohou získat počet položek v `ListBox`nebo nastavit `CheckBox` na vybraný stav.

  **Přístup k akcím ovládacího prvku test uživatelského rozhraní**

  Chcete-li provádět akce s ovládacími prvky testu uživatelského rozhraní, jako je kliknutí myší nebo akce klávesnice, použijte metody v třídách <xref:Microsoft.VisualStudio.TestTools.UITesting.Mouse> a <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard>:

- K provedení akce orientované na myš, jako je například kliknutí myší, na ovládacím prvku test uživatelského rozhraní, použijte <xref:Microsoft.VisualStudio.TestTools.UITesting.Mouse.Click%2A>.

   `Mouse.Click(buttonCancel);`

- K provedení akcí orientovaných na klávesnici, jako je například psaní do ovládacího prvku pro úpravy, použijte <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A>.

   `Keyboard.SendKeys(textBoxDestination, @"C:\Temp\Output.txt");`

  **Přístup k vlastnostem ovládacího prvku test uživatelského rozhraní**

  Chcete-li získat a nastavit hodnoty vlastností specifických pro ovládací prvky uživatelského rozhraní, můžete přímo získat nebo nastavit hodnoty vlastností ovládacího prvku nebo můžete použít metody <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A?displayProperty=fullName> a <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A?displayProperty=fullName> s názvem konkrétní vlastnosti, kterou chcete získat nebo nastavit.

  <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A> vrátí objekt, který lze následně přetypovat na příslušný <xref:System.Type>. <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A> přijímá objekt pro hodnotu vlastnosti.

##### <a name="to-get-or-set-properties-from-ui-test-controls-directly"></a>Chcete-li získat nebo nastavit vlastnosti z ovládacích prvků testu uživatelského rozhraní přímo

- Pomocí ovládacích prvků, které jsou odvozeny z T:Microsoft.VisualStudio.TestTools.UITesting.UITestControl, jako je například T:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls.HtmlList nebo T: Microsoft. VisualStudio. TestTools. UITesting. WinControls. WinComboBox, můžete získat nebo nastavit hodnoty vlastností přímo následujícím způsobem:

    ```
    int i = myHtmlList.ItemCount;
    myWinCheckBox.Checked = true;
    ```

##### <a name="to-get-properties-from-ui-test-controls"></a>Získání vlastností z ovládacích prvků testu uživatelského rozhraní

- Chcete-li získat hodnotu vlastnosti z ovládacího prvku, použijte <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A>.

- Chcete-li určit vlastnost ovládacího prvku, který má být získán, použijte odpovídající řetězec z třídy `PropertyNames` v každém ovládacím prvku jako parametr pro <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A>.

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A> vrátí příslušný datový typ, ale tato návratová hodnota je převedena jako <xref:System.Object>. Návratový <xref:System.Object> musí být převeden jako příslušný typ.

     Příklad:

     `int i = (int)GetProperty(myHtmlList.PropertyNames.ItemCount);`

##### <a name="to-set-properties-for-ui-test-controls"></a>Nastavení vlastností ovládacích prvků testu uživatelského rozhraní

- Chcete-li nastavit vlastnost v ovládacím prvku, použijte <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A>.

- Chcete-li určit vlastnost ovládacího prvku, který má být nastaven, použijte odpovídající řetězec z `PropertyNames` třídy jako první parametr pro <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A>, s hodnotou vlastnosti jako druhý parametr.

     Příklad:

     `SetProperty(myWinCheckBox.PropertyNames.Checked, true);`

### <a name="debugging"></a> Ladění
 Můžete analyzovat kódované testy uživatelského rozhraní pomocí protokolů programových testů uživatelského rozhraní. Protokoly programových testů uživatelského rozhraní filtr a zaznamenávají důležité informace o běhu programového testu uživatelského rozhraní. Formát protokolů vám umožní rychle ladit problémy. Další informace naleznete v tématu [Analýza programových testů uživatelského rozhraní pomocí protokolů kódovaného testu uživatelského rozhraní](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md).

## <a name="VerifyCodeUsingCUITWhatsNext"></a>Co dál?
 **Další možnosti pro spuštění programových testů uživatelského rozhraní:** Programové testy uživatelského rozhraní lze spustit přímo ze sady Visual Studio, jak je popsáno dříve v tomto tématu. Kromě toho můžete spouštět automatizované testy uživatelského rozhraní z [!INCLUDE[TCMext](../includes/tcmext-md.md)]nebo z [!INCLUDE[esprbuild](../includes/esprbuild-md.md)]. Když jsou programové testy uživatelského rozhraní automatizované, musí při jejich spouštění pracovat na rozdíl od jiných automatizovaných testů.

- [Postupy: spuštění testů z Microsoft Visual Studio](https://msdn.microsoft.com/library/1a1207a9-2a33-4a1e-a1e3-ddf0181b1046)

- [Spouštění automatizovaných testů v Microsoft Test Manager](https://msdn.microsoft.com/0632f265-63fe-4859-a413-9bb934c66835)

- [Postupy: konfigurace a spuštění plánovaných testů po sestavení aplikace](https://msdn.microsoft.com/32acfeb1-b1aa-4afb-8cfe-cc209e6183fd)

- [Spuštění testů v procesu sestavení](https://msdn.microsoft.com/library/d05743a1-c5cf-447e-bed9-bed3cb595e38)

- [Spouštění automatizovaných testů z příkazového řádku](https://msdn.microsoft.com/library/f18179c6-b688-4e41-9898-8aca130c4fc3)

- [Postupy: nastavení testovacího agenta pro spouštění testů, které komunikují s plochou](/visualstudio/test/how-to-set-up-your-test-agent-to-run-tests-that-interact-with-the-desktop?view=vs-2015)

- [&#91;vyřazení&#93; pomocí programových testů uživatelského rozhraní v zátěžových testech](https://msdn.microsoft.com/library/704339ff-7da7-4d5f-acb3-c3b23f4acb43)

  **Přidání podpory pro vlastní ovládací prvky:**  Rozhraní programového testování uživatelského rozhraní nepodporuje všechny možné uživatelské rozhraní a nemusí podporovat uživatelské rozhraní, které chcete testovat. Například nelze okamžitě vytvořit programový test uživatelského rozhraní pro [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)]. Můžete však vytvořit rozšíření pro programové testování uživatelského rozhraní, které bude podporovat vlastní ovládací prvek.

- [Povolení programového testování uživatelského rozhraní pro vaše ovládací prvky](../test/enable-coded-ui-testing-of-your-controls.md)

- [Rozšiřování programových testů UI a záznamů akcí k podpoře Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)

  Programové testy uživatelského rozhraní se často používají k automatizaci ručních testů. Další pokyny naleznete v tématu [testování pro průběžné doručování pomocí sady Visual Studio 2012 – Kapitola 5: automatizace systémových testů](https://go.microsoft.com/fwlink/?LinkID=255196). Další informace o manuálních testech naleznete v [ &#91;tématu&#93; vyřazeno Vytváření manuálních testovacích případů pomocí Microsoft Test Manager](https://msdn.microsoft.com/library/9989e184-c8e4-444b-998d-a1a5ec94461e). Další informace o automatizovaných systémových testech naleznete v tématu [vytváření automatizovaných testů pomocí Microsoft Test Manager](https://msdn.microsoft.com/7b5075ee-ddfe-411d-b1d4-94283550a5d0).

## <a name="external-resources"></a>Externí zdroje

### <a name="guidance"></a>Doprovodné materiály
- [Testování pro průběžné doručování pomocí sady Visual Studio 2012 – Kapitola 2: testování částí: testování uvnitř](https://go.microsoft.com/fwlink/?LinkID=255188)

- [Testování pro průběžné doručování pomocí sady Visual Studio 2012 – Kapitola 5: automatizace systémových testů](https://go.microsoft.com/fwlink/?LinkID=255196)

### <a name="faq"></a>Nejčastější dotazy
- [Nejčastější dotazy k programovým testům UI – 1](https://go.microsoft.com/fwlink/?LinkID=230576)

- [Nejčastější dotazy k programovým testům UI – 2](https://go.microsoft.com/fwlink/?LinkID=230578)

### <a name="forum"></a>Fórum
- [Testování automatizace uživatelského rozhraní sady Visual Studio (zahrnuje CodedUI)](https://go.microsoft.com/fwlink/?LinkID=224497)

## <a name="see-also"></a>Viz také:

- [UIMap](/previous-versions/dd580454(v=vs.140))
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>
- [Zlepšení kvality kódu](https://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)
- [Návod: Vytváření, upravování a údržba programového testu UI](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
- [Anatomie programového testu UI](../test/anatomy-of-a-coded-ui-test.md)
- [Doporučené postupy pro programové testy UI](../test/best-practices-for-coded-ui-tests.md)
- [Testování rozsáhlé aplikace s více mapami uživatelského rozhraní](../test/testing-a-large-application-with-multiple-ui-maps.md)
- [Úpravy programových testů uživatelského rozhraní pomocí Editoru programových testů uživatelského rozhraní](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)
- [Podporované konfigurace a platformy pro programové testy uživatelského rozhraní a zaznamenávání akcí](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
- [Upgrade programových testů UI z produktu Visual Studio 2010](../test/upgrading-coded-ui-tests-from-visual-studio-2010.md)
- [Generování kódovaného testu uživatelského rozhraní z existujícího záznamu akce](https://msdn.microsoft.com/library/56736963-9027-493b-b5c4-2d4e86d1d497)
