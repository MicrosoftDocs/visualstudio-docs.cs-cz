---
title: Zjišťují se požadavky na systém | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- setup, VSPackages
- launch conditions
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
caps.latest.revision: 51
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 467554b8e50878bcdf1029e4792bbf168a09fa11
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64788469"
---
# <a name="detecting-system-requirements"></a>Zjištění požadavků na systém
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

VSPackage nemůže fungovat, pokud není nainstalována aplikace Visual Studio. Když použijete Microsoft Instalační služba systému Windows ke správě instalace VSPackage, můžete nakonfigurovat instalační program, aby zjistil, jestli je nainstalovaná aplikace Visual Studio. Můžete ji také nakonfigurovat tak, aby zkontrolovala, jestli v systému nejsou jiné požadavky, třeba na konkrétní verzi Windows nebo konkrétní velikost paměti RAM.  
  
## <a name="detecting-visual-studio-editions"></a>Zjišťují se edice sady Visual Studio.  
 Chcete-li zjistit, zda je nainstalována edice sady Visual Studio, ověřte, zda je hodnota klíč registru instalace (REG_DWORD) 1 v příslušné složce, jak je uvedeno v následující tabulce. Všimněte si, že je v hierarchii edice sady Visual Studio:  
  
1. Enterprise  
  
2. Professional  
  
3. Komunita  
  
   Pokud je nainstalovaná edice "vyšší", přidají se klíče registru pro tuto edici i pro "nižší" edice. To znamená, že pokud je verze Enterprise Edition nainstalovaná, instalační klíč se nastaví na 1 pro Enterprise i pro edice Professional a Community. Proto je nutné zaškrtnout pouze "nejvyšší" edici, kterou potřebujete.  
  
> [!NOTE]
> V 64 bitové verzi editoru registru se v části HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node zobrazí 32 bitů klíčů \\ . Klíče sady Visual Studio jsou pod HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing \\ .  
  
|Produkt|Klíč|  
|-------------|---------|  
|Visual Studio Enterprise 2015|HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\enterprise|  
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\professional|  
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\community|  
|Prostředí sady Visual Studio 2015 (integrovaný a izolovaný režim)|HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell|  
  
## <a name="detecting-when-visual-studio-is-running"></a>Zjištění, kdy běží aplikace Visual Studio  
 Rozhraní VSPackage nelze správně zaregistrovat, pokud je aplikace Visual Studio spuštěna při instalaci sady VSPackage. Instalační program musí zjistit, kdy je spuštěná aplikace Visual Studio, a pak zamítnout instalaci programu. Instalační služba systému Windows neumožňují použití položek tabulky k povolení takového zjišťování. Místo toho je nutné vytvořit vlastní akci, a to následujícím způsobem: pomocí `EnumProcesses` funkce zjistíte devenv.exe proces a potom buď nastavte instalační vlastnost, která se používá v podmínce spuštění, nebo podmíněně zobrazí dialogové okno s výzvou, aby uživatel zavřel sadu Visual Studio.  
  
## <a name="see-also"></a>Viz také  
 [Instalace balíčků VSPackage pomocí Instalační služby systému Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
