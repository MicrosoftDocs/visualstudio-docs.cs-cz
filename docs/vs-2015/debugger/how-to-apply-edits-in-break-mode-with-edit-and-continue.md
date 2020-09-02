---
title: 'Postupy: použití úprav v režimu pozastavení pomocí funkce upravit a pokračovat | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
helpviewer_keywords:
- Edit and Continue [Visual Basic], applying edits in break mode
- break mode, applying code changes
- Edit and Continue, applying edits in break mode
- editing, break mode
- coding, editing in break mode
- code, editing in break mode
ms.assetid: 1eef7498-6a1f-4fba-8146-510adc6375c9
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5c04dc0ae6e5272d2544ad7436fa7ca516c9a022
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64795655"
---
# <a name="how-to-apply-edits-in-break-mode-with-edit-and-continue"></a>Postupy: Použití úprav v režimu pozastavení pomocí operace Upravit a pokračovat
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete použít příkaz Upravit a pokračovat pro úpravu kódu v režimu přerušení a pak pokračovat bez zastavení a restartování provádění.  
  
 Úpravy a pokračování nejsou k dispozici v následujících scénářích ladění:  
  
- Ladění ve smíšeném režimu (nativní/spravované)  
  
- Ladění SQL.  
  
- Ladění výpisu nástroje Dr. Watson.  
  
- Úprava kódu po neošetřené výjimce, pokud není vybrána možnost **unwind zásobníku volání při neošetřených výjimkách** .  
  
- Ladění vložené aplikace modulu runtime.  
  
- Ladění aplikace pomocí příkazu **připojit** namísto spuštění aplikace s nástrojem **Start** z nabídky **ladění** .  
  
- Ladění optimalizovaného kódu.  
  
- Ladění spravovaného kódu, pokud je cílem 64 aplikace. Pokud chcete použít příkaz Upravit a pokračovat, musíte nastavit cíl na x86. (_Project_**Vlastnosti**projektu, karta **kompilovat** , **Pokročilé nastavení kompilátoru** .)  
  
- Ladění staré verze kódu po selhání sestavení nové verze kvůli chybám sestavení.  
  
### <a name="to-edit-code-in-break-mode"></a>Úprava kódu v režimu pozastavení  
  
1. Do režimu přerušení zadejte jednu z následujících možností:  
  
    - Nastavte zarážku v kódu a pak zvolte **Spustit ladění** z nabídky **ladění** a počkejte, než aplikace dorazí na zarážku.  
  
         ani  
  
    - Spusťte ladění a v nabídce **ladění** vyberte možnost **rozdělit vše** .  
  
         ani  
  
    - Pokud dojde k výjimce, klikněte na **Povolit úpravy** v**Pomocníkovi s výjimkami**.  
  
2. Proveďte požadované a právní změny kódu.  
  
     Další informace najdete v tématu [nepodporované úpravy v Visual Basic upravit a pokračovat](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md).  
  
    > [!NOTE]
    > Pokud se pokusíte změnit kód, který není povolen úpravou a pokračováním, bude vaše úprava podtržena fialovou vlnovkou a úloha se zobrazí v Seznam úkolů. Nebudete moci pokračovat v provádění kódu, Pokud nevrátíte neplatnou změnu kódu.  
  
3. V nabídce **ladit** klikněte na **pokračovat** a pokračujte v provádění.  
  
     Váš kód se teď provádí s použitými úpravami, které jsou součástí projektu.  
  
## <a name="see-also"></a>Viz také  
 [Nepodporované úpravy v Visual Basic upravit a pokračovat](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md)   
 [Upravit a pokračovat (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)
