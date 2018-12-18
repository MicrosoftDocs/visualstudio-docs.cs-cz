---
title: Spouštění aplikací pro Windows Phone v emulátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c7590788-beb3-403c-a7dd-18472a9e585e
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e7035e4a77b67fb5207f878c8e0650236afda7c6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51739976"
---
# <a name="run-windows-phone-apps-in-the-emulator"></a>Spouštění aplikací pro Windows Phone v emulátoru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Emulátor Windows Phone poskytuje virtualizované prostředí, ve kterém můžete ladění a testování aplikací pro Windows Phone v počítači bez fyzického zařízení. Můžete simulovat běžné touch a otočení události a zvolte velikost fyzické obrazovky a rozlišení, kterou chcete emulovat. Můžete také otestovat mnoho běžně používaných funkcí, jako je například umístění, sítí, oznámení, senzory, akcelerometr a volitelné SD karty.  
  
 Další informace o funkcích, které můžete testovat se spustila v emulátoru najdete v tématu [testování funkcí aplikace v emulátoru Windows Phone](http://msdn.microsoft.com/en-us/c1b2b0ec-b8cc-4a98-84c1-701428e45cb1).  
  
 Emulátor spolu s Visual Studio, poskytuje kompletní prostředí, ve kterém můžete návrh, vývoj, ladění a testování aplikací pro Windows Phone.  
  
##  <a name="BKMK_run"></a> Spuštění aplikace Windows Phone v emulátoru  
 Když vyvíjíte aplikace pro Windows Phone, můžete k nasazení a testování vaší aplikace rychle emulátoru Windows Phone. Doporučujeme vám, že provedete test aplikace skutečný zařízení Windows Phone, ale před publikujte aplikaci ve Store Windows Phone. Díky tomu můžete prostředí vaší aplikace, jak uživatelé budou moct používat ho.  
  
 Při spuštění aplikace Windows Phone v emulátoru Windows Phone poprvé, dojde k následujícím událostem:  
  
1. Spuštění emulátoru.  
  
2. Emulátor načte operačního systému Windows Phone.  
  
3. Emulátor se zobrazí na obrazovce Start Windows Phone.  
  
4. Aplikace je nasazená do emulátoru.  
  
5. Vaše aplikace běží v emulátoru.  
  
   Pokud vybraný emulátor je již spuštěn, je aplikace nasazena a spuštění v spuštěný emulátor. Najednou můžete spustit pouze jedna instance každé emulátoru.  
  
> [!TIP]
>  Při testování vaší aplikace v emulátoru, ponechte emulátor, které jsou otevřené mezi ladicími relacemi, takže budete moci spustit vaši aplikaci znovu rychle pracovní postupy.  
  
###  <a name="BKMK_vs"></a> Spuštění aplikace ze sady Visual Studio  
  
##### <a name="to-deploy-and-run-an-app-from-visual-studio"></a>K nasazení a spuštění aplikace ze sady Visual Studio  
  
1.  V sadě Visual Studio otevřete projekt Windows Phone.  
  
2.  Na **standardní** nástrojů, vyberte jednu z možností emulátoru.  
  
     ![Seznam imagí Windows Phone Emulator](../debugger/media/wp-emulator-list.png "WP_Emulator_list")  
  
3.  K nasazení a spuštění aplikace s laděním, na **ladění** nabídky, klikněte na tlačítko **spustit ladění**, nebo stiskněte klávesu F5.  
  
     K nasazení a spuštění aplikace bez ladění, na **ladění** nabídky, klikněte na tlačítko **spustit bez ladění**, nebo stisknutím kláves Ctrl + F5.  
  
     Nasazení a spuštění vaší aplikace.  
  
     K nasazení aplikace bez nutnosti spuštění, dále **sestavení** nabídky, klikněte na tlačítko **nasadit řešení**.  
  
##### <a name="to-stop-a-running-app"></a>Zastavit spuštěné aplikace  
  
- Zastavit spuštěné aplikace, proveďte jednu z následujících akcí:  
  
  - V sadě Visual Studio na **ladění** nabídky, klikněte na tlačítko **Zastavit ladění**, nebo stiskněte klávesy Shift + F5.  
  
  - V emulátoru, stiskněte **zpět** tlačítko pro ukončení aplikace. Pokud aktivní stránka aplikace nebyla úvodní stránku aplikace, bude pravděpodobně nutné stisknutím klávesy **zpět** tlačítko více než jednou.  
  
    Otevře se obrazovka aplikace ukončí a spuštění. Ukončí aktuální relace ladění.  
  
##### <a name="to-restart-an-app-without-debugging"></a>K restartování aplikace bez ladění  
  
1.  V emulátoru na obrazovce Start, potáhněte doleva, chcete-li zobrazit seznam aplikací.  
  
2.  V seznamu aplikací klepněte na ikonu aplikace. Restartování aplikace bez ladění.  
  
##### <a name="to-deactivate-a-running-app"></a>Deaktivace spuštěné aplikace  
  
1.  Před spuštěním aplikace v sadě Visual Studio, klikněte pravým tlačítkem na projekt v Průzkumníku řešení a pak vyberte **vlastnosti** otevřete **Návrháře projektu**.  
  
2.  V **Návrháře projektu**na **ladění** ponechte **objektů označených jako neplatné po deaktivaci při ladění** zaškrtněte políčko není zaškrtnuto, pokud chcete aplikaci přejdete v neaktivní stav, kdy deaktivovat. Zaškrtněte políčko, pokud chcete aplikaci bude označen jako neplatný, při deaktivaci.  
  
3.  Na **ladění** nabídky, klikněte na tlačítko **spustit ladění**, nebo stisknutím klávesy F5 spusťte aplikaci.  
  
4.  V emulátoru, stiskněte **Start** tlačítko. Se zobrazí na úvodní obrazovku a aplikace je deaktivováno. Aplikace buď přejde do stavu neaktivní nebo je označen jako neplatný, v závislosti na nastavení **objektů označených jako neplatné po deaktivaci při ladění** zaškrtávací políčko.  
  
##### <a name="to-reactivate-a-dormant-or-tombstoned-app"></a>Opětovná aktivace aplikace neaktivní nebo označen jako neplatný  
  
-   V emulátoru, stiskněte **zpět** se vrátit do aplikace. Pokud přejde na jinou stránku nebo otevřít jiné aplikace, bude pravděpodobně nutné stisknutím klávesy **zpět** tlačítko více než jednou a znovu aktivujte ji.  
  
     Obnoví se relace ladění. Pokud ladicí program má odpojit z aplikace, budete muset stisknutím klávesy F5 pokračovat v relaci ladění.  
  
###  <a name="BKMK_depltool"></a> Spuštění aplikace s nástrojem pro nasazení aplikace  
 Můžete také použít nástroj pro nasazení aplikace Windows Phone (**AppDeploy.exe**) ke spuštění vaší aplikace se spustila v emulátoru. Tento nástroj je samostatná aplikace, který je nainstalován při instalaci nástroje pro vývoj Windows Phone.  
  
 Další informace najdete v tématu [aplikací nasadit Windows Phone 8.1 pomocí nástroje nasazení aplikace](http://msdn.microsoft.com/library/23700f82-1399-44d9-bc0c-714be4a48ee6).  
  
##  <a name="BKMK_toolbar"></a> Konfigurace emulátorem Windows Phone pomocí nástrojů emulátoru  
 Tato tabulka uvádí dostupné konfigurace tlačítka na panelu nástrojů emulátoru.  
  
|Tlačítka panelu nástrojů|Možnosti konfigurace|  
|---------------------|---------------------------|  
|![Zadejte možnosti nástrojů Windows Phone Emulator](../debugger/media/wp-emulator.png "WP_Emulator_")|**Konfigurace bodu jedním nebo více bodu vstupu**<br /><br /> Když povolíte Multi-Factor vstupní bod, kliknete pravým tlačítkem přesunout dotykovými body bez zásahu do obrazovky. Klepněte na položku můžete přesunout i dotykovými body současně.|  
|![Orientace na panelu nástrojů Windows Phone Emulator](../debugger/media/wp-emulator-rotation.png "WP_Emulator_rotation")|**Konfigurace orientace v emulátoru**<br /><br /> Orientace v emulátoru Windows Phone můžete změnit na jednu ze tří směrů: výšku, na šířku doleva nebo doprava na šířku. Velikost emulátoru nezmění při změně orientace.<br /><br /> Chcete-li změnit orientaci, klikněte na tlačítko **Otočit doleva** tlačítko nebo **Otočit doprava** tlačítko.|  
|![Velikost panelu nástrojů Windows Phone Emulator](../debugger/media/wp-emulator-size.png "WP_Emulator_size")|**Konfigurovat velikost emulátoru**<br /><br /> Můžete změnit velikost emulátoru na obrazovce počítače hostitele. Bodů na palec (DPI) pro emulátor je založená na hostitele sledování DPI, bez ohledu na hodnotu přiblížení.<br /><br /> – Chcete-li přizpůsobit emulátoru na obrazovku, klikněte na tlačítko **přizpůsobit na obrazovku** tlačítko.<br />– Chcete-li změnit nastavení přiblížení či oddálení, klikněte na tlačítko **přiblížení** tlačítko. **Přiblížení** zobrazí se dialogové okno. V **přiblížení** dialogového okna zadejte hodnotu zvětšení 33 až 100.|  
  
##  <a name="BKMK_buttons"></a> Použití simulované hardwarová tlačítka v emulátoru  
 Simulace použití v telefonu hardwarová tlačítka s použitím simulovaného hardwarová tlačítka na pravé straně obrazovky emulátoru.  
  
- Klikněte na tlačítko **Power** tlačítko pro simulaci zapnutí zobrazení odhlásit a znovu přihlásit. Klepněte a podržte pro simulaci vypnutí telefonu.  
  
- Klikněte na tlačítko **svazku nahoru** nebo **svazku dolů** tlačítko pro simulaci změna svazku v telefonu mluvčího pro telefonní hovory a oznámení.  
  
- **Fotoaparát** tlačítko spustí aplikace fotoaparát. Můžete simulovat trvá fotku nebo video s použitím ovládacích prvků v aplikaci fotoaparát.  
  
  Následující snímek obrazovky ukazuje simulované hardwarová tlačítka.  
  
1. Levý obrázek se zobrazí na obrazovce Start na emulátoru.  
  
2. Střední image emulátoru zobrazí po klepnutí **Power** tlačítko Vypnout zobrazení.  
  
3. Pravý obrázek se zobrazí na obrazovce emulátoru po klepnutí **svazku nahoru** tlačítko zvětšete svazek.  
  
   ![Tlačítka v emulátoru Windows Phone](../debugger/media/wp-emulator-buttons.png "WP_Emulator_buttons")  
  
##  <a name="BKMK_tasks_kbd"></a> Použití klávesnice počítače pomocí emulátoru  
 Emulátor podporuje mapování klávesnice hardwaru na vašem vývojovém počítači, na klávesnici na Windows Phone. Chování klíče je stejné jako u zařízení s Windows Phone.  
  
 Ve výchozím nastavení není povolená hardwarová klávesnice. Tato implementace je stejná jako posuvné klávesnice, který musí být nasazené, než budete moct použít. Před povolením klávesnice hardwaru emulátor přijímá klíče vstup pouze z klíče ovládacího prvku.  
  
 Speciální znaky na klávesnici lokalizovanou verzi sady Windows vývojový počítač nepodporuje emulátor. Zadat speciální znaky, které se nacházejí na lokalizované klávesnice, místo toho použijte Panel vstup softwaru (SIP).  
  
 Použití klávesnice počítače se spustila v emulátoru, stiskněte klávesu PAGE UP klíč nebo klíč PAUSE/BREAK (emulátor systému Windows 8 nebo 8.1) nebo F4 (emulátor Windows 10).  
  
 Pokud chcete zastavit pomocí klávesnice počítače se spustila v emulátoru, stiskněte klávesu PAGE DOWN klíč nebo klíč PAUSE/BREAK (emulátor systému Windows 8 nebo 8.1) nebo F4 (emulátor Windows 10).  
  
 V následující tabulce jsou uvedeny kláves na klávesnici hardwaru, můžete použít k emulaci tlačítek a jiných ovládacích prvků ve Windows Phone.  
  
|Hardwarový klíč počítače|Windows Phone hardwarové tlačítko.|Poznámky|  
|---------------------------|-----------------------------------|-----------|  
|F1|ZPĚT|Dlouhé stisknutí fungovat podle očekávání.|  
|F2|SPUŠTĚNÍ|Dlouhé stisknutí fungovat podle očekávání.|  
|F3|HLEDÁNÍ||  
|F4|V emulátoru Windows 10 Přepne mezi pomocí klávesnice v místním počítači a ne pomocí klávesnice v místním počítači.|Není k dispozici v emulátoru systému Windows 8 nebo 8.1.|  
|F5|Nelze použít.||  
|F6|FOTOAPARÁTU POLOVINĚ|Vyhrazené fotoaparát tlačítko, které se stiskne urazili polovinu cesty.|  
|F7|ÚPLNÉ FOTOAPARÁTU|Tlačítko vyhrazené fotoaparátu.|  
|F8|Nelze použít.||  
|F9|SVAZEK NAHORU||  
|F10|SVAZEK DOLŮ||  
|F11|Nelze použít.||  
|F12|NAPÁJENÍ|Stisknutím klávesy F12 dvakrát povolit zamykací obrazovce.<br /><br /> Dlouhé stisknutí fungovat podle očekávání.|  
|ESC|ZPĚT|Dlouhé stisknutí fungovat podle očekávání.|  
|PAUSE/BREAK|Přepnout klávesnice (jenom pro emulátor systému windows 8 nebo 8.1).|Není k dispozici pro emulátor systému Windows 10.|  
|PAGE UP|Umožňuje hardwaru pomocí klávesnice (jenom emulátor systému Windows 8 nebo 8.1).|Není k dispozici pro emulátor systému Windows 10.|  
|O STRÁNKU DOLŮ|Zakáže hardwaru klávesnice (jenom emulátor systému Windows 8 nebo 8.1).|Není k dispozici pro emulátor systému Windows 10.|  
  
##  <a name="BKMK_checkpoints"></a> Uložit a načíst vlastní kontrolní body  
 Uložte snímek stavu na emulátor pomocí **kontrolní body** kartu v emulátoru **dalších nástrojů**. Tato funkce je užitečná, pokud se často testování aplikace s využitím stejných dat a nastavení.  
  
 Například pokud vaše aplikace vyžaduje několik kontaktů, můžete vytvořit jednou záznamů kontaktů a uložte snímek emulátoru. Jinak budete muset znovu vytvořit záznamů kontaktů pokaždé, když spusťte emulátor.  
  
- Klikněte na tlačítko **nového kontrolního bodu** zachytit nový snímek stavu emulátoru s daty a nastavením požadovaným pro testování vaší aplikace znovu později. Nový kontrolní bod se přidá do **kontrolní body** seznamu.  
  
   Kontrolní bod nelze zachytit, zatímco je připojen ladicí program v emulátoru.  
  
- Vyberte kontrolní bod v **kontrolní body** seznamu zobrazíte informace o kontrolního bodu.  
  
- Vyberte přepínač v **výchozí** sloupec aby uložené kontrolní bod výchozí kontrolní bod pro aktivní emulátoru.  
  
- Klikněte na tlačítko **obnovení** restartovat operační systém Windows Phone v emulátoru a načíst vybraný snímek.  
  
- Klikněte na tlačítko **odstranit** odstranit snímek, který už nepotřebujete.  
  
  Původní obrázek emulátoru se vždy zobrazí jako první položku **kontrolní body** seznamu a nelze změnit ani odstranit. Můžete ale vybrat jiný snímek jako výchozí image emulátoru.  
  
  ![Kontrolní body kartu emulátoru Windows Phone](../debugger/media/wp-emulator-checkpoints.png "WP_Emulator_checkpoints")  
  
##  <a name="BKMK_tasks_shot"></a> Pořídit snímky obrazovky v emulátoru  
 Můžete vytvořit kopie obrazovky aplikací Windows Phone pomocí nástroje snímek obrazovky v okně Další nástroje. Nástroj vytvoří soubory PNG, odpovídající řešení spuštěný emulátor.  
  
 ![Snímky obrazovky z Windows Phone Emulator](../debugger/media/wp-emulator-screenshots.png "WP_Emulator_screenshots")  
  
#### <a name="to-create-an-app-screenshot-by-using-the-built-in-emulator-screenshot-tool"></a>Vytvoření – snímek obrazovky aplikace s použitím nástroje snímek obrazovky s integrovanou emulátoru  
  
1. K optimalizaci kvality vaší snímky obrazovky, nastavte úroveň přiblížení emulátoru do 100 procent. Vyšší nastavení úrovně přiblížení, tím lepší kvalitu na snímku obrazovky.  
  
2. Spusťte aplikaci v emulátoru.  
  
3. Na panelu nástrojů emulátor, klikněte na tlačítko Rozbalit otevřete **další nástroje** okna.  
  
4. Klikněte na tlačítko **snímek obrazovky** kartu.  
  
5. Když je aplikace připravená, klikněte na tlačítko **zachycení** tlačítko.  
  
    Snímek obrazovky se zobrazí v pracovním prostoru.  
  
6. Klikněte na tlačítko **Uložit** tlačítko Otevřít **uložit jako** dialogové okno.  
  
7. Vyberte umístění a **název_souboru** a potom klikněte na tlačítko **Uložit**.  
  
8. Volitelně můžete přejít na jiné stránky v aplikaci a zachytit další snímky obrazovky.  
  
9. Spuštění emulátoru se jiná obrazovka řešení k zachycení stejné snímků na jiné řešení. Pokud jste spustili aplikaci s laděním, je nutné zastavit ladění předtím, než spustíte jej znovu na jiný emulátor.  
  
   Zakažte čítače frekvence snímků na obrazovce emulátoru ještě před zaznamenáním snímky obrazovky, který bude odeslán do Windows Phone Store.  
  
#### <a name="to-disable-frame-rate-counters-in-the-emulator-before-capturing-screenshots"></a>Chcete-li zakázat čítače frekvence snímků se spustila v emulátoru před pořizování snímků  
  
-   Určení verze sestavení v sadě Visual Studio. Po zadání sestavení pro vydání, spusťte aplikaci tak, že vyberete **nasadit _[název aplikace]_**  odkaz na **sestavení** nabídky.  
  
-   Alternativně můžete Zakomentovat řádek kódu v souboru app.xaml.cs nebo app.xaml.vb, která nastaví hodnotu `EnableFrameRateCounter` k `true`.



