---
title: Zadat podrobné soubory protokolu (nasazení ClickOnce)
description: Naučte se, jak zadat podrobnosti o protokolech aktivit, které ClickOnce udržuje pro instalaci, inicializaci, aktualizaci a odinstalaci nasazení ClickOnce.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- logs, ClickOnce deployment
- ClickOnce deployment, logging
ms.assetid: 0807a28d-2e40-4a51-ab10-308d808ded6b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0da285cfef49bd495fbecf39131e49cacd0476a5
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350917"
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>Postupy: určení podrobných souborů protokolu pro ClickOnce nasazení
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] udržuje soubory protokolu aktivit pro všechna nasazení. Tyto protokoly dokumentují informace týkající se instalace, inicializace, aktualizace a odinstalace [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazení. Chcete-li zvýšit podrobnosti, které [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] zapisuje do těchto souborů protokolu, použijte Editor registru ( *regedit.exe* ) a určete úroveň podrobností.

> [!CAUTION]
> Pokud používáte Editor registru nesprávně, může dojít k vážným problémům, které mohou vyžadovat přeinstalaci operačního systému. Editor registru použijte na vlastní riziko.

 Následující postup popisuje, jak zadat úroveň podrobností pro [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] soubory protokolu pro aktuálního uživatele. Chcete-li snížit úroveň podrobností, odeberte tuto hodnotu registru.

### <a name="to-specify-verbose-log-files"></a>Určení podrobných souborů protokolu

1. Otevřete *Regedit.exe*.

2. Přejděte k uzlu **HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment**.

3. V případě potřeby vytvořte novou řetězcovou hodnotu s názvem `LogVerbosityLevel` .

4. Nastavte `LogVerbosityLevel` hodnotu na `1` .

## <a name="see-also"></a>Viz také
- [Řešení potíží s nasazeními ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)