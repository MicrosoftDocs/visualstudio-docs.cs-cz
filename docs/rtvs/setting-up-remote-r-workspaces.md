---
title: Vzdálené pracovní prostory pro R
description: Jak nastavit vzdálené pracovní prostory R a k němu připojit ze sady Visual Studio.
ms.date: 12/04/2017
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: 207e4c2d6e7db9dd40288306b3a87086c4568f76
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49827711"
---
# <a name="set-up-remote-workspaces"></a>Nastavení vzdálených pracovních prostorů

Tento článek vysvětluje postup konfigurace serveru pro vzdálený protokolem SSL a příslušnou službu R. To umožňuje nástroji R pro Visual Studio (RTVS) pro připojení k vzdálené pracovní prostor na tomto serveru.

## <a name="remote-computer-requirements"></a>Požadavky na vzdáleném počítači

- Windows 10, Windows Server 2016 nebo Windows Server 2012 R2. Také vyžaduje RTVS
- [Rozhraní .NET framework 4.6.1](https://www.microsoft.com/download/details.aspx?id=49981) nebo vyšší

## <a name="install-an-ssl-certificate"></a>Nainstalovat certifikát SSL

RTVS vyžaduje, aby se stane veškerá komunikace se vzdáleným serverem přes protokol HTTP, která vyžaduje certifikát SSL na serveru. Můžete použít buď certifikát podepsaný důvěryhodnou certifikační autoritou (doporučeno), nebo certifikát podepsaný svým držitelem. (RTVS certifikát podepsaný svým držitelem způsobí upozornění na problém při připojení.) S jedním z nich pak musíte nainstalovat na počítač a povolit přístup k jeho privátní klíč.

### <a name="obtain-a-trusted-certificate"></a>Získání důvěryhodného certifikátu

Důvěryhodný certifikát je vydaný certifikační autoritou (viz [certifikační autority v encyklopedii Wikipedia](https://en.wikipedia.org/wiki/Certificate_authority) pozadí). Podobně jako získávání government identifikační karty, důvěryhodný certifikát zahrnuje další proces a je to možné poplatky, ale ověří pravosti požadavku a žadatel.

Pole s klíčem, který má být v certifikátu je plně kvalifikovaný název domény počítače R serveru. Certifikační autorita vyžaduje ověření, že máte oprávnění k vytvoření nového serveru pro doménu, ke které server patří.

Další informace najdete v části [certifikáty s veřejným klíčem](https://en.wikipedia.org/wiki/Public_key_certificate) v encyklopedii Wikipedia.

## <a name="install-an-ssl-certificate-on-windows"></a>Nainstalujte certifikát SSL na Windows

Certifikát SSL musí být nainstalován ručně na Windows. Postupujte podle níže uvedených pokynů k instalaci certifikátu SSL.

### <a name="obtain-a-self-signed-certificate-windows"></a>Získat certifikát podepsaný svým držitelem (Windows)

Tuto část přeskočte, pokud máte důvěryhodný certifikát. Ve srovnání s certifikát od důvěryhodné autority, jako je vytváření identifikační karty sami se certifikát podepsaný svým držitelem. Tento proces je samozřejmě mnohem jednodušší než práce s důvěryhodnou autoritou, ale také nemá silné ověřování, což znamená, že útočník může nahradit vlastní certifikát bez znaménka a zachytit veškerý síťový provoz mezi klientem a Server. Proto *certifikát podepsaný svým držitelem by měla sloužit pouze k testování scénářů v důvěryhodné síti a nikdy v produkčním prostředí.*

Z tohoto důvodu RTVS vždy vydává toto upozornění při připojování k serveru pomocí certifikátu podepsaného svým držitelem:

![Dialogové okno upozornění certifikátu podepsaného svým držitelem](media/workspaces-remote-self-signed-certificate-warning.png)

Vydat certifikát podepsaný svým držitelem:

1. Přihlaste se k počítači R serveru pomocí účtu správce.
1. Otevřete nový příkazový řádek Powershellu správce a vydejte následující příkaz a nahraďte `"remote-machine-name"` s plně kvalifikovaný název domény počítače serveru.

    ```ps
    New-SelfSignedCertificate -CertStoreLocation Cert:\LocalMachine\My -DnsName "remote-machine-name"
    ```

1. Pokud jste provedli nikdy PowerShell před v R serveru, spusťte následující příkaz pro spuštění příkazů explicitně povolit:

    ```ps
    Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
    ```

Na pozadí, naleznete v tématu [certifikáty podepsané svým držitelem](https://en.wikipedia.org/wiki/Self-signed_certificate) v encyklopedii Wikipedia.

### <a name="install-the-certificate"></a>Instalace certifikátu

Pokud chcete nainstalovat certifikát na vzdáleném počítači, spusťte *certlm.msc* (Správce certifikátů) z příkazového řádku. Klikněte pravým tlačítkem na **osobní** a pak zvolte položku **všechny úkoly** > **Import** příkaz:

![Příkaz pro import certifikátů](media/workspaces-remote-certificate-import.png)

### <a name="grant-permissions-to-read-the-ssl-certificates-private-key"></a>Udělit oprávnění ke čtení privátní klíč certifikátu SSL

Jakmile je certifikát importován, udělte `NETWORK SERVICE` účet oprávnění ke čtení privátní klíč, jak je popsáno v následujících pokynech. `NETWORK_SERVICE` účet pro provedení zprostředkovatele služby R, což je služba, která ukončuje příchozí připojení SSL k serveru.

1. Spustit *certlm.msc* (Správce certifikátů) z příkazového řádku správce.
1. Rozbalte **osobní** > **certifikáty**, klikněte pravým tlačítkem na certifikát a vyberte **všechny úkoly** > **spravovat privátní Klíče**.
1. Klikněte pravým tlačítkem na certifikát a vyberte **spravovat soukromé klíče** příkaz **všechny úkoly**.
1. V zobrazeném dialogu vyberte **přidat** a zadejte `NETWORK SERVICE` jako název účtu:

    ![Spravovat soukromé klíče dialogovém okně Přidání služba NETWORK_SERVICE](media/workspaces-remote-manage-private-key-dialog.png)

1. Vyberte **OK** dvakrát na Zavřít dialogová okna a potvrzení provedených změn.

## <a name="install-an-ssl-certificate-on-ubuntu"></a>Nainstalovat certifikát SSL na Ubuntu

`rtvs-daemon` Balíček nainstaluje certifikát podepsaný svým držitelem ve výchozím nastavení jako součást instalace.

### <a name="obtain-a-self-signed-certificate-ubuntu"></a>Získat certifikát podepsaný svým držitelem (Ubuntu)

Výhody a rizika při použití certifikátu podepsaného svým držitelem najdete v popisu Windows. `rtvs-daemon` Balíček vygeneruje a konfiguruje během instalace certifikátu podepsaného svým držitelem. Je potřeba provést jenom v případě, že chcete nahradit automaticky generované certifikát podepsaný svým držitelem.

Chcete-li vydat certifikát podepsaný svým držitelem:

1. Přihlaste se k počítači Linux nebo SSH.
2. Nainstalujte `ssl-cert` balíčku:
    ```sh
    sudo apt-get install ssl-cert
    ```
3. Spustit `make-ssl-cert` k vygenerování certifikátu SSL podepsaného držitelem výchozí:
    ```sh
    sudo make-ssl-cert generate-default-snakeoil --force-overwrite
    ```
4. Převeďte do formátu PFX vygenerovaný klíč a soubory PEM. Vygenerovaný soubor PFX by měla být v domovské složky:
    ```sh
    openssl pkcs12 -export -out ~/ssl-cert-snakeoil.pfx -inkey /etc/ssl/private/ssl-cert-snakeoil.key -in /etc/ssl/certs/ssl-cert-snakeoil.pem -password pass:SnakeOil
    ```

### <a name="configure-rtvs-daemon"></a>Konfigurace démona RTVS

Cesta k souboru certifikátu protokolu SSL (cesta k PFX) musí být nastavena v */etc/rtvs/rtvsd.config.json*. Aktualizace `X509CertificateFile` a `X509CertificatePassword` pomocí hesla a cesta k souboru v uvedeném pořadí.

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

Uložte soubor a potom démon, restartujte `sudo systemctl restart rtvsd`.

## <a name="install-r-services-on-windows"></a>Instalace služby R na Windows

Ke spuštění kódu jazyka R, musí mít vzdálený počítač interpret R nainstalovat následujícím způsobem:

1. Stáhnout a nainstalovat některou z následujících akcí:

   - [Microsoft R Open](https://mran.microsoft.com/open/)
   - [R server CRAN pro Windows](https://cran.r-project.org/bin/windows/base/)

     Obě mají stejné funkce, ale Microsoft R Open výhody další hardware accelerated lineární algebraický knihovny laskavým [Intel Math jádra Library](https://software.intel.com/intel-mkl).

2. Spustit [instalační program služby R](https://aka.ms/rtvs-services) a pak po zobrazení výzvy. Instalační program provede následující akce:

    - Vytvořte složku v *%PROGRAMFILES%\R Tools for Visual Studio\1.0\\*  a zkopírujte všechny požadované binární soubory.
    - Nainstalujte `RHostBrokerService` a `RUserProfileService` a nakonfigurovat tak, aby se spouštěla automaticky.
    - Konfigurace `seclogon` automatického spouštění služby.
    - Přidat *Microsoft.R.Host.exe* a *Microsoft.R.Host.Broker.exe* do brány firewall pravidla pro příchozí provoz na výchozím portu 5444.

Služby R se automaticky spustit, když se počítač se restartuje:

- **Služba Service Broker hostitele R** zpracovává veškerý provoz protokolu HTTPS mezi Visual Studio a procesu, kde běží kód R na počítači.
- **Služba profilu uživatele R** je privilegovaných komponenta, která zpracovává vytvořit profil uživatele Windows. Služba se volá, když se nový uživatel poprvé přihlásí k počítači R serveru.

Zobrazí se tyto služby v konzole pro správu služeb (*compmgmt.msc*).

## <a name="install-r-services-on-linux"></a>Instalace R Services v Linuxu

Ke spuštění kódu jazyka R, musí mít vzdálený počítač interpret R nainstalovat následujícím způsobem:

1. Stáhnout a nainstalovat některou z následujících akcí:

   - [Microsoft R Open](https://mran.microsoft.com/open/)
   - [R server CRAN pro Windows](https://cran.r-project.org/bin/linux/ubuntu/)

     Obě mají stejné funkce, ale Microsoft R Open výhody další hardware accelerated lineární algebraický knihovny laskavým [Intel Math jádra Library](https://software.intel.com/intel-mkl).

2. Postupujte podle pokynů [Vzdálená služba R pro Linux](setting-up-remote-r-service-on-linux.md), která zahrnuje fyzických počítačů se systémem Ubuntu, virtuální počítače Azure s Ubuntu, subsystém Windows pro Linux (WSL) a kontejnery Dockeru, včetně těch, které běží na kontejner úložiště Azure.

## <a name="configure-r-services"></a>Konfigurace služby R

S R services na vzdáleném počítači spuštěny budete také potřebovat postup vytváření uživatelských účtů, nastavovat pravidla brány firewall, konfigurace sítě Azure a konfigurace certifikátu SSL.

1. Uživatelských účtů: vytvoření účtů pro každý uživatel, který používá vzdálený počítač. Můžete vytvořit buď standardní (Neprivilegovaný) místní uživatelské účty, nebo můžete připojit do domény počítače serveru R a přidat do příslušných skupin zabezpečení k `Users` skupiny zabezpečení.

1. Pravidla brány firewall: ve výchozím nastavení, `R Host Broker` naslouchá na portu TCP 5444. Proto se ujistěte, že jsou povolené pro příchozí a odchozí provoz pravidla brány firewall na Windows (odchozí je vyžadována pro instalaci balíčků a podobné scénáře).  Instalační program služby R Nastaví tato pravidla pro integrované brány Windows firewall automaticky. Pokud používáte bránu firewall jiného dodavatele, ale otevřít port 5444 pro `R Host Broker` ručně.

1. Konfigurace Azure: Pokud váš vzdálený počítač je virtuální počítač v Azure, otevřete port 5444 pro příchozí provoz v rámci sítě Azure jako, který je nezávislý brány Windows Firewall. Podrobnosti najdete v tématu [filtrování provozu sítě s použitím skupin zabezpečení sítě](https://docs.microsoft.com/azure/virtual-network/virtual-networks-nsg) v dokumentaci k Azure.

1. Zjistit R Host Broker, který certifikát SSL pro načtení: Pokud instalujete certifikát na intranetový server, je pravděpodobné, že plně kvalifikovaný název domény serveru je stejný jako název rozhraní NETBIOS. V takovém případě nic, je třeba provést, protože to je výchozí certifikát, který je načten.

    Ale pokud k instalaci certifikátu na serveru přístupem k Internetu (třeba virtuální počítač Azure), použijte plně kvalifikovaný název domény (FQDN) serveru, protože plně kvalifikovaný název domény serveru přístupem k Internetu je vždy stejný jako název rozhraní NETBIOS.

    Používá název FQDN, přejděte k instalaci služby R (*% PROGRAM FILES%\R vzdálené služby k Visual Studio\1.0* ve výchozím nastavení), otevřete *Microsoft.R.Host.Broker.Config.json* souboru v textovém editoru a jeho obsah nahraďte následujícím, přiřazení CN na cokoli, co váš server je plně kvalifikovaný název domény, například `foo.westus.cloudapp.azure.com`:

    ```json
    {
      "server.urls": "https://0.0.0.0:5444",
      "security": {
        "X509CertificateName": "CN=your-server-fully-qualified-domain-name"
      }
    }
    ```

    Uložte soubor a restartovat počítač změny projeví.

## <a name="troubleshooting"></a>Poradce při potížích

**Q. Počítač, R server neodpovídá, co mám dělat?**

Zkuste příkaz ping vzdáleném počítači z příkazového řádku: `ping remote-machine-name`. Pokud se příkaz ping nezdaří, zkontrolujte, zda že je spuštěna.

**Q. Interaktivní okno R uvádí, že je vzdálený počítač zapnutý, ale není proč služba spuštěna?**

Existují tři možné důvody:

- [Rozhraní .NET framework 4.6.1](https://www.microsoft.com/download/details.aspx?id=49981) nebo vyšší není nainstalován v počítači.
- Pravidla firewallu pro `Microsoft.R.Host.Broker` a `Microsoft.R.Host` pro příchozí a odchozí připojení na portu 5444 nejsou povolené.
- Certifikát SSL s `CN=<remote-machine-name>` nebyl nainstalován.

Restartujte počítač po změnách výše. Ujistěte se, že `RHostBrokerService` a `RUserProfileService` běží prostřednictvím buď Správce úloh (karta služby) nebo *services.msc*.

**Q. Proč interaktivní okno R Checks "401 Přístup byl odepřen" při připojování k serveru R?**

Existují dva možné důvody:

- Je vysoce pravděpodobné, `NETWORK SERVICE` účet nemá přístup k privátnímu klíči certifikátu protokolu SSL. Postupujte podle pokynů starší udělit `NETWORK SERVICE` přístup k privátnímu klíči.
- Ujistěte se, že `seclogon` se službou. Použití *services.msc* konfigurace `seclogon` na automatické spouštění.

**Q. Proč interaktivní okno R Checks "404 Nenalezeno" při připojování k serveru R?**

Tato chyba je pravděpodobně z důvodu chybějící knihovny Visual C++ redistributable. Zkontrolujte interaktivním okně jazyka r. Pokud je zpráva týkající se chybějící knihovny (DLL). Zkontrolujte, že VS 2015 redistributable je nainstalovaný a zda máte jazyk R nainstalovaný také.

**Q. Nemám přístup ke internet nebo prostředek v interaktivním okně R, co mám dělat?**

Ujistěte se, že pravidla brány firewall pro `Microsoft.R.Host.Broker` a `Microsoft.R.Host` povolí odchozí přístup na port 5444. Restartujte počítač po aplikování změn.

**Q. Jste se pokusili tato řešení a ani to nepomůže. A co teď?**

Podívejte se v souborech protokolu v *C:\Windows\ServiceProfiles\NetworkService\AppData\Local\Temp*. Tato složka obsahuje samostatný soubor protokolu pro každou instanci zprostředkovatele služby R, který byl spuštěn. Nový soubor protokolu se vytvoří při každém restartu služby. Zkontrolujte poslední soubor protokolu pro příčiny o co může být špatně.
