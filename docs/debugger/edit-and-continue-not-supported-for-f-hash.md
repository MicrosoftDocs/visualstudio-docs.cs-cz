---
title: 'V jazyce F # není podporována úprava a pokračování. Microsoft Docs'
description: 'Pro ladění F # není podporována úprava a pokračování. Úpravy kódu během ladění nejsou aplikovány na zdroj, takže kód, který se právě ladí, se neshoduje se zdrojem.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [F#]
- Debugging [F#], Edit and Continue
ms.assetid: 40ec77bb-07e3-4b58-9254-ae015009441c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a686cf91a515d2b7b59d87d7b3ca8e92d4e54c59
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871985"
---
# <a name="edit-and-continue-not-supported-for-f"></a>Operace Upravit a pokračovat není podporována pro F#. #
Při ladění kódu F # není podporována úprava a pokračování. Úpravy kódu F # jsou možné během relace ladění, ale je třeba se jim vyhnout. Změny kódu se během ladicí relace nepoužívají. Proto jakékoli úpravy provedené v kódu F # při ladění způsobí, že se zdrojový kód neshoduje s laděným kódem.
