---
title: Registrace VSPackage | Microsoft Docs
description: Soubor. pkgdef obsahuje informace, které by jinak bylo přidáno do systémového registru. Přečtěte si, jak Visual Studio používá soubory. pkgdef pro popis/vyhledání VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9e2ed8d7c376f7d9f23e06786fefc1a955ebea3a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069462"
---
# <a name="registering-vspackages"></a>Registrace balíčků VSPackage
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] spoléhá na soubory. pkgdef pro popis a vyhledání VSPackage. Soubor. pkgdef obsahuje všechny registrační informace, které by jinak byly přidány do systémového registru. Spravované sady VSPackage jsou registrovány přidáním atributů ke zdrojovému kódu a následným spuštěním [nástroje CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md) ve výsledném sestavení pro vygenerování souboru. pkgdef.

## <a name="in-this-section"></a>V tomto oddílu
- [Specifikace umístění souboru balíčku VSPackage pro prostředí sady VS](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)

 Popisuje cestu načítání pro VSPackage.

- [Registrace a zrušení registrace rozšíření VSPackages](../../extensibility/registering-and-unregistering-vspackages.md)

 Vysvětluje, jak zaregistrovat VSPackage.
