---
title: 'Postupy: povolení a zákaz úprav a pokračování | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- /INCREMENTAL linker option
- Apply Code Changes command
- Edit and Continue, disabling
- code changes, applying in break mode
- INCREMENTAL linker option
- Edit and Continue, enabling
- break mode, applying code changes
- Edit and Continue, applying code changes
- Step command
- Go command
ms.assetid: fd961a1c-76fa-420d-ad8f-c1a6c003b0db
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 70914da9be4046589a0ca3b8e5fd4ae13210ca51
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65689267"
---
# <a name="how-to-enable-and-disable-edit-and-continue"></a>Postupy: Povolení a zákaz operace Upravit a pokračovat
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V dialogovém okně **Možnosti** v době návrhu můžete zakázat nebo povolit možnost upravit a pokračovat. Při ladění nejde toto nastavení změnit.  
  
 Funkce upravit a pokračovat funguje pouze v sestavení ladění. Pro nativní C++ vyžaduje příkaz Upravit a pokračovat možnost použití možnosti/INCREMENTAL.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-enabledisable-edit-and-continue"></a>Povolení nebo zakázání úprav a pokračování  
  
1. Otevřete stránku možnosti ladění (**Nástroje/možnosti/ladění**).  
  
2. Přejděte dolů na kategorie **Upravit a pokračovat** .  
  
3. Pokud ho chcete povolit, zaškrtněte políčko **Povolit úpravy a pokračovat** . Pokud ho chcete zakázat, zrušte zaškrtnutí políčka.  
  
   > [!NOTE]
   > Pokud je povolená možnost IntelliTrace a shromáždíte obě události IntelliTrace a informace o volání, možnost upravit a pokračovat je zakázaná. Další informace najdete v tématu [Konfigurace IntelliTrace](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
4. Klikněte na **OK**.  
  
   Další informace o těchto možnostech naleznete v části [Obecné, ladění, dialogové okno Možnosti](../debugger/general-debugging-options-dialog-box.md).  
  
## <a name="see-also"></a>Viz také  
 [Upravit a pokračovat](../debugger/edit-and-continue.md)
