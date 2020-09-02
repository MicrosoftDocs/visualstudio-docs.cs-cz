---
title: 'Chyba: sdílení souborů systému Windows bylo konfigurováno... | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.remote_credentials_prohibited
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c45a1b74-61ec-4c64-9e2c-13051a4f50a5
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 96d65ae615522bcee43ddf5e8181e96eecc0d958
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157502"
---
# <a name="error-windows-file-sharing-has-been-configured"></a>Chyba: Sdílení souborů systému Windows bylo konfigurováno...
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sdílení souborů systému Windows bylo nakonfigurováno, takže se ke vzdálenému počítači připojíte pomocí jiného uživatelského jména. Toto není kompatibilní se vzdáleným laděním  
  
 Aktuální konfigurace sdílení souborů je nastavená tak, aby se připojovala ke vzdálenému počítači s použitím jiného uživatelského jména. V tomto scénáři není možné vzdálené ladění.  
  
 Chcete-li tuto chybu opravit, přihlaste se k počítači pomocí jiného názvu účtu nebo změňte sdílení souborů tak, aby používalo název účtu, který ladíte.  
  
 Pokud se chcete ke vzdálenému počítači připojit pomocí tohoto uživatelského jména, musíte se nejdřív odpojit od vzdáleného počítače.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Přihlaste se k místnímu počítači, počítač, ze kterého ladíte, pomocí názvu druhého účtu.  
  
     —nebo—  
  
     . Odpojte se od vzdáleného počítače a potom překonfigurujte sdílení souborů, aby se připojil k druhému počítači pomocí názvu účtu:  
  
    1. V nabídce **Start** přejděte na položku **příslušenství**a poté klikněte na položku **příkazový řádek**.  
  
    2. Do příkazového řádku Windows zadejte:  
  
         `net use /delete computer_name`  
  
    3. Nastavení sdílení souborů změňte pomocí kterékoli z metod popsaných v nápovědě k systému Windows.
