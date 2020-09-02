---
title: 'V jazyce F # není podporována úprava a pokračování. Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue [F#]
- Debugging [F#], Edit and Continue
ms.assetid: 40ec77bb-07e3-4b58-9254-ae015009441c
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a4fef61335679e3f82d5916726981e003bf9c332
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62428454"
---
# <a name="edit-and-continue-not-supported-for-f"></a>Operace Upravit a pokračovat není podporována pro F#. #
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při ladění kódu F # není podporována úprava a pokračování. Úpravy kódu F # jsou možné během relace ladění, ale je třeba se jim vyhnout. Změny kódu se během ladicí relace nepoužívají. Proto jakékoli úpravy provedené v kódu F # při ladění způsobí, že se zdrojový kód neshoduje s laděným kódem.
