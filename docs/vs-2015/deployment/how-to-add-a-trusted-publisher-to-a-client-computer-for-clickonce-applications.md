---
title: 'Postupy: Přidání důvěryhodného vydavatele do klientského počítače pro aplikace ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, install without prompting
- trusted application deployment, Trusted Publishers
ms.assetid: 35fe324c-45a1-4509-b7be-5c18b4b1b4ab
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 296aec3b2b5cd307400b230375a7171f158fee60
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75847699"
---
# <a name="how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications"></a>Postupy: Přidání důvěryhodného vydavatele na klientskou stanici pro aplikace ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při nasazení důvěryhodných aplikací můžete nakonfigurovat klientské počítače tak, aby vaše aplikace [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] běžely s vyšší úrovní důvěryhodnosti bez zobrazení výzvy uživateli. Následující postupy ukazují, jak pomocí nástroje příkazového řádku CertMgr. exe přidat certifikát vydavatele do úložiště důvěryhodných vydavatelů v klientském počítači.  
  
 Příkazy, které použijete, se mírně liší v závislosti na tom, jestli certifikační autorita (CA), která certifikát vystavila, je součástí důvěryhodného kořenového certifikátu klienta. Pokud je klientský počítač se systémem Windows součástí domény, bude obsahovat v seznamu certifikační autority, které jsou považovány za důvěryhodné kořenové adresáře. Tento seznam je obvykle nakonfigurovaný správcem systému. Pokud certifikát vystavila jedna z těchto důvěryhodných kořenových adresářů nebo certifikační autorita, která je zřetězena s jednou z těchto důvěryhodných kořenových adresářů, můžete certifikát přidat do důvěryhodného kořenového úložiště klienta. Pokud na druhé straně váš certifikát nevydala jedna z těchto důvěryhodných kořenových adresářů, musíte certifikát přidat do důvěryhodného kořenového úložiště klienta i do úložiště důvěryhodných vydavatelů.  
  
> [!NOTE]
> Certifikáty je třeba přidat na každý klientský počítač, do kterého plánujete nasadit aplikaci [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], která vyžaduje zvýšená oprávnění. Certifikáty přidáte buď ručně, nebo prostřednictvím aplikace, kterou nasadíte do klientů. Tyto počítače je třeba nakonfigurovat pouze jednou, a poté můžete nasadit libovolný počet aplikací [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] podepsaných stejným certifikátem.  
  
 Do úložiště můžete také přidat certifikát programově pomocí třídy <xref:System.Security.Cryptography.X509Certificates.X509Store>.  
  
 Přehled nasazení důvěryhodných aplikací najdete v tématu [Přehled nasazení důvěryhodných aplikací](../deployment/trusted-application-deployment-overview.md).  
  
### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-the-trusted-root"></a>Přidání certifikátu do úložiště důvěryhodných vydavatelů pod důvěryhodným kořenovým adresářem  
  
1. Získejte digitální certifikát od certifikační autority.  
  
2. Exportujte certifikát do formátu Base64 X. 509 (. cer). Další informace o formátech certifikátů najdete v tématu [Export certifikátu](https://technet.microsoft.com/library/cc730988(WS.10).aspx).  
  
3. Z příkazového řádku v klientských počítačích spusťte následující příkaz:  
  
     **certmgr.exe -add certificate.cer -c -s -r localMachine TrustedPublisher**  
  
### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-a-different-root"></a>Přidání certifikátu do úložiště důvěryhodných vydavatelů pod jiným kořenem  
  
1. Získejte digitální certifikát od certifikační autority.  
  
2. Exportujte certifikát do formátu Base64 X. 509 (. cer). Další informace o formátech certifikátů najdete v tématu [Export certifikátu](https://technet.microsoft.com/library/cc730988(WS.10).aspx).  
  
3. Z příkazového řádku v klientských počítačích spusťte následující příkaz:  
  
     **certmgr.exe -add good.cer -c -s -r localMachine Root**  
  
     **certmgr.exe -add good.cer -c -s -r localMachine TrustedPublisher**  
  
## <a name="see-also"></a>Viz také  
 [Návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [Zabezpečení aplikací ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Zabezpečení přístupu ke kódu pro aplikace ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce a  Authenticode](../deployment/clickonce-and-authenticode.md)  
 [Přehled nasazení důvěryhodných aplikací](../deployment/trusted-application-deployment-overview.md)   
 [Postupy: povolení nastavení zabezpečení ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Postupy: nastavení zóny zabezpečení pro aplikaci ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Postupy: nastavení vlastních oprávnění pro aplikaci ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Postupy: ladění aplikace ClickOnce s omezenými oprávněními](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Postupy: Přidání důvěryhodného vydavatele do klientského počítače pro aplikace ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [Postupy: Opětovné podepsání manifestů aplikace a nasazení](../deployment/how-to-re-sign-application-and-deployment-manifests.md)   
 [Postupy: Konfigurace chování výzvy důvěryhodnosti ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)
