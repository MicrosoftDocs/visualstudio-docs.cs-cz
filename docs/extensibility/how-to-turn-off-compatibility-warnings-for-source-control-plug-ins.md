---
title: Vypnout upozornění na kompatibilitu modulů plug-in správy zdrojového kódu | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 22dd3821426aa1dae6265c520ddac60dd93e1c5e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710727"
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Postup: Vypnutí upozornění na kompatibilitu modulů plug-in pro řízení zdrojového kódu
Uživateli se může zobrazit několik upozornění [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]kompatibility při použití správy zdrojového kódu v . Prezentovaná upozornění závisí na možnostech modulu plug-in správy zdrojového kódu a lze je zakázat, jak je podrobně popsáno zde.

### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>Zakázání upozornění: "Zajištění optimální integrace správy zdrojového kódu s visual studio"

- Nastavte následující položku registru (v případě potřeby sečtením hodnoty):

   **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETKompatibilní = dword:00000001**

   Toto upozornění se zobrazí[!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] u všech nemodulových modulů.

### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>Zakázání upozornění: "Nainstalovaný zprostředkovatel správy zdrojového kódu nepodporuje všechny funkce"

- Nastavte následující dvě hodnoty registru (v případě potřeby sečtením hodnot):

     **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider = dword:00000000**

    **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = dword:00000001**

     Toto upozornění se zobrazí, pokud modul plug-in správy zdrojového kódu explicitně nepodporuje reentrancy pro více projektů (to znamená, pokud může sezměnami pouze jeden soubor a projekt najednou).

     To je nejlepší podporovat reentrancy (schopnost);`SCC_CAP_REENTRANT` tímto způsobem odstraníte toto upozornění. Pokud však tato podpora není možná, lze tyto položky registru nastavit.

## <a name="see-also"></a>Viz také
- [Příznaky schopností](../extensibility/capability-flags.md)
