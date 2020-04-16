---
title: Úpravy kódovaných testů ui
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.codedUItest.testeditor
helpviewer_keywords:
- coded UI test, Coded UI Test Editor
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 8df6d1ea44cb9737c39653366c7b35823051d5f6
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81445035"
---
# <a name="edit-coded-ui-tests-using-the-coded-ui-test-editor"></a>Úprava kódovaných testů ui pomocí Editoru testů programovaného ui

Programový editor testů ui umožňuje snadno upravit kódované testy ui. Pomocí Editoru testů programovaného ui můžete vyhledat, zobrazit a upravit vlastnosti testovacích metod a akcí ui. Kromě toho můžete použít mapu ovládacího prvku ui k zobrazení a úpravám odpovídajících ovládacích prvků.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Požadavky**

- Visual Studio Enterprise
- Kódovaná testovací komponenta ui

## <a name="features-of-the-coded-ui-test-editor"></a>Funkce editoru programových testů ui

Použití Editoru testů programového rozhraní je rychlejší a efektivnější než úprava kódu v kódovaných testovacích metodách rozhraní AU pomocí Editoru kódu. Pomocí Editoru testů programového rozhraní můžete pomocí panelu nástrojů a místních nabídek rychle vyhledat a upravit hodnoty vlastností přidružené k akcím a ovládacím prvkům ui. Pomocí panelu nástrojů editoru testů programového rozhraní můžete například provést následující příkazy:

![Editor testů ui](../test/media/uitesteditor.png)

1. [Hledání](../ide/finding-and-replacing-text.md) vám pomůže najít akce a ovládací prvky ui.

2. **Odstraněním** odeberete nežádoucí akce ui.

3. **Přejmenování** změní názvy testovacích metod a ovládacích prvků.

4. **Vlastnosti** otevřou okno **Vlastnosti** pro vybranou položku.

5. **Rozdělit na novou metodu** umožňuje modularizovat akce ui.

6. **Přesunout kód** přidá vlastní kód do testovacích metod.

7. **Vložit zpoždění před** přidá pauzu před akci ui, zadaný v milisekundách.

8. **Vyhledejte ovládací prvek ui** identifikuje umístění ovládacího prvku v ui testovny aplikace.

9. **Vyhledejte vše** pomáhá ověřit vlastnost ovládacího prvku a významné změny ovládacích prvků aplikace.

Když otevřete soubor *UIMap.uitest* přidružený k vašemu programovanému testu uI, otevře se kódovaný test ui v **Editoru testů kódovaného ui**. Následující postupy popisují, jak pak můžete vyhledat a upravit testovací metody a vlastnosti akcí uj a ovládací prvky pomocí panelu nástrojů editoru a místní nabídky.

## <a name="open-a-coded-ui-test"></a>Otevření kódovaného testu ui

Můžete zobrazit a upravit test kódovaného rozhraní Visual C# a Visual Basic pomocí **Editoru testů programového rozhraní**.

![Kontextová nabídka Upravit pomocí tvůrce programových testů ui](../test/media/editcodeduitest.png)

V **Průzkumníku řešení**otevřete místní nabídku *u UIMap.uitest* a zvolte **Otevřít**. Kódovaný test ui se zobrazí v **Programovém editoru testů uI**. Nyní můžete zobrazit a upravit zaznamenané metody, akce a odpovídající ovládací prvky v programovém testu ui.

> [!TIP]
> Když vyberete akci ui, která se nachází v metodě v podokně **Akce ui,** zobrazí se odpovídající ovládací prvek. Můžete také upravit akci uj.

## <a name="modify-ui-action-and-control-properties"></a>Úprava vlastností akce a ovládacího prvku ui

Pomocí Editoru testkódovaného ui můžete rychle vyhledat a zobrazit všechny akce ui v testovacích metodách. Když v editoru vyberete akci uj., automaticky se zvýrazní odpovídající ovládací prvek. Podobně pokud vyberete ovládací prvek, přidružené akce ui jsou zvýrazněny. Když vyberete akci uživatelského rozhraní nebo ovládací prvek, je pak snadné použít okno **Vlastnosti** k úpravě vlastností, které s ním odpovídají.

![Vlastnosti akce ui](../test/media/codeduiedituiaction.png)

Chcete-li upravit vlastnosti akce uj. **UI Action**

Pokud například server není k dispozici a k webovému prohlížeči je přidružena akce uživatelského prostředí, která uvádí **Přejít na\/webovou stránku http: /Contoso1/default.aspx**, můžete adresu URL změnit na `http://Contoso2/default.aspx`.

![Vlastnosti ovládacích prvků](../test/media/codeduitestcontrolprop.png)

Úprava vlastností ovládacího prvku se provádí stejným způsobem jako akce ui. V podokně **Mapa ovládacího prvku ui** vyberte ovládací prvek, který chcete upravit, a upravit jeho vlastnosti pomocí okna **Vlastnosti.**

Vývojář například mohl změnit vlastnost **(ID)** na ovládacím prvku tlačítka ve zdrojovém kódu testované aplikace z "idSubmit" na "idLogin". Při změně vlastnosti **(ID)** v aplikaci nebude programovaný test ui schopen najít ovládací prvek tlačítka a selže. V takovém případě může tester otevřít **kolekci Vlastnosti vyhledávání** a změnit vlastnost **Id** tak, aby odpovídala nové hodnotě, kterou vývojář použil v aplikaci. Tester může také změnit hodnotu **vlastnosti Popisný název** z "Odeslat" na "Přihlásit". Provedením této změny je přidružená akce uživatelského rozhraní v editoru programových testů uživatelského rozhraní aktualizována z tlačítka "Zvolit odeslat" na tlačítko "Zvolit přihlášení".

Po dokončení úprav uložte změny do souboru *UIMap.Designer* tak, že **zvolíte Uložit** na panelu nástrojů sady Visual Studio.

### <a name="tips"></a>Tipy

- Pokud se okno **Vlastnosti** nezobrazí, stiskněte a podržte **klávesu Alt,** když stisknete **Enter**nebo stiskněte **klávesu F4**.

- Chcete-li vrátit zpět provedené změny vlastností, vyberte v nabídce **Úpravy** možnost **Zpět** nebo stiskněte **kombinaci kláves Ctrl**+**Z**.

- Pomocí tlačítka **Najít** v panelu nástrojů editoru test ui kódu můžete v sadě Visual Studio otevřít nástroj **Hledání a nahradit.** Potom můžete použít **najít** ovládací prvek najít akci ui v editoru test programovaného ui. Můžete se například pokusit najít tlačítko "Přihlásit se". To může být užitečné při velkých testech. Funkci nahradit nelze použít v nástroji **Najít a nahradit** v Editoru testů programového ui. Další informace naleznete v tématu Najít ovládací prvek v [tématu Najít a nahradit text](../ide/finding-and-replacing-text.md).

- Někdy může být obtížné vizualizovat, kde jsou ovládací prvky umístěny v ui testované aplikace. Jednou z možností programového editoru testů ui je, že můžete vybrat ovládací prvek uvedený v mapě ovládacího prvku ui a zobrazit jeho umístění v testované aplikaci. Další informace naleznete [v tématu Lokalizovat ovládací prvek uj.](#locate-a-ui-control-in-the-application-under-test)

- Může být nutné rozšířit ovládací prvek kontejneru, který obsahuje ovládací prvek, který chcete upravit. Další informace naleznete v [tématu Vyhledejte ovládací prvek a jeho potomci](#locate-a-control-and-its-descendants) umístěné dále níže v tomto článku.

## <a name="delete-unwanted-ui-actions"></a>Odstranění nežádoucích akcí ui

Nežádoucí akce ui můžete snadno odebrat v programovém testu ui.

![Odstranit akci ui](../test/media/codeduideleteuiaction.png)

V podokně **akce ui** rozbalte testovací metodu, která obsahuje akci ui, kterou chcete odstranit. Otevřete místní nabídku akce uj. **Delete**

## <a name="split-a-test-method-into-two-separate-methods"></a>Zkušební metoda se rozdělí na dvě samostatné metody

Můžete rozdělit testovací metodu upřesnit nebo modularizovat akce ui. Například váš test může mít jednu testovací metodu s akcemi ui ve dvou ovládacích prvcích kontejneru. Akce uživatelského prostředí může být lépe modularizované ve dvou metodách, které odpovídají jednomu kontejneru.

![Rozdělení zkušební metody](../test/media/codeduitestsplitmethod1.png)

![Dvě zkušební metody](../test/media/codeduitestsplitmethod2.png)

V podokně **akce ui** rozbalte testovací metodu, kterou chcete rozdělit na dvě samostatné metody, a vyberte akci ui, kde chcete začít novou testovací metodu. Buď otevřete místní nabídku pro akci uj. a pak zvolte **Rozdělit do nové metody**, nebo zvolte tlačítko Rozdělit na novou **metodu** na panelu nástrojů Editor testů kódovaného u.. Nová testovací metoda se zobrazí v podokně **Akce ui.** Obsahuje akce ui počínaje akcí, kde jste zadali rozdělení.

Po dokončení rozdělení metody uložte změny do souboru *UIMap.Designer* výběrem **uložit** na panelu nástrojů Sady Visual Studio.

> [!WARNING]
> Pokud rozdělíte metodu, musíte upravit libovolný kód, který volá existující metodu také volat novou metodu, kterou se chystáte vytvořit, pokud stále chcete tyto akce ui zahrnuty. Při rozdělení metody se zobrazí dialogové okno Microsoft Visual Studio. Varuje vás, že je nutné upravit libovolný kód, který volá existující metodu také volat novou metodu, kterou se chystáte vytvořit. Zvolte **Ano**.

### <a name="tips"></a>Tipy

- Chcete-li rozdělení vrátit zpět, zvolte **Zpět** z nabídky **Úpravy** nebo stiskněte **ctrl**+**z**.

- Novou metodu můžete přejmenovat. Vyberte ji v podokně **Akce uživatelského rozhraní** a v pruhu nástrojů Editor testů programového rozhraní zvolte tlačítko **Přejmenovat.**

   -nebo-

   Otevřete místní nabídku nové zkušební metody a zvolte **Přejmenovat**.

   Zobrazí se dialogové okno aplikace Microsoft Visual Studio. Varuje, že je nutné upravit libovolný kód, který odkazuje na metodu. Zvolte **Ano**.

## <a name="move-a-test-method-to-the-uimap-file-to-facilitate-customization"></a>Přesunutí testovací metody do souboru UIMap pro usnadnění přizpůsobení

Pokud zjistíte, že jedna z testovacích metod v testu kódovaného ui vyžaduje vlastní kód, musíte jej přesunout do souboru *UIMap.cs* nebo *UIMap.vb.* V opačném případě bude váš kód přepsán při každém překompilování kódovaného testu ui. Pokud nepřesunete metodu, váš vlastní kód bude přepsán při každém překompilován testu.

V podokně **akcí ui** vyberte testovací metodu, kterou chcete přesunout do souboru *UIMap.cs* nebo *UIMap.vb,* abyste usnadnili vlastní funkci kódu, která nebude přepsána při opětovnékompilaci testovacího kódu. Dále zvolte tlačítko **Přesunout kód** na panelu nástrojů Editor testů zakódovaného ui nebo otevřete místní nabídku testovací metody a zvolte **Přesunout kód**. Testovací metoda je odebrána ze souboru *UIMap.uitest* a již se nezobrazuje v podokně **Akce ui.** Chcete-li upravit přesunutý testovací soubor, otevřete *soubor UIMap.cs* nebo *Soubor UIMap.vb* z **Průzkumníka řešení**.

Po dokončení přesunutí metody uložte změny do souboru *UIMap.Designer* výběrem **uložit** na panelu nástrojů Sady Visual Studio.

> [!WARNING]
> Po přesunutí metody ji již nelze upravovat pomocí Editoru testů programového rozhraní. Musíte přidat vlastní kód a spravovat jej pomocí Editoru kódu. Při přesunutí metody se zobrazí dialogové okno Microsoft Visual Studio. Varuje vás, že metoda bude přesunuta ze souboru *UIMap.uitest* do souboru *UIMap.cs* nebo *UIMap.vb* a že již nebudete moci upravovat metodu pomocí programového editoru testů ui. Zvolte **Ano**.

### <a name="tips"></a>Tipy

Chcete-li přesunutí vrátit zpět, vyberte v nabídce **Úpravy** možnost **Zpět** nebo stiskněte **kombinaci kláves Ctrl**+**Z**. Potom je však nutné ručně odebrat kód ze souboru *UIMap.cs* nebo *UIMap.vb.*

## <a name="locate-a-ui-control-in-the-application-under-test"></a>Vyhledání ovládacího prvku ui v testovce aplikace

Někdy může být obtížné vizualizovat, kde jsou ovládací prvky umístěny v ui testované aplikace. Jednou z možností programového editoru testů ui je, že můžete vybrat ovládací prvek uvedený v mapě ovládacího prvku ui a zobrazit jeho umístění v testované aplikaci. Pomocí **funkce Lokalizovat ovládací prvek ui** v testovce aplikace lze také ověřit změny vlastností hledání, které jste provedli v ovládacím prvku.

![Vyhledání ovládacího prvku ui](../test/media/codeduilocatecontrol.png)

![Kontrola umístěná v testované aplikaci](../test/media/codeduilocatecontrol2.png)

V podokně **Mapa ovládacího prvku ui** vyberte ovládací prvek, který chcete vyhledat v aplikaci přidružené k testu. Dále otevřete místní nabídku ovládacího prvku a pak zvolte **Vyhledat ovládací prvek ui**. V aplikaci, která je testována, je ovládací prvek označen modrým ohraničením.

> [!NOTE]
> Před vyhledáním ovládacího prvku ui ověřte, zda je spuštěna aplikace přidružená k testu.

### <a name="tips"></a>Tipy

Můžete použít **vyhledat vše** možnost ověřit, že všechny ovládací prvky pod kontejnerem mohou být správně umístěny. Tato možnost je popsána v další části.

## <a name="locate-a-control-and-its-descendants"></a>Vyhledání ovládacího prvku a jeho potomků

Můžete ověřit, že všechny ovládací prvky v kontejneru může být správně umístěn v ui testované aplikace. To může být užitečné při ověřování změn vlastností hledání, které jste provedli v kontejneru. Navíc pokud došlo k významné změny v ui testované aplikace, můžete ověřit, že existující vlastnosti hledání ovládacího prvku jsou stále správné.

![Vyhledání všech ovládacích prvků potomků](../test/media/codeduilocateall.png)

![Všechny ovládací prvky umístěné](../test/media/codeduilocateall2.png)

V podokně **Mapa ovládacího prvku ui** vyberte ovládací prvek kontejneru, který chcete vyhledat a zobrazit všechny potomky pro. Dále otevřete místní nabídku ovládacího prvku a zvolte **Vyhledat vše**. Ovládací prvek kontejneru a všechny jeho podřízené ovládací prvky jsou označeny v editoru test kódovanéuživatelské rozhraní se zeleným zaškrtnutím nebo červené "X". Tyto značky vás upozorní, pokud byly ovládací prvky úspěšně umístěny v testované aplikaci.

> [!NOTE]
> Před vyhledáním ovládacích prvků ui ověřte, zda je spuštěna aplikace přidružená k testu.

## <a name="insert-a-delay-before-a-ui-action"></a>Vložení zpoždění před akcí uj.u.

Někdy můžete chtít, aby test čekat na určité události, jako je například okno se zobrazí, indikátor průběhu zmizí a tak dále. Pomocí Editoru test kódovaného ui, můžete to provést vložením zpoždění před akce ui. Můžete určit, kolik sekund má být zpoždění.

![Vložení zpoždění před akcí uj.](../test/media/codeduidelay.png)

![Zpoždění přidáno s 5 sekund](../test/media/codeduidealy2.png)

V podokně **akce ui** rozbalte testovací metodu, která obsahuje akci ui, kterou chcete vložit před zpoždění. Vyberte akci ui. Dále otevřete místní nabídku akce uj. **Insert Delay Before** Před vybranou akci uživatelského rozhraní je vložena a zvýrazněna prodleva s následujícím textem: **Počkejte 1 sekundu na zpoždění mezi akcemi uživatele**. V okně **Vlastnosti** změňte hodnotu vlastnosti **Delay** na požadovaný počet milisekund.

Po dokončení vkládání zpoždění uložte změny do souboru *UIMap.Designer* výběrem **uložit** na panelu nástrojů sady Visual Studio.

Pokud potřebujete zajistit, že konkrétní ovládací prvek je k dispozici před akce ui, měli byste zvážit přidání vlastního kódu testovací metody pomocí příslušné metody UITestControl.WaitForControlXXX(). Další informace naleznete [v tématu Vytvoření programových testů ui čekat na konkrétní události během přehrávání](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md).

## <a name="see-also"></a>Viz také

- [Testování kódu pomocí automatizace uživatelského rozhraní](../test/use-ui-automation-to-test-your-code.md)
- [Vytvoření kódovaných testů ui](../test/use-ui-automation-to-test-your-code.md)
- [Vytvoření kódu ui řízeného daty](../test/creating-a-data-driven-coded-ui-test.md)
- [Návod: Vytvoření, úpravy a údržba kódovaného testu ui](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
