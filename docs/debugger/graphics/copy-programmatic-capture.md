---
title: Kopírování (zachytávání pomocí kódu programu) | Microsoft Docs
description: Pomocí metody Copy třídy VsgDbg zkopírujte obsah aktivního souboru protokolu grafiky (.vsglog) do nového souboru.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5e4006803364407fed4b837ea992a95429c1db39
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232658"
---
# <a name="copy-programmatic-capture"></a>Copy (zachytávání prostřednictvím kódu programu)
Zkopíruje obsah aktivního souboru protokolu grafiky (.vsglog) do nového souboru.

## <a name="syntax"></a>Syntaxe

```C++
void Copy(
  wchar_t const * szNewVSGLog
);
```

#### <a name="parameters"></a>Parametry
 `szNewVSGLog` Název nového souboru protokolu grafiky.

## <a name="remarks"></a>Poznámky
 Chcete-li zkopírovat informace grafiky do nového souboru, musíte již zaznamenat některé informace grafiky. Jinak se nic nestane.