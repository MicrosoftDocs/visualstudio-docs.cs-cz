---
title: Nástroj CreateExpInstance | Microsoft Docs
description: Přečtěte si o nástroji CreateExpInstance, který umožňuje vytvořit, obnovit nebo odstranit experimentální instanci sady Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cce9bc25cb2ed820d3291ab65d94a868bb401ec9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898133"
---
# <a name="createexpinstance-utility"></a>Nástroj CreateExpInstance
Pomocí nástroje **CreateExpInstance** můžete vytvořit, obnovit nebo odstranit experimentální instanci sady Visual Studio. Experimentální instanci můžete použít k ladění a testování rozšíření sady Visual Studio, aniž byste museli měnit příslušný produkt.

## <a name="syntax"></a>Syntaxe

```
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix
```

## <a name="parameters"></a>Parametry
 **/Create** Vytvoří experimentální instanci.

 **/Reset po vyčištění** Odstraní experimentální instanci a pak vytvoří novou.

 **/Clean** Odstraní experimentální instanci.

 **/VSInstance** Název adresáře, který obsahuje základní instanci sady Visual Studio ke zkopírování.

 **/Rootsuffix** Přípona, která se má připojit k názvu adresáře experimentální instance.

## <a name="remarks"></a>Poznámky
 Když pracujete s rozšířením sady Visual Studio, můžete stisknutím klávesy F5 otevřít výchozí experimentální instanci a nainstalovat aktuální rozšíření. Pokud není k dispozici žádná experimentální instance, Visual Studio vytvoří jednu, která má výchozí nastavení.

 Výchozí umístění experimentální instance závisí na čísle verze sady Visual Studio. Například pro Visual Studio 2015 je umístění *%localappdata%\Microsoft\VisualStudio\14.0Exp \\*. Všechny soubory v umístění adresáře jsou považovány za součást této instance. Žádná další experimentální instance nebude aplikací Visual Studio načtena, pokud nebude název adresáře změněn na výchozí umístění.

 Visual Studio nepřistupuje k systémovému registru při otevření experimentální instance. To se liší od dřívějších verzí sady Visual Studio, které používaly experimentální verzi podregistru.

 Nástroj **CreateExpInstance** nahrazuje nástroj **VSRegEx** .

 V následujícím příkladu je obnovena výchozí experimentální instance sady Visual Studio:

 **CreateExpInstance.exe/reset po vyčištění/VSInstance = 14.0/RootSuffix = exp**

## <a name="see-also"></a>Viz také
- [Balíčky VSPackage](../../extensibility/internals/vspackages.md)
