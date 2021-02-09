---
title: Zadat offline nebo online režim instalace (ClickOnce)
description: Naučte se, jak určit režim instalace pro aplikaci ClickOnce, která určuje, jestli je aplikace k dispozici offline nebo online.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, specifying install mode
- install mode
- online applications
- offline applications
- ClickOnce install mode
ms.assetid: 0aee5fc1-e966-4bda-9b8f-d9997aeaa779
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 918cb7e60f4e3fed2beee024d51b94499b14b632
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900426"
---
# <a name="how-to-specify-the-clickonce-offline-or-online-install-mode"></a>Postupy: určení offline nebo online režimu instalace ClickOnce
Aplikace `Install Mode` pro [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikaci určuje, zda bude aplikace k dispozici offline nebo online. Pokud zvolíte, **že je aplikace dostupná jenom online**, musí mít uživatel přístup k [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] umístění publikování (buď webové stránce, nebo sdílené složce), aby bylo možné aplikaci spustit. Když vyberete aplikaci, která **je k dispozici v režimu offline**, aplikace přidá položky do nabídky **Start** a do dialogového okna **Přidat nebo odebrat programy** . uživatel může aplikaci spustit, když nejsou připojeni.

`Install Mode`Lze nastavit na stránce **publikovat** v **Návrháři projektu**.

> [!NOTE]
> `Install Mode`Lze také nastavit pomocí Průvodce publikováním. Další informace naleznete v tématu [How to: Publish a aplikace ClickOnce using the Publish Wizard](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

### <a name="to-make-a-clickonce-application-available-online-only"></a>Zpřístupnění aplikace ClickOnce pouze online

1. S projektem vybraným v **Průzkumník řešení** v nabídce **projekt** klikněte na **vlastnosti**.

2. Klikněte na kartu **publikovat** .

3. V oblasti **režim instalace a nastavení** klikněte na tlačítko možnost **aplikace je k dispozici pouze online** .

### <a name="to-make-a-clickonce-application-available-online-or-offline"></a>Zpřístupnění aplikace ClickOnce online nebo offline

1. S projektem vybraným v **Průzkumník řešení** v nabídce **projekt** klikněte na **vlastnosti**.

2. Klikněte na kartu **publikovat** .

3. V oblasti **režim instalace a nastavení** klikněte na tlačítko **aplikace je k dispozici v režimu offline** a možnost.

     Při instalaci aplikace přidá položky do nabídky **Start** a **přidá nebo odebere programy** v Ovládacích panelech.

## <a name="see-also"></a>Viz také
- [Publikování aplikací ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Postupy: publikování aplikace ClickOnce pomocí Průvodce publikováním](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
- [Výběr strategie nasazení ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)