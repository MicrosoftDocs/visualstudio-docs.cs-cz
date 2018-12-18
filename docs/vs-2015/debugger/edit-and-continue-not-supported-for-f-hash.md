---
title: Upravit a pokračovat není podporována pro F# | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 0d177630af5827362d7e631cb4def29f71e6020d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51799727"
---
# <a name="edit-and-continue-not-supported-for-f"></a>Operace Upravit a pokračovat není podporována pro F#. #
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Upravit a pokračovat není podporovaná při ladění F# kódu. Úpravy F# kódu je možné během relace ladění, ale mělo by se vyhnout. Během relace ladění se nepoužijí změny kódu. Proto se veškeré úpravy provedené F# kódu během ladění způsobí zdrojový kód, který neodpovídá kódu, který se právě ladí.



