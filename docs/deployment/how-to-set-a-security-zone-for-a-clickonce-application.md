---
title: Nastavení zóny zabezpečení (aplikace ClickOnce)
description: Přečtěte si o nastavení oprávnění zabezpečení přístupu kódu pro aplikaci ClickOnce, která začíná základní sadou oprávnění v Návrháři projektu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, security settings
- code access security, ClickOnce applications
- security zones, ClickOnce applications
ms.assetid: d3dac454-518a-44d7-a76e-ccb7b9c3a150
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 23174667827e63afb93d82679a51d65512731710
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946069"
---
# <a name="how-to-set-a-security-zone-for-a-clickonce-application"></a>Postupy: nastavení zóny zabezpečení pro aplikaci ClickOnce
Při nastavování oprávnění zabezpečení přístupu kódu pro aplikaci ClickOnce musíte začít se základní sadou oprávnění na stránce **zabezpečení** **Návrháře projektu**.

 Ve většině případů můžete také zvolit **internetovou** zónu, která obsahuje omezená sada oprávnění, nebo zónu **místního intranetu** , která obsahuje větší sadu oprávnění. Pokud vaše aplikace vyžaduje vlastní oprávnění, můžete to udělat tak, že vyberete **vlastní** zónu zabezpečení. Další informace o nastavení vlastních oprávnění naleznete v tématu [Postupy: nastavení vlastních oprávnění pro aplikaci ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).

### <a name="to-set-a-security-zone"></a>Nastavení zóny zabezpečení

1. Když je vybrán projekt v **Průzkumník řešení**, v nabídce **projekt** klikněte na **vlastnosti**.

2. Klikněte na kartu **Zabezpečení**.

3. Zaškrtněte políčko **Povolit nastavení zabezpečení ClickOnce** .

4. Vyberte přepínač možnost **aplikace s částečnou důvěryhodností** .

     Ovládací prvky v oddílu **oprávnění zabezpečení ClickOnce** jsou povolené.

5. V zóně, ve které **bude aplikace nainstalována** , vyberte zónu zabezpečení.

## <a name="see-also"></a>Viz také
- [Postupy: nastavení vlastních oprávnění pro aplikaci ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Zabezpečení aplikací ClickOnce](../deployment/securing-clickonce-applications.md)
- [Zabezpečení přístupu ke kódu pro aplikace ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
