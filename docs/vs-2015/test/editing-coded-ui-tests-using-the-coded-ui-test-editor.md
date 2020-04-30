---
title: Úpravy programových testů uživatelského rozhraní pomocí editoru programových testů UI | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
f1_keywords:
- vs.codedUItest.testeditor
helpviewer_keywords:
- coded UI test, Coded UI Test Editor
ms.assetid: 76435c4b-593e-43a3-a9fe-709a7f9f5e0f
caps.latest.revision: 42
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c070f1bafb157e3979eb9c1f49b317b17807f1e7
ms.sourcegitcommit: da5ebc29544fdbdf625ab4922c9777faf2bcae4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/29/2020
ms.locfileid: "82586996"
---
# <a name="editing-coded-ui-tests-using-the-coded-ui-test-editor"></a>Úpravy programových testů uživatelského rozhraní pomocí Editoru programových testů uživatelského rozhraní
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Editor programového testu UI umožňuje snadno upravit kódované testy uživatelského rozhraní. Pomocí editoru programového testu UI můžete vyhledat, zobrazit a upravit vlastnosti testovacích metod a akcí uživatelského rozhraní. Kromě toho můžete použít mapu ovládacího prvku uživatelského rozhraní k zobrazení a úpravě odpovídajících ovládacích prvků.

 **Požadavky**

- Visual Studio Enterprise

## <a name="why-should-i-do-this"></a>Proč to mám udělat?
 Použití editoru programového testu UI je rychlejší a efektivnější než úprava kódu v metodách programového testu UI pomocí editoru kódu. Pomocí editoru programového testu UI můžete pomocí panelů nástrojů a místních nabídek rychle vyhledat a upravit hodnoty vlastností přidružené k akcím a ovládacím prvkům uživatelského rozhraní. Například můžete použít panel nástrojů editoru programového testu UI k provedení následujících příkazů:

 ![Edito testu uživatelského rozhraní](../test/media/uitesteditor.png "UITestEditor")

1. [Hledání](../ide/finding-and-replacing-text.md) vám pomůže najít akce a ovládací prvky uživatelského rozhraní.

2. [Odstranit](#CodedUITestEditor_DeleteUIActions) odebere nechtěné akce uživatelského rozhraní.

3. **Přejmenování** změní názvy testovacích metod a ovládacích prvků.

4. **Vlastnosti** otevře okno Vlastnosti pro vybranou položku.

5. [Rozdělení na novou metodu](#CodedUITestEditor_SplitMethods) vám umožní naplánovat modularizaci akce uživatelského rozhraní.

6. [Přesunutí kódu](#CodedUITestEditor_MoveMethods) přidá vlastní kód do testovacích metod.

7. [Vložení prodlevy před](#CodedUITestEditor_InsertDelay) přidáním pauzy před akcí uživatelského rozhraní, které je zadáno v milisekundách.

8. [Vyhledání ovládacího prvku uživatelského rozhraní](#CodedUITestEditor_LocateUIControl) identifikuje umístění ovládacího prvku v uživatelském rozhraní testované aplikace.

9. [Vyhledat vše](#CodedUITestEditor_LocateDecendants) vám pomůže ověřit vlastnost ovládacího prvku a významné změny ovládacích prvků aplikace.

## <a name="how-do-i-do-this"></a>Jak to udělám?
 V [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]nástroji otevření souboru UIMap. UITest přidruženého k zakódovanému testu uživatelského rozhraní v projektu programového testu UI se automaticky zobrazí programový test uživatelského rozhraní v editoru programového testu UI. Následující postupy popisují, jak můžete vyhledat a upravit testovací metody a vlastnosti pro akce uživatelského rozhraní a ovládací prvky pomocí panelu nástrojů a místních nabídek editoru.

## <a name="open-a-coded-ui-test"></a>Otevření programového testu uživatelského rozhraní
 Pomocí editoru programového testu UI můžete zobrazit a upravit programový test UI založený na jazyce Visual C# a Visual Basic.

 ![Místní nabídka upravit pomocí Tvůrce programového testu uživatelského rozhraní](../test/media/editcodeduitest.png "EditCodedUITest")

 V Průzkumník řešení otevřete místní nabídku pro **UIMap. UITest** a klikněte na **otevřít**. Programový test uživatelského rozhraní se zobrazí v Editoru programového testu uživatelského rozhraní. Nyní můžete zobrazit a upravit zaznamenané metody, akce a odpovídající ovládací prvky v programovém testu uživatelského rozhraní.

> [!TIP]
> Když vyberete akci uživatelského rozhraní, která je umístěna v metodě v podokně **akce uživatelského rozhraní** , je zvýrazněn odpovídající ovládací prvek. Můžete také upravit akci uživatelského rozhraní nebo vlastnosti ovládacích prvků.

 *Nevidím* Editor programového testu UI.
Je možné, že používáte verzi Visual Studio Enterprise před 2012. Editor programového testu uživatelského rozhraní byl také k dispozici v sadě Visual Studio 2010 Feature Pack 2 s předplatným MSDN. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Microsoft Visual Studio 2010 Feature Pack 2](https://msdn.microsoft.com/library/gg269474.aspx).

## <a name="modify-ui-action-properties-and-their-corresponding-control-properties"></a><a name="CodedUITestEditor_EditActionAndControlProperties"></a>Úprava vlastností akce uživatelského rozhraní a jejich odpovídajících vlastností ovládacích prvků
 Pomocí editoru programového testu UI můžete rychle najít a zobrazit všechny akce uživatelského rozhraní v testovacích metodách. Když vyberete akci uživatelského rozhraní v editoru, odpovídající ovládací prvek se automaticky zvýrazní. Podobně pokud vyberete ovládací prvek, jsou zvýrazněny související akce uživatelského rozhraní. Když vyberete akci uživatelského rozhraní nebo ovládací prvek, je pak snadné použít okno Vlastnosti pro úpravu vlastností, které s ním odpovídají.

 ![Vlastnosti akce uživatelského rozhraní](../test/media/codeduiedituiaction.png "CodedUIEditUIAction") Upravit vlastnosti akce uživatelského rozhraní

 Chcete-li upravit vlastnosti akce uživatelského rozhraní, v podokně **akce uživatelského rozhraní** rozbalte testovací metodu obsahující akci uživatelského rozhraní, pro kterou chcete upravit vlastnosti, vyberte akci uživatelského rozhraní a pak upravte vlastnosti pomocí okno Vlastnosti.

 Například pokud server není k dispozici a máte přidruženou akci uživatelského rozhraní k webovému prohlížeči, který uvádí stav **Přejít na webovou stránku<http://Contoso1/default.aspx’>**, můžete změnit adresu URL na. `‘http://Contoso2/default.aspx’`

 ![Vlastnosti ovládacího prvku](../test/media/codeduitestcontrolprop.png "CodedUITestControlProp") Upravit vlastnosti ovládacího prvku

 Změna vlastností ovládacího prvku se provádí stejným způsobem jako akce uživatelského rozhraní. V podokně **Mapa ovládacího prvku uživatelského rozhraní** vyberte ovládací prvek, který chcete upravit, a upravte jeho vlastnosti pomocí okno Vlastnosti.

 Vývojář například mohl změnit vlastnost **(ID)** na ovládacím prvku tlačítko ve zdrojovém kódu pro aplikaci, která je testována z "idSubmit" na "idLogin". V aplikaci se změnila vlastnost **(ID)** , Programový test uživatelského rozhraní nebude moci najít ovládací prvek tlačítko a nebude úspěšný. V tomto případě může tester otevřít kolekci **Vlastnosti hledání** a změnit vlastnost **ID** tak, aby odpovídala nové hodnotě, kterou vývojář v aplikaci použil. Tester může také změnit hodnotu vlastnosti **popisného názvu** z "Odeslat" na "login". Díky této změně se přidružená akce uživatelského rozhraní v editoru programového testu uživatelského rozhraní aktualizuje z příkazu "Odeslat tlačítko" na "zvolit" tlačítko Login.

 Po dokončení úprav uložte změny do souboru UIMap. Designer kliknutím na [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] tlačítko **Uložit** na panelu nástrojů.

 *Co dalšího mám vědět?*
 **Tip**

- ![Tip](../test/media/tip.png "Tip") Pokud se okno Vlastnosti nezobrazí, stiskněte a podržte klávesu **ALT** , stiskněte klávesu **ENTER**nebo stiskněte klávesu **F4**.

- ![Tip](../test/media/tip.png "Tip") Provedené změny vlastností vrátíte zpět výběrem možnosti **zpět** v nabídce **Úpravy** nebo stisknutím kombinace kláves CTRL + Z.

- ![Tip](../test/media/tip.png "Tip") K otevření nástroje najít a nahradit v sadě Visual Studio můžete použít tlačítko **Najít** na panelu nástrojů editoru programového testu UI. Pak můžete pomocí ovládacího prvku hledání vyhledat akci uživatelského rozhraní v editoru programového testu UI. Například se můžete pokusit najít kliknutím na tlačítko Login. To může být užitečné při velkých testech. Všimněte si, že v editoru programového testu UI nelze použít funkci nahrazení v nástroji najít a nahradit. Další informace najdete v tématu Vyhledání ovládacího prvku při [hledání a nahrazování textu](../ide/finding-and-replacing-text.md).

- ![Tip](../test/media/tip.png "Tip") V některých případech může být obtížné vizualizovat, kde jsou ovládací prvky umístěny v uživatelském rozhraní testované aplikace. Jednou z možností Editoru programového testu UI je, že můžete vybrat ovládací prvek uvedený v mapě ovládacího prvku uživatelského rozhraní a zobrazit jeho umístění v testované aplikaci. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Vyhledání ovládacího prvku uživatelského rozhraní v testované aplikaci](#CodedUITestEditor_LocateUIControl) , které najdete dále v tomto tématu.

- ![Tip](../test/media/tip.png "Tip") Může být nutné rozšířit ovládací prvek kontejneru, který obsahuje ovládací prvek, který chcete upravit. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Vyhledání ovládacího prvku a jeho následníků](#CodedUITestEditor_LocateDecendants) umístěných níže v tomto tématu.

## <a name="delete-unwanted-ui-actions"></a><a name="CodedUITestEditor_DeleteUIActions"></a>Odstranit nechtěné akce uživatelského rozhraní
 Můžete snadno odebrat nechtěné akce uživatelského rozhraní v programovém testu uživatelského rozhraní.

 ![Akce odstranění uživatelského rozhraní](../test/media/codeduideleteuiaction.png "CodedUIDeleteUIAction")

 V podokně **akce uživatelského rozhraní** rozbalte testovací metodu obsahující akci uživatelského rozhraní, kterou chcete odstranit. Otevřete místní nabídku pro akci uživatelského rozhraní a vyberte možnost **Odstranit**.

## <a name="split-a-test-method-into-two-separate-methods"></a><a name="CodedUITestEditor_SplitMethods"></a>Rozdělení testovací metody do dvou samostatných metod
 Můžete rozdělit testovací metodu pro upřesnění nebo pro naplánovat modularizacií akcí uživatelského rozhraní. Například váš test může mít jedinou testovací metodu s akcemi uživatelského rozhraní ve dvou ovládacích prvcích kontejneru. Akce uživatelského rozhraní mohou být lépe modulární ve dvou metodách, které odpovídají jednomu kontejneru.

 ![Splt testovací metodu](../test/media/codeduitestsplitmethod1.png "CodedUITestSplitMethod1")

 ![Dvě testovací metody](../test/media/codeduitestsplitmethod2.png "CodedUITestSplitMethod2")

 V podokně **akce uživatelského rozhraní** rozbalte testovací metodu, kterou chcete rozdělit do dvou samostatných metod, a vyberte akci uživatelského rozhraní, kde chcete spustit novou metodu testu. Buď otevřete místní nabídku pro akci uživatelského rozhraní a zvolte možnost **rozdělit do nové metody**, nebo zvolte tlačítko rozdělit na **novou metodu** na panelu nástrojů editoru programového testu UI. Nová testovací metoda se zobrazí v podokně akce uživatelského rozhraní. Obsahuje akce uživatelského rozhraní od akce, kde jste určili rozdělení.

 Po dokončení rozdělení metody uložte změny do souboru UIMap. Designer kliknutím na [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] tlačítko **Uložit** na panelu nástrojů.

 *Co dalšího mám vědět?*
 **Důležité problémy**

- ![Caution icon](../test/media/caution.gif "Upozornění") **Upozornění** na ikonu upozornění: Pokud rozdělíte metodu, je třeba upravit jakýkoli kód, který volá existující metodu, aby také volal novou metodu, kterou vytváříte, pokud stále chcete tyto akce uživatelského rozhraní zahrnout. Při rozdělení metody se zobrazí dialogové okno Microsoft Visual Studio. Upozorňuje vás, že je nutné upravit jakýkoli kód, který volá existující metodu pro volání nové metody, kterou vytváříte. Vyberte **Ano**.

  **Tip**

- ![Tip](../test/media/tip.png "Tip") Chcete-li rozdělení vrátit zpět, zvolte možnost **zpět** v nabídce **Úpravy** nebo stiskněte klávesy CTRL + Z.

- ![Tip](../test/media/tip.png "Tip") Novou metodu můžete přejmenovat. Vyberte ji v podokně akce uživatelského rozhraní a klikněte na tlačítko **Přejmenovat** na panelu nástrojů editoru programového testu UI.

   -nebo-

   Otevřete místní nabídku pro novou testovací metodu a vyberte možnost **Přejmenovat**.

   Zobrazí se dialogové okno aplikace Microsoft Visual Studio. Upozorňuje vás, že je nutné upravit jakýkoli kód, který odkazuje na metodu. Vyberte **Ano**.

## <a name="move-a-test-method-to-the-uimap-file-to-facilitate-customization"></a><a name="CodedUITestEditor_MoveMethods"></a>Přesunutí testovací metody do souboru UIMap, aby se usnadnilo přizpůsobení
 Pokud určíte, že jedna z vašich zkušebních metod v programovém testu UI vyžaduje vlastní kód, je nutné ji přesunout do souboru UIMap.cs nebo UIMap. vb. V opačném případě bude váš kód při každém překompilování kódovaného testu uživatelského rozhraní přepsán. Pokud tuto metodu nepřesunete, váš vlastní kód se přepíše pokaždé, když je test znovu zkompilován.

 V podokně **akce uživatelského rozhraní** vyberte testovací metodu, kterou chcete přesunout do souboru UIMap.cs nebo UIMap. vb, abyste usnadnili funkci vlastního kódu, která nebude přepsána při překompilování testovacího kódu. Dále klikněte na tlačítko **přesunout kód** na panelu nástrojů editoru programového testu UI nebo otevřete místní nabídku pro testovací metodu a vyberte možnost **přesunout kód**. Testovací metoda je odebrána ze souboru UIMap.uitest a v podokně Akce uživatelského rozhraní se již nezobrazí. Chcete-li upravit testovací soubor, který jste přesunuli, otevřete soubor UIMap.cs nebo UIMap. vb z Průzkumník řešení.

 Po dokončení přesunutí metody uložte změny do souboru UIMap. Designer kliknutím na [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] tlačítko **Uložit** na panelu nástrojů.

 *Co dalšího mám vědět?*
 **Důležité problémy**

- ![Caution icon](../test/media/caution.gif "Upozornění") **Upozornění** na ikonu upozornění: Pokud jste přepnuli metodu, nemůžete ji již upravovat pomocí editoru programového testu UI. Musíte přidat vlastní kód a spravovat jej pomocí Editoru kódu. Při přesunutí metody se zobrazí dialogové okno Microsoft Visual Studio. Upozorňuje vás, že metoda bude přesunuta ze souboru UIMap. UITest do souboru UIMap.cs nebo UIMap. vb a že již nebudete moci upravovat metodu pomocí editoru programového testu uživatelského rozhraní. Vyberte **Ano**.

  **Tip**

- ![Tip](../test/media/tip.png "Tip") Chcete-li zrušit přesun, vyberte možnost **zpět** v nabídce **Úpravy** nebo stiskněte klávesy CTRL + Z. Je však nutné ručně odebrat kód ze souboru UIMap.cs nebo UIMap. vb.

## <a name="locating-a-ui-control-in-the-application-under-test"></a><a name="CodedUITestEditor_LocateUIControl"></a>Vyhledání ovládacího prvku uživatelského rozhraní v testované aplikaci
 V některých případech může být obtížné vizualizovat, kde jsou ovládací prvky umístěny v uživatelském rozhraní testované aplikace. Jednou z možností Editoru programového testu UI je, že můžete vybrat ovládací prvek uvedený v mapě ovládacího prvku uživatelského rozhraní a zobrazit jeho umístění v testované aplikaci. Pomocí funkce **najít ovládací prvek uživatelského rozhraní** v testované aplikaci lze také použít k ověření úprav vlastností hledání, které jste provedli v ovládacím prvku.

 ![Vyhledat ovládací prvek uživatelského rozhraní](../test/media/codeduilocatecontrol.png "CodedUILocateControl")

 ![Ovládací prvek umístěný v testované aplikaci](../test/media/codeduilocatecontrol2.png "CodedUILocateControl2")

 V podokně **Mapa ovládacího prvku uživatelského rozhraní** vyberte ovládací prvek, který chcete najít v aplikaci přidružené k testu. Potom otevřete místní nabídku pro ovládací prvek a pak zvolte **najít ovládací prvek uživatelského rozhraní**. V testované aplikaci je ovládací prvek označený modrým ohraničením.

 *Co dalšího mám vědět?*
 **Důležité problémy**

- ![Caution icon](../test/media/caution.gif "Upozornění") **Upozornění** na ikonu upozornění: před UMÍSTĚNÍM ovládacího prvku uživatelského rozhraní ověřte, zda je aplikace přidružená k testu spuštěna.

  **Tip**

- ![Tip](../test/media/tip.png "Tip") Alternativně můžete použít možnost **Najít vše** a ověřit tak, že všechny ovládací prvky v kontejneru mohou být správně umístěny. Tato možnost je popsaná v následující části.

## <a name="locating-a-control-and-its-descendants"></a><a name="CodedUITestEditor_LocateDecendants"></a>Vyhledání ovládacího prvku a jeho následníků
 Můžete ověřit, že všechny ovládací prvky v kontejneru mohou být správně umístěny v uživatelském rozhraní testované aplikace. To může být užitečné při ověřování změn vlastností hledání, které jste mohli u kontejneru provést. Pokud se navíc v uživatelském rozhraní testované aplikace objevily významné změny, můžete ověřit, zda jsou stále správné vlastnosti hledání stávajících ovládacích prvků.

 ![Najít všechny podřízené ovládací prvky](../test/media/codeduilocateall.png "CodedUILocateAll")

 ![Všechny ovládací prvky umístěné](../test/media/codeduilocateall2.png "CodedUILocateAll2")

 V podokně **Mapa ovládacího prvku uživatelského rozhraní** vyberte ovládací prvek kontejneru, který chcete najít a zobrazit všechny následníky pro. Potom otevřete místní nabídku ovládacího prvku a vyberte **Najít vše**. Ovládací prvek kontejner a všechny jeho odvozené ovládací prvky jsou označeny v editoru programového testu UI buď zeleným zaškrtnutím, nebo červeným znakem "X". Tyto značky vám pomůžou zjistit, jestli se ovládací prvky úspěšně nacházely v testované aplikaci.

 *Co dalšího mám vědět?*
 **Důležité problémy**

- ![Caution icon](../test/media/caution.gif "Upozornění") **Upozornění** na ikonu upozornění: před UMÍSTĚNÍM ovládacích prvků uživatelského rozhraní ověřte, zda je aplikace přidružená k testu spuštěna.

## <a name="inserting-a-delay-before-a-ui-action"></a><a name="CodedUITestEditor_InsertDelay"></a>Vložení zpoždění před akci uživatelského rozhraní
 V některých případech můžete chtít, aby test čekal na výskyt určitých událostí, jako je okno, které se má zobrazit, indikátor průběhu zmizí a tak dále. Pomocí editoru programového testu UI můžete to provést vložením zpoždění před akci uživatelského rozhraní. Můžete zadat, kolik sekund má být zpoždění.

 ![Vložení zpoždění před akcí uživatelského rozhraní](../test/media/codeduidelay.png "CodedUIDelay")

 ![Zpoždění přidané s 5 sekundami](../test/media/codeduidealy2.png "CodedUIDealy2")

 V podokně **akce uživatelského rozhraní** rozbalte testovací metodu, která obsahuje akci uživatelského rozhraní, do které chcete vložit zpoždění. Vyberte akci uživatelského rozhraní. Dále otevřete místní nabídku pro akci uživatelského rozhraní a vyberte možnost **Vložit zpoždění před**. Je vložena a zvýrazněna prodleva před zvolenou akcí uživatelského rozhraní s následujícím textem: pro **prodlevu uživatele mezi akcemi počkejte 1 sekundy**. V okno Vlastnosti změňte hodnotu vlastnosti **Delay** na požadovaný počet milisekund.

 Po dokončení vkládání prodlevy uložte změny do souboru UIMap. Designer kliknutím na [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] tlačítko **Uložit** na panelu nástrojů.

 *Co dalšího mám vědět?*
 **Poznámky**

- ![Prerequsite](../test/media/prereq.png "Požadavků ohlásila") Pokud potřebujete zajistit, aby byl konkrétní ovládací prvek k dispozici před akcí uživatelského rozhraní, měli byste zvážit přidání vlastního kódu do testovací metody pomocí příslušné metody UITestControl. WaitForControlXXX (). [!INCLUDE[crdefault](../includes/crdefault-md.md)][Vytváření programových testů uživatelského rozhraní čeká na konkrétní události během přehrávání](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md).

  **Tip**

- ![Tip](../test/media/tip.png "Tip") Pokud se okno Vlastnosti nezobrazuje, stiskněte a podržte klávesu ALT, stiskněte klávesu ENTER nebo stiskněte klávesu F4.

## <a name="external-resources"></a>Externí zdroje

### <a name="guidance"></a>Doprovodné materiály
 [Testování pro průběžné doručování pomocí sady Visual Studio 2012 – Kapitola 2: testování částí: testování uvnitř](https://msdn.microsoft.com/library/jj159340.aspx)

### <a name="faq"></a>Nejčastější dotazy
 [Nejčastější dotazy k programovým testům UI – 1](https://docs.microsoft.com/archive/blogs/mathew_aniyan/content-index-for-coded-ui-test)

 [Nejčastější dotazy k programovým testům UI – 2](https://social.msdn.microsoft.com/Forums/en-US/vsautotest/thread/3a74dd2c-cef8-4923-abbf-7a91f489e6c4)

### <a name="forum"></a>Fórum
 [Testování automatizace uživatelského rozhraní sady Visual Studio (zahrnuje CodedUI)](https://social.msdn.microsoft.com/Forums/en-US/vsautotest)

## <a name="see-also"></a>Viz také
 [Použití automatizace uživatelského rozhraní k otestování kódu](../test/use-ui-automation-to-test-your-code.md) [vytváření](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate) programových testů UI Vytvoření programového testu UI založeného na [datech](../test/creating-a-data-driven-coded-ui-test.md) [generování kódovaného testu uživatelského rozhraní z existujícího návodu k záznamu akce](https://msdn.microsoft.com/library/56736963-9027-493b-b5c4-2d4e86d1d497) [: vytváření, úpravy a údržba programového testu UI](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
