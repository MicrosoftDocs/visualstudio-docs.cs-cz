
1. Zavřete a znovu otevřete konzolu pro správu služby IIS na zobrazit aktualizovanou konfiguraci možností v uživatelském rozhraní.

2. Ve službě IIS, klikněte pravým tlačítkem myši **výchozí webový server**, zvolte **nasadit** > **konfigurace nasazení publikování na webu**.

    ![Konfiguraci nasazení webu](../../deployment/media/tutorial-configure-web-deploy-publishing.png)

3. V **konfigurace nasazení publikování na webu** dialogovém okně zkontrolujte nastavení.

4. Klikněte na tlačítko **nastavení**.

    V **výsledky** panelu ukazuje výstup, které přístupová práva jsou udělena pro zadaného uživatele a že soubor s *.publishsettings* přípona souboru byl vytvořen v části znázorněné v dialogovém okně pole.

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

    V závislosti na konfiguraci systému Windows Server a služby IIS najdete v článku různé hodnoty v souboru XML. Tady je několik podrobností o hodnoty, které se zobrazí:

   * *Msdeploy.axd* soubor odkazuje `publishUrl` atribut je dynamicky generovaný soubor obslužné rutiny HTTP pro nasazení webu. (Pro testovací účely `http://myhostname:8172` obecně funguje stejně.)
   * `publishUrl` Je port nastaven na port 8172, což je výchozí nastavení pro nasazení webu.
   * `destinationAppUrl` Je port nastaven na port 80, což je výchozí hodnota pro službu IIS.
   * Pokud se nemůžete připojit ke vzdálenému hostiteli v sadě Visual Studio pomocí názvu hostitele (v následujících krocích), otestujte adresu IP místo názvu hostitele.

     > [!NOTE]
     > Pokud publikujete do IIS a běžící na Virtuálním počítači Azure, je nutné otevřít nasazení webu a portů služby IIS ve skupině zabezpečení sítě. Podrobné informace najdete v tématu [instalace a spuštění služby IIS](/azure/virtual-machines/windows/quick-create-portal#open-port-80-for-web-traffic).

5. Zkopírujte tento soubor do počítače, ve kterém běží sady Visual Studio.
