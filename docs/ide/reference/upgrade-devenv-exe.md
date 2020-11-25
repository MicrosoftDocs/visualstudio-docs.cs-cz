---
title: -Upgrade (devenv.exe)
description: Naučte se, jak použít přepínač příkazového řádku devenv pro upgrade k aktualizaci souboru řešení a všech jeho souborů projektu, nebo souboru projektu, na aktuální formáty sady Visual Studio pro tyto soubory.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /upgrade Devenv switch
- Devenv, /upgrade switch
- upgrade Devenv switch
ms.assetid: 3468045c-5cc9-4157-9a9d-622452145d27
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2bb0565783efb27cf4194bb25982ee0f717be776
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040950"
---
# <a name="upgrade-devenvexe"></a>/Upgrade (devenv.exe)

Aktualizuje soubor řešení a všechny jeho soubory projektu nebo zadaný soubor projektu na aktuální formáty sady Visual Studio pro tyto soubory.

## <a name="syntax"></a>Syntaxe

```shell
devenv {SolutionFile|ProjectFile} /Upgrade [/Out OutputFilename]
```

## <a name="arguments"></a>Argumenty

- *Souborřešení*

  Vyžaduje se, pokud upgradujete celé řešení a jeho projekty. Cesta a název souboru řešení. Můžete zadat pouze název souboru řešení nebo úplnou cestu a název souboru řešení. Pokud složka nebo soubor s názvem ještě neexistují, vytvoří se.

- *ProjectFile*

  Vyžaduje se, pokud upgradujete jeden projekt. Cesta a název souboru projektu v rámci řešení. Můžete zadat pouze název souboru projektu nebo úplnou cestu a název souboru projektu. Pokud složka nebo soubor s názvem ještě neexistují, vytvoří se.

- `/Out`*OutputFilename*

  Nepovinný parametr. Název souboru, do kterého chcete odeslat výstup nástroje. Pokud soubor již existuje, nástroj připojí výstup na konec souboru.

## <a name="remarks"></a>Poznámky

Zálohy se automaticky vytvoří a zkopírují do adresáře s názvem Backup vytvořeného v aktuálním adresáři.

Řešení nebo projekty se správou zdrojového kódu musí být rezervovány, aby bylo možné je upgradovat.

Pomocí `/Upgrade` přepínače nedojde k otevření sady Visual Studio. Výsledky upgradu lze zobrazit v sestavě upgradu pro vývojový jazyk řešení nebo projektu. Nevrátí se žádné informace o chybě ani o použití. Další informace o upgradu projektů v aplikaci Visual Studio naleznete v tématu [port, migrace a upgrade projektů sady Visual Studio](../../porting/port-migrate-and-upgrade-visual-studio-projects.md).

## <a name="example"></a>Příklad

Tento příklad upgraduje soubor řešení s názvem "MyProject. sln".

```shell
devenv "%USERPROFILE%\source\repos\MyProject\MyProject.sln" /upgrade
```

## <a name="see-also"></a>Viz také

- [Devenv – přepínače příkazového řádku](../../ide/reference/devenv-command-line-switches.md)
