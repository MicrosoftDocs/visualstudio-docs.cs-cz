---
title: Kopírovat (programové zachycení) | Microsoft Docs
description: Použijte metodu copy třídy VsgDbg ke zkopírování obsahu souboru protokolu Active Graphics (. vsglog) do nového souboru.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 62140f279d805e5162661c22110671871afff1ae
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879186"
---
# <a name="copy-programmatic-capture"></a>Copy (zachytávání prostřednictvím kódu programu)
Zkopíruje obsah souboru protokolu Active Graphics (. vsglog) do nového souboru.

## <a name="syntax"></a>Syntaxe

```C++
void Copy(
  wchar_t const * szNewVSGLog
);
```

#### <a name="parameters"></a>Parametry
 `szNewVSGLog` Název souboru nového souboru protokolu grafiky.

## <a name="remarks"></a>Poznámky
 Chcete-li zkopírovat informace o grafice do nového souboru, musíte již zachytit informace grafiky. v opačném případě se nic nestane.