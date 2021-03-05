---
title: Nepovedlo se připojit k &lt; názvu počítače &gt; . Počítač se v síti nepodařilo najít. | Dokumentace Microsoftu
description: 'K tomuto chování dochází, pokud je splněna jedna z následujících podmínek: (1) vaše připojení ke vzdálenému počítači bylo přerušeno. (2) váš uživatelský účet na vzdáleném počítači je zakázán. (3) platnost vašeho hesla na vzdáleném počítači vypršela.'
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
ms.openlocfilehash: 5e0d83f043e020ad3c65ac0f986ec174fac95585
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146428"
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
