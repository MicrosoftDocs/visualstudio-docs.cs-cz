---
title: 'Postupy: určení offline nebo online režimu instalace ClickOnce Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d4111ca5aee4a405a4a797dbfee14a3d4b50435f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149751"
---
# <a name="how-to-specify-the-clickonce-offline-or-online-install-mode"></a>Postupy: Určení offline nebo online režimu instalace ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aplikace `Install Mode` pro [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikaci určuje, zda bude aplikace k dispozici offline nebo online. Pokud zvolíte, **že je aplikace dostupná jenom online**, musí mít uživatel přístup k [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] umístění publikování (buď webové stránce, nebo sdílené složce), aby bylo možné aplikaci spustit. Když vyberete aplikaci, která **je k dispozici v režimu offline**, aplikace přidá položky do nabídky **Start** a do dialogového okna **Přidat nebo odebrat programy** . uživatel může aplikaci spustit, když nejsou připojeni.  
  
 `Install Mode`Lze nastavit na stránce **publikovat** v **Návrháři projektu**.  
  
 **Poznámka:** `Install Mode` Lze také nastavit pomocí Průvodce publikováním. Další informace naleznete v tématu [How to: Publish a aplikace ClickOnce using the Publish Wizard](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
### <a name="to-make-a-clickonce-application-available-online-only"></a>Zpřístupnění aplikace ClickOnce pouze online  
  
1. S projektem vybraným v **Průzkumník řešení**v nabídce **projekt** klikněte na **vlastnosti**.  
  
2. Klikněte na kartu **publikovat** .  
  
3. V oblasti **režim instalace a nastavení** klikněte na tlačítko možnost **aplikace je k dispozici pouze online** .  
  
### <a name="to-make-a-clickonce-application-available-online-or-offline"></a>Zpřístupnění aplikace ClickOnce online nebo offline  
  
1. S projektem vybraným v **Průzkumník řešení**v nabídce **projekt** klikněte na **vlastnosti**.  
  
2. Klikněte na kartu **publikovat** .  
  
3. V oblasti **režim instalace a nastavení** klikněte na tlačítko **aplikace je k dispozici v režimu offline** a možnost.  
  
     Při instalaci aplikace přidá položky do nabídky **Start** a **přidá nebo odebere programy** v Ovládacích panelech.  
  
## <a name="see-also"></a>Viz také  
 [Publikování aplikací ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Postupy: publikování aplikace ClickOnce pomocí Průvodce publikováním](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Výběr strategie nasazení ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)
