---
ms.openlocfilehash: 69f4f4c2b55670d510652b44a203b9f0eafcc53a
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "68143548"
---

1. Zavřete a znovu otevřete Konzolu pro správu služby IIS a zobrazte aktualizované možnosti konfigurace v ui.

2. Ve službě IIS klepněte pravým tlačítkem myši na **výchozí web**a zvolte **možnost Nasadit** > **konfigurovat publikování na nasazení webu**.

    ![Konfigurace konfigurace nasazení webu](../../deployment/media/tutorial-configure-web-deploy-publishing.png)

3. V dialogovém okně **Konfigurovat publikování na nasazení webu** zkontrolujte nastavení.

4. Klepněte na **položku Nastavení**.

    V panelu **Výsledky** výstup ukazuje, že přístupová práva jsou udělena určenému uživateli a že soubor s příponou *souboru .publishsettings* byl vygenerován v umístění zobrazeném v dialogovém okně.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <publishData>
      <publishProfile
        publishUrl="https://myhostname:8172/msdeploy.axd"
        msdeploySite="Default Web Site"
        destinationAppUrl="http://myhostname:80/"
        mySQLDBConnectionString=""
        SQLServerDBConnectionString=""
        profileName="Default Settings"
        publishMethod="MSDeploy"
        userName="myhostname\myusername" />
    </publishData>
    ```

    V závislosti na konfiguraci systému Windows Server a služby IIS se v souboru XML zobrazují různé hodnoty. Zde je několik podrobností o zobrazených hodnotách:

   * Soubor *msdeploy.axd* odkazovaný `publishUrl` v atributu je dynamicky generovaný soubor obslužné rutiny HTTP pro nasazení webu. (Pro účely `http://myhostname:8172` testování, obecně funguje také.)
   * Port `publishUrl` je nastaven na port 8172, což je výchozí pro nasazení webu.
   * Port `destinationAppUrl` je nastaven na port 80, což je výchozí pro iis.
   * Pokud se nemůžete připojit ke vzdálenému hostiteli v sadě Visual Studio pomocí názvu hostitele (v pozdějších krocích), otestujte adresu IP místo názvu hostitele.

     > [!NOTE]
     > Pokud publikujete do služby IIS spuštěné na virtuálním počítači Azure, musíte otevřít porty Nasazení webu a IIS ve skupině Zabezpečení sítě. Podrobné informace naleznete v [tématu Instalace a spuštění služby IIS](/azure/virtual-machines/windows/quick-create-portal#install-web-server).

5. Zkopírujte tento soubor do počítače, ve kterém používáte visual studio.
