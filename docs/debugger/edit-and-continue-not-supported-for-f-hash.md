---
title: 'V jazyce F # není podporována úprava a pokračování. Microsoft Docs'
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ceb0ca767b1ac6364e103925fb86ed639c3d321d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62851161"
---
# <a name="edit-and-continue-not-supported-for-f"></a>Operace Upravit a pokračovat není podporována pro F#. #
Při ladění kódu F # není podporována úprava a pokračování. Úpravy kódu F # jsou možné během relace ladění, ale je třeba se jim vyhnout. Změny kódu se během ladicí relace nepoužívají. Proto jakékoli úpravy provedené v kódu F # při ladění způsobí, že se zdrojový kód neshoduje s laděným kódem.
