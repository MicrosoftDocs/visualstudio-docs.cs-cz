---
description: Sdílení souborů systému Windows bylo nakonfigurováno, takže se ke vzdálenému počítači připojíte pomocí jiného uživatelského jména.
title: Sdílení souborů systému Windows bylo konfigurováno... | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.remote_credentials_prohibited
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cc34e269d609837d9080cd1e84787fbabf45ce76
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146246"
---
# <a name="error-windows-file-sharing-has-been-configured"></a>Chyba: Sdílení souborů systému Windows bylo konfigurováno...
Sdílení souborů systému Windows bylo nakonfigurováno, takže se ke vzdálenému počítači připojíte pomocí jiného uživatelského jména. Toto není kompatibilní se vzdáleným laděním

 Aktuální konfigurace sdílení souborů je nastavená tak, aby se připojovala ke vzdálenému počítači s použitím jiného uživatelského jména. V tomto scénáři není možné vzdálené ladění.

 Chcete-li tuto chybu opravit, přihlaste se k počítači pomocí jiného názvu účtu nebo změňte sdílení souborů tak, aby používalo název účtu, který ladíte.

 Pokud se chcete ke vzdálenému počítači připojit pomocí tohoto uživatelského jména, musíte se nejdřív odpojit od vzdáleného počítače.

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Přihlaste se k místnímu počítači, počítač, ze kterého ladíte, pomocí názvu druhého účtu.

     —nebo—

     . Odpojte se od vzdáleného počítače a potom překonfigurujte sdílení souborů, aby se připojil k druhému počítači pomocí názvu účtu:

    1. V nabídce **Start** přejděte na položku **příslušenství** a poté klikněte na položku **příkazový řádek**.

    2. Do příkazového řádku Windows zadejte:

         `net use /delete computer_name`

    3. Nastavení sdílení souborů změňte pomocí kterékoli z metod popsaných v nápovědě k systému Windows.
