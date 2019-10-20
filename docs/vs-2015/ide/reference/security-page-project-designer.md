---
title: Stránka zabezpečení, Návrhář projektu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesSecurity
- vb.XBAPProjectPropertiesSecurity
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Project Designer, Security page
- Security page in Project Designer
ms.assetid: 641d9cd3-fa07-498a-8568-3c169bb4d3d5
caps.latest.revision: 40
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 768b0d43d8e6b52781e3f2dc2029e0b96b3a6548
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665528"
---
# <a name="security-page-project-designer"></a>Stránka Zabezpečení, návrhář projektu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Stránka **zabezpečení** **Návrháře projektu** se používá ke konfiguraci nastavení zabezpečení přístupu kódu pro aplikace, které jsou nasazeny pomocí nasazení [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)]. Další informace najdete v tématu [zabezpečení přístupu kódu pro aplikace ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md).

 Chcete-li získat přístup ke stránce **zabezpečení** , klikněte na uzel projektu v **Průzkumník řešení**a potom v nabídce **projekt** klikněte na příkaz **vlastnosti**. Když se zobrazí **Návrhář projektu** , klikněte na kartu **zabezpečení** .

## <a name="security-settings"></a>Nastavení zabezpečení
 **Povolit nastavení zabezpečení ClickOnce** Určuje, zda jsou nastavení zabezpečení povolena v době návrhu. Pokud tato možnost není zaškrtnutá, všechny ostatní možnosti na stránce **zabezpečení** nejsou k dispozici.

> [!NOTE]
> Když publikujete aplikaci pomocí průvodce **publikováním** , tato možnost je automaticky povolena.

 Když vyberete tuto možnost, budete mít možnost výběru jednoho ze dvou přepínačů: **jedná se o úplnou důvěryhodnou aplikaci** nebo **se jedná o aplikaci s částečnou důvěryhodností**.

 Ve výchozím nastavení je pro projekty aplikace webového prohlížeče WPF Tato možnost vybraná.

 Ve výchozím nastavení pro všechny ostatní typy projektů Tato možnost není zaškrtnuta.

 **Toto je aplikace s plnou důvěryhodností** . Vyberete-li tuto možnost, aplikace při instalaci nebo spuštění v klientském počítači požádá o úplná oprávnění důvěryhodnosti. Nepoužívejte úplný vztah důvěryhodnosti, pokud je to možné, protože vaší aplikaci bude udělen neomezený přístup k prostředkům, jako je třeba systém souborů a registr.

 Ve výchozím nastavení pro projekty aplikace webového prohlížeče WPF je tato možnost nastavena na částečnou důvěryhodnost.

 Ve výchozím nastavení pro všechny ostatní typy projektů je tato možnost nastavena na úplný vztah důvěryhodnosti.

 **Toto je aplikace s částečnou důvěryhodností** . Pokud vyberete tuto možnost, aplikace při instalaci nebo spuštění v klientském počítači vyžádá částečná oprávnění vztahu důvěryhodnosti. *Částečná důvěryhodnost* znamená, že se spustí jenom akce, které jsou povolené v rámci požadovaných oprávnění zabezpečení přístupu ke kódu. Další informace o tom, jak nakonfigurovat oprávnění zabezpečení, najdete v tématu [zabezpečení přístupu kódu pro aplikace ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md).

 Nastavení zabezpečení s částečnou důvěryhodností můžete určit konfigurací možností v oblasti **oprávnění zabezpečení ClickOnce** .

## <a name="clickonce-security-permissions"></a>Oprávnění zabezpečení ClickOnce
 **Zóna, ze které se aplikace nainstaluje** Určuje výchozí sadu oprávnění zabezpečení přístupu kódu. Vyberte **Internet** nebo **místní intranet** pro sadu omezených oprávnění, nebo vyberte **(vlastní)** a nakonfigurujte vlastní sadu oprávnění. Pokud aplikace požaduje více oprávnění, než je uděleno v zóně, zobrazí se uživateli výzva k zadání vztahu důvěryhodnosti ClickOnce pro koncového uživatele, který udělí další oprávnění. Další informace o tom, jak nakonfigurovat oprávnění zabezpečení, najdete v tématu [zabezpečení přístupu kódu pro aplikace ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md).

 Ve výchozím nastavení jsou pro projekty aplikace webového prohlížeče WPF tyto možnosti nastaveny na možnost **Internet**.

 **Upravit oprávnění XML** Otevře šablonu manifestu aplikace (App. manifest) pro konfiguraci oprávnění pro sadu oprávnění **(vlastní)** .

 **Rozšířené možnosti** Otevře [dialogové okno Upřesnit nastavení zabezpečení](../../ide/reference/advanced-security-settings-dialog-box.md), které se používá ke konfiguraci nastavení pro ladění aplikace s omezenými oprávněními. Tato nastavení jsou kontrolována během ladění a výjimky oprávnění označují, že vaše aplikace může potřebovat více oprávnění, než je definováno v zóně.

## <a name="see-also"></a>Viz také
 <xref:System.Security.Permissions.WebBrowserPermission><xref:System.Security.Permissions.MediaPermission>
 [Zabezpečení přístupu kódu pro ClickOnce aplikace](../../deployment/code-access-security-for-clickonce-applications.md) [Postupy: povolení nastavení zabezpečení ClickOnce](../../deployment/how-to-enable-clickonce-security-settings.md) [Postupy: nastavení zóny zabezpečení pro aplikaci ClickOnce](../../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md) [Postupy: nastavení vlastních oprávnění pro aplikaci ClickOnce](../../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md) [Postupy: Ladění aplikace ClickOnce s omezenými oprávněními](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md) [ClickOnce vlastnosti projektu zabezpečení a nasazení](../../deployment/clickonce-security-and-deployment.md) [referenční](../../ide/reference/project-properties-reference.md) [dialogové okno Upřesnit nastavení zabezpečení](../../ide/reference/advanced-security-settings-dialog-box.md)
