---
title: Kopírovat (programové zachycení) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3a888605cfae6b5430782defd198f83988c31870
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62895951"
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