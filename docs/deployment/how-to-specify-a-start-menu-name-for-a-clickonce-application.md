---
title: Zadat název nabídky Start pro aplikaci ClickOnce
description: Zjistěte, jak změnit zobrazované jméno aplikace ClickOnce nastavením názvu produktu v dialogovém okně Možnosti publikování.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Start menu resource name
- Start menu name
- ClickOnce deployment, Start menu name
ms.assetid: 4b5183b2-2fd4-4433-9310-4a73bb12c4e3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 12a6ebce0ff3bb7c3040765c1a82f876d0055c4d
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349669"
---
# <a name="how-to-specify-a-start-menu-name-for-a-clickonce-application"></a>Postupy: určení názvu nabídky Start pro aplikaci ClickOnce
Když [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] je aplikace nainstalována pro online i offline použití, přidá se do nabídky **Start** položka a seznam **Přidat nebo odebrat programy** . Ve výchozím nastavení je zobrazované jméno stejné jako název sestavení aplikace, ale můžete změnit název zobrazení nastavením **názvu produktu** v dialogovém okně **Možnosti publikování** .

 **Název produktu** se zobrazí na stránce *publish.htm* ; v případě nainstalované offline aplikace se jedná o název položky v nabídce **Start** a také na název, který se zobrazí v nabídce **Přidat nebo odebrat programy**.

 **Název vydavatele** se zobrazí na stránce *publish.htm* nad **názvem produktu** a v případě nainstalované offline aplikace bude také názvem složky, která obsahuje ikonu aplikace v nabídce **Start** .

 Zástupce v nabídce Start nebo odkaz na aplikaci se vytvoří v *%AppData%\Microsoft\Windows\Start start\programy \\<jméno \> vydavatele*. Zástupce nebo odkaz na aplikaci má stejný název jako název produktu.

 Vlastnosti **název produktu** a **název vydavatele** můžete nastavit v dialogovém okně **Možnosti publikování** , které je k dispozici na stránce **publikovat** v **Návrháři projektu**.

### <a name="to-specify-a-start-menu-name"></a>Určení názvu nabídky Start

1. S projektem vybraným v **Průzkumník řešení** v nabídce **projekt** klikněte na **vlastnosti**.

2. Klikněte na kartu **publikovat** .

3. Kliknutím na tlačítko **Možnosti** otevřete dialogové okno **Možnosti publikování** .

4. Klikněte na **Popis**.

5. V dialogovém okně **Možnosti publikování** zadejte název, který se zobrazí v poli **název produktu**.

6. V případě potřeby můžete zadat název vydavatele v **názvu vydavatele**.

## <a name="see-also"></a>Viz také
- [Publikování aplikací ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Postupy: publikování aplikace ClickOnce pomocí Průvodce publikováním](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)