---
title: Přidat důvěryhodného vydavatele do klientského pole (ClickOnce)
description: Naučte se, jak přidat certifikát do klientského počítače tak, aby vaše aplikace ClickOnce běžely na vyšší úrovni důvěryhodnosti bez zobrazení výzvy uživateli.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c04b8d700d7739f0e4ef1fba259aab0595cea28c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947811"
---
# <a name="how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications"></a>Postupy: Přidání důvěryhodného vydavatele do klientského počítače pro aplikace ClickOnce
Při nasazení důvěryhodných aplikací můžete nakonfigurovat klientské počítače tak, aby [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace běžely s vyšší úrovní důvěryhodnosti bez zobrazení výzvy uživateli. Následující postupy ukazují, jak pomocí nástroje příkazového řádku CertMgr.exe přidat certifikát vydavatele do úložiště důvěryhodných vydavatelů v klientském počítači.

 Příkazy, které použijete, se mírně liší v závislosti na tom, jestli certifikační autorita (CA), která certifikát vystavila, je součástí důvěryhodného kořenového certifikátu klienta. Pokud je klientský počítač se systémem Windows součástí domény, bude obsahovat v seznamu certifikační autority, které jsou považovány za důvěryhodné kořenové adresáře. Tento seznam je obvykle nakonfigurovaný správcem systému. Pokud certifikát vystavila jedna z těchto důvěryhodných kořenových adresářů nebo certifikační autorita, která je zřetězena s jednou z těchto důvěryhodných kořenových adresářů, můžete certifikát přidat do důvěryhodného kořenového úložiště klienta. Pokud na druhé straně váš certifikát nevydala jedna z těchto důvěryhodných kořenových adresářů, musíte certifikát přidat do důvěryhodného kořenového úložiště klienta i do úložiště důvěryhodných vydavatelů.

> [!NOTE]
> Certifikáty je třeba přidat na každý klientský počítač, do kterého plánujete nasadit [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikaci, která vyžaduje zvýšená oprávnění. Certifikáty přidáte buď ručně, nebo prostřednictvím aplikace, kterou nasadíte do klientů. Tyto počítače je třeba nakonfigurovat pouze jednou, a poté můžete nasadit libovolný počet [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikací podepsaný se stejným certifikátem.

 Do úložiště můžete také přidat certifikát programově pomocí <xref:System.Security.Cryptography.X509Certificates.X509Store> třídy.

 Přehled nasazení důvěryhodných aplikací najdete v tématu [Přehled nasazení důvěryhodných aplikací](../deployment/trusted-application-deployment-overview.md).

### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-the-trusted-root"></a>Přidání certifikátu do úložiště důvěryhodných vydavatelů pod důvěryhodným kořenovým adresářem

1. Získejte digitální certifikát od certifikační autority.

2. Exportujte certifikát do formátu Base64 X. 509 (*. cer*). Další informace o formátech certifikátů najdete v tématu [Export certifikátu](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc730988(v=ws.10)).

3. Z příkazového řádku v klientských počítačích spusťte následující příkaz:

     **certmgr.exe – přidání certifikátu. cer-c-s-r localMachine TrustedPublisher**

### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-a-different-root"></a>Přidání certifikátu do úložiště důvěryhodných vydavatelů pod jiným kořenem

1. Získejte digitální certifikát od certifikační autority.

2. Exportujte certifikát do formátu Base64 X. 509 (*. cer*). Další informace o formátech certifikátů najdete v tématu [Export certifikátu](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc730988(v=ws.10)).

3. Z příkazového řádku v klientských počítačích spusťte následující příkaz:

     **certmgr.exe – přidat dobrý. cer-c-s-r localMachine root**

     **certmgr.exe – přidat dobrý. cer-c-s-r localMachine TrustedPublisher**

## <a name="see-also"></a>Viz také
- [Návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
- [Zabezpečení aplikací ClickOnce](../deployment/securing-clickonce-applications.md)
- [Zabezpečení přístupu ke kódu pro aplikace ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
- [ClickOnce a kód Authenticode](../deployment/clickonce-and-authenticode.md)
- [Přehled nasazení důvěryhodných aplikací](../deployment/trusted-application-deployment-overview.md)
- [Postupy: povolení nastavení zabezpečení ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)
- [Postupy: nastavení zóny zabezpečení pro aplikaci ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Postupy: nastavení vlastních oprávnění pro aplikaci ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Postupy: ladění aplikace ClickOnce s omezenými oprávněními](securing-clickonce-applications.md)
- [Postupy: Přidání důvěryhodného vydavatele do klientského počítače pro aplikace ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)
- [Postupy: Opětovné podepsání manifestů aplikace a nasazení](../deployment/how-to-re-sign-application-and-deployment-manifests.md)
- [Postupy: Konfigurace chování výzvy důvěryhodnosti ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)