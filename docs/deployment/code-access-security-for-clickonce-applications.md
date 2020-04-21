---
title: Zabezpečení přístupu kódu pro aplikace ClickOnce | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9fd2d9b6792cae002967c9000474a825bd3a0651
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649282"
---
# <a name="code-access-security-for-clickonce-applications"></a>Zabezpečení přístupu ke kódu pro aplikace ClickOnce
Aplikace ClickOnce jsou založeny na rozhraní .NET Framework a podléhají omezením zabezpečení přístupu kódu. Z tohoto důvodu je důležité, abyste pochopili důsledky zabezpečení přístupu kódu a odpovídajícím způsobem napište aplikace ClickOnce.

 Zabezpečení přístupu kódu je mechanismus v rozhraní .NET Framework, který pomáhá omezit přístup, který má kód k chráněným prostředkům a operacím. Měli byste nakonfigurovat oprávnění zabezpečení přístupu kódu pro vaši aplikaci ClickOnce tak, aby používala zónu vhodnou pro umístění instalačního programu aplikace. Ve většině případů můžete zvolit zónu **Internet** pro omezenou sadu oprávnění nebo zónu **Místní intranet** pro větší sadu oprávnění.

## <a name="default-clickonce-code-access-security"></a>Výchozí zabezpečení přístupu kódu ClickOnce
 Ve výchozím nastavení aplikace ClickOnce obdrží oprávnění úplné důvěryhodnosti při instalaci nebo spuštění v klientském počítači.

- Aplikace, která má oprávnění úplné důvěryhodnosti, má neomezený přístup k prostředkům, jako je například systém souborů a registr. To potenciálně umožňuje, aby vaše aplikace (a systém koncového uživatele) byly zneužity škodlivým kódem.

- Pokud aplikace vyžaduje oprávnění úplné důvěryhodnosti, může být koncový uživatel vyzván k udělení oprávnění k aplikaci. To znamená, že aplikace není skutečně poskytují ClickOnce zkušenosti a výzva může být potenciálně matoucí pro méně zkušené uživatele.

  > [!NOTE]
  > Při instalaci aplikace z vyměnitelného média, jako je například disk CD-ROM, není uživatel vyzván. Kromě toho může správce sítě nakonfigurovat zásady sítě tak, aby uživatelé nebyli při instalaci aplikace z důvěryhodného zdroje vyzváni. Další informace naleznete v tématu [Přehled nasazení důvěryhodných aplikací](../deployment/trusted-application-deployment-overview.md).

  Chcete-li omezit oprávnění pro aplikaci ClickOnce, můžete upravit oprávnění zabezpečení přístupu kódu pro vaši aplikaci a požádat o zónu, která nejlépe vyhovuje oprávněním, která vaše aplikace vyžaduje. Ve většině případů můžete vybrat zónu, ze které je aplikace nasazována. Pokud je například vaše aplikace podnikovou aplikací, můžete použít zónu **Místní intranet.** Pokud je vaše aplikace internetová aplikace, můžete použít **zónu Internet.**

## <a name="configure-security-permissions"></a>Konfigurace oprávnění zabezpečení
 Vždy byste měli nakonfigurovat aplikaci ClickOnce tak, aby požadovala příslušnou zónu pro omezení oprávnění zabezpečení přístupu kódu. Oprávnění zabezpečení můžete nakonfigurovat na stránce **Zabezpečení** **návrháře projektu**.

 Stránka **Zabezpečení** v **Návrháři projektu** obsahuje zaškrtávací políčko **Povolit nastavení zabezpečení Po kliknutíOnce.** Pokud je toto políčko zaškrtnuto, požadavky na oprávnění zabezpečení jsou přidány do manifestu nasazení pro vaši aplikaci. V době instalace bude uživatel vyzván k udělení oprávnění, pokud požadovaná oprávnění překročí výchozí oprávnění pro zónu, ze které je aplikace nasazena. Další informace naleznete v [tématu How to: Enable ClickOnce security settings](../deployment/how-to-enable-clickonce-security-settings.md).

 Aplikacím nasazeným z různých umístění jsou uděleny různé úrovně oprávnění bez zobrazení výzvy. Například při nasazení aplikace z Internetu obdrží vysoce omezující sadu oprávnění. Při instalaci z místního intranetu získá více oprávnění a při instalaci z disku CD-ROM získá oprávnění úplné důvěryhodnosti.

 Jako výchozí bod pro konfiguraci oprávnění můžete vybrat zónu zabezpečení ze seznamu **Zóna** na stránce **Zabezpečení.** Pokud vaše aplikace bude potenciálně nasazena z více než jedné zóny, vyberte zónu s nejmenšími oprávněními. Další informace naleznete v [tématu Postup: Nastavení zóny zabezpečení pro aplikaci ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md).

 Vlastnosti, které lze nastavit, se liší podle sady oprávnění; ne všechny sady oprávnění mají konfigurovatelné vlastnosti. Další informace o úplném seznamu oprávnění, která <xref:System.Security.Permissions>může vaše aplikace požadovat, naleznete v tématu . Další informace o nastavení oprávnění pro vlastní zónu naleznete v tématu [Postup: Nastavení vlastních oprávnění pro aplikaci ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).

## <a name="debug-an-application-that-has-restricted-permissions"></a>Ladění aplikace s omezenými oprávněními
 Jako vývojář s největší pravděpodobností spustíte vývojový počítač s oprávněními úplné důvěryhodnosti. Proto se nezobrazí stejné výjimky zabezpečení při ladění aplikace, které mohou uživatelé zobrazit při spuštění s omezenými oprávněními.

 Chcete-li zachytit tyto výjimky, musíte ladit aplikaci se stejnými oprávněními jako koncový uživatel. Ladění s omezenými oprávněními lze povolit na stránce **Zabezpečení** **Návrháře projektu**.

 Při ladění aplikace s omezenými oprávněními budou vyvolány výjimky pro všechny požadavky na zabezpečení kódu, které nebyly povoleny na stránce **Zabezpečení.** Zobrazí se pomocná pomocná pomoc nápomocní s informacemi, která poskytuje návrhy, jak upravit kód, aby se zabránilo výjimce.

 Kromě toho při psaní kódu funkce IntelliSense v Editoru kódu zakáže všechny členy, kteří nejsou zahrnuti v oprávněních zabezpečení, které jste nakonfigurovali.

 Další informace naleznete v [tématu How to: Debug a ClickOnce Application with Restricted Permissions](securing-clickonce-applications.md).

## <a name="security-permissions-for-browser-hosted-applications"></a>Oprávnění zabezpečení pro aplikace hostované prohlížečem
 Visual Studio poskytuje následující typy projektů pro aplikace WPF (Windows Presentation Foundation):

- Aplikace WPF pro Windows

- Aplikace webového prohlížeče WPF

- Knihovna vlastních ovládacích prvků WPF

- Knihovna služeb WPF

  Z těchto typů projektů jsou ve webovém prohlížeči hostovány pouze aplikace webového prohlížeče WPF, a proto vyžadují zvláštní nastavení nasazení a zabezpečení. Výchozí nastavení zabezpečení pro tyto aplikace jsou následující:

- **Povolení nastavení zabezpečení ClickOnce**

- **Jedná se o aplikaci s částečnou důvěryhodností.**

- **Zóna Internet** (s vybranou výchozí sadou oprávnění pro aplikace webového prohlížeče WPF)

  V dialogovém okně **Upřesnit nastavení zabezpečení** je zaškrtnuto a zakázáno **políčko Ladit tuto aplikaci pomocí vybrané sady oprávnění.** Důvodem je, že ladění v zóně nelze vypnout pro aplikace hostované prohlížečem.

## <a name="see-also"></a>Viz také
- [Zabezpečení aplikací ClickOnce](../deployment/securing-clickonce-applications.md)
- [Postup: Povolení nastavení zabezpečení ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)
- [Postup: Nastavení zóny zabezpečení pro aplikaci ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Postup: Nastavení vlastních oprávnění pro aplikaci ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Postup: Ladění aplikace ClickOnce s omezenými oprávněními](securing-clickonce-applications.md)
- [Přehled nasazení důvěryhodných aplikací](../deployment/trusted-application-deployment-overview.md)
- [Stránka Zabezpečení, návrhář projektu](../ide/reference/security-page-project-designer.md)