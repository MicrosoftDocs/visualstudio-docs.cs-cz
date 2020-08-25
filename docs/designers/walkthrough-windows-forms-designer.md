---
title: Kurz Návrhář formulářů
ms.date: 08/09/2019
ms.topic: tutorial
helpviewer_keywords:
- Windows Forms Designer, get started
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 831e0216bcecff2e9ac6551184ddbfda56a4b525
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88801292"
---
# <a name="tutorial-get-started-with-windows-forms-designer"></a>Kurz: Začínáme s Návrhář formulářů

Návrhář formulářů poskytuje mnoho nástrojů pro sestavování aplikací model Windows Forms. Tento článek ukazuje, jak vytvořit aplikaci pomocí různých nástrojů, které poskytuje návrhář, včetně následujících úloh:

- Uspořádejte ovládací prvky pomocí zarovnávacím čárám.
- Provádění úloh návrháře pomocí inteligentních značek.
- Nastavte okraje a odsazení ovládacích prvků.
- Uspořádejte ovládací prvky pomocí <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.
- Rozdělte rozložení ovládacího prvku pomocí <xref:System.Windows.Forms.SplitContainer> ovládacího prvku.
- Navigace v rozložení pomocí okna Osnova dokumentu.
- Umístěte ovládací prvky na zobrazení velikost a informace o poloze.
- Nastavte hodnoty vlastností pomocí okno Vlastnosti.

Až budete hotovi, budete mít vlastní ovládací prvek, který je sestaven pomocí mnoha funkcí rozložení dostupných v Návrhář formulářů. Tento ovládací prvek implementuje uživatelské rozhraní (UI) pro jednoduchou kalkulačku. Následující obrázek znázorňuje obecné rozložení ovládacího prvku kalkulačka:

![Uživatelské rozhraní kalkulačky Průvodce Touring](media/calculator-ui.gif)

## <a name="create-the-custom-control-project"></a>Vytvoření projektu vlastního ovládacího prvku

Prvním krokem je vytvoření projektu ovládacího prvku DemoCalculator.

1. Otevřete Visual Studio a vytvořte nový projekt **knihovny ovládacích prvků model Windows Forms** . Pojmenujte projekt **DemoCalculatorLib**.

   ::: moniker range=">=vs-2019"

   ![Šablona knihovny ovládacích prvků model Windows Forms v aplikaci Visual Studio 2019](media/windows-forms-control-library-template.png)

   ::: moniker-end

2. Chcete-li přejmenovat soubor, v **Průzkumník řešení**klikněte pravým tlačítkem myši na **UserControl1. vb** nebo **UserControl1.cs**, vyberte položku **Přejmenovat**a změňte název souboru na DemoCalculator. vb nebo DemoCalculator.cs. Pokud se zobrazí dotaz, zda chcete přejmenovat všechny odkazy na prvek kódu "UserControl1", vyberte možnost **Ano** .

Návrhář formulářů zobrazuje plochu návrháře pro ovládací prvek DemoCalculator. V tomto zobrazení můžete graficky navrhovat vzhled ovládacího prvku výběrem ovládacích prvků a komponent z panelu nástrojů a jejich umístěním na plochu návrháře. Další informace o vlastních ovládacích prvcích naleznete v tématu [odrůdy vlastních ovládacích prvků](/dotnet/framework/winforms/controls/varieties-of-custom-controls).

## <a name="design-the-control-layout"></a>Návrh rozložení ovládacího prvku

Ovládací prvek DemoCalculator obsahuje několik ovládacích prvků model Windows Forms. V tomto postupu uspořádáte ovládací prvky pomocí Návrhář formulářů.

1. V Návrhář formulářů změňte ovládací prvek DemoCalculator na větší velikost tím, že vyberete úchyt pro změnu velikosti v pravém dolním rohu a přetáhnete ho dolů a doprava. V pravém dolním rohu sady Visual Studio Najděte informace o velikosti a umístění ovládacích prvků. Nastavte velikost ovládacího prvku na Width 500 a Height 400. při změně velikosti ovládacího prvku Sledujte informace o velikosti.

2. V **sadě nástrojů**vyberte uzel **kontejnery** a otevřete jej. Vyberte ovládací prvek **SplitContainer** a přetáhněte ho na plochu návrháře.

   `SplitContainer`Je umístěn na návrhové ploše ovládacího prvku DemoCalculator.

    > [!TIP]
    > `SplitContainer`Ovládací prvek přizpůsobí velikost ovládacího prvku DemoCalculator. Pokud chcete zobrazit nastavení vlastností ovládacího prvku, podívejte se na okno **vlastnosti** `SplitContainer` . Vyhledejte <xref:System.Windows.Forms.SplitContainer.Dock%2A> vlastnost. Jeho hodnota je [Vlastnost DockStyle. Fill](xref:System.Windows.Forms.DockStyle.Fill), což znamená, že `SplitContainer` ovládací prvek bude vždycky měnit velikost sebe sama na hranice ovládacího prvku DemoCalculator. Chcete-li toto chování ověřit, změňte velikost ovládacího prvku DemoCalculator.

3. V okně **vlastnosti** změňte hodnotu <xref:System.Windows.Forms.SplitContainer.Dock%2A> vlastnosti na `None` .

    `SplitContainer`Ovládací prvek se zmenší na jeho výchozí velikost a již nedodržuje velikost ovládacího prvku DemoCalculator.

4. Vyberte glyf inteligentních značek ( ![ glyf inteligentních značek ](media/smart-tag-glyph.gif) ) v pravém horním rohu `SplitContainer` ovládacího prvku. Vyberte **Dock v nadřazeném kontejneru** a nastavte `Dock` vlastnost na `Fill` .

    `SplitContainer`Ovládací prvek je ukotven na hranice ovládacího prvku DemoCalculator.

    > [!NOTE]
    > Několik ovládacích prvků nabízí inteligentní značky pro usnadnění návrhu. Další informace najdete v tématu [Návod: provádění běžných úloh pomocí inteligentních značek v ovládacích prvcích model Windows Forms](/dotnet/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls).

5. Vyberte svislé ohraničení mezi panely a přetáhněte je napravo, aby se většina místa v levém panelu vybrala na maximum.

    `SplitContainer`Rozdělí ovládací prvek DemoCalculator na dva panely s pohyblivým ohraničením, které ho odděluje. Panel na levé straně bude obsahovat tlačítka a zobrazení kalkulačky a panel na pravé straně zobrazí záznam aritmetických operací provedených uživatelem.

6. V okně **vlastnosti** změňte hodnotu `BorderStyle` vlastnosti na `Fixed3D` .

7. V **sadě nástrojů**vyberte uzel **běžné ovládací prvky** a otevřete jej. Vyberte `ListView` ovládací prvek a přetáhněte ho do pravého panelu `SplitContainer` ovládacího prvku.

8. Vyberte `ListView` glyf inteligentních značek ovládacího prvku. Na panelu inteligentních značek změňte `View` nastavení na `Details` .

9. Na panelu inteligentních značek vyberte **Upravit sloupce**.

   Otevře se dialogové okno **Editor kolekce ColumnHeader** .

10. V dialogovém okně **Editor kolekce ColumnHeader** vyberte **Přidat** a přidejte do `ListView` ovládacího prvku sloupec. Změňte hodnotu `Text` vlastnosti sloupce na **history**. Vyberte **OK** a vytvořte sloupec.

11. Na panelu inteligentních značek vyberte **ukotvit v nadřazeném kontejneru**a pak výběrem glyfu inteligentních značek zavřete panel inteligentních značek.

12. Z **panelu nástrojů**uzlu **kontejnerů** přetáhněte `TableLayoutPanel` ovládací prvek do levého panelu `SplitContainer` ovládacího prvku.

    `TableLayoutPanel`Ovládací prvek se zobrazí na návrhové ploše s otevřeným panelem inteligentních značek. `TableLayoutPanel`Ovládací prvek uspořádá své podřízené ovládací prvky v mřížce. `TableLayoutPanel`Ovládací prvek bude obsahovat zobrazení a tlačítka ovládacího prvku DemoCalculator. Další informace naleznete v tématu [Návod: uspořádání ovládacích prvků pomocí kontejneru TableLayoutPanel](/dotnet/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel).

13. Vyberte možnost **Upravit řádky a sloupce** na panelu inteligentních značek.

    Otevře se dialogové okno **styly sloupců a řádků** .

14. Vyberte tlačítko **Přidat** , dokud se nezobrazí pět sloupců. Vyberte všechny pět sloupců a v poli **typ velikosti** vyberte **procenta** . Nastavte hodnotu **procenta** na **20**. Tím se u každého sloupce nastaví stejná šířka.

15. V části **Zobrazit**vyberte **řádky**.

16. Vyberte **Přidat** do zobrazení pěti řádků. Vyberte možnost všechny pět řádků a v poli **typ velikosti** vyberte **procento** . Nastavte hodnotu **procenta** na **20**. Tím se nastaví každý řádek na stejnou výšku.

17. Vyberte **OK** a potvrďte provedené změny a potom vyberte glyf inteligentních značek, který panel inteligentních značek zavře.

18. V okně **vlastnosti** změňte hodnotu `Dock` vlastnosti na `Fill` .

## <a name="populate-the-control"></a>Naplnit ovládací prvek

Nyní, když je nastaveno rozložení ovládacího prvku, lze naplnit ovládací prvek DemoCalculator tlačítky a zobrazením.

1. V **panelu nástrojů**vyberte `TextBox` ikonu ovládacího prvku.

   `TextBox`Ovládací prvek je umístěn v první buňce `TableLayoutPanel` ovládacího prvku.

2. V okně **vlastnosti** změňte hodnotu `TextBox` vlastnosti jeho ColumnSpan ovládacího prvku na hodnotu **5**.

   `TextBox`Ovládací prvek se přesune na pozici, která je zarovnána na střed svého řádku.

3. Změňte hodnotu `TextBox` vlastnosti ovládacího prvku `Anchor` na `Left` , `Right` .

   `TextBox`Ovládací prvek se rozbalí vodorovně a rozdělí na všechny pět sloupců.

4. Změňte hodnotu `TextBox` vlastnosti ovládacího prvku `TextAlign` na `Right` .

5. V okně **vlastnosti** rozbalte `Font` uzel vlastnost. Nastavte `Size` na hodnotu **14**a nastavte `Bold` na **hodnotu true** pro `TextBox` ovládací prvek.

6. Vyberte `TableLayoutPanel` ovládací prvek.

7. V **panelu nástrojů**vyberte `Button` ikonu.

   `Button`Ovládací prvek je umístěn v další otevřené buňce `TableLayoutPanel` ovládacího prvku.

8. V **sadě nástrojů**vyberte `Button` ikonu čtyřikrát a naplňte druhý řádek `TableLayoutPanel` ovládacího prvku.

9. Vyberte všechna pět `Button` ovládacích prvků tak, že je vyberete a podržíte klávesu **SHIFT** . Stisknutím **kombinace kláves CTRL** + **C** zkopírujte `Button` ovládací prvky do schránky.

10. Stisknutím **kombinace kláves CTRL** + **V** třikrát vložte kopie `Button` ovládacích prvků do zbývajících řádků `TableLayoutPanel` ovládacího prvku.

11. Vyberte všechny 20 `Button` ovládacích prvků tak, že je vyberete a podržíte klávesu **SHIFT** .

12. V okně **vlastnosti** změňte hodnotu `Dock` vlastnosti na `Fill` .

    Všechny `Button` ovládací prvky Dock, aby vyplnily buňky, které obsahují.

13. V okně **vlastnosti** rozbalte `Margin` uzel vlastnost. Nastavte hodnotu `All` na **5**.

    Všechny `Button` ovládací prvky mají menší velikost pro vytvoření většího okraje mezi nimi.

14. Vyberte **button10** a **Button20**a pak stiskněte **Delete** pro jejich odebrání z rozložení.

15. Vyberte **Button5** a **button15**a pak změňte hodnotu `RowSpan` vlastnosti na **2**. Toto jsou tlačítka **clear** a **=** pro ovládací prvek DemoCalculator.

## <a name="use-the-document-outline-window"></a>Použití okna Osnova dokumentu

Když se ovládací prvek nebo formulář naplní několika ovládacími prvky, může být jednodušší procházet rozložení pomocí okna Osnova dokumentu.

1. Na panelu nabídek vyberte možnost **Zobrazit**  >  **ostatní**  >  **Osnova dokumentu**Windows.

   Okno Osnova dokumentu zobrazuje stromové zobrazení ovládacího prvku DemoCalculator a jeho ovládacích prvků na jeho prvku. Ovládací prvky kontejneru, jako je `SplitContainer` například zobrazit jejich podřízené ovládací prvky jako poduzly ve stromové struktuře. Můžete také přejmenovat ovládací prvky na místě pomocí okna Osnova dokumentu.

2. V okně **Osnova dokumentu** klikněte pravým tlačítkem myši na možnost **Button1**a pak vyberte možnost **Přejmenovat**. Změňte jeho název na sevenButton.

3. Pomocí okna **Osnova dokumentu** přejmenujte `Button` ovládací prvky z názvu vygenerovaného návrhářem na název výroby podle následujícího seznamu:

   - Button1 na **sevenButton**

   - Button2 do **eightButton**

   - Button3 na **nineButton**

   - Button4 na **divisionButton**

   - Button5 na **clearButton**

   - Button6 na **fourButton**

   - button7 na **fiveButton**

   - button8 na **sixButton**

   - button9 na **multiplicationButton**

   - button11 na **oneButton**

   - button12 na **twoButton**

   - button13 na **threeButton**

   - button14 na **subtractionButton**

   - button15 na **equalsButton**

   - button16 na **zeroButton**

   - button17 na **changeSignButton**

   - button18 na **decimalButton**

   - button19 na **additionButton**

4. Pomocí okna **Osnova** a **vlastnosti** dokumentu změňte `Text` hodnotu vlastnosti pro každý `Button` název ovládacího prvku podle následujícího seznamu:

   - Změňte vlastnost text ovládacího prvku sevenButton na hodnotu **7** .

   - Změňte vlastnost text ovládacího prvku eightButton na hodnotu **8** .

   - Změnit vlastnost text ovládacího prvku nineButton na **9**

   - Změnit vlastnost text ovládacího prvku divisionButton na **/** (lomítko)

   - Změňte vlastnost text ovládacího prvku clearButton na **clear** .

   - Změňte vlastnost text ovládacího prvku fourButton na **4** .

   - Změňte vlastnost text ovládacího prvku fiveButton na **5** .

   - Změňte vlastnost text ovládacího prvku sixButton na **6** .

   - Změnit vlastnost text ovládacího prvku multiplicationButton na **\*** (hvězdičku)

   - Změňte vlastnost text ovládacího prvku oneButton na hodnotu **1** .

   - Změňte vlastnost text ovládacího prvku twoButton na **2** .

   - Změnit vlastnost text ovládacího prvku threeButton na **3**

   - Změnit vlastnost text ovládacího prvku subtractionButton na **-** (spojovník)

   - Změnit vlastnost text ovládacího prvku equalsButton na **=** (symbol rovná se)

   - Změňte vlastnost text ovládacího prvku zeroButton na **hodnotu 0** .

   - Změňte vlastnost text ovládacího prvku changeSignButton na **+/-**

   - Změňte vlastnost text ovládacího prvku decimalButton na **.** (tečka)

   - Změnit vlastnost text ovládacího prvku additionButton na **+** (znaménko plus)

5. Na návrhové ploše vyberte všechny `Button` ovládací prvky tak, že je vyberete, a přitom podržíte klávesu **SHIFT** .

6. V okně **vlastnosti** rozbalte `Font` uzel vlastnost. Nastavte `Size` na hodnotu **14**a `Bold` pro všechny ovládací prvky nastavte na **hodnotu true** `Button` .

Tím se dokončí návrh ovládacího prvku DemoCalculator. To vše zůstává k poskytnutí logiky kalkulačky.

## <a name="implement-event-handlers"></a>Implementace obslužných rutin událostí

Tlačítka na ovládacím prvku DemoCalculator mají obslužné rutiny událostí, které lze použít k implementaci mnohem logiky kalkulačky. Návrhář formulářů umožňuje implementovat zástupné procedury všech obslužných rutin událostí pro všechna tlačítka jediným výběrem.

1. Na návrhové ploše vyberte všechny `Button` ovládací prvky tak, že je vyberete, a přitom podržíte klávesu **SHIFT** .

2. Vyberte jeden z `Button` ovládacích prvků.

   Editor kódu se otevře v obslužných rutinách událostí generovaných návrhářem.

## <a name="test-the-control"></a>Testování ovládacího prvku

Vzhledem k tomu, že ovládací prvek DemoCalculator dědí z <xref:System.Windows.Forms.UserControl> třídy, můžete otestovat jeho chování pomocí **kontejneru testu UserControl**. Další informace naleznete v tématu [How to: test runtime Behavior prvku UserControl](/dotnet/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol).

1. Stisknutím klávesy **F5** Sestavte a spusťte ovládací prvek DemoCalculator v **kontejneru testu UserControl**.

2. Vyberte ohraničení mezi `SplitContainer` panely a přetáhněte je doleva a doprava. `TableLayoutPanel`A všechny jeho podřízené ovládací prvky mění velikost sebe sama tak, aby se vešly do dostupného místa.

3. Po dokončení testování ovládacího prvku vyberte možnost **Zavřít**.

## <a name="use-the-control-on-a-form"></a>Použití ovládacího prvku na formuláři

Ovládací prvek DemoCalculator lze použít v jiných složených ovládacích prvcích nebo na formuláři. Následující postup popisuje, jak ho používat.

### <a name="create-the-project"></a>Vytvoření projektu

Prvním krokem je vytvoření projektu aplikace. Pomocí tohoto projektu sestavíte aplikaci, která zobrazuje váš vlastní ovládací prvek.

1. Vytvořte nový projekt **aplikace model Windows Forms** a pojmenujte ho **DemoCalculatorTest**.

2. V **Průzkumník řešení**klikněte pravým tlačítkem na projekt **DemoCalculatorTest** a pak vyberte **Přidat odkaz** . tím otevřete dialogové okno **Přidat odkaz** .

3. Pokud chcete přidat odkaz na testovací projekt, klikněte na kartu **projekty** a potom vyberte projekt DemoCalculatorLib.

4. V **Průzkumník řešení**klikněte pravým tlačítkem na **DemoCalculatorTest**a pak vyberte **nastavit jako spouštěný projekt**.

5. V Návrhář formulářů zvětšete velikost formuláře na přibližně **700 x 500**.

### <a name="use-the-control-in-the-forms-layout"></a>Použití ovládacího prvku v rozložení formuláře

Chcete-li použít ovládací prvek DemoCalculator v aplikaci, je nutné jej umístit na formulář.

1. V **sadě nástrojů**rozbalte uzel **součásti DemoCalculatorLib** .

2. Přetáhněte ovládací prvek **DemoCalculator** z **panelu nástrojů** do formuláře. Přesuňte ovládací prvek do levého horního rohu formuláře. Když je ovládací prvek blízko ohraničení formuláře, zobrazí se *zarovnávacím čárám* . Zarovnávacím čárám Určuje vzdálenost `Padding` vlastnosti formuláře a vlastnosti ovládacího prvku `Margin` . Umístěte ovládací prvek na místo označeného zarovnávacím čárám.

   Další informace naleznete v tématu [Návod: uspořádání ovládacích prvků pomocí zarovnávacím čárám](/dotnet/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines).

3. Přetáhněte `Button` ovládací prvek z **panelu nástrojů** a přetáhněte ho do formuláře.

4. Přesuňte `Button` ovládací prvek kolem ovládacího prvku DemoCalculator a sledujte, kde se zobrazuje zarovnávacím čárám. Pomocí této funkce můžete zarovnat ovládací prvky přesně a snadno. `Button`Po dokončení tento ovládací prvek odstraňte.

5. Klikněte pravým tlačítkem myši na ovládací prvek DemoCalculator a pak vyberte **vlastnosti**.

6. Změňte hodnotu `Dock` vlastnosti na `Fill` .

7. Vyberte formulář a potom rozbalte `Padding` uzel vlastnost. Změňte hodnotu **vše** na **20**.

   Velikost ovládacího prvku DemoCalculator je zmenšena tak, aby odpovídala nové `Padding` hodnotě formuláře.

8. Změňte velikost formuláře přetažením různých úchytů pro změnu velikosti na různé pozice. Sledujte, jak se velikost ovládacího prvku DemoCalculator přizpůsobí.

## <a name="next-steps"></a>Další kroky

Tento článek ukazuje, jak vytvořit uživatelské rozhraní pro jednoduchou kalkulačku. Chcete-li pokračovat, můžete svou funkčnost nasadit pomocí logiky kalkulačky a pak [aplikaci publikovat pomocí technologie ClickOnce](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md). Nebo můžete pokračovat v jiném kurzu, kde [vytvoříte prohlížeč obrázků pomocí model Windows Forms](../ide/tutorial-1-create-a-picture-viewer.md).

## <a name="see-also"></a>Viz také

- [Windows Forms – ovládací prvky](/dotnet/framework/winforms/controls/)
- [Usnadnění pro model Windows Forms ovládací prvky](/dotnet/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form)
- [Publikování pomocí technologie ClickOnce](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
