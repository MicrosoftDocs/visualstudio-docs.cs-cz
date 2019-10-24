---
title: 'Chyba: nepovedlo se ověřit zabezpečení, protože služba správy služby IIS neodpověděla | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f668de3d7c7e9a8bd075beb972199cf849feea65
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737877"
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

## <a name="see-also"></a>Viz také:
- [Ladění webových aplikací: Chyby a řešení potíží](../debugger/debugging-web-applications-errors-and-troubleshooting.md)