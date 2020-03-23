---
title: Vzdálené pracovní prostory pro R
description: Jak nastavit vzdálené pracovní prostory R a připojit se k němu z visual studia.
ms.date: 12/04/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 686f98aaaade035f1632139d255ccff8b37eddf3
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75850055"
---
# <a name="set-up-remote-workspaces"></a>Nastavení vzdálených pracovních prostorů

Tento článek vysvětluje, jak nakonfigurovat vzdálený server s protokolem SSL a příslušnou službou R. To umožňuje nástroje R pro visual studio (RTVS) pro připojení ke vzdálenému pracovnímu prostoru na tomto serveru.

## <a name="remote-computer-requirements"></a>Požadavky na vzdálený počítač

- Windows 10, Windows Server 2016 nebo Windows Server 2012 R2. RTVS také vyžaduje, aby
- [Rozhraní .NET Framework 4.6.1](https://www.microsoft.com/download/details.aspx?id=49981) nebo vyšší

## <a name="install-an-ssl-certificate"></a>Instalace certifikátu SSL

RTVS vyžaduje, aby veškerá komunikace se vzdáleným serverem probíhá přes protokol HTTP, který vyžaduje certifikát SSL na serveru. Můžete použít buď certifikát podepsaný důvěryhodnou certifikační autoritou (doporučenou), nebo certifikát podepsaný svým držitelem. (Certifikát podepsaný svým držitelem způsobí, že rtvs vydávat upozornění při připojení.) S jedním z nich je pak nutné jej nainstalovat do počítače a povolit přístup k jeho soukromému klíči.

### <a name="obtain-a-trusted-certificate"></a>Získání důvěryhodného certifikátu

Důvěryhodný certifikát vydává certifikační autorita (informace o pozadí najdete [na certifikačních úřadech na Wikipedii).](https://en.wikipedia.org/wiki/Certificate_authority) Stejně jako získání vládního identifikačního průkazu, vydávání důvěryhodného certifikátu zahrnuje více procesů a možných poplatků, ale ověřuje pravost žádosti a žadateli.

Pole klíče, které musí být v certifikátu, je plně kvalifikovaný název domény počítače serveru R. Certifikační autorita vyžaduje důkaz, že jste oprávněni vytvořit nový server pro doménu, do které server patří.

Další informace naleznete v tématu [certifikáty veřejných klíčů](https://en.wikipedia.org/wiki/Public_key_certificate) na Wikipedii.

## <a name="install-an-ssl-certificate-on-windows"></a>Instalace certifikátu SSL do systému Windows

Certifikát SSL musí být nainstalován ručně v systému Windows. Podle následujících pokynů nainstalujte certifikát SSL.

### <a name="obtain-a-self-signed-certificate-windows"></a>Získání certifikátu podepsaného svým držitelem (Windows)

Pokud máte důvěryhodný certifikát, tuto část přeskočte. Ve srovnání s certifikátem od důvěryhodné autority je certifikát podepsaný svým držitelem jako vytvoření identifikační karty pro sebe. Tento proces je samozřejmě mnohem jednodušší než práce s důvěryhodnou autoritou, ale také postrádá silné ověřování, což znamená, že útočník může nahradit svůj vlastní certifikát za nepodepsaný certifikát a zachytit veškerý provoz mezi klientem a Server. Certifikát *podepsaný svým držitelem by proto měl být používán pouze pro testovací scénáře v důvěryhodné síti a nikdy v produkčním prostředí.*

Z tohoto důvodu rtvs vždy vydá následující upozornění při připojování k serveru s certifikátem podepsaným svým držitelem:

![Dialogové okno upozornění na certifikát podepsaný svým držitelem](media/workspaces-remote-self-signed-certificate-warning.png)

Jak vydat certifikát podepsaný svým držitelem:

1. Přihlaste se k počítači serveru R pomocí účtu správce.
1. Otevřete nový příkazový řádek prostředí PowerShell správce `"remote-machine-name"` a vydejte následující příkaz, který nahradí plně kvalifikovaný název domény počítače serveru.

    ```ps
    New-SelfSignedCertificate -CertStoreLocation Cert:\LocalMachine\My -DnsName "remote-machine-name"
    ```

1. Pokud jste v počítači se serverem R nikdy předtím nespouštěli prostředí PowerShell, spusťte následující příkaz, který explicitně povolí spuštění příkazů:

    ```ps
    Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
    ```

Informace o pozadí najdete v [tématu certifikáty podepsané svým](https://en.wikipedia.org/wiki/Self-signed_certificate) držitelem na Wikipedii.

### <a name="install-the-certificate"></a>Instalace certifikátu

Chcete-li certifikát nainstalovat do vzdáleného počítače, spusťte *příkaz certlm.msc* (správce certifikátů) z příkazového řádku. Klikněte pravým tlačítkem myši na složku **Osobní** a vyberte příkaz**Import** ovat **všechny úkoly:** > 

![Příkaz importovat certifikát](media/workspaces-remote-certificate-import.png)

### <a name="grant-permissions-to-read-the-ssl-certificates-private-key"></a>Udělit oprávnění ke čtení soukromého klíče certifikátu SSL

Po importu certifikátu `NETWORK SERVICE` udělte oprávnění k účtu ke čtení soukromého klíče, jak je popsáno v následujících pokynech. `NETWORK_SERVICE`je účet používaný ke spuštění zprostředkovatele služeb R Services, což je služba, která ukončuje příchozí připojení SSL k počítači serveru.

1. Spusťte *soubor certlm.msc* (Správce certifikátů) z příkazového řádku správce.
1. Rozbalte **osobní** > **certifikáty**, klikněte pravým tlačítkem myši na certifikát a vyberte **možnost Všechny úkoly** > spravovat soukromé**klíče**.
1. Klikněte pravým tlačítkem myši na certifikát a v části **Všechny úkoly**vyberte příkaz **Spravovat soukromé klíče** .
1. V zobrazeném dialogovém okně `NETWORK SERVICE` vyberte **Přidat** a zadat jako název účtu:

    ![Dialogové okno Spravovat soukromé klávesy, přidání NETWORK_SERVICE](media/workspaces-remote-manage-private-key-dialog.png)

1. Výběrem **možnosti OK** dvakrát zavřete dialogová okna a potvrďte změny.

## <a name="install-an-ssl-certificate-on-ubuntu"></a>Instalace certifikátu SSL na Ubuntu

Balíček `rtvs-daemon` nainstaluje certifikát podepsaný svým držitelem ve výchozím nastavení jako součást instalace.

### <a name="obtain-a-self-signed-certificate-ubuntu"></a>Získání certifikátu podepsaného svým držitelem (Ubuntu)

Výhody a rizika používání certifikátu podepsaného svým držitelem najdete v popisu systému Windows. Balíček `rtvs-daemon` generuje a konfiguruje certifikát podepsaný svým držitelem během instalace. To budete muset provést pouze v případě, že chcete nahradit certifikát podepsaný svým držitelem s automatickým podpisem.

Vlastní vydání certifikátu podepsaného svým držitelem:

1. SSH nebo se přihlaste k počítači s Linuxem.
2. Instalační `ssl-cert` balíček:

    ```sh
    sudo apt-get install ssl-cert
    ```

3. Spuštěním `make-ssl-cert` vygenerujete výchozí certifikát SSL podepsaný svým držitelem:

    ```sh
    sudo make-ssl-cert generate-default-snakeoil --force-overwrite
    ```

4. Převeďte generované soubory klíče a PEM na PFX. Vygenerované PFX by měly být ve vaší domovské složce:

    ```sh
    openssl pkcs12 -export -out ~/ssl-cert-snakeoil.pfx -inkey /etc/ssl/private/ssl-cert-snakeoil.key -in /etc/ssl/certs/ssl-cert-snakeoil.pem -password pass:SnakeOil
    ```

### <a name="configure-rtvs-daemon"></a>Konfigurace daemonu RTVS

Cesta k souboru certifikátu SSL (cesta k PFX) musí být nastavena v *parametru /etc/rtvs/rtvsd.config.json*. Aktualizovat `X509CertificateFile` `X509CertificatePassword` a s cestou souboru a heslo, resp.

```json
{
  "logging": { "logFolder": "/tmp" },
  "security": {
    "allowedGroup": "",
    "X509CertificateFile": "/etc/rtvs/ssl-cert-snakeoil.pfx",
    "X509CertificatePassword": "SnakeOil"
  },
  "startup": { "name": "rtvsd" },
  "urls": "https://0.0.0.0:5444"
}
```

Uložte soubor a restartujte daemon , `sudo systemctl restart rtvsd`.

## <a name="install-r-services-on-windows"></a>Instalace služeb R v systému Windows

Chcete-li spustit kód R, musí mít vzdálený počítač nainstalovaný překladač R následujícím způsobem:

1. Stáhněte a nainstalujte jednu z následujících možností:

   - [Microsoft R Open](https://mran.microsoft.com/open/)
   - [CRAN R pro Windows](https://cran.r-project.org/bin/windows/base/)

     Oba mají stejné funkce, ale Microsoft R Open těží z dalších hardwarově akcelerovaných lineárních algebraových knihoven s laskavým svolením [knihovny jádra Intel Math](https://software.intel.com/intel-mkl).

2. Spusťte [instalační program služby R services](https://github.com/Microsoft/RTVS/blob/master/doc/rtvsd/rtvs-remote-downloads.md) a po zobrazení výzvy restartujte počítač. Instalační program provádí následující akce:

    - Vytvořte složku v *%PROGRAMFILES%\R Nástroje pro\\ Visual Studio\1.0* a zkopírujte všechny požadované binární soubory.
    - `RHostBrokerService` Nainstalujte `RUserProfileService` a nakonfigurujte automatické spuštění.
    - Nakonfigurujte službu `seclogon` tak, aby se spouštěla automaticky.
    - Přidejte do příchozích pravidel brány firewall na výchozím portu 5444 přidejte *microsoft.r.host.exe* a *microsoft.r.host.broker.exe.*

Služby R se spouštějí automaticky po restartování počítače:

- **R Host Broker Service** zpracovává všechny přenosy HTTPS mezi Visual Studio a proces, kde kód R běží v počítači.
- **R Služba profilů uživatelů** je privilegovaná součást, která zpracovává vytváření uživatelských profilů systému Windows. Služba je volána při prvním přihlášení nového uživatele k počítači serveru R.

Tyto služby můžete vidět v konzole pro správu služeb (*compmgmt.msc*).

## <a name="install-r-services-on-linux"></a>Instalace služeb R na Linuxu

Chcete-li spustit kód R, musí mít vzdálený počítač nainstalovaný překladač R následujícím způsobem:

1. Stáhněte a nainstalujte jednu z následujících možností:

   - [Microsoft R Open](https://mran.microsoft.com/open/)
   - [CRAN R pro Windows](https://cran.r-project.org/bin/linux/ubuntu/)

     Oba mají stejné funkce, ale Microsoft R Open těží z dalších hardwarově akcelerovaných lineárních algebraových knihoven s laskavým svolením [knihovny jádra Intel Math](https://software.intel.com/intel-mkl).

2. Postupujte podle pokynů na [vzdálené službě R pro Linux](setting-up-remote-r-service-on-linux.md), která zahrnuje fyzické počítače Ubuntu, virtuální počítače Azure Ubuntu, podsystém Windows pro Linux (WSL) a kontejnery Dockeru, včetně kontejnerů spuštěných v úložišti kontejnerů Azure.

## <a name="configure-r-services"></a>Konfigurace služeb R

Pokud jsou služby R spuštěné ve vzdáleném počítači, musíte také vytvořit uživatelské účty, nastavit pravidla brány firewall, nakonfigurovat sítě Azure a nakonfigurovat certifikát SSL.

1. Uživatelské účty: Vytvořte účty pro každého uživatele, který přistupuje ke vzdálenému počítači. Můžete vytvořit buď standardní (neprivilegované) místní uživatelské účty, nebo můžete připojit počítač serveru R k `Users` doméně a přidat příslušné skupiny zabezpečení do skupiny zabezpečení.

1. Pravidla brány firewall: `R Host Broker` Ve výchozím nastavení naslouchá na portu TCP 5444. Proto se ujistěte, že jsou povolena pravidla brány firewall systému Windows pro příchozí i odchozí přenosy (odchozí je potřeba pro instalaci balíčků a podobných scénářů).  Instalační služba služby R nastaví tato pravidla automaticky pro vestavěnou bránu firewall systému Windows. Pokud však používáte bránu firewall jiného výrobce, otevřete port 5444 pro `R Host Broker` ruční použití.

1. Konfigurace Azure: Pokud je váš vzdálený počítač virtuální počítač v Azure, otevřete port 5444 pro příchozí provoz v rámci sítě Azure, který je nezávislý na bráně firewall systému Windows. Podrobnosti najdete v [tématu Filtrování síťového provozu se skupinou zabezpečení sítě](/azure/virtual-network/virtual-networks-nsg) v dokumentaci k Azure.

1. Sdělte zprostředkovateli hostitele R, který certifikát SSL načíst: Pokud instalujete certifikát na intranetový server, je pravděpodobné, že plně kvalifikovaný název domény serveru je stejný jako jeho název NETBIOS. V tomto případě není nic, co je třeba udělat, protože se jedná o výchozí certifikát, který je načten.

    Pokud však instalujete certifikát na internetový server (například virtuální počítač Azure), použijte plně kvalifikovaný název domény (FQDN) serveru, protože plně kvalifikovaný název internetového serveru není nikdy stejný jako jeho název NETBIOS.

    Chcete-li použít hlavní název souboru Souborů, přejděte na místo, kde je nainstalována služba R Services (*%PROGRAM FILES%\R Vzdálená služba pro visual studio\1.0)* otevřete soubor *Microsoft.R.Host.Broker.Config.json* v textovém editoru a nahraďte jeho obsah následujícím: přiřaďte cn k libovolnému fqdn serveru, například `foo.westus.cloudapp.azure.com`:

    ```json
    {
      "server.urls": "https://0.0.0.0:5444",
      "security": {
        "X509CertificateName": "CN=your-server-fully-qualified-domain-name"
      }
    }
    ```

    Uložte soubor a restartujte počítač, chcete-li použít změny.

## <a name="troubleshooting"></a>Řešení potíží

**Dotaz: Počítač serveru R neodpovídá, co mám dělat?**

Zkuste příkazový příkaz ping na `ping remote-machine-name`vzdálený počítač z příkazového řádku: . Pokud se příkaz ping nezdaří, zkontrolujte, zda je počítač spuštěn.

**Dotaz: Interaktivní okno R říká, že vzdálený počítač je zapnutý, ale proč není služba spuštěna?**

Existují tři možné důvody:

- [Rozhraní .NET Framework 4.6.1](https://www.microsoft.com/download/details.aspx?id=49981) nebo vyšší není v počítači nainstalováno.
- Brána `Microsoft.R.Host.Broker` firewall `Microsoft.R.Host` pro příchozí i odchozí připojení na portu 5444 a nejsou povolena pro ně.
- Nebyl nainstalován certifikát `CN=<remote-machine-name>` SSL.

Restartujte počítač po provedení některé z výše uvedených změn. Potom se `RHostBrokerService` ujistěte, že a `RUserProfileService` jsou spuštěny prostřednictvím Správce úloh (karta služby) nebo *services.msc*.

**Otázka: Proč interaktivní okno R říká "401 Přístup odepřen" při připojování k serveru R?**

Existují dva možné důvody:

- Je vysoce pravděpodobné, `NETWORK SERVICE` že účet nemá přístup k soukromému klíči certifikátu SSL. Postupujte podle předchozích `NETWORK SERVICE` pokynů a udělte přístup k soukromému klíči.
- Ujistěte `seclogon` se, že služba je spuštěna. Pomocí *souboru services.msc* nakonfigurujte `seclogon` automatické spuštění.

**Otázka: Proč interaktivní okno R říká "404 nebyl nalezen" při připojování k serveru R?**

Tato chyba je pravděpodobně z důvodu chybějící visual c++ redistribuovatelné knihovny. Zkontrolujte interaktivní okno R a zjistěte, zda se nezobrazuje zpráva týkající se chybějící knihovny (DLL). Pak zkontrolujte, zda je nainstalován vS 2015 redistributable a že máte nainstalovánr také.

**Otázka: Nemám přístup k internetu/prostředku z interaktivního okna R, co mám dělat?**

Ujistěte se, `Microsoft.R.Host.Broker` že `Microsoft.R.Host` brána firewall pravidla pro a povolit odchozí přístup na portu 5444. Po použití změn restartujte počítač.

**Otázka: Zkoušel jsem všechna tato řešení, a to ještě nefunguje. A teď co?**

Vyhledejte soubory protokolu v *c:\Windows\ServiceProfiles\NetworkService\AppData\Local\Temp*. Tato složka obsahuje samostatné soubory protokolu pro každou instanci služby R Broker Service, která byla spuštěna. Při každém restartování služby je vytvořen nový soubor protokolu. V nejnovějším souboru protokolu naleznete informace o tom, co se může pokazit.
