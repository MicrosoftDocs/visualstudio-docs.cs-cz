---
title: Aplikace nastavení napříč různými připojeními projektů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6d8b8d7d6dc1e596686a2fad7b53363b2387a47b
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500040"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>Aplikace nastavení napříč různými připojeními projektů
Modul plug-in správy zdrojového kódu vytvořených pomocí verze 1.2 zdrojový ovládací prvek modulu Plug-in API můžete použít dávkové operace ke spuštění stejnou operaci správy zdrojových kódů napříč více projekty nebo více kontexty připojení. Dávky je možné vyloučit redundantní, dialogová okna uživatelským prostředím jednotlivých projektů.  
  
 Pokud uživatel vybere více položek, které patří do více než jedno připojení v modulu plug-in správy zdrojového kódu, vytvořené pomocí zdrojového ovládacího prvku modulu Plug-in API verze 1.1 (například dvě webové projekty na počítačích jinou sdílenou složku) a ověří je, uživateli se zobrazí stejné Dialogové okno opakovaně. Této situaci dojde i v případě, že uživatel klikne **použít u všech** zaškrtněte políčko v dialogovém okně, protože rozhraní IDE obnoví svůj stav pro každý kontext připojení.  
  
## <a name="new-capability-flag"></a>Nový příznak funkce  
 `SccBeginBatch` Funkce nastaví `SCC_CAP_BATCH` příznak označující, že dávkové operace probíhá.  
  
## <a name="new-functions"></a>Nové funkce  
Následující nové funkce podporují dávkové operace:  
  
-   [Sccbeginbatch –](../../extensibility/sccbeginbatch-function.md)  
  
-   [Sccendbatch –](../../extensibility/sccendbatch-function.md)  

  
`SCCBeginBatch` Funkce spustí skupinu operací správy zdrojů. `SccEndBatch` Funkce uzavře skupině. Skupiny nemůže být vnořený.  
  
## <a name="see-also"></a>Viz také:  
 [Co je nového v zdrojový ovládací prvek modulu Plug-in API verze 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)