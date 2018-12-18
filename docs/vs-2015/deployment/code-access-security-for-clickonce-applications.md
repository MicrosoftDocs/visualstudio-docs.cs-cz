---
title: Zabezpečení přístupu ke kódu pro aplikace ClickOnce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vb.XBAPProjectPropertiesSecurity.HowTo
- vb.XBAProjectPropertiesSecurity.HowTo
- vb.ProjectPropertiesSecurity.HowTo
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], security
- ClickOnce applications, caspol
- security [ClickOnce], WPF browser-hosted applications
- security [ClickOnce], ClickOnce applications
- ClickOnce applications, code access security policies
- security, ClickOnce
ms.assetid: 04b104d0-0bd3-4ccb-b164-1de92d234487
caps.latest.revision: 33
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: ea1f91a50180dce6edec17afead5649ecd3e1f50
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49816063"
---
# <a name="code-access-security-for-clickonce-applications"></a>Zabezpečení přístupu ke kódu pro aplikace ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aplikace ClickOnce jsou založeny na rozhraní .NET Framework a jsou v souladu s omezením zabezpečení přístupu kódu. Z tohoto důvodu je důležité, že rozumíte důsledkům kód přistupovat k zabezpečení a zapisovat vaše aplikace ClickOnce odpovídajícím způsobem.  
  
 Zabezpečení přístupu kódu je mechanismus v rozhraní .NET Framework, která pomáhá omezit přístup, který má kód k chráněným prostředkům a operacím. Měli byste nakonfigurovat oprávnění zabezpečení přístupu kódu pro aplikace ClickOnce použije oblasti, které jsou vhodné pro umístění instalačním programem aplikace. Ve většině případů můžete použít **Internet** zónu pro omezenou sadu oprávnění nebo **místní Intranet** zónu pro větší sadu oprávnění.  
  
## <a name="default-clickonce-code-access-security"></a>Zabezpečení přístupu kódu ClickOnce výchozí  
 Ve výchozím nastavení aplikace ClickOnce obdrží oprávnění plné důvěryhodnosti při instalaci nebo spuštění na klientském počítači.  
  
- Aplikace, který má oprávnění plné důvěryhodnosti má neomezený přístup k prostředkům, jako je například systém souborů a registru. To umožňuje potenciálně aplikaci (a koncový uživatel systému) zneužití škodlivým kódem.  
  
- Pokud aplikace vyžaduje oprávnění plné důvěryhodnosti, koncový uživatel může zobrazit výzva k udělení oprávnění k aplikaci. To znamená, že aplikace neposkytuje skutečně ClickOnce prostředí a na řádku může být potenciálně matoucí pro méně zkušených uživatelů.  
  
  > [!NOTE]
  >  Při instalaci aplikace z vyměnitelných médií, jako je například disk CD-ROM, uživatel není vyzván. Kromě toho správce sítě můžete nakonfigurovat zásady sítě tak, aby se uživatelům nebude výzva při instalaci aplikace z důvěryhodného zdroje. Další informace najdete v tématu [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
  Pokud chcete omezit oprávnění pro aplikaci ClickOnce, můžete upravit oprávnění zabezpečení přístupu kódu pro vaši aplikaci na vyžádání, která nejlíp odpovídá oprávnění, která vaše aplikace vyžaduje zóny. Ve většině případů vyberete zónu, ze kterého je aplikace nasazena. Například pokud vaše aplikace je podniková aplikace, můžete použít **místní Intranet** zóny. Pokud je vaše aplikace internetovou aplikaci, můžete použít **Internet** zóny.  
  
## <a name="configuring-security-permissions"></a>Konfigurace oprávnění zabezpečení  
 Vždy byste měli konfigurovat vaše aplikace ClickOnce k vyžádání příslušnou zónu omezit oprávnění zabezpečení přístupu kódu. Můžete nakonfigurovat oprávnění zabezpečení na **zabezpečení** stránku **Návrháře projektu**.  
  
 **Zabezpečení** stránku **Návrháře projektu** obsahuje **povolit nastavení zabezpečení ClickOnce** zaškrtávací políčko. Když je toto políčko zaškrtnuto, požadavky na oprávnění zabezpečení se přidají do manifestu nasazení pro vaši aplikaci. Během instalace bude uživatel vyzván k udělení oprávnění, pokud se požadovaná oprávnění překročit výchozí oprávnění pro zónu, ze kterého je aplikace nasazená. Další informace najdete v tématu [postupy: povolení nastavení zabezpečení ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md).  
  
 Aplikace nasazené z různých míst jsou udělena různé úrovně oprávnění bez zobrazení výzvy. Například když je aplikace nasazená z Internetu, obdrží vysoce omezující sadu oprávnění. Při instalaci z místní Intranet, obdrží další oprávnění a při instalaci z disku CD-ROM, obdrží oprávnění plné důvěryhodnosti.  
  
 Jako výchozí bod pro konfiguraci oprávnění, můžete vybrat ze zóny zabezpečení **zóny** seznamu **zabezpečení** stránky. Pokud vaše aplikace bude nasazena potenciálně z více než jednu zónu, vyberte zónu s nejnižšími oprávněními. Další informace najdete v tématu [postupy: nastavení zóny zabezpečení pro aplikaci ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md).  
  
 Vlastnosti, které je možné nastavit se liší podle sada oprávnění; Ne všechny sady oprávnění má konfigurovatelné vlastnosti. Další informace o úplný seznam oprávnění, která aplikace může požadovat najdete v tématu <xref:System.Security.Permissions>. Další informace o tom, jak nastavit oprávnění pro vlastní zónu, naleznete v tématu [postupy: nastavení vlastních oprávnění pro aplikaci ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).  
  
## <a name="debugging-an-application-that-has-restricted-permissions"></a>Ladění aplikace, který má omezená oprávnění  
 Jako vývojář pravděpodobně spuštění vývojového počítače pomocí oprávnění plné důvěryhodnosti. Proto se nezobrazí stejné zabezpečení výjimky při ladění aplikace, které uživatelé mohou vidět, když použijí ho s omezenými oprávněními.  
  
 Aby bylo možné zachytit tyto výjimky, je třeba ladit aplikaci stejná oprávnění jako koncový uživatel. Ladění s omezenými oprávněními může být povoleno na **zabezpečení** stránku **Návrháře projektu**.  
  
 Při ladění aplikace s omezenými oprávněními, se pro všechny požadavky zabezpečení kódu, které nebyly byla zapnuta vyvolané výjimky **zabezpečení** stránky. Zobrazí se pomocníka výjimky, poskytuje návrhy o tom, jak upravit kód pro zabránění výjimce.  
  
 Kromě toho při psaní kódu, funkci IntelliSense v editoru kódu zakáže všechny členy, které nejsou součástí oprávnění zabezpečení, které jste nakonfigurovali.  
  
 Další informace najdete v tématu [postupy: ladění aplikace ClickOnce s omezenými oprávněními](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md).  
  
## <a name="security-permissions-for-browser-hosted-applications"></a>Oprávnění zabezpečení pro aplikace hostované prohlížečem  
 Visual Studio poskytuje následující typy projektů pro aplikace Windows Presentation Foundation (WPF):  
  
- Aplikace WPF Windows  
  
- Aplikace WPF webového prohlížeče  
  
- Knihovna vlastních ovládacích prvků WPF  
  
- Knihovna služby WPF  
  
  Tyto typy projektů pouze aplikace WPF webového prohlížeče jsou hostované ve webovém prohlížeči a proto vyžaduje speciální nasazení a nastavení zabezpečení. Výchozí nastavení zabezpečení pro tyto aplikace jsou následující:  
  
- **Povolení nastavení zabezpečení ClickOnce**  
  
- **Toto je aplikace s částečnou důvěryhodností**  
  
- **Zóna Internetu** (s výchozí sady oprávnění pro aplikace WPF webového prohlížeče vybrané)  
  
  V **Upřesnit nastavení zabezpečení** dialogové okno, **Ladit tuto aplikaci s vybranou sadou oprávnění** zaškrtávací políčko je vybraná a zakázaná. Je to proto nejde ji vypnout ladění v zóně pro aplikace hostované prohlížečem.  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečování aplikací ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Postupy: povolení nastavení zabezpečení ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Postupy: nastavení zóny zabezpečení pro aplikaci ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Postupy: nastavení vlastních oprávnění pro aplikaci ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Postupy: ladění aplikace ClickOnce s omezenými oprávněními](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Přehled nasazení důvěryhodných aplikací](../deployment/trusted-application-deployment-overview.md)   
 [Stránka Zabezpečení, Návrhář projektu](../ide/reference/security-page-project-designer.md)



