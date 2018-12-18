---
title: Použití automatizace uživatelského rozhraní k testování kódu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
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
ms.author: gewarren
manager: douge
ms.openlocfilehash: 251f6a99f64a191f1a5d957157c06c7e89147217
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49812670"
---
# <a name="use-ui-automation-to-test-your-code"></a>Použití automatizace uživatelského rozhraní k testování kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Automatizované testy, které ovládají aplikaci prostřednictvím jejího uživatelského rozhraní (UI) jsou označovány jako *programové testy UI* (CUITs). Tyto testy zahrnují funkční testování ovládacích prvků uživatelského rozhraní. Umožňují ověřit, že celá aplikace včetně uživatelského rozhraní, funguje správně. Programové testy uživatelského rozhraní jsou obzvláště užitečná, pokud je ověření nebo jiná logika v uživatelském rozhraní, například na webové stránce. Používají se také často k automatizaci existujícího manuálního testu.  
  
 Jak je znázorněno na následujícím obrázku, může být typické vývojové prostředí, kde na začátku můžete jednoduše svou aplikaci (F5) a klikněte na tlačítko prostřednictvím ovládacích prvků uživatelského rozhraní k ověření, že všechno správně funguje. Můžete pak se rozhodnout vytvořit programový test, takže není nutné a pokračujte v testování aplikace ručně. V závislosti na konkrétní funkce testování ve vaší aplikaci můžete napsat kód pro funkční testování nebo pro test integrace, který může nebo nemusí obsahovat testování na úrovni uživatelského rozhraní. Pokud chcete jednoduše přímý přístup k spustí nějakou obchodní logiku, může kód testu jednotek. Ale za určitých okolností může být vhodné zahrnout testování různých ovládacích prvků uživatelského rozhraní v aplikaci. Programový test uživatelského rozhraní můžete automatizovat počáteční (F5) scénář, ověření, že změny v kódu neovlivní funkčnost aplikace.  
  
 ![Testování během vývoje aplikace](../test/media/cuit-overview.png "CUIT_Overview")  
  
 Vytvoření programového testu uživatelského rozhraní je jednoduché. Můžete jednoduše ručním prováděním testu při testování Tvůrce CUIT běží na pozadí. Můžete také určit, jaké hodnoty by se zobrazit v konkrétních polích. Tvůrce testu CUIT zaznamená vaše akce a generuje kód z nich. Po vytvoření testu, můžete ho upravit v začínáte se speciálním editorem, který umožňuje upravit posloupnost akcí.  
  
 Případně pokud máte testovací případ, která byla zaznamenána v nástroji Microsoft Test Manager, může generovat kód od. Další informace najdete v tématu [záznam a přehrávání zpět manuálních testů](http://msdn.microsoft.com/library/9792e72f-600e-441f-9d4e-6510e5965665).  
  
 Specializované Tvůrce CUIT testu a editor umožňují snadno vytvářet a upravovat programové testy uživatelského rozhraní, i když jsou hlavní dovednosti koncentrované testování místo psaní kódu. Ale pokud jste vývojář a chcete rozšířit test pokročilejší způsobem, kód je strukturována tak, aby se snadno kopírovat a upravit. Například může zaznamenat test koupit na webu a pak upravte generovaný kód pro přidání smyčku, která koupí mnoho položek.  
  
 **Požadavky**  
  
- Visual Studio Enterprise  
  
  Další informace o tom, které platformy a konfigurace podporují programové testy UI, naleznete v tématu [podporované konfigurace a platformy pro kódované testy uživatelského rozhraní a zaznamenávání akcí](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md).  
  
  **V tomto tématu**  
  
- [Vytváření programových testů UI](#VerifyingCodeUsingCUITCreate)  
  
  -   [Main – procedura](#VerifyingCodeUsingCUITCreate)  
  
  -   [Spuštění a zastavení aplikace](#starting)  
  
  -   [Ověření vlastností ovládacích prvků uživatelského rozhraní](#VerifyingCodeUsingCUITGenerateAssertions)  
  
- [Přizpůsobení programového testu UI](#VerifyingCodeCUITModify)  
  
  -   [Generovaný kód](#generatedCode)  
  
  -   [Kódování akce ovládacího prvku uživatelského rozhraní a vlastnosti](#actions)  
  
  -   [Ladění](#debugging)  
  
- [Co se chystá](#VerifyCodeUsingCUITWhatsNext)  
  
##  <a name="VerifyingCodeUsingCUITCreate"></a> Vytváření programových testů UI  
  
1. **Vytvořte projekt programového testu UI.**  
  
    Programové testy uživatelského rozhraní musí být součástí projektu programového testu UI. Pokud ještě nemáte projekt programového testu uživatelského rozhraní, vytvořte si ho. V **Průzkumníka řešení**, v místní nabídce řešení zvolte **přidat**, **nový projekt** a pak vyberte buď **jazyka Visual Basic** nebo **Visual C#**. Dále zvolte **testovací**, **programový Test uživatelského rozhraní**.  
  
   - <em>Nevidím **programový Test uživatelského rozhraní</em>* šablony projektu.*  
  
      Pravděpodobně používáte verzi sady Visual Studio, který nepodporuje programové testy uživatelského rozhraní. Chcete-li vytvořit kódované testy uživatelského rozhraní, musíte použít Visual Studio Enterprise.  
  
2. **Přidejte soubor do programového testu uživatelského rozhraní.**  
  
    Pokud jste právě vytvořili projekt programového uživatelského rozhraní, první soubor CUIT je automaticky přidán. Pokud chcete přidat jiný soubor testu, otevřete místní nabídku na projekt programového testu UI, přejděte na **přidat**a klikněte na tlačítko **programový Test uživatelského rozhraní**.  
  
    ![Vytvořit programový test UI](../test/media/codedui-create.png "CodedUI_Create")  
  
    V **generovat kód pro programový Test uživatelského rozhraní** dialogového okna zvolte **zaznamenat akce, upravit mapu uživatelského rozhraní nebo přidat kontrolní výrazy**.  
  
    ![Vyberte záznamu akce](../test/media/codedui-codegendialogb.png "CodedUI_CodeGenDialogB")  
  
    Tvůrce programového testu uživatelského rozhraní se zobrazí a je minimalizován sady Visual Studio.  
  
    ![Tvůrce programového testu UI](../test/media/codedui-testbuilder.png "CodedUI_TestBuilder")  
  
3. **Zaznamenejte posloupnost akcí**.  
  
    **Účelem zahájení zaznamenávání**, zvolte **záznam** ikonu. Provedení akce, které chcete otestovat ve vaší aplikaci, včetně spuštění aplikace, pokud je povinný.  
  
    Například pokud testujete webovou aplikaci, můžete může spustit prohlížeč, přejděte na web a přihlaste se k aplikaci.  
  
    **Pozastavit záznam**, například pokud budete muset řešit příchozí pošty, zvolte **pozastavit**.  
  
   > [!WARNING]
   >  Všechny akce provedené v klientských počítačích, bude zaznamenán. Pozastavte záznam, pokud provádíte akce, které může vést k citlivá data nebudou zahrnuty v záznamu.  
  
    **Chcete-li odstranit některé akce** , který jste si poznamenali omylem, zvolte **upravit akce**.  
  
    **Ke generování kódu** , který bude replikovat vaše akce, zvolte **generovat kód** ikonu a zadejte název a popis pro kódované UI testovací metoda.  
  
4. **Ověřte hodnoty v polích uživatelského rozhraní, jako je například textová pole**.  
  
    Zvolte **přidat kontrolní výrazy** v Tvůrce programového testu UI a klikněte na tlačítko ovládacího prvku uživatelského rozhraní ve spuštěné aplikaci. V seznamu vlastností, které se zobrazí, vyberte vlastnosti, například **Text** v textovém poli. V místní nabídce zvolte **přidat kontrolní výraz**. V dialogovém okně vyberte operátor porovnání, hodnotu porovnání a chybová zpráva.  
  
    Zavřete okno kontrolní výraz a zvolte **generovat kód**.  
  
    ![Programový test uživatelského rozhraní, které cílí na element](../test/media/codedui-1.png "CodedUI_1")  
  
   > [!TIP]
   >  Střídání nahrávání akcí a ověření hodnot. Generování kódu na konci každé posloupnost akcí nebo ověření. Pokud chcete, bude možné později vložit nové akce a ověření.  
  
    Další podrobnosti najdete v tématu [ověřování vlastnosti ovládacích prvků](#VerifyingCodeUsingCUITGenerateAssertions).  
  
5. **Zobrazení kódu vygenerovaného testu**.  
  
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
  
6. **Přidání více akcí a kontrolní výrazy**.  
  
    Umístěte kurzor na slovo v odpovídajícím bodě v testovací metodě a potom v místní nabídce zvolte **generovat kód pro programový Test uživatelského rozhraní**. V tomto okamžiku se vloží nový kód.  
  
7. **Upravit podrobnosti o testovacích akcí a kontrolní výrazy**.  
  
    Otevřete UIMap.uitest. Tento soubor se otevře v editoru programového testu UI, kde je můžete upravit libovolnou posloupností akce, které jste si poznamenali i upravit vaše kontrolní výrazy.  
  
    ![Programové Editor testu UI](../test/media/cuit-editor-edit.png "CUIT_Editor_edit")  
  
    Další informace najdete v tématu [testů uživatelského rozhraní programového úpravy pomocí editoru programového testu UI](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).  
  
8. **Spustit test**.  
  
    Pomocí nástroje Test Explorer, nebo otevřete místní nabídku v testovací metodě a klikněte na tlačítko **spustit testy**. Další informace o tom, jak spustit testy, naleznete v tématu [spouštění testů jednotek pomocí Průzkumníka testů](../test/run-unit-tests-with-test-explorer.md) a *dalších možností pro spouštění programových testů UI* v [co se chystá?](#VerifyCodeUsingCUITWhatsNext) části na konci tohoto tématu.  
  
   Zbývající části tohoto tématu poskytují další podrobnosti o postupu v tomto postupu.  
  
   Podrobnější příklad naleznete v tématu [návod: vytváření, úpravy a údržba programového testu UI](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md). V tomto návodu vytvoříte jednoduchou aplikaci Windows Presentation Foundation (WPF) pro demonstraci vytvoření, úpravy a správy programového testu UI. Návod poskytuje řešení pro opravu testů, které byly poškozeny různými chybami časování a refaktoringem ovládacích prvků.  
  
###  <a name="starting"></a> Spuštění a zastavení testovanou aplikaci  
 *Nechci spouštět a zastavovat Moje aplikace, prohlížeče nebo databáze samostatně pro každý test. Jak se můžu vyhnout, který?*  
  
-   ![Prerequsite](../test/media/prereq.png "požadavky") Pokud nechcete pro záznam akce, které chcete spustit aplikaci v rámci testu, je nutné spustit aplikace, než se rozhodnete **záznam** ikonu.  
  
-   ![Prerequsite](../test/media/prereq.png "požadavky")na konci testu je proces, ve kterém běží test ukončen. Pokud jste začali vaše aplikace v testu, aplikace obvykle ukončí.  Pokud nechcete, aby test zavřete aplikaci při jejím ukončení, musíte přidat soubor s příponou .runsettings do vašeho řešení a použití `KeepExecutorAliveAfterLegacyRun` možnost. Další informace najdete v tématu [konfigurace testů jednotek s použitím souboru .runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).  
  
-   ![Prerequsite](../test/media/prereq.png "požadavky") můžete přidat testovací metodu initialize, identifikovat podle atributu [TestInitialize], která spustí kód na začátku každé zkušební metody. Například by mohl spustit aplikaci z metody TestInitialize.  
  
-   ![Prerequsite](../test/media/prereq.png "požadavky") přidáte čistící metoda testu, identifikovat podle atributu [TestCleanup], která spustí kód na konci jednotlivých zkušebních metod. Například metoda zavřít aplikaci může volat z metoda TestCleanup.  
  
###  <a name="VerifyingCodeUsingCUITGenerateAssertions"></a> Ověření vlastností ovládacích prvků uživatelského rozhraní  
 Můžete použít **Tvůrce programového testu UI** přidat ovládací prvek uživatelského rozhraní (UI) pro <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> pro test nebo ke generování kódu pro metodu ověřování, používá kontrolní výraz pro ovládací prvek uživatelského rozhraní.  
  
 Chcete-li vygenerovat kontrolní výrazy pro vaše ovládací prvky uživatelského rozhraní, zvolte **přidat kontrolní výrazy** nástroj Tvůrce programového testu UI a přetáhněte ji na ovládací prvek na aplikaci v rámci testu, který chcete ověřit správnost. Pokud pole obsahuje ovládací prvek, uvolněte tlačítko myši. Kód třídy ovládacího prvku se okamžitě vytvoří v `UIMap.Designer.cs` souboru.  
  
 ![Programový test uživatelského rozhraní, které cílí na element](../test/media/codedui-1.png "CodedUI_1")  
  
 Vlastnosti pro tento ovládací prvek je nyní obsažena v **přidat kontrolní výrazy** dialogové okno.  
  
 Jiný způsob přechodu na určitý ovládací prvek je na šipku **(<<)** rozbalte zobrazení **mapování ovládacího prvku UI**. Najít nadřazený, na stejné úrovni nebo podřízený ovládací prvek, klikněte na libovolné místo na mapě a pohyb stromu pomocí kláves se šipkami.  
  
 ![Programových testů UI vlastnosti](../test/media/codedui-2.png "CodedUI_2")  
  
- *Všechny vlastnosti se mi nezobrazují, když v aplikaci vyberte ovládací prvek, nebo se mi nezobrazují ovládacího prvku v mapování ovládacího prvku uživatelského rozhraní.*  
  
   Ovládací prvek, který chcete ověřit kód aplikace, musí mít jedinečné ID, jako je například atributu HTML ID nebo WPF UId. Můžete potřebovat k aktualizaci kódu aplikace přidejte tyto identifikátory.  
  
  Dále otevřete místní nabídku pro vlastnost pro ovládací prvek uživatelského rozhraní, který chcete ověřit a pak přejděte na **přidat kontrolní výraz**. V **přidat kontrolní výraz** dialogové okno, vyberte **Komparátor** pro vaše kontrolního výrazu, například <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A>a zadejte hodnotu pro vaše kontrolního výrazu v **hodnotu porovnání**.  
  
  ![Programových testů UI kontrolní výrazy](../test/media/codedui-3.png "CodedUI_3")  
  
  Po přidání všech kontrolních výrazů pro test, zvolte **OK**.  
  
  Chcete-li generovat kód pro vaše kontrolní výrazy a přidejte ovládací prvek do mapy uživatelského rozhraní, zvolte **generovat kód** ikonu. Zadejte název pro metodu programového testu uživatelského rozhraní a popis pro metodu, která se přidají jako komentář pro metodu. Zvolte **přidejte a generujte**. V dalším kroku vyberte **zavřete** ikonu Zavřít **Tvůrce programového testu UI**. Tím se vygeneruje kód, podobně jako v následujícím kódu. Například, pokud zadaný název je `AssertForAddTwoNumbers`, kód bude vypadat jako v tomto příkladu:  
  
- Volání metody assert AssertForAddTwoNumbers přidá do testovací metody v souboru programového testu uživatelského rozhraní:  
  
  ```  
  [TestMethod]  
  public void CodedUITestMethod1()  
  {  
      this.UIMap.AddTwoNumbers();  
      this.UIMap.AssertForAddTwoNumbers();  
  }  
  ```  
  
   Můžete upravit tento soubor, chcete-li změnit pořadí kroků a kontrolní výrazy nebo k vytvoření nové metody testu. Chcete-li přidat další kód, umístěte kurzor v testovací metodě a v místní nabídce zvolte **generovat kód pro programový Test uživatelského rozhraní**.  
  
- Přidá metodu nazvanou `AssertForAddTwoNumbers` do mapy uživatelského rozhraní (UIMap.uitest). Tento soubor se otevře v editoru programového testu UI, kde můžete upravit kontrolní výrazy.  
  
   ![Vyhodnocení upravit pomocí editoru programového testu UI](../test/media/cuit-editor-assert.png "CUIT_Editor_assert")  
  
   Další informace najdete v tématu [testů uživatelského rozhraní programového úpravy pomocí editoru programového testu UI](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).  
  
   Můžete také zobrazit generovaný kód výrazu metody v UIMap.Designer.cs. Tento soubor by neměl upravit. Pokud chcete vytvořit přizpůsobené verzi kódu, zkopírovat do jiného souboru, jako je například UIMap.cs metody, přejmenujte metody a upravit je.  
  
  ```  
  public void AssertForAddTwoNumbers()  
  {  
      ...  
  }  
  ```  
  
  *Ovládací prvek, který chcete vybrat ztratí fokus a zmizí při vyberte přidat kontrolní výrazy nástroj Tvůrce programového testu UI. Jak se vybírá ovládací prvek?*  
  **Výběr skrytý ovládací prvek pomocí klávesnice**  
  
  V některých případech, kdy [přidání ovládacích prvků a jejich vlastnosti ověřování](#VerifyingCodeUsingCUITGenerateAssertions), možná budete muset pomocí klávesnice. Například když zkusíte zaznamenat programový test UI používající ovládací prvek místní nabídky, seznam položek nabídky v ovládacím prvku ztratí fokus a zmizí při pokusu o vyberte nástroj přidat kontrolní výrazy Tvůrce programového testu UI. To je patrné na následujícím obrázku, kde bude místní nabídky v aplikaci Internet Explorer ztratí fokus a zmizí, pokud se pokusíte vyberte pomocí nástroje Přidat kontrolní výrazy.  
  
  ![CodedUITest&#95;SelectControlKeyboard](../test/media/codeduitest-selectcontrolkeyboard.png "CodedUITest_SelectControlKeyboard")  
  
  Použití klávesnice k výběru ovládacího prvku uživatelského rozhraní, najeďte myší ovládací prvek pomocí myši. Potom podržte klávesu **Ctrl** klíč a **můžu** klíče ve stejnou dobu. Verze klíče. Tvůrce programového testu UT zaznamenané ovládacího prvku.  
  
> [!WARNING]
>  Pokud používáte Microsoft Lync, je třeba nejprve spustit Tvůrce programového testu UI zavřít Lync. Microsoft Lync, dochází ke kolizím s **Ctrl + I** klávesové zkratky.  
  
 *Můžu nelze zaznamenat najedete myší na ovládací prvek. Je možné vyřešit?*  
 **Ruční nahrávání se ukazatel myši nachází**  
  
 Za určitých okolností konkrétní ovládací prvek, který se používá v programového uživatelského rozhraní testu může vyžadovat použití klávesnice k události ručně zaznamenávat myši při najetí myší. Například při testování formuláře Windows nebo aplikaci Windows Presentation Foundation (WPF), může existovat vlastní kód. Nebo může být zvláštní chování definované pro najedete myší na ovládací prvek, jako je například uzel stromu, rozbalení, když uživatel najede myší ho. K otestování za těchto okolností, budete muset ručně byli informováni vždy, předdefinované Tvůrce programového testu UI, které jsou ukazatele myši nad ovládací prvek stisknutím kombinace kláves.  
  
 Když provádíte programového testu uživatelského rozhraní, najeďte myší ovládací prvek. Stiskněte a podržte klávesu Ctrl, a stiskněte a podržte klávesu Shift a R na klávesnici. Verze klíče. Pomocí Tvůrce programového testu UT se zaznamená událost myši při najetí myší.  
  
 ![CodedUI&#95;při najetí myší](../test/media/codedui-hover.png "CodedUI_Hover")  
  
 Po vytvoření testovací metody, podobně jako v následujícím příkladu kódu se přidají do souboru UIMap.Desinger.cs:  
  
```csharp  
// Mouse hover '1' label at (87, 9)  
Mouse.Hover(uIItem1Text, new Point(87, 9));  
  
```  
  
 *Přiřazení klíče pro zachytávání událostí myši při najetí myší se Moje prostředí používá jinde. Můžete změnit výchozí přiřazení klíče?*  
 **Konfigurace přiřazení klávesových přechodu myši**  
  
 V případě potřeby výchozí přiřazení klávesnice Ctrl + Shift + R, který se používá k aplikování ukázání událostí myši v programových testů UI může nakonfigurován k používání různých klíčů.  
  
> [!WARNING]
>  Není nutné změnit přiřazení klávesnice pro události myši při najetí myší za běžných okolností. Buďte opatrní při přiřazení přiřazení klávesnice. Podle vašeho výběru mohou být již používá jinde v rámci sady Visual Studio nebo aplikaci právě testováno.  
  
 Chcete-li změnit přiřazení klávesnice, je třeba upravit následující konfigurační soubor:  
  
 `<drive letter:>\Program Files (x86)\Microsoft Visual Studio 11.0\Common7\IDE\CodedUITestBuilder.exe.config`  
  
 V konfiguračním souboru změňte hodnoty `HoverKeyModifier` a `HoverKey` pro změnu přiřazení klávesnice:  
  
```  
<!-- Begin : Background Recorder Settings -->  
<!-- HoverKey to use. -->  
<add key="HoverKeyModifier" value="Control, Shift"/>  
<add key="HoverKey" value="R"/>  
  
```  
  
 *Mám problémy s nahráváním umístění ukazatele myši na webovou stránku. Existuje opravy v tomto případě příliš?*  
 **Nastavení implicitní ukazatel myši nachází pro webový prohlížeč**  
  
 V mnoha weby když najedete myší na ovládací prvek konkrétní rozšiřuje zobrazíte další podrobnosti. Obecně tyto vypadat nabídky v aplikacích klasické pracovní plochy. Protože jde o častou, programové testy uživatelského rozhraní povolit implicitní ukazatele pro procházení webu. Například pokud jste záznam se nachází v aplikaci Internet Explorer, je vyvolána událost. Tyto události může vést k redundantní pohybuje nahrávají. Z toho důvodu se zaznamenávají implicitní ukazatele s `ContinueOnError` nastavena na `true` v konfiguračním souboru testu uživatelského rozhraní. To umožňuje přehrávání pokračovat, pokud událost při najetí myší se nezdaří.  
  
 Pokud chcete povolit nahrávání implicitní ukazatele ve webovém prohlížeči, otevřete konfigurační soubor:  
  
 `<drive letter:>\Program Files (x86)\Microsoft Visual Studio 11.0\Common7\IDE\CodedUITestBuilder.exe.config`  
  
 Ověřte, zda konfigurační soubor má klíč `RecordImplicitiHovers` nastavena na hodnotě `true` jak je znázorněno v následujícím příkladu:  
  
```  
<!--Use this to enable/disable recording of implicit hovers.-->  
<add key="RecordImplicitHover" value="true"/>  
  
```  
  
##  <a name="VerifyingCodeCUITModify"></a> Přizpůsobení programového testu UI  
 Po vytvoření programového testu UI, můžete ji upravit pomocí některého z následujících nástrojů v sadě Visual Studio:  
  
-   **Tvůrce programového testu UI:** do testů přidat další ovládací prvky a ověřování pomocí Tvůrce programového testu UI. V části [přidání ovládacích prvků a jejich vlastnosti ověřování](#VerifyingCodeUsingCUITGenerateAssertions) v tomto tématu.  
  
-   **Editor testu Coded UI:** Editor programového testu uživatelského rozhraní umožňuje snadno upravovat programové testy uživatelského rozhraní. Použití editoru programového testu UI, můžete vyhledat, zobrazit a upravit testovací metody. Můžete také upravit akce uživatelského rozhraní a jim přidružené ovládací prvky v mapování ovládacího prvku uživatelského rozhraní. Další informace najdete v tématu [testů uživatelského rozhraní programového úpravy pomocí editoru programového testu UI](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).  
  
-   **Editor kódu:**  
  
    -   Ručně přidejte kód pro ovládací prvky v testu, jak je popsáno v [akce ovládacího prvku uživatelského rozhraní kódování a vlastnosti](#VerifyingCodeCUITActionsandProperties) v tomto tématu.  
  
    -   Po vytvoření programového testu UI můžete upravit tak být řízený daty. Další informace najdete v tématu [vytváření data-Driven programový Test uživatelského rozhraní](../test/creating-a-data-driven-coded-ui-test.md).  
  
    -   Programové přehrávání testů uživatelského rozhraní webu můžete dát pokyn testů čekala určitých událostí pravděpodobnější, jako je okno se zobrazí indikátor průběhu signalizující zmizí a tak dále. K tomu přidáte odpovídající metodu UITestControl.WaitForControlXXX(). Úplný seznam dostupných metod najdete v tématu [vytváření programového uživatelského rozhraní testy čekat pro konkrétní události při přehrávání](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md). Příklad programový test UI, který čeká na ovládací prvek pro povolit pomocí WaitForControlEnabled metodu, najdete v části [návod: vytváření, úpravy a údržbu programový Test uživatelského rozhraní](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md).  
  
    -   Programové testy UI zahrnují podporu pro některé ovládací prvky jazyka HTML5, které jsou zahrnuty v aplikaci Internet Explorer 9 a Internet Explorer 10. Další informace najdete v tématu [pomocí ovládacích prvků HTML5 v programových testů uživatelského rozhraní](../test/using-html5-controls-in-coded-ui-tests.md).  
  
    -   **Programový test UI kódování pokyny:**  
  
        -   [Anatomie programového testu UI](../test/anatomy-of-a-coded-ui-test.md)  
  
        -   [Doporučené postupy pro programové testy UI](../test/best-practices-for-coded-ui-tests.md)  
  
        -   [Testování rozsáhlé aplikace s více mapami uživatelského rozhraní](../test/testing-a-large-application-with-multiple-ui-maps.md)  
  
        -   [Podporované konfigurace a platformy pro programové testy uživatelského rozhraní a zaznamenávání akcí](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)  
  
###  <a name="generatedCode"></a> Generovaný kód  
 Pokud zvolíte **generovat kód**, několika částí kódu jsou vytvořeny:  
  
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
  
   Klikněte pravým tlačítkem v této metodě, chcete-li přidat více zaznamenané akce a ověření. Můžete také upravit ho ručně, aby se rozšířit nebo upravit kód. Může některý kód například uzavřete ve smyčce.  
  
   Můžete také přidat nové metody testu, přidejte kód k nim stejným způsobem. Každá testovací metoda musí mít `[TestMethod]` atribut.  
  
- **Metoda ve UIMap.uitest**  
  
   Tato metoda zahrnuje podrobné akce, které jste si poznamenali nebo hodnotu, která jste ověřili. Tento kód můžete upravit tak, že otevřete UIMap.uitest. Otevře se v začínáte se speciálním editorem, ve kterém můžete odstranit nebo Refaktorujte již nahrané akce.  
  
   Vytvořena metoda Youcan také zobrazit v UIMap.Designer.cs. Tato metoda provádí akce, že jste si poznamenali při spuštění testu.  
  
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
  >  Tento soubor by neměl upravit, protože se znovu vygeneruje, když vytvoříte další testy.  
  
   Upravit verze těchto metod můžete nastavit zkopírováním UIMap.cs. Například může vytvořit parametrizovanou verzi, která lze volat z testovací metody:  
  
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
  
- **Deklarace v UIMap.uitest**  
  
   Tyto deklarace představují ovládací prvky uživatelského rozhraní aplikace, které jsou používány vašeho testu. Používají se vygenerovaný kód pracovat ovládací prvky a přístup k jejich vlastností.  
  
   Můžete také je můžete psát vlastní kód. Například můžete mít vaše testovací metoda vyberte hypertextový odkaz ve webové aplikaci, zadejte hodnotu v textovém poli, nebo větví a provést různé testovací akce na základě hodnoty v poli.  
  
   Můžete přidat více programové testy uživatelského rozhraní a více objekty mapování uživatelského rozhraní a soubory, aby usnadnil testování rozsáhlé aplikace. Další informace najdete v tématu [testování rozsáhlé aplikace s více mapami uživatelského rozhraní](../test/testing-a-large-application-with-multiple-ui-maps.md).  
  
  Další informace o generovaný kód, naleznete v tématu [anatomie programového testu UI](../test/anatomy-of-a-coded-ui-test.md).  
  
###  <a name="actions"></a> Kódování akce ovládacího prvku uživatelského rozhraní a vlastnosti  
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
  
##### <a name="to-get-or-set-properties-from-ui-test-controls-directly"></a>Pro získání nebo nastavení vlastnosti přímo z ovládacích prvků uživatelského rozhraní testu  
  
-   Pomocí ovládacích prvků, které jsou odvozeny z T:Microsoft.VisualStudio.TestTools.UITesting.UITestControl, jako je například T:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls.HtmlList nebo T: Microsoft.VisualStudio.TestTools.UITesting.WinControls.WinComboBox, můžete získat nebo nastavit jejich hodnoty vlastností přímo, následujícím způsobem:  
  
    ```  
    int i = myHtmlList.ItemCount;  
    myWinCheckBox.Checked = true;  
    ```  
  
##### <a name="to-get-properties-from-ui-test-controls"></a>Chcete-li získat vlastnosti z ovládacích prvků uživatelského rozhraní testu  
  
-   K získání hodnoty vlastnosti z ovládacího prvku použijte <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A>.  
  
-   Pokud chcete nastavit vlastnost ovládacího prvku, chcete-li získat, použijte příslušným řetězcem z `PropertyNames` třídy v každém ovládacím prvku jako parametr <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A>.  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A> vrátí odpovídající typ dat, ale to vrátit hodnotu je typovaná jako <xref:System.Object>. Vrácení <xref:System.Object> musíte přetypovat jako odpovídajícího typu.  
  
     Příklad:  
  
     `int i = (int)GetProperty(myHtmlList.PropertyNames.ItemCount);`  
  
##### <a name="to-set-properties-for-ui-test-controls"></a>Chcete-li nastavit vlastnosti pro test uživatelského rozhraní ovládacích prvků  
  
-   Chcete-li nastavit vlastnost v ovládacím prvku, použijte <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A>.  
  
-   Chcete-li určit vlastnost ovládacího prvku, chcete-li nastavit, použijte příslušným řetězcem z `PropertyNames` třídu jako první parametr <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A>, s hodnotou vlastnosti jako druhý parametr.  
  
     Příklad:  
  
     `SetProperty(myWinCheckBox.PropertyNames.Checked, true);`  
  
###  <a name="debugging"></a> Ladění  
 Programové testy uživatelského rozhraní pomocí protokolů z programových testů uživatelského rozhraní můžete analyzovat. Programového uživatelského rozhraní testu protokoly filtr a záznam, který běží důležité informace o programového testu UI. Formát protokolů umožňuje ladit problémy rychle. Další informace najdete v tématu [analýza programových testů pomocí programového uživatelského rozhraní protokolů testů](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md).  
  
##  <a name="VerifyCodeUsingCUITWhatsNext"></a> Co se chystá?  
 **Další možností pro spouštění programových testů UI:** spustit programové testy UI přímo ze sady Visual Studio, jak je popsáno výše v tomto tématu. Kromě toho můžete spustit automatizované testy uživatelského rozhraní z [!INCLUDE[TCMext](../includes/tcmext-md.md)], nebo z [!INCLUDE[esprbuild](../includes/esprbuild-md.md)]. Pokud jsou automatizované programové testy UI, mají komunikovat s plochou, když spustíte, je oproti jiným automatizovaným testům.  
  
- [Postupy: spuštění testů ze sady Microsoft Visual Studio](http://msdn.microsoft.com/library/1a1207a9-2a33-4a1e-a1e3-ddf0181b1046)  
  
- [Spuštění automatických testů v nástroji Microsoft Test Manager](http://msdn.microsoft.com/en-us/0632f265-63fe-4859-a413-9bb934c66835)  
  
- [Postupy: Konfigurace a spuštění naplánovaných testů po sestavení aplikace](http://msdn.microsoft.com/en-us/32acfeb1-b1aa-4afb-8cfe-cc209e6183fd)  
  
- [Spuštění testů v procesu sestavení](http://msdn.microsoft.com/library/d05743a1-c5cf-447e-bed9-bed3cb595e38)  
  
- [Spouštění automatizovaných testů z příkazového řádku](http://msdn.microsoft.com/library/f18179c6-b688-4e41-9898-8aca130c4fc3)  
  
- [Postupy: nastavení testovacího agenta pro spouštění testů komunikujících s plochou](~/E:/Repos/visualstudio-docs-pr/docs/test/how-to-set-up-your-test-agent-to-run-tests-that-interact-with-the-desktop.md)  
  
- [&#91;Vyřazeno&#93; pomocí programových testů uživatelského rozhraní v zátěžových testech](http://msdn.microsoft.com/library/704339ff-7da7-4d5f-acb3-c3b23f4acb43)  
  
  **Přidání podpory pro vlastní ovládací prvky:** programového uživatelského rozhraní testovací rozhraní nepodporuje všechna možná uživatelská rozhraní a nemusí podporovat uživatelské rozhraní, které chcete testovat. Například nelze okamžitě vytvořit programový test UI uživatelského rozhraní pro [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)]. Můžete však vytvořit rozšíření programového uživatelského rozhraní testování rozhraní, která bude podporovat vlastní ovládací prvek.  
  
- [Povolení programového testování uživatelského rozhraní pro vaše ovládací prvky](../test/enable-coded-ui-testing-of-your-controls.md)  
  
- [Rozšiřování programových testů UI a záznamů akcí k podpoře Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)  
  
  Programové testy uživatelského rozhraní se často používají k automatizaci ručních testů. Další informace najdete v tématu [testování pro nepřetržité dodávky s Visual Studio 2012 – kapitola 5: automatizace systémových testů](http://go.microsoft.com/fwlink/?LinkID=255196). Další informace o ruční testy, naleznete v tématu [ &#91;vyřazeno&#93; vytváření ručních testovacích případů pomocí nástroje Microsoft Test Manager](http://msdn.microsoft.com/library/9989e184-c8e4-444b-998d-a1a5ec94461e). Další informace o automatizované systémové testy, naleznete v tématu [vytváření automatizovaných testů pomocí nástroje Microsoft Test Manager](http://msdn.microsoft.com/en-us/7b5075ee-ddfe-411d-b1d4-94283550a5d0).  
  
## <a name="external-resources"></a>Externí zdroje  
  
### <a name="guidance"></a>Doprovodné materiály  
 [Testování pro nepřetržité dodávky s Visual Studio 2012 – kapitola 2: testování částí: testování uvnitř](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
 [Testování pro nepřetržité dodávky s Visual Studio 2012 – kapitola 5: automatizace systémových testů](http://go.microsoft.com/fwlink/?LinkID=255196)  
  
### <a name="faq"></a>Nejčastější dotazy  
 [Programové testy UI – nejčastější dotazy – 1](http://go.microsoft.com/fwlink/?LinkID=230576)  
  
 [Programové testy UI – nejčastější dotazy -2](http://go.microsoft.com/fwlink/?LinkID=230578)  
  
### <a name="forum"></a>Fórum  
 [Visual Studio automatické testování uživatelského rozhraní (včetně CodedUI)](http://go.microsoft.com/fwlink/?LinkID=224497)  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>   
 [Zlepšení kvality kódu](http://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)   
 [Návod: Vytváření, úpravy a údržba programového testu UI](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)   
 [Anatomie programového testu UI](../test/anatomy-of-a-coded-ui-test.md)   
 [Osvědčené postupy pro programové testy UI](../test/best-practices-for-coded-ui-tests.md)   
 [Testování rozsáhlé aplikace s více mapami uživatelského rozhraní](../test/testing-a-large-application-with-multiple-ui-maps.md)   
 [Úpravy programových testů uživatelského rozhraní pomocí editoru testů programového uživatelského rozhraní](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)   
 [Podporované konfigurace a platformy pro programové testy uživatelského rozhraní a zaznamenávání akcí](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)   
 [Upgrade programových testů UI z produktu Visual Studio 2010](../test/upgrading-coded-ui-tests-from-visual-studio-2010.md)   
 [Generování programového testu UI ze stávajícího záznamu akcí](http://msdn.microsoft.com/library/56736963-9027-493b-b5c4-2d4e86d1d497)



