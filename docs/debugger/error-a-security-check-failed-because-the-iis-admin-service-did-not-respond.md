---
description: K této chybě dochází, pokud služba správy služby IIS nereaguje.
title: Ověření zabezpečení se nezdařilo, protože služba správy služby IIS neodpověděla | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.iis_not_responding
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 42c0a5a1a1fdb3a997f46a6933df9c8681fe0498
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147079"
---
# <a name="error-a-security-check-failed-because-the-iis-admin-service-did-not-respond"></a>Chyba: Kontrola zabezpečení selhala, protože služba správy služby IIS neodpověděla.
K této chybě dochází, pokud služba správy služby IIS nereaguje. To obvykle znamená, že došlo k potížím s instalací služby IIS. Nejdřív ověřte, že je služba spuštěná pomocí nástroje **služby** z **nástrojů pro správu**.

### <a name="to-correct-this-error"></a>Oprava této chyby

- Přeinstalujte službu IIS pomocí ovládacího panelu **Přidat nebo odebrat programy** .

- -nebo-

- Z počítače odeberte službu IIS pomocí ovládacího panelu Přidat nebo odebrat programy. Pokud jste službu IIS odebrali a pořád máte problémy, zkontrolujte registr a ujistěte se, že tento klíč už neexistuje:

    `HKEY_CLASSES_ROOT\CLSID\{A9E69610-B80D-11D0-B9B9-00A0C922E750}`

     -nebo-

- Zakažte službu Správce služby IIS pomocí ovládacího panelu nástroje pro správu. Tím se na vašem počítači zakáže služba IIS.

     Po provedení některého z těchto tří kroků restartujte počítač.

     Další informace najdete v dokumentaci ke službě IIS.

## <a name="see-also"></a>Viz také
- [Ladění webových aplikací: chyby a řešení potíží](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
