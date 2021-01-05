---
title: Kopírovat (programové zachycení) | Microsoft Docs
description: Použijte metodu copy třídy VsgDbg ke zkopírování obsahu souboru protokolu Active Graphics (. vsglog) do nového souboru.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 126b1d7a2fa9064a343e7eadbe83dd1eeecccb83
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727841"
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