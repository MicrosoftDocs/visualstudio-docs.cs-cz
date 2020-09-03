---
title: Instalace a konfigurace nástrojů pro sestavení pomocí iOS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: tgt-pltfrm-cross-plat
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: d0c311c9-9eb9-42c5-ba07-25604362cd28
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 7290ba820c9b678e0b87bdbeaadf9c025162e8ae
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75844466"
---
# <a name="install-and-configure-tools-to-build-using-ios"></a>Instalace a konfigurace nástrojů pro vytváření pomocí iOS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual C++ for Cross-Platform Mobile Development můžete použít k úpravám, ladění a nasazování kódu iOS do simulátoru iOS nebo na zařízení s iOS, ale z důvodu licenčních omezení musí být kód sestavený a spuštěný vzdáleně na Macu. Pokud chcete vytvářet a spouštět aplikace pro iOS pomocí sady Visual Studio, musíte na Macu nastavit a nakonfigurovat vzdáleného agenta [vcremote](https://www.npmjs.com/package/vcremote). Vzdálený Agent zpracovává požadavky na sestavení ze sady Visual Studio a spustí aplikaci na zařízení s iOS připojeném k počítači Mac nebo v simulátoru iOS na Macu.  
  
> [!NOTE]
> Informace o použití služeb Mac hostovaných v cloudu místo Mac najdete v tématu [sestavování a simulace iOS v cloudu](https://taco.visualstudio.com/docs/build_ios_cloud/). Pokyny jsou pro sestavování pomocí Visual Studio Tools pro Apache Cordova. Chcete-li použít pokyny k sestavení pomocí Visual C++ for Cross-Platform Mobile Development, nahraďte vcremote pro vs-MDA-Remote.  
  
 Jakmile nainstalujete nástroje pro sestavení pomocí iOS, přečtěte si toto téma, kde najdete způsoby, jak rychle nakonfigurovat a aktualizovat vzdáleného agenta pro vývoj pro iOS v aplikaci Visual Studio a na Macu.  
  
 [Požadavky](#Prerequisites)  
  
 [Instalace vzdáleného agenta pro iOS](#Install)  
  
 [Spustit vzdáleného agenta](#Start)  
  
 [Konfigurace vzdáleného agenta v aplikaci Visual Studio](#ConfigureVS)  
  
 [Vygenerovat nový bezpečnostní kód PIN](#GeneratePIN)  
  
 [Vygenerovat nový certifikát serveru](#GenerateCert)  
  
 [Konfigurace vzdáleného agenta na Macu](#ConfigureMac)  
  
## <a name="prerequisites"></a><a name="Prerequisites"></a> Požadovaný  
 Pokud chcete nainstalovat a používat vzdáleného agenta pro vývoj kódu pro iOS, musíte nejdřív splnit tyto požadavky:  
  
- Počítač Mac se systémem OS X Mavericks nebo novějším  
  
- [Apple ID](https://appleid.apple.com/)  
  
- Aktivní účet [programu pro vývojáře pro iOS](https://developer.apple.com/programs/ios/) s Apple  
  
- [Xcode 6](https://developer.apple.com/xcode/downloads/)  
  
     Xcode 6 se dá stáhnout z App Storu.  
  
- Nástroje příkazového řádku Xcode  
  
     Pokud chcete nainstalovat nástroje příkazového řádku Xcode, otevřete aplikaci Terminal na Macu a zadejte následující příkaz:  
  
     `xcode-select --install`  
  
- Podpisová identita pro iOS konfigurovaná v Xcode  
  
     Podrobné informace o získání identity podepisování pro iOS najdete v tématu [Údržba podpisových identit a certifikátů](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingCertificates/MaintainingCertificates.html) v knihovně iOS Developer Library. Chcete-li zobrazit nebo nastavit podpisovou identitu v Xcode, otevřete nabídku **Xcode** a vyberte možnost **Předvolby**. Vyberte **účty** a zvolte vaše Apple ID a pak klikněte na tlačítko **Zobrazit podrobnosti** .  
  
- Pokud pro vývoj používáte zařízení s iOS, zřizuje se zřizovací profil nakonfigurovaný v Xcode pro vaše zařízení.  
  
     Podrobné informace o vytváření zřizovacích profilů najdete v tématu [vytváření zřizovacích profilů pomocí členské centra](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingProfiles/MaintainingProfiles.html#//apple_ref/doc/uid/TP40012582-CH30-SW24) v knihovně iOS Developer Library.  
  
- [Node.js](https://nodejs.org/en/)  
  
- Aktualizovaná verze npm  
  
     Verze NPM, která se dodává s Node.js nemusí být dostatečně poslední pro instalaci vcremote. Pokud chcete aktualizovat NPM, otevřete aplikaci Terminal na Macu a zadejte následující příkaz:  
  
     `sudo npm install -g npm@latest`  
  
## <a name="install-the-remote-agent-for-ios"></a><a name="Install"></a> Instalace vzdáleného agenta pro iOS  
 Když nainstalujete Visual C++ for Cross-Platform Mobile Development, Visual Studio může komunikovat s [vcremote](https://www.npmjs.com/package/vcremote), vzdáleným agentem běžícím na Macu, který přenáší soubory, sestaví a spustí aplikaci pro iOS a odesílá příkazy ladění.  
  
 Před instalací vzdáleného agenta se ujistěte, že jste splnili [požadavky](#Prerequisites) a nainstalovaná [Visual C++ for Cross-Platform Mobile Development](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md#InstallTheTools).  
  
### <a name="to-download-and-install-the-remote-agent"></a><a name="DownloadInstall"></a> Stažení a instalace vzdáleného agenta  
  
- Z aplikace terminálu na Macu zadejte:  
  
   `sudo npm install -g --unsafe-perm vcremote`  
  
   Přepínač globální instalace (**-g**) se doporučuje, ale není povinný.  
  
   Během instalace se vcremote nainstaluje a v počítači Mac se aktivuje vývojářský režim. Nainstalují se taky [homebrew](https://brew.sh/) a dva balíčky NPM, vcremote-lib a vcremote-util.  
  
  > [!NOTE]
  > K instalaci homebrew musíte mít přístup sudo (správce). Pokud potřebujete nainstalovat vcremote bez sudo, můžete ručně nainstalovat homebrew do umístění usr/local a přidat složku bin do své cesty. Další informace najdete v [dokumentaci k homebrew](https://github.com/Homebrew/homebrew/wiki/Installation). Pokud chcete povolit režim pro vývojáře ručně, zadejte tento příkaz do aplikace Terminal: `DevToolsSecurity –enable`  
  
  Pokud aktualizujete na novou verzi sady Visual Studio, musíte také aktualizovat na aktuální verzi vzdáleného agenta. Chcete-li aktualizovat vzdáleného agenta, opakujte postup stažení a instalace vzdáleného agenta.  
  
## <a name="start-the-remote-agent"></a><a name="Start"></a> Spustit vzdáleného agenta  
 Aby bylo možné sestavit a spustit kód pro iOS, musí být spuštěný vzdálený Agent pro Visual Studio. Aby bylo možné komunikovat, musí být aplikace Visual Studio spárována se vzdáleným agentem. Ve výchozím nastavení je vzdálený agent spuštěn v režimu zabezpečeného připojení, což vyžaduje, aby kód PIN byl spárován se sadou Visual Studio.  
  
### <a name="to-start-the-remote-agent"></a><a name="RemoteAgentStartServer"></a> Spuštění vzdáleného agenta  
  
- Z aplikace terminálu na Macu zadejte:  
  
   `vcremote`  
  
   Tím se spustí vzdálený agent s výchozím adresářem buildu ~/vcremote. Další možnosti konfigurace najdete v tématu [Konfigurace vzdáleného agenta na počítači Mac](#ConfigureMac).  
  
  Při prvním spuštění agenta a při každém vytvoření nového certifikátu klienta budete mít k dispozici požadované informace pro konfiguraci agenta v aplikaci Visual Studio, včetně názvu hostitele, portu a kódu PIN.  
  
  ![Použití vcremote k vygenerování zabezpečeného kódu PIN](../cross-platform/media/cppmdd-vcremote-generateclientcert.png "CPPMDD_vcremote_generateClientCert")  
  
  Pokud máte v úmyslu nakonfigurovat vzdáleného agenta v aplikaci Visual Studio pomocí názvu hostitele, otestujte počítač Mac z Windows pomocí názvu hostitele a ověřte, zda je dostupný. V opačném případě bude možná potřeba místo toho použít IP adresu.  
  
  Vygenerovaný kód PIN slouží pouze k jednorázovému použití a je platný pouze po dobu omezeného času. Pokud aplikaci Visual Studio nespárujte se vzdáleným agentem dřív, než vyprší časový limit, budete muset vygenerovat nový PIN kód. Další informace najdete v tématu [vygenerování nového bezpečnostního kódu PIN](#GeneratePIN).  
  
  Můžete použít vzdáleného agenta v nezabezpečeném režimu. V nezabezpečeném režimu může být vzdálený agent spárován se systémem Visual Studio bez kódu PIN.  
  
#### <a name="to-disable-secured-connection-mode"></a>Zakázání režimu zabezpečeného připojení  
  
- Pokud chcete v vcremote zakázat režim zabezpečeného připojení, zadejte tento příkaz do aplikace Terminal na vašem počítači Mac:  
  
     `vcremote --secure false`  
  
#### <a name="to-enable-secured-connection-mode"></a>Postup povolení režimu zabezpečeného připojení  
  
- Pokud chcete povolit režim zabezpečeného připojení, zadejte tento příkaz:  
  
   `vcremote --secure true`  
  
  Jakmile spustíte vzdáleného agenta, můžete ho použít ze sady Visual Studio, dokud ho nezastavíte.  
  
#### <a name="to-stop-the-remote-agent"></a>Zastavení vzdáleného agenta  
  
- V okně terminálu vcremote je spuštěná v, zadejte `Control+C` .  
  
## <a name="configure-the-remote-agent-in-visual-studio"></a><a name="ConfigureVS"></a> Konfigurace vzdáleného agenta v aplikaci Visual Studio  
 Pokud se chcete připojit ke vzdálenému agentovi ze sady Visual Studio, musíte v možnostech sady Visual Studio zadat vzdálenou konfiguraci.  
  
#### <a name="to-configure-the-remote-agent-from-visual-studio"></a>Konfigurace vzdáleného agenta ze sady Visual Studio  
  
1. Pokud agent na Macu ještě neběží, postupujte podle kroků v části [spuštění vzdáleného agenta](#Start). Aby bylo možné úspěšně spárovat, připojit a sestavit projekt, musí váš počítač Mac používat vcremote pro Visual Studio.  
  
2. Na Macu Získejte název hostitele nebo IP adresu vašeho počítače Mac.  
  
    IP adresu můžete získat pomocí příkazu **ifconfig** v okně terminálu. Použijte adresu inet uvedenou v části aktivní síťové rozhraní.  
  
3. Na řádku nabídek sady Visual Studio vyberte **nástroje**, **Možnosti**.  
  
4. V dialogovém okně **Možnosti** rozbalte položku **různé platformy**, **C++**, **iOS**.  
  
5. Do polí **název hostitele** a **port** zadejte hodnoty určené vzdáleným agentem při jeho spuštění. Název hostitele může být název DNS nebo IP adresa vašeho počítače Mac. Výchozí port je 3030.  
  
   > [!NOTE]
   > Pokud nemůžete testovat počítač Mac pomocí protokolu s názvem hostitele, možná budete muset použít IP adresu.  
  
6. Pokud používáte vzdáleného agenta ve výchozím režimu zabezpečeného připojení, zaškrtněte políčko **zabezpečení** a potom zadejte hodnotu PIN zadanou vzdáleným agentem v poli **kód PIN** . Pokud používáte vzdáleného agenta v nezabezpečeném režimu připojení, zrušte zaškrtnutí políčka **zabezpečení** a nechte pole **připnout** prázdné.  
  
7. Vyberte **dvojici** , chcete-li povolit párování.  
  
    ![Konfigurace připojení vcremote pro buildy iOS](../cross-platform/media/cppmdd-options-ios.PNG "CPPMDD_Options_iOS")  
  
    Párování přetrvává, dokud nezměníte název hostitele nebo port. Pokud v dialogovém okně **Možnosti** změníte název hostitele nebo port, chcete-li změnu vrátit zpět, klikněte na tlačítko **vrátit** a vraťte se k předchozí dvojici.  
  
    Pokud párování neproběhne úspěšně, ověřte, že je vzdálený agent spuštěný, podle kroků v části [spuštění vzdáleného agenta](#Start). Pokud uplynula spousta času od vygenerování kódu PIN vzdáleného agenta, postupujte podle kroků v části [Vytvoření nového bezpečnostního kódu PIN](#GeneratePIN) na Macu a akci opakujte. Pokud používáte název hostitele vašeho počítače Mac, zkuste místo toho použít IP adresu v poli **název hostitele** .  
  
8. Aktualizujte název složky v poli **Remote root** a určete složku používanou vzdáleným agentem ve vašem domovském adresáři (~) na Macu. Ve výchozím nastavení používá vzdálený agent `username` jako vzdálený kořen/Users//vcremote.  
  
9. Kliknutím na **tlačítko OK** uložte nastavení vzdáleného párování připojení.  
  
   Visual Studio používá stejné informace pro připojení ke vzdálenému agentovi na počítači Mac, a to pokaždé, když ho použijete. Pokud nevytvoříte nový certifikát zabezpečení na Macu nebo změníte jeho název hostitele nebo IP adresu, nemusíte si aplikaci Visual Studio spárovat se vzdáleným agentem.  
  
## <a name="generate-a-new-security-pin"></a><a name="GeneratePIN"></a> Vygenerovat nový bezpečnostní kód PIN  
 Když spustíte vzdáleného agenta poprvé, vygenerovaný kód PIN bude platný po omezené době – ve výchozím nastavení je to 10 minut. Pokud aplikaci Visual Studio nespárujte se vzdáleným agentem před vypršením časového limitu, budete muset vygenerovat nový PIN kód.  
  
#### <a name="to-generate-a-new-pin"></a>Vygenerování nového kódu PIN  
  
1. Zastavte agenta nebo otevřete druhé okno terminálu aplikace na Macu a použijte ho k zadání příkazu.  
  
2. V aplikaci Terminal App zadejte tento příkaz:  
  
     `vcremote generateClientCert`  
  
     Vzdálený agent vygeneruje nový dočasný PIN kód. Chcete-li spárovat aplikaci Visual Studio pomocí nového kódu PIN, opakujte postup v části [Konfigurace vzdáleného agenta v aplikaci Visual Studio](#ConfigureVS).  
  
## <a name="generate-a-new-server-certificate"></a><a name="GenerateCert"></a> Vygenerovat nový certifikát serveru  
 Z bezpečnostních důvodů jsou certifikáty serveru, které spárují sadu Visual Studio se vzdáleným agentem, vázané na IP adresu nebo název hostitele vašeho počítače Mac. Pokud se tyto hodnoty změní, musíte vygenerovat nový certifikát serveru a pak znovu nakonfigurovat aplikaci Visual Studio novými hodnotami.  
  
#### <a name="to-generate-a-new-server-certificate"></a>Vygenerování nového certifikátu serveru  
  
1. Zastavte agenta vcremote.  
  
2. V aplikaci Terminal App zadejte tento příkaz:  
  
     `vcremote resetServerCert`  
  
3. Po zobrazení výzvy k potvrzení zadejte `Y` .  
  
4. V aplikaci Terminal App zadejte tento příkaz:  
  
     `vcremote generateClientCert`  
  
     Tím se vygeneruje nový dočasný PIN kód.  
  
5. Chcete-li spárovat aplikaci Visual Studio pomocí nového kódu PIN, opakujte postup v části [Konfigurace vzdáleného agenta v aplikaci Visual Studio](#ConfigureVS).  
  
## <a name="configure-the-remote-agent-on-the-mac"></a><a name="ConfigureMac"></a> Konfigurace vzdáleného agenta na Macu  
 Vzdálený Agent můžete nakonfigurovat pomocí různých možností příkazového řádku. Můžete například zadat port pro naslouchání požadavkům sestavení a určit maximální počet sestavení, která mají být v systému souborů uchovávána. Ve výchozím nastavení je limit 10 Builds. Vzdálený agent odebere sestavení, která překračují maximum při vypnutí.  
  
#### <a name="to-configure-the-remote-agent"></a>Konfigurace vzdáleného agenta  
  
- Úplný seznam příkazů vzdáleného agenta zobrazíte tak, že v terminálu aplikace zadáte:  
  
     `vcremote --help`  
  
- Pokud chcete zakázat zabezpečený režim a povolit jednoduchá připojení založená na protokolu HTTP, zadejte:  
  
     `vcremote --secure false`  
  
     Když použijete tuto možnost, zrušte zaškrtnutí políčka **zabezpečení** a nechte pole **připnout** prázdné při konfiguraci agenta v aplikaci Visual Studio.  
  
- Pokud chcete zadat umístění pro soubory vzdáleného agenta, zadejte:  
  
     `vcremote --serverDir directory_path`  
  
     kde *directory_path* je umístění na Macu k umístění souborů protokolu, sestavení a certifikátů serveru. Ve výchozím nastavení je toto umístění/Users/*username*/vcremote. Sestavení jsou uspořádána podle čísla sestavení v tomto umístění.  
  
- Pokud chcete k zachycení `stdout` a `stderr` souboru s názvem Server. log použít proces na pozadí, zadejte:  
  
     `vcremote > server.log 2>&1 &`  
  
     Soubor Server. log může pomoct při řešení problémů s sestavením.  
  
- Chcete-li spustit agenta pomocí konfiguračního souboru místo parametrů příkazového řádku, zadejte:  
  
     `vcremote --config config_file_path`  
  
     kde *config_file_path* je cesta ke konfiguračnímu souboru ve formátu JSON. Možnosti spuštění a jejich hodnoty nesmí obsahovat pomlčky.  
  
## <a name="see-also"></a>Viz také  
 [Instalace komponenty Visual C++ for Cross-Platform Mobile Development](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md)
