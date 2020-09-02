---
title: Ukázka Dia2dump – | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- sample applications [DIA SDK]
- Dia2dump sample [DIA SDK]
ms.assetid: 492c0893-7043-452f-a020-890a47230d20
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a817720c1ad73b666e0c9a586bb583120a2533c1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197600"
---
# <a name="dia2dump-sample"></a>Dia2dump – ukázka
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ukázka Dia2dump – je nainstalována se sadou Visual Studio a obsahuje zdrojový soubor Dia2dump –. cpp. Kompilovaný spustitelný soubor se spustí z příkazového řádku a zobrazí obsah celého souboru databáze programu (PDB).  
  
### <a name="to-install-the-sample"></a>Instalace ukázky  
  
1. Ověřte, že váš systém splňuje všechny požadavky na instalaci popsané na úvodní stránce instalace sady Visual Studio.  
  
2. Nainstalujte Visual Studio a postupujte podle pokynů pro instalaci a pokyny k instalaci zahrnutých ukázek.  
  
#### <a name="to-build-the-sample"></a>Sestavení ukázky  
  
1. V aplikaci Visual Studio otevřete soubor Dia2dump –. sln. (Pokud je to nutné, Visual Studio vám pomůže s upgradem projektu Dia2dump –.)  
  
2. Na stránkách vlastností projektu zadejte do pole **C/C++** &#124; **Obecné** &#124; **Další adresáře include adresářů** parametr `..\DIA SDK\include` Directory. To zaručuje, že kompilátor může najít soubor Dia2. h.  
  
3. V nabídce **sestavení** klikněte na příkaz **znovu sestavit řešení**.  
  
4. Zavřete Visual Studio.  
  
#### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku  
  
1. Otevřete příkazový řádek a zadejte následující příkaz:  
  
    ```  
    dia2dump filename  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Zdrojový soubor Dia2dump –. cpp](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)   
 [Postupy: Řešení potíží spojených s neúspěšným upgradem projektu sady Visual Studio](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md)
