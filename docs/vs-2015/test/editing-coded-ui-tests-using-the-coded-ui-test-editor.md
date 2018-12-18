---
title: Úpravy programových testů UI pomocí editoru testů kódované UI | Dokumentace Microsoftu
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
- vs.codedUItest.testeditor
helpviewer_keywords:
- coded UI test, Coded UI Test Editor
ms.assetid: 76435c4b-593e-43a3-a9fe-709a7f9f5e0f
caps.latest.revision: 42
ms.author: gewarren
manager: douge
ms.openlocfilehash: 1bf24c24a60a37fd8fc5859d216c34eaa2e9b4f8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49951254"
---
# <a name="editing-coded-ui-tests-using-the-coded-ui-test-editor"></a>Úpravy programových testů uživatelského rozhraní pomocí Editoru programových testů uživatelského rozhraní
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Editor programového testu uživatelského rozhraní umožňuje snadno upravovat programové testy uživatelského rozhraní. Použití editoru programového testu UI, můžete vyhledat, zobrazit a upravit vlastnosti testovací metody a akce uživatelského rozhraní. Kromě toho můžete použít v mapování ovládacího prvku uživatelského rozhraní k zobrazení a jejich odpovídající ovládacích prvcích pro úpravy.  
  
 **Požadavky**  
  
-   Visual Studio Enterprise  
  
## <a name="why-should-i-do-this"></a>Proč to mám dělat?  
 Použití editoru programového testu UI je rychlejší a efektivnější než úpravy kódu v programových testovací metody uživatelského rozhraní pomocí editoru kódu. Se editoru programového testu UI, můžete použít nástrojů a v místní nabídky rychle vyhledat a upravte hodnoty vlastností související s ovládacími prvky a akce uživatelského rozhraní. Například můžete použít editoru programového testu UI pro panel nástrojů k provedení následujících příkazů:  
  
 ![Edito Test uživatelského rozhraní](../test/media/uitesteditor.png "UITestEditor")  
  
1.  [Najít](../ide/finding-and-replacing-text.md) pomáhá při hledání akce uživatelského rozhraní a ovládací prvky.  
  
2.  [Odstranit](#CodedUITestEditor_DeleteUIActions) odebere nežádoucích akcí uživatelského rozhraní.  
  
3.  **Přejmenovat** změní názvy pro testovací metody a ovládací prvky.  
  
4.  **Vlastnosti** se otevře okno Vlastnosti pro vybranou položku.  
  
5.  [Rozdělit na novou metodu](#CodedUITestEditor_SplitMethods) umožňuje modularizaci akce uživatelského rozhraní.  
  
6.  [Přesunout kód](#CodedUITestEditor_MoveMethods) přidá vlastní kód testovací metody.  
  
7.  [Vložit zpoždění před](#CodedUITestEditor_InsertDelay) přidá pozastavení před akci uživatelského rozhraní, zadává v milisekundách.  
  
8.  [Vyhledejte ovládací prvek uživatelského rozhraní](#CodedUITestEditor_LocateUIControl) Určuje umístění ovládacího prvku v uživatelském rozhraní aplikace v rámci testu.  
  
9. [Najít všechny](#CodedUITestEditor_LocateDecendants) ověříte pomáhá řídit vlastnost a významné změny na ovládací prvky vaší aplikace.  
  
## <a name="how-do-i-do-this"></a>Jak to udělám?  
 V [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], otevřením souboru UIMap.uitest přidruženého programového testu uživatelského rozhraní v projektu programového testu uživatelského rozhraní se automaticky zobrazí programový test uživatelského rozhraní v editoru programového testu UI. Následující postupy popisují, jak můžete poté vyhledejte a upravovat testovací metody a vlastnosti pro akce uživatelského rozhraní a ovládacích prvků pomocí editoru panelu nástrojů a nabídek.  
  
## <a name="open-a-coded-ui-test"></a>Spustit programový test uživatelského rozhraní  
 Můžete zobrazit a upravit vaše Visual C# a Visual Basic založena programových testů UI pomocí editoru programového testu UI.  
  
 ![Kontextové nabídky upravit pomocí Tvůrce programového testu UI](../test/media/editcodeduitest.png "EditCodedUITest")  
  
 V Průzkumníku řešení otevřete místní nabídku pro **UIMap.uitest** a zvolte **otevřete**. Programový test uživatelského rozhraní se zobrazí v Editoru programového testu uživatelského rozhraní. Nyní můžete zobrazit a upravit nahrané metody, akce a odpovídající ovládací prvky v programovém testu uživatelského rozhraní.  
  
> [!TIP]
>  Když vyberete akci uživatelského rozhraní, který je umístěný v metodě v **akce uživatelského rozhraní** podokně odpovídající ovládací prvek je zvýrazněn. Můžete také upravit akce uživatelského rozhraní nebo vlastností ovládacích prvků.  
  
 *Nevidím* Editor programového testu uživatelského rozhraní.  
 Pravděpodobně používáte verzi sady Visual Studio Enterprise před 2012. Editor programového testu uživatelského rozhraní se také k dispozici v sadě Visual Studio 2010 funkce aktualizací Service Pack 2 s předplatným MSDN. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Microsoft Visual Studio 2010 Feature Pack 2](http://go.microsoft.com/fwlink/?LinkID=204119).  
  
##  <a name="CodedUITestEditor_EditActionAndControlProperties"></a> Úprava vlastností akce uživatelského rozhraní a jejich odpovídající vlastnosti ovládacích prvků  
 Pomocí editoru programového testu UI, můžete rychle najít a zobrazit všechny akce uživatelského rozhraní ve vašich testovacích metodách. Při výběru akce uživatelského rozhraní v editoru je zvýrazněn automaticky odpovídající ovládací prvek. Podobně pokud vyberete ovládací prvek, jsou zvýrazněny přidružené akce uživatelského rozhraní. Když vyberete akci uživatelského rozhraní nebo ovládacího prvku, je pak snadno použitelné v okně Vlastnosti k úpravě vlastností, které odpovídají s ním.  
  
 ![Vlastností akce uživatelského rozhraní](../test/media/codeduiedituiaction.png "CodedUIEditUIAction")  
Úpravy vlastností akce uživatelského rozhraní  
  
 Úpravy vlastností akce uživatelského rozhraní v **akce uživatelského rozhraní** podokně rozbalte položku testovací metoda, která obsahuje akce uživatelského rozhraní, který chcete upravit vlastnosti pro vybrané akce uživatelského rozhraní a potom upravte vlastnosti pomocí okna Vlastnosti.  
  
 Například pokud server není k dispozici a máte akce uživatelského rozhraní související s webovým prohlížečem, který uvádí **přejít na webovou stránku "<http://Contoso1/default.aspx’>**, můžete změnit adresu URL `‘http://Contoso2/default.aspx’`.  
  
 ![Vlastnosti ovládacího prvku](../test/media/codeduitestcontrolprop.png "CodedUITestControlProp")  
Úpravy vlastností ovládacích prvků  
  
 Úprava vlastností pro ovládací prvek se provádí stejným způsobem jako akce uživatelského rozhraní. V **mapování ovládacího prvku UI** podokně, vyberte ovládací prvek, který chcete upravit a změnit jeho vlastnosti v okně Vlastnosti.  
  
 Například vývojář změnil **(ID)** vlastnosti u ovládacího prvku tlačítko ve zdrojovém kódu aplikace testovány z "idSubmit" k "idLogin." S **(ID)** vlastnost změněn v aplikaci, programový test uživatelského rozhraní nebude možné najít ovládací prvek tlačítko a se nezdaří. V takovém případě můžete otevřít tester **vlastnosti hledání** kolekce a změnit **Id** vlastnost tak, aby odpovídala nové hodnoty, které vývojář používaných v aplikaci. Tester může změnit také **popisný název** hodnoty vlastnosti z "Odeslat" "Login". Touto změnou přidružené akce uživatelského rozhraní v uživatelském rozhraní editoru programového testu je aktualizováno z hodnoty "Vyberte"Odeslat"button" na "Vyberte"Přihlášení"tlačítko."  
  
 Po dokončení provedené změny, uložte změny do souboru UIMap.Designer výběrem **Uložit** na [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nástrojů.  
  
 *Co dalšího mohu vědět?*  
 **Tipy**  
  
-   ![Tip](../test/media/tip.png "Tip") Pokud se nezobrazí v okně Vlastnosti, stiskněte a podržte **Alt** při stisknutí klávesy **Enter**, nebo také stisknout klávesu **F4**.  
  
-   ![Tip](../test/media/tip.png "Tip") Pokud chcete vrátit zpět provedené změny vlastností, vyberte **zpět** z **upravit** nabídky nebo stisknutím klávesy Ctrl + Z.  
  
-   ![Tip](../test/media/tip.png "Tip") můžete použít **najít** tlačítko v panelu nástrojů editoru programového testu uživatelského rozhraní v sadě Visual Studio otevřete nástroj Najít a nahradit. Potom můžete ovládacího prvku Find najít akce uživatelského rozhraní v editoru programového testu UI. Například můžete zkusit najít "klikněte na tlačítko"Přihlášení"." To může být užitečné v testech velké. Mějte na paměti, že nemohou používat funkce nahradit v nástroji Najít a nahradit v editoru programového testu UI. Další informace najdete v tématu najít v ovládacím prvku [hledání a nahrazení textu](../ide/finding-and-replacing-text.md).  
  
-   ![Tip](../test/media/tip.png "Tip") v některých případech může být obtížné vizualizovat, kde jsou umístěny ovládací prvky v uživatelském rozhraní aplikace v rámci testu. Jednou z možností editoru programového testu uživatelského rozhraní je, že můžete vybrat ovládací prvek, který je uvedený v mapování ovládacího prvku uživatelského rozhraní a zobrazit jeho umístění v testované aplikaci. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Vyhledávání ovládacího prvku uživatelského rozhraní v testované aplikaci](#CodedUITestEditor_LocateUIControl) najít další níže v tomto tématu.  
  
-   ![Tip](../test/media/tip.png "Tip") bude pravděpodobně nutné rozšířit ovládací prvek kontejneru, který obsahuje ovládací prvek, který chcete upravit. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Vyhledávání ovládacího prvku a jeho následníky](#CodedUITestEditor_LocateDecendants) najít další níže v tomto tématu.  
  
##  <a name="CodedUITestEditor_DeleteUIActions"></a> Odstranění nežádoucích akcí uživatelského rozhraní  
 Můžete snadno odebrat nežádoucích akcí uživatelského rozhraní programového testu UI.  
  
 ![Odstranění akce uživatelského rozhraní](../test/media/codeduideleteuiaction.png "CodedUIDeleteUIAction")  
  
 V **akce uživatelského rozhraní** podokně rozbalte položku testovací metoda, která obsahuje akce uživatelského rozhraní, který chcete odstranit. Otevřete místní nabídku pro akce uživatelského rozhraní a zvolte **odstranit**.  
  
##  <a name="CodedUITestEditor_SplitMethods"></a> Testovací metoda rozdělit do dvou samostatných metod  
 Testovací metoda, pro upřesnění nebo modularizaci akce uživatelského rozhraní můžete rozdělit. Například test může mít jeden testovací metodou akce uživatelského rozhraní ve dvou ovládacích prvků kontejneru. Akce uživatelského rozhraní může být lepší modulární v dvě metody, které odpovídají jeden kontejner.  
  
 ![Testovací metoda Splt](../test/media/codeduitestsplitmethod1.png "CodedUITestSplitMethod1")  
  
 ![Testování dvě metody](../test/media/codeduitestsplitmethod2.png "CodedUITestSplitMethod2")  
  
 V **akce uživatelského rozhraní** podokně rozbalte položku testovací metoda, kterou chcete rozdělit do dvou samostatných metod a výběr akce uživatelského rozhraní, kde chcete začít novou testovací metodu. Buď otevřete místní nabídku pro akce uživatelského rozhraní a klikněte na tlačítko **rozdělit na novou metodu**, nebo zvolte **rozdělit na novou metodu** tlačítko na panelu nástrojů editoru programového testu UI. Nové metody testu se zobrazí v podokně Akce uživatelského rozhraní. Obsahuje akce uživatelského rozhraní od akce, ve kterém jste zadali rozdělení.  
  
 Po dokončení rozdělení metodu, uložte změny do souboru UIMap.Designer výběrem **Uložit** na [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nástrojů.  
  
 *Co dalšího mohu vědět?*  
 **Důležité problémy**  
  
- ![Ikona upozornění](../test/media/caution.gif "upozornění") **upozornění:** Pokud rozdělíte metodu, je nutné upravit veškerý kód, který volá metodu existující také volání nové metody, které se chystáte vytvořit, pokud chcete i tyto uživatelského rozhraní akce zahrnuté. Pokud rozdělíte metodu, zobrazí se dialogové okno sady Microsoft Visual Studio. Upozorňuje vás, že je třeba upravit jakýkoli kód, který volá metodu existující také zavolat novou metodu, kterou se chystáte vytvořit. Zvolte **Ano**.  
  
  **Tipy**  
  
- ![Tip](../test/media/tip.png "Tip") zrušit rozdělení, zvolte **zpět** z **upravit** nabídky nebo stisknutím klávesy Ctrl + Z.  
  
- ![Tip](../test/media/tip.png "Tip") přejmenujete nové metody. Vyberte v podokně Akce uživatelského rozhraní a zvolte **přejmenovat** tlačítko na panelu nástrojů editoru programového testu UI.  
  
   -nebo-  
  
   Otevřete místní nabídku pro nové testovací metoda a zvolte možnost **přejmenovat**.  
  
   Zobrazí se dialogové okno aplikace Microsoft Visual Studio. Upozorňuje vás, že je třeba upravit jakýkoli kód, který odkazuje na metodu. Zvolte **Ano**.  
  
##  <a name="CodedUITestEditor_MoveMethods"></a> Přesunout testovací metodu do souboru UIMap za účelem usnadnění přizpůsobení  
 Pokud zjistíte, že jedna z testovacích metod v kódované UI test vyžaduje vlastní kód, musíte jej přesunout do souboru UIMap.cs nebo UIMap.vb. V opačném případě kódu budou přepsány pokaždé, když se znovu zkompiluje programový test uživatelského rozhraní. Pokud přesunete není metodu, váš vlastní kód, budou přepsány pokaždé, když test přepsán.  
  
 V **akce uživatelského rozhraní** podokně, vyberte testovací metody, kterou chcete přesunout do souboru UIMap.cs nebo UIMap.vb k usnadnění funkce vlastního kódu, který nebude při testovací kód je znovu zkompilovat. V dalším kroku vyberte **přesunout kód** tlačítko na panelu nástrojů editoru programového testu UI nebo otevřete místní nabídku pro metodu testování a zvolte **přesunout kód**. Testovací metoda je odebrána ze souboru UIMap.uitest a v podokně Akce uživatelského rozhraní se již nezobrazí. Chcete-li upravit přesunutý soubor testu, otevřete UIMap.cs nebo UIMap.vb souboru z Průzkumníku řešení.  
  
 Po dokončení přesunutí metody, uložte změny do souboru UIMap.Designer výběrem **Uložit** na [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nástrojů.  
  
 *Co dalšího mohu vědět?*  
 **Důležité problémy**  
  
- ![Ikona upozornění](../test/media/caution.gif "upozornění") **upozornění:** po přesunutí metody je nemůžete nadále upravovat pomocí editoru programového testu UI. Musíte přidat vlastní kód a spravovat jej pomocí Editoru kódu. Při přesunutí metody se zobrazí dialogové okno sady Microsoft Visual Studio. Upozorňuje vás, že metoda bude přesunuta ze souboru UIMap.uitest do UIMap.cs nebo UIMap.vb Souborová služba a který se již budete moci upravit metodu pomocí editoru programového testu UI. Zvolte **Ano**.  
  
  **Tipy**  
  
- ![Tip](../test/media/tip.png "Tip") vrácení přesunutí, vyberte **zpět** z **upravit** nabídky nebo stisknutím klávesy Ctrl + Z. Ale musíte pak ručně odebrat kód ze souboru UIMap.cs nebo UIMap.vb.  
  
##  <a name="CodedUITestEditor_LocateUIControl"></a> Vyhledávání ovládacího prvku uživatelského rozhraní v testované aplikaci  
 V některých případech může být obtížné vizualizovat, kde jsou umístěny ovládací prvky v uživatelském rozhraní aplikace v rámci testu. Jednou z možností editoru programového testu uživatelského rozhraní je, že můžete vybrat ovládací prvek, který je uvedený v mapování ovládacího prvku uživatelského rozhraní a zobrazit jeho umístění v testované aplikaci. Použití **vyhledejte ovládací prvek uživatelského rozhraní** funkce na testovanou aplikaci lze také ověřit hledání vlastnost změny provedené na ovládací prvek.  
  
 ![Vyhledejte ovládací prvek uživatelského rozhraní](../test/media/codeduilocatecontrol.png "CodedUILocateControl")  
  
 ![Ovládací prvek umístěný v testované aplikaci](../test/media/codeduilocatecontrol2.png "CodedUILocateControl2")  
  
 V **mapování ovládacího prvku UI** podokně, vyberte ovládací prvek, který chcete vyhledat v aplikace přidružené k testu. Dále otevřete místní nabídku pro ovládací prvek a pak zvolte **vyhledejte ovládací prvek uživatelského rozhraní**. V aplikaci, která je právě testováno je určen ovládací prvek s modrým ohraničením.  
  
 *Co dalšího mohu vědět?*  
 **Důležité problémy**  
  
- ![Ikona upozornění](../test/media/caution.gif "upozornění") **upozornění:** předtím, než můžete vyhledat ovládací prvek uživatelského rozhraní, ověřte, zda je spuštěna aplikace spojené s testem.  
  
  **Tipy**  
  
- ![Tip](../test/media/tip.png "Tip") Alternativně můžete použít **vyhledejte všechny** možnost ověřit, že všechny ovládací prvky v rámci kontejneru může být správně umístěný. Tato možnost je popsaná v další části.  
  
##  <a name="CodedUITestEditor_LocateDecendants"></a> Vyhledávání ovládacího prvku a jejích potomků  
 Můžete ověřit, že všechny ovládací prvky v rámci kontejneru může být správně umístěn v uživatelském rozhraní aplikace v rámci testu. To může být užitečné při ověřování hledání vlastnost provedené změny mohou mít ke kontejneru. Kromě toho v uživatelském rozhraní aplikace v rámci testu byly významné změny, můžete ověřit, že jsou stále správné existující vlastnosti hledání ovládacího prvku.  
  
 ![Vyhledejte všechny odvozené ovládací prvky](../test/media/codeduilocateall.png "CodedUILocateAll")  
  
 ![Všechny ovládací prvky umístěné](../test/media/codeduilocateall2.png "CodedUILocateAll2")  
  
 V **mapování ovládacího prvku UI** podokně, vyberte ovládací prvek kontejneru, který chcete vyhledat a zobrazit všechny následníky pro. Dále otevřete místní nabídku pro ovládací prvek a vyberte **vyhledejte všechny**. Ovládací prvek kontejneru a všech jeho podřízených ovládacích prvků, jsou označeny v editoru programového testu UI s zelená značka zaškrtnutí nebo red "X". Tyto značky umožňují vědět, pokud ovládací prvky byly úspěšně umístěny v testované aplikaci.  
  
 *Co dalšího mohu vědět?*  
 **Důležité problémy**  
  
-   ![Ikona upozornění](../test/media/caution.gif "upozornění") **upozornění:** před vyhledávání ovládacích prvků uživatelského rozhraní, ověřte, zda je spuštěna aplikace spojené s testem.  
  
##  <a name="CodedUITestEditor_InsertDelay"></a> Vložení prodlevy před akci uživatelského rozhraní  
 V některých případech můžete chtít provést test čekání na určité události pravděpodobnější, jako je okno se zobrazí indikátor průběhu zmizí a tak dále. Pomocí editoru programového testu uživatelského rozhraní, lze provést pomocí vložení prodlevy před akci uživatelského rozhraní. Můžete určit, kolik sekund má zpoždění, aby.  
  
 ![Vložit zpoždění před akci uživatelského rozhraní](../test/media/codeduidelay.png "CodedUIDelay")  
  
 ![Zpoždění přidána s 5 sekund](../test/media/codeduidealy2.png "CodedUIDealy2")  
  
 V **akce uživatelského rozhraní** podokně rozbalte položku testovací metoda, která obsahuje akce uživatelského rozhraní, který chcete vložit zpoždění před. Výběr akce uživatelského rozhraní. Dále otevřete místní nabídku pro akce uživatelského rozhraní a zvolte **vložit zpoždění před**. Zpoždění při vkládání a zvýrazněná, před vybrané akce uživatelského rozhraní s následujícím textem: **vyčkat, než 1 sekundy pro zpoždění uživatele mezi akcemi**. V okně Vlastnosti změňte hodnotu **zpoždění** vlastnost na požadovanou dobu v milisekundách.  
  
 Po dokončení vkládání zpoždění, uložte změny do souboru UIMap.Designer výběrem **Uložit** na [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nástrojů.  
  
 *Co dalšího mohu vědět?*  
 **Poznámky**  
  
- ![Prerequsite](../test/media/prereq.png "požadavky") Pokud je potřeba zajistit, že určitý ovládací prvek je k dispozici před akci uživatelského rozhraní, měli byste zvážit přidání vlastního kódu pro testovací metodu pomocí odpovídající UITestControl.WaitForControlXXX() Metoda. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Provádění kódované UI testy vyčkat, než konkrétní události při přehrávání](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md).  
  
  **Tipy**  
  
- ![Tip](../test/media/tip.png "Tip") Pokud se nezobrazí v okně Vlastnosti, stiskněte a podržte klávesu Alt při stisknutí klávesy Enter nebo alternativně stisknutím klávesy F4.  
  
## <a name="external-resources"></a>Externí zdroje  
  
### <a name="guidance"></a>Doprovodné materiály  
 [Testování pro nepřetržité dodávky s Visual Studio 2012 – kapitola 2: testování částí: testování uvnitř](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
### <a name="faq"></a>Nejčastější dotazy  
 [Programové testy UI – nejčastější dotazy – 1](http://go.microsoft.com/fwlink/?LinkID=230576)  
  
 [Programové testy UI – nejčastější dotazy -2](http://go.microsoft.com/fwlink/?LinkID=230578)  
  
### <a name="forum"></a>Fórum  
 [Visual Studio automatické testování uživatelského rozhraní (včetně CodedUI)](http://go.microsoft.com/fwlink/?LinkID=224497)  
  
## <a name="see-also"></a>Viz také  
 [Použití automatizace uživatelského rozhraní k testování kódu](../test/use-ui-automation-to-test-your-code.md)   
 [Vytváření programových testů UI](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)   
 [Vytvoření datově řízeného programového testu UI](../test/creating-a-data-driven-coded-ui-test.md)   
 [Generování programového testu UI ze stávajícího záznamu akcí](http://msdn.microsoft.com/library/56736963-9027-493b-b5c4-2d4e86d1d497)   
 [Návod: Vytváření, upravování a údržba programového testu UI](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)



