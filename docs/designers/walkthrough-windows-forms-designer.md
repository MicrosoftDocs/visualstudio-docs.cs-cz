---
title: Kurz Návrhář formulářů
ms.date: 08/09/2019
ms.topic: conceptual
helpviewer_keywords:
- Windows Forms Designer, get started
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 419e5ddb5d915307130a6fdadd795ce5b3236033
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72634135"
---
# <a name="walkthrough-get-started-with-windows-forms-designer"></a>Návod: Začínáme s Návrhář formulářů

Návrhář formulářů poskytuje mnoho nástrojů pro sestavování aplikací model Windows Forms. Tento článek ukazuje, jak vytvořit aplikaci pomocí různých nástrojů, které poskytuje návrhář, včetně následujících úloh:

- Uspořádejte ovládací prvky pomocí zarovnávacím čárám.
- Provádění úloh návrháře pomocí inteligentních značek.
- Nastavte okraje a odsazení ovládacích prvků.
- Uspořádejte ovládací prvky pomocí ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel>.
- Rozdělte rozložení ovládacího prvku pomocí ovládacího prvku <xref:System.Windows.Forms.SplitContainer>.
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

   @No__t_0 je umístěn na návrhové ploše ovládacího prvku DemoCalculator.

    > [!TIP]
    > Ovládací prvek `SplitContainer` přizpůsobí velikost ovládacího prvku DemoCalculator. Chcete-li zobrazit nastavení vlastností ovládacího prvku `SplitContainer`, podívejte se do okna **vlastnosti** . Vyhledejte vlastnost <xref:System.Windows.Forms.SplitContainer.Dock%2A>. Jeho hodnota je [Vlastnost DockStyle. Fill](xref:System.Windows.Forms.DockStyle.Fill), což znamená, že ovládací prvek `SplitContainer` vždy změní velikost sebe sama na hranice ovládacího prvku DemoCalculator. Chcete-li toto chování ověřit, změňte velikost ovládacího prvku DemoCalculator.

3. V okně **vlastnosti** změňte hodnotu vlastnosti <xref:System.Windows.Forms.SplitContainer.Dock%2A> na `None`.

    Ovládací prvek `SplitContainer` se zmenší na jeho výchozí velikost a již nedodržuje velikost ovládacího prvku DemoCalculator.

4. Vyberte glyf inteligentních značek (![Smart glyf značek ](media/smart-tag-glyph.gif)) v pravém horním rohu ovládacího prvku `SplitContainer`. Vyberte **Dock v nadřazeném kontejneru** a nastavte vlastnost `Dock` na `Fill`.

    Ovládací prvek `SplitContainer` ukotven na hranice ovládacího prvku DemoCalculator.

    > [!NOTE]
    > Několik ovládacích prvků nabízí inteligentní značky pro usnadnění návrhu. Další informace najdete v tématu [Návod: provádění běžných úloh pomocí inteligentních značek v ovládacích prvcích model Windows Forms](/dotnet/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls).

5. Vyberte svislé ohraničení mezi panely a přetáhněte je napravo, aby se většina místa v levém panelu vybrala na maximum.

    @No__t_0 rozdělí ovládací prvek DemoCalculator na dva panely s pohyblivým ohraničením, které ho odděluje. Panel na levé straně bude obsahovat tlačítka a zobrazení kalkulačky a panel na pravé straně zobrazí záznam aritmetických operací provedených uživatelem.

6. V okně **vlastnosti** změňte hodnotu vlastnosti `BorderStyle` na `Fixed3D`.

7. V **sadě nástrojů**vyberte uzel **běžné ovládací prvky** a otevřete jej. Vyberte ovládací prvek `ListView` a přetáhněte ho do pravého panelu ovládacího prvku `SplitContainer`.

8. Vyberte glyf inteligentních značek `ListView` ovládacího prvku. Na panelu inteligentních značek změňte nastavení `View` na `Details`.

9. Na panelu inteligentních značek vyberte **Upravit sloupce**.

   Otevře se dialogové okno **Editor kolekce ColumnHeader** .

10. V dialogovém okně **Editor kolekce ColumnHeader** vyberte **Přidat** a přidejte sloupec do ovládacího prvku `ListView`. Změňte hodnotu vlastnosti `Text` sloupce na **history**. Vyberte **OK** a vytvořte sloupec.

11. Na panelu inteligentních značek vyberte **ukotvit v nadřazeném kontejneru**a pak výběrem glyfu inteligentních značek zavřete panel inteligentních značek.

12. Z **panelu nástrojů**uzlu **kontejnerů** přetáhněte ovládací prvek `TableLayoutPanel` do levého panelu ovládacího prvku `SplitContainer`.

    Ovládací prvek `TableLayoutPanel` se zobrazí na návrhové ploše s otevřeným panelem inteligentních značek. Ovládací prvek `TableLayoutPanel` uspořádá své podřízené ovládací prvky v mřížce. Ovládací prvek `TableLayoutPanel` bude obsahovat zobrazení a tlačítka ovládacího prvku DemoCalculator. Další informace naleznete v tématu [Návod: uspořádání ovládacích prvků pomocí kontejneru TableLayoutPanel](/dotnet/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel).

13. Vyberte možnost **Upravit řádky a sloupce** na panelu inteligentních značek.

    Otevře se dialogové okno **styly sloupců a řádků** .

14. Vyberte tlačítko **Přidat** , dokud se nezobrazí pět sloupců. Vyberte všechny pět sloupců a v poli **typ velikosti** vyberte **procenta** . Nastavte hodnotu **procenta** na **20**. Tím se u každého sloupce nastaví stejná šířka.

15. V části **Zobrazit**vyberte **řádky**.

16. Vyberte **Přidat** do zobrazení pěti řádků. Vyberte možnost všechny pět řádků a v poli **typ velikosti** vyberte **procento** . Nastavte hodnotu **procenta** na **20**. Tím se nastaví každý řádek na stejnou výšku.

17. Vyberte **OK** a potvrďte provedené změny a potom vyberte glyf inteligentních značek, který panel inteligentních značek zavře.

18. V okně **vlastnosti** změňte hodnotu vlastnosti `Dock` na `Fill`.

## <a name="populate-the-control"></a>Naplnit ovládací prvek

Nyní, když je nastaveno rozložení ovládacího prvku, lze naplnit ovládací prvek DemoCalculator tlačítky a zobrazením.

1. V **sadě nástrojů**poklikejte na ikonu ovládacího prvku `TextBox`.

   Do první buňky ovládacího prvku `TableLayoutPanel` je umístěn ovládací prvek `TextBox`.

2. V okně **vlastnosti** změňte hodnotu vlastnosti jeho ColumnSpan ovládacího prvku `TextBox` na **5**.

   Ovládací prvek `TextBox` se přesune na pozici, která je zarovnána na střed svého řádku.

3. Změňte hodnotu vlastnosti `Anchor` ovládacího prvku `TextBox` na `Left`, `Right`.

   Ovládací prvek `TextBox` se rozbalí vodorovně a rozdělí na všechna pět sloupců.

4. Změňte hodnotu vlastnosti `TextAlign` ovládacího prvku `TextBox` na `Right`.

5. V okně **vlastnosti** rozbalte uzel vlastností `Font`. Nastavte `Size` na hodnotu **14**a pro ovládací prvek `TextBox` nastavte `Bold` na **true** .

6. Vyberte ovládací prvek `TableLayoutPanel`.

7. Na **panelu nástrojů**dvakrát klikněte na ikonu `Button`.

   @No__t_0 ovládací prvek je umístěn v další otevřené buňce ovládacího prvku `TableLayoutPanel`.

8. V **soupravě nástrojů**dvakrát klikněte na ikonu `Button` a naplňte druhý řádek ovládacího prvku `TableLayoutPanel`.

9. Vyberte všechna pět `Button` ovládacích prvků tak, že je vyberete a podržíte klávesu **SHIFT** . Stisknutím **kombinace kláves Ctrl** +**C** zkopírujte ovládací prvky `Button` do schránky.

10. Stisknutím **kombinace kláves Ctrl** +**V** třikrát vložte kopie `Button` ovládacích prvků do zbývajících řádků ovládacího prvku `TableLayoutPanel`.

11. Vyberte všechny 20 `Button` ovládacích prvků tím, že je vyberete a podržíte klávesu **SHIFT** .

12. V okně **vlastnosti** změňte hodnotu vlastnosti `Dock` na `Fill`.

    Všechny ovládací prvky `Button` ukotveny, aby vyplnily buňky, které obsahují.

13. V okně **vlastnosti** rozbalte uzel vlastností `Margin`. Nastavte hodnotu `All` na **5**.

    Všechny ovládací prvky `Button` mají menší velikost pro vytvoření většího okraje mezi nimi.

14. Vyberte **button10** a **Button20**a pak stiskněte **Delete** pro jejich odebrání z rozložení.

15. Vyberte **Button5** a **button15**a pak změňte hodnotu vlastnosti `RowSpan` na **2**. Toto jsou tlačítka pro **vymazání** a **=** pro ovládací prvek DemoCalculator.

## <a name="use-the-document-outline-window"></a>Použití okna Osnova dokumentu

Když se ovládací prvek nebo formulář naplní několika ovládacími prvky, může být jednodušší procházet rozložení pomocí okna Osnova dokumentu.

1. Na panelu nabídek vyberte možnost **zobrazit**  >  další**osnova dokumentu** > **Windows** .

   Okno Osnova dokumentu zobrazuje stromové zobrazení ovládacího prvku DemoCalculator a jeho ovládacích prvků na jeho prvku. Ovládací prvky kontejneru jako `SplitContainer` zobrazují jejich podřízené ovládací prvky jako poduzly ve stromové struktuře. Můžete také přejmenovat ovládací prvky na místě pomocí okna Osnova dokumentu.

2. V okně **Osnova dokumentu** klepněte pravým tlačítkem myši na tlačítko **Button1**a pak vyberte možnost **Přejmenovat**. Změňte jeho název na sevenButton.

3. Pomocí okna **Osnova dokumentu** Přejmenujte ovládací prvky `Button` z názvu vygenerovaného návrhářem na název výroby podle následujícího seznamu:

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

4. Pomocí okna **Osnova** a **vlastnosti** dokumentu změňte hodnotu vlastnosti `Text` pro každý název ovládacího prvku `Button` podle následujícího seznamu:

   - Změňte vlastnost text ovládacího prvku sevenButton na hodnotu **7** .

   - Změňte vlastnost text ovládacího prvku eightButton na hodnotu **8** .

   - Změnit vlastnost text ovládacího prvku nineButton na **9**

   - Změňte vlastnost text ovládacího prvku divisionButton na **/** (lomítko).

   - Změňte vlastnost text ovládacího prvku clearButton na **clear** .

   - Změňte vlastnost text ovládacího prvku fourButton na **4** .

   - Změňte vlastnost text ovládacího prvku fiveButton na **5** .

   - Změňte vlastnost text ovládacího prvku sixButton na **6** .

   - Změnit vlastnost text ovládacího prvku multiplicationButton na **\*** (hvězdička)

   - Změňte vlastnost text ovládacího prvku oneButton na hodnotu **1** .

   - Změňte vlastnost text ovládacího prvku twoButton na **2** .

   - Změnit vlastnost text ovládacího prvku threeButton na **3**

   - Změnit vlastnost text ovládacího prvku subtractionButton na **-** (spojovník)

   - Změňte vlastnost text ovládacího prvku equalsButton na **=** (znaménko rovná se).

   - Změňte vlastnost text ovládacího prvku zeroButton na **hodnotu 0** .

   - Změňte vlastnost text ovládacího prvku changeSignButton na **+/-**

   - Změňte vlastnost text ovládacího prvku decimalButton na **.** hodin

   - Změnit vlastnost text ovládacího prvku additionButton na **+** (znaménko plus)

5. Na návrhové ploše vyberte všechny ovládací prvky `Button` tím, že je vyberete a podržíte klávesu **SHIFT** .

6. V okně **vlastnosti** rozbalte uzel vlastností `Font`. Nastavte `Size` na hodnotu **14**a pro všechny ovládací prvky `Button` nastavte `Bold` na **true** .

Tím se dokončí návrh ovládacího prvku DemoCalculator. To vše zůstává k poskytnutí logiky kalkulačky.

## <a name="implement-event-handlers"></a>Implementace obslužných rutin událostí

Tlačítka na ovládacím prvku DemoCalculator mají obslužné rutiny událostí, které lze použít k implementaci mnohem logiky kalkulačky. Návrhář formulářů umožňuje implementovat zástupné procedury všech obslužných rutin událostí pro všechna tlačítka jediným kliknutím.

1. Na návrhové ploše vyberte všechny ovládací prvky `Button` tím, že je vyberete a podržíte klávesu **SHIFT** .

2. Dvakrát klikněte na jeden z ovládacích prvků `Button`.

   Editor kódu se otevře v obslužných rutinách událostí generovaných návrhářem.

## <a name="test-the-control"></a>Testování ovládacího prvku

Vzhledem k tomu, že ovládací prvek DemoCalculator dědí z třídy <xref:System.Windows.Forms.UserControl>, můžete otestovat jeho chování pomocí **kontejneru testu UserControl**. Další informace naleznete v tématu [How to: test runtime Behavior prvku UserControl](/dotnet/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol).

1. Stisknutím klávesy **F5** Sestavte a spusťte ovládací prvek DemoCalculator v **kontejneru testu UserControl**.

2. Vyberte ohraničení mezi `SplitContainer` panely a přetáhněte je doleva a doprava. @No__t_0 a všechny jeho podřízené ovládací prvky mění velikost sebe sama tak, aby se vešly do dostupného místa.

3. Po dokončení testování ovládacího prvku vyberte možnost **Zavřít**.

## <a name="use-the-control-on-a-form"></a>Použití ovládacího prvku na formuláři

Ovládací prvek DemoCalculator lze použít v jiných složených ovládacích prvcích nebo na formuláři. Následující postup popisuje, jak ho používat.

### <a name="create-the-project"></a>Vytvoření projektu

Prvním krokem je vytvoření projektu aplikace. Pomocí tohoto projektu sestavíte aplikaci, která zobrazuje váš vlastní ovládací prvek.

1. Vytvořte nový projekt **aplikace model Windows Forms** a pojmenujte ho **DemoCalculatorTest**.

2. V **Průzkumník řešení**klikněte pravým tlačítkem na projekt **DemoCalculatorTest** a pak vyberte **Přidat odkaz** . tím otevřete dialogové okno **Přidat odkaz** .

3. Vyberte kartu **projekty** a potom poklikejte na projekt DemoCalculatorLib, abyste přidali odkaz na projekt testů.

4. V **Průzkumník řešení**klikněte pravým tlačítkem na **DemoCalculatorTest**a pak vyberte **nastavit jako spouštěný projekt**.

5. V Návrhář formulářů zvětšete velikost formuláře na přibližně **700 x 500**.

### <a name="use-the-control-in-the-forms-layout"></a>Použití ovládacího prvku v rozložení formuláře

Chcete-li použít ovládací prvek DemoCalculator v aplikaci, je nutné jej umístit na formulář.

1. V **sadě nástrojů**rozbalte uzel **součásti DemoCalculatorLib** .

2. Přetáhněte ovládací prvek **DemoCalculator** z **panelu nástrojů** do formuláře. Přesuňte ovládací prvek do levého horního rohu formuláře. Když je ovládací prvek blízko ohraničení formuláře, zobrazí se *zarovnávacím čárám* . Zarovnávacím čárám Určuje vzdálenost vlastnosti `Padding` formuláře a vlastnost `Margin` ovládacího prvku. Umístěte ovládací prvek na místo označeného zarovnávacím čárám.

   Další informace naleznete v tématu [Návod: uspořádání ovládacích prvků pomocí zarovnávacím čárám](/dotnet/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines).

3. Přetáhněte ovládací prvek `Button` z **panelu nástrojů** a přetáhněte ho do formuláře.

4. Přesuňte ovládací prvek `Button` kolem ovládacího prvku DemoCalculator a sledujte, kde se zarovnávacím čárám zobrazuje. Pomocí této funkce můžete zarovnat ovládací prvky přesně a snadno. Až skončíte, odstraňte ovládací prvek `Button`.

5. Pravým tlačítkem myši vyberte ovládací prvek DemoCalculator a pak vyberte **vlastnosti**.

6. Změňte hodnotu vlastnosti `Dock` na `Fill`.

7. Vyberte formulář a potom rozbalte uzel vlastností `Padding`. Změňte hodnotu **vše** na **20**.

   Velikost ovládacího prvku DemoCalculator je zmenšena tak, aby odpovídala nové hodnotě `Padding` formuláře.

8. Změňte velikost formuláře přetažením různých úchytů pro změnu velikosti na různé pozice. Sledujte, jak se velikost ovládacího prvku DemoCalculator přizpůsobí.

## <a name="next-steps"></a>Další kroky

Tento článek ukazuje, jak vytvořit uživatelské rozhraní pro jednoduchou kalkulačku. Chcete-li pokračovat, můžete svou funkčnost nasadit pomocí logiky kalkulačky a pak [aplikaci publikovat pomocí technologie ClickOnce](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md). Nebo můžete pokračovat v jiném kurzu, kde [vytvoříte prohlížeč obrázků pomocí model Windows Forms](../ide/tutorial-1-create-a-picture-viewer.md).

## <a name="see-also"></a>Viz také:

- [Ovládací prvky model Windows Forms](/dotnet/framework/winforms/controls/)
- [Usnadnění pro model Windows Forms ovládací prvky](/dotnet/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form)
- [Publikování pomocí technologie ClickOnce](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)