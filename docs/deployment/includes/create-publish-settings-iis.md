---
ms.openlocfilehash: b8002d9e911c8d8c07a5aaf5286168e49a374a7c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85292123"
---

1. Zavřete a znovu otevřete konzolu pro správu služby IIS, abyste zobrazili aktualizované možnosti konfigurace v uživatelském rozhraní.

2. Ve službě IIS klikněte pravým tlačítkem na **výchozí web**a vyberte **nasadit**  >  **Konfigurovat nasazení webu publikování**.

    ![Konfigurace konfigurace Nasazení webu](../../deployment/media/tutorial-configure-web-deploy-publishing.png)

   Pokud se nabídka **nasadit** nezobrazuje, Projděte si předchozí část a ověřte, jestli je spuštěná nasazení webu.

3. V dialogovém okně **Konfigurace publikování nasazení webu** prověřte nastavení.

4. Klikněte na tlačítko **nastavit**.

    Na panelu **výsledky** zobrazuje výstup oprávnění pro přístup k zadanému uživateli a soubor s příponou *. publishsettings* byl vygenerován v umístění zobrazeném v dialogovém okně.

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

    V závislosti na konfiguraci Windows serveru a IIS se v souboru XML zobrazí různé hodnoty. Tady je několik podrobností o zobrazených hodnotách:

   * Soubor *MSDeploy. axd* , na který se odkazuje v `publishUrl` atributu, je dynamicky generovaný soubor obslužné rutiny HTTP pro nasazení webu. ( `http://myhostname:8172` Obecně funguje i pro účely testování.)
   * `publishUrl`Port je nastaven na port 8172, což je výchozí hodnota pro nasazení webu.
   * `destinationAppUrl`Port je nastaven na port 80, což je výchozí hodnota pro službu IIS.
   * Pokud se nemůžete připojit ke vzdálenému hostiteli v aplikaci Visual Studio pomocí názvu hostitele (v pozdějších krocích), otestujte IP adresu místo názvu hostitele.

     > [!NOTE]
     > Pokud publikujete do služby IIS běžící na virtuálním počítači Azure, musíte otevřít Nasazení webu a porty služby IIS ve skupině zabezpečení sítě. Podrobné informace najdete v tématu [instalace a spuštění služby IIS](/azure/virtual-machines/windows/quick-create-portal#install-web-server).

5. Zkopírujte tento soubor do počítače, na kterém je spuštěná aplikace Visual Studio.
