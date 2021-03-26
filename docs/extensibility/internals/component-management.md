---
title: Správa součástí | Microsoft Docs
description: Naučte se spravovat Instalační služba systému Windows komponenty při vytváření instalačního programu sady VSPackage v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], components
- installation [Visual Studio SDK], file management
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9767af4c30957111526303600f9e8eda815b42f0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057088"
---
# <a name="component-management"></a>Správa součástí
Jednotky úloh v Instalační služba systému Windows jsou označovány jako Instalační služba systému Windows komponenty (někdy označované jako WICs nebo pouze komponenty). Identifikátor GUID identifikuje každou součást WIC, což je základní jednotka instalace a počítání odkazů pro nastavení, která používají Instalační služba systému Windows.

 I když můžete použít několik produktů k vytvoření instalačního programu sady VSPackage, Tato diskuze předpokládá použití souborů Instalační služba systému Windows (*. msi*). Při vytváření instalačního programu je nutné správně spravovat nasazení souboru, aby se vždy nastalo správný počet odkazů. V důsledku toho nebudou různé verze produktu v kombinaci scénářů instalace a odinstalace navzájem narušovat ani přerušovat.

 V Instalační služba systému Windows probíhá počítání odkazů na úrovni komponenty. Své prostředky, soubory, položky registru a tak dále je nutné pečlivě uspořádat do komponent. Existují i další úrovně organizace, jako jsou moduly, funkce a produkty, které můžou pomáhat v různých scénářích. Další informace najdete v tématu [základy Instalační služba systému Windows](../../extensibility/internals/windows-installer-basics.md).

## <a name="guidelines-of-authoring-setup-for-side-by-side-installation"></a>Pokyny k vytváření nastavení pro souběžnou instalaci

- Vytváření souborů a klíčů registru, které jsou sdíleny mezi verzemi, do jejich vlastních komponent.

     Díky tomu je můžete snadno využívat v další verzi. Například zadejte knihovny, které jsou registrovány globálně, přípony souborů, další položky zaregistrované v **HKEY_CLASSES_ROOT** atd.

- Seskupte sdílené součásti do samostatných slučovacích modulů.

     Tato strategie vám pomůže vytvořit správně pro souběžnou instalaci.

- Nainstalujte sdílené soubory a klíče registru pomocí stejné Instalační služba systému Windows komponenty napříč verzemi.

     Použijete-li jinou součást, soubory a položky registru se odinstalují, když se odinstaluje jedna verze VSPackage, ale je stále nainstalován jiný VSPackage.

- Nepoužívejte kombinaci verzí a sdílených položek ve stejné součásti.

     Díky tomu není možné instalovat sdílené položky do globálního umístění a z položek se správou verzí do izolovaných umístění.

- Nemusíte mít sdílené klíče registru, které odkazují na soubory se správou verzí.

     Pokud to uděláte, budou se sdílené klíče přepsat při instalaci další verze VSPackage. Po odebrání druhé verze se zobrazí soubor, na který se klíč odkazuje.

## <a name="see-also"></a>Viz také
- [Volba mezi Shared a VSPackage se správou verzí](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)
- [Scénáře instalace VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)
