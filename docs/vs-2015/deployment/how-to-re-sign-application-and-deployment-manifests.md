---
title: 'Postupy: Opětovné podepisování manifestů aplikace a nasazení | Dokumentace Microsoftu'
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
- Office applications, signing manifests
- deploying applications [ClickOnce], signing manifests
- deploying applications, signing manifests
- ClickOnce deployment, signing manifests
- Office development in Visual Studio, signing manifests
ms.assetid: d53bceb9-4d3b-4c22-b909-8f370e7231fb
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 734258871e72e6272abcd61c4efa1a00765f8a32
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49185715"
---
# <a name="how-to-re-sign-application-and-deployment-manifests"></a>Postupy: Opětovné podepisování manifestů aplikace a nasazení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Když provedete změny vlastnosti nasazení v manifestu aplikace pro aplikace Windows Forms, aplikace Windows Presentation Foundation (xbap) nebo řešení pro systém Office, musíte znovu podepsat obě aplikace a manifesty nasazení se certifikát. Tento proces pomáhá zajistit, že zmanipulovanou soubory nejsou nainstalované v počítačích koncových uživatelů.  
  
 Jiný scénář, kde může být znovu podepište manifesty je, pokud zákazníci chtějí k podepsání aplikace a manifesty nasazení vlastním certifikátem.  
  
## <a name="re-signing-the-application-and-deployment-manifests"></a>Aplikace a nasazení opětovné podepisování manifestů  
 Tento postup předpokládá, že jste už provedli změny do souboru manifestu aplikace (.manifest). Další informace najdete v tématu [postupy: Změna vlastností nasazení](http://msdn.microsoft.com/en-us/66052a3a-8127-4964-8147-2477ef5d1472).  
  
#### <a name="to-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>K opětovnému podepsání aplikace a nasazení manifestů s Mage.exe  
  
1.  Otevřít **příkazový řádek sady Visual Studio** okna.  
  
2.  Přejděte do složky, která obsahuje soubory manifestu, které chcete podepsat.  
  
3.  Zadejte následující příkaz k podepsání souboru manifestu aplikace. Nahraďte názvem souboru manifestu plus rozšíření manifestu. Nahraďte úplnou nebo relativní cestu k souboru certifikátu certifikát a heslo nahraďte heslo pro certifikát.  
  
    ```  
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Můžete například spustit následující příkaz k podepsání manifestu aplikace pro doplněk, aplikace Windows Form nebo aplikace Windows Presentation Foundation prohlížeče. Dočasné certifikáty vytvořené pomocí sady Visual Studio se nedoporučuje pro nasazení do produkčního prostředí.  
  
    ```  
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
4.  Zadejte následující příkaz k aktualizaci a podepsat soubor manifestu nasazení, nahraďte zástupné názvy jako v předchozím kroku.  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Můžete například spustit následující příkaz k aktualizaci a podepsání manifestu nasazení pro doplněk aplikace Excel, aplikace modelu Windows Forms nebo aplikace Windows Presentation Foundation prohlížeče.  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  Volitelně můžete zkopírovat hlavní manifest nasazení (publikování\\*appname*.application) do adresáře nasazení vaší verze (soubory publish\Application\\*appname*_ *verze*).  
  
## <a name="updating-and-re-signing-the-application-and-deployment-manifests"></a>Aktualizace a opětovné podepsání aplikace a manifestů nasazení  
 Tento postup předpokládá, že již provedli jste změny do vaší aplikace (.manifest) soubor manifestu, ale, že existují další soubory, které byly aktualizovány. Když jsou aktualizovány soubory, je nutné aktualizovat také-the-hash, který představuje soubor.  
  
#### <a name="to-update-and-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Aktualizace a opětovné podepisování aplikace a nasazení manifestů s Mage.exe  
  
1.  Otevřít **příkazový řádek sady Visual Studio** okna.  
  
2.  Přejděte do složky, která obsahuje soubory manifestu, které chcete podepsat.  
  
3.  Odeberte příponu .deploy souborů ve výstupní složce publikovat.  
  
4.  Zadejte následující příkaz k aktualizaci manifestu aplikace se nové hodnoty hash pro aktualizované soubory a podepsání souboru manifestu aplikace. Nahraďte názvem souboru manifestu plus rozšíření manifestu. Nahraďte úplnou nebo relativní cestu k souboru certifikátu certifikát a heslo nahraďte heslo pro certifikát.  
  
    ```  
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Můžete například spustit následující příkaz k podepsání manifestu aplikace pro doplněk, aplikace Windows Form nebo aplikace Windows Presentation Foundation prohlížeče. Dočasné certifikáty vytvořené pomocí sady Visual Studio se nedoporučuje pro nasazení do produkčního prostředí.  
  
    ```  
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  Zadejte následující příkaz k aktualizaci a podepsat soubor manifestu nasazení, nahraďte zástupné názvy jako v předchozím kroku.  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Můžete například spustit následující příkaz k aktualizaci a podepsání manifestu nasazení pro doplněk aplikace Excel, aplikace modelu Windows Forms nebo aplikace Windows Presentation Foundation prohlížeče.  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
6.  Přidáte příponu souboru .deploy zpátky k souborům, s výjimkou souborů manifestů aplikace a nasazení.  
  
7.  Volitelně můžete zkopírovat hlavní manifest nasazení (publikování\\*appname*.application) do adresáře nasazení vaší verze (soubory publish\Application\\*appname*_ *verze*).  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečování aplikací ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Zabezpečení přístupu ke kódu pro aplikace ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce a kód Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Přehled nasazení důvěryhodných aplikací](../deployment/trusted-application-deployment-overview.md)   
 [Postupy: povolení nastavení zabezpečení ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Postupy: nastavení zóny zabezpečení pro aplikaci ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Postupy: nastavení vlastních oprávnění pro aplikaci ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Postupy: ladění aplikace ClickOnce s omezenými oprávněními](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Postupy: Přidání důvěryhodného vydavatele na klientský počítač pro aplikace ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [Postupy: Konfigurace chování výzvy důvěryhodnosti ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)



