---
title: Nepovedlo se připojit k &lt; názvu počítače &gt; . Počítač se v síti nepodařilo najít. | Dokumentace Microsoftu
ms.date: 11/04/2016
ms.topic: error-reference
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: dcf52a258a46f44afaf6e890531496f57b11fc24
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871062"
---
# <a name="error-unable-to-connect-to-the-machine-ltnamegt-the-machine-cannot-be-found-on-the-network"></a>Chyba: Nelze se připojit k názvu počítače &lt; &gt; . Počítač se v síti nepodařilo najít.
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

## <a name="see-also"></a>Viz také
- [Vzdálené ladění](../debugger/remote-debugging.md)
- [Nastavení a příprava ladicího programu](../debugger/debugger-settings-and-preparation.md)