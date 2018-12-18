---
title: 'Postupy: Opětovné podepisování manifestů aplikace a nasazení | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Office applications, signing manifests
- deploying applications [ClickOnce], signing manifests
- deploying applications, signing manifests
- ClickOnce deployment, signing manifests
- Office development in Visual Studio, signing manifests
ms.assetid: d53bceb9-4d3b-4c22-b909-8f370e7231fb
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cce175f487d24e528d7527c424a1f76fa2a82824
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44280672"
---
# <a name="how-to-re-sign-application-and-deployment-manifests"></a>Postupy: Opětovné podepisování manifestů aplikace a nasazení
Když provedete změny vlastnosti nasazení v manifestu aplikace pro aplikace Windows Forms, aplikace Windows Presentation Foundation (xbap) nebo řešení pro systém Office, musíte znovu podepsat obě aplikace a manifesty nasazení se certifikát. Tento proces pomáhá zajistit, že zmanipulovanou soubory nejsou nainstalované v počítačích koncových uživatelů.  
  
 Jiný scénář, kde může být znovu podepište manifesty je, pokud zákazníci chtějí k podepsání aplikace a manifesty nasazení vlastním certifikátem.  
  
## <a name="re-sign-the-application-and-deployment-manifests"></a>Znovu podepište manifesty nasazení a aplikace  
 Tento postup předpokládá, že jste už provedli změny do souboru manifestu aplikace (*.manifest*). Další informace najdete v tématu [postupy: Změna vlastností nasazení](https://msdn.microsoft.com/library/66052a3a-8127-4964-8147-2477ef5d1472).  
  
#### <a name="to-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>K opětovnému podepsání aplikace a nasazení manifestů s Mage.exe  
  
1.  Otevřít **příkazový řádek sady Visual Studio** okna.  
  
2.  Přejděte do složky, která obsahuje soubory manifestu, které chcete podepsat.  
  
3.  Zadejte následující příkaz k podepsání souboru manifestu aplikace. Nahraďte *manifestu* s názvem souboru manifestu a rozšíření. Nahraďte *certifikát* úplnou nebo relativní cestou k souboru certifikátu a nahraďte *heslo* se heslo pro certifikát.  
  
    ```cmd  
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Můžete například spustit následující příkaz k podepsání manifestu aplikace pro doplněk, aplikace Windows Form nebo aplikace Windows Presentation Foundation prohlížeče. Dočasné certifikáty vytvořené pomocí sady Visual Studio se nedoporučuje pro nasazení do produkčního prostředí.  
  
    ```cmd  
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
4.  Zadejte následující příkaz k aktualizaci a podepsat soubor manifestu nasazení, nahraďte zástupné názvy jako v předchozím kroku.  
  
    ```cmd  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Můžete například spustit následující příkaz k aktualizaci a podepsání manifestu nasazení pro doplněk aplikace Excel, aplikace modelu Windows Forms nebo aplikace Windows Presentation Foundation prohlížeče.  
  
    ```cmd  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  Volitelně můžete zkopírovat hlavní manifest nasazení (*publikovat\\\<název_aplikace > .application*) do adresáře nasazení vaší verze (*publish\Application soubory\\ \<název_aplikace > _\<verze >*).  
  
## <a name="update-and-re-sign-the-application-and-deployment-manifests"></a>Aktualizace a opětovné podepisování manifestů aplikace a nasazení  
 Tento postup předpokládá, že jste už provedli změny do souboru manifestu aplikace (*.manifest*), ale, že existují další soubory, které byly aktualizovány. Když jsou aktualizovány soubory, je nutné aktualizovat také-the-hash, který představuje soubor.  
  
#### <a name="to-update-and-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Aktualizace a opětovné podepisování aplikace a nasazení manifestů s Mage.exe  
  
1.  Otevřít **příkazový řádek sady Visual Studio** okna.  
  
2.  Přejděte do složky, která obsahuje soubory manifestu, které chcete podepsat.  
  
3.  Odeberte *.deploy* přípona souboru ze souborů v okně Publikovat výstupní složka.  
  
4.  Zadejte následující příkaz k aktualizaci manifestu aplikace se nové hodnoty hash pro aktualizované soubory a podepsání souboru manifestu aplikace. Nahraďte *manifestu* s názvem souboru manifestu a rozšíření. Nahraďte *certifikát* úplnou nebo relativní cestou k souboru certifikátu a nahraďte *heslo* se heslo pro certifikát.  
  
    ```cmd  
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Můžete například spustit následující příkaz k podepsání manifestu aplikace pro doplněk, aplikace Windows Form nebo aplikace Windows Presentation Foundation prohlížeče. Dočasné certifikáty vytvořené pomocí sady Visual Studio se nedoporučuje pro nasazení do produkčního prostředí.  
  
    ```cmd  
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  Zadejte následující příkaz k aktualizaci a podepsat soubor manifestu nasazení, nahraďte zástupné názvy jako v předchozím kroku.  
  
    ```cmd  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Můžete například spustit následující příkaz k aktualizaci a podepsání manifestu nasazení pro doplněk aplikace Excel, aplikace modelu Windows Forms nebo aplikace Windows Presentation Foundation prohlížeče.  
  
    ```cmd  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
6.  Přidat *.deploy* příponu souboru zpět k souborům, s výjimkou souborů manifestů aplikace a nasazení.  
  
7.  Volitelně můžete zkopírovat hlavní manifest nasazení (*publikovat\\\<název_aplikace > .application*) do adresáře nasazení vaší verze (*publish\Application soubory\\ \<název_aplikace > _\<verze >*).  
  
## <a name="see-also"></a>Viz také:  
 [Zabezpečení aplikací ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Zabezpečení přístupu ke kódu pro aplikace ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce a kód Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Přehled nasazení důvěryhodných aplikací](../deployment/trusted-application-deployment-overview.md)   
 [Postupy: povolení nastavení zabezpečení ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Postupy: nastavení zóny zabezpečení pro aplikaci ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Postupy: nastavení vlastních oprávnění pro aplikaci ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Postupy: ladění aplikace ClickOnce s omezenými oprávněními](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Postupy: Přidání důvěryhodného vydavatele na klientský počítač pro aplikace ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [Postupy: Konfigurace chování výzvy důvěryhodnosti ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)