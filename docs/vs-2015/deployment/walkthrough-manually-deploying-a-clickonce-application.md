---
title: 'Návod: Ruční nasazení aplikace ClickOnce | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 51
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 4e8874324c5e5cbfb5bc42e5c6c23666b5e14b67
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49236168"
---
# <a name="walkthrough-manually-deploying-a-clickonce-application"></a>Návod: Ruční nasazení aplikace ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud Visual Studio nelze použít k nasazení vaší [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace, nebo potřebujete používat funkce pokročilého nasazení, jako je například nasazení důvěryhodné aplikace by měla použít nástroj příkazového řádku Mage.exe k vytvoření vašeho [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifesty. Tento návod popisuje, jak vytvořit [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazení pomocí rozhraní příkazového řádku verze (Mage.exe) nebo grafický verze (MageUI.exe) Manifest Generation and Editing Tool.  
  
## <a name="prerequisites"></a>Požadavky  
 Tento názorný postup obsahuje některé požadavky a možnosti, které je nutné zvolit před vytvořením nasazení.  
  
-   Nainstalujte Mage.exe a MageUI.exe.  
  
     Mage.exe a MageUI.exe jsou součástí [!INCLUDE[winsdklong](../includes/winsdklong-md.md)]. Musí mít buď [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] nainstalované nebo verzi [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] součástí sady Visual Studio. Další informace najdete v tématu [sady Windows SDK](http://go.microsoft.com/fwlink/?LinkId=158044) na webové stránce MSDN.  
  
-   Poskytují aplikace k nasazení.  
  
     Tento názorný průvodce předpokládá, že budete mít aplikaci Windows, který jste připraveni k nasazení. Tato aplikace bude uvedené jako AppToDeploy.  
  
-   Zjistěte, jak se bude distribuovat nasazení.  
  
     Zahrnují možnosti distribuce: Web, sdílenou složku nebo disk CD. Další informace najdete v tématu [ClickOnce – zabezpečení a nasazení](../deployment/clickonce-security-and-deployment.md).  
  
-   Určete, jestli aplikace vyžaduje zvýšenou úroveň vztahu důvěryhodnosti.  
  
     Pokud vaše aplikace vyžaduje úplný vztah důvěryhodnosti – například úplný přístup k systému uživatele, můžete použít `-TrustLevel` – možnost nástroje Mage.exe nastavit. Pokud chcete definovat vlastní sadu pro vaši aplikaci oprávnění, kopírovat části oprávnění Internetu nebo intranetu z jiného manifestu, ho upravit tak, aby odpovídala vašim potřebám a přidejte ho do manifestu aplikace pomocí textového editoru nebo MageUI.exe. Další informace najdete v tématu [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
-   Získání certifikátu pomocí technologie Authenticode.  
  
     Předplatné nasazení s certifikátem Authenticode. Testovací certifikát můžete vygenerovat pomocí nástrojů sady Visual Studio, MageUI.exe, nebo MakeCert.exe a Pvk2Pfx.exe, nebo můžete získat certifikát z certifikační autority (CA). Pokud budete chtít použít nasazení důvěryhodné aplikace, musíte také provést jednorázová instalace certifikátu do všech klientských počítačů. Další informace najdete v tématu [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
    > [!NOTE]
    >  Můžete se přihlásit taky nasazení certifikátem CNG, který můžete získat od certifikační autority.  
  
-   Ujistěte se, že aplikace nemá manifest s informacemi o nástroji Řízení uživatelských účtů.  
  
     Je potřeba určit, jestli vaše aplikace obsahuje manifest s informacemi řízení uživatelských účtů (UAC), například `<dependentAssembly>` elementu. Prozkoumat manifest aplikace, můžete použít Windows Sysinternals [Sigcheck](http://go.microsoft.com/fwlink/?LinkId=158035) nástroj.  
  
     Pokud vaše aplikace obsahuje manifest s podrobnostmi o nástroji Řízení uživatelských účtů, je nutné znovu vytvořit bez informace o nástroji Řízení uživatelských účtů. Pro projekt C# v sadě Visual Studio otevřete vlastnosti projektu a vyberte kartu aplikace. V **Manifest** rozevíracího seznamu vyberte **vytvořit aplikaci bez manifestu**. Pro projekt jazyka Visual Basic v sadě Visual Studio, otevřete vlastnosti projektu, vyberte kartu aplikace a klikněte na tlačítko **nastavení nástroje Řízení uživatelských účtů zobrazení**. V otevřeném souboru manifestu, odeberte všechny prvky v rámci jednoho `<asmv1:assembly>` elementu.  
  
-   Zjistěte, jestli aplikace vyžaduje požadavky na klientském počítači.  
  
     [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace nasazené v sadě Visual Studio můžete zahrnout instalace nezbytné součásti zaváděcí nástroj (setup.exe) v rámci vašeho nasazení. Tento návod vytvoří dva vyžadované pro manifesty [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazení. Zaváděcí můžete vytvořit pomocí [GenerateBootstrapper – úloha](../msbuild/generatebootstrapper-task.md).  
  
### <a name="to-deploy-an-application-with-the-mageexe-command-line-tool"></a>K nasazení aplikace pomocí nástroje příkazového řádku Mage.exe  
  
1.  Vytvoření adresáře, ve kterém budete ukládat vaše [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] soubory nasazení.  
  
2.  V adresáři nasazení, který jste právě vytvořili vytvořte podadresář s verzí. Pokud je to poprvé, že nasazujete aplikace, název podadresáře verze **1.0.0.0**.  
  
    > [!NOTE]
    >  Verze vašeho nasazení může být liší od verze vaší aplikace.  
  
3.  Zkopírujte všechny soubory aplikace do podadresáře verze, včetně spustitelných souborů, sestavení, prostředky a datové soubory. V případě potřeby můžete vytvořit další podadresářů, které obsahují další soubory.  
  
4.  Otevřít [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] nebo Visual Studio příkazového řádku a změňte verzi podadresář.  
  
5.  Vytvořte manifest aplikace pomocí volání Mage.exe. Následující příkaz vytvoří manifest aplikace pro kód zkompilovaný ke spuštění na procesor Intel x86.  
  
    ```  
    mage -New Application -Processor x86 -ToFile AppToDeploy.exe.manifest -name "My App" -Version 1.0.0.0 -FromDirectory .   
    ```  
  
    > [!NOTE]
    >  Nezapomeňte použít tečku (.) po `-FromDirectory` možnost, která označuje aktuální adresář. Pokud neuvedete, tečky, musíte zadat cestu k souborům aplikace.  
  
6.  Podepsat manifest aplikace certifikátem Authenticode. Nahraďte *mycert.pfx* s cestou k souboru certifikátu. Nahraďte *hesel* heslem pro váš soubor certifikátu.  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile mycert.pfx -Password passwd  
    ```  
  
     Podepsat manifest aplikace certifikátem CNG, použijte následující postup. Nahraďte *cngCert.pfx* s cestou k souboru certifikátu.  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile cngCert.pfx  
    ```  
  
7.  Přejděte do kořenového adresáře nasazení.  
  
8.  Generovat manifest nasazení pomocí volání Mage.exe. Ve výchozím nastavení, Mage.exe označí vaši [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazení jako nainstalovaná aplikace, takže ji můžete spustit online a offline. Aby byla aplikace k dispozici pouze v případě, že uživatel je online, použijte `-Install` možnost s hodnotou `false`. Pokud použijete výchozí nastavení a budou uživatelé instalovat aplikace z webové stránky nebo sdílené složky, ujistěte se, že hodnota `-ProviderUrl` možnost odkazuje na umístění aplikace manifestu na webovém serveru nebo sdílené složky.  
  
    ```  
    mage -New Deployment -Processor x86 -Install true -Publisher "My Co." -ProviderUrl "\\myServer\myShare\AppToDeploy.application" -AppManifest 1.0.0.0\AppToDeploy.exe.manifest -ToFile AppToDeploy.application  
    ```  
  
9. Podepsat manifest nasazení vaším certifikátem Authenticode nebo CNG.  
  
    ```  
    mage -Sign AppToDeploy.application -CertFile mycert.pfx -Password passwd  
    ```  
  
     or  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile cngCert.pfx  
    ```  
  
10. Zkopírujte všechny soubory v adresáři pro nasazení na cílové nasazení nebo média. To může být buď složka na webovou stránku nebo serveru FTP, sdílené složky nebo disku CD-ROM.  
  
11. Uživatelům poskytnout adresu URL, název UNC nebo fyzická média, které jsou potřebné k instalaci vaší aplikace. Zadáte adresu URL nebo UNC, je nutné zadat úplnou cestu uživatele do manifestu nasazení. Například pokud AppToDeploy nasazuje do http://webserver01/ v adresáři AppToDeploy úplná cesta adresy URL by http://webserver01/AppToDeploy/AppToDeploy.application.  
  
### <a name="to-deploy-an-application-with-the-mageuiexe-graphical-tool"></a>K nasazení aplikace pomocí grafického nástroje MageUI.exe  
  
1.  Vytvoření adresáře, ve kterém budete ukládat vaše [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] soubory nasazení.  
  
2.  V adresáři nasazení, který jste právě vytvořili vytvořte podadresář s verzí. Pokud je to poprvé, že nasazujete aplikace, název podadresáře verze **1.0.0.0**.  
  
    > [!NOTE]
    >  Verze vašeho nasazení je pravděpodobně odlišná od verze aplikace.  
  
3.  Zkopírujte všechny soubory aplikace do podadresáře verze, včetně spustitelných souborů, sestavení, prostředky a datové soubory. V případě potřeby můžete vytvořit další podadresářů, které obsahují další soubory.  
  
4.  Spuštění grafického nástroje MageUI.exe.  
  
    ```  
    MageUI.exe  
    ```  
  
5.  Vytvořit nový manifest aplikace tak, že vyberete **souboru**, **nový**, **Manifest aplikace** z nabídky.  
  
6.  Ve výchozím **název** kartu, zadejte název a verzi číslo tohoto nasazení. Také určit, **procesoru** , která je sestavená vaše aplikace, jako je například x86.  
  
7.  Vyberte **soubory** kartě a klikněte na tlačítko se třemi tečkami (**...** ) vedle **adresáře aplikace** textového pole. Zobrazí se dialogové okno Vyhledat složku.  
  
8.  Vyberte verzi podadresář obsahující soubory aplikace a pak klikněte na tlačítko **OK**.  
  
9. Pokud nasazujete z Internetové informační služby (IIS), vyberte **při sestavování přidat příponu .deploy odstraní do souboru, která není nutné** zaškrtávací políčko.  
  
10. Klikněte na tlačítko **naplnit** a přidejte všechny soubory aplikace do seznamu. Pokud vaše aplikace obsahuje více než jeden spustitelný soubor, označte hlavní spustitelný soubor pro toto nasazení jako při spuštění aplikace tak, že vyberete **vstupní bod** z **typ souboru** rozevíracího seznamu. (Pokud vaše aplikace obsahuje pouze jeden spustitelný soubor, MageUI.exe označíte ho za vás.)  
  
11. Vyberte **oprávněních** kartě a vyberte úroveň vztahu důvěryhodnosti, musíte aplikaci k vyhodnocení. Výchozí hodnota je **FullTrust**, která bude vhodná pro většinu aplikací.  
  
12. Vyberte **souboru**, **uložit jako** z nabídky. Zobrazí se dialogové okno Možnosti podpisu, výzvou k podepsání manifestu aplikace.  
  
13. Pokud máte certifikát uložený jako soubor ve vašem systému souborů, použijte **podepsat pomocí souboru certifikátu** možnost a vyberte certifikát ze systému souborů pomocí tří teček (**...** ) tlačítko. Znovu zadejte heslo certifikátu.  
  
     -nebo-  
  
     Pokud váš certifikát se ukládají v úložišti certifikátů dostupný z vašeho počítače, vyberte **přihlašování pomocí uloženého certifikátu** možnost a vyberte certifikát ze seznamu.  
  
14. Klikněte na tlačítko **OK** podepsat manifest aplikace. Zobrazí se dialogové okno Uložit jako.  
  
15. V dialogovém okně Uložit jako zadejte adresář, verze a potom klikněte na tlačítko **Uložit**.  
  
16. Vyberte **souboru**, **nový**, **Manifest nasazení** z nabídky pro vytvoření manifestu nasazení.  
  
17. Na **název** kartu, zadejte název a verzi číslo pro toto nasazení (**1.0.0.0** v tomto příkladu). Také určit, **procesoru** , která je sestavená vaše aplikace, jako je například x86.  
  
18. Vyberte **popis** kartu a zadejte hodnoty pro **vydavatele** a **produktu**. (**Produktu** je název zadaný pro vaše aplikace v nabídce Windows Start při instalaci aplikace na klientském počítači pro použití v offline režimu.)  
  
19. Vyberte **možnosti nasazení** kartu a v **počáteční umístění** textové pole, zadejte umístění manifestu aplikace na webovém serveru nebo sdílené složky. Například \\\myServer\myShare\AppToDeploy.application.  
  
20. Pokud jste přidali v předchozím kroku příponu .deploy, také vybrat **použít příponu názvu souboru .deploy** tady.  
  
21. Vyberte **možnosti aktualizace** kartu a určete, jak často chcete aktualizovat tento aplikaci. Pokud vaše aplikace používá <xref:System.Deployment.Application.UpdateCheckInfo> vyhledat aktualizace samotné, zrušte **tato aplikace by měla vyhledávat aktualizace** zaškrtávací políčko.  
  
22. Vyberte **odkaz na aplikaci** kartu a potom klikněte na tlačítko **manifestu vyberte** tlačítko. Otevřené dialogové okno se zobrazí.  
  
23. Vyberte manifestu aplikace, kterou jste vytvořili dříve a pak klikněte na tlačítko **otevřít**.  
  
24. Vyberte **souboru**, **uložit jako** z nabídky. Zobrazí se dialogové okno Možnosti podpisu, výzvou k podepsání manifestu nasazení.  
  
25. Pokud máte certifikát uložený jako soubor ve vašem systému souborů, použijte **podepsat pomocí souboru certifikátu** možnost a vyberte certifikát ze systému souborů pomocí tří teček (**...** ) tlačítko. Znovu zadejte heslo certifikátu.  
  
     -nebo-  
  
     Pokud váš certifikát se ukládají v úložišti certifikátů dostupný z vašeho počítače, vyberte **přihlašování pomocí uloženého certifikátu** možnost a vyberte certifikát ze seznamu.  
  
26. Klikněte na tlačítko **OK** pro podepsání manifestu nasazení. Zobrazí se dialogové okno Uložit jako.  
  
27. V **uložit jako** dialogovém okně nahoru jednoho adresáře do kořenového adresáře vašeho nasazení a pak klikněte na tlačítko **Uložit**.  
  
28. Zkopírujte všechny soubory v adresáři pro nasazení na cílové nasazení nebo média. To může být buď složka na webovou stránku nebo serveru FTP, sdílené složky nebo disku CD-ROM.  
  
29. Uživatelům poskytnout adresu URL, název UNC nebo fyzická média, které jsou potřebné k instalaci vaší aplikace. Pokud zadáte adresu URL nebo UNC, musí poskytnout uživatelům úplnou cestu k manifestu nasazení. Například pokud AppToDeploy nasazuje do http://webserver01/ v adresáři AppToDeploy úplná cesta adresy URL by http://webserver01/AppToDeploy/AppToDeploy.application.  
  
## <a name="next-steps"></a>Další kroky  
 Pokud potřebujete nasadit novou verzi aplikace, vytvořte nový adresář s názvem za novou verzi, například 1.0.0.1 — a kopírovat soubory nové aplikace do nového adresáře. Dále je třeba použít předchozí postup vytvoření a podepsání nový manifest aplikace a aktualizace a podepsání manifestu nasazení. Buďte opatrní určete stejné vyšší verzi v obou Mage.exe `-New` a `–Update` volání, jako [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nejvýznamnější nejvíce vlevo celé aktualizuje pouze vyšší verze. Pokud jste použili MageUI.exe, můžete aktualizovat manifest nasazení tak, že otevřete, vyberete **odkaz na aplikaci** kartu, kliknutím **manifestu vyberte** tlačítko a pak vyberete aktualizaci manifest aplikace.  
  
## <a name="see-also"></a>Viz také  
 [Mage.exe (generování manifestu a nástroj pro úpravy)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [MageUI.exe (Manifest Generation and Editing Tool, grafický klient)](http://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)   
 [Publikování aplikací ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [ClickOnce – Manifest nasazení](../deployment/clickonce-deployment-manifest.md)   
 [ClickOnce – manifest aplikace ](../deployment/clickonce-application-manifest.md)



