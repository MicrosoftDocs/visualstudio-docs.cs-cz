---
title: Nastavení aplikace v rámci více připojení k projektu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bca17fdc440fc373d0d4811ed57cd5d27a6c201a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203845"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>Aplikace nastavení napříč různými připojeními projektů
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Modul plug-in správy zdrojových kódů sestavený pomocí modulu plug-in pro správu zdrojového kódu rozhraní API 1,2 může použít dávkovou operaci ke spuštění stejné operace správy zdrojových kódů v několika projektech nebo v několika kontextech připojení. Dávky lze použít k odstranění redundantních dialogových oken pro jednotlivé projekty z uživatelského prostředí.  
  
 Pokud uživatel vybere více položek, které patří do více než jednoho připojení v modulu plug-in správy zdrojového kódu vytvořeném pomocí rozhraní API modulu plug-in správy zdrojových kódů 1,1 (například dva webové projekty v různých počítačích sdílených souborů) a zařadí je, uživatel uvidí stejné dialogové okno opakovaně. K tomu dojde i v případě, že uživatel klikne v dialogovém okně na zaškrtávací políčko **použít u všech** , protože rozhraní IDE obnoví stav pro každý kontext připojení.  
  
## <a name="new-capability-flag"></a>Příznak nové schopnosti  
 `SccBeginBatch` Funkce nastaví `SCC_CAP_BATCH` příznak tak, aby označoval, že probíhá operace dávky.  
  
## <a name="new-functions"></a>Nové funkce  
 Dávková operace podporuje následující nové funkce:  
  
- [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)  
  
- [SccEndBatch](../../extensibility/sccendbatch-function.md)  
  
  `SCCBeginBatch`Funkce spustí skupinu operací správy zdrojového kódu. `SccEndBatch` zavře skupinu. Skupiny nesmí být vnořené.  
  
## <a name="see-also"></a>Viz také  
 [Co je nového v rozhraní API modulu plug-in správy zdrojového kódu ve verzi 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
