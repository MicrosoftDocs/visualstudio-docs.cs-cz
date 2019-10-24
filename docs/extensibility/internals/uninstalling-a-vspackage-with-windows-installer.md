---
title: Odinstalace VSPackage pomocí Instalační služba systému Windows | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a8e92937e848d124c18dc91b9bdfa0f020f27f20
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722133"
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>Odinstalace balíčku VSPackage pomocí Instalační služby systému Windows
Ve většině případů Instalační služba systému Windows může odinstalovat VSPackage pouhým "zrušením", co bylo nutné k instalaci sady VSPackage. Vlastní akce popsané v [příkazech, které musí být spuštěny po instalaci,](../../extensibility/internals/commands-that-must-be-run-after-installation.md) musí být spuštěny i po odinstalaci. Vzhledem k tomu, že volání nástroje devenv. exe proběhne těsně před standardní akcí volán InstallFinalize pro instalaci i odinstalaci, poskytují položky tabulky CustomAction a InstallExecuteSequence v obou případech.

> [!NOTE]
> Po odinstalaci balíčku MSI spusťte `devenv /setup`.

 Obecně platí, že pokud do balíčku Instalační služba systému Windows přidáte vlastní akce, musíte tyto akce zpracovat během odinstalace a vrácení zpět. Pokud přidáte vlastní akce pro vlastní registraci sady VSPackage, například musíte přidat vlastní akce a zrušit tak jejich registraci.

> [!NOTE]
> Uživatel může nainstalovat VSPackage a pak odinstalovat verze [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], se kterými je integrovaná. Můžete zajistit, aby odinstalace VSPackage v tomto scénáři fungovala tím, že eliminuje vlastní akce, které spouštějí kód se závislostmi na [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="handling-launch-conditions-at-uninstall-time"></a>Zpracování podmínek spuštění v době odinstalace
 Standardní akce LaunchConditions přečte řádky tabulky LaunchCondition, aby zobrazila chybové zprávy, pokud nejsou splněny podmínky. Vzhledem k tomu, že podmínky spuštění se obecně používají k zajištění toho, že jsou splněny požadavky na systém, můžete při odinstalaci obvykle vynechat podmínky spuštění, a to přidáním podmínky, `NOT Installed`, do řádku LaunchConditions tabulky LaunchCondition.

 Alternativou je přidání `OR Installed` ke spouštěcím podmínkám, které během odinstalace nejsou důležité. Tím je zajištěno, že při odinstalaci bude podmínka vždy pravdivá, a proto se nezobrazí chybová zpráva podmínky spuštění.

> [!NOTE]
> `Installed` je vlastnost Instalační služba systému Windows sady, když zjistí, že vaše sada VSPackage již byla v systému nainstalována.

## <a name="see-also"></a>Viz také:
- [Instalační služba systému Windows](https://msdn.microsoft.com/library/187d8965-c79d-4ecb-8689-10930fa8b3b5)
- [Zjištění požadavků na systém](../../extensibility/internals/detecting-system-requirements.md)