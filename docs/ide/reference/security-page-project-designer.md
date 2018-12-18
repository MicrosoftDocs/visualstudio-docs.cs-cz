---
title: Stránka Zabezpečení, návrhář projektu
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesSecurity
- vb.XBAPProjectPropertiesSecurity
helpviewer_keywords:
- Project Designer, Security page
- Security page in Project Designer
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 75877dfd8620af9d3fdfecb5cfcb10761a739515
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
ms.locfileid: "31949576"
---
# <a name="security-page-project-designer"></a>Stránka Zabezpečení, návrhář projektu

**Zabezpečení** stránky **Návrhář projektu** slouží ke konfiguraci nastavení zabezpečení přístupu kódu pro aplikace, které jsou nasazeny pomocí [!INCLUDE[ndptecclick](../../deployment/includes/ndptecclick_md.md)] nasazení. Další informace najdete v tématu [zabezpečení přístupu kódu pro aplikace ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md).

 Pro přístup k **zabezpečení** klikněte na uzel projektu v **Průzkumníku řešení**a pak klikněte na **projektu** nabídky, klikněte na tlačítko **vlastnosti**. Když **Návrhář projektu** se zobrazí, klikněte na tlačítko **zabezpečení** kartě.

## <a name="security-settings"></a>Nastavení zabezpečení

 **Povolení nastavení zabezpečení ClickOnce**

 Určuje, zda je povoleno nastavení zabezpečení v době návrhu. Pokud tato možnost vybrána, všechny ostatní možnosti na **zabezpečení** stránky nejsou k dispozici.

> [!NOTE]
> Při publikování aplikace pomocí **publikovat** průvodce, tato možnost je automaticky povolené.


 Když vyberete tuto možnost, máte možnost výběru mezi dvěma přepínací tlačítka: **Toto je aplikace s úplným vztahem důvěryhodnosti** nebo **Toto je aplikace s částečnou důvěryhodností**.

 Tato možnost je vybrána ve výchozím nastavení pro projekty aplikace WPF webového prohlížeče.

 Tato možnost vybrána ve výchozím nastavení pro všechny ostatní typy projektu.

 **Toto je aplikace s úplným vztahem důvěryhodnosti**

 Pokud vyberete tuto možnost, aplikace, pokud je nainstalovat nebo spustit na klientském počítači požádá o oprávnění plné důvěryhodnosti. Vyhněte se použití, úplný vztah důvěryhodnosti Pokud je to možné, protože vaše aplikace bude udělen neomezený přístup k prostředkům, například systém souborů a registr.

 Ve výchozím nastavení pro projekty aplikace WPF webového prohlížeče je tato možnost nastavena na částečné důvěryhodnosti.

 Ve výchozím nastavení pro všechny ostatní typy projektů je tato možnost nastavena na úplný vztah důvěryhodnosti.

 **Toto je aplikace s částečnou důvěryhodností**

 Pokud vyberete tuto možnost, aplikace, pokud je nainstalovat nebo spustit na klientském počítači požádá o oprávnění částečné důvěryhodnosti. *Částečná důvěryhodnost* znamená, že se spustí jenom akce, které jsou povoleny v rámci přístupová oprávnění zabezpečení požadovaná kódu. Další informace o tom, jak nakonfigurovat oprávnění zabezpečení najdete v tématu [zabezpečení přístupu kódu pro aplikace ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md).

 Můžete zadat nastavení zabezpečení částečné důvěryhodnosti na možnosti v konfiguraci **oprávnění zabezpečení ClickOnce** oblasti.

## <a name="clickonce-security-permissions"></a>Oprávnění zabezpečení ClickOnce

 **Zóny, kterou vaše aplikace bude nainstalována z**

 Určuje výchozí sadu oprávnění zabezpečení přístupu ke kódu. Zvolte **Internet** nebo **místní Intranet** pro s omezenými oprávněními nastavit, nebo zvolte **(vlastní)** chcete konfigurovat vlastní oprávnění nastavit. Pokud aplikace vyžaduje další oprávnění, než udělena v zóně, se zobrazí výzva vztahu důvěryhodnosti ClickOnce pro koncové uživatele a udělit další oprávnění. Další informace o tom, jak nakonfigurovat oprávnění zabezpečení najdete v tématu [zabezpečení přístupu kódu pro aplikace ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md).

 Ve výchozím nastavení pro projekty aplikace WPF webového prohlížeče, je tato možnost nastavena na **Internet**.

 **Upravit oprávnění XML**

 Otevře manifestu šablony aplikace (app.manifest) konfigurace oprávnění pro **(vlastní)** sadu oprávnění.

 **Pokročilé**

 Otevře se [rozšířené zabezpečení dialogové okno nastavení](../../ide/reference/advanced-security-settings-dialog-box.md), který slouží ke konfiguraci nastavení pro ladění aplikace s omezenými oprávněními. Tato nastavení jsou zaškrtnutá políčka během ladění a výjimek oprávnění znamenat, že vaše aplikace může potřebovat větší oprávnění než definované v zóně.

## <a name="see-also"></a>Viz také

- <xref:System.Security.Permissions.WebBrowserPermission>
- <xref:System.Security.Permissions.MediaPermission>
- [Zabezpečení přístupu ke kódu pro aplikace ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md)
- [Postupy: Povolení nastavení zabezpečení ClickOnce](../../deployment/how-to-enable-clickonce-security-settings.md)
- [Postupy: Nastavení zóny zabezpečení pro aplikaci ClickOnce](../../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Postupy: Nastavení vlastních oprávnění pro aplikaci ClickOnce](../../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Postupy: Ladění aplikace ClickOnce s omezenými oprávněními](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)
- [ClickOnce – zabezpečení a nasazení](../../deployment/clickonce-security-and-deployment.md)
- [Referenční dokumentace k vlastnostem projektu](../../ide/reference/project-properties-reference.md)
- [Dialogové okno Pokročilé nastavení zabezpečení](../../ide/reference/advanced-security-settings-dialog-box.md)