---
title: Stránka Zabezpečení, návrhář projektu
description: Stránka zabezpečení Návrháře projektu slouží ke konfiguraci nastavení zabezpečení přístupu kódu pro aplikace, které jsou nasazeny pomocí nasazení ClickOnce.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesSecurity
- vb.XBAPProjectPropertiesSecurity
helpviewer_keywords:
- Project Designer, Security page
- Security page in Project Designer
author: Mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7080c1a2ce77d26987f81acaa0a751887f9f574e
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350254"
---
# <a name="security-page-project-designer"></a>Stránka Zabezpečení, návrhář projektu

Stránka **zabezpečení** **Návrháře projektu** slouží ke konfiguraci nastavení zabezpečení přístupu kódu pro aplikace, které jsou nasazeny pomocí nasazení ClickOnce. Další informace najdete v tématu [zabezpečení přístupu kódu pro aplikace ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md).

Chcete-li získat přístup ke stránce **zabezpečení** , klikněte na uzel projektu v **Průzkumník řešení** a potom v nabídce **projekt** klikněte na příkaz **vlastnosti**. Když se zobrazí **Návrhář projektu** , klikněte na kartu **zabezpečení** .

## <a name="security-settings"></a>Nastavení zabezpečení

 **Povolit nastavení zabezpečení ClickOnce**

Určuje, zda jsou nastavení zabezpečení povolena v době návrhu. Pokud tato možnost není zaškrtnutá, všechny ostatní možnosti na stránce **zabezpečení** nejsou k dispozici.

> [!NOTE]
> Když publikujete aplikaci pomocí průvodce **publikováním** , tato možnost je automaticky povolena.

Když vyberete tuto možnost, budete mít možnost výběru jednoho ze dvou přepínačů: **jedná se o úplnou důvěryhodnou aplikaci** nebo **se jedná o aplikaci s částečnou důvěryhodností**.

Ve výchozím nastavení je pro projekty aplikace webového prohlížeče WPF Tato možnost vybraná.

Ve výchozím nastavení pro všechny ostatní typy projektů Tato možnost není zaškrtnuta.

 **Toto je aplikace s plnou důvěryhodností.**

Vyberete-li tuto možnost, aplikace při instalaci nebo spuštění v klientském počítači požádá o úplná oprávnění důvěryhodnosti. Nepoužívejte úplný vztah důvěryhodnosti, pokud je to možné, protože vaší aplikaci bude udělen neomezený přístup k prostředkům, jako je třeba systém souborů a registr.

Ve výchozím nastavení pro projekty aplikace webového prohlížeče WPF je tato možnost nastavena na částečnou důvěryhodnost.

Ve výchozím nastavení pro všechny ostatní typy projektů je tato možnost nastavena na úplný vztah důvěryhodnosti.

 **Toto je aplikace s částečnou důvěryhodností.**

Pokud vyberete tuto možnost, aplikace při instalaci nebo spuštění v klientském počítači vyžádá částečná oprávnění vztahu důvěryhodnosti. *Částečná důvěryhodnost* znamená, že se spustí jenom akce, které jsou povolené v rámci požadovaných oprávnění zabezpečení přístupu ke kódu. Další informace o tom, jak nakonfigurovat oprávnění zabezpečení, najdete v tématu [zabezpečení přístupu kódu pro aplikace ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md).

Nastavení zabezpečení s částečnou důvěryhodností můžete určit konfigurací možností v oblasti **oprávnění zabezpečení ClickOnce** .

## <a name="clickonce-security-permissions"></a>Oprávnění zabezpečení ClickOnce

 **Zóna, ze které se aplikace nainstaluje**

Určuje výchozí sadu oprávnění zabezpečení přístupu kódu. Vyberte **Internet** nebo **místní intranet** pro sadu omezených oprávnění, nebo vyberte **(vlastní)** a nakonfigurujte vlastní sadu oprávnění. Pokud aplikace požaduje více oprávnění, než je uděleno v zóně, zobrazí se uživateli výzva k zadání vztahu důvěryhodnosti ClickOnce pro koncového uživatele, který udělí další oprávnění. Další informace o tom, jak nakonfigurovat oprávnění zabezpečení, najdete v tématu [zabezpečení přístupu kódu pro aplikace ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md).

Ve výchozím nastavení jsou pro projekty aplikace webového prohlížeče WPF tyto možnosti nastaveny na možnost **Internet**.

 **Upravit oprávnění XML**

Otevře šablonu manifestu aplikace (App. manifest) pro konfiguraci oprávnění pro sadu oprávnění **(vlastní)** .

 **Pokročilý**

Otevře [dialogové okno Upřesnit nastavení zabezpečení](../../ide/reference/advanced-security-settings-dialog-box.md), které se používá ke konfiguraci nastavení pro ladění aplikace s omezenými oprávněními. Tato nastavení jsou kontrolována během ladění a výjimky oprávnění označují, že vaše aplikace může potřebovat více oprávnění, než je definováno v zóně.

## <a name="see-also"></a>Viz také

- <xref:System.Security.Permissions.WebBrowserPermission>
- <xref:System.Security.Permissions.MediaPermission>
- [Zabezpečení přístupu ke kódu pro aplikace ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md)
- [Postupy: Povolení nastavení zabezpečení ClickOnce](../../deployment/how-to-enable-clickonce-security-settings.md)
- [Postupy: Nastavení zóny zabezpečení pro aplikaci ClickOnce](../../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Postupy: Nastavení vlastních oprávnění pro aplikaci ClickOnce](../../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Zabezpečení aplikací ClickOnce](../../deployment/securing-clickonce-applications.md)
- [ClickOnce – zabezpečení a nasazení](../../deployment/clickonce-security-and-deployment.md)
- [Referenční dokumentace k vlastnostem projektu](../../ide/reference/project-properties-reference.md)
- [Dialogové okno Upřesnit nastavení zabezpečení](../../ide/reference/advanced-security-settings-dialog-box.md)
