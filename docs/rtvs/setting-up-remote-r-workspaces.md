---
title: Vzdálené pracovní prostory pro R
description: Jak nastavit vzdálené pracovní prostory R a připojit se k ní ze sady Visual Studio.
ms.date: 12/04/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 686f98aaaade035f1632139d255ccff8b37eddf3
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850055"
---
# <a name="set-up-remote-workspaces"></a>Nastavení vzdálených pracovních prostorů

Tento článek vysvětluje, jak nakonfigurovat vzdálený server s protokolem SSL a příslušnou službou jazyka R. To umožňuje Nástroje R pro Visual Studio (RTVS) připojení ke vzdálenému pracovnímu prostoru na tomto serveru.

## <a name="remote-computer-requirements"></a>Požadavky na vzdálený počítač

- Windows 10, Windows Server 2016 nebo Windows Server 2012 R2. RTVS také vyžaduje
- [.NET Framework 4.6.1](https://www.microsoft.com/download/details.aspx?id=49981) nebo vyšší

## <a name="install-an-ssl-certificate"></a>Instalace certifikátu SSL

RTVS vyžaduje, aby veškerá komunikace se vzdáleným serverem následovala přes protokol HTTP, která vyžaduje certifikát SSL na serveru. Můžete použít buď certifikát podepsaný důvěryhodnou certifikační autoritou (doporučeno), nebo certifikát podepsaný svým držitelem. (Certifikát podepsaný svým držitelem způsobí, že RTVS při připojení vydá upozornění.) V takovém případě ho budete muset nainstalovat do počítače a povolíte přístup k jeho privátnímu klíči.

### <a name="obtain-a-trusted-certificate"></a>Získání důvěryhodného certifikátu

Důvěryhodný certifikát vystavuje certifikační autorita (viz téma [certifikační autorita na Wikipedii](https://en.wikipedia.org/wiki/Certificate_authority) pro pozadí). Podobně jako získání identifikační karty pro státní správu a vydávání důvěryhodného certifikátu je potřeba mít víc procesu a možné poplatky, ale ověří pravost žádosti a žadatele.

Klíčovým polem, které se musí nacházet v certifikátu, je plně kvalifikovaný název domény počítače s R serverem. Certifikační autorita vyžaduje ověření, že máte oprávnění k vytvoření nového serveru pro doménu, do které server patří.

Další informace najdete v tématu [Certifikáty veřejných klíčů](https://en.wikipedia.org/wiki/Public_key_certificate) v Wikipedii.

## <a name="install-an-ssl-certificate-on-windows"></a>Instalace certifikátu SSL ve Windows

Certifikát SSL musí být nainstalován ručně v systému Windows. Pomocí následujících pokynů nainstalujte certifikát SSL.

### <a name="obtain-a-self-signed-certificate-windows"></a>Získání certifikátu podepsaného svým držitelem (Windows)

Pokud máte důvěryhodný certifikát, přeskočte tuto část. V porovnání s certifikátem důvěryhodné autority je certifikát podepsaný svým držitelem, jako by se vytvořila identifikační karta pro sebe. Tento proces je samozřejmě mnohem jednodušší než při práci s důvěryhodnou autoritou, ale také nemá silné ověřování, což znamená, že útočník může nahradit svůj vlastní certifikát pro nepodepsaný certifikát a zachytit veškerý provoz mezi klientem a WebServer. *Certifikát podepsaný svým držitelem by proto měl být používán pouze pro testovací scénáře, v důvěryhodné síti a nikdy v produkčním prostředí.*

Z tohoto důvodu RTVS při připojování k serveru s certifikátem podepsaným svým držitelem vždycky vystaví následující upozornění:

![Dialogové okno upozornění certifikátu podepsaného svým držitelem](media/workspaces-remote-self-signed-certificate-warning.png)

Vydání certifikátu podepsaného svým držitelem:

1. Přihlaste se k počítači R serveru pomocí účtu správce.
1. Otevřete nový příkazový řádek PowerShellu pro správce a vydejte následující příkaz a nahraďte `"remote-machine-name"` plně kvalifikovaným názvem domény vašeho počítačového serveru.

    ```ps
    New-SelfSignedCertificate -CertStoreLocation Cert:\LocalMachine\My -DnsName "remote-machine-name"
    ```

1. Pokud jste prostředí PowerShell nikdy nespouštěli v počítači se systémem R Server, spusťte následující příkaz, který umožní spustit příkazy explicitně:

    ```ps
    Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
    ```

Základní informace najdete v tématu [certifikáty podepsané svým držitelem](https://en.wikipedia.org/wiki/Self-signed_certificate) v Wikipedii.

### <a name="install-the-certificate"></a>Nainstalujte certifikát.

Chcete-li nainstalovat certifikát na vzdáleném počítači, spusťte *Certlm. msc* (Správce certifikátů) z příkazového řádku. Klikněte pravým tlačítkem na **osobní** složku a vyberte příkaz **všechny úkoly** > **importovat** :

![Import certifikátu – příkaz](media/workspaces-remote-certificate-import.png)

### <a name="grant-permissions-to-read-the-ssl-certificates-private-key"></a>Udělení oprávnění ke čtení privátního klíče certifikátu SSL

Po importu certifikátu udělte účtu `NETWORK SERVICE` oprávnění ke čtení privátního klíče, jak je popsáno v následujících pokynech. `NETWORK_SERVICE` je účet, který slouží ke spuštění zprostředkovatele služby R Services, což je služba, která ukončuje příchozí připojení SSL k počítači serveru.

1. Spusťte *Certlm. msc* (Správce certifikátů) z příkazového řádku správce.
1. Rozbalte položku **osobní** > **certifikáty**, klikněte pravým tlačítkem na svůj certifikát a vyberte **všechny úlohy** > **spravovat soukromé klíče**.
1. Klikněte pravým tlačítkem na certifikát a vyberte příkaz **spravovat soukromé klíče** v části **všechny úlohy**.
1. V dialogovém okně, které se zobrazí, vyberte **Přidat** a zadejte `NETWORK SERVICE` jako název účtu:

    ![Dialogové okno Správa privátních klíčů, přidání NETWORK_SERVICE](media/workspaces-remote-manage-private-key-dialog.png)

1. Dvojitým kliknutím na **OK** zavřete dialogová okna a potvrďte provedené změny.

## <a name="install-an-ssl-certificate-on-ubuntu"></a>Instalace certifikátu SSL v Ubuntu

Balíček `rtvs-daemon` nainstaluje ve výchozím nastavení certifikát podepsaný svým držitelem, který bude součástí instalace.

### <a name="obtain-a-self-signed-certificate-ubuntu"></a>Získání certifikátu podepsaného svým držitelem (Ubuntu)

Výhody a rizika použití certifikátu podepsaného svým držitelem najdete v popisu systému Windows. Balíček `rtvs-daemon` generuje a nakonfiguruje certifikát podepsaný svým držitelem během instalace. Tento postup bude nutné provést pouze v případě, že chcete nahradit automaticky generovaný certifikát podepsaný svým držitelem.

Postup při vydání certifikátu podepsaného svým držitelem:

1. SSH nebo Přihlaste se k počítači se systémem Linux.
2. Nainstalovat balíček `ssl-cert`:

    ```sh
    sudo apt-get install ssl-cert
    ```

3. Spuštěním `make-ssl-cert` vygenerujte výchozí certifikát SSL podepsaný svým držitelem:

    ```sh
    sudo make-ssl-cert generate-default-snakeoil --force-overwrite
    ```

4. Převeďte vygenerované klíče a soubory PEM na PFX. Vygenerovaný soubor PFX by měl být v domovské složce:

    ```sh
    openssl pkcs12 -export -out ~/ssl-cert-snakeoil.pfx -inkey /etc/ssl/private/ssl-cert-snakeoil.key -in /etc/ssl/certs/ssl-cert-snakeoil.pem -password pass:SnakeOil
    ```

### <a name="configure-rtvs-daemon"></a>Konfigurace démona RTVS

Cesta k souboru certifikátu SSL (cesta k PFX) musí být nastavená v */etc/RTVS/rtvsd.config.JSON*. Aktualizujte `X509CertificateFile` a `X509CertificatePassword` pomocí cesty k souboru a hesla v uvedeném pořadí.

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

Uložte soubor a restartujte démona `sudo systemctl restart rtvsd`.

## <a name="install-r-services-on-windows"></a>Instalace služby R Services ve Windows

Aby bylo možné spustit kód R, musí mít vzdálený počítač nainstalovanou Interpret R, jak je znázorněno níže:

1. Stáhněte a nainstalujte jednu z následujících možností:

   - [Microsoft R Open](https://mran.microsoft.com/open/)
   - [CRAN R pro Windows](https://cran.r-project.org/bin/windows/base/)

     Oba mají stejné funkce, ale Microsoft R Open přináší výhody z dalších hardwarových akcelerovaných lineárních algebraický knihoven, které jsou v [knihovně Intel Math kernel](https://software.intel.com/intel-mkl).

2. Po zobrazení výzvy spusťte [instalační program služby R](https://github.com/Microsoft/RTVS/blob/master/doc/rtvsd/rtvs-remote-downloads.md) a restartujte ho. Instalační program provede následující akce:

    - Vytvořte složku v *%ProgramFiles%\r Tools for Visual Studio\1.0\\* a zkopírujte všechny požadované binární soubory.
    - Nainstalovat `RHostBrokerService` a `RUserProfileService` a nakonfigurovat tak, aby se spouštěla automaticky.
    - Nakonfigurujte službu `seclogon` tak, aby se spouštěla automaticky.
    - Přidejte *Microsoft. r. Host. exe* a *Microsoft. r. Host. Broker. exe* na příchozí pravidla brány firewall na výchozí port 5444.

Služba R Services se spustí automaticky při restartování počítače:

- **Služba Zprostředkovatel hostitele R** zpracovává veškerý přenos HTTPS mezi Visual Studio a proces, ve kterém se v počítači spouští kód R.
- **Služba profilu uživatele R** je privilegovaná součást, která zpracovává vytváření profilů uživatelů Windows. Služba se volá, když se nový uživatel poprvé přihlásí k počítači s R serverem.

Tyto služby můžete zobrazit v konzole pro správu služeb (*compmgmt. msc*).

## <a name="install-r-services-on-linux"></a>Instalace služby R Services na Linux

Aby bylo možné spustit kód R, musí mít vzdálený počítač nainstalovanou Interpret R, jak je znázorněno níže:

1. Stáhněte a nainstalujte jednu z následujících možností:

   - [Microsoft R Open](https://mran.microsoft.com/open/)
   - [CRAN R pro Windows](https://cran.r-project.org/bin/linux/ubuntu/)

     Oba mají stejné funkce, ale Microsoft R Open přináší výhody z dalších hardwarových akcelerovaných lineárních algebraický knihoven, které jsou v [knihovně Intel Math kernel](https://software.intel.com/intel-mkl).

2. Postupujte podle pokynů ve [službě Vzdálená služba R pro Linux](setting-up-remote-r-service-on-linux.md), která se vztahuje na fyzické počítače Ubuntu, virtuální počítače Azure Ubuntu, podsystém Windows pro Linux (WSL) a kontejnery Docker, včetně těch, které běží v úložišti kontejnerů Azure.

## <a name="configure-r-services"></a>Konfigurace služeb R

Se službami R běžícími na vzdáleném počítači budete taky muset vytvořit uživatelské účty, nastavit pravidla brány firewall, nakonfigurovat síť Azure a nakonfigurovat certifikát SSL.

1. Uživatelské účty: vytvořte účty pro každého uživatele, který přistupuje ke vzdálenému počítači. Můžete vytvořit standardní (bez privilegované) místní uživatelské účty nebo můžete připojit počítač R serveru k doméně a přidat příslušné skupiny zabezpečení do skupiny zabezpečení `Users`.

1. Pravidla brány firewall: ve výchozím nastavení `R Host Broker` naslouchá na portu TCP 5444. Proto zajistěte, aby u příchozího i odchozího provozu byla povolená pravidla brány firewall systému Windows (pro instalaci balíčků a podobných scénářů je potřeba odchozí).  Instalační program služby R nastaví tato pravidla automaticky pro vestavěnou bránu Windows Firewall. Pokud však používáte bránu firewall jiného výrobce, otevřete ručně port 5444 pro `R Host Broker`.

1. Konfigurace Azure: Pokud je váš vzdálený počítač v Azure virtuálním počítačem, otevřete port 5444 pro příchozí provoz v rámci sítí Azure, což je nezávisle na bráně Windows Firewall. Podrobnosti najdete v tématu [filtrování síťového provozu pomocí skupiny zabezpečení sítě](/azure/virtual-network/virtual-networks-nsg) v dokumentaci k Azure.

1. Řekněte zprostředkovateli hostitele R, který certifikát SSL má načíst: Pokud instalujete certifikát na intranetový server, je možné, že plně kvalifikovaný název domény vašeho serveru je stejný jako název NETBIOS. V takovém případě nemusíte nic dělat, protože se jedná o výchozí načtený certifikát.

    Pokud však certifikát instalujete na server s přístupem k Internetu (například virtuální počítač Azure), použijte plně kvalifikovaný název domény (FQDN) serveru, protože plně kvalifikovaný název domény internetového serveru není nikdy stejný jako název NETBIOS.

    Chcete-li použít plně kvalifikovaný název domény, přejděte na místo, kde je nainstalováno služby R ( *% Program Files%\r Remote Service for Visual Studio\1.0* ve výchozím nastavení), otevřete soubor *Microsoft. R. Host. Broker. config. JSON* v textovém editoru a nahraďte jeho obsah následujícím kódem, který přiřadíte k libovolnému názvu domény vašeho serveru, například `foo.westus.cloudapp.azure.com`:

    ```json
    {
      "server.urls": "https://0.0.0.0:5444",
      "security": {
        "X509CertificateName": "CN=your-server-fully-qualified-domain-name"
      }
    }
    ```

    Uložte soubor a restartujte počítač, aby se změny projevily.

## <a name="troubleshooting"></a>Odstraňování problémů

**Otázka. počítač s R serverem nereaguje, co mám dělat?**

Zkuste na vzdáleném počítači pomocí příkazu příkazového řádku: `ping remote-machine-name`. Pokud se příkaz if nezdařil, ujistěte se, že počítač běží.

**Dotaz. interaktivní okno R znamená, že je vzdálený počítač zapnutý, ale proč služba není spuštěná?**

Existují tři možné důvody:

- V počítači není nainstalována [.NET Framework 4.6.1](https://www.microsoft.com/download/details.aspx?id=49981) nebo vyšší.
- Pravidla brány firewall pro `Microsoft.R.Host.Broker` a `Microsoft.R.Host` nejsou povolena pro příchozí i odchozí připojení na portu 5444.
- Certifikát SSL s `CN=<remote-machine-name>` nebyl nainstalován.

Po provedení některé z výše uvedených změn restartujte počítač. Pak se ujistěte, že `RHostBrokerService` a `RUserProfileService` běží buď pomocí Správce úloh (karta služby) nebo *Services. msc*.

**Otázka: Proč interaktivní okno R říká "401 Přístup odepřen" při připojování k serveru R?**

Existují dva možné důvody:

- Je velmi pravděpodobnější, že účet `NETWORK SERVICE` nemá přístup k privátnímu klíči certifikátu SSL. Postupujte podle předchozích pokynů a udělte `NETWORK SERVICE` přístup k privátnímu klíči.
- Ujistěte se, že je služba `seclogon` spuštěná. Pomocí *služby Services. msc* nakonfigurujte `seclogon`, aby se spouštěla automaticky.

**Dotaz: Proč interaktivní okno R říká "404 Nenalezeno" při připojování k serveru R?**

Tato chyba je pravděpodobně způsobena chybějícími C++ knihovnami Visual Redistributable Library. Zkontrolujte interaktivní okno R a podívejte se, jestli existuje zpráva týkající se chybějící knihovny (DLL). Potom zkontrolujte, zda je nainstalovaná verze VS 2015 Redistributable a zda máte nainstalované i R.

**Otázka: nemůžu získat přístup k Internetu/prostředku z interaktivního okna R, co mám dělat?**

Ujistěte se, že pravidla brány firewall pro `Microsoft.R.Host.Broker` a `Microsoft.R.Host` povolují odchozí přístup na portu 5444. Po použití změn restartujte počítač.

**Q. Zkoušel jsem všechna tato řešení a stále nefunguje. Co teď?**

Prohlédněte si soubory protokolu v *C:\Windows\ServiceProfiles\NetworkService\AppData\Local\Temp*. Tato složka obsahuje samostatné soubory protokolu pro každou instanci služby zprostředkovatele R, která byla spuštěna. Při každém restartování služby se vytvoří nový soubor protokolu. V nejnovějším souboru protokolu si projděte informace o tom, co se může stát chybou.
