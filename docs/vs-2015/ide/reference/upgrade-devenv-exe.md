---
title: -Upgrade (devenv. exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /upgrade Devenv switch
- Devenv, /upgrade switch
- upgrade Devenv switch
ms.assetid: 3468045c-5cc9-4157-9a9d-622452145d27
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 24bb6160f9895f129c4d7d36c2b0aa8a56ca282a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657903"
---
# <a name="upgrade-devenvexe"></a>/Upgrade (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Aktualizuje soubor řešení a všechny jeho soubory projektu nebo zadaný soubor projektu na aktuální [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] formáty pro tyto soubory.

## <a name="syntax"></a>Syntaxe

```
devenv SolutionFile | ProjectFile /upgrade
```

## <a name="arguments"></a>Arguments
 `SolutionFile` nutné, pokud upgradujete celé řešení a jeho projekty. Cesta a název souboru řešení. Můžete zadat pouze název souboru řešení nebo úplnou cestu a název souboru řešení. Pokud složka nebo soubor s názvem ještě neexistuje, vytvoří se.

 `ProjectFile` nutné při upgradu jednoho projektu. Cesta a název souboru projektu v rámci řešení. Můžete zadat pouze název souboru projektu nebo úplnou cestu a název souboru projektu. Pokud složka nebo soubor s názvem ještě neexistuje, vytvoří se.

## <a name="remarks"></a>Poznámky
 Zálohy se automaticky vytvoří a zkopírují do adresáře s názvem Backup, který se vytvoří v aktuálním adresáři.

 Řešení nebo projekty se správou zdrojového kódu musí být rezervovány, aby bylo možné je upgradovat.

 Použití přepínače `/upgrade` nespustí [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Výsledky upgradu lze zobrazit v sestavě upgradu pro vývojový jazyk řešení nebo projektu. Nevrátí se žádné informace o chybě ani o použití. Další informace o tom, jak upgradovat projekty v [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], naleznete v tématu [How to: Troubleshooting the neúspěšné aktualizace projektu sady Visual Studio](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md).

## <a name="example"></a>Příklad
 Tento příklad upgraduje soubor řešení s názvem "MyProject. sln" ve výchozí složce pro [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] řešení.

```
devenv "MyProject.sln" /upgrade
```

## <a name="see-also"></a>Viz také
 [Postupy: řešení potíží s neúspěšným upgradem projektu sady Visual Studio –](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md) [přepínače příkazového řádku devenv](../../ide/reference/devenv-command-line-switches.md)
