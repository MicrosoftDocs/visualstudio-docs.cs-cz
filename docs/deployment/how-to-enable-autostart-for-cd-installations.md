---
title: Povolit automatické spouštění pro instalaci CD | Microsoft Docs
description: Naučte se, jak povolit automatické spouštění při nasazení aplikace ClickOnce pomocí vyměnitelného média, jako je například CD-ROM nebo DVD-ROM.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, AutoStart
- ClickOnce deployment, installation on CD or DVD
- deploying applications [ClickOnce], installation on CD or DVD
ms.assetid: caaec619-900c-4790-90e3-8c91f5347635
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b157df8666223e72a1e36d58505a5c087b0351bf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900682"
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>Postupy: povolení funkce Autostart pro instalace z disku CD
Když nasadíte [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikaci pomocí vyměnitelného média, jako je například CD-ROM nebo DVD-ROM, můžete povolit `AutoStart` , aby se [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace automaticky spustila při vložení média.

 `AutoStart` lze povolit na stránce **publikovat** v **Návrháři projektu**.

### <a name="to-enable-autostart"></a>Povolení autostart

1. Když je vybrán projekt v **Průzkumník řešení**, v nabídce **projekt** klikněte na **vlastnosti**.

2. Klikněte na kartu **publikovat** .

3. Klikněte na tlačítko **Možnosti** .

     Zobrazí se dialogové okno **Možnosti publikování** .

4. Klikněte na tlačítko **nasazení**.

5. Zaškrtněte políčko **pro instalaci CD, automaticky spustit instalační program při vložení disku CD** .

     Po publikování aplikace bude soubor *Autorun. inf* zkopírován do umístění pro publikování.

## <a name="see-also"></a>Viz také
- [Publikování aplikací ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Postupy: publikování aplikace ClickOnce pomocí Průvodce publikováním](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)