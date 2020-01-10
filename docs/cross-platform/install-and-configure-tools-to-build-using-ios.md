---
title: Instalace a konfigurace nástrojů pro sestavení pomocí iOS | Microsoft Docs
ms.custom: ''
ms.date: 10/17/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: d0c311c9-9eb9-42c5-ba07-25604362cd28
author: corob-msft
ms.author: corob
manager: jillfra
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: e869a02475917f2444bedbb1bc9b7373b893d098
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75846896"
---
# <a name="install-and-configure-tools-to-build-using-ios"></a>Instalace a konfigurace nástrojů pro vytváření pomocí iOS

Můžete použít Visual Studio s **vývojem mobilních C++**  aplikací pro různé platformy s nástroji k úpravám, ladění a nasazování kódu iOS do simulátoru iOS nebo do zařízení s iOS. Z důvodu licenčních omezení se ale kód musí sestavit a spustit vzdáleně na Macu. Pokud chcete vytvářet a spouštět aplikace pro iOS pomocí sady Visual Studio, musíte na Macu nastavit a nakonfigurovat vzdáleného agenta [vcremote](https://www.npmjs.com/package/vcremote). Vzdálený Agent zpracovává požadavky na sestavení ze sady Visual Studio a spustí aplikaci na zařízení s iOS připojeném k počítači Mac nebo v simulátoru iOS na Macu.

> [!NOTE]
> Informace o použití služeb Mac hostovaných v cloudu místo Mac najdete v tématu [Konfigurace sady Visual Studio pro připojení k vašemu cloudu Mac hosta](/visualstudio/cross-platform/tools-for-cordova/tips-workarounds/host-a-mac-in-the-cloud?view=toolsforcordova-2017#configure-visual-studio-to-connect-to-your-cloud-hosted-mac). Pokyny jsou pro sestavování pomocí Visual Studio Tools pro Apache Cordova. Chcete-li použít pokyny k sestavení C++pomocí, nahraďte `vcremote` `remotebuild`.

Až nainstalujete nástroje pro sestavení pomocí iOS, přečtěte si tento článek, kde najdete způsoby, jak rychle nakonfigurovat a aktualizovat vzdáleného agenta pro vývoj pro iOS v aplikaci Visual Studio a na Macu.

## <a name="prerequisites"></a>Požadavky

Pokud chcete nainstalovat a používat vzdáleného agenta pro vývoj kódu pro iOS, musíte nejdřív splnit tyto požadavky:

- Počítač Mac se systémem macOS Mojave verze 10,14 nebo novější

- [Apple ID](https://appleid.apple.com/)

- Aktivní účet [programu Apple Developer program](https://developer.apple.com/programs/)

   Můžete získat bezplatný účet, který umožňuje aplikacím zkušebního načtení zařízení se systémem iOS jenom pro testování, ale ne pro distribuci.

- [Xcode](https://developer.apple.com/xcode/downloads/) verze 10.2.1 nebo novější

   Xcode je možné stáhnout z App Storu.

- Nástroje příkazového řádku Xcode

   Pokud chcete nainstalovat nástroje příkazového řádku Xcode, otevřete aplikaci Terminal na Macu a zadejte následující příkaz:

   `xcode-select --install`

- Účet Apple ID nakonfigurovaný v Xcode jako podpisová identita pro podepisování aplikací

   Chcete-li zobrazit nebo nastavit podpisovou identitu v Xcode, otevřete nabídku **Xcode** a vyberte možnost **Předvolby**. Vyberte **účty** a zvolte vaše Apple ID a pak klikněte na tlačítko **Zobrazit podrobnosti** . Podrobné pokyny najdete v tématu [Přidání vašeho účtu Apple ID](https://help.apple.com/xcode/mac/current/#/devaf282080a) .
   
   Podrobné informace o požadavcích na podpis najdete v tématu [co je podepisování aplikací](https://help.apple.com/xcode/mac/current/#/dev3a05256b8). 

- Pokud pro vývoj používáte zařízení s iOS, zřizuje se zřizovací profil nakonfigurovaný v Xcode pro vaše zařízení.

   Xcode poskytuje automatické podepisování, kde podle potřeby vytváří podpisové certifikáty. Podrobné informace o automatickém podepisování Xcode najdete v tématu [Automatické podepisování](https://help.apple.com/xcode/mac/current/#/dev80cc24546).

   Pokud chcete provést ruční podepisování, musíte pro svoji aplikaci vytvořit zřizovací profil. Podrobné informace o vytváření zřizovacích profilů najdete v tématu [Vytvoření vývojového zřizovacího profilu](https://help.apple.com/developer-account/#/devf2eb157f8). 

- [Node. js](https://nodejs.org/) verze 8.11.3 a npm verze 5.6.0

   Nainstalujte 8.11.3 verze Node. js na Macu. Při instalaci balíčku Node. js by měl být součástí npm verze 5.6.0. Jiné verze Node. js a npm nemusí podporovat některé moduly používané ve vzdáleném agentovi `vcremote`, což může způsobit selhání instalace `vcremote`.

## <a name="Install"></a>Instalace vzdáleného agenta pro iOS

Když nainstalujete vývoj pro mobilní zařízení C++ pomocí úlohy, Visual Studio může komunikovat s [vcremote](https://www.npmjs.com/package/vcremote), vzdáleným agentem běžícím na Macu, aby přenesl soubory, vytvořil a spouštěl aplikaci pro iOS a odesílal příkazy pro ladění.

Než nainstalujete vzdáleného agenta, ujistěte se, že jste splnili [požadavky](#prerequisites) a dokončili kroky instalace v části [Instalace mobilního vývoje pro různé platformy C++pomocí ](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md#install-the-tools).

### <a name="DownloadInstall"></a>Stažení a instalace vzdáleného agenta

- Z aplikace terminálu na Macu zadejte:

   `sudo npm install -g --unsafe-perm vcremote`

   Přepínač globální instalace ( **-g**) se doporučuje, ale není povinný.

   Během instalace se `vcremote` nainstaluje a v počítači Mac se aktivuje vývojářský režim. Nainstalují se taky [homebrew](https://brew.sh/) a dva balíčky npm, `vcremote-lib` a `vcremote-utils`. Po dokončení instalace je bezpečné ignorovat všechna upozornění týkající se přeskočení volitelných závislostí.

   > [!NOTE]
   > K instalaci homebrew musíte mít přístup sudo (správce). Pokud potřebujete nainstalovat `vcremote` bez sudo, můžete homebrew nainstalovat ručně v umístění usr/local a přidat složku bin do své cesty. Další informace najdete v [dokumentaci k homebrew](https://github.com/Homebrew/homebrew/wiki/Installation). Pokud chcete povolit režim pro vývojáře ručně, zadejte tento příkaz do aplikace Terminal: `DevToolsSecurity -enable`

Pokud aktualizujete na novou verzi sady Visual Studio, musíte také aktualizovat na aktuální verzi vzdáleného agenta. Chcete-li aktualizovat vzdáleného agenta, opakujte postup stažení a instalace vzdáleného agenta.

## <a name="Start"></a>Spustit vzdáleného agenta

Aby bylo možné sestavit a spustit kód pro iOS, musí být spuštěný vzdálený Agent pro Visual Studio. Aby bylo možné komunikovat, musí být aplikace Visual Studio spárována se vzdáleným agentem. Ve výchozím nastavení je vzdálený agent spuštěn v režimu zabezpečeného připojení, což vyžaduje, aby kód PIN byl spárován se sadou Visual Studio.

### <a name="RemoteAgentStartServer"></a>Spuštění vzdáleného agenta

- Z aplikace terminálu na Macu zadejte:

   `vcremote`

   Tento příkaz spustí vzdáleného agenta s výchozím adresářem buildu `~/vcremote`. Další možnosti konfigurace najdete v tématu [Konfigurace vzdáleného agenta na počítači Mac](#ConfigureMac).

Při prvním spuštění agenta a pokaždé, když vytvoříte nový certifikát klienta, budete mít k dispozici požadované informace pro konfiguraci agenta v aplikaci Visual Studio, včetně názvu hostitele, portu a kódu PIN.

![Použití vcremote k vygenerování zabezpečeného kódu PIN](../cross-platform/media/cppmdd_vcremote_generateclientcert.png "CPPMDD_vcremote_generateClientCert")

Pokud máte v úmyslu nakonfigurovat vzdáleného agenta v aplikaci Visual Studio pomocí názvu hostitele, otestujte počítač Mac z Windows pomocí názvu hostitele a ověřte, zda je dostupný. V opačném případě bude možná potřeba místo toho použít IP adresu.

Vygenerovaný kód PIN slouží pouze k jednorázovému použití a je platný pouze po dobu omezeného času. Pokud aplikaci Visual Studio nespárujte se vzdáleným agentem dřív, než vyprší časový limit, budete muset vygenerovat nový PIN kód. Další informace najdete v tématu [vygenerování nového bezpečnostního kódu PIN](#GeneratePIN).

Můžete použít vzdáleného agenta v nezabezpečeném režimu. V nezabezpečeném režimu může být vzdálený agent spárován se systémem Visual Studio bez kódu PIN.

#### <a name="to-disable-secured-connection-mode"></a>Zakázání režimu zabezpečeného připojení

- Pokud chcete v `vcremote`zakázat režim zabezpečeného připojení, zadejte tento příkaz do aplikace Terminal na vašem počítači Mac:

   `vcremote --secure false`

#### <a name="to-enable-secured-connection-mode"></a>Postup povolení režimu zabezpečeného připojení

- Pokud chcete povolit režim zabezpečeného připojení, zadejte tento příkaz:

   `vcremote --secure true`

Jakmile spustíte vzdáleného agenta, můžete ho použít ze sady Visual Studio, dokud ho nezastavíte.

#### <a name="to-stop-the-remote-agent"></a>Zastavení vzdáleného agenta

- V okně terminálu `vcremote` v systému zadejte **ovládací prvek**+**C**.

## <a name="ConfigureVS"></a>Konfigurace vzdáleného agenta v aplikaci Visual Studio

Pokud se chcete připojit ke vzdálenému agentovi ze sady Visual Studio, musíte v možnostech sady Visual Studio zadat vzdálenou konfiguraci.

### <a name="to-configure-the-remote-agent-from-visual-studio"></a>Konfigurace vzdáleného agenta ze sady Visual Studio

1. Pokud agent na Macu ještě neběží, postupujte podle kroků v části [spuštění vzdáleného agenta](#Start). Aby bylo možné úspěšně spárovat, připojit a sestavit projekt, musí být spuštěný počítač Mac `vcremote` pro Visual Studio.

1. Na Macu Získejte název hostitele nebo IP adresu vašeho počítače Mac.

   IP adresu můžete získat pomocí příkazu **ifconfig** v okně terminálu. Použijte adresu inet uvedenou v části aktivní síťové rozhraní.

1. Na řádku nabídek sady Visual Studio vyberte **nástroje**, **Možnosti**.

1. V dialogovém okně **Možnosti** rozbalte položku **různé platformy**, **C++** **iOS**.

1. Do polí **název hostitele** a **port** zadejte hodnoty určené vzdáleným agentem při jeho spuštění. Název hostitele může být název DNS nebo IP adresa vašeho počítače Mac. Výchozí port je 3030.

   > [!NOTE]
   > Pokud nemůžete testovat počítač Mac pomocí protokolu s názvem hostitele, možná budete muset použít IP adresu.

1. Pokud používáte vzdáleného agenta ve výchozím režimu zabezpečeného připojení, zaškrtněte políčko **zabezpečení** a potom zadejte hodnotu PIN zadanou vzdáleným agentem v poli **kód PIN** . Pokud používáte vzdáleného agenta v nezabezpečeném režimu připojení, zrušte zaškrtnutí políčka **zabezpečení** a nechte pole **připnout** prázdné.

1. Vyberte **dvojici** , chcete-li povolit párování.

   ![Konfigurace připojení vcremote pro buildy iOS](../cross-platform/media/cppmdd_options_ios.PNG "CPPMDD_Options_iOS")

   Párování přetrvává, dokud nezměníte název hostitele nebo port. Pokud v dialogovém okně **Možnosti** změníte název hostitele nebo port, chcete-li změnu vrátit zpět, klikněte na tlačítko **vrátit** a vraťte se k předchozí dvojici.

   Pokud párování neproběhne úspěšně, ověřte, že je vzdálený agent spuštěný, podle kroků v části [spuštění vzdáleného agenta](#Start). Pokud uplynula spousta času od vygenerování kódu PIN vzdáleného agenta, postupujte podle kroků v části [Vytvoření nového bezpečnostního kódu PIN](#GeneratePIN) na Macu a akci opakujte. Pokud používáte název hostitele vašeho počítače Mac, zkuste místo toho použít IP adresu v poli **název hostitele** .

1. Aktualizujte název složky v poli **Remote root** a určete složku používanou vzdáleným agentem v domovském adresáři ( *~* ) na Macu. Vzdálený agent ve výchozím nastavení používá `/Users/<username>/vcremote` jako vzdálený kořenový adresář.

1. Kliknutím na **tlačítko OK** uložte nastavení vzdáleného párování připojení.

Visual Studio používá stejné informace pro připojení ke vzdálenému agentovi na počítači Mac, a to pokaždé, když ho použijete. Pokud nevytvoříte nový certifikát zabezpečení na Macu nebo změníte jeho název hostitele nebo IP adresu, nemusíte si aplikaci Visual Studio spárovat se vzdáleným agentem.

## <a name="GeneratePIN"></a>Vygenerovat nový bezpečnostní kód PIN

Když spustíte vzdáleného agenta poprvé, vygenerovaný kód PIN bude platný po omezené době – ve výchozím nastavení je to 10 minut. Pokud aplikaci Visual Studio nespárujte se vzdáleným agentem před vypršením časového limitu, budete muset vygenerovat nový PIN kód.

### <a name="to-generate-a-new-pin"></a>Vygenerování nového kódu PIN

1. Zastavte agenta nebo otevřete druhé okno terminálu aplikace na Macu a použijte ho k zadání příkazu.

1. V aplikaci Terminal App zadejte tento příkaz:

   `vcremote generateClientCert`

   Vzdálený agent vygeneruje nový dočasný PIN kód. Chcete-li spárovat aplikaci Visual Studio pomocí nového kódu PIN, opakujte postup v části [Konfigurace vzdáleného agenta v aplikaci Visual Studio](#ConfigureVS).

## <a name="GenerateCert"></a>Vygenerovat nový certifikát serveru

Z bezpečnostních důvodů jsou certifikáty serveru, které spárují sadu Visual Studio se vzdáleným agentem, vázané na IP adresu nebo název hostitele vašeho počítače Mac. Pokud se tyto hodnoty změní, musíte vygenerovat nový certifikát serveru a pak znovu nakonfigurovat aplikaci Visual Studio novými hodnotami.

### <a name="to-generate-a-new-server-certificate"></a>Vygenerování nového certifikátu serveru

1. Zastavte agenta `vcremote`.

1. V aplikaci Terminal App zadejte tento příkaz:

   `vcremote resetServerCert`

1. Po zobrazení výzvy k potvrzení zadejte `Y`.

1. V aplikaci Terminal App zadejte tento příkaz:

   `vcremote generateClientCert`

   Tento příkaz vygeneruje nový dočasný PIN kód.

1. Chcete-li spárovat aplikaci Visual Studio pomocí nového kódu PIN, opakujte postup v části [Konfigurace vzdáleného agenta v aplikaci Visual Studio](#ConfigureVS).

## <a name="ConfigureMac"></a>Konfigurace vzdáleného agenta na Macu

Vzdálený Agent můžete nakonfigurovat pomocí různých možností příkazového řádku. Můžete například zadat port pro naslouchání požadavkům sestavení a určit maximální počet sestavení, která mají být v systému souborů uchovávána. Ve výchozím nastavení je limit 10 Builds. Vzdálený agent odebere sestavení, která překračují maximum při vypnutí.

### <a name="to-configure-the-remote-agent"></a>Konfigurace vzdáleného agenta

- Úplný seznam příkazů vzdáleného agenta zobrazíte tak, že v terminálu aplikace zadáte:

   `vcremote --help`

- Pokud chcete zakázat zabezpečený režim a povolit jednoduchá připojení založená na protokolu HTTP, zadejte:

   `vcremote --secure false`

   Když použijete tuto možnost, zrušte zaškrtnutí políčka **zabezpečení** a nechte pole **připnout** prázdné při konfiguraci agenta v aplikaci Visual Studio.

- Pokud chcete zadat umístění pro soubory vzdáleného agenta, zadejte:

   `vcremote --serverDir directory_path`

   kde *directory_path* je umístění na Macu k umístění souborů protokolu, sestavení a certifikátů serveru. Ve výchozím nastavení je toto umístění `/Users/<username>/vcremote`. Sestavení jsou uspořádána podle čísla sestavení v tomto umístění.

- Chcete-li použít proces na pozadí k zachycení `stdout` a `stderr` souboru s názvem Server. log, zadejte:

   `vcremote > server.log 2>&1 &`

   Soubor Server. log může pomoct při řešení problémů s sestavením.

- Chcete-li spustit agenta pomocí konfiguračního souboru místo parametrů příkazového řádku, zadejte:

   `vcremote --config config_file_path`

   kde *config_file_path* je cesta ke konfiguračnímu souboru ve formátu JSON. Možnosti spuštění a jejich hodnoty nesmí obsahovat pomlčky.

## <a name="troubleshoot-the-remote-agent"></a>Řešení potíží se vzdáleným agentem

### <a name="debugging-on-an-ios-device"></a>Ladění na zařízení s iOS

Pokud ladění na zařízení se systémem iOS nefunguje, mohou nastat problémy s nástrojem [ideviceinstaller](https://github.com/libimobiledevice/ideviceinstaller), který se používá ke komunikaci se zařízením s iOS. Tento nástroj se obvykle instaluje z homebrew během instalace `vcremote`. Použijte následující postup jako alternativní řešení.

Otevřete aplikaci Terminal a aktualizujte `ideviceinstaller` a její závislosti spuštěním následujících příkazů v uvedeném pořadí:

1. Ujistěte se, že je aktualizace homebrew

   `brew update`

1. Odinstalace `libimobiledevice` a `usbmuxd`

   `brew uninstall --ignore-dependencies libimobiledevice`

   `brew uninstall --ignore-dependencies usbmuxd`

1. Instalace nejnovější verze `libimobiledevice` a `usbmuxd`

   `brew install --HEAD usbmuxd`

   `brew unlink usbmuxd`

   `brew link usbmuxd`

   `brew install --HEAD libimobiledevice`

1. Odinstalace a přeinstalace `ideviceinstaller`

   `brew uninstall ideviceinstaller`

   `brew install ideviceinstaller`

Ověřte, že `ideviceinstaller` můžou komunikovat se zařízením tím, že se pokusí zobrazit seznam aplikací nainstalovaných v zařízení:

`ideviceinstaller -l`

Pokud `ideviceinstaller` chyby, ke kterým nemůže přistupovat `/var/db/lockdown`složky, změňte oprávnění ve složce pomocí:

`sudo chmod 777 /var/db/lockdown`
    
Pak znovu ověřte, jestli `ideviceinstaller` může komunikovat se zařízením.

## <a name="see-also"></a>Viz také:

- [Instalace vývoje mobilních aplikací pro různé platformy pomocíC++](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md)
