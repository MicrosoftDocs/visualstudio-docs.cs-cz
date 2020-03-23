---
title: Kurz návrháře formulářů Windows
ms.date: 08/09/2019
ms.topic: conceptual
helpviewer_keywords:
- Windows Forms Designer, get started
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 07526637f2d8083f37f55aa3da36bb01479db087
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589835"
---
# <a name="walkthrough-get-started-with-windows-forms-designer"></a>Návod: Začínáme s Návrhářem formulářů Windows

Návrhář formulářů systému Windows poskytuje mnoho nástrojů pro vytváření aplikací windows forms. Tento článek ukazuje, jak vytvořit aplikaci pomocí různých nástrojů poskytovaných návrhářem, včetně následujících úkolů:

- Uspořádejte ovládací prvky pomocí snaplines.
- S pomocí inteligentních značek dosávat úlohy návrháře.
- Nastavte okraje a odsazení ovládacích prvků.
- Uspořádejte <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvky pomocí ovládacího prvku.
- Rozdělení rozložení ovládacího prvku <xref:System.Windows.Forms.SplitContainer> pomocí ovládacího prvku.
- Procházení rozložení pomocí okna Osnova dokumentu
- Ovládací prvky umístěte pomocí zobrazení informací o velikosti a umístění.
- Nastavte hodnoty vlastností pomocí okna Vlastnosti.

Po dokončení budete mít vlastní ovládací prvek, který byl sestaven pomocí mnoha funkcí rozložení dostupných v Návrháři formulářů Windows. Tento ovládací prvek implementuje uživatelské rozhraní (UI) pro jednoduchou kalkulačku. Následující obrázek znázorňuje obecné rozložení ovládacího prvku kalkulačky:

![UI kalkulačky s průvodcem](media/calculator-ui.gif)

## <a name="create-the-custom-control-project"></a>Vytvoření vlastního řídicího projektu

Prvním krokem je vytvoření řídicího projektu DemoCalculator.

1. Otevřete Visual Studio a vytvořte nový projekt **knihovny Windows Forms Control Library.** Pojmenujte projekt **DemoCalculatorLib**.

   ::: moniker range=">=vs-2019"

   ![Šablona knihovny Windows Forms Control Library ve Visual Studiu 2019](media/windows-forms-control-library-template.png)

   ::: moniker-end

2. Chcete-li soubor přejmenovat, vyberte v **Průzkumníku řešení**vpravém výběru **UserControl1.vb** nebo **UserControl1.cs**vyberte **Přejmenovat**a změňte název souboru na DemoCalculator.vb nebo DemoCalculator.cs. Vyberte **Ano,** pokud budete dotázáni, zda chcete přejmenovat všechny odkazy na prvek kódu "UserControl1".

Návrhář formulářů systému Windows zobrazuje povrch návrháře pro ovládací prvek DemoCalculator. V tomto zobrazení můžete graficky navrhnout vzhled ovládacího prvku výběrem ovládacích prvků a součástí z panelu nástrojů a jejich umístěním na povrch návrháře. Další informace o vlastních ovládacích prvcích naleznete v [tématu Odrůdy vlastních ovládacích prvků](/dotnet/framework/winforms/controls/varieties-of-custom-controls).

## <a name="design-the-control-layout"></a>Návrh rozložení ovládacího prvku

Ovládací prvek DemoCalculator obsahuje několik ovládacích prvků windows forms. V tomto postupu uspořádáte ovládací prvky pomocí Návrháře formulářů systému Windows.

1. V Návrháři formulářů systému Windows změňte ovládací prvek DemoCalculator na větší velikost výběrem úchytu pro změnu velikosti v pravém dolním rohu a jeho přetažením dolů a doprava. V pravém dolním rohu sady Visual Studio najděte informace o velikosti a umístění ovládacích prvků. Nastavte velikost ovládacího prvku na šířku 500 a výšku 400 sledováním informací o velikosti při změně velikosti ovládacího prvku.

2. V **panelu nástrojů**vyberte uzel **Kontejnery,** který chcete otevřít. Vyberte ovládací prvek **SplitContainer** a přetáhněte jej na povrch návrháře.

   Je `SplitContainer` umístěn na povrchu návrháře ovládacího prvku DemoCalculator.

    > [!TIP]
    > Ovládací `SplitContainer` prvek velikosti sám přizpůsobit velikost DemoCalculator ovládacího prvku. Podívejte se na **okno Vlastnosti** zobrazíte nastavení vlastností ovládacího `SplitContainer` prvku. Najděte <xref:System.Windows.Forms.SplitContainer.Dock%2A> nemovitost. Jeho hodnota je [DockStyle.Fill](xref:System.Windows.Forms.DockStyle.Fill) `SplitContainer` , což znamená, že ovládací prvek bude vždy velikost sám na hranice DemoCalculator ovládacího prvku. Změňte velikost democalculator ovládacího prvku k ověření tohoto chování.

3. V okně **Vlastnosti** změňte <xref:System.Windows.Forms.SplitContainer.Dock%2A> hodnotu `None`vlastnosti na .

    Ovládací `SplitContainer` prvek zmenší na výchozí velikost a již nebude sledovat velikost democalculator ovládacího prvku.

4. Vpravém horním rohu![ovládacího](media/smart-tag-glyph.gif) `SplitContainer` prvku vyberte glyf inteligentní značky (Flyfg inteligentní značky). Chcete-li vlastnost nastavit `Dock` na `Fill`možnost Dock **v nadřazeném kontejneru,** nastavte vlastnost na .

    Ovládací `SplitContainer` prvek se ukotví k hranicím ovládacího prvku DemoCalculator.

    > [!NOTE]
    > Několik ovládacích prvků nabízí inteligentní značky pro usnadnění návrhu. Další informace naleznete [v tématu Návod: Provádění běžných úloh pomocí inteligentních značek v ovládacích prvcích windows forms](/dotnet/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls).

5. Vyberte svislou hranici mezi panely a přetáhněte ji doprava, aby většina prostoru pořízenélevým panelem.

    Rozděluje `SplitContainer` ovládací prvek DemoCalculator na dva panely s pohyblivým okrajem, které je oddělují. Panel vlevo bude obsahovat tlačítka kalkulačky a displej a panel vpravo zobrazí záznam aritmetické operace prováděné uživatelem.

6. V okně **Vlastnosti** změňte `BorderStyle` hodnotu `Fixed3D`vlastnosti na .

7. V **panelu nástrojů**vyberte uzel **Společné ovládací prvky,** který chcete otevřít. Vyberte `ListView` ovládací prvek a přetáhněte `SplitContainer` jej do pravého panelu ovládacího prvku.

8. Vyberte `ListView` glyf inteligentní značky ovládacího prvku. V panelu inteligentních `View` značek `Details`změňte nastavení na .

9. V panelu inteligentních značek vyberte **Upravit sloupce**.

   Otevře se dialogové okno **Editor kolekce záhlaví sloupců.**

10. V dialogovém okně **Editor kolekce záhlaví sloupců** vyberte **Přidat** a přidejte do ovládacího `ListView` prvku sloupec. Změňte hodnotu `Text` vlastnosti sloupce na **Historie**. Chcete-li vytvořit sloupec, vyberte **OK.**

11. V panelu inteligentních tagů vyberte **Dock in Parent Container**a pak vyberte glyf inteligentníznačky, který zavře panel inteligentních tagů.

12. Z **panelu nástrojů**uzlu `TableLayoutPanel` **Kontejnery** přetáhněte ovládací `SplitContainer` prvek do levého panelu ovládacího prvku.

    Ovládací `TableLayoutPanel` prvek se zobrazí na povrchu návrháře s otevřeným panelem inteligentních značek. Ovládací `TableLayoutPanel` prvek uspořádá podřízené ovládací prvky v mřížce. Ovládací `TableLayoutPanel` prvek bude obsahovat displej a tlačítka ovládacího prvku DemoCalculator. Další informace naleznete [v tématu Návod: Uspořádat ovládací prvky pomocí TableLayoutPanel](/dotnet/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel).

13. Na panelu inteligentních tagů vyberte **Upravit řádky a sloupce.**

    Otevře se dialogové okno **Styly sloupců a řádků.**

14. Vyberte tlačítko **Přidat,** dokud se nezobrazí pět sloupců. Vyberte všech pět sloupců a pak v poli **Typ velikosti** vyberte **Procento.** Nastavte hodnotu **Procenta** na **20**. Tím se nastaví každý sloupec na stejnou šířku.

15. V části **Zobrazit**vyberte **Řádky**.

16. Vyberte **Přidat,** dokud se nezobrazí pět řádků. Vyberte všech pět řádků a v poli **Typ velikosti** vyberte **Procento.** Nastavte hodnotu **Procenta** na **20**. Tím se každý řádek nastaví na stejnou výšku.

17. Vyberte **OK,** chcete-li změny přijmout, a pak vyberte glyf inteligentní značky, který zavře panel inteligentních značek.

18. V okně **Vlastnosti** změňte `Dock` hodnotu `Fill`vlastnosti na .

## <a name="populate-the-control"></a>Naplnění ovládacího prvku

Nyní, když je nastaveno rozložení ovládacího prvku, můžete naplnit ovládací prvek DemoCalculator tlačítky a displejem.

1. V **panelu nástrojů**poklepejte na ikonu ovládacího `TextBox` prvku.

   Ovládací `TextBox` prvek je umístěn v `TableLayoutPanel` první buňce ovládacího prvku.

2. V okně **Vlastnosti** změňte `TextBox` hodnotu vlastnosti ColumnSpan ovládacího prvku na **hodnotu 5**.

   Ovládací `TextBox` prvek se přesune do polohy, která je vystředěna v řádku.

3. Změňte hodnotu `TextBox` vlastnosti `Anchor` ovládacího prvku na `Left`. `Right`

   Ovládací `TextBox` prvek se zvětšuje vodorovně tak, aby překresloval všech pět sloupců.

4. Změňte hodnotu `TextBox` vlastnosti `TextAlign` ovládacího prvku na `Right`.

5. V okně **Vlastnosti** `Font` rozbalte uzel vlastnosti. Nastavte `Size` hodnotu **14**a `Bold` nastavte `TextBox` hodnotu **true** pro ovládací prvek.

6. Vyberte `TableLayoutPanel` ovládací prvek.

7. V **panelu nástrojů**poklepejte na `Button` ikonu.

   Ovládací `Button` prvek je umístěn v další `TableLayoutPanel` otevřené buňce ovládacího prvku.

8. V **panelu nástrojů**poklepejte na `Button` ikonu ještě čtyřikrát `TableLayoutPanel` a naplňte druhý řádek ovládacího prvku.

9. Vyberte `Button` všech pět ovládacích prvků tak, že je vyberete a podržíte klávesu **Shift.** Stisknutím **klávesy**+Ctrl `Button` **C** zkopírujte ovládací prvky do schránky.

10. Třikrát stiskněte **kombinaci kláves Ctrl**+**V,** chcete-li vložit kopie `Button` ovládacích prvků do zbývajících řádků ovládacího `TableLayoutPanel` prvku.

11. Vyberte všech `Button` 20 ovládacích prvků tak, že je vyberete a podržíte klávesu **Shift.**

12. V okně **Vlastnosti** změňte `Dock` hodnotu `Fill`vlastnosti na .

    Všechny `Button` ovládací prvky se zakotvují, aby vyplnily své obsahující buňky.

13. V okně **Vlastnosti** `Margin` rozbalte uzel vlastnosti. Nastavte hodnotu `All` **5**.

    Všechny `Button` ovládací prvky jsou menší, aby se mezi nimi vytvořila větší hranice.

14. Vyberte **button10** a **button20**a stisknutím **klávesy Delete** je odeberte z rozvržení.

15. Vyberte **button5** a **button15**a změňte hodnotu jejich vlastnosti `RowSpan` na **2**. Jedná se **Clear** o **=** Clear a tlačítka pro democalculator ovládací prvek.

## <a name="use-the-document-outline-window"></a>Použití okna Osnova dokumentu

Pokud je ovládací prvek nebo formulář naplněn několika ovládacími prvky, může být pro vás snazší procházet rozložení pomocí okna Osnova dokumentu.

1. Na řádku nabídek zvolte **Zobrazit** > další**osnovu dokumentu systému****Windows** > .

   Okno Osnova dokumentu zobrazuje stromové zobrazení ovládacího prvku DemoCalculator a jeho základních ovládacích prvků. Ovládací prvky `SplitContainer` kontejneru, jako je zobrazit jejich podřízené ovládací prvky jako poduzly ve stromu. Ovládací prvky můžete také přejmenovat na místě pomocí okna Osnova dokumentu.

2. V okně **Osnova dokumentu** vyberte tlačítko vpravo1 a pak vyberte **button1** **Přejmenovat**. Změňte jeho název na sevenButton.

3. Pomocí okna **Osnova dokumentu** `Button` přejmenujte ovládací prvky z názvu generovaného návrhářem na název výroby podle následujícího seznamu:

   - button1 až **sevenButton**

   - button2 to **eightButton**

   - button3 až **nineButton**

   - button4 na **divisionButton**

   - button5 pro **vymazáníButton**

   - button6 až **fourButton**

   - button7 až **fiveButton**

   - button8 až **sixButton**

   - button9 až **NásobeníButton**

   - button11 až **oneButton**

   - button12 až **twoButton**

   - button13 až **threeButton**

   - button14 až **odčítáníTlačítko**

   - button15 až **equalsButton**

   - button16 až **zeroButton**

   - button17 pro **změnuSignButton**

   - button18 až **decimalButton**

   - button19 až **additionButton**

4. Pomocí oken **Osnova dokumentu** a `Text` **Vlastnosti** změňte hodnotu vlastnosti pro každý `Button` název ovládacího prvku podle následujícího seznamu:

   - Změnit vlastnost textu ovládacího prvku sevenButton na **7**

   - Změnit vlastnost text ovládacího prvku eightButton na **8**

   - Změnit vlastnost textu ovládacího prvku nineButton na **9**

   - Změnit vlastnost divisionButton, **/** vlastnost textu ovládacího prvku, na (lomítko)

   - Změna vlastnosti textu ovládacího prvku clearButton na **Vymazat**

   - Změnit vlastnost fourButton control text na **4**

   - Změnit vlastnost fiveButton ovládacího prvku na **5**

   - Změnit vlastnost sixButton, vlastnost textu ovládacího prvku, na **6**

   - Změnit vlastnost textu ovládacího prvku **\*** multiplicationButton na (hvězdička)

   - Změnit vlastnost oneButton, vlastnost textu ovládacího prvku na **1**

   - Změnit vlastnost twoButton control text na **2**

   - Změnit vlastnost threeButton control text na **3**

   - Změnit vlastnost textu ovládacího **-** prvku odčítáníButton na (pomlčka)

   - Změnit vlastnost textu ovládacího **=** prvku equalsButton na (znaménko rovná se)

   - Změnit vlastnost zeroButton ovládacího prvku na **hodnotu 0**

   - Změnit vlastnost textu ovládacího prvku changeSignButton na**+/-**

   - Změňte vlastnost textu ovládacího prvku decimalButton na **.** (tečka)

   - Změnit vlastnost text ovládacího **+** prvku additionButton na (znaménko plus)

5. Na povrchu návrháře `Button` vyberte všechny ovládací prvky tak, že je vyberete a podržíte klávesu **Shift.**

6. V okně **Vlastnosti** `Font` rozbalte uzel vlastnosti. Nastavte `Size` hodnotu **14**a nastavte `Bold` `Button` hodnotu **true** pro všechny ovládací prvky.

Tím je dokončen návrh ovládacího prvku DemoCalculator. Vše, co zbývá, je poskytnout kalkulačku logiku.

## <a name="implement-event-handlers"></a>Implementace obslužných rutin událostí

Tlačítka na democalculator ovládací prvek mají obslužné rutiny událostí, které lze použít k implementaci velké části logiky kalkulačky. Návrhář formulářů systému Windows umožňuje implementovat zástupné procedury všech obslužných rutin událostí pro všechna tlačítka jedním poklepáním.

1. Na povrchu návrháře `Button` vyberte všechny ovládací prvky tak, že je vyberete a podržíte klávesu **Shift.**

2. Poklepejte na `Button` jeden z ovládacích prvků.

   Editor kódu se otevře obslužné rutiny událostí generované návrhářem.

## <a name="test-the-control"></a>Otestujte ovládací prvek

Vzhledem k tomu, že <xref:System.Windows.Forms.UserControl> democalculator ovládací prvek dědí z třídy, můžete otestovat jeho chování s **UserControl testovací kontejner**. Další informace naleznete v [tématu How to: Test the run-time behavior of a UserControl](/dotnet/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol).

1. Stisknutím **klávesy F5** vytvořte a spusťte ovládací prvek DemoCalculator v **testovacím kontejneru UserControl**.

2. Vyberte ohraničení `SplitContainer` mezi panely a přetáhněte ho doleva a doprava. `TableLayoutPanel` A všechny jeho podřízené ovládací prvky změnit velikost sami, aby se vešly do dostupného místa.

3. Po dokončení testování ovládacího prvku vyberte **zavřít**.

## <a name="use-the-control-on-a-form"></a>Použití ovládacího prvku ve formuláři

Ovládací prvek DemoCalculator lze použít v jiných složených ovládacích prvcích nebo ve formuláři. Následující postup popisuje, jak ji používat.

### <a name="create-the-project"></a>Vytvoření projektu

Prvním krokem je vytvoření projektu aplikace. Tento projekt použijete k vytvoření aplikace, která zobrazuje vlastní ovládací prvek.

1. Vytvořte nový projekt **aplikace Windows Forms Application** a pojmenujte jej **DemoCalculatorTest**.

2. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt **DemoCalculatorTest** a pak vyberte **Přidat odkaz** a otevřete dialogové okno Přidat **odkaz.**

3. Vyberte kartu **Projekty** a poklepejte na projekt DemoCalculatorLib a přidejte odkaz na testovací projekt.

4. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na **položku DemoCalculatorTest**a potom vyberte příkaz **Nastavit jako počáteční projekt**.

5. V Návrháři formulářů systému Windows zvětšete velikost formuláře na přibližně **700 x 500**.

### <a name="use-the-control-in-the-forms-layout"></a>Použití ovládacího prvku v rozvržení formuláře

Chcete-li použít ovládací prvek DemoCalculator v aplikaci, musíte jej umístit do formuláře.

1. V **panelu nástrojů**rozbalte uzel **Komponenty DemoCalculatorLib.**

2. Přetáhněte ovládací prvek **DemoCalculator** z **panelu nástrojů** do formuláře. Přesuňte ovládací prvek do levého horního rohu formuláře. Když je ovládací prvek blízko ohraničení formuláře, zobrazí se *snaplines.* Snaplines označují vzdálenost `Padding` vlastnosti formuláře a vlastnosti `Margin` ovládacího prvku. Umístěte ovládací prvek do umístění označeného snaplines.

   Další informace naleznete [v tématu Návod: Uspořádání ovládacích prvků pomocí snaplines](/dotnet/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines).

3. Přetáhněte `Button` ovládací prvek z **panelu nástrojů** do formuláře.

4. Přesuňte `Button` ovládací prvek kolem ovládacího prvku DemoCalculator a sledujte, kde se zobrazí snaplines. Pomocí této funkce můžete ovládací prvky přesně a snadno zarovnat. Po `Button` dokončení odstraňte ovládací prvek.

5. Vyberte ovládací prvek DemoCalculator vpravo a pak vyberte **vlastnosti**.

6. Změňte hodnotu `Dock` vlastnosti na `Fill`.

7. Vyberte formulář a rozbalte uzel vlastnosti. `Padding` Změňte hodnotu **All** na **20**.

   Velikost democalculator ovládacího prvku je snížena tak, aby vyhovovala nové `Padding` hodnotě formuláře.

8. Změňte velikost formuláře přetažením různých úchytů pro změny velikosti do různých pozic. Sledujte, jak je velikost ovládacího prvku DemoCalculator přizpůsobit.

## <a name="next-steps"></a>Další kroky

Tento článek ukázal, jak vytvořit uživatelské rozhraní pro jednoduchou kalkulačku. Chcete-li pokračovat, můžete rozšířit jeho funkce implementací logiky kalkulačky a potom [publikovat aplikaci pomocí ClickOnce](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md). Nebo pokračujte v jiném kurzu, kde [vytvoříte prohlížeč obrázků pomocí windows forms](../ide/tutorial-1-create-a-picture-viewer.md).

## <a name="see-also"></a>Viz také

- [Windows Forms – ovládací prvky](/dotnet/framework/winforms/controls/)
- [Ovládací prvky usnadnění pro Windows Forms](/dotnet/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form)
- [Publikovat pomocí ClickOnce](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
