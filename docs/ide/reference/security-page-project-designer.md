---
title: Stránka Zabezpečení, návrhář projektu
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesSecurity
- vb.XBAPProjectPropertiesSecurity
helpviewer_keywords:
- Project Designer, Security page
- Security page in Project Designer
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1834713ad114ab8a86e314bbe052f4873b308956
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593574"
---
# <a name="security-page-project-designer"></a>Stránka Zabezpečení, návrhář projektu

Stránka **Zabezpečení** **návrháře projektu** se používá ke konfiguraci nastavení zabezpečení přístupu kódu pro aplikace, které jsou nasazeny pomocí nasazení ClickOnce. Další informace naleznete v [tématu Zabezpečení přístupu kódu pro aplikace ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md).

Chcete-li získat přístup ke stránce **Zabezpečení,** klepněte na uzel projektu v **Průzkumníku řešení**a potom v nabídce **Project** klepněte na příkaz **Vlastnosti**. Po zobrazení **Návrháře projektů** klikněte na kartu **Zabezpečení.**

## <a name="security-settings"></a>Nastavení zabezpečení

 **Povolení nastavení zabezpečení ClickOnce**

Určuje, zda jsou nastavení zabezpečení povolena v době návrhu. Pokud tato možnost není zaškrtnuta, nejsou k dispozici všechny ostatní možnosti na stránce **Zabezpečení.**

> [!NOTE]
> Při publikování aplikace pomocí Průvodce **publikováním** je tato možnost automaticky povolena.

Vyberete-li tuto možnost, budete mít možnost vybrat jedno ze dvou přepínacích tlačítek: **Jedná se o aplikaci s úplným vztahem důvěryhodnosti** nebo **o aplikaci s částečnou důvěryhodností**.

Ve výchozím nastavení je vybrána tato možnost pro projekty aplikace webového prohlížeče WPF.

Ve výchozím nastavení je tato možnost pro všechny ostatní typy projektů vymazána.

 **Toto je aplikace s plnou důvěryhodností.**

Pokud vyberete tuto možnost, aplikace požádá o oprávnění úplné důvěryhodnosti při instalaci nebo spuštění v klientském počítači. Pokud je to možné, nepoužívejte úplnou důvěryhodnost, protože vaší aplikaci bude udělen neomezený přístup k prostředkům, jako je například systém souborů a registr.

Ve výchozím nastavení je pro projekty aplikace webového prohlížeče WPF tato možnost nastavena na částečnou důvěryhodnost.

Ve výchozím nastavení je tato možnost pro všechny ostatní typy projektů nastavena na hodnotu Úplná důvěryhodnost.

 **Jedná se o aplikaci s částečnou důvěryhodností.**

Pokud vyberete tuto možnost, aplikace požádá o částečná oprávnění důvěryhodnosti při instalaci nebo spuštění v klientském počítači. *Částečný vztah důvěryhodnosti* znamená, že budou spuštěny pouze akce, které jsou povoleny podle požadovaných oprávnění zabezpečení přístupu kódu. Další informace o konfiguraci oprávnění zabezpečení naleznete v [tématu Code Access Security for ClickOnce Applications](../../deployment/code-access-security-for-clickonce-applications.md).

Nastavení zabezpečení Částečná důvěryhodnost můžete určit konfigurací možností v oblasti **Oprávnění zabezpečení ClickOnce.**

## <a name="clickonce-security-permissions"></a>ClickOnce Oprávnění zabezpečení

 **Zóna, ze které bude aplikace nainstalována**

Určuje výchozí sadu oprávnění zabezpečení přístupu kódu. Chcete-li nastavit omezená oprávnění, zvolte **internet** nebo **místní intranet** nebo zvolte **(Vlastní)** pro konfiguraci vlastní sady oprávnění. Pokud aplikace požaduje více oprávnění, než je uděleno v zóně, zobrazí se výzva důvěryhodnosti ClickOnce pro koncového uživatele udělit další oprávnění. Další informace o konfiguraci oprávnění zabezpečení naleznete v [tématu Code Access Security for ClickOnce Applications](../../deployment/code-access-security-for-clickonce-applications.md).

Ve výchozím nastavení je u projektů aplikace webového prohlížeče WPF tato možnost nastavena na **internet**.

 **Upravit oprávnění XML**

Otevře šablonu manifestu aplikace (app.manifest) pro konfiguraci oprávnění pro **sadu oprávnění (Vlastní).**

 **Pokročilé**

Otevře [dialogové okno Upřesnit nastavení zabezpečení](../../ide/reference/advanced-security-settings-dialog-box.md), které slouží ke konfiguraci nastavení pro ladění aplikace s omezenými oprávněními. Tato nastavení jsou kontrolovány během ladění a výjimky oprávnění označují, že vaše aplikace může potřebovat více oprávnění, než je definováno v zóně.

## <a name="see-also"></a>Viz také

- <xref:System.Security.Permissions.WebBrowserPermission>
- <xref:System.Security.Permissions.MediaPermission>
- [Zabezpečení přístupu kódu pro aplikace ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md)
- [Postupy: Povolení nastavení zabezpečení ClickOnce](../../deployment/how-to-enable-clickonce-security-settings.md)
- [Postupy: Nastavení zóny zabezpečení pro aplikaci ClickOnce](../../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Postupy: Nastavení vlastních oprávnění pro aplikaci ClickOnce](../../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Postupy: Ladění aplikace ClickOnce s omezenými oprávněními](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)
- [ClickOnce Zabezpečení a nasazení](../../deployment/clickonce-security-and-deployment.md)
- [Referenční dokumentace k vlastnostem projektu](../../ide/reference/project-properties-reference.md)
- [Dialogové okno Pokročilé nastavení zabezpečení](../../ide/reference/advanced-security-settings-dialog-box.md)
