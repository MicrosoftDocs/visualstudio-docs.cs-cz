---
title: Úpravy programových testů uživatelského rozhraní
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
f1_keywords:
- vs.codedUItest.testeditor
helpviewer_keywords:
- coded UI test, Coded UI Test Editor
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 6c45a8abceacb1d566ca5aba382e7955f1c2601e
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2018
ms.locfileid: "52895558"
---
# <a name="edit-coded-ui-tests-using-the-coded-ui-test-editor"></a>Úprava programových testů uživatelského rozhraní pomocí editoru programového testu uživatelského rozhraní

Editor programového testu uživatelského rozhraní umožňuje snadno upravovat programové testy uživatelského rozhraní. Použití editoru programového testu UI, můžete vyhledat, zobrazit a upravit vlastnosti testovací metody a akce uživatelského rozhraní. Kromě toho můžete použít v mapování ovládacího prvku uživatelského rozhraní k zobrazení a jejich odpovídající ovládacích prvcích pro úpravy.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Požadavky**

- Visual Studio Enterprise
- Programový test komponenta uživatelského prostředí

## <a name="features-of-the-coded-ui-test-editor"></a>Funkce nástroje editoru programového testu UI

Použití editoru programového testu UI je rychlejší a efektivnější než úpravy kódu v programových testovací metody uživatelského rozhraní pomocí editoru kódu. Se editoru programového testu UI, můžete použít nástrojů a v místní nabídky rychle vyhledat a upravte hodnoty vlastností související s ovládacími prvky a akce uživatelského rozhraní. Například můžete použít editoru programového testu UI pro panel nástrojů k provedení následujících příkazů:

![Editor testu UI](../test/media/uitesteditor.png)

1. [Najít](../ide/finding-and-replacing-text.md) pomáhá při hledání akce uživatelského rozhraní a ovládací prvky.

2. **Odstranit** odebere nežádoucích akcí uživatelského rozhraní.

3. **Přejmenovat** změní názvy pro testovací metody a ovládací prvky.

4. **Vlastnosti** otevře **vlastnosti** okna pro vybranou položku.

5. **Rozdělit na novou metodu** umožňuje modularizaci akce uživatelského rozhraní.

6. **Přesunout kód** přidá vlastní kód testovací metody.

7. **Vložit zpoždění před** přidá pozastavení před akci uživatelského rozhraní, zadává v milisekundách.

8. **Vyhledejte ovládací prvek uživatelského rozhraní** Určuje umístění ovládacího prvku v uživatelském rozhraní aplikace v rámci testu.

9. **Najít všechny** ověříte pomáhá řídit vlastnost a významné změny na ovládací prvky vaší aplikace.

Když otevřete *UIMap.uitest* přidružený žádný programového testu UI, programový test otevře uživatelské rozhraní v souboru **editoru programového testu UI**. Následující postupy popisují, jak můžete poté vyhledejte a upravovat testovací metody a vlastnosti pro akce uživatelského rozhraní a ovládacích prvků pomocí editoru panelu nástrojů a nabídek.

## <a name="open-a-coded-ui-test"></a>Spustit programový test uživatelského rozhraní

Můžete zobrazit a upravit vaše Visual C# a Visual Basic založena programových testů UI pomocí **editoru programového testu UI**.

![Kontextové nabídky upravit pomocí Tvůrce programového testu UI](../test/media/editcodeduitest.png)

V **Průzkumníka řešení**, otevřete místní nabídku pro *UIMap.uitest* a zvolte **otevřete**. Programový test uživatelského rozhraní se zobrazí v **editoru programového testu UI**. Nyní můžete zobrazit a upravit nahrané metody, akce a odpovídající ovládací prvky v programovém testu uživatelského rozhraní.

> [!TIP]
> Když vyberete akci uživatelského rozhraní, který je umístěný v metodě v **akce uživatelského rozhraní** podokně odpovídající ovládací prvek je zvýrazněn. Můžete také upravit akce uživatelského rozhraní nebo vlastností ovládacích prvků.

## <a name="modify-ui-action-and-control-properties"></a>Úprava vlastností akce a ovládací prvek uživatelského rozhraní

Pomocí editoru programového testu UI, můžete rychle najít a zobrazit všechny akce uživatelského rozhraní ve vašich testovacích metodách. Při výběru akce uživatelského rozhraní v editoru je zvýrazněn automaticky odpovídající ovládací prvek. Podobně pokud vyberete ovládací prvek, jsou zvýrazněny přidružené akce uživatelského rozhraní. Když vyberete akci uživatelského rozhraní nebo ovládacího prvku, je pak snadno použitelné **vlastnosti** okna k úpravě vlastností, které odpovídají s ním.

![Vlastností akce uživatelského rozhraní](../test/media/codeduiedituiaction.png)

Úpravy vlastností akce uživatelského rozhraní v **akce uživatelského rozhraní** podokně rozbalte položku testovací metoda, která obsahuje akce uživatelského rozhraní, který chcete upravit vlastnosti pro vybrané akce uživatelského rozhraní a potom upravte vlastnosti pomocí okna Vlastnosti.

Například pokud server není k dispozici a máte akce uživatelského rozhraní související s webovým prohlížečem, který uvádí **přejít na webovou stránku "<http://Contoso1/default.aspx>"**, můžete změnit adresu URL `'http://Contoso2/default.aspx'`.

![Vlastnosti ovládacích prvků](../test/media/codeduitestcontrolprop.png)

Úprava vlastností pro ovládací prvek se provádí stejným způsobem jako akce uživatelského rozhraní. V **mapování ovládacího prvku UI** podokně, vyberte ovládací prvek, který chcete upravit a změnit jeho vlastnosti pomocí **vlastnosti** okna.

Například vývojář změnil **(ID)** vlastnosti u ovládacího prvku tlačítko ve zdrojovém kódu aplikace testovány z "idSubmit" k "idLogin." S **(ID)** vlastnost změněn v aplikaci, programový test uživatelského rozhraní nebude možné najít ovládací prvek tlačítko a se nezdaří. V takovém případě můžete otevřít tester **vlastnosti hledání** kolekce a změnit **Id** vlastnost tak, aby odpovídala nové hodnoty, které vývojář používaných v aplikaci. Tester může změnit také **popisný název** hodnoty vlastnosti z "Odeslat" "Login". Touto změnou přidružené akce uživatelského rozhraní v uživatelském rozhraní editoru programového testu je aktualizováno z hodnoty "Vyberte"Odeslat"button" na "Vyberte"Přihlášení"tlačítko."

Po dokončení změn se uložit změny *UIMap.Designer* soubor výběrem **Uložit** na panelu nástrojů sady Visual Studio.

### <a name="tips"></a>Tipy

- Pokud **vlastnosti** okno nezobrazí, stiskněte a podržte **Alt** při stisknutí klávesy **Enter**, nebo stiskněte klávesu **F4**.

- Chcete-li vrátit zpět provedené změny vlastností, vyberte **zpět** z **upravit** nabídky nebo stisknutím klávesy **Ctrl**+**Z**.

- Můžete použít **najít** tlačítko v panelu nástrojů editoru programového testu uživatelského rozhraní **najít a nahradit** nástroje v sadě Visual Studio. Pak můžete použít **najít** ovládacího prvku najít akce uživatelského rozhraní v editoru programového testu UI. Například můžete zkusit najít "klikněte na tlačítko"Přihlášení"." To může být užitečné v testech velké. Nemůžete použít funkci nahradit v **najít a nahradit** nástroj v editoru programového testu UI. Další informace najdete v tématu najít v ovládacím prvku [najít a nahradit text](../ide/finding-and-replacing-text.md).

- V některých případech může být obtížné vizualizovat, kde jsou umístěny ovládací prvky v uživatelském rozhraní aplikace v rámci testu. Jednou z možností editoru programového testu uživatelského rozhraní je, že můžete vybrat ovládací prvek, který je uvedený v mapování ovládacího prvku uživatelského rozhraní a zobrazit jeho umístění v testované aplikaci. Další informace najdete v tématu [vyhledání ovládacího prvku uživatelského rozhraní v testované aplikaci](#locate-a-ui-control-in-the-application-under-test) najít další níže v tomto článku.

- Může být potřeba rozšířit ovládací prvek kontejneru, který obsahuje ovládací prvek, který chcete upravit. Další informace najdete v tématu [vyhledejte ovládací prvek a jeho následníky](#locate-a-control-and-its-descendants) najít další níže v tomto článku.

## <a name="delete-unwanted-ui-actions"></a>Odstranění nežádoucích akcí uživatelského rozhraní

Můžete snadno odebrat nežádoucích akcí uživatelského rozhraní programového testu UI.

![Odstranění akce uživatelského rozhraní](../test/media/codeduideleteuiaction.png)

V **akce uživatelského rozhraní** podokně rozbalte položku testovací metoda, která obsahuje akce uživatelského rozhraní, který chcete odstranit. Otevřete místní nabídku pro akce uživatelského rozhraní a zvolte **odstranit**.

## <a name="split-a-test-method-into-two-separate-methods"></a>Testovací metoda rozdělit do dvou samostatných metod

Testovací metoda, pro upřesnění nebo modularizaci akce uživatelského rozhraní můžete rozdělit. Například test může mít jeden testovací metodou akce uživatelského rozhraní ve dvou ovládacích prvků kontejneru. Akce uživatelského rozhraní může být lepší modulární v dvě metody, které odpovídají jeden kontejner.

![Split – metoda test](../test/media/codeduitestsplitmethod1.png)

![Dva testovací metody](../test/media/codeduitestsplitmethod2.png)

V **akce uživatelského rozhraní** podokně rozbalte položku testovací metoda, kterou chcete rozdělit do dvou samostatných metod a výběr akce uživatelského rozhraní, kde chcete začít novou testovací metodu. Buď otevřete místní nabídku pro akce uživatelského rozhraní a klikněte na tlačítko **rozdělit na novou metodu**, nebo zvolte **rozdělit na novou metodu** tlačítko na panelu nástrojů editoru programového testu UI. Nové metody testu se zobrazí v **akce uživatelského rozhraní** podokně. Obsahuje akce uživatelského rozhraní od akce, ve kterém jste zadali rozdělení.

Po dokončení rozdělení metodu, uložte změny *UIMap.Designer* soubor výběrem **Uložit** na panelu nástrojů sady Visual Studio.

> [!WARNING]
> Pokud rozdělíte metodu, je třeba upravit jakýkoli kód, který volá metodu existující také zavolat novou metodu, kterou se chystáte vytvořit, pokud chcete i tyto akce uživatelského rozhraní, které jsou zahrnuty. Pokud rozdělíte metodu, zobrazí se dialogové okno sady Microsoft Visual Studio. Upozorňuje vás, že je třeba upravit jakýkoli kód, který volá metodu existující také zavolat novou metodu, kterou se chystáte vytvořit. Zvolte **Ano**.

### <a name="tips"></a>Tipy

- Chcete-li zrušit rozdělení, zvolte **zpět** z **upravit** nabídky nebo stisknutím klávesy **Ctrl**+**Z**.

- Nové metody, můžete přejmenovat. Vyberte ho v **akce uživatelského rozhraní** podokně a zvolte **přejmenovat** tlačítko na panelu nástrojů editoru programového testu UI.

   -nebo-

   Otevřete místní nabídku pro nové testovací metoda a zvolte možnost **přejmenovat**.

   Zobrazí se dialogové okno aplikace Microsoft Visual Studio. Upozorňuje vás, že je třeba upravit jakýkoli kód, který odkazuje na metodu. Zvolte **Ano**.

## <a name="move-a-test-method-to-the-uimap-file-to-facilitate-customization"></a>Přesunout testovací metodu do souboru UIMap za účelem usnadnění přizpůsobení

Pokud zjistíte, že jedna z testovacích metod v kódované UI test vyžaduje vlastní kód, je nutné přesunout do buď *UIMap.cs* nebo *UIMap.vb* souboru. V opačném případě kódu budou přepsány pokaždé, když se znovu zkompiluje programový test uživatelského rozhraní. Pokud přesunete není metodu, váš vlastní kód, budou přepsány pokaždé, když test přepsán.

V **akce uživatelského rozhraní** podokně, vyberte testovací metody, kterou chcete přesunout *UIMap.cs* nebo *UIMap.vb* soubor pro usnadnění funkce vlastního kódu, který nedojde k přepsání Pokud testovací kód přepsán. V dalším kroku vyberte **přesunout kód** tlačítko na panelu nástrojů editoru programového testu UI nebo otevřete místní nabídku pro metodu testování a zvolte **přesunout kód**. Testovací metoda je odebrána z *UIMap.uitest* souboru a už nebude zobrazovat v **akce uživatelského rozhraní** podokně. Chcete-li upravit přesunutý soubor testu, otevřete *UIMap.cs* nebo *UIMap.vb* souboru z **Průzkumníka řešení**.

Po dokončení přesunutí metody, uložit změny *UIMap.Designer* soubor výběrem **Uložit** na panelu nástrojů sady Visual Studio.

> [!WARNING]
> Po přesunutí metody můžete nadále upravovat pomocí editoru programového testu UI. Musíte přidat vlastní kód a spravovat jej pomocí Editoru kódu. Při přesunutí metody se zobrazí dialogové okno sady Microsoft Visual Studio. Upozorňuje vás, že metoda bude přesunuta ze *UIMap.uitest* do souboru *UIMap.cs* nebo *UIMap.vb* Souborová služba a že se už budete moci upravit pomocí metody Editor programového testu UI. Zvolte **Ano**.

### <a name="tips"></a>Tipy

K přechodu zpět, vyberte **zpět** z **upravit** nabídky nebo stisknutím klávesy **Ctrl**+**Z**. Ale musíte pak ručně odebrat kód z *UIMap.cs* nebo *UIMap.vb* souboru.

## <a name="locate-a-ui-control-in-the-application-under-test"></a>Vyhledejte v testované aplikaci prvku uživatelského rozhraní

V některých případech může být obtížné vizualizovat, kde jsou umístěny ovládací prvky v uživatelském rozhraní aplikace v rámci testu. Jednou z možností editoru programového testu uživatelského rozhraní je, že můžete vybrat ovládací prvek, který je uvedený v mapování ovládacího prvku uživatelského rozhraní a zobrazit jeho umístění v testované aplikaci. Použití **vyhledejte ovládací prvek uživatelského rozhraní** funkce na testovanou aplikaci lze také ověřit hledání vlastnost změny provedené na ovládací prvek.

![Vyhledejte ovládací prvek uživatelského rozhraní](../test/media/codeduilocatecontrol.png)

![Ovládací prvek umístěný v testované aplikaci](../test/media/codeduilocatecontrol2.png)

V **mapování ovládacího prvku UI** podokně, vyberte ovládací prvek, který chcete vyhledat v aplikace přidružené k testu. Dále otevřete místní nabídku pro ovládací prvek a pak zvolte **vyhledejte ovládací prvek uživatelského rozhraní**. V aplikaci, která je právě testováno je určen ovládací prvek s modrým ohraničením.

> [!NOTE]
> Předtím, než můžete vyhledat ovládací prvek uživatelského rozhraní, ověřte, zda je spuštěna aplikace spojené s testem.

### <a name="tips"></a>Tipy

Můžete použít **vyhledejte všechny** možnost ověřit, že všechny ovládací prvky v rámci kontejneru může být správně umístěný. Tato možnost je popsaná v další části.

## <a name="locate-a-control-and-its-descendants"></a>Vyhledejte ovládací prvek a jejích potomků

Můžete ověřit, že všechny ovládací prvky v rámci kontejneru může být správně umístěn v uživatelském rozhraní aplikace v rámci testu. To může být užitečné při ověřování hledání vlastnost provedené změny mohou mít ke kontejneru. Kromě toho v uživatelském rozhraní aplikace v rámci testu byly významné změny, můžete ověřit, že jsou stále správné existující vlastnosti hledání ovládacího prvku.

![Vyhledání všech potomků ovládacích prvků](../test/media/codeduilocateall.png)

![Všechny ovládací prvky umístěné](../test/media/codeduilocateall2.png)

V **mapování ovládacího prvku UI** podokně, vyberte ovládací prvek kontejneru, který chcete vyhledat a zobrazit všechny následníky pro. Dále otevřete místní nabídku pro ovládací prvek a vyberte **vyhledejte všechny**. Ovládací prvek kontejneru a všech jeho podřízených ovládacích prvků, jsou označeny v editoru programového testu UI s zelená značka zaškrtnutí nebo red "X". Tyto značky umožňují vědět, pokud ovládací prvky byly úspěšně umístěny v testované aplikaci.

> [!NOTE]
> Před vyhledávání ovládacích prvků uživatelského rozhraní, ověřte, zda je spuštěna aplikace spojené s testem.

## <a name="insert-a-delay-before-a-ui-action"></a>Vložení prodlevy před akci uživatelského rozhraní

V některých případech můžete chtít provést test čekání na určité události pravděpodobnější, jako je okno se zobrazí indikátor průběhu zmizí a tak dále. Pomocí editoru programového testu uživatelského rozhraní, lze provést pomocí vložení prodlevy před akci uživatelského rozhraní. Můžete určit, kolik sekund má zpoždění, aby.

![Vložit zpoždění před akci uživatelského rozhraní](../test/media/codeduidelay.png)

![Zpoždění přidána s 5 sekund](../test/media/codeduidealy2.png)

V **akce uživatelského rozhraní** podokně rozbalte položku testovací metoda, která obsahuje akce uživatelského rozhraní, který chcete vložit zpoždění před. Výběr akce uživatelského rozhraní. Dále otevřete místní nabídku pro akce uživatelského rozhraní a zvolte **vložit zpoždění před**. Zpoždění při vkládání a zvýrazněná, před vybrané akce uživatelského rozhraní s následujícím textem: **vyčkat, než 1 sekundy pro zpoždění uživatele mezi akcemi**. V **vlastnosti** okna, změňte hodnotu **zpoždění** vlastnost na požadovanou dobu v milisekundách.

Po dokončení vkládání zpoždění, uložte změny *UIMap.Designer* soubor výběrem **Uložit** na panelu nástrojů sady Visual Studio.

Pokud je potřeba zajistit, že určitý ovládací prvek je k dispozici před akci uživatelského rozhraní, měli byste zvážit přidání vlastního kódu pro testovací metodu pomocí odpovídající metody UITestControl.WaitForControlXXX(). Další informace najdete v tématu [vytváření uživatelského rozhraní čekání programových testů konkrétní události při přehrávání](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md).

## <a name="see-also"></a>Viz také:

- [Použití automatizace uživatelského rozhraní k testování kódu](../test/use-ui-automation-to-test-your-code.md)
- [Vytvoření programové testy uživatelského rozhraní](../test/use-ui-automation-to-test-your-code.md)
- [Vytvoření datově řízeného programového testu UI](../test/creating-a-data-driven-coded-ui-test.md)
- [Návod: Vytváření, úpravy a údržba programového uživatelského rozhraní testu](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)