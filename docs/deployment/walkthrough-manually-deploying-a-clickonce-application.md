---
title: 'Návod: Ruční nasazení aplikace ClickOnce | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Mage.exe, manual ClickOnce deployments
- MageUI.exe, manual ClickOnce deployments
- deploying applications [ClickOnce], manual ClickOnce deployments
- ClickOnce deployment, manually
- ClickOnce deployment, SDK tools
- manual ClickOnce deployments
- manifests [ClickOnce]
ms.assetid: ccee6551-a1b9-4ca2-8845-9c1cf4ac2560
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d02a12c9c412e4dbcc83efc96fd5d8171f0d61b6
ms.sourcegitcommit: 8589d85cc10710ef87e6363a2effa5ee5610d46a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2019
ms.locfileid: "72806813"
---
# <a name="walkthrough-manually-deploy-a-clickonce-application"></a>Návod: Ruční nasazení aplikace ClickOnce
Pokud nemůžete použít Visual Studio k nasazení [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace nebo potřebujete použít pokročilé funkce nasazení, jako je například nasazení důvěryhodné aplikace, měli byste použít nástroj příkazového řádku *Mage. exe* k vytvoření manifestů [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Tento návod popisuje, jak vytvořit nasazení [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pomocí buď verze příkazového řádku (*Mage. exe*) nebo grafické verze (*MageUI. exe*) Manifest Generation and Editing Tool.

## <a name="prerequisites"></a>Požadavky
 Tento návod obsahuje některé předpoklady a možnosti, které je třeba vybrat před sestavením nasazení.

- Nainstalujte *Mage. exe* a *MageUI. exe*.

   *Mage. exe* a *MageUI. exe* jsou součástí [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Musíte mít buď nainstalovanou [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)], nebo verzi [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)], která je součástí sady Visual Studio. Další informace najdete v tématu [Windows SDK](https://www.microsoft.com/download/details.aspx?id=8279) na webu MSDN.

- Poskytněte aplikaci, která se má nasadit.

   Tento návod předpokládá, že máte aplikaci pro Windows, kterou jste připraveni nasadit. Tato aplikace bude označována jako AppToDeploy.

- Určete, jak bude nasazení distribuováno.

   Mezi možnosti distribuce patří: web, sdílení souborů nebo CD. Další informace najdete v tématu [zabezpečení a nasazení ClickOnce](../deployment/clickonce-security-and-deployment.md).

- Určete, zda aplikace vyžaduje zvýšenou úroveň důvěryhodnosti.

   Pokud vaše aplikace vyžaduje úplný vztah důvěryhodnosti – například plný přístup k systému uživatele – můžete použít možnost `-TrustLevel` *Mage. exe* pro nastavení. Pokud chcete pro svou aplikaci definovat vlastní sadu oprávnění, můžete zkopírovat část oprávnění Internet nebo intranet z jiného manifestu, upravit ji tak, aby vyhovovala vašim potřebám, a přidat ji do manifestu aplikace pomocí textového editoru nebo *MageUI. exe*. Další informace najdete v tématu [Přehled nasazení důvěryhodných aplikací](../deployment/trusted-application-deployment-overview.md).

- Získejte certifikát Authenticode.

   Své nasazení byste měli podepsat pomocí certifikátu Authenticode. Testovací certifikát můžete vygenerovat pomocí nástrojů Visual Studio, *MageUI. exe*nebo *Makecert. exe* a *Pvk2Pfx. exe* , nebo můžete získat certifikát od certifikační autority (CA). Pokud se rozhodnete použít nasazení důvěryhodné aplikace, musíte také provést jednorázovou instalaci certifikátu do všech klientských počítačů. Další informace najdete v tématu [Přehled nasazení důvěryhodných aplikací](../deployment/trusted-application-deployment-overview.md).

  > [!NOTE]
  > Nasazení můžete taky podepsat pomocí certifikátu CNG, který můžete získat od certifikační autority.

- Ujistěte se, že aplikace neobsahuje manifest s informacemi o nástroji Řízení uživatelských účtů.

   Musíte určit, jestli vaše aplikace obsahuje manifest s informacemi o nástroji Řízení uživatelských účtů (UAC), jako je `<dependentAssembly>` element. Chcete-li prostudovat manifest aplikace, můžete použít nástroj [Sigcheck](/sysinternals/downloads/sigcheck) Windows Sysinternals.

   Pokud vaše aplikace obsahuje manifest s podrobnostmi o nástroji Řízení uživatelských účtů, je nutné ji znovu sestavit bez informací o nástroji Řízení uživatelských účtů. Pro C# projekt v aplikaci Visual Studio otevřete vlastnosti projektu a vyberte kartu aplikace. V rozevíracím seznamu **manifest** vyberte možnost **vytvořit aplikaci bez manifestu**. Pro projekt Visual Basic v aplikaci Visual Studio otevřete vlastnosti projektu, vyberte kartu aplikace a klikněte na tlačítko **Zobrazit nastavení nástroje řízení uživatelských účtů**. V otevřeném souboru manifestu odeberte všechny prvky v rámci jednoho `<asmv1:assembly>` elementu.

- Určete, jestli aplikace vyžaduje požadavky na klientském počítači.

   aplikace [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazené ze sady Visual Studio můžou zahrnovat zaváděcí nástroj instalace nezbytných součástí (*Setup. exe*) s vaším nasazením. Tento návod vytvoří dva manifesty, které jsou požadovány pro nasazení [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Potřebný zaváděcí nástroj můžete vytvořit pomocí [úlohy GenerateBootstrapper –](../msbuild/generatebootstrapper-task.md).

### <a name="to-deploy-an-application-with-the-mageexe-command-line-tool"></a>Nasazení aplikace pomocí nástroje příkazového řádku Mage. exe

1. Vytvořte adresář, do kterého budete ukládat soubory nasazení [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].

2. V adresáři nasazení, který jste právě vytvořili, vytvořte podadresář verze. Pokud se jedná o první nasazení aplikace, pojmenujte podadresář verze **1.0.0.0**.

   > [!NOTE]
   > Verze vašeho nasazení může být odlišná od verze vaší aplikace.

3. Zkopírujte všechny soubory vaší aplikace do podadresáře Version, včetně spustitelných souborů, sestavení, prostředků a datových souborů. V případě potřeby můžete vytvořit další podadresáře, které obsahují další soubory.

4. Otevřete [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] nebo příkazový řádek sady Visual Studio a přejděte do podadresáře Version (verze).

5. Vytvořte manifest aplikace s voláním *Mage. exe*. Následující příkaz vytvoří manifest aplikace pro kód zkompilovaný ke spuštění na procesorech Intel x86.

   ```cmd
   mage -New Application -Processor x86 -ToFile AppToDeploy.exe.manifest -name "My App" -Version 1.0.0.0 -FromDirectory .
   ```

   > [!NOTE]
   > Nezapomeňte zahrnout tečku (.) po `-FromDirectory` možnosti, která označuje aktuální adresář. Pokud neuvedete tečku, musíte zadat cestu k souborům aplikace.

6. Podepište manifest aplikace pomocí certifikátu Authenticode. Nahraďte *mycert. pfx* cestou k souboru certifikátu. Nahraďte *passwd* heslem k souboru certifikátu.

   ```cmd
   mage -Sign AppToDeploy.exe.manifest -CertFile mycert.pfx -Password passwd
   ```

   Počínaje sadou .NET Framework 4.6.2 SDK, která je distribuována se sadou Visual Studio a pomocí Windows SDK, nástroj *Mage. exe* podepisuje manifesty s CNG a také s certifikáty Authenticode. Používejte stejné parametry příkazového řádku jako u certifikátů Authenticode.

7. Přejděte do kořenové složky adresáře nasazení.

8. Vygenerujte manifest nasazení s voláním *Mage. exe*. Nástroj *Mage. exe* ve výchozím nastavení označí nasazení [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] jako nainstalovanou aplikaci, aby mohla běžet online i offline. Pokud chcete, aby byla aplikace dostupná jenom v případě, že je uživatel online, použijte možnost `-Install` s hodnotou `false`. Použijete-li výchozí nastavení a uživatelé budou instalovat aplikaci z webu nebo sdílené složky, ujistěte se, že hodnota možnosti `-ProviderUrl` odkazuje na umístění manifestu aplikace na webovém serveru nebo sdílené složce.

   ```cmd
   mage -New Deployment -Processor x86 -Install true -Publisher "My Co." -ProviderUrl "\\myServer\myShare\AppToDeploy.application" -AppManifest 1.0.0.0\AppToDeploy.exe.manifest -ToFile AppToDeploy.application
   ```

9. Podepište manifest nasazení pomocí certifikátu Authenticode nebo CNG.

    ```cmd
    mage -Sign AppToDeploy.application -CertFile mycert.pfx -Password passwd
    ```

10. Zkopírujte všechny soubory v adresáři nasazení do cílového umístění nebo na médium nasazení. Může to být složka na webu nebo serveru FTP, sdílená složka nebo jednotka CD-ROM.

11. Poskytněte uživatelům adresu URL, cestu UNC nebo fyzické médium potřebné k instalaci vaší aplikace. Pokud zadáte adresu URL nebo cestu UNC, musíte uživatelům poskytnout úplnou cestu k manifestu nasazení. Pokud je například AppToDeploy nasazena do http://webserver01/ v adresáři AppToDeploy, bude úplná cesta URL http://webserver01/AppToDeploy/AppToDeploy.application.

### <a name="to-deploy-an-application-with-the-mageuiexe-graphical-tool"></a>Nasazení aplikace pomocí grafického nástroje MageUI. exe

1. Vytvořte adresář, do kterého budete ukládat soubory nasazení [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].

2. V adresáři nasazení, který jste právě vytvořili, vytvořte podadresář verze. Pokud se jedná o první nasazení aplikace, pojmenujte podadresář verze **1.0.0.0**.

   > [!NOTE]
   > Verze vašeho nasazení je pravděpodobně odlišná od verze vaší aplikace.

3. Zkopírujte všechny soubory vaší aplikace do podadresáře Version, včetně spustitelných souborů, sestavení, prostředků a datových souborů. V případě potřeby můžete vytvořit další podadresáře, které obsahují další soubory.

4. Spusťte grafický nástroj *MageUI. exe* .

   ```cmd
   MageUI.exe
   ```

5. Vytvořte nový manifest aplikace výběrem položky **soubor**, **Nový**a **manifest aplikace** z nabídky.

6. Na kartě výchozí **název** zadejte název a číslo verze tohoto nasazení. Zadejte také **procesor** , pro který je aplikace sestavená, například x86.

7. Vyberte kartu **soubory** a klikněte na tlačítko se třemi tečkami ( **...** ) vedle textového pole **adresář aplikace** . Zobrazí se dialogové okno **Vyhledat složku** .

8. Vyberte podadresář verze obsahující soubory aplikace a klikněte na tlačítko **OK**.

9. Pokud nasadíte z Internetová informační služba (IIS), zaškrtněte políčko **po naplnění přidat příponu. deploy do libovolného souboru, který** toto pole nemá.

10. Kliknutím na tlačítko **naplnit** přidáte všechny soubory aplikace do seznamu souborů. Pokud vaše aplikace obsahuje více než jeden spustitelný soubor, označte hlavní spustitelný soubor pro toto nasazení jako spouštěcí aplikaci tak, že vyberete **vstupní bod** v rozevíracím seznamu **typ souboru** . (Pokud vaše aplikace obsahuje pouze jeden spustitelný soubor, nástroj *MageUI. exe* ho označí za vás.)

11. Vyberte kartu **požadovaná oprávnění** a vyberte úroveň důvěryhodnosti, kterou budete potřebovat k vyhodnocení vaší aplikace. Výchozí hodnota je **FullTrust**, která bude vhodná pro většinu aplikací.

12. V nabídce vyberte **soubor**, **Uložit jako** . Zobrazí se dialogové okno možnosti podepisování, které vás vyzve k podepsání manifestu aplikace.

13. Pokud máte certifikát uložený jako soubor v systému souborů, použijte možnost **podepsat se souborem certifikátu** a vyberte certifikát ze systému souborů pomocí tlačítka se třemi tečkami ( **...** ). Pak zadejte heslo certifikátu.

     -nebo-

     Pokud je váš certifikát uložený v úložišti certifikátů, které je dostupné z vašeho počítače, vyberte možnost **podepsat s uloženým certifikátem** a vyberte certifikát ze seznamu poskytnutých.

14. Pro podepsání manifestu aplikace klikněte na tlačítko **OK** . Zobrazí se dialogové okno **Uložit jako** .

15. V dialogovém okně **Uložit jako** zadejte adresář verze a pak klikněte na **Uložit**.

16. V nabídce vyberte **soubor**, **Nový**, **manifest nasazení** a vytvořte svůj manifest nasazení.

17. Na kartě **název** zadejte název a číslo verze pro toto nasazení (**1.0.0.0** v tomto příkladu). Zadejte také **procesor** , pro který je aplikace sestavená, například x86.

18. Vyberte kartu **Popis** a zadejte hodnoty pro **vydavatele** a **produkt**. (**Produkt** je název daný vaší aplikaci v nabídce Start systému Windows, když se vaše aplikace nainstaluje na klientský počítač pro použití v režimu offline.)

19. Vyberte kartu **Možnosti nasazení** a v textovém poli **Začátek umístění** zadejte umístění manifestu aplikace na webovém serveru nebo sdílené složce. Například *\\\myServer\myShare\AppToDeploy.Application*.

20. Pokud jste v předchozím kroku přidali rozšíření *. deploy* , vyberte zde také možnost **použít. nasadit příponu názvu souboru** .

21. Vyberte kartu **Možnosti aktualizace** a určete, jak často se má tato aplikace aktualizovat. Pokud vaše aplikace používá <xref:System.Deployment.Application.UpdateCheckInfo> ke kontrole samotných aktualizací, zrušte zaškrtnutí políčka **Tato aplikace by měla vyhledávat aktualizace** .

22. Vyberte kartu **odkaz na aplikaci** a pak klikněte na tlačítko **Vybrat manifest** . Zobrazí se dialogové okno otevřít.

23. Vyberte manifest aplikace, který jste vytvořili dříve, a pak klikněte na **otevřít**.

24. V nabídce vyberte **soubor**, **Uložit jako** . Zobrazí se dialogové okno **možnosti podepisování** , které vás vyzve k podepsání manifestu nasazení.

25. Pokud máte certifikát uložený jako soubor v systému souborů, použijte možnost **podepsat se souborem certifikátu** a vyberte certifikát ze systému souborů pomocí tlačítka se třemi tečkami ( **...** ). Pak zadejte heslo certifikátu.

     -nebo-

     Pokud je váš certifikát uložený v úložišti certifikátů, které je dostupné z vašeho počítače, vyberte možnost **podepsat s uloženým certifikátem** a vyberte certifikát ze seznamu poskytnutých.

26. Pro podepsání manifestu nasazení klikněte na tlačítko **OK** . Zobrazí se dialogové okno **Uložit jako** .

27. V dialogovém okně **Uložit jako** přesuňte jeden adresář do kořenového adresáře nasazení a pak klikněte na **Uložit**.

28. Zkopírujte všechny soubory v adresáři nasazení do cílového umístění nebo na médium nasazení. Může to být složka na webu nebo serveru FTP, sdílená složka nebo jednotka CD-ROM.

29. Poskytněte uživatelům adresu URL, cestu UNC nebo fyzické médium potřebné k instalaci vaší aplikace. Pokud zadáte adresu URL nebo cestu UNC, musíte uživatelům poskytnout úplnou cestu k manifestu nasazení. Pokud je například AppToDeploy nasazena do http://webserver01/ v adresáři AppToDeploy, bude úplná cesta URL http://webserver01/AppToDeploy/AppToDeploy.application.

## <a name="next-steps"></a>Další kroky
 Pokud potřebujete nasadit novou verzi aplikace, vytvořte nový adresář s názvem po nové verzi (třeba 1.0.0.1) a zkopírujte nové soubory aplikace do nového adresáře. Dále je nutné postupovat podle předchozích kroků k vytvoření a podepsání nového manifestu aplikace a aktualizaci a podepsání manifestu nasazení. Buďte opatrní, abyste zadali stejnou vyšší verzi v `-New` *Mage. exe* a `-Update` volání, protože [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aktualizuje jenom novější verze s největším největším celým číslem. Pokud jste použili *MageUI. exe*, můžete manifest nasazení aktualizovat otevřením, výběrem karty **odkaz na aplikaci** , kliknutím na tlačítko **Vybrat manifest** a následným výběrem aktualizovaného manifestu aplikace.

## <a name="see-also"></a>Viz také:
- [Mage.exe (Manifest Generation and Editing Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [MageUI.exe (Manifest Generation and Editing Tool, grafický klient)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)
- [Publikování aplikací ClickOnce](../deployment/publishing-clickonce-applications.md)
- [ClickOnce – manifest nasazení](../deployment/clickonce-deployment-manifest.md)
- [Manifest aplikace ClickOnce](../deployment/clickonce-application-manifest.md)