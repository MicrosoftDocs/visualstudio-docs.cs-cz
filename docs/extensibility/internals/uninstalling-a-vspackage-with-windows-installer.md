---
title: Odinstalace balíčku VSPackage s Instalační službou systému Windows | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: fee88e895d40d42114eaf53422503524594b485f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704280"
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>Odinstalace balíčku VSPackage pomocí Instalační služby systému Windows
Z větší části, Windows Installer můžete odinstalovat VSPackage jen tím, že "vrátit" to, co udělal pro instalaci VSPackage. Vlastní akce popsané v [příkazy, které musí být spuštěny po instalaci](../../extensibility/internals/commands-that-must-be-run-after-installation.md) musí být spuštěna po odinstalaci také. Vzhledem k tomu, že volání devenv.exe dojít těsně před InstallFinalize standardní akce pro instalaci i odinstalaci, customaction a InstallExecuteSequence položky tabulky slouží oba případy.

> [!NOTE]
> Spusťte `devenv /setup` po odinstalaci balíčku MSI.

 Obecně platí, že pokud přidáte vlastní akce do balíčku Instalační služby systému Windows, je nutné tyto akce zpracovat během odinstalace a vrácení zpět. Pokud přidáte vlastní akce pro vlastní registraci vspackage, například, musíte přidat vlastní akce zrušit registraci, taky.

> [!NOTE]
> Je možné, aby uživatel nainstalovat VSPackage a potom odinstalovat verze, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] s nimiž je integrován. Můžete zajistit, že vaše VSPackage odinstalace funguje v tomto scénáři odstraněním vlastní [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]akce, které spouštějí kód se závislostmi na .

## <a name="handling-launch-conditions-at-uninstall-time"></a>Podmínky spuštění při odinstalaci
 Standardní akce LaunchConditions přečte řádky TableCondition tabulka zobrazit chybové zprávy, pokud podmínky nejsou splněny. Vzhledem k tomu, že podmínky spuštění se obvykle používají k zajištění splnění systémových `NOT Installed`požadavků, můžete obecně přeskočit podmínky spuštění během odinstalace přidáním podmínky , do řádku LaunchConditions v tabulce LaunchCondition.

 Alternativou je `OR Installed` přidat ke spuštění podmínky, které nejsou důležité při odinstalaci. Tím zajistíte, že podmínka bude vždy pravdivá během odinstalace, a proto se nezobrazí chybová zpráva o stavu spuštění.

> [!NOTE]
> `Installed`Je vlastnost, kterou Instalační služba systému Windows nastavuje, když zjistí, že váš balíček VSPackage již byl v systému nainstalován.

## <a name="see-also"></a>Viz také
- [Instalační služba systému Windows](https://msdn.microsoft.com/library/187d8965-c79d-4ecb-8689-10930fa8b3b5)
- [Zjištění požadavků na systém](../../extensibility/internals/detecting-system-requirements.md)
