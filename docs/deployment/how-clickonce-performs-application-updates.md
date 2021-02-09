---
title: Jak ClickOnce provádí aktualizace aplikace | Microsoft Docs
description: Přečtěte si, jak ClickOnce používá informace o verzi souboru k rozhodnutí, jestli chcete aplikaci aktualizovat. ClickOnce používá opravy souborů, aby se zabránilo redundanci při stahování.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- updates, ClickOnce
- ClickOnce deployment, updates
- deploying applications [ClickOnce], application updates
ms.assetid: d54313c2-cf0c-420d-b151-99953a95f0bb
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cdef39a0ab07d4cb9c9f42cf897bd7728934b88d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99915742"
---
# <a name="how-clickonce-performs-application-updates"></a>Jak ClickOnce provádí aktualizaci aplikací
ClickOnce používá informace o verzi souboru, které jsou uvedeny v manifestu nasazení aplikace, k rozhodnutí, zda chcete aktualizovat soubory aplikace. Po zahájení aktualizace používá ClickOnce techniku s názvem *opravy souborů* , aby nedocházelo k redundantnímu stahování souborů aplikace.

## <a name="file-patching"></a>Opravy souborů
 Při aktualizaci aplikace ClickOnce nestáhne všechny soubory pro novou verzi aplikace, pokud se soubory nezmění. Místo toho porovná signatury hodnot hash souborů zadaných v manifestu aplikace pro aktuální aplikaci proti podpisům v manifestu pro novou verzi. Pokud se signatury souboru liší, ClickOnce stáhne novou verzi. Pokud se signatury shodují, soubor se nezměnil z jedné verze na další. V tomto případě ClickOnce zkopíruje existující soubor a použije ho v nové verzi aplikace. Tento přístup zabraňuje, aby ClickOnce musela stahovat celou aplikaci znovu, i když se změnil pouze jeden nebo dva soubory.

 Oprava souborů funguje také pro sestavení, která jsou stažena na vyžádání pomocí <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroupAsync%2A> metod a.

 Použijete-li aplikaci Visual Studio k zkompilování aplikace, budou generovány nové podpisy hash pro všechny soubory pokaždé, když znovu sestavíte celý projekt. V tomto případě budou všechna sestavení stažena do klienta, i když se může změnit pouze několik sestavení.

 Opravy souborů nefungují u souborů, které jsou označeny jako data a uloženy v adresáři dat. Ty se vždycky stáhnou bez ohledu na signaturu hash souboru. Další informace o datovém adresáři najdete v tématu [přístup k místním a vzdáleným datům v aplikacích ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).

## <a name="see-also"></a>Viz také
- [Výběr strategie aktualizace ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)
- [Výběr strategie nasazení ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)