---
title: Zjišťování systémových požadavků | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 9ab254df5d53f379704128d8860b8d7fe5655bae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708737"
---
# <a name="detect-system-requirements"></a>Zjištění systémových požadavků
Balíček VSPackage nemůže fungovat, pokud není nainstalována sada Visual Studio. Při použití Instalační služby systému Microsoft Windows ke správě instalace balíčku VSPackage můžete nakonfigurovat instalační program tak, aby zjistil, zda je nainstalována sada Visual Studio. Můžete jej také nakonfigurovat tak, aby zkontroloval další požadavky systému, například konkrétní verzi systému Windows nebo určité množství paměti RAM.

## <a name="detect-visual-studio-editions"></a>Detekce edic sady Visual Studio
 Chcete-li zjistit, zda je nainstalována edice sady Visual Studio, ověřte, zda je hodnota klíče registru **Install** *(REG_DWORD) 1* v příslušné složce, jak je uvedeno v následující tabulce. Všimněte si, že existuje hierarchie edic Sady Visual Studio:

1. Enterprise

2. Professional

3. Komunita

Pokud je nainstalována novější edice, jsou přidány klíče registru pro tuto edici i pro dřívější edice. To znamená, že pokud je nainstalována edice Enterprise, je **instalační** klíč nastaven na *1* pro enterprise a také pro edice Professional a Community. Proto je třeba zkontrolovat pouze nejnovější vydání, které potřebujete.

> [!NOTE]
> V 64bitové verzi editoru registru jsou 32bitové klíče zobrazeny pod **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\\**. Klávesy sady Visual Studio jsou pod **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\\**.

|Produkt|Klíč|
|-------------|---------|
|Visual Studio Enterprise 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\Enterprise|
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servis\14.0\Professional|
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\community|
|Visual Studio 2015 Shell (integrované a izolované)|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell|

## <a name="detect-when-visual-studio-is-running"></a>Zjištění, když je spuštěna sada Visual Studio
 Váš VSPackage nelze zaregistrovat správně, pokud je spuštěna visual studio při instalaci VSPackage. Instalační program musí zjistit, kdy je spuštěna sada Visual Studio a potom odmítnout instalaci programu. Instalační služba systému Windows neumožňuje použití položek tabulky k povolení takového zjišťování. Místo toho je nutné vytvořit vlastní akci takto: Pomocí `EnumProcesses` funkce zjišťujte proces *devenv.exe* a potom nastavte vlastnost instalačního programu, která se používá v podmínce spuštění, nebo podmíněně zobrazte dialogové okno, které vyzve uživatele k zavření sady Visual Studio.

## <a name="see-also"></a>Viz také
- [Instalace balíčků VSPackages s Instalační službou systému Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
