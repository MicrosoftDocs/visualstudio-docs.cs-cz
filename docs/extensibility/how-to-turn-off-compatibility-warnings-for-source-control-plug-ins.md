---
title: Vypnutí upozornění kompatibility pro ovládací prvek moduly plug-in zdrojového kódu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b1dca06ca82e467080f4bcd88a3b10c691345344
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49888343"
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Postupy: vypnutí upozornění kompatibility pro ovládací prvek moduly plug-in zdrojového kódu
Při použití správy zdrojového kódu v se uživatel může zobrazit upozornění na kompatibilitu s několika [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Upozornění zobrazí závisí na možnostech modul plug-in správy zdrojového kódu a může být vypnuta, protože podrobné tady.  
  
### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>Toto upozornění zakážete: "aby integrace správy optimální zdrojového kódu pomocí sady Visual Studio"  
  
- Nastavte následující položku registru (přidání hodnota v případě potřeby):  
  
   **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = DWORD: 00000001**  
  
   Toto upozornění se zobrazí u všech jinou hodnotu než[!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] moduly plug-in.  
  
### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>Toto upozornění zakážete: "nainstalovaný poskytovatel správy zdrojů nepodporuje všechny funkce.  
  
-   Nastavte následující hodnoty registru dva (přidání hodnot v případě potřeby):  
  
     **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider = DWORD: 00000000**  
  
    **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = DWORD: 00000001**  
  
     Toto upozornění se zobrazí, pokud modul plug-in správy zdrojového kódu nepodporuje explicitně opětovný vstup pro více projektů (tj. Pokud můžete zkontrolovat v pouze jeden soubor a projekt současně).  
  
     Je nejvhodnější pro podporu opětovný vstup (`SCC_CAP_REENTRANT` schopností); tím se již toto upozornění. Nicméně pokud tato podpora není možné, můžete nastavit tyto položky registru.  
  
## <a name="see-also"></a>Viz také:  
 [Příznaky funkcí](../extensibility/capability-flags.md)