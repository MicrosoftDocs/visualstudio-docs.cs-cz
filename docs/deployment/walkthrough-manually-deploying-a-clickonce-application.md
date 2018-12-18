---
title: 'Návod: Ruční nasazení aplikace ClickOnce | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e9f25c0e0b60a3b0f52df534db8f3593a26a435a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49902873"
---
# <a name="walkthrough-manually-deploy-a-clickonce-application"></a>Návod: Ruční nasazení aplikace ClickOnce
Pokud Visual Studio nelze použít k nasazení vaší [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace, nebo potřebujete používat funkce pokročilého nasazení, jako je například nasazení důvěryhodné aplikace, měli byste použít *Mage.exe* nástroj příkazového řádku k vytvoření vašeho [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesty. Tento návod popisuje, jak vytvořit [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazení pomocí příkazového řádku verze (*Mage.exe*) nebo grafický verze (*MageUI.exe*) generování manifestu a Nástroj pro úpravy.  
  
## <a name="prerequisites"></a>Požadavky  
 Tento názorný postup obsahuje některé požadavky a možnosti, které je nutné zvolit před vytvořením nasazení.  
  
- Nainstalujte *Mage.exe* a *MageUI.exe*.  
  
   *Mage.exe* a *MageUI.exe* jsou součástí [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Musí mít buď [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] nainstalované nebo verzi [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] součástí sady Visual Studio. Další informace najdete v tématu [sady Windows SDK](http://go.microsoft.com/fwlink/?LinkId=158044) na webové stránce MSDN.  
  
- Poskytují aplikace k nasazení.  
  
   Tento názorný průvodce předpokládá, že budete mít aplikaci Windows, který jste připraveni k nasazení. Tato aplikace bude uvedené jako AppToDeploy.  
  
- Zjistěte, jak se bude distribuovat nasazení.  
  
   Zahrnují možnosti distribuce: Web, sdílenou složku nebo disk CD. Další informace najdete v tématu [ClickOnce – zabezpečení a nasazení](../deployment/clickonce-security-and-deployment.md).  
  
- Určete, jestli aplikace vyžaduje zvýšenou úroveň vztahu důvěryhodnosti.  
  
   Pokud vaše aplikace vyžaduje úplný vztah důvěryhodnosti – například úplný přístup k systému uživatele, můžete použít `-TrustLevel` možnost *Mage.exe* nastavit. Pokud chcete definovat vlastní sadu pro vaši aplikaci oprávnění, můžete zkopírovat části oprávnění Internetu nebo intranetu z jiného manifestu, ho upravit tak, aby odpovídala vašim potřebám a přidejte ho do manifestu aplikace, buď pomocí textového editoru nebo  *MageUI.exe*. Další informace najdete v tématu [Přehled nasazení důvěryhodných aplikací](../deployment/trusted-application-deployment-overview.md).  
  
- Získání certifikátu pomocí technologie Authenticode.  
  
   Předplatné nasazení s certifikátem Authenticode. Pomocí sady Visual Studio, můžete vygenerovat certifikát testu *MageUI.exe*, nebo *MakeCert.exe* a *Pvk2Pfx.exe* nástroje, nebo můžete certifikát můžete získat z certifikátu Autorita (CA). Pokud budete chtít použít nasazení důvěryhodné aplikace, musíte také provést jednorázová instalace certifikátu do všech klientských počítačů. Další informace najdete v tématu [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
  > [!NOTE]
  >  Můžete se přihlásit taky nasazení certifikátem CNG, který můžete získat od certifikační autority.  
  
- Ujistěte se, že aplikace nemá manifest s informacemi o nástroji Řízení uživatelských účtů.  
  
   Je potřeba určit, jestli vaše aplikace obsahuje manifest s informacemi řízení uživatelských účtů (UAC), například `<dependentAssembly>` elementu. Prozkoumat manifest aplikace, můžete použít Windows Sysinternals [Sigcheck](http://go.microsoft.com/fwlink/?LinkId=158035) nástroj.  
  
   Pokud vaše aplikace obsahuje manifest s podrobnostmi o nástroji Řízení uživatelských účtů, je nutné znovu vytvořit bez informace o nástroji Řízení uživatelských účtů. Pro projekt C# v sadě Visual Studio otevřete vlastnosti projektu a vyberte kartu aplikace. V **Manifest** rozevíracího seznamu vyberte **vytvořit aplikaci bez manifestu**. Pro projekt jazyka Visual Basic v sadě Visual Studio, otevřete vlastnosti projektu, vyberte kartu aplikace a klikněte na tlačítko **nastavení nástroje Řízení uživatelských účtů zobrazení**. V otevřeném souboru manifestu, odeberte všechny prvky v rámci jednoho `<asmv1:assembly>` elementu.  
  
- Zjistěte, jestli aplikace vyžaduje požadavky na klientském počítači.  
  
   [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace nasazené v sadě Visual Studio můžete zahrnout zaváděcí nástroj instalace nezbytné součásti (*setup.exe*) v rámci vašeho nasazení. Tento návod vytvoří dva vyžadované pro manifesty [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazení. Zaváděcí můžete vytvořit pomocí [GenerateBootstrapper – úloha](../msbuild/generatebootstrapper-task.md).  
  
### <a name="to-deploy-an-application-with-the-mageexe-command-line-tool"></a>K nasazení aplikace pomocí nástroje příkazového řádku Mage.exe  
  
1. Vytvoření adresáře, ve kterém budete ukládat vaše [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] soubory nasazení.  
  
2. V adresáři nasazení, který jste právě vytvořili vytvořte podadresář s verzí. Pokud je to poprvé, že nasazujete aplikace, název podadresáře verze **1.0.0.0**.  
  
   > [!NOTE]
   >  Verze vašeho nasazení může být liší od verze vaší aplikace.  
  
3. Zkopírujte všechny soubory aplikace do podadresáře verze, včetně spustitelných souborů, sestavení, prostředky a datové soubory. V případě potřeby můžete vytvořit další podadresářů, které obsahují další soubory.  
  
4. Otevřít [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] nebo Visual Studio příkazového řádku a změňte verzi podadresář.  
  
5. Vytvořte manifest aplikace pomocí volání *Mage.exe*. Následující příkaz vytvoří manifest aplikace pro kód zkompilovaný ke spuštění na procesor Intel x86.  
  
   ```cmd
   mage -New Application -Processor x86 -ToFile AppToDeploy.exe.manifest -name "My App" -Version 1.0.0.0 -FromDirectory .   
   ```  
  
   > [!NOTE]
   >  Nezapomeňte použít tečku (.) po `-FromDirectory` možnost, která označuje aktuální adresář. Pokud neuvedete, tečky, musíte zadat cestu k souborům aplikace.  
  
6. Podepsat manifest aplikace certifikátem Authenticode. Nahraďte *mycert.pfx* s cestou k souboru certifikátu. Nahraďte *hesel* heslem pro váš soubor certifikátu.  
  
   ```cmd
   mage -Sign AppToDeploy.exe.manifest -CertFile mycert.pfx -Password passwd  
   ```  
  
   Od verze sady SDK rozhraní .NET Framework 4.6.2, který je distribuován v sadě Visual Studio a sadou Windows SDK, *mage.exe* podepíše manifest s CNG, stejně jako s certifikáty Authenticode. Stejně jako u Authenticode certifikáty použijte stejné parametry příkazového řádku.
    
7. Přejděte do kořenového adresáře nasazení.  
  
8. Generovat manifest nasazení pomocí volání *Mage.exe*. Ve výchozím nastavení *Mage.exe* označí vaši [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazení jako nainstalovaná aplikace, takže ji můžete spustit online a offline. Aby byla aplikace k dispozici pouze v případě, že uživatel je online, použijte `-Install` možnost s hodnotou `false`. Pokud použijete výchozí nastavení a budou uživatelé instalovat aplikace z webové stránky nebo sdílené složky, ujistěte se, že hodnota `-ProviderUrl` možnost odkazuje na umístění aplikace manifestu na webovém serveru nebo sdílené složky.  
  
   ```cmd  
   mage -New Deployment -Processor x86 -Install true -Publisher "My Co." -ProviderUrl "\\myServer\myShare\AppToDeploy.application" -AppManifest 1.0.0.0\AppToDeploy.exe.manifest -ToFile AppToDeploy.application  
   ```  
  
9. Podepsat manifest nasazení vaším certifikátem Authenticode nebo CNG.  
  
    ```cmd  
    mage -Sign AppToDeploy.application -CertFile mycert.pfx -Password passwd  
    ```  
  
10. Zkopírujte všechny soubory v adresáři pro nasazení na cílové nasazení nebo média. To může být buď složka na webovou stránku nebo serveru FTP, sdílené složky nebo disku CD-ROM.  
  
11. Uživatelům poskytnout adresu URL, název UNC nebo fyzická média, které jsou potřebné k instalaci vaší aplikace. Zadáte adresu URL nebo UNC, je nutné zadat úplnou cestu uživatele do manifestu nasazení. Například pokud AppToDeploy nasazuje do http://webserver01/ v adresáři AppToDeploy úplná cesta adresy URL by http://webserver01/AppToDeploy/AppToDeploy.application.  
  
### <a name="to-deploy-an-application-with-the-mageuiexe-graphical-tool"></a>K nasazení aplikace pomocí grafického nástroje MageUI.exe  
  
1. Vytvoření adresáře, ve kterém budete ukládat vaše [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] soubory nasazení.  
  
2. V adresáři nasazení, který jste právě vytvořili vytvořte podadresář s verzí. Pokud je to poprvé, že nasazujete aplikace, název podadresáře verze **1.0.0.0**.  
  
   > [!NOTE]
   >  Verze vašeho nasazení je pravděpodobně odlišná od verze aplikace.  
  
3. Zkopírujte všechny soubory aplikace do podadresáře verze, včetně spustitelných souborů, sestavení, prostředky a datové soubory. V případě potřeby můžete vytvořit další podadresářů, které obsahují další soubory.  
  
4. Spustit *MageUI.exe* grafického nástroje.  
  
   ```cmd  
   MageUI.exe  
   ```  
  
5. Vytvořit nový manifest aplikace tak, že vyberete **souboru**, **nový**, **Manifest aplikace** z nabídky.  
  
6. Ve výchozím **název** kartu, zadejte název a verzi číslo tohoto nasazení. Také určit, **procesoru** , která je sestavená vaše aplikace, jako je například x86.  
  
7. Vyberte **soubory** kartě a klikněte na tlačítko se třemi tečkami (**...** ) vedle **adresáře aplikace** textového pole. A **vyhledat složku** zobrazí se dialogové okno.  
  
8. Vyberte verzi podadresář obsahující soubory aplikace a pak klikněte na tlačítko **OK**.  
  
9. Pokud nasazujete z Internetové informační služby (IIS), vyberte **při sestavování přidat příponu .deploy odstraní do souboru, která není nutné** zaškrtávací políčko.  
  
10. Klikněte na tlačítko **naplnit** a přidejte všechny soubory aplikace do seznamu. Pokud vaše aplikace obsahuje více než jeden spustitelný soubor, označte hlavní spustitelný soubor pro toto nasazení jako při spuštění aplikace tak, že vyberete **vstupní bod** z **typ souboru** rozevíracího seznamu. (Pokud vaše aplikace obsahuje pouze jeden spustitelný soubor, *MageUI.exe* označí za vás.)  
  
11. Vyberte **oprávněních** kartě a vyberte úroveň vztahu důvěryhodnosti, musíte aplikaci k vyhodnocení. Výchozí hodnota je **FullTrust**, která bude vhodná pro většinu aplikací.  
  
12. Vyberte **souboru**, **uložit jako** z nabídky. Zobrazí se dialogové okno Možnosti podpisu, výzvou k podepsání manifestu aplikace.  
  
13. Pokud máte certifikát uložený jako soubor ve vašem systému souborů, použijte **podepsat pomocí souboru certifikátu** možnost a vyberte certifikát ze systému souborů pomocí tří teček (**...** ) tlačítko. Znovu zadejte heslo certifikátu.  
  
     -nebo-  
  
     Pokud váš certifikát se ukládají v úložišti certifikátů dostupný z vašeho počítače, vyberte **přihlašování pomocí uloženého certifikátu** možnost a vyberte certifikát ze seznamu.  
  
14. Klikněte na tlačítko **OK** podepsat manifest aplikace. **Uložit jako** zobrazí se dialogové okno.  
  
15. V **uložit jako** dialogové okno, zadejte adresář, verze a potom klikněte na tlačítko **Uložit**.  
  
16. Vyberte **souboru**, **nový**, **Manifest nasazení** z nabídky pro vytvoření manifestu nasazení.  
  
17. Na **název** kartu, zadejte název a verzi číslo pro toto nasazení (**1.0.0.0** v tomto příkladu). Také určit, **procesoru** , která je sestavená vaše aplikace, jako je například x86.  
  
18. Vyberte **popis** kartu a zadejte hodnoty pro **vydavatele** a **produktu**. (**Produktu** je název zadaný pro vaše aplikace v nabídce Windows Start při instalaci aplikace na klientském počítači pro použití v offline režimu.)  
  
19. Vyberte **možnosti nasazení** kartu a v **počáteční umístění** textové pole, zadejte umístění manifestu aplikace na webovém serveru nebo sdílené složky. Například  *\\\myServer\myShare\AppToDeploy.application*.  
  
20. Pokud jste přidali *.deploy* rozšíření v předchozím kroku, také vybrat **použít příponu názvu souboru .deploy** tady.  
  
21. Vyberte **možnosti aktualizace** kartu a určete, jak často chcete aktualizovat tento aplikaci. Pokud vaše aplikace používá <xref:System.Deployment.Application.UpdateCheckInfo> vyhledat aktualizace samotné, zrušte **tato aplikace by měla vyhledávat aktualizace** zaškrtávací políčko.  
  
22. Vyberte **odkaz na aplikaci** kartu a potom klikněte na tlačítko **manifestu vyberte** tlačítko. Otevřené dialogové okno se zobrazí.  
  
23. Vyberte manifestu aplikace, kterou jste vytvořili dříve a pak klikněte na tlačítko **otevřít**.  
  
24. Vyberte **souboru**, **uložit jako** z nabídky. A **možnosti podpisu** zobrazí se dialogové okno s výzvou k podepsání manifestu nasazení.  
  
25. Pokud máte certifikát uložený jako soubor ve vašem systému souborů, použijte **podepsat pomocí souboru certifikátu** možnost a vyberte certifikát ze systému souborů pomocí tří teček (**...** ) tlačítko. Znovu zadejte heslo certifikátu.  
  
     -nebo-  
  
     Pokud váš certifikát se ukládají v úložišti certifikátů dostupný z vašeho počítače, vyberte **přihlašování pomocí uloženého certifikátu** možnost a vyberte certifikát ze seznamu.  
  
26. Klikněte na tlačítko **OK** pro podepsání manifestu nasazení. **Uložit jako** zobrazí se dialogové okno.  
  
27. V **uložit jako** dialogovém okně nahoru jednoho adresáře do kořenového adresáře vašeho nasazení a pak klikněte na tlačítko **Uložit**.  
  
28. Zkopírujte všechny soubory v adresáři pro nasazení na cílové nasazení nebo média. To může být buď složka na webovou stránku nebo serveru FTP, sdílené složky nebo disku CD-ROM.  
  
29. Uživatelům poskytnout adresu URL, název UNC nebo fyzická média, které jsou potřebné k instalaci vaší aplikace. Pokud zadáte adresu URL nebo UNC, musí poskytnout uživatelům úplnou cestu k manifestu nasazení. Například pokud AppToDeploy nasazuje do http://webserver01/ v adresáři AppToDeploy úplná cesta adresy URL by http://webserver01/AppToDeploy/AppToDeploy.application.  
  
## <a name="next-steps"></a>Další kroky  
 Pokud potřebujete nasadit novou verzi aplikace, vytvořte nový adresář s názvem za novou verzi, například 1.0.0.1 — a kopírovat soubory nové aplikace do nového adresáře. Dále je třeba použít předchozí postup vytvoření a podepsání nový manifest aplikace a aktualizace a podepsání manifestu nasazení. Buďte opatrní určete stejné vyšší verzi v obou *Mage.exe* `-New` a `-Update` volání, jako [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nejvýznamnější nejvíce vlevo celé aktualizuje pouze vyšší verze. Pokud jste použili *MageUI.exe*, manifest nasazení můžete aktualizovat otevřením, vyberete **odkaz na aplikaci** kartu, kliknutím **manifestu vyberte** tlačítko, a výběrem manifestu aktualizovanou aplikaci.  
  
## <a name="see-also"></a>Viz také:  
 [Mage.exe (generování manifestu a nástroj pro úpravy)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [MageUI.exe (Manifest Generation and Editing Tool, grafický klient)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)   
 [Publikování aplikací ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [ClickOnce – manifest nasazení](../deployment/clickonce-deployment-manifest.md)   
 [ClickOnce – manifest aplikace](../deployment/clickonce-application-manifest.md)