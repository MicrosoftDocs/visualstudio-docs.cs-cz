---
title: Registrace VSPackage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b40793a5ab317b6a467e55df13302f19cec82640
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80705749"
---
# <a name="registering-vspackages"></a>Registrace balíčků VSPackage
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] spoléhá na soubory. pkgdef pro popis a vyhledání VSPackage. Soubor. pkgdef obsahuje všechny registrační informace, které by jinak byly přidány do systémového registru. Spravované sady VSPackage jsou registrovány přidáním atributů ke zdrojovému kódu a následným spuštěním [nástroje CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md) ve výsledném sestavení pro vygenerování souboru. pkgdef.

## <a name="in-this-section"></a>V tomto oddílu
- [Specifikace umístění souboru balíčku VSPackage pro prostředí sady VS](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)

 Popisuje cestu načítání pro VSPackage.

- [Registrace a zrušení registrace rozšíření VSPackages](../../extensibility/registering-and-unregistering-vspackages.md)

 Vysvětluje, jak zaregistrovat VSPackage.
