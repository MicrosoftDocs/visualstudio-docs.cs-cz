---
title: Nástroj CreateExpInstance | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6a6b302976495e6067fad14317856cda4ac4625f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709244"
---
# <a name="createexpinstance-utility"></a>Nástroj CreateExpInstance
Pomocí nástroje **CreateExpInstance** vytvořte, resetujte nebo odstraňte experimentální instanci sady Visual Studio. Experimentální instanci můžete použít k ladění a testování rozšíření sady Visual Studio beze změny základního produktu.

## <a name="syntax"></a>Syntaxe

```
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix
```

## <a name="parameters"></a>Parametry
 **/Vytvořit** Vytvoří experimentální instanci.

 **/Obnovit** Odstraní experimentální instanci a potom vytvoří novou.

 **/Vyčistit** Odstraní experimentální instanci.

 **/VSInstance** Název adresáře, který obsahuje základní instanci sady Visual Studio ke kopírování.

 **/RootSuffix** Přípona pro připojení k názvu adresáře instance experimentu.

## <a name="remarks"></a>Poznámky
 Při práci na rozšíření sady Visual Studio můžete stisknutím klávesy F5 otevřít výchozí experimentální instanci a nainstalovat aktuální rozšíření. Pokud není k dispozici žádná experimentální instance, Visual Studio vytvoří ten, který má výchozí nastavení.

 Výchozí umístění experimentální instance závisí na čísle verze sady Visual Studio. Například pro Visual Studio 2015 je umístění *%localappdata%\Microsoft\VisualStudio\14.0Exp\\*. Všechny soubory v umístění adresáře jsou považovány za součást této instance. Žádné další experimentální instance nebudou načteny aplikací Visual Studio, pokud nebude název adresáře změněn na výchozí umístění.

 Visual Studio nemá přístup k systémovému registru při otevření instance experimentální. To se liší od předchozích verzí sady Visual Studio, které používaly experimentální verzi podregistru registru.

 Nástroj **CreateExpInstance** nahrazuje nástroj **VsRegEx.**

 Následující příklad obnoví výchozí experimentální instanci sady Visual Studio:

 **CreateExpInstance.exe /Reset /VSInstance=14.0 /RootSuffix=Exp**

## <a name="see-also"></a>Viz také
- [Balíčky VSPackage](../../extensibility/internals/vspackages.md)
