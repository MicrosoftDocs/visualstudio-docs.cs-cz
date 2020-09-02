---
title: Odinstalace VSPackage pomocí Instalační služba systému Windows | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9a309779850dd33b77b426beb5627f61c40c2c4f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675232"
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>Odinstalace balíčku VSPackage pomocí Instalační služby systému Windows
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ve většině případů Instalační služba systému Windows může odinstalovat VSPackage pouhým "zrušením", co bylo nutné k instalaci sady VSPackage. Vlastní akce popsané v [příkazech, které musí být spuštěny po instalaci,](../../extensibility/internals/commands-that-must-be-run-after-installation.md) musí být spuštěny i po odinstalaci. Vzhledem k tomu, že volání devenv.exe nastávají těsně před standardní akcí volán InstallFinalize pro instalaci i odinstalaci, poskytují položky tabulky CustomAction a InstallExecuteSequence v obou případech.  
  
> [!NOTE]
> Spustit `devenv /setup` po odinstalaci balíčku MSI.  
  
 Obecně platí, že pokud do balíčku Instalační služba systému Windows přidáte vlastní akce, musíte tyto akce zpracovat během odinstalace a vrácení zpět. Pokud přidáte vlastní akce pro vlastní registraci sady VSPackage, například musíte přidat vlastní akce a zrušit tak jejich registraci.  
  
> [!NOTE]
> Uživatel může nainstalovat VSPackage a pak odinstalovat verze nástroje, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] se kterými je integrovaný. Můžete zajistit, aby odinstalace VSPackage v tomto scénáři fungovala tím, že eliminuje vlastní akce, které spouštějí kód se závislostmi na [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="handling-launch-conditions-at-uninstall-time"></a>Zpracování podmínek spuštění v době odinstalace  
 Standardní akce LaunchConditions přečte řádky tabulky LaunchCondition, aby zobrazila chybové zprávy, pokud nejsou splněny podmínky. Vzhledem k tomu, že podmínky spuštění se obecně používají k zajištění splnění požadavků na systém, můžete při odinstalaci obvykle vynechat podmínky spuštění, a to tak, že `NOT Installed` do řádku LaunchConditions tabulky LaunchCondition přidáte podmínku.  
  
 Alternativou je přidat `OR Installed` ke spouštěcím podmínkám, které během odinstalace nejsou důležité. Tím je zajištěno, že při odinstalaci bude podmínka vždy pravdivá, a proto se nezobrazí chybová zpráva podmínky spuštění.  
  
> [!NOTE]
> `Installed` je vlastnost Instalační služba systému Windows sady, když zjistí, že je váš VSPackage již v systému nainstalován.  
  
## <a name="see-also"></a>Viz také  
 [Instalační služba systému Windows](https://msdn.microsoft.com/187d8965-c79d-4ecb-8689-10930fa8b3b5)   
 [Zjištění požadavků na systém](../../extensibility/internals/detecting-system-requirements.md)
