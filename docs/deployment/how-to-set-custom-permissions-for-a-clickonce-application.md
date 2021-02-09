---
title: Nastavit vlastní oprávnění (aplikace ClickOnce)
description: Naučte se, jak nasadit aplikaci ClickOnce, která používá výchozí oprávnění, nebo vytvořte vlastní zónu pro konkrétní oprávnění, která aplikace potřebuje.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, permissions
- permissions, ClickOnce applications
ms.assetid: 660459ca-ef73-44a8-b323-610001f63b93
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2050f3534caba8aba12fa8550eb6e573a3d0db08
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885037"
---
# <a name="how-to-set-custom-permissions-for-a-clickonce-application"></a>Postupy: nastavení vlastních oprávnění pro aplikaci ClickOnce
Můžete nasadit [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikaci, která používá výchozí oprávnění pro zóny Internet nebo místní intranet. Alternativně můžete vytvořit vlastní zónu pro konkrétní oprávnění, která aplikace potřebuje. To lze provést přizpůsobením oprávnění zabezpečení na stránce **zabezpečení** **Návrháře projektu**.

### <a name="to-customize-a-permission"></a>Přizpůsobení oprávnění

1. S projektem vybraným v **Průzkumník řešení** v nabídce **projekt** klikněte na **vlastnosti**.

2. Klikněte na kartu **Zabezpečení**.

3. Zaškrtněte políčko **Povolit nastavení zabezpečení ClickOnce** .

4. Vyberte přepínač možnost **aplikace s částečnou důvěryhodností** .

     Ovládací prvky v oddílu **oprávnění zabezpečení ClickOnce** jsou povolené.

5. Z rozevíracího seznamu zóna, ve které **se aplikace nainstaluje** , klikněte na **(vlastní)**.

6. Klikněte na **Upravit oprávnění XML**.

     Soubor *App. manifest* se otevře v editoru XML.

7. Před `</applicationRequestMinimum>` element přidejte kód XML pro oprávnění, která vaše aplikace vyžaduje.

    > [!NOTE]
    > Můžete použít `ToXml` metodu sady oprávnění k vygenerování kódu XML pro manifest aplikace. Chcete-li například vygenerovat XML pro <xref:System.Security.Permissions.EnvironmentPermission> sadu oprávnění, zavolejte <xref:System.Security.Permissions.EnvironmentPermission.ToXml%2A> metodu.

## <a name="see-also"></a>Viz také
- [Zabezpečené aplikace ClickOnce](../deployment/securing-clickonce-applications.md)
- [Zabezpečení přístupu ke kódu pro aplikace ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
