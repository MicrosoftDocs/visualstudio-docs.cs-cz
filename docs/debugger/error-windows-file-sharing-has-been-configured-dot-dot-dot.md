---
title: 'Chyba: Sdílení souborů systému Windows byl nakonfigurován... | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.remote_credentials_prohibited
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
ms.openlocfilehash: 591b051cb6164f4c8d260be3de29833154c96255
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
ms.locfileid: "31472786"
---
# <a name="error-windows-file-sharing-has-been-configured"></a>Chyba: Sdílení souborů systému Windows bylo konfigurováno...
Sdílení souborů systému Windows je nakonfigurovaný tak, aby se připojit ke vzdálenému počítači pomocí jiné uživatelské jméno. Toto je kompatibilní s vzdálené ladění  
  
 Aktuální konfigurace sdílení souborů je nastavený pro připojení ke vzdálenému počítači pomocí jiné uživatelské jméno. Vzdálené ladění není možné v tomto scénáři.  
  
 Chcete-li opravit tuto chybu, přihlášení k počítači pomocí jiných název účtu nebo změňte sdílení souborů pro použití názvu účtu, pod kterou ladíte.  
  
 Pokud se chcete připojit ke vzdálenému počítači pomocí tohoto uživatelského jména, je nutné nejprve odpojit ze vzdáleného počítače.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Přihlaste se do místního počítače, počítač, kterou ladíte, pomocí jiných název účtu.  
  
     —nebo—  
  
     . Odpojení ze vzdáleného počítače a překonfigurujte sdílení souborů pro připojení k jiným počítačem pomocí název účtu:  
  
    1.  Na **spustit** nabídky, přejděte na příkaz **Příslušenství**a potom klikněte na **příkazového řádku**.  
  
    2.  Na příkazovém řádku Windows zadejte:  
  
         `net use /delete computer_name`  
  
    3.  Změňte nastavení sdílení souborů pomocí metod najdete v nápovědě k systému Windows.