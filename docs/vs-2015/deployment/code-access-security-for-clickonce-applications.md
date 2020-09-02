---
title: Zabezpečení přístupu ke kódu pro aplikace ClickOnce | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 54160bbdfe834a1b3226f4445b862c151bcf35c3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64782952"
---
# <a name="code-access-security-for-clickonce-applications"></a>Zabezpečení přístupu ke kódu pro aplikace ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aplikace ClickOnce jsou založené na .NET Framework a podléhají omezením zabezpečení přístupu kódu. Z tohoto důvodu je důležité pochopit důsledky zabezpečení přístupu kódu a zapsat aplikace ClickOnce odpovídajícím způsobem.  
  
 Zabezpečení přístupu kódu je mechanismus v .NET Framework, který pomáhá omezit přístup kódu k chráněným prostředkům a operacím. Měli byste nakonfigurovat oprávnění zabezpečení přístupu kódu pro aplikaci ClickOnce tak, aby používala zónu vhodnou pro umístění instalačního programu aplikace. Ve většině případů můžete zvolit **internetovou** zónu pro omezená sadu oprávnění nebo zónu **místního intranetu** pro větší sadu oprávnění.  
  
## <a name="default-clickonce-code-access-security"></a>Výchozí zabezpečení přístupu kódu ClickOnce  
 Ve výchozím nastavení aplikace ClickOnce obdrží plná oprávnění důvěryhodnosti při instalaci nebo spuštění v klientském počítači.  
  
- Aplikace s úplnými oprávněními důvěryhodnosti má neomezený přístup k prostředkům, jako je třeba systém souborů a registr. To potenciálně umožňuje zneužití vaší aplikace (a systému koncového uživatele) škodlivým kódem.  
  
- Když aplikace vyžaduje plná oprávnění důvěryhodnosti, může se koncovému uživateli zobrazit výzva k udělení oprávnění k aplikaci. To znamená, že aplikace ještě neposkytuje prostředí ClickOnce a výzva může být matoucí pro méně zkušené uživatele.  
  
  > [!NOTE]
  > Při instalaci aplikace z vyměnitelných médií, jako je například disk CD-ROM, se uživateli nezobrazí výzva. Kromě toho může správce sítě nakonfigurovat zásady sítě tak, aby se uživatelům při instalaci aplikace z důvěryhodného zdroje nezobrazovaly žádné výzvy. Další informace najdete v tématu [Přehled nasazení důvěryhodných aplikací](../deployment/trusted-application-deployment-overview.md).  
  
  Chcete-li omezit oprávnění pro aplikaci ClickOnce, můžete upravit oprávnění zabezpečení přístupu kódu pro vaši aplikaci a požádat o zónu, která nejlépe odpovídá oprávněním, která vaše aplikace vyžaduje. Ve většině případů můžete vybrat zónu, ze které se aplikace nasazuje. Pokud je vaše aplikace například podniková aplikace, můžete použít zónu **místního intranetu** . Pokud je vaše aplikace internetovou aplikací, můžete použít **internetovou** zónu.  
  
## <a name="configuring-security-permissions"></a>Konfigurace oprávnění zabezpečení  
 Aplikaci ClickOnce byste měli vždycky nakonfigurovat tak, aby požadovala příslušnou zónu pro omezení oprávnění zabezpečení přístupu kódu. Oprávnění zabezpečení můžete nakonfigurovat na stránce **zabezpečení** **Návrháře projektu**.  
  
 Stránka **zabezpečení** v **Návrháři projektu** obsahuje zaškrtávací políčko **Povolit nastavení zabezpečení ClickOnce** . Pokud je toto políčko zaškrtnuto, do manifestu nasazení aplikace jsou přidány požadavky oprávnění zabezpečení. V době instalace bude uživatel vyzván k udělení oprávnění, pokud požadovaná oprávnění překročí výchozí oprávnění pro zónu, ze které je aplikace nasazena. Další informace najdete v tématu [Postup: povolení nastavení zabezpečení ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md).  
  
 Aplikacím nasazeným z různých umístění jsou udělena různé úrovně oprávnění bez zobrazení výzvy. Například při nasazení aplikace z Internetu obdrží vysoce omezující sadu oprávnění. Při instalaci z místního intranetu obdrží více oprávnění a při instalaci z disku CD-ROM obdrží oprávnění s úplným vztahem důvěryhodnosti.  
  
 Jako výchozí bod pro konfiguraci oprávnění můžete vybrat zónu zabezpečení ze seznamu **zón** na stránce **zabezpečení** . Pokud bude aplikace potenciálně nasazena z více než jedné zóny, vyberte zónu s nejnižšími oprávněními. Další informace najdete v tématu [Postupy: nastavení zóny zabezpečení pro aplikaci ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md).  
  
 Vlastnosti, které lze nastavit, se liší podle sady oprávnění; Ne všechny sady oprávnění mají konfigurovatelné vlastnosti. Další informace o úplném seznamu oprávnění, která vaše aplikace může požadovat, najdete v tématu <xref:System.Security.Permissions> . Další informace o tom, jak nastavit oprávnění pro vlastní zónu, najdete v tématu [Postupy: nastavení vlastních oprávnění pro aplikaci ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).  
  
## <a name="debugging-an-application-that-has-restricted-permissions"></a>Ladění aplikace, která má omezená oprávnění  
 Jako vývojář pravděpodobně spustíte vývojový počítač s úplnými oprávněními důvěryhodnosti. Proto se při ladění aplikace, které mohou uživatelé zobrazit při spuštění s omezenými oprávněními, nezobrazuje stejné výjimky zabezpečení.  
  
 Aby bylo možné tyto výjimky zachytit, je nutné ladit aplikaci se stejnými oprávněními jako koncový uživatel. Ladění s omezenými oprávněními lze povolit na stránce **zabezpečení** **Návrháře projektu**.  
  
 Při ladění aplikace s omezenými oprávněními budou výjimky vyvolány pro všechny požadavky zabezpečení kódu, které nebyly na stránce **zabezpečení** povoleny. Zobrazí se Pomocník s výjimkou, který poskytuje návrhy na úpravu kódu, aby se zabránilo výjimce.  
  
 Kromě toho při psaní kódu funkce technologie IntelliSense v editoru kódu zakáže všechny členy, kteří nejsou součástí oprávnění zabezpečení, která jste nakonfigurovali.  
  
 Další informace naleznete v tématu [How to: Debug a aplikace ClickOnce s omezenými oprávněními](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md).  
  
## <a name="security-permissions-for-browser-hosted-applications"></a>Oprávnění zabezpečení pro aplikace hostované v prohlížeči  
 Visual Studio poskytuje následující typy projektů pro aplikace Windows Presentation Foundation (WPF):  
  
- WPF – aplikace systému Windows  
  
- Aplikace webového prohlížeče WPF  
  
- Knihovna vlastních ovládacích prvků WPF  
  
- Knihovna služby WPF  
  
  Z těchto typů projektů jsou hostovány pouze aplikace webového prohlížeče WPF ve webovém prohlížeči, a proto vyžadují speciální nastavení nasazení a zabezpečení. Výchozí nastavení zabezpečení pro tyto aplikace jsou následující:  
  
- **Povolit nastavení zabezpečení ClickOnce**  
  
- **Toto je aplikace s částečnou důvěryhodností.**  
  
- **Zóna Internetu** (se zvolenou výchozí sadou oprávnění pro aplikace webového prohlížeče WPF)  
  
  V dialogovém okně **Upřesnit nastavení zabezpečení** je zaškrtnuté políčko **Ladit tuto aplikaci s vybranou sadou oprávnění** a je zakázaná. Důvodem je to, že ladění v zóně nelze vypnout pro aplikace hostované v prohlížeči.  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení aplikací ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Postupy: povolení nastavení zabezpečení ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Postupy: nastavení zóny zabezpečení pro aplikaci ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Postupy: nastavení vlastních oprávnění pro aplikaci ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Postupy: ladění aplikace ClickOnce s omezenými oprávněními](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Přehled nasazení důvěryhodných aplikací](../deployment/trusted-application-deployment-overview.md)   
 [Stránka Zabezpečení, návrhář projektu](../ide/reference/security-page-project-designer.md)
