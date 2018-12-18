---
title: -Upgrade (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /upgrade Devenv switch
- Devenv, /upgrade switch
- upgrade Devenv switch
ms.assetid: 3468045c-5cc9-4157-9a9d-622452145d27
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ba94a599c119d537efb90b29c1c2ec0084ace447
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948332"
---
# <a name="upgrade-devenvexe"></a>/Upgrade (devenv.exe)
Aktualizuje soubor řešení a všechny jeho soubory projektu nebo zadaný pro aktuální soubor projektu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] formáty pro tyto soubory.

## <a name="syntax"></a>Syntaxe

```cmd
devenv SolutionFile | ProjectFile /upgrade
```

## <a name="arguments"></a>Arguments
 `SolutionFile`

 Povinné, pokud upgradujete celé řešení a jeho projekty. Cesta a název souboru řešení. Můžete zadat pouze název souboru řešení nebo úplnou cestu a název souboru řešení. Pokud složka nebo soubor s názvem ještě neexistuje, vytvoří se.

 `ProjectFile`

 Povinné, pokud upgradujete jeden projekt. Cesta a název souboru projektu v rámci řešení. Můžete zadat pouze název souboru projektu nebo úplnou cestu a název souboru projektu. Pokud složka nebo soubor s názvem ještě neexistuje, vytvoří se.

## <a name="remarks"></a>Poznámky
 Zálohy jsou automaticky vytvořeny a zkopírován do adresáře s názvem Zálohování, který je vytvořen v aktuálním adresáři.

 Řešení se spravovanými zdroji nebo projekty musí být rezervován dříve, než je možné upgradovat.

 Použití `/upgrade` přepínač nespustí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Výsledky upgradu lze zobrazit v sestavě upgradu pro vývojový jazyk řešení nebo projektu. Vrátí se žádné informace o chybě nebo použití. Další informace o upgradu projektů v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], naleznete v tématu [Port, migrace a Upgrade projektů sady Visual Studio](../../porting/port-migrate-and-upgrade-visual-studio-projects.md).

## <a name="example"></a>Příklad
 V tomto příkladu upgraduje soubor řešení s názvem "MyProject.sln" ve výchozí složce pro [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] řešení.

```cmd
devenv "MyProject.sln" /upgrade
```

## <a name="see-also"></a>Viz také

- [Přepínače příkazového řádku nástroje devenv](../../ide/reference/devenv-command-line-switches.md)