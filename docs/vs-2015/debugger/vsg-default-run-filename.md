---
title: VSG_DEFAULT_RUN_FILENAME | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: ea549d2f-c857-458c-93c7-bc5a2d11d15d
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2980d34028c58a6abadb2df21bf22c8d37cda6e0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160765"
---
# <a name="vsg_default_run_filename"></a>VSG_DEFAULT_RUN_FILENAME
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Definuje výchozí název souboru protokolu grafiky.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
#define VSG_DEFAULT_FILENAME filename  
```  
  
#### <a name="parameters"></a>Parametry  
 `filename`  
 Název souboru, který je ve výchozím nastavení k souboru protokolu grafiky při zachycení informací grafiky prostřednictvím kódu programu.  
  
## <a name="value"></a>Hodnota  
 Řetězcový literál, který představuje název souboru protokolu grafiky. Ve výchozím nastavení je to L "default. vsglog".  
  
```cpp  
#define VSG_DEFAULT_FILENAME L"default.vsglog"  
```  
  
## <a name="remarks"></a>Poznámky  
 Pokud je definován symbol preprocesoru `DONT_SAVE_VSGLOG_TO_TEMP` , je název souboru relativní vzhledem k aktuálnímu adresáři zachycené aplikace nebo je absolutní cesta. v opačném případě je relativní vzhledem k adresáři dočasných souborů uživatele a nemůže být absolutní cesta.  
  
 Chcete-li změnit definovaný název souboru, je nutné jej před vložením `vsgcapture.h` do programu předefinovat.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak změnit výchozí název souboru digitalizačního souboru:  
  
```cpp  
// Redefine the default capture filename before including vsgcapture.h  
#define VSG_DEFAULT_FILENAME L"capture.vsglog"  
  
#include <vsgcapture.h>  
```  
  
## <a name="see-also"></a>Viz také  
 [DONT_SAVE_VSGLOG_TO_TEMP](../debugger/dont-save-vsglog-to-temp.md)
