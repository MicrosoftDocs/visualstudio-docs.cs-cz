---
title: Zjišťují se požadavky na systém | Microsoft Docs
description: Naučte se, jak nakonfigurovat Microsoft Instalační služba systému Windows pro detekci požadavků na systém, jako je třeba edice sady Visual Studio, která je nainstalovaná.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- setup, VSPackages
- launch conditions
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c4befcf3950c41beba2440e6f023983269137b1f
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329806"
---
# <a name="detect-system-requirements"></a>Zjistit požadavky na systém
VSPackage nemůže fungovat, pokud není nainstalována aplikace Visual Studio. Když použijete Microsoft Instalační služba systému Windows ke správě instalace VSPackage, můžete nakonfigurovat instalační program, aby zjistil, jestli je nainstalovaná aplikace Visual Studio. Můžete ji také nakonfigurovat tak, aby zkontrolovala, jestli v systému nejsou jiné požadavky, třeba na konkrétní verzi Windows nebo konkrétní velikost paměti RAM.

## <a name="detect-visual-studio-editions"></a>Zjistit edice sady Visual Studio
 Chcete-li zjistit, zda je nainstalována edice sady Visual Studio, ověřte, zda je **Install** hodnota klíč registru instalace *(REG_DWORD) 1* v příslušné složce, jak je uvedeno v následující tabulce. Všimněte si, že je v hierarchii edice sady Visual Studio:

1. Enterprise

2. Professional

3. Komunita

Když je nainstalovaná novější edice, přidají se klíče registru pro tuto edici i pro předchozí edice. To znamená, že pokud je verze Enterprise Edition nainstalovaná, **instalační** klíč se nastaví na *1* pro Enterprise a také na edice Professional a Community. Proto je nutné zaškrtnout pouze nejnovější edici, kterou potřebujete.

> [!NOTE]
> V 64 bitové verzi editoru registru se v části **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\\** zobrazí 32 bitové klíče. Klíče sady Visual Studio jsou pod **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\\**.

|Produkt|Klíč|
|-------------|---------|
|Visual Studio Enterprise 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\enterprise|
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\professional|
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\community|
|Prostředí sady Visual Studio 2015 (integrovaný a izolovaný režim)|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell|

## <a name="detect-when-visual-studio-is-running"></a>Rozpoznat, kdy je spuštěná aplikace Visual Studio
 Rozhraní VSPackage nelze správně zaregistrovat, pokud je aplikace Visual Studio spuštěna při instalaci sady VSPackage. Instalační program musí zjistit, kdy je spuštěná aplikace Visual Studio, a pak zamítnout instalaci programu. Instalační služba systému Windows neumožňují použití položek tabulky k povolení takového zjišťování. Místo toho je nutné vytvořit vlastní akci, a to následujícím způsobem: pomocí `EnumProcesses` funkce zjistíte *devenv.exe* proces a potom buď nastavte instalační vlastnost, která se používá v podmínce spuštění, nebo podmíněně zobrazí dialogové okno s výzvou, aby uživatel zavřel sadu Visual Studio.

## <a name="see-also"></a>Viz také
- [Instalace VSPackage pomocí Instalační služba systému Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
