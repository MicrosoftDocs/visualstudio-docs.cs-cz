---
title: Zadat podrobné soubory protokolu (nasazení ClickOnce)
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
ms.openlocfilehash: 54c90f6a544607e78dd8f294bfc307bc87377b70
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808708"
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>Postupy: určení podrobných souborů protokolu pro ClickOnce nasazení
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] udržuje soubory protokolu aktivit pro všechna nasazení. Tyto protokoly dokumentují informace týkající se instalace, inicializace, aktualizace a odinstalace [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazení. Chcete-li zvýšit podrobnosti, které [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] zapisuje do těchto souborů protokolu, použijte Editor registru (*regedit.exe*) a určete úroveň podrobností.

> [!CAUTION]
> Pokud používáte Editor registru nesprávně, může dojít k vážným problémům, které mohou vyžadovat přeinstalaci operačního systému. Editor registru použijte na vlastní riziko.

 Následující postup popisuje, jak zadat úroveň podrobností pro [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] soubory protokolu pro aktuálního uživatele. Chcete-li snížit úroveň podrobností, odeberte tuto hodnotu registru.

### <a name="to-specify-verbose-log-files"></a>Určení podrobných souborů protokolu

1. Otevřete *Regedit.exe*.

2. Přejděte k uzlu **HKEY_CURRENT_USER \software\classes\software\microsoft\windows\currentversion\deployment**.

3. V případě potřeby vytvořte novou řetězcovou hodnotu s názvem `LogVerbosityLevel` .

4. Nastavte `LogVerbosityLevel` hodnotu na `1` .

## <a name="see-also"></a>Viz také
- [Řešení potíží s nasazeními ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)