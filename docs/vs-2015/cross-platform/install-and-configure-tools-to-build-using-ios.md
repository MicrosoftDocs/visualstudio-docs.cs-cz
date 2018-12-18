---
title: Instalace a konfigurace nástrojů pro vytváření pomocí iOS | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
ms.assetid: d0c311c9-9eb9-42c5-ba07-25604362cd28
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6a5d5543ace2087db4ed5349e72fcaf53228d8ec
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51787806"
---
# <a name="install-and-configure-tools-to-build-using-ios"></a>Instalace a konfigurace nástrojů pro vytváření pomocí iOS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Visual C++ pro vývoj mobilních řešení napříč platformami můžete použít pro úpravy, ladění a nasazení iOS kódu do simulátoru iOS nebo zařízení s Iosem, ale z důvodu licenčních omezení, kód musí být vytvořená a vzdálené spouštění v počítačích Mac. Pokud chcete sestavovat a spouštět aplikace pro iOS pomocí sady Visual Studio, budete muset nastavit a nakonfigurovat vzdálený agent [vcremote](http://go.microsoft.com/fwlink/p/?LinkId=534988), na vašem počítači Mac. Vzdálený agent obslužné rutiny žádosti o sestavení ze sady Visual Studio aplikace a spustí se na zařízení s iOS připojené k počítači Mac, nebo simulátor iOS na macu  
  
> [!NOTE]
>  Informace o používání služeb hostovaných v cloudu Mac místo Mac najdete v tématu [vytváření a simulace iOS v cloudu](https://taco.visualstudio.com/en-us/docs/build_ios_cloud/). Pokyny jsou určené pro sestavení pomocí nástrojů Visual Studio pro Apache Cordova. Chcete-li postupujte podle pokynů pro sestavení pomocí jazyka Visual C++ pro vývoj mobilních řešení napříč platformami, nahraďte vcremote pro vs-mda-remote.  
  
 Jakmile nainstalujete nástroje pro vytváření pomocí iOS, přečtěte si toto téma způsoby, jak rychle nakonfigurovat a aktualizovat vzdálený agent pro vývoj pro iOS v sadě Visual Studio a na vašem počítači Mac.  
  
 [Požadované součásti](#Prerequisites)  
  
 [Instalace vzdáleného agenta pro iOS](#Install)  
  
 [Spuštění vzdáleného agenta](#Start)  
  
 [Konfigurace vzdáleného agenta v sadě Visual Studio](#ConfigureVS)  
  
 [Vygenerovat nový bezpečnostní kód PIN](#GeneratePIN)  
  
 [Vytvoření nového certifikátu serveru](#GenerateCert)  
  
 [Konfigurace vzdáleného agenta na počítači Mac](#ConfigureMac)  
  
##  <a name="Prerequisites"></a> Požadované součásti  
 Chcete-li nainstalovat a používat vzdálený agent pro vývoj kódu pro iOS, musíte nejprve mít tyto požadavky:  
  
-   Počítač Mac se systémem OS X Mavericks nebo vyšší  
  
-   [Apple ID](https://appleid.apple.com/)  
  
-   Aktivní [iOS Developer Program](https://developer.apple.com/programs/ios/) účtu Apple  
  
-   [Xcode 6](https://developer.apple.com/xcode/downloads/)  
  
     Xcode 6 si můžete stáhnout z App Store.  
  
-   Nástroje příkazového řádku Xcode  
  
     Instalace nástrojů příkazového řádku Xcode, otevřete aplikaci terminál na počítači Mac a zadejte následující příkaz:  
  
     `xcode-select --install`  
  
-   Podpisová identita nakonfigurované v prostředí Xcode pro iOS  
  
     Podrobné informace o získání identitu podepisování pro iOS najdete v tématu [zachování identity Your podepisování a certifikáty](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingCertificates/MaintainingCertificates.html) v knihovně iOS Developer Library. Chcete-li zobrazit nebo nastavit podpisové identity v Xcode, otevřete **Xcode** nabídku a zvolte **Předvolby**. Vyberte **účty** a vyberte svoje Apple ID a klikněte na tlačítko **zobrazit podrobnosti o** tlačítko.  
  
-   Pokud používáte zařízení s Iosem pro vývoj, zřizovací profil nakonfigurovaný v Xcode pro vaše zařízení  
  
     Podrobné informace o vytváření zřizovací profily, najdete v části [vytváření zřizování profilů pomocí centra](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingProfiles/MaintainingProfiles.html#//apple_ref/doc/uid/TP40012582-CH30-SW24) v knihovně iOS Developer Library.  
  
-   [Node.js](http://nodejs.org/)  
  
-   Najít aktualizovanou verzi npm  
  
     Tato verze npm, která se dodává s využitím Node.js nemusí být dostatečně nová, aby instalace vcremote. Pokud chcete aktualizovat npm, otevřete aplikaci terminál na počítači Mac a zadejte následující příkaz:  
  
     `sudo npm install -g npm@latest`  
  
##  <a name="Install"></a> Instalace vzdáleného agenta pro iOS  
 Při instalaci Visual C++ pro vývoj Multiplatformních mobilních řešení pro Visual Studio může komunikovat s [vcremote](http://go.microsoft.com/fwlink/p/?LinkId=534988), vzdáleného agenta spuštěného na počítači Mac, přenos souborů, sestavte a spusťte aplikaci pro iOS a odeslat příkazy ladění.  
  
 Před instalací vzdáleného agenta, ujistěte se, že jste splnili [požadavky](#Prerequisites) a nainstalované [Visual C++ pro vývoj mobilních řešení napříč platformami](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md#InstallTheTools).  
  
###  <a name="DownloadInstall"></a> Stažení a instalace vzdáleného agenta  
  
- Z terminálu aplikace na počítači Mac zadejte:  
  
   `sudo npm install -g --unsafe-perm vcremote`  
  
   Globální instalace (**-g**) přepínač se doporučuje, ale nevyžaduje.  
  
   Během instalace vcremote je nainstalovaná a je aktivován režim pro vývojáře na vašem počítači Mac. [Homebrew](http://brew.sh/) a nainstaluje se také dva balíčky npm, vcremote lib a vcremote-utils.  
  
  > [!NOTE]
  >  K instalaci Homebrew, musí mít přístup sudo (správce). Pokud je potřeba nainstalovat vcremote bez sudo, můžete ručně nainstalujte Homebrew v umístění usr/local a jeho složku bin přidat do cesty. Další informace najdete v tématu [Homebrew dokumentaci](https://github.com/Homebrew/homebrew/wiki/Installation). Vývojářský režim povolit ručně, v aplikaci terminál zadejte tento příkaz: `DevToolsSecurity –enable`  
  
  Pokud aktualizujete na novou verzi sady Visual Studio, je třeba aktualizovat na aktuální verzi vzdáleného agenta. Aktualizace vzdáleného agenta, opakujte postup stažení a instalace vzdáleného agenta.  
  
##  <a name="Start"></a> Spuštění vzdáleného agenta  
 Vzdálený agent musí být spuštěná sada Visual Studio sestavte a spusťte váš kód s Iosem. Visual Studio musí být párována s vzdáleného agenta předtím, než může komunikovat. Ve výchozím nastavení se vzdálený agent spouští v režimu zabezpečené připojení, která vyžaduje kód PIN spárovat se sadou Visual Studio.  
  
###  <a name="RemoteAgentStartServer"></a> Spuštění vzdáleného agenta  
  
- Z terminálu aplikace na počítači Mac zadejte:  
  
   `vcremote`  
  
   Spustí se vzdálený agent s výchozí adresář sestavení z ~ / vcremote. Další možnosti konfigurace, najdete v části [konfigurace vzdáleného agenta na počítači Mac](#ConfigureMac).  
  
  Při prvním spuštění agenta a kdykoli vytvořit nový klientský certifikát, jsou k dispozici požadované informace pro konfiguraci agenta v sadě Visual Studio, včetně názvu hostitele, port a kód PIN.  
  
  ![Ke generování zabezpečeného PIN kódu použít vcremote](../cross-platform/media/cppmdd-vcremote-generateclientcert.png "CPPMDD_vcremote_generateClientCert")  
  
  Pokud máte v úmyslu konfigurace vzdáleného agenta v sadě Visual Studio pomocí názvu hostitele, odešlete zprávu ping Mac z Windows pomocí názvu hostitele k ověření, že je dostupný. V opačném případě budete muset místo toho použijte IP adresu.  
  
  Vygenerovaný PIN kód je pro jeden čas použití a je platná pouze po omezenou dobu. Pokud aplikace Visual Studio není spárovat se vzdáleným agentem před vypršení časového limitu, je potřeba vygenerovat nový kód PIN. Další informace najdete v tématu [vygenerovat nový bezpečnostní kód PIN](#GeneratePIN).  
  
  Vzdálený agent můžete použít v nezabezpečeném režimu. V nezabezpečeném režimu se dají párovat vzdáleného agenta se sadou Visual Studio bez kódu PIN.  
  
#### <a name="to-disable-secured-connection-mode"></a>Chcete-li zakázat režim zabezpečené připojení  
  
-   Chcete-li zakázat režim zabezpečených připojení v vcremote, zadejte tento příkaz v aplikaci terminál na počítači Mac:  
  
     `vcremote --secure false`  
  
#### <a name="to-enable-secured-connection-mode"></a>Pokud chcete povolit režim zabezpečené připojení  
  
- Pokud chcete povolit režim zabezpečené připojení, zadejte tento příkaz:  
  
   `vcremote --secure true`  
  
  Po zahájení vzdáleného agenta můžete použít v sadě Visual Studio až po ukončení.  
  
#### <a name="to-stop-the-remote-agent"></a>Chcete-li zastavit vzdáleného agenta  
  
-   V terminálu okno vcremote běží v, zadejte `Control+C`.  
  
##  <a name="ConfigureVS"></a> Konfigurace vzdáleného agenta v sadě Visual Studio  
 Pro připojení ke vzdálenému agentu ze sady Visual Studio, musíte zadat konfigurace vzdáleného v možnostech sady Visual Studio.  
  
#### <a name="to-configure-the-remote-agent-from-visual-studio"></a>Konfigurace vzdáleného agenta ze sady Visual Studio  
  
1. Jestliže dosud není spuštěn agent na počítači Mac, postupujte podle kroků v [spustit vzdálený agent](#Start). Počítače Mac musí být spuštěná vcremote pro Visual Studio úspěšně spárovat, připojit a sestavte projekt.  
  
2. Na počítači Mac získáte název hostitele nebo IP adresu vašeho macu.  
  
    Můžete získat IP adresu pomocí **ifconfig** příkazu v okně terminálu. Použijte adresu inet uvedené v části active síťové rozhraní.  
  
3. Na řádku nabídek sady Visual Studio, zvolte **nástroje**, **možnosti**.  
  
4. V **možnosti** dialogového okna rozbalte **různé platformy**, **C++**, **iOS**.  
  
5. V **název hostitele** a **Port** pole, zadejte hodnoty určené vzdáleného agenta při jeho spuštění. Název hostitele může být název DNS nebo IP adresu vašeho macu. Výchozí port je 3030.  
  
   > [!NOTE]
   >  Pokud je příkazem ping otestovat Mac pomocí názvu hostitele, budete muset použít IP adresu.  
  
6. Pokud používáte vzdálený agent ve výchozím režimu zabezpečené připojení, zkontrolujte **Secure** zaškrtávací políčko, zadejte PIN kód hodnotu zadanou pomocí vzdáleného agenta v **Pin** pole. Pokud používáte vzdálený agent v režimu nezabezpečená připojení, zrušte zaškrtnutí políčka **Secure** zaškrtávací políčko a nechat **Pin** prázdné pole.  
  
7. Zvolte **pár** povolit párování.  
  
    ![Konfigurace připojení vcremote pro sestavení iOS](../cross-platform/media/cppmdd-options-ios.PNG "CPPMDD_Options_iOS")  
  
    Párování se opakuje dokud nezměníte název hostitele nebo portu. Pokud změníte název hostitele nebo port v **možnosti** dialogové okno, vrátit zpět změny, zvolte **vrácení** tlačítka se vrátit k předchozí párování.  
  
    Pokud spárování úspěšné není, ověřte, že vzdálený agent běží, pomocí kroků v [spustit vzdálený agent](#Start). Pokud příliš mnoho času uplynulo od vzdáleného agenta PIN kód se vygeneroval, postupujte podle kroků v [vygenerovat nový bezpečnostní kód PIN](#GeneratePIN) na Macu a zkuste to znovu. Pokud použijete název hostitele počítače Mac, zkuste použít IP adresu v **název hostitele** místo toho.  
  
8. Aktualizovat název složky v **vzdálený kořen** pole zadat složku, která používají vzdálený agent ve vašem adresáři Domovská stránka (~) na počítači Mac. Ve výchozím nastavení vzdálený agent používá /Users/`username`/vcremote jako vzdálený kořen.  
  
9. Zvolte **OK** se uložit nastavení vzdáleného připojení párování.  
  
   Visual Studio používá stejné informace pro připojení k vzdáleného agenta na počítači Mac pokaždé, když ho používáte. Nepotřebujete spárovat sady Visual Studio se vzdáleným agentem znovu není-li vygenerovat nový certifikát zabezpečení na počítači Mac, nebo jeho název hostitele nebo IP adresu změny.  
  
##  <a name="GeneratePIN"></a> Vygenerovat nový bezpečnostní kód PIN  
 Při prvním spuštění vzdáleného agenta vygenerovaný PIN kód je platný po omezenou dobu – ve výchozím nastavení, 10 minut. Pokud před vypršení časového limitu, nepárují sady Visual Studio se vzdáleným agentem, je potřeba vygenerovat nový kód PIN.  
  
#### <a name="to-generate-a-new-pin"></a>Chcete-li vygenerovat nový kód PIN  
  
1.  Zastavte agenta, nebo otevřete druhou okna aplikace na terminálu na svém počítači Mac a, který slouží k zadání příkazu.  
  
2.  V aplikaci terminál, zadejte tento příkaz:  
  
     `vcremote generateClientCert`  
  
     Vzdálený agent vygeneruje nový dočasný PIN kód. Visual Studio spárovat s použitím nového kódu PIN, opakujte kroky v [konfigurace vzdáleného agenta v sadě Visual Studio](#ConfigureVS).  
  
##  <a name="GenerateCert"></a> Vytvoření nového certifikátu serveru  
 Z bezpečnostních důvodů certifikáty serveru tento pár Visual Studio se vzdáleným agentem jsou svázány se IP adresa nebo název hostitele vašeho macu. Pokud tyto hodnoty změnit, musíte vygenerovat nový certifikát serveru a potom znovu nakonfigurovat sady Visual Studio s novými hodnotami.  
  
#### <a name="to-generate-a-new-server-certificate"></a>Pro vytvoření nového certifikátu serveru  
  
1.  Zastavte agenta vcremote.  
  
2.  V aplikaci terminál, zadejte tento příkaz:  
  
     `vcremote resetServerCert`  
  
3.  Po zobrazení výzvy k potvrzení, zadejte `Y`.  
  
4.  V aplikaci terminál, zadejte tento příkaz:  
  
     `vcremote generateClientCert`  
  
     Tím se vygeneruje nový dočasný PIN kód.  
  
5.  Visual Studio spárovat s použitím nového kódu PIN, opakujte kroky v [konfigurace vzdáleného agenta v sadě Visual Studio](#ConfigureVS).  
  
##  <a name="ConfigureMac"></a> Konfigurace vzdáleného agenta na počítači Mac  
 Můžete nakonfigurovat pomocí různých možností příkazového řádku vzdáleného agenta. Můžete například zadat port pro naslouchání požadavkům na sestavení a zadejte maximální počet buildů udržovat v systému souborů. Výchozí limit je 10 buildů. Vzdálený agent odebere sestavení, které překračují maximální na vypnutí.  
  
#### <a name="to-configure-the-remote-agent"></a>Konfigurace vzdáleného agenta  
  
-   Pokud chcete zobrazit úplný seznam příkazů vzdáleného agenta, v terminálu aplikaci, zadejte:  
  
     `vcremote --help`  
  
-   Zabezpečený režim zakázání a povolení jednoduché připojení na základě protokolu HTTP, zadejte:  
  
     `vcremote --secure false`  
  
     Když použijete tuto možnost, zrušte **Secure** zaškrtávací políčko a nechat **Pin** prázdné pole při konfiguraci agenta v sadě Visual Studio.  
  
-   Chcete-li zadat umístění pro soubory vzdáleného agenta, zadejte:  
  
     `vcremote --serverDir directory_path`  
  
     kde *directory_path* je umístění na počítači Mac chcete umístit soubory protokolů, sestavení a certifikáty serveru. Ve výchozím nastavení je toto umístění: /Users/*uživatelské jméno*/vcremote. Sestavení jsou uspořádané podle čísla sestavení v tomto umístění.  
  
-   Použití proces na pozadí k zachycení `stdout` a `stderr` do souboru s názvem server.log, zadejte:  
  
     `vcremote > server.log 2>&1 &`  
  
     Soubor server.log může být užitečné při řešení potíží s problémy se sestavením.  
  
-   Chcete-li spustit agenta pomocí konfiguračního souboru namísto parametrů příkazového řádku, zadejte:  
  
     `vcremote --config config_file_path`  
  
     kde *config_file_path* je cesta ke konfiguračnímu souboru ve formátu JSON. Možnosti spuštění a jejich hodnoty nesmí obsahovat pomlčky.  
  
## <a name="see-also"></a>Viz také  
 [Instalace komponenty Visual C++ for Cross-Platform Mobile Development](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md)

