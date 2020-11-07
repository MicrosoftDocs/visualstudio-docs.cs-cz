---
title: Změnit jazyk publikování pro aplikaci ClickOnce
description: Naučte se, jak zadat jazyk nebo jazykovou verzi pro lokalizaci aplikace v ClickOnce namísto výchozího nastavení pro jazyk a jazykovou verzi vašeho vývojového počítače.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Publish language property
- ClickOnce deployment, changing publish language
- publishing, ClickOnce
ms.assetid: ef5024c4-cda1-4970-bc75-32a2a10c92c3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7fed8c137b5bce225d8a231bb5a263b87c2bf361
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350163"
---
# <a name="how-to-change-the-publish-language-for-a-clickonce-application"></a>Postupy: Změna jazyka publikování pro aplikaci ClickOnce

Při publikování [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace je uživatelské rozhraní zobrazené během instalace výchozím nastavením pro jazyk a jazykovou verzi vašeho vývojového počítače. Pokud publikujete lokalizovanou aplikaci, bude nutné zadat jazyk a jazykovou verzi, aby odpovídaly lokalizované verzi. Tato vlastnost je určena `Publish language` vlastností projektu.

`Publish language`Vlastnost lze nastavit v dialogovém okně **Možnosti publikování** přístupném ze stránky **publikovat** v **Návrháři projektu**.

> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, v nabídce **nástroje** klikněte na položku **Nastavení importu a exportu** . Další informace najdete v tématu [resetování nastavení](../ide/environment-settings.md#reset-settings).

## <a name="to-change-the-publish-language"></a>Změna jazyka publikování

1. S projektem vybraným v **Průzkumník řešení** v nabídce **projekt** klikněte na **vlastnosti**.

2. Klikněte na kartu **publikovat** .

3. Kliknutím na tlačítko **Možnosti** otevřete dialogové okno **Možnosti publikování** .

4. Klikněte na **Popis**.

5. V dialogovém okně **Možnosti publikování** vyberte v rozevíracím seznamu **jazyk publikování** jazyk a jazykovou verzi a pak klikněte na tlačítko **OK**.

## <a name="see-also"></a>Viz také

- [Publikování aplikací ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Postupy: publikování aplikace ClickOnce pomocí Průvodce publikováním](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)