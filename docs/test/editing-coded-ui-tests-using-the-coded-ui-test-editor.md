---
title: Úpravy programových testů uživatelského rozhraní
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.codedUItest.testeditor
helpviewer_keywords:
- coded UI test, Coded UI Test Editor
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: d6c2fcf3d8807e9095abc9546e8bf1e39aecb8ea
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85288725"
---
# <a name="edit-coded-ui-tests-using-the-coded-ui-test-editor"></a>Úpravy programových testů uživatelského rozhraní pomocí editoru programových testů uživatelského rozhraní

Editor programového testu UI umožňuje snadno upravit kódované testy uživatelského rozhraní. Pomocí editoru programového testu UI můžete vyhledat, zobrazit a upravit vlastnosti testovacích metod a akcí uživatelského rozhraní. Kromě toho můžete použít mapu ovládacího prvku uživatelského rozhraní k zobrazení a úpravě odpovídajících ovládacích prvků.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Požadavky**

- Visual Studio Enterprise
- Komponenta programového testu uživatelského rozhraní

## <a name="features-of-the-coded-ui-test-editor"></a>Funkce editoru programového testu UI

Použití editoru programového testu UI je rychlejší a efektivnější než úprava kódu v metodách programového testu UI pomocí editoru kódu. Pomocí editoru programového testu UI můžete pomocí panelů nástrojů a místních nabídek rychle vyhledat a upravit hodnoty vlastností přidružené k akcím a ovládacím prvkům uživatelského rozhraní. Například můžete použít panel nástrojů editoru programového testu UI k provedení následujících příkazů:

![Editor testu uživatelského rozhraní](../test/media/uitesteditor.png)

1. [Hledání](../ide/finding-and-replacing-text.md) vám pomůže najít akce a ovládací prvky uživatelského rozhraní.

2. **Odstranit** odebere nechtěné akce uživatelského rozhraní.

3. **Přejmenování** změní názvy testovacích metod a ovládacích prvků.

4. **Vlastnosti** otevře okno **vlastnosti** pro vybranou položku.

5. **Rozdělení na novou metodu** vám umožní naplánovat modularizaci akce uživatelského rozhraní.

6. **Přesunutí kódu** přidá vlastní kód do testovacích metod.

7. **Vložení prodlevy před** přidáním pauzy před akcí uživatelského rozhraní, které je zadáno v milisekundách.

8. **Vyhledání ovládacího prvku uživatelského rozhraní** identifikuje umístění ovládacího prvku v uživatelském rozhraní testované aplikace.

9. **Vyhledat vše** vám pomůže ověřit vlastnost ovládacího prvku a významné změny ovládacích prvků aplikace.

Když otevřete soubor *UIMap. UITest* přidružený k zakódovanému testu UI, Programový test uživatelského rozhraní se otevře v editoru programového **testu UI**. Následující postupy popisují, jak můžete vyhledat a upravit testovací metody a vlastnosti pro akce uživatelského rozhraní a ovládací prvky pomocí panelu nástrojů a místních nabídek editoru.

## <a name="open-a-coded-ui-test"></a>Otevření programového testu uživatelského rozhraní

Pomocí editoru programového **testu UI**můžete zobrazit a upravit programový test UI založený na jazyce Visual C# a Visual Basic.

![Místní nabídka upravit pomocí Tvůrce programového testu uživatelského rozhraní](../test/media/editcodeduitest.png)

V **Průzkumník řešení**otevřete místní nabídku pro *UIMap. UITest* a klikněte na **otevřít**. Programový test uživatelského rozhraní se zobrazí v **editoru programového testu UI**. Nyní můžete zobrazit a upravit zaznamenané metody, akce a odpovídající ovládací prvky v programovém testu uživatelského rozhraní.

> [!TIP]
> Když vyberete akci uživatelského rozhraní, která je umístěna v metodě v podokně **akce uživatelského rozhraní** , je zvýrazněn odpovídající ovládací prvek. Můžete také upravit akci uživatelského rozhraní nebo vlastnosti ovládacích prvků.

## <a name="modify-ui-action-and-control-properties"></a>Upravit akce uživatelského rozhraní a vlastnosti ovládacího prvku

Pomocí editoru programového testu UI můžete rychle najít a zobrazit všechny akce uživatelského rozhraní v testovacích metodách. Když vyberete akci uživatelského rozhraní v editoru, odpovídající ovládací prvek se automaticky zvýrazní. Podobně pokud vyberete ovládací prvek, jsou zvýrazněny související akce uživatelského rozhraní. Když vyberete akci uživatelského rozhraní nebo ovládací prvek, je pak snadné použít okno **vlastnosti** pro úpravu vlastností, které s ním odpovídají.

![Vlastnosti akce uživatelského rozhraní](../test/media/codeduiedituiaction.png)

Chcete-li upravit vlastnosti akce uživatelského rozhraní, v podokně **akce uživatelského rozhraní** rozbalte testovací metodu obsahující akci uživatelského rozhraní, pro kterou chcete upravit vlastnosti, vyberte akci uživatelského rozhraní a pak upravte vlastnosti pomocí okno Vlastnosti.

Například pokud server není k dispozici a máte přidruženou akci uživatelského rozhraní k webovému prohlížeči, který uvádí stav **Přejít na webovou stránku http: \/ /Contoso1/default.aspx**, můžete změnit adresu URL na `http://Contoso2/default.aspx` .

![Vlastnosti ovládacích prvků](../test/media/codeduitestcontrolprop.png)

Změna vlastností ovládacího prvku se provádí stejným způsobem jako akce uživatelského rozhraní. V podokně **Mapa ovládacího prvku uživatelského rozhraní** vyberte ovládací prvek, který chcete upravit, a upravte jeho vlastnosti pomocí okna **vlastnosti** .

Vývojář například mohl změnit vlastnost **(ID)** na ovládacím prvku tlačítko ve zdrojovém kódu pro aplikaci, která je testována z "idSubmit" na "idLogin". V aplikaci se změnila vlastnost **(ID)** , Programový test uživatelského rozhraní nebude moci najít ovládací prvek tlačítko a nebude úspěšný. V tomto případě může tester otevřít kolekci **Vlastnosti hledání** a změnit vlastnost **ID** tak, aby odpovídala nové hodnotě, kterou vývojář v aplikaci použil. Tester může také změnit hodnotu vlastnosti **popisného názvu** z "Odeslat" na "login". Díky této změně se přidružená akce uživatelského rozhraní v editoru programového testu uživatelského rozhraní aktualizuje z příkazu "Odeslat tlačítko" na "zvolit" tlačítko Login.

Po dokončení úprav uložte změny do souboru *UIMap. Designer* kliknutím na tlačítko **Uložit** na panelu nástrojů sady Visual Studio.

### <a name="tips"></a>Tipy

- Pokud se okno **vlastnosti** nezobrazí, stiskněte a podržte klávesu **ALT** , stiskněte klávesu **ENTER**nebo stiskněte klávesu **F4**.

- Provedené změny vlastností vrátíte zpět výběrem možnosti **zpět** v nabídce **Úpravy** nebo stisknutím klávesy **CTRL** + **Z**.

- K otevření nástroje **Najít a nahradit** v sadě Visual Studio můžete použít tlačítko **Najít** na panelu nástrojů editoru programového testu UI. Pak můžete pomocí ovládacího prvku **hledání** vyhledat akci uživatelského rozhraní v editoru programového testu UI. Například se můžete pokusit najít kliknutím na tlačítko Login. To může být užitečné při velkých testech. V editoru programového testu UI nelze použít funkci Replace v nástroji **Najít a nahradit** . Další informace najdete v tématu Vyhledání [a nahrazení textu](../ide/finding-and-replacing-text.md)v části najít ovládací prvek.

- V některých případech může být obtížné vizualizovat, kde jsou ovládací prvky umístěny v uživatelském rozhraní testované aplikace. Jednou z možností Editoru programového testu UI je, že můžete vybrat ovládací prvek uvedený v mapě ovládacího prvku uživatelského rozhraní a zobrazit jeho umístění v testované aplikaci. Další informace naleznete v tématu [vyhledání ovládacího prvku uživatelského rozhraní v testované aplikaci](#locate-a-ui-control-in-the-application-under-test) , které najdete dále v tomto článku.

- Může být nutné rozšířit ovládací prvek kontejneru, který obsahuje ovládací prvek, který chcete upravit. Další informace naleznete v tématu [vyhledání ovládacího prvku a jeho následníků](#locate-a-control-and-its-descendants) uvedených níže v tomto článku.

## <a name="delete-unwanted-ui-actions"></a>Odstranit nechtěné akce uživatelského rozhraní

Můžete snadno odebrat nechtěné akce uživatelského rozhraní v programovém testu uživatelského rozhraní.

![Akce odstranění uživatelského rozhraní](../test/media/codeduideleteuiaction.png)

V podokně **akce uživatelského rozhraní** rozbalte testovací metodu obsahující akci uživatelského rozhraní, kterou chcete odstranit. Otevřete místní nabídku pro akci uživatelského rozhraní a vyberte možnost **Odstranit**.

## <a name="split-a-test-method-into-two-separate-methods"></a>Rozdělení testovací metody do dvou samostatných metod

Můžete rozdělit testovací metodu pro upřesnění nebo pro naplánovat modularizacií akcí uživatelského rozhraní. Například váš test může mít jedinou testovací metodu s akcemi uživatelského rozhraní ve dvou ovládacích prvcích kontejneru. Akce uživatelského rozhraní mohou být lépe modulární ve dvou metodách, které odpovídají jednomu kontejneru.

![Rozdělení testovací metody](../test/media/codeduitestsplitmethod1.png)

![Dvě testovací metody](../test/media/codeduitestsplitmethod2.png)

V podokně **akce uživatelského rozhraní** rozbalte testovací metodu, kterou chcete rozdělit do dvou samostatných metod, a vyberte akci uživatelského rozhraní, kde chcete spustit novou metodu testu. Buď otevřete místní nabídku pro akci uživatelského rozhraní a zvolte možnost **rozdělit do nové metody**, nebo zvolte tlačítko rozdělit na **novou metodu** na panelu nástrojů editoru programového testu UI. Nová testovací metoda se zobrazí v podokně **akce uživatelského rozhraní** . Obsahuje akce uživatelského rozhraní od akce, kde jste určili rozdělení.

Po dokončení rozdělení metody uložte změny do souboru *UIMap. Designer* kliknutím na tlačítko **Uložit** na panelu nástrojů sady Visual Studio.

> [!WARNING]
> Pokud rozdělíte metodu, je nutné upravit jakýkoli kód, který volá existující metodu pro volání nové metody, kterou vytváříte, pokud stále chcete tyto akce uživatelského rozhraní zahrnout. Při rozdělení metody se zobrazí dialogové okno Microsoft Visual Studio. Upozorňuje vás, že je nutné upravit jakýkoli kód, který volá existující metodu pro volání nové metody, kterou vytváříte. Vyberte **Ano**.

### <a name="tips"></a>Tipy

- Chcete-li rozdělení vrátit zpět, zvolte možnost **zpět** v nabídce **Úpravy** nebo stiskněte klávesu **CTRL** + **Z**.

- Novou metodu můžete přejmenovat. Vyberte ji v podokně **akce uživatelského rozhraní** a klikněte na tlačítko **Přejmenovat** na panelu nástrojů editoru programového testu UI.

   -nebo-

   Otevřete místní nabídku pro novou testovací metodu a vyberte možnost **Přejmenovat**.

   Zobrazí se dialogové okno aplikace Microsoft Visual Studio. Upozorňuje vás, že je nutné upravit jakýkoli kód, který odkazuje na metodu. Vyberte **Ano**.

## <a name="move-a-test-method-to-the-uimap-file-to-facilitate-customization"></a>Přesunutí testovací metody do souboru UIMap, aby se usnadnilo přizpůsobení

Pokud určíte, že jedna z vašich zkušebních metod v programovém testu UI vyžaduje vlastní kód, je nutné ji přesunout do souboru *UIMap.cs* nebo *UIMap. vb* . V opačném případě bude váš kód při každém překompilování kódovaného testu uživatelského rozhraní přepsán. Pokud tuto metodu nepřesunete, váš vlastní kód se přepíše pokaždé, když je test znovu zkompilován.

V podokně **akce uživatelského rozhraní** vyberte testovací metodu, kterou chcete přesunout do souboru *UIMap.cs* nebo *UIMap. vb* , abyste usnadnili funkci vlastního kódu, která nebude přepsána při překompilování testovacího kódu. Dále klikněte na tlačítko **přesunout kód** na panelu nástrojů editoru programového testu UI nebo otevřete místní nabídku pro testovací metodu a vyberte možnost **přesunout kód**. Testovací metoda je odebrána ze souboru *UIMap. UITest* a již se nezobrazuje v podokně **akce uživatelského rozhraní** . Chcete-li upravit testovací soubor, který jste přesunuli, otevřete soubor *UIMap.cs* nebo *UIMap. vb* z **Průzkumník řešení**.

Po dokončení přesunutí metody uložte změny do souboru *UIMap. Designer* kliknutím na tlačítko **Uložit** na panelu nástrojů sady Visual Studio.

> [!WARNING]
> Po přesunutí metody již nelze upravovat pomocí editoru programového testu UI. Musíte přidat vlastní kód a spravovat jej pomocí Editoru kódu. Při přesunutí metody se zobrazí dialogové okno Microsoft Visual Studio. Upozorňuje vás, že metoda bude přesunuta ze souboru *UIMap. UITest* do souboru *UIMap.cs* nebo *UIMap. vb* a že již nebudete moci upravovat metodu pomocí editoru programového testu uživatelského rozhraní. Vyberte **Ano**.

### <a name="tips"></a>Tipy

Chcete-li zrušit přesun, vyberte možnost **zpět** v nabídce **Úpravy** nebo stiskněte klávesu **CTRL** + **Z**. Je však nutné ručně odebrat kód ze souboru *UIMap.cs* nebo *UIMap. vb* .

## <a name="locate-a-ui-control-in-the-application-under-test"></a>Vyhledání ovládacího prvku uživatelského rozhraní v testované aplikaci

V některých případech může být obtížné vizualizovat, kde jsou ovládací prvky umístěny v uživatelském rozhraní testované aplikace. Jednou z možností Editoru programového testu UI je, že můžete vybrat ovládací prvek uvedený v mapě ovládacího prvku uživatelského rozhraní a zobrazit jeho umístění v testované aplikaci. Pomocí funkce **najít ovládací prvek uživatelského rozhraní** v testované aplikaci lze také použít k ověření úprav vlastností hledání, které jste provedli v ovládacím prvku.

![Vyhledat ovládací prvek uživatelského rozhraní](../test/media/codeduilocatecontrol.png)

![Ovládací prvek umístěný v testované aplikaci](../test/media/codeduilocatecontrol2.png)

V podokně **Mapa ovládacího prvku uživatelského rozhraní** vyberte ovládací prvek, který chcete najít v aplikaci přidružené k testu. Potom otevřete místní nabídku pro ovládací prvek a pak zvolte **najít ovládací prvek uživatelského rozhraní**. V testované aplikaci je ovládací prvek označený modrým ohraničením.

> [!NOTE]
> Před umístěním ovládacího prvku uživatelského rozhraní ověřte, zda je aplikace přidružená k testu spuštěna.

### <a name="tips"></a>Tipy

Pomocí možnosti **Najít vše** můžete ověřit, zda lze správně umístit všechny ovládací prvky v kontejneru. Tato možnost je popsaná v následující části.

## <a name="locate-a-control-and-its-descendants"></a>Vyhledat ovládací prvek a jeho následníky

Můžete ověřit, že všechny ovládací prvky v kontejneru mohou být správně umístěny v uživatelském rozhraní testované aplikace. To může být užitečné při ověřování změn vlastností hledání, které jste mohli u kontejneru provést. Pokud se navíc v uživatelském rozhraní testované aplikace objevily významné změny, můžete ověřit, zda jsou stále správné vlastnosti hledání stávajících ovládacích prvků.

![Najít všechny podřízené ovládací prvky](../test/media/codeduilocateall.png)

![Všechny ovládací prvky umístěné](../test/media/codeduilocateall2.png)

V podokně **Mapa ovládacího prvku uživatelského rozhraní** vyberte ovládací prvek kontejneru, který chcete najít a zobrazit všechny následníky pro. Potom otevřete místní nabídku ovládacího prvku a vyberte **Najít vše**. Ovládací prvek kontejner a všechny jeho odvozené ovládací prvky jsou označeny v editoru programového testu UI buď zeleným zaškrtnutím, nebo červeným znakem "X". Tyto značky vám pomůžou zjistit, jestli se ovládací prvky úspěšně nacházely v testované aplikaci.

> [!NOTE]
> Před umístěním ovládacích prvků uživatelského rozhraní ověřte, zda je spuštěna aplikace přidružená k testu.

## <a name="insert-a-delay-before-a-ui-action"></a>Vložení zpoždění před akci uživatelského rozhraní

V některých případech můžete chtít, aby test čekal na výskyt určitých událostí, jako je okno, které se má zobrazit, indikátor průběhu zmizí a tak dále. Pomocí editoru programového testu UI můžete to provést vložením zpoždění před akci uživatelského rozhraní. Můžete zadat, kolik sekund má být zpoždění.

![Vložení zpoždění před akcí uživatelského rozhraní](../test/media/codeduidelay.png)

![Zpoždění přidané s 5 sekundami](../test/media/codeduidealy2.png)

V podokně **akce uživatelského rozhraní** rozbalte testovací metodu, která obsahuje akci uživatelského rozhraní, do které chcete vložit zpoždění. Vyberte akci uživatelského rozhraní. Dále otevřete místní nabídku pro akci uživatelského rozhraní a vyberte možnost **Vložit zpoždění před**. Je vložena a zvýrazněna prodleva před zvolenou akcí uživatelského rozhraní s následujícím textem: pro **prodlevu uživatele mezi akcemi počkejte 1 sekundy**. V okně **vlastnosti** změňte hodnotu vlastnosti **Delay** na požadovaný počet milisekund.

Po vložení prodlevy uložte změny do souboru *UIMap. Designer* kliknutím na tlačítko **Uložit** na panelu nástrojů sady Visual Studio.

Pokud potřebujete zajistit, aby byl konkrétní ovládací prvek k dispozici před akcí uživatelského rozhraní, měli byste zvážit přidání vlastního kódu do testovací metody pomocí příslušné metody UITestControl. WaitForControlXXX (). Další informace najdete v tématu [vytváření programových testů uživatelského rozhraní, které čekají na konkrétní události během přehrávání](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md).

## <a name="see-also"></a>Viz také

- [Použití automatizace uživatelského rozhraní k otestování kódu](../test/use-ui-automation-to-test-your-code.md)
- [Vytvořit kódované testy uživatelského rozhraní](../test/use-ui-automation-to-test-your-code.md)
- [Vytvořit datově řízený programový test uživatelského rozhraní](../test/creating-a-data-driven-coded-ui-test.md)
- [Návod: vytváření, upravování a údržba programového testu uživatelského rozhraní](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
