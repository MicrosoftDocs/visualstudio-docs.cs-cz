---
title: -SafeMode (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 28480399238c1c915056d3929f8fd188cfff7eca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665513"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Spustí se [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] v nouzovém režimu a načte jenom výchozí prostředí a služby.

## <a name="syntax"></a>Syntax

```
devenv /SafeMode
```

## <a name="remarks"></a>Poznámky
 Tento přepínač brání načtení všech VSPackage od jiných výrobců při [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] spuštění, takže zajišťuje stabilní spuštění.

## <a name="description"></a>Popis
 Následující příklad je spuštěn [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] v nouzovém režimu.

## <a name="code"></a>Kód

```
Devenv.exe /SafeMode
```

## <a name="see-also"></a>Viz také
 [Devenv – přepínače příkazového řádku](../../ide/reference/devenv-command-line-switches.md)
