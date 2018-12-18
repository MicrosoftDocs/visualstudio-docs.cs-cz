Nástroj nasazení webu 3.6 pro servery hostující poskytuje další konfiguraci funkce, které umožňují vytváření souboru s nastavením publikování v uživatelském rozhraní.

1. Pokud máte webové nasazení 3.6 už nainstalovaná v systému Windows Server, odinstalujte ji pomocí **ovládací panely** > **programy** > **odinstalační Program**.

2. Dále nainstalujte 3.6 nasadit Web pro hostování servery v systému Windows Server.

    Chcete-li nainstalovat nasazení webu pro hostování servery, použijte [instalačního programu webové platformy (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). (Chcete-li najít odkaz na Web Platform Installer ze služby IIS, vyberte **IIS** v levém podokně Správce serveru. Klikněte pravým tlačítkem na server a vyberte **Správce Internetové informační služby (IIS)**.)

    Instalace webové platformy najdete **nasazení webu pro hostování servery** na kartě aplikace.

3. Pokud jste ještě nenainstalovali **IIS skripty a nástroje správy**, jeho instalaci.

    Přejděte na **vybrat role serveru** > **webového serveru (IIS)** > **nástroje pro správu**a pak vyberte **skriptů pro správu služby IIS Nástroje a** roli, klikněte na tlačítko **Další**a potom nainstalujte roli.

    ![Nainstaluje nástroje a skripty pro správu služby IIS](../../deployment/media/tutorial-iis-management-scripts-and-tools.png)

    Skripty a nástroje, je potřeba povolit generování souboru s nastavením publikování.

4. (Volitelné) Ověřte, že nasazení webu běží správně tak, že otevřete **ovládací panely > systém a zabezpečení > Nástroje pro správu > služby** a ujistěte se, že **webová služba agenta nasazení** běží () název služby se liší ve starších verzích).

    Pokud služba agent není spuštěna, spusťte ji. Pokud není k dispozici na všech, přejděte na **ovládací panely > programy > odinstalovat program**, Najít **Microsoft Web Deploy <version>** . Zvolit **změnu** instalace a ujistěte se, že jste zvolili **se nainstaluje na místní pevný disk** pro součásti nasazení webu. Dokončete instalaci změnit.