---
title: Spuštění aplikací Windows Phone v emulátoru | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c7590788-beb3-403c-a7dd-18472a9e585e
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5673ebf28cc652e3bcd973808db87b5bb058659c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683525"
---
# <a name="run-windows-phone-apps-in-the-emulator"></a>Spouštění aplikací pro Windows Phone v emulátoru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Emulátor Windows Phone poskytuje virtualizované prostředí, ve kterém můžete ladit a testovat Windows Phone aplikace v počítači bez fyzického zařízení. Můžete simulovat běžné události dotykové ovládání a rotace a zvolit velikost fyzické obrazovky a rozlišení, které chcete emulovat. Můžete také otestovat mnoho běžně používaných funkcí, jako je umístění, sítě, oznámení, senzory, akcelerometr a volitelná karta SD.  
  
 Další informace o funkcích, které můžete testovat v emulátoru, najdete v tématu věnovaném [testování funkcí aplikace v emulátoru Windows Phone](https://msdn.microsoft.com/c1b2b0ec-b8cc-4a98-84c1-701428e45cb1).  
  
 Společně se sadou Visual Studio poskytuje emulátor kompletní prostředí, ve kterém můžete navrhovat, vyvíjet, ladit a testovat aplikace Windows Phone.  
  
## <a name="run-a-windows-phone-app-in-the-emulator"></a><a name="BKMK_run"></a> Spuštění aplikace Windows Phone v emulátoru  
 Při vývoji aplikace Windows Phone můžete použít emulátor Windows Phone k rychlému nasazení a otestování vaší aplikace. Před publikováním aplikace v obchodě Windows Phone doporučujeme otestovat svou aplikaci na skutečném Windows Phoneovém zařízení. To vám umožní vyzkoušet si aplikaci, protože k ní uživatelé budou mít zkušenosti.  
  
 Při prvním spuštění aplikace Windows Phone v emulátoru Windows Phone dojde k následujícím událostem:  
  
1. Spustí se emulátor.  
  
2. Emulátor načte Windows Phone operační systém.  
  
3. Emulátor zobrazí Windows Phone úvodní obrazovku.  
  
4. Vaše aplikace se nasadí do emulátoru.  
  
5. Vaše aplikace se spouští na emulátoru.  
  
   Pokud je vybraný emulátor už spuštěný, vaše aplikace se nasadí a spustí ve spuštěném emulátoru. V jednom okamžiku může běžet jenom jedna instance každého emulátoru.  
  
> [!TIP]
> Když testujete aplikaci na emulátoru, nechte emulátor otevřený mezi relacemi ladění, abyste mohli aplikaci znovu spustit rychleji.  
  
### <a name="run-an-app-from-visual-studio"></a><a name="BKMK_vs"></a> Spuštění aplikace ze sady Visual Studio  
  
##### <a name="to-deploy-and-run-an-app-from-visual-studio"></a>Nasazení a spuštění aplikace ze sady Visual Studio  
  
1. V aplikaci Visual Studio otevřete Windows Phone projekt.  
  
2. Na panelu nástrojů **standardní** vyberte jednu z možností emulátoru.  
  
     ![Seznam imagí emulátoru Windows Phone](../debugger/media/wp-emulator-list.png "WP_Emulator_list")  
  
3. Pokud chcete aplikaci nasadit a spustit s laděním, v nabídce **ladění** klikněte na **Spustit ladění**nebo stiskněte klávesu F5.  
  
     Pokud chcete aplikaci nasadit a spustit bez ladění, v nabídce **ladění** klikněte na **Spustit bez ladění**nebo stiskněte klávesy CTRL + F5.  
  
     Vaše aplikace je nasazená a spuštěná.  
  
     Pokud chcete aplikaci nasadit bez spuštění, klikněte v nabídce **sestavení** na **nasadit řešení**.  
  
##### <a name="to-stop-a-running-app"></a>Zastavení spuštěné aplikace  
  
- Pokud chcete zastavit spuštěnou aplikaci, proveďte jednu z následujících akcí:  
  
  - V aplikaci Visual Studio v nabídce **ladění** klikněte na možnost **Zastavit ladění**nebo stiskněte klávesy Shift + F5.  
  
  - Kliknutím na tlačítko **zpět** v emulátoru aplikaci ukončíte. Pokud aktivní stránka aplikace není úvodní stránkou aplikace, může být nutné stisknout tlačítko **zpět** více než jednou.  
  
    Aplikace se ukončí a otevře se obrazovka Start. Tím se ukončí aktuální relace ladění.  
  
##### <a name="to-restart-an-app-without-debugging"></a>Restartování aplikace bez ladění  
  
1. V emulátoru na obrazovce Start přetáhnutím vlevo zobrazíte seznam aplikací.  
  
2. V seznamu aplikace klepněte na ikonu aplikace. Aplikace se restartuje bez ladění.  
  
##### <a name="to-deactivate-a-running-app"></a>Deaktivace běžící aplikace  
  
1. Před spuštěním aplikace, v aplikaci Visual Studio, klikněte pravým tlačítkem myši na projekt v Průzkumník řešení a pak vyberte **vlastnosti** . otevře se **Návrhář projektu**.  
  
2. Pokud chcete, aby aplikace přešla do neaktivního stavu při deaktivaci, v **Návrháři projektu**na stránce **ladění** ponechte **neplatnou hodnotu po deaktivaci při ladění** . Zaškrtněte políčko, pokud chcete, aby byla aplikace označena při deaktivaci.  
  
3. V nabídce **ladění** klikněte na **Spustit ladění**nebo stiskněte klávesu F5 pro spuštění aplikace.  
  
4. V emulátoru stiskněte tlačítko **Start** . Zobrazí se obrazovka Start a aplikace se deaktivuje. Aplikace buď přejde do nepoužívaného stavu, nebo je označena jako neoznačená, v závislosti na nastavení neurčité **při deaktivaci při ladění** .  
  
##### <a name="to-reactivate-a-dormant-or-tombstoned-app"></a>Opětovná aktivace neaktivní nebo označené aplikace  
  
- V emulátoru se stisknutím tlačítka **zpět** vraťte do aplikace. Pokud jste přešli na jiné stránky nebo jste otevřeli jinou aplikaci, může být nutné stisknout tlačítko **zpět** více než jednou a aplikaci znovu aktivovat.  
  
     Relace ladění pokračuje. Pokud se ladicí program odpojil od aplikace, může být nutné stisknout klávesu F5, aby se relace ladění obnovila.  
  
### <a name="run-an-app-with-the-application-deployment-tool"></a><a name="BKMK_depltool"></a> Spuštění aplikace pomocí nástroje pro nasazení aplikace  
 K spuštění aplikace v emulátoru můžete také použít nástroj Windows Phone aplikace pro nasazení (**AppDeploy.exe**). Tento nástroj je samostatná aplikace, která je nainstalovaná při instalaci nástrojů Windows Phone Development.  
  
 Další informace najdete v tématu [nasazení aplikací Windows Phone 8,1 pomocí nástroje pro nasazení aplikací](https://msdn.microsoft.com/library/23700f82-1399-44d9-bc0c-714be4a48ee6).  
  
## <a name="configure-the-windows-phone-emulator-with-the-emulator-toolbar"></a><a name="BKMK_toolbar"></a> Konfigurace emulátoru Windows Phone pomocí panelu nástrojů emulátoru  
 Tato tabulka zobrazuje tlačítka konfigurace, která jsou k dispozici na panelu nástrojů emulátoru.  
  
|Tlačítka panelu nástrojů|Možnosti konfigurace|  
|---------------------|---------------------------|  
|![Možnosti vstupu na panelu nástrojů emulátoru Windows Phone](../debugger/media/wp-emulator.png "WP_Emulator_")|**Konfigurace vstupu s jedním bodem nebo víceřádkovou desetinnou čárkou**<br /><br /> Když povolíte Víceřádkový vstup, můžete kliknout pravým tlačítkem myši a přesunout dotykové body, aniž byste museli se dotýkat obrazovky. Pak můžete kliknout levým na, chcete-li současně přesunout oba dotykové body.|  
|![Orientace na panelu nástrojů emulátoru Windows Phone](../debugger/media/wp-emulator-rotation.png "WP_Emulator_rotation")|**Konfigurace orientace emulátoru**<br /><br /> Orientaci v Windows Phone emulátoru můžete změnit na jednu ze tří orientací: na výšku, na šířku doleva nebo na šířku. Velikost emulátoru se při změně orientace nemění.<br /><br /> Chcete-li změnit orientaci, klikněte na tlačítko **Otočit doleva** nebo tlačítko **Otočit doprava** .|  
|![Možnosti velikosti na panelu nástrojů emulátoru Windows Phone](../debugger/media/wp-emulator-size.png "WP_Emulator_size")|**Konfigurace velikosti emulátoru**<br /><br /> Velikost emulátoru můžete změnit na obrazovce hostitelského počítače. Počet bodů na palec (DPI) pro emulátor je založen na rozlišení DPI monitoru hostitele, bez ohledu na hodnotu přiblížení.<br /><br /> – Chcete-li přizpůsobit emulátor na obrazovku, klikněte na tlačítko **Přizpůsobit obrazovce** .<br />– Chcete-li změnit nastavení přiblížení, klikněte na tlačítko **přiblížení** . Otevře se dialogové okno **Lupa** . V dialogovém okně **Lupa** zadejte hodnotu přiblížení mezi 33 a 100.|  
  
## <a name="use-the-simulated-hardware-buttons-on-the-emulator"></a><a name="BKMK_buttons"></a> Použití simulovaných hardwarových tlačítek na emulátoru  
 Simulujte použití hardwarových tlačítek telefonu na pravé straně obrazovky emulátoru pomocí tlačítek simulovaného hardwaru.  
  
- Klikněte na tlačítko **napájení** a Simulujte tak vypnutí a zapnutí displeje. Kliknutím a podržením simulaci Zapněte telefon.  
  
- Kliknutím na tlačítko **Hlasitost nahoru** nebo **dolů** můžete simulovat změnu objemu mluvčího telefonu pro telefonní hovory a oznámení.  
  
- Tlačítko **kamera** spustí aplikaci kamery. Můžete simulovat fotku nebo video pomocí ovládacích prvků v aplikaci kamera.  
  
  Na následujícím snímku obrazovky vidíte simulovaná hardwarová tlačítka.  
  
1. Na levém obrázku se zobrazí úvodní obrazovka na emulátoru.  
  
2. Po klepnutí na tlačítko **napájení** se na prostřední imagi zobrazí emulátor, aby se displej vypnul.  
  
3. Pravý obrázek zobrazuje obrazovku emulátoru po klepnutí na tlačítko **hlasitosti** a zvyšuje hlasitost.  
  
   ![Tlačítka na emulátoru Windows Phone](../debugger/media/wp-emulator-buttons.png "WP_Emulator_buttons")  
  
## <a name="use-the-computer-keyboard-with-the-emulator"></a><a name="BKMK_tasks_kbd"></a> Použití počítačové klávesnice s emulátorem  
 Emulátor podporuje mapování hardwarové klávesnice ve vývojovém počítači na klávesnici na Windows Phone. Chování klíčů je stejné jako u Windows Phoneho zařízení.  
  
 Hardwarová klávesnice není standardně povolená. Tato implementace je ekvivalentní posuvné klávesnici, která musí být nasazena před tím, než ji budete moci použít. Než povolíte hardwarovou klávesnici, emulátor akceptuje vstup klíče jenom z řídicích kláves.  
  
 Emulátor nepodporuje speciální znaky na klávesnici lokalizované verze počítače s Windows Development. Chcete-li zadat speciální znaky, které jsou k dispozici na lokalizované klávesnici, použijte místo toho panel pro zadání softwaru (SIP).  
  
 Chcete-li použít klávesnici počítače v emulátoru, stiskněte klávesu PAGE UP nebo klíč pro pozastavení/přerušení (emulátor systému Windows 8/8.1) nebo F4 (emulátor systému Windows 10).  
  
 Chcete-li ukončit používání klávesnice počítače v emulátoru, stiskněte klávesu PAGE DOWN nebo klíč pozastavení/přerušení (emulátor systému Windows 8/8.1) nebo F4 (emulátor systému Windows 10).  
  
 V následující tabulce je uveden seznam klíčů na hardwarové klávesnici, které lze použít k emulaci tlačítek a dalších ovládacích prvků na Windows Phone.  
  
|Hardwarový klíč počítače|Windows Phone – tlačítko hardwaru|Poznámky|  
|---------------------------|-----------------------------------|-----------|  
|F1|NÁVRAT|Dlouhá stisknutí fungují podle očekávání.|  
|F2|Čína|Dlouhá stisknutí fungují podle očekávání.|  
|F3|SEARCH||  
|F4|V emulátoru Windows 10 přepíná mezi použitím klávesnice místního počítače a nepoužívá klávesnici místního počítače.|Nelze použít v emulátoru systému Windows 8/8.1.|  
|F5|Neužívá se.||  
|F6|FOTOAPARÁT – POLOVIČNÍ|Vyhrazené tlačítko kamery, ve kterém se stiskne uprostřed.|  
|F7|KAMERA PLNÁ|Vyhrazené tlačítko fotoaparátu|  
|F8|Neužívá se.||  
|F9|NAVÝŠENÍ OBJEMU||  
|F10|SNÍŽIT HLASITOST||  
|Kláves|Neužívá se.||  
|F12|POWER|Dvojím stisknutím klávesy F12 povolte zamykací obrazovku.<br /><br /> Dlouhá stisknutí fungují podle očekávání.|  
|KLÁVES|NÁVRAT|Dlouhá stisknutí fungují podle očekávání.|  
|POZASTAVIT/PŘERUŠIT|Přepnout klávesnici (jenom emulátor Windows 8/8.1).|Nelze použít pro emulátor systému Windows 10.|  
|O STRÁNKU NAHORU|Povolí hardwarovou klávesnici (jenom emulátor Windows 8/8.1).|Nelze použít pro emulátor systému Windows 10.|  
|O STRÁNKU DOLŮ|Zakáže hardwarovou klávesnici (jenom emulátor Windows 8/8.1).|Nelze použít pro emulátor systému Windows 10.|  
  
## <a name="save-and-load-custom-checkpoints"></a><a name="BKMK_checkpoints"></a> Uložit a načíst vlastní kontrolní body  
 Uložte snímek stavu emulátoru pomocí karty **kontrolní body** v **dalších nástrojích**emulátoru. Tato funkce je užitečná v případě, že aplikaci často testujete se stejnými daty a nastaveními.  
  
 Například pokud vaše aplikace vyžaduje několik kontaktů, můžete si vytvořit záznamy kontaktů jednou a uložit snímek emulátoru. V opačném případě je nutné znovu vytvořit záznamy kontaktů při každém spuštění emulátoru.  
  
- Kliknutím na **Nový kontrolní bod** Zachyťte nový snímek stavu emulátoru s daty a nastavením požadovaným pro otestování aplikace znovu později. Nový kontrolní bod se přidá do seznamu **kontrolních bodů** .  
  
   Kontrolní bod nelze zachytit, pokud je ladicí program připojen k emulátoru.  
  
- Výběrem kontrolního bodu v seznamu **kontrolní body** zobrazíte informace o kontrolním bodu.  
  
- Výběrem přepínače ve **výchozím** sloupci nastavte, aby byl uložený kontrolní bod výchozím kontrolním bodem pro aktivní emulátor.  
  
- Kliknutím na **obnovit** restartujte Windows Phone operační systém na emulátoru a načtěte vybraný snímek.  
  
- Kliknutím na tlačítko **Odstranit** odstraňte snímek, který již nepotřebujete.  
  
  Původní image emulátoru se vždycky zobrazí jako první položka v seznamu **kontrolní body** a nedá se změnit ani odstranit. Můžete ale vybrat jiný snímek jako výchozí image emulátoru.  
  
  ![Karta kontrolní body v emulátoru Windows Phone](../debugger/media/wp-emulator-checkpoints.png "WP_Emulator_checkpoints")  
  
## <a name="capture-screenshots-in-the-emulator"></a><a name="BKMK_tasks_shot"></a> Zachytit snímky obrazovky v emulátoru  
 Snímky obrazovky vaší aplikace Windows Phone můžete vytvořit pomocí nástroje snímek obrazovky z dalších oken nástrojů. Nástroj vytvoří soubory PNG, které odpovídají rozlišení běžícího emulátoru.  
  
 ![Snímky obrazovky z emulátoru Windows Phone](../debugger/media/wp-emulator-screenshots.png "WP_Emulator_screenshots")  
  
#### <a name="to-create-an-app-screenshot-by-using-the-built-in-emulator-screenshot-tool"></a>Vytvoření snímku aplikace pomocí integrovaného nástroje pro snímek obrazovky emulátoru  
  
1. Pro optimalizaci kvality snímků obrazovky nastavte úroveň přiblížení emulátoru na 100 procent. Čím vyšší úroveň přiblížení nastavíte, tím lepší kvalita obrazovky.  
  
2. Spusťte aplikaci v emulátoru.  
  
3. Kliknutím na tlačítko Rozbalit na panelu nástrojů emulátoru otevřete další okno **nástrojů** .  
  
4. Klikněte na kartu **snímek obrazovky** .  
  
5. Až bude vaše aplikace připravená, klikněte na tlačítko **zachytit** .  
  
    Snímek obrazovky se zobrazí v pracovním prostoru.  
  
6. Kliknutím na tlačítko **Uložit** otevřete dialogové okno **Uložit jako** .  
  
7. Zvolte umístění a **název souboru** , který chcete, a pak klikněte na **Uložit**.  
  
8. Volitelně můžete přejít na jiné stránky v aplikaci a zachytit další snímky obrazovky.  
  
9. Spusťte emulátor s jiným rozlišením obrazovky a zachyťte stejné snímky obrazovky v jiném rozlišení. Pokud jste aplikaci spustili s laděním, je nutné zastavit ladění před tím, než je budete moci znovu spustit na jiném emulátoru.  
  
   Než zachytíte snímky obrazovky, které se odešlou do úložiště Windows Phone, zakažte čítače snímkových frekvencí na obrazovce emulátoru.  
  
#### <a name="to-disable-frame-rate-counters-in-the-emulator-before-capturing-screenshots"></a>Zakázání čítačů frekvence snímků v emulátoru před zachycením snímků obrazovky  
  
- Zadejte sestavení pro vydání v aplikaci Visual Studio. Po zadání buildu pro vydání spusťte aplikaci kliknutím na odkaz **nasadit _[název aplikace]_ ** v nabídce **sestavení** .  
  
- Alternativně můžete odkomentovat řádek kódu v souboru app.xaml.cs nebo App. XAML, který nastaví hodnotu `EnableFrameRateCounter` na `true` .
