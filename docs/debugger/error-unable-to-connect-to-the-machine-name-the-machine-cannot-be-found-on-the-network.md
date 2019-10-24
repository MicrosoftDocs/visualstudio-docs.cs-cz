---
title: 'Chyba: Nelze se připojit k počítači &lt;name &gt;. Počítač se v síti nepodařilo najít. | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.remote.dcom_disabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- DCOM, unable to connect error
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7d0f820156714a726d506d8871d4e42a8dc12a23
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736840"
---
# <a name="error-unable-to-connect-to-the-machine-ltnamegt-the-machine-cannot-be-found-on-the-network"></a>Chyba: Nelze se připojit k počítači &lt;name &gt;. Počítač se v síti nepodařilo najít.
K tomuto chování dochází, pokud je splněna jedna z následujících podmínek:

- Připojení ke vzdálenému počítači bylo přerušeno.

- Váš uživatelský účet na vzdáleném počítači je zakázán.

- Platnost vašeho hesla na vzdáleném počítači vypršela.

### <a name="to-resolve-this-behavior"></a>Řešení tohoto chování

- Ujistěte se, že je místní počítač a vzdálený počítač ve stejné síti. K tomu použijte Průzkumníka Windows (nebo Průzkumníka souborů) a pokuste se získat přístup ke vzdálenému počítači.

     ani

- Ujistěte se, že uživatelský účet, který používáte pro připojení ke vzdálenému počítači, je povolený.

     ani

- Ujistěte se, že heslo, které používáte pro připojení ke vzdálenému počítači, je platné a nevypršela jeho platnost.

## <a name="see-also"></a>Viz také:
- [Vzdálené ladění](../debugger/remote-debugging.md)
- [Nastavení a příprava ladicího programu](../debugger/debugger-settings-and-preparation.md)