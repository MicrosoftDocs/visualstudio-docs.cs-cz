---
title: Přidání důvěryhodného vydavatele do klientského počítače pro aplikace ClickOnce
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, install without prompting
- trusted application deployment, Trusted Publishers
ms.assetid: 35fe324c-45a1-4509-b7be-5c18b4b1b4ab
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1423952405a31063ee88ce6fa1dfe0b75d80fe5d
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649206"
---
# <a name="how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications"></a>Postup: Přidání důvěryhodného vydavatele do klientského počítače pro aplikace ClickOnce
Pomocí funkce Trusted Application Deployment můžete konfigurovat [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] klientské počítače tak, aby aplikace běžely s vyšší úrovní důvěryhodnosti bez zobrazení výzvy uživateli. Následující postupy ukazují, jak pomocí nástroje příkazového řádku CertMgr.exe přidat certifikát vydavatele do úložiště důvěryhodných vydavatelů v klientském počítači.

 Příkazy, které používáte, se mírně liší v závislosti na tom, zda certifikační autorita (CA), která certifikát vydala, je součástí důvěryhodného kořenového adresáře klienta. Pokud je klientský počítač se systémem Windows součástí domény, bude v seznamu obsahovat certifikační autority, které jsou považovány za důvěryhodné kořeny. Tento seznam je obvykle konfigurován správcem systému. Pokud byl certifikát vydán některou z těchto důvěryhodných kořenových adresářů nebo certifikačníautoritou, která se zřetězí s jedním z těchto důvěryhodných kořenových adresářů, můžete jej přidat do důvěryhodného kořenového úložiště klienta. Pokud na druhé straně váš certifikát nebyl vydán jedním z těchto důvěryhodných kořenových adresářů, je nutné přidat certifikát do úložiště důvěryhodného kořenového adresáře klienta i do úložiště důvěryhodných vydavatelů.

> [!NOTE]
> Certifikáty je nutné přidat tímto způsobem v každém [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] klientském počítači, do kterého plánujete nasadit aplikaci, která vyžaduje zvýšená oprávnění. Certifikáty přidáte ručně nebo prostřednictvím aplikace, kterou nasadíte svým klientům. Tyto počítače je třeba nakonfigurovat pouze jednou, po [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] kterém můžete nasadit libovolný počet aplikací podepsaných stejným certifikátem.

 Můžete také přidat certifikát do úložiště programově <xref:System.Security.Cryptography.X509Certificates.X509Store> pomocí třídy.

 Přehled nasazení důvěryhodných aplikací naleznete v tématu [Přehled nasazení důvěryhodných aplikací](../deployment/trusted-application-deployment-overview.md).

### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-the-trusted-root"></a>Přidání certifikátu do úložiště důvěryhodných vydavatelů pod důvěryhodným kořenem

1. Získejte digitální certifikát od certifikační autority.

2. Exportujte certifikát do formátu Base64 X.509 (*.cer).* Další informace o formátech certifikátů naleznete [v tématu Export certifikátu](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc730988(v=ws.10)).

3. Na příkazovém řádku v klientských počítačích spusťte následující příkaz:

     **certmgr.exe -přidat certificate.cer -c -s -r localMachine TrustedPublisher**

### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-a-different-root"></a>Přidání certifikátu do úložiště důvěryhodných vydavatelů pod jiným kořenem

1. Získejte digitální certifikát od certifikační autority.

2. Exportujte certifikát do formátu Base64 X.509 (*.cer).* Další informace o formátech certifikátů naleznete [v tématu Export certifikátu](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc730988(v=ws.10)).

3. Na příkazovém řádku v klientských počítačích spusťte následující příkaz:

     **certmgr.exe -přidat good.cer -c -s -r localMachine Root**

     **certmgr.exe -přidat good.cer -c -s -r localMachine TrustedPublisher**

## <a name="see-also"></a>Viz také
- [Návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
- [Zabezpečení aplikací ClickOnce](../deployment/securing-clickonce-applications.md)
- [Zabezpečení přístupu ke kódu pro aplikace ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
- [ClickOnce a kód Authenticode](../deployment/clickonce-and-authenticode.md)
- [Přehled nasazení důvěryhodných aplikací](../deployment/trusted-application-deployment-overview.md)
- [Postup: Povolení nastavení zabezpečení ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)
- [Postup: Nastavení zóny zabezpečení pro aplikaci ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Postup: Nastavení vlastních oprávnění pro aplikaci ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Postup: Ladění aplikace ClickOnce s omezenými oprávněními](securing-clickonce-applications.md)
- [Postup: Přidání důvěryhodného vydavatele do klientského počítače pro aplikace ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)
- [Postup: Opětovné podepsání manifestů aplikací a nasazení](../deployment/how-to-re-sign-application-and-deployment-manifests.md)
- [Postup: Konfigurace chování výzvy k důvěře ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)