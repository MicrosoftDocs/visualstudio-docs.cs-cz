---
title: Nelze připojit k procesu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.remote.unable2attach
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7036210f47e99ca11edbdb86fdf1f44e40829237
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
ms.locfileid: "31476712"
---
# <a name="unable-to-attach-to-the-process"></a>Nelze připojit k procesu.
Nelze připojit k procesu. Ladicí program součásti na server obdržel při připojení k tomuto počítači byl zamítnut přístup.  
  
 Existují dvě běžné scénáře, které tato chyba způsobit:  
  
 **Scénář 1:** A počítač se systémem Windows XP. Počítač B je spuštěný Windows Server 2003. Registr na počítač B obsahuje následující hodnotu DWORD:  
  
 `HKLM\Software\Microsoft\MachineDebugManager\AllowLaunchAsOtherUser=1`  
  
 Uživatel 1 spustí relaci terminálového serveru (relace 1) na počítači B a spustí spravované aplikace z této relace.  
  
 Přihlášení uživatele 2, který je správcem na obou počítačích, na počítač A. Z ní se pokusí připojit k aplikaci spuštěné v relaci 1 na počítač B.  
  
 **Scénář 2:** jeden uživatel je přihlášený dva počítače, A a B, ve stejné pracovní skupině, pomocí stejného hesla na obou počítačích. Ladicí program běží na počítači A a při pokusu o připojení ke spravované aplikaci spuštěné v počítači B. počítač A má **přístup k síti: model sdílení a zabezpečení pro místní účty** nastavena na **hosta**.  
  
### <a name="to-solve-scenario-1"></a>K vyřešení scénář 1  
  
-   Spuštění spravované aplikace stejný název uživatelského účtu a heslo a ladicí program.  
  
### <a name="to-solve-scenario-2"></a>K vyřešení scénáři 2  
  
1.  Z **spustit** nabídce zvolte **ovládací panely**.  
  
2.  V Ovládacích panelech klikněte dvakrát na **nástroje pro správu**.  
  
3.  V okně nástroje pro správu klikněte dvakrát na **místní zásady zabezpečení**.  
  
4.  V okně místní zásady zabezpečení, vyberte **místní zásady**.  
  
5.  V **zásady** sloupce, klikněte dvakrát na **přístup k síti: model sdílení a zabezpečení pro místní účty**.  
  
6.  V **přístup k síti: model sdílení a zabezpečení pro místní účty** dialogové okno pole, změňte nastavení zabezpečení pro **Classic**a klikněte na tlačítko **OK**.  
  
    > [!CAUTION]
    >  Změna modelu zabezpečení na klasickém může způsobit neočekávané přístup ke sdíleným souborům a komponenty DCOM. Pokud provedete tuto změnu, můžete ověřovat vzdáleného uživatele s vaší místní uživatelský účet a spíše než hosta. Pokud vzdálený uživatel odpovídá svoje uživatelské jméno a heslo, bude mít přístup všechny složky nebo objekt modelu DCOM, které jste sdíleli na tohoto uživatele. Pokud použijete tento model zabezpečení, ujistěte se, že všechny uživatelské účty na počítači mít silná hesla nebo nastavit island izolovanou síť pro ladění a ladit počítače před neoprávněným přístupem.  
  
7.  Zavřete všechna okna.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení ladicího programu a příprava](../debugger/debugger-settings-and-preparation.md)