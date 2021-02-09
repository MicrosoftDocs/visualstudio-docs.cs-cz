---
title: Nastavení publikační verze ClickOnce | Microsoft Docs
description: Naučte se, jak nastavit vlastnost verze publikování ClickOnce, která určuje, jestli je aplikace aktualizace.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, setting publish version
- publishing, ClickOnce
- Publish Version property
ms.assetid: 06f15504-6385-40a6-b01d-cd90ca36dc73
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 71d74d8b16e058b150187a231a1f3a7323c0c612
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885024"
---
# <a name="how-to-set-the-clickonce-publish-version"></a>Postupy: nastavení verze publikování ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `Publish Version` Vlastnost určuje, zda bude aplikace, kterou publikujete, považována za aktualizaci. Pokaždé, když se verze zvýší, aplikace se publikuje jako aktualizace.

 `Publish Version`Vlastnost lze nastavit na stránce **publikovat** v **Návrháři projektu**.

> [!NOTE]
> K dispozici je možnost projektu, která bude automaticky zvyšovat hodnotu `Publish Version` vlastnosti při každém publikování aplikace. Tato možnost je ve výchozím nastavení povolena. Další informace najdete v tématu [Postup: automatické zvýšení verze publikování ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md).

### <a name="to-change-the-publish-version"></a>Změna verze publikování

1. Když je vybrán projekt v **Průzkumník řešení**, v nabídce **projekt** klikněte na **vlastnosti**.

2. Klikněte na kartu **publikovat** .

3. V poli **verze publikování** Zvyšte číslo **verze, podverze,** **sestavení** nebo **Revize** . 

    > [!NOTE]
    > Nikdy byste neměli snižovat číslo verze; v takovém případě by mohlo dojít k nepředvídatelnému chování aktualizace.

## <a name="see-also"></a>Viz také
- [Výběr strategie aktualizace ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)
- [Postupy: automatické zvýšení verze publikování ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)
- [Publikování aplikací ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Postupy: publikování aplikace ClickOnce pomocí Průvodce publikováním](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)