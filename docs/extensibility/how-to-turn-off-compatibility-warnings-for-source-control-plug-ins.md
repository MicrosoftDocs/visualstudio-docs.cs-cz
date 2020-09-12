---
title: Vypnout upozornění pro moduly plug-in správy zdrojového kódu
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 406d063bd2df6dd1d831c3a8220d8d513596a79a
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2020
ms.locfileid: "90037182"
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Postupy: vypnutí upozornění kompatibility pro moduly plug-in správy zdrojového kódu

Uživatel může při využívání správy zdrojového kódu v nástroji zobrazit několik upozornění na kompatibilitu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Uvedená upozornění závisí na možnostech modulu plug-in správy zdrojových kódů a lze je zakázat, jak je uvedeno zde.

### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>Chcete-li zakázat upozornění: "Chcete-li zajistit optimální integraci správy zdrojového kódu se sadou Visual Studio"

- Nastavte následující položku registru (Pokud je to nutné, přidejte hodnotu):

   **HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = DWORD: 00000001**

   Toto upozornění se zobrazí pro všechny [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] nemodulované moduly plug-in.

### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>Zakázání upozornění: "nainstalovaný poskytovatel správy zdrojových kódů nepodporuje všechny funkce"

- Nastavte následující dvě hodnoty registru (v případě potřeby přidejte hodnoty):

     **HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider = DWORD: 00000000**

    **HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = DWORD: 00000001**

     Toto upozornění se zobrazí, pokud modul plug-in správy zdrojových kódů explicitně nepodporuje Vícenásobný přístup pro více projektů (tj. Pokud je možné vrátit se změnami pouze jeden soubor a projekt v jednom okamžiku).

     Je nejlepší podporovat Vícenásobný přístup ( `SCC_CAP_REENTRANT` schopnost). uděláte to tak, že se toto upozornění odstraní. Pokud však tato podpora není možná, je možné nastavit tyto položky registru.

## <a name="see-also"></a>Viz také

- [Příznaky schopností](../extensibility/capability-flags.md)
