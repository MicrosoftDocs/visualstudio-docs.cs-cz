---
title: Nelze se připojit k procesu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.remote.unable2attach
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 0468de6c-3ff1-4979-a8c6-8afb53f37547
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c74799daf57ca031c4b3ce6bf76f72e453eeb0b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64824205"
---
# <a name="unable-to-attach-to-the-process"></a>Nelze připojit k procesu.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

K procesu se nelze připojit. Komponenta ladicího programu na serveru obdržela při připojování k tomuto počítači odepřený přístup.  
  
 Tato chyba je způsobená dvěma běžnými scénáři:  
  
 **Scénář 1:** Počítač A používá systém Windows XP. Počítač B používá systém Windows Server 2003. Registr v počítači B obsahuje následující hodnotu DWORD:  
  
 `HKLM\Software\Microsoft\MachineDebugManager\AllowLaunchAsOtherUser=1`  
  
 Uživatel 1 spustí relaci terminálového serveru (relace 1) na počítači B a spustí spravovanou aplikaci z této relace.  
  
 Uživatel 2, který je správcem obou počítačů, je přihlášen do počítače A. Odtud se pokusí připojit k aplikaci spuštěné v relaci 1 na počítači B.  
  
 **Scénář 2:** Jeden uživatel je přihlášen do dvou počítačů, a a B ve stejné pracovní skupině, přičemž používá stejné heslo na obou počítačích. Ladicí program je spuštěn v počítači a a pokouší se připojit ke spravované aplikaci běžící na počítači B. počítač A má **přístup k síti: model sdílení a zabezpečení místních účtů** nastavených na hodnotu **Host**.  
  
### <a name="to-solve-scenario-1"></a>Řešení scénáře 1  
  
- Spusťte ladicí program a spravovanou aplikaci pod stejným názvem a heslem uživatelského účtu.  
  
### <a name="to-solve-scenario-2"></a>Řešení scénáře 2  
  
1. V nabídce **Start** klikněte na položku **Ovládací panely**.  
  
2. V Ovládacích panelech poklikejte na **Nástroje pro správu**.  
  
3. V okně nástroje pro správu poklikejte na **místní zásady zabezpečení**.  
  
4. V okně místní zásady zabezpečení vyberte **místní zásady**.  
  
5. Ve sloupci **zásady** poklikejte na **přístup k síti: model sdílení a zabezpečení místních účtů**.  
  
6. V dialogovém okně **přístup k síti: model sdílení a zabezpečení místních účtů** změňte místní nastavení zabezpečení na **Classic**a klikněte na tlačítko **OK**.  
  
    > [!CAUTION]
    > Změna modelu zabezpečení na klasický může mít za následek neočekávaný přístup ke sdíleným souborům a komponentám DCOM. Pokud tuto změnu provedete, vzdálený uživatel se bude moci ověřit pomocí místního uživatelského účtu místo hosta. Pokud vzdálený uživatel odpovídá vašemu uživatelskému jménu a heslu, bude mít tento uživatel přístup ke všem složkám nebo objektům DCOM, které jste sdíleli. Pokud použijete tento model zabezpečení, ujistěte se, že všechny uživatelské účty v počítači mají silná hesla, nebo nastavte izolovaný síťový ostrůvek pro ladění a laděné počítače, aby se zabránilo neoprávněnému přístupu.  
  
7. Zavřete všechna okna.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení a příprava ladicího programu](../debugger/debugger-settings-and-preparation.md)
