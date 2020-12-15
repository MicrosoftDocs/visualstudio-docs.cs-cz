---
title: Odinstalace VSPackage pomocí Instalační služba systému Windows | Microsoft Docs
description: Instalační služba systému Windows může odinstalovat VSPackage pomocí reverzní instalace. Naučte se pracovat s vlastními akcemi v balíčku Instalační služba systému Windows.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f78f27a3b2b2607f04a61352b543774f8b59e88c
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97488151"
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>Odinstalace balíčku VSPackage pomocí Instalační služby systému Windows
Ve většině případů Instalační služba systému Windows může odinstalovat VSPackage pouhým "zrušením", co bylo nutné k instalaci sady VSPackage. Vlastní akce popsané v [příkazech, které musí být spuštěny po instalaci,](../../extensibility/internals/commands-that-must-be-run-after-installation.md) musí být spuštěny i po odinstalaci. Vzhledem k tomu, že volání devenv.exe nastávají těsně před standardní akcí volán InstallFinalize pro instalaci i odinstalaci, poskytují položky tabulky CustomAction a InstallExecuteSequence v obou případech.

> [!NOTE]
> Spustit `devenv /setup` po odinstalaci balíčku MSI.

 Obecně platí, že pokud do balíčku Instalační služba systému Windows přidáte vlastní akce, musíte tyto akce zpracovat během odinstalace a vrácení zpět. Pokud přidáte vlastní akce pro vlastní registraci sady VSPackage, například musíte přidat vlastní akce a zrušit tak jejich registraci.

> [!NOTE]
> Uživatel může nainstalovat VSPackage a pak odinstalovat verze nástroje, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se kterými je integrovaný. Můžete zajistit, aby odinstalace VSPackage v tomto scénáři fungovala tím, že eliminuje vlastní akce, které spouštějí kód se závislostmi na [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="handling-launch-conditions-at-uninstall-time"></a>Zpracování podmínek spuštění v době odinstalace
 Standardní akce LaunchConditions přečte řádky tabulky LaunchCondition, aby zobrazila chybové zprávy, pokud nejsou splněny podmínky. Vzhledem k tomu, že podmínky spuštění se obecně používají k zajištění splnění požadavků na systém, můžete při odinstalaci obvykle vynechat podmínky spuštění, a to tak, že `NOT Installed` do řádku LaunchConditions tabulky LaunchCondition přidáte podmínku.

 Alternativou je přidat `OR Installed` ke spouštěcím podmínkám, které během odinstalace nejsou důležité. Tím je zajištěno, že při odinstalaci bude podmínka vždy pravdivá, a proto se nezobrazí chybová zpráva podmínky spuštění.

> [!NOTE]
> `Installed` je vlastnost Instalační služba systému Windows sady, když zjistí, že je váš VSPackage již v systému nainstalován.

## <a name="see-also"></a>Viz také
- [Instalační služba systému Windows](/previous-versions/ee231230(v=vs.100))
- [Zjištění požadavků na systém](../../extensibility/internals/detecting-system-requirements.md)