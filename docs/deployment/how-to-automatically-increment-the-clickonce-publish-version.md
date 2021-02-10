---
title: Automatické zvýšení verze publikování ClickOnce
description: Naučte se, jak zakázat automatické zvyšování čísla revize pro aplikaci ClickOnce pomocí sady Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], incrementing publish version automatically
- Publish Version property, incrementing
- ClickOnce deployment, incrementing publish version automatically
- publishing, ClickOnce
ms.assetid: 686ab88a-6305-4914-a05b-fe269cc0ae1e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b84b0a8932bb9d8fd4738c2cd4924b61bb6faeb7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947772"
---
# <a name="how-to-automatically-increment-the-clickonce-publish-version"></a>Postupy: automatické zvýšení verze publikování ClickOnce

Při publikování [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace Změna `Publish Version` vlastnosti způsobí, že se aplikace publikuje jako aktualizace. Ve výchozím nastavení Visual Studio automaticky zvyšuje `Revision` počet `Publish Version` pokaždé, když publikujete aplikaci.

Toto chování můžete zakázat na stránce **publikovat** v **Návrháři projektu**.

> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, v nabídce **nástroje** klikněte na položku **Nastavení importu a exportu** . Další informace najdete v tématu [resetování nastavení](../ide/environment-settings.md#reset-settings).

## <a name="to-disable-automatically-incrementing-the-publish-version"></a>Zakázání automatického zvýšení verze publikování

1. S projektem vybraným v **Průzkumník řešení** v nabídce **projekt** klikněte na **vlastnosti**.

2. Klikněte na kartu **publikovat** .

3. V části **publikovat verzi** zrušte zaškrtnutí políčka **automaticky zvyšovat revizi při každém vydání** .

## <a name="see-also"></a>Viz také

- [Postupy: nastavení verze publikování ClickOnce](../deployment/how-to-set-the-clickonce-publish-version.md)
- [Publikování aplikací ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Postupy: publikování aplikace ClickOnce pomocí Průvodce publikováním](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)