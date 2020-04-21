---
title: 'Postup: Znovu podepsat manifesty aplikací a nasazení | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fc69ce1f79644d7f4b35fbb1c1e3a41691761390
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649189"
---
# <a name="how-to-re-sign-application-and-deployment-manifests"></a>Postup: Opětovné podepsání manifestů aplikací a nasazení
Po provedení změn vlastností nasazení v manifestu aplikace pro aplikace systému Windows Forms, aplikace Windows Presentation Foundation (xbap) nebo řešení sady Office je nutné znovu podepsat manifesty aplikace i nasazení pomocí certifikátu. Tento proces pomáhá zajistit, že nenainstalované soubory nebudou nainstalovány v počítačích koncových uživatelů.

 Dalším scénářem, kde můžete znovu podepsat manifesty je, když vaši zákazníci chtějí podepsat manifesty aplikace a nasazení pomocí vlastního certifikátu.

## <a name="re-sign-the-application-and-deployment-manifests"></a>Opětovné podepsání manifestů aplikace a nasazení
 Tento postup předpokládá, že jste již provedli změny v souboru manifestu aplikace (*.manifest*). Další informace naleznete v [tématu Postup: Změna vlastností nasazení](https://msdn.microsoft.com/library/66052a3a-8127-4964-8147-2477ef5d1472).

#### <a name="to-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Opětovné podepsání manifestů aplikace a nasazení pomocí souboru Mage.exe

1. Otevřete okno **příkazového řádku sady Visual Studio.**

2. Změňte adresáře na složku obsahující soubory manifestu, které chcete podepsat.

3. Zadejte následující příkaz pro podepsání souboru manifestu aplikace. Nahradit *ManifestFileName* s názvem souboru manifestu plus příponu. Nahraďte *certifikát* relativní nebo plně kvalifikovanou cestou souboru certifikátu a nahraďte *heslo* pro certifikát.

    ```cmd
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password
    ```

     Můžete například spustit následující příkaz k podepsání manifestu aplikace pro doplněk, aplikaci Windows Form nebo aplikaci prohlížeče Windows Presentation Foundation. Dočasné certifikáty vytvořené aplikací Visual Studio se nedoporučují pro nasazení do produkčního prostředí.

    ```cmd
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

4. Zadejte následující příkaz pro aktualizaci a podepsání souboru manifestu nasazení a nahrazte zástupné názvy jako v předchozím kroku.

    ```cmd
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password
    ```

     Můžete například spustit následující příkaz k aktualizaci a podepsání manifestu nasazení pro doplněk aplikace Aplikace Excel, aplikaci Windows Forms nebo aplikaci prohlížeče Windows Presentation Foundation.

    ```cmd
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

5. Volitelně můžete zkopírovat manifest hlavního nasazení (*publikovat\\\<název aplikace>.application*) do adresáře pro nasazení verze (*publish\Application\\\<Files název aplikace\<>_ verze>*).

## <a name="update-and-re-sign-the-application-and-deployment-manifests"></a>Aktualizace a opětovné podepsání manifestů aplikace a nasazení
 Tento postup předpokládá, že jste již provedli změny v souboru manifestu aplikace (*.manifest*), ale že existují další soubory, které byly aktualizovány. Při aktualizaci souborů musí být aktualizována také hash, která soubor představuje.

#### <a name="to-update-and-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Aktualizace a opětovné podepsání manifestů aplikace a nasazení pomocí programu Mage.exe

1. Otevřete okno **příkazového řádku sady Visual Studio.**

2. Změňte adresáře na složku obsahující soubory manifestu, které chcete podepsat.

3. Odeberte příponu *.deploy* ze souborů ve výstupní složce publikování.

4. Zadejte následující příkaz pro aktualizaci manifestu aplikace novými hashy pro aktualizované soubory a podepište soubor manifestu aplikace. Nahradit *ManifestFileName* s názvem souboru manifestu plus příponu. Nahraďte *certifikát* relativní nebo plně kvalifikovanou cestou souboru certifikátu a nahraďte *heslo* pro certifikát.

    ```cmd
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password
    ```

     Můžete například spustit následující příkaz k podepsání manifestu aplikace pro doplněk, aplikaci Windows Form nebo aplikaci prohlížeče Windows Presentation Foundation. Dočasné certifikáty vytvořené aplikací Visual Studio se nedoporučují pro nasazení do produkčního prostředí.

    ```cmd
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

5. Zadejte následující příkaz pro aktualizaci a podepsání souboru manifestu nasazení a nahrazte zástupné názvy jako v předchozím kroku.

    ```cmd
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password
    ```

     Můžete například spustit následující příkaz k aktualizaci a podepsání manifestu nasazení pro doplněk aplikace Aplikace Excel, aplikaci Windows Forms nebo aplikaci prohlížeče Windows Presentation Foundation.

    ```cmd
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

6. Přidejte příponu *.deploy* file back do souborů, s výjimkou souborů manifestu aplikace a nasazení.

7. Volitelně můžete zkopírovat manifest hlavního nasazení (*publikovat\\\<název aplikace>.application*) do adresáře pro nasazení verze (*publish\Application\\\<Files název aplikace\<>_ verze>*).

## <a name="see-also"></a>Viz také
- [Zabezpečení aplikací ClickOnce](../deployment/securing-clickonce-applications.md)
- [Zabezpečení přístupu ke kódu pro aplikace ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
- [ClickOnce a kód Authenticode](../deployment/clickonce-and-authenticode.md)
- [Přehled nasazení důvěryhodných aplikací](../deployment/trusted-application-deployment-overview.md)
- [Postup: Povolení nastavení zabezpečení ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)
- [Postup: Nastavení zóny zabezpečení pro aplikaci ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Postup: Nastavení vlastních oprávnění pro aplikaci ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Postup: Ladění aplikace ClickOnce s omezenými oprávněními](securing-clickonce-applications.md)
- [Postup: Přidání důvěryhodného vydavatele do klientského počítače pro aplikace ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)
- [Postup: Konfigurace chování výzvy k důvěře ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)