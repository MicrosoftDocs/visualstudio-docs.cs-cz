---
title: 'Postupy: Opětovné podepsání manifestů aplikace a nasazení | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d5956ad23fe22c7c36b712fac61df268586142df
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697560"
---
# <a name="how-to-re-sign-application-and-deployment-manifests"></a>Postupy: Opětovné podepisování manifestů aplikace a nasazení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Poté, co provedete změny vlastností nasazení v manifestu aplikace pro aplikace model Windows Forms, Windows Presentation Foundation aplikací (XBAP) nebo řešení pro systém Office, je nutné znovu podepsat manifesty aplikace a nasazení pomocí certifikátu. Tento proces pomáhá zajistit, aby v počítačích koncových uživatelů nebyly nainstalovány neoprávněné soubory.  
  
 Dalším scénářem, kdy je možné znovu podepsat manifesty, je, že zákazníci chtějí podepsat aplikace a manifesty nasazení s vlastním certifikátem.  
  
## <a name="re-signing-the-application-and-deployment-manifests"></a>Opětovné podepisování manifestů aplikace a nasazení  
 Tento postup předpokládá, že jste již provedli změny v souboru manifestu aplikace (. manifest). Další informace najdete v tématu [Postupy: Změna vlastností nasazení](https://msdn.microsoft.com/66052a3a-8127-4964-8147-2477ef5d1472).  
  
#### <a name="to-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Opětovné podepsání manifestů aplikace a nasazení pomocí Mage.exe  
  
1. Otevřete okno **příkazového řádku sady Visual Studio** .  
  
2. Změňte adresář na složku, která obsahuje soubory manifestu, které chcete podepsat.  
  
3. Zadejte následující příkaz pro podepsání souboru manifestu aplikace. Nahraďte ManifestFileName názvem vašeho souboru manifestu a příponou. Nahraďte certifikát relativní nebo plně kvalifikovanou cestou k souboru certifikátu a heslo nahraďte heslem pro certifikát.  
  
    ```  
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Můžete například spustit následující příkaz pro podepsání manifestu aplikace pro doplněk, formulářovou aplikaci Windows nebo aplikace Windows Presentation Foundationho prohlížeče. Dočasné certifikáty vytvořené v aplikaci Visual Studio se nedoporučují pro nasazení do produkčních prostředí.  
  
    ```  
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
4. Zadejte následující příkaz, který aktualizuje a podepíše soubor manifestu nasazení a nahradí názvy zástupných symbolů jako v předchozím kroku.  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Můžete například spustit následující příkaz pro aktualizaci a podepsání manifestu nasazení pro doplněk aplikace Excel, aplikaci model Windows Forms nebo aplikaci Windows Presentation Foundation Browser.  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5. Volitelně můžete zkopírovat hlavní manifest nasazení (publikovat \\ *AppName*. Application) do adresáře nasazení verze (publish\Application Files \\ *AppName*_*verze*).  
  
## <a name="updating-and-re-signing-the-application-and-deployment-manifests"></a>Aktualizace a opětovné podepisování manifestů aplikace a nasazení  
 Tento postup předpokládá, že jste již provedli změny v souboru manifestu aplikace (. manifest), ale že existují i jiné soubory, které byly aktualizovány. Když se aktualizují soubory, musí se aktualizovat i hodnota hash, která představuje soubor.  
  
#### <a name="to-update-and-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Aktualizace a opětovné podepsání manifestů aplikace a nasazení pomocí Mage.exe  
  
1. Otevřete okno **příkazového řádku sady Visual Studio** .  
  
2. Změňte adresář na složku, která obsahuje soubory manifestu, které chcete podepsat.  
  
3. Odeberte příponu souboru. deploy ze souborů ve výstupní složce publikování.  
  
4. Zadejte následující příkaz, který aktualizuje manifest aplikace o nové hodnoty hash pro aktualizované soubory a podepíše soubor manifestu aplikace. Nahraďte ManifestFileName názvem vašeho souboru manifestu a příponou. Nahraďte certifikát relativní nebo plně kvalifikovanou cestou k souboru certifikátu a heslo nahraďte heslem pro certifikát.  
  
    ```  
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Můžete například spustit následující příkaz pro podepsání manifestu aplikace pro doplněk, formulářovou aplikaci Windows nebo aplikace Windows Presentation Foundationho prohlížeče. Dočasné certifikáty vytvořené v aplikaci Visual Studio se nedoporučují pro nasazení do produkčních prostředí.  
  
    ```  
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5. Zadejte následující příkaz, který aktualizuje a podepíše soubor manifestu nasazení a nahradí názvy zástupných symbolů jako v předchozím kroku.  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Můžete například spustit následující příkaz pro aktualizaci a podepsání manifestu nasazení pro doplněk aplikace Excel, aplikaci model Windows Forms nebo aplikaci Windows Presentation Foundation Browser.  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
6. Přidejte příponu souboru. deploy zpátky do souborů s výjimkou souborů manifestu aplikace a nasazení.  
  
7. Volitelně můžete zkopírovat hlavní manifest nasazení (publikovat \\ *AppName*. Application) do adresáře nasazení verze (publish\Application Files \\ *AppName*_*verze*).  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení aplikací ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Zabezpečení přístupu ke kódu pro aplikace ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce a Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Přehled nasazení důvěryhodných aplikací](../deployment/trusted-application-deployment-overview.md)   
 [Postupy: povolení nastavení zabezpečení ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Postupy: nastavení zóny zabezpečení pro aplikaci ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Postupy: nastavení vlastních oprávnění pro aplikaci ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Postupy: ladění aplikace ClickOnce s omezenými oprávněními](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Postupy: Přidání důvěryhodného vydavatele do klientského počítače pro aplikace ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [Postupy: Konfigurace chování výzvy důvěryhodnosti ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)
