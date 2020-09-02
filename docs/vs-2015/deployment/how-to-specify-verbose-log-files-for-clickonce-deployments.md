---
title: 'Postupy: určení podrobných souborů protokolu pro nasazení ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- logs, ClickOnce deployment
- ClickOnce deployment, logging
ms.assetid: 0807a28d-2e40-4a51-ab10-308d808ded6b
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 78fa278952004348e035a675a1e159b2164285b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64832931"
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>Postupy: Určení souborů podrobného protokolování pro nasazení ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] udržuje soubory protokolu aktivit pro všechna nasazení. Tyto protokoly dokumentují informace týkající se instalace, inicializace, aktualizace a odinstalace [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazení. Chcete-li zvýšit podrobnosti, které [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] zapisuje do těchto souborů protokolu, použijte Editor registru (**regedit.exe**) a určete úroveň podrobností.  
  
> [!CAUTION]
> Pokud používáte Editor registru nesprávně, může dojít k vážným problémům, které mohou vyžadovat přeinstalaci operačního systému. Editor registru použijte na vlastní riziko.  
  
 Následující postup popisuje, jak zadat úroveň podrobností pro [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] soubory protokolu pro aktuálního uživatele. Chcete-li snížit úroveň podrobností, odeberte tuto hodnotu registru.  
  
### <a name="to-specify-verbose-log-files"></a>Určení podrobných souborů protokolu  
  
1. Otevřete **Regedit.exe**.  
  
2. Přejděte k uzlu `HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment` .  
  
3. V případě potřeby vytvořte novou řetězcovou hodnotu s názvem `LogVerbosityLevel` .  
  
4. Nastavte `LogVerbosityLevel` hodnotu na `1` .  
  
## <a name="see-also"></a>Viz také  
 [Řešení potíží s nasazením ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)
